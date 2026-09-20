# Daily Tech Drop — Smart Retries with Exponential Backoff 🔁

When an app calls an API or network service, temporary failures can happen because of slow internet, server overload, or rate limits. A useful technique is **exponential backoff**: wait a little after the first failure, then wait longer after each retry.

Instead of retrying immediately three times, use delays like:

`1 second → 2 seconds → 4 seconds`

This reduces pressure on the server and gives a temporary problem time to recover.

## Small Python example

```python
import time


def retry(operation, attempts=4, base_delay=1):
    for attempt in range(attempts):
        try:
            return operation()
        except Exception as error:
            last_attempt = attempt == attempts - 1

            if last_attempt:
                raise error

            delay = base_delay * (2 ** attempt)
            print(f"Attempt {attempt + 1} failed: {error}")
            print(f"Retrying in {delay} second(s)...")
            time.sleep(delay)


def unstable_task():
    # Replace this with a real API call or database operation.
    raise ConnectionError("Temporary network problem")


try:
    retry(unstable_task)
except ConnectionError as error:
    print("Operation failed after all retries:", error)
```

## Why it is useful

You can use this pattern for:

- REST API requests
- Database connections
- File uploads
- Microservice-to-microservice calls
- IoT devices with unstable connectivity

In production, also add a **maximum delay**, retry only errors that are temporary, and use a small random value called **jitter** so many clients do not retry at exactly the same time.

## Today’s experiment 🧪

Modify the example so that:

1. The operation succeeds on the third attempt.
2. The maximum delay is 5 seconds.
3. A random jitter of 0–0.5 seconds is added to each delay.

## Beginner takeaway

A reliable network program does not assume that every failure is permanent.

**Fail safely → wait intelligently → retry selectively → stop clearly**
