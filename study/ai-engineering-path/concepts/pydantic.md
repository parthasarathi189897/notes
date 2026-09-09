# Pydantic v2 — Core Concept Notes

Quick reference covering ~80% of daily Pydantic usage. Tied to use cases like parsing/validating messy LLM JSON output.

---

## 1. The Basics — `BaseModel`

```python
from pydantic import BaseModel
from typing import Optional
from datetime import datetime

class User(BaseModel):
    id: int
    name: str = 'John Doe'
    signup_ts: Optional[datetime] = None
    friends: list[int] = []

external_data = {'id': '123', 'signup_ts': '2017-06-01 12:22', 'friends': [1, '2', b'3']}
user = User(**external_data)
print(user)
# id=123 name='John Doe' signup_ts=datetime.datetime(2017, 6, 1, 12, 22) friends=[1, 2, 3]
```

**Key idea:** Pydantic doesn't just *check* types — it *coerces* them. `'123'` → `int`, a date string → `datetime`, mixed list items → `int`. Plain Python type hints do none of this at runtime; Pydantic is what actually enforces them.

---

## 2. `Optional` vs. Defaults — Two Separate Knobs

`Optional[X]` = `Union[X, None]`. It only says "this value can be `X` or `None`." It does **not** make the field skippable — that's controlled purely by whether you give it a `= default`.

```python
# Optional, no default → still REQUIRED
class A(BaseModel):
    x: Optional[str]
A()  # ❌ ValidationError: field required

# Optional, with default → NOT required
class B(BaseModel):
    x: Optional[str] = None
B()  # ✅ x=None

# NOT Optional, with default → NOT required
class C(BaseModel):
    x: str = "hello"
C()  # ✅ x='hello'

# NOT Optional, no default → REQUIRED
class D(BaseModel):
    x: str
D()  # ❌ ValidationError: field required
```

### ⚠️ Gotcha: `x: str = None`

This "works" but is a trap:

```python
class C(BaseModel):
    x: str = None

C()          # ✅ x=None   — defaults are NOT validated by default
C(x=None)    # ❌ ValidationError — explicit input IS validated, and None isn't a str
```

Inconsistent behavior depending on whether the field is omitted vs. explicitly passed. **Rule of thumb:** if `None` is a valid value, always write `Optional[str] = None` (or `str | None = None` in 3.10+) — never `str = None`.

---

## 3. Field Constraints — `Field()`

```python
from pydantic import BaseModel, Field

class Product(BaseModel):
    name: str = Field(min_length=1, max_length=100)
    price: float = Field(gt=0)            # greater than 0
    quantity: int = Field(ge=0, le=1000)  # 0 <= quantity <= 1000
    sku: str = Field(pattern=r'^[A-Z]{3}-\d{4}$')  # regex
```

Common constraint kwargs: `gt` / `ge` / `lt` / `le` (numbers), `min_length` / `max_length` (strings, lists), `pattern` (regex).

---

## 4. Nested Models

```python
class Address(BaseModel):
    city: str
    zip_code: str

class Customer(BaseModel):
    name: str
    address: Address   # nested model

c = Customer(name="Jane", address={"city": "SF", "zip_code": "94105"})
print(c.address.city)  # SF — nested dict auto-converts to Address
```

---

## 5. Lists and Dicts of Models

```python
class Order(BaseModel):
    items: list[str]
    customers: list[Customer]     # list of nested models
    metadata: dict[str, str] = {}
```

---

## 6. Enums for Fixed Choices

Useful for category/priority-style fields extracted by an LLM.

```python
from enum import Enum

class Priority(str, Enum):
    LOW = "low"
    MEDIUM = "medium"
    HIGH = "high"

class Ticket(BaseModel):
    priority: Priority

Ticket(priority="high")    # ✅ works
Ticket(priority="urgent")  # ❌ ValidationError — not in the enum
```

---

## 7. Custom Validators — `field_validator`

For cleaning/normalizing or rejecting messy input (core to LLM-output parsing).

```python
from pydantic import BaseModel, field_validator

class Ticket(BaseModel):
    email: str

    @field_validator('email')
    @classmethod
    def check_email(cls, v):
        if '@' not in v:
            raise ValueError('must contain @')
        return v.lower().strip()

Ticket(email='  JANE@Example.com  ')  # email='jane@example.com'
Ticket(email='not-an-email')          # ❌ ValidationError: must contain @
```

---

## 8. Cross-Field Validation — `model_validator`

When one field's validity depends on another.

```python
from pydantic import model_validator

class DateRange(BaseModel):
    start: str
    end: str

    @model_validator(mode='after')
    def check_order(self):
        if self.end < self.start:
            raise ValueError('end must be after start')
        return self
```

---

## 9. Catching `ValidationError`

```python
from pydantic import ValidationError

try:
    Ticket(email="bad")
except ValidationError as e:
    print(e.errors())  # structured list of dicts — great for logging / retry logic
```

Useful when you want to catch a failure and re-prompt an LLM rather than crash.

---

## 10. JSON Round-Tripping (I/O)

```python
t = Ticket(email="jane@example.com")

t.model_dump()        # {'email': 'jane@example.com'}   — plain dict
t.model_dump_json()   # '{"email": "jane@example.com"}' — JSON string

Ticket.model_validate({"email": "x@y.com"})        # from dict
Ticket.model_validate_json('{"email": "x@y.com"}') # from JSON string — typical for LLM output
```

---

## Reference Docs

- Models: https://docs.pydantic.dev/latest/concepts/models/
- Fields: https://docs.pydantic.dev/latest/concepts/fields/
- Validators: https://docs.pydantic.dev/latest/concepts/validators/
- Error Handling: https://docs.pydantic.dev/latest/errors/errors/
- JSON: https://docs.pydantic.dev/latest/concepts/json/

## Example
```python
from pydantic import BaseModel,Field, ValidationError

class SupportMessage(BaseModel):
	sender_email: str = Field(pattern=r'^[\w\.\+-]+@[\w-]+\.[a-zA-Z]{2,}$')
	message_body: str = Field(min_length=5)
	priority: int = Field(ge=1, le=5)
	is_resolved: bool = False
	
SupportMessage(
    sender_email= "jane@example.com",
    message_body = "My order hasn't arrived",
    priority = "3"  
)

try: 
	SupportMessage(
    	sender_email = "not-an-email",
    	message_body = "hi",
    	priority = 9
	)
except ValidationError as e:
	print(e.errors())
```
