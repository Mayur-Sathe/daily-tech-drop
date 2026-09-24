# Daily Tech Drop — Structured Logging for Easier Debugging 🧾

When something fails in a project, `print("error")` often is not enough. A better technique is **structured logging**: record events in a consistent format so you can search, filter, and understand them quickly.

Instead of writing:

```text
Login failed
```

write something like:

```json
{"event":"login_failed","user_id":42,"reason":"wrong_password"}
```

That extra structure becomes very useful when your app grows.

## Small code example

```python
import json
from datetime import datetime, timezone


def log_event(event: str, **details):
    record = {
        "time": datetime.now(timezone.utc).isoformat(),
        "event": event,
        **details,
    }
    print(json.dumps(record))


log_event("motor_command", device="esp32-car", action="forward", speed=80)
log_event("motor_command_failed", device="esp32-car", reason="driver_timeout")
```

Example output:

```json
{"time":"2026-09-24T00:00:00+00:00","event":"motor_command","device":"esp32-car","action":"forward","speed":80}
```

## Why this matters

Structured logs help you:

- search for one event type
- filter by device, user, or request ID
- compare failures across time
- connect logs from multiple services
- debug projects without guessing

## Today’s experiment 🧪

Add a `request_id` to every log record.

Then try these improvements:

1. Write logs to a file instead of only the terminal.
2. Add a `level` field such as `INFO`, `WARNING`, or `ERROR`.
3. Create a function that prints only error records.
4. Use the same format in one of your ESP32 or Python projects.

## Beginner takeaway

Good debugging starts with good evidence:

**Record clearly → Search quickly → Fix confidently**

A few consistent fields today can save a lot of time when your project becomes larger tomorrow.
