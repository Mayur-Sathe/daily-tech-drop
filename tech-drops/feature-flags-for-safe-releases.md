# Daily Tech Drop — Feature Flags: Release Code Without Releasing Risk 🚦

A **feature flag** lets you turn a feature on or off using configuration instead of changing code every time. This is useful when you want to test a feature with a few users, release it gradually, or quickly disable it if something goes wrong.

## Why it matters

Feature flags help you separate:

- **Deploying code** — putting code into production
- **Releasing a feature** — making it visible to users

That separation makes experiments safer and rollbacks faster.

## Small code example

```python
FEATURES = {
    "new_dashboard": False,
    "dark_mode": True,
}


def is_enabled(name: str) -> bool:
    return FEATURES.get(name, False)


if is_enabled("new_dashboard"):
    print("Show the new dashboard")
else:
    print("Show the old dashboard")
```

The code is simple, but the idea scales. In a real app, the flag values could come from a JSON file, environment variables, or a feature-management service.

## Today’s experiment 🧪

Add one feature flag to a small project you already have.

Try this mini-plan:

1. Pick one visible feature.
2. Put its on/off state in one configuration object.
3. Write one helper function such as `is_enabled()`.
4. Test both states.
5. Add a short comment explaining when the flag can be removed.

## Beginner takeaway

A practical release workflow is:

**Build → Deploy → Enable gradually → Observe → Keep or disable**

Feature flags are a small technique that teaches a big software-engineering idea: make changes reversible whenever possible.
