# Daily Tech Drop — Project Zenith 🚀

## Project Zenith: A Windows PC Designed for Local AI

Microsoft is working on **Project Zenith**, a new Windows experience aimed at developer-class devices with large amounts of unified memory and high memory bandwidth.

The interesting part: Microsoft says systems with **64GB+ unified memory** can run AI models with **30B+ parameters locally**, without relying entirely on cloud inference.

### Why this matters

Running AI locally can mean:

- 🔒 Better privacy — data can stay on your machine
- ⚡ Lower latency — no network round trip for inference
- 💰 Potentially lower cloud/API costs
- 🧑‍💻 More freedom to experiment with local models

### Try It: Your First “Local AI” Experiment

You can start learning the idea with a tiny Python program that behaves like a local command-line assistant:

```python
while True:
    prompt = input("You: ")

    if prompt.lower() in ["exit", "quit"]:
        break

    print("AI: I received your prompt locally! 🤖")
```

This isn't an AI model yet — it's a starting point for understanding the local inference workflow.

### Challenge of the Day 🧪

Modify the program so it remembers the last **5 messages** using a Python list or JSON file.

Then try replacing the simple response with a locally running open-source model such as a small LLM.

### Bonus Tech Drop: GitHub Copilot Code Review

GitHub has also introduced the ability for **Copilot code review to approve pull requests** when enabled by repository administrators. This can make automated review part of a larger CI/CD workflow.

## Sources

- Microsoft Windows Developer Blog: Project Zenith
- GitHub Changelog: Copilot code review approvals

---

**Learn something. Build something. Repeat tomorrow. 🚀**
