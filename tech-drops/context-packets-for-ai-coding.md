# Daily Tech Drop — Context Packets for AI Coding 🚀

AI coding tools work best when they understand the project, not just the one sentence you type. A useful technique is to prepare a small **context packet** before asking for a change.

A context packet contains four things:

- The exact goal
- The files that may change
- The project rules to follow
- The tests that prove the feature works

## Try it in Python

```python
from dataclasses import dataclass

@dataclass
class ContextPacket:
    goal: str
    files: list[str]
    rules: list[str]
    tests: list[str]

packet = ContextPacket(
    goal="Add email validation to the registration form",
    files=["app.py", "templates/register.html", "tests/test_register.py"],
    rules=["Do not change the database schema", "Return clear validation errors"],
    tests=["valid email passes", "missing @ fails", "empty input fails"],
)

print(packet)
```

The code is simple, but the habit is powerful: define what the agent is allowed to touch and how you will judge success.

## Today’s experiment 🧪

Choose one small feature in a project and write a context packet with:

1. One clear goal
2. Three relevant files
3. Three rules
4. Three tests

Give the packet to an AI coding assistant and compare the result with a vague prompt such as: “Add email validation.”

## Key lesson

Better context usually produces better code than a longer prompt.

**Context → Plan → Generate → Test → Review**

---

**Learn something. Build something. Repeat tomorrow. 🚀**

## Sources

- Atlassian announcement on agentic development workflows, September 2026
- General software engineering practice: requirements, testing, and code review
