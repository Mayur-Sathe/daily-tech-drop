# Daily Tech Drop — Spec-Driven Development 🚀

## Write the Requirement Before the Code

A practical trend in modern AI-assisted development is **spec-driven development**: instead of jumping straight into implementation, you first write a small, testable specification.

This is useful whether you code manually or use an AI coding assistant. A clear spec reduces vague prompts, prevents missing edge cases, and makes code review easier.

### A simple format

Write requirements like this:

> **When** a user submits a valid email, **the system shall** save it and show a success message.

> **When** the email is invalid, **the system shall** reject it and show an error.

These statements are simple, but they already describe behavior that can become tests.

### Try It in Python

```python
import re


def validate_email(email: str) -> bool:
    pattern = r"^[^@\\s]+@[^@\\s]+\\.[^@\\s]+$"
    return re.match(pattern, email) is not None


# Examples derived from the specification
assert validate_email("mayur@example.com") is True
assert validate_email("not-an-email") is False
```

The important idea is not the regular expression. It is that the **requirements and tests agree before the feature is built**.

### Why it matters

- Fewer misunderstandings between people and AI tools
- Easier debugging because expected behavior is explicit
- Better tests and cleaner code reviews
- Requirements can become documentation automatically

### Challenge of the Day 🧪

Create a tiny to-do list app and write 5 requirements before coding. For example:

1. An empty task cannot be added.
2. A valid task appears in the list.
3. Completed tasks are marked clearly.
4. Duplicate tasks are rejected.
5. A task can be deleted.

Then ask an AI coding assistant to implement **one requirement at a time** and write a test for each one.

### Key Lesson

AI can generate code quickly, but a precise specification tells it **what “correct” means**.

## Sources

- Recent developer tooling discussions increasingly emphasize structured, spec-first workflows for AI-assisted coding.
- AWS Kiro is one current example of a tool built around requirements, design, and implementation planning before code generation.

---

**Learn something. Build something. Repeat tomorrow. 🚀**
