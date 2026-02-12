# Frappe Framework Agent Skills

Expert-level Frappe Framework knowledge for AI coding assistants—DocTypes, APIs, testing, and best practices.

## Why Frappe Agent Skills?

AI coding assistants are powerful, but they often:
- Generate outdated Frappe patterns (pre-v13, pre-Query Builder)
- Miss critical permission checks in API handlers
- Skip proper DocType controller patterns
- Ignore existing tooling in your project

These Agent Skills solve this by giving AI assistants expert-level Frappe knowledge in a format they can use.

## Available Skills

#### Core Skills
| Skill | Description |
|-------|-------------|
| `frappe-router` | Entry point—routes to appropriate skill based on task |
| `frappe-project-triage` | Detect project type, installed apps, version, and tooling |

#### Development Skills
| Skill | Description |
|-------|-------------|
| `frappe-app-development` | Scaffold and architect custom Frappe apps with hooks, background jobs, and service layers |
| `frappe-doctype-development` | Create and modify DocTypes, controllers, child tables |
| `frappe-api-development` | Build REST and RPC APIs with proper auth and permissions |

#### UI & Frontend Skills
| Skill | Description |
|-------|-------------|
| `frappe-desk-customization` | Customize Frappe Desk UI with form scripts, list views, and dialogs |
| `frappe-frontend-development` | Build modern Vue 3 frontend apps using Frappe UI |
| `frappe-ui-patterns` | UI/UX patterns derived from official Frappe apps (CRM, Helpdesk, HRMS) |
| `frappe-printing-templates` | Build print formats, email templates, and Jinja-based rendering |
| `frappe-reports` | Create Report Builder, Query Reports (SQL), and Script Reports (Python + JS) |
| `frappe-web-forms` | Build public-facing web forms for data collection |

#### Testing & Infrastructure
| Skill | Description |
|-------|-------------|
| `frappe-testing` | Write and run unit, integration, and UI tests |
| `frappe-manager` | Docker-based dev environments with Frappe Manager |

#### Patterns & Best Practices
| Skill | Description |
|-------|-------------|
| `frappe-enterprise-patterns` | Production patterns for CRM/Helpdesk-style apps |

## Installation

### Using Skills CLI (Recommended)

```bash
# Install all Frappe skills
npx skills add lubusIN/agent-skills --skills=frappe-*

# Or install specific Frappe skills
npx skills add lubusIN/agent-skills --skills=frappe-doctype-development,frappe-api-development
```

### Manual Installation

```bash
# Clone the parent repo
git clone https://github.com/lubusIN/agent-skills.git
cd agent-skills

# Copy Frappe skills to your AI assistant's skills directory
# Claude Code (global)
cp -r skills/frappe/frappe-* ~/.claude/skills/

# Cursor (global)
cp -r skills/frappe/frappe-* ~/.cursor/skills/

# Or into your project
cp -r skills/frappe/frappe-* /path/to/your-project/.claude/skills/
```

## How It Works

Each skill contains:

```
frappe-doctype-development/
├── SKILL.md              # Main instructions (when to use, procedure, verification)
└── references/           # Deep-dive docs on specific topics
    ├── doctypes.md
    ├── controllers.md
    └── ...
```

When you ask your AI assistant to work on Frappe code, it reads these skills and follows documented procedures rather than guessing.

### Skill Structure

Each SKILL.md follows a standard format:
- **When to use** — Trigger conditions for this skill
- **Inputs required** — What info the agent needs before starting
- **Procedure** — Step-by-step instructions
- **Verification** — Checklist to confirm success
- **Failure modes** — Common issues and fixes
- **Escalation** — When to consult docs or ask user

## Compatibility

- Frappe Framework v13+
- Works with ERPNext, HRMS, and custom apps
- Compatible with any AI assistant that supports Agent Skills

## Contributing

See the [main repository CONTRIBUTING.md](../../CONTRIBUTING.md) for guidelines on contributing to Frappe skills.

## License

MIT - See [LICENSE](../../LICENSE) in the root repository.
