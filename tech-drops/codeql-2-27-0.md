# Daily Tech Drop — CodeQL 2.27.0 🚀

## Make Security Scanning Smarter with CodeQL

GitHub released **CodeQL 2.27.0 on September 9, 2026**. The update adds native Linux ARM64 support, a new Rust command-line-injection query, expanded Java/Kotlin and C# framework coverage, and other accuracy improvements.

### Why this matters

Security bugs are often easier to fix when you catch them during development instead of after deployment. CodeQL scans source code like data and asks questions such as:

- Can user input reach a dangerous command?
- Can untrusted data reach a SQL query?
- Is a secret or cryptographic value hard-coded?

This is called **static analysis**: checking code without running the application.

### A simple security pattern: validate before use

```python
import shlex
import subprocess


def list_files(folder: str) -> str:
    # Keep the command structure fixed and pass the folder as one argument.
    safe_folder = shlex.quote(folder)
    result = subprocess.run(
        ["ls", "-la", safe_folder],
        capture_output=True,
        text=True,
        check=True,
    )
    return result.stdout


print(list_files("."))
```

The important idea is not the `ls` command. It is avoiding unsafe string concatenation such as:

```python
# Avoid this pattern with untrusted input:
# subprocess.run("ls -la " + folder, shell=True)
```

When user input becomes part of a shell command, attackers may inject extra commands.

### Today’s experiment 🧪

Create a small Python script that accepts a filename from the user and reads it safely.

Then test three cases:

1. A normal filename.
2. A filename containing spaces.
3. A path such as `../../secret.txt`.

Add validation so the script only reads files inside a specific `documents/` folder.

### Key lesson

AI can help write code quickly, but security tools help answer a different question: **Can this code be misused?** Learn to combine both—generate faster, then scan and test before shipping.

## Source

- GitHub Changelog: CodeQL 2.27.0 adds support for Linux ARM64 (September 9, 2026)

---

**Learn something. Check something. Build something safer. 🚀**
