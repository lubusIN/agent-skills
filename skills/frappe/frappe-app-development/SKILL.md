---
name: frappe-app-development
description: Legacy combined skill for Frappe development. Prefer using specialized skills instead (frappe-router, frappe-doctype-development, frappe-api-development, etc.).
---

# Frappe App Development (Legacy)

> [!NOTE]
> This skill has been split into smaller, composable skills for better modularity.
> Use `frappe-router` to route to the appropriate specialized skill.

## Available Skills

| Skill | Purpose |
|-------|---------|
| `frappe-router` | Entry point—routes to appropriate skill |
| `frappe-project-triage` | Detect project type, apps, version |
| `frappe-doctype-development` | Create/modify DocTypes |
| `frappe-api-development` | Build REST/RPC APIs |
| `frappe-testing` | Write and run tests |
| `frappe-manager` | Docker-based dev environments |
| `frappe-enterprise-patterns` | CRM/Helpdesk architecture |

## Quick Start

1. Run `frappe-project-triage` to understand the project
2. Use `frappe-router` to select the right skill for your task
3. Follow the procedural steps in that skill

## References

This skill's `references/` directory contains detailed documentation that the specialized skills link to. These files are preserved for backward compatibility and shared reference.
