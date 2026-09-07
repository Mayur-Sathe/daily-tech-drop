# Daily Tech Drop — Agent Relay 🚀

## What if an AI coding agent could work inside your own network?

A new idea is emerging in developer infrastructure: let cloud-based coding agents plan and reason, but run their actual tool calls inside infrastructure you control.

Coder recently announced **Agent Relay**, a self-hosted execution layer designed to let cloud coding agents operate inside customer-managed environments. The useful concept is **separating the brain from the hands**:

- The agent can plan in the cloud.
- Code, secrets, databases, and internal services stay behind your network boundary.
- The execution layer can apply your own permissions, logging, and policies.

That pattern is valuable beyond AI coding. It can be used for support bots, finance workflows, internal automation, and business tools where data cannot freely leave the company.

### Tiny experiment: separate planning from execution

This toy example models the architecture with two functions: one creates a plan, and another executes only allowed actions.

```python
ALLOWED_ACTIONS = {"read_file", "run_tests"}


def plan(task):
    # Imagine this came from a cloud AI agent.
    return [
        ("read_file", "app.py"),
        ("run_tests", "pytest -q"),
        ("delete_file", "app.py"),  # blocked by policy
    ]


def execute(actions):
    for action, target in actions:
        if action not in ALLOWED_ACTIONS:
            print(f"BLOCKED: {action} -> {target}")
            continue
        print(f"EXECUTE: {action} -> {target}")

execute(plan("check the project"))
```

### Why this is a strong portfolio project

Build a small **Safe Agent Runner** with FastAPI:

1. Accept a task.
2. Generate a plan.
3. Validate each action against an allow-list.
4. Run it in a sandbox.
5. Store an audit log.

That is a practical bridge between AI, backend development, cybersecurity, and business automation.

### Challenge of the day 🧪

Add:

- a JSON policy file,
- user roles such as `viewer` and `developer`,
- a dry-run mode,
- and a log showing who approved each action.

## Ready-to-publish social post

> AI agents should not need unlimited access to your entire company.
>
> A powerful architecture is to separate the agent’s “brain” from its “hands”:
>
> - the model plans,
> - your infrastructure executes,
> - your policies decide what is allowed.
>
> I recreated the idea with a tiny Python experiment that blocks unsafe actions before execution. Next step: turn it into a FastAPI service with role-based permissions, sandboxing, and audit logs.
>
> This could become a real product for small businesses that want AI automation without exposing all their data to the cloud.
>
> #AI #Python #CyberSecurity #FastAPI #Automation #BuildInPublic

## Source

- Coder announcement on Agent Relay, September 2, 2026

---

**Build systems that are useful, safe, and easy to explain. 🚀**
