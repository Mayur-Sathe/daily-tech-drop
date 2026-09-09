# Daily Tech Drop — Gemini 3.8 Flash in GitHub Copilot 🚀

GitHub announced that **Gemini 3.8 Flash** is now available in GitHub Copilot. GitHub says the model performed strongly in early testing on complex terminal-based coding tasks, especially when validating work and recovering from actionable failures. citeturn758408search6

## Why this matters

A model picker is becoming like choosing the right tool for a job:

- Use a fast model for quick explanations and small edits.
- Try a stronger model for multi-file changes or debugging.
- Compare outputs instead of assuming the first answer is correct.

GitHub says Gemini 3.8 Flash is rolling out across VS Code, Visual Studio, Copilot CLI, JetBrains IDEs, Xcode, Eclipse, and other Copilot surfaces. Availability may appear gradually depending on your plan and account. citeturn758408search6

## Try this technique: validate generated code

Instead of asking an AI tool only to write code, ask it to generate code **and a test**.

```python

def slugify(text: str) -> str:
    """Convert text into a simple URL-friendly slug."""
    return "-".join(text.lower().strip().split())


assert slugify("  Learn Python Today  ") == "learn-python-today"
assert slugify("GitHub Copilot") == "github-copilot"
```

The `assert` statements act as tiny safety checks. If a future change breaks the behavior, Python immediately shows you that something is wrong.

## Today’s experiment 🧪

Create a small function for one of these tasks:

1. Remove duplicate values from a list while preserving order.
2. Check whether a password contains uppercase, lowercase, digits, and symbols.
3. Convert a sentence into a filename-safe string.

Then ask your coding assistant to:

- explain the code,
- write three tests,
- find one edge case,
- improve the implementation.

## Key lesson

The most useful AI coding habit is not “generate more code.” It is **generate, test, review, and then improve**.

### Source

- [GitHub Changelog — Gemini 3.8 Flash is now available in GitHub Copilot](https://github.blog/changelog/2026-09-03-gemini-3-8-flash-is-now-available-in-github-copilot/)

---

**Learn something. Build something. Verify everything. 🚀**
