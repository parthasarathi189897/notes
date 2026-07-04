Type hint

Data validation happen with pydantic module.
Pydantic is written in rust.
Both input param validation and making sure the output follow a structured output we use pydantic.

Creating and using models:
- Pydantic models are the foundation of data validation in python.
- They use **python type annotations** to define the structure and validate data at **run time.**
```python
from pydantic import BaseModel

class Person(BaseModel):
	name: str
	age: int
	city: str
	
person = Person(name="Partha", age=39, city="San Jose")
```

How pydantic is different from dataclass:
- Runtime data validation happens with pydantic but not with dataclass
- Both gives type hint

More examples:

```python
from typing import Optional, List
from pydantic import BaseModel

class Address(BaseModel):
	street: str
	city: str
	zip_code: int
	
class Employee(BaseModel):
	id: int
	name: str
	department: str
	salary: Optional[float] = None #Optional with default value
	is_active: bool = True # Verify if it works? Does it make the field optional
	skills: List[str] # List of strings
	address: Address # Nested Model
	 
	
try:
	employee = Employee(id=1, name = "Partha", department = "IT", skills = ["python", "html"], address = {street: "456 Epic way", city: "San Jose", zip_code: 95134})
except ValueError as e:
	print(e) 
	
```

Automatic type conversions also happen:
- str to number
- number to bool

Customizations and Constraints:

```python
from pydantic import BaseModel, Field

class Item(BaseModel):
	name: str = Field(min_length=2, max_length=50)
	price: str = Field(gt=0, le=10) # greater than and less than equal. gt, ge, lt, le
	
class Person(BaseModel):
	age: int = Field(default=18, description="Person age, default to 18")
	email: str = Field(default_factory = lambda: "user@email.com", description="person email, default to user@email.com")
	
Person.model_json_schema()
```