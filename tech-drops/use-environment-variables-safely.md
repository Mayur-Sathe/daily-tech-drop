# Daily Tech Drop — Use Environment Variables for Configuration 🔐

A common beginner mistake is putting API keys, database passwords, or device settings directly inside source code. A safer technique is to keep configuration in **environment variables**.

This gives you two benefits:

- secrets stay out of your Git history
- the same code can run in development, testing, and production with different settings

## Small code example

```python
import os

API_URL = os.getenv("API_URL", "http://localhost:8000")
DEBUG = os.getenv("DEBUG", "false").lower() == "true"

print("API URL:", API_URL)
print("Debug mode:", DEBUG)
```

Set the values before running the program:

```bash
export API_URL="https://api.example.com"
export DEBUG="true"
python app.py
```

On Windows PowerShell:

```powershell
$env:API_URL = "https://api.example.com"
$env:DEBUG = "true"
python app.py
```

## Why this matters

The same idea is used in web apps, CI/CD pipelines, cloud deployments, and IoT systems. For a project such as an ESP32 dashboard, you can keep server addresses and feature settings outside the code so the program is easier to reuse.

Never commit real secrets. Add files such as `.env` to `.gitignore` when using a local dotenv workflow.

## Today’s experiment 🧪

1. Add a `PORT` environment variable.
2. Convert it from text into an integer.
3. Provide a fallback value such as `8000`.
4. Print a helpful message when the value is invalid.

Bonus challenge: create a small `.env.example` file containing placeholder names only:

```text
API_URL=
DEBUG=false
PORT=8000
```

## Beginner takeaway

Keep **code** and **configuration** separate:

**Write once → Configure per environment → Avoid hard-coded secrets**
