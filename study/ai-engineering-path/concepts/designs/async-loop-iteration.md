#### One tick of the event loop (what `run_until_complete` does in a cycle)

```mermaid
flowchart TD
    START([loop starts]) --> CHECK{Ready queue<br/>empty?}

    CHECK -- "no (work to do)" --> POP[Pop one ready callback / coroutine]
    POP --> RUNC["Run it until it either<br/>hits await, or returns"]
    RUNC --> AW{Hit await on<br/>unfinished work?}

    AW -- "yes" --> REG["Register a wake-up callback<br/>on that future → coroutine SUSPENDS"]
    REG --> CHECK

    AW -- "no — it returned" --> SETRES["Set the Task's result<br/>→ schedule whatever was awaiting it"]
    SETRES --> CHECK

    CHECK -- "yes (nothing ready)" --> ANYT{Any timers or<br/>I/O still pending?}

    ANYT -- "yes" --> SELECT["selector.select(timeout = next timer)<br/>🛑 the single thread idles here at the OS level"]
    SELECT --> WAKE["A timer fires / socket is ready<br/>→ push its callback onto the ready queue"]
    WAKE --> CHECK

    ANYT -- "no" --> STOP([loop stops])
```

> The loop only ever does two things: **drain the ready queue**, then **sleep on the selector** until something becomes ready. Repeat.
