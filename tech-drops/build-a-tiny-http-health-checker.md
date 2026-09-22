# Daily Tech Drop — Build a Tiny HTTP Health Checker 🩺

A simple but powerful production habit is to give every service a **health check**. Monitoring tools can call it to answer one basic question: “Is this service alive and responding?”

This idea is useful for web apps, APIs, IoT dashboards, and deployment pipelines. A health endpoint should be fast, predictable, and avoid exposing sensitive information.

## Small code example

```python
from http.server import BaseHTTPRequestHandler, HTTPServer
import json


class HealthHandler(BaseHTTPRequestHandler):
    def do_GET(self):
        if self.path == "/health":
            body = json.dumps({"status": "ok"}).encode()

            self.send_response(200)
            self.send_header("Content-Type", "application/json")
            self.send_header("Content-Length", str(len(body)))
            self.end_headers()
            self.wfile.write(body)
        else:
            self.send_response(404)
            self.end_headers()


server = HTTPServer(("localhost", 8000), HealthHandler)
print("Health server running on http://localhost:8000/health")
server.serve_forever()
```

Run it, then open `http://localhost:8000/health` in your browser. You should see:

```json
{"status": "ok"}
```

## Why this matters

A health check can help you:

- detect whether an app is running
- verify a deployment succeeded
- monitor an ESP32 or local dashboard backend
- let load balancers remove unhealthy instances
- create a simple first step toward observability

## Today’s experiment 🧪

Extend the endpoint with two checks:

1. `/health` — only confirms the process is alive.
2. `/ready` — confirms the app is ready to serve traffic.

Then add a small `uptime_seconds` value using `time.monotonic()`.

Bonus challenge: write a tiny Python client using `urllib.request` that calls the endpoint and prints `Healthy` only when the response code is 200.

## Beginner takeaway

Reliable systems are built from small, observable pieces:

**Run → Check → Report → React**

A tiny health endpoint is one of the easiest ways to start thinking like a backend and DevOps engineer.
