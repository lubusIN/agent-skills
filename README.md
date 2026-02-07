# Agent Skills

Expert-level framework knowledge for AI coding assistants—best practices, patterns, and workflows for Frappe, Laravel, FilamentPHP, and more.

## Why Agent Skills?

AI coding assistants are powerful, but they often:
- Generate outdated framework patterns and anti-patterns
- Miss critical security checks (permissions, validation, authentication)
- Skip proper architectural patterns and conventions
- Ignore existing tooling and best practices in your project

Agent Skills solve this by giving AI assistants expert-level framework knowledge in a structured, discoverable format.

## Available Skills

### Frappe Framework

| Skill | Description |
|-------|-------------|
| `frappe-router` | Entry point—routes to appropriate skill based on task |
| `frappe-project-triage` | Detect project type, installed apps, version, and tooling |
| `frappe-doctype-development` | Create and modify DocTypes, controllers, child tables |
| `frappe-api-development` | Build REST and RPC APIs with proper auth and permissions |
| `frappe-testing` | Write and run unit, integration, and UI tests |
| `frappe-manager` | Docker-based dev environments with Frappe Manager |
| `frappe-enterprise-patterns` | Production patterns for CRM/Helpdesk-style apps |

[📖 View Frappe Skills Documentation](skills/frappe/README.md)

### Laravel (Coming Soon)

Laravel skills for routing, Eloquent ORM, middleware, authentication, and more.

### FilamentPHP (Coming Soon)

FilamentPHP skills for admin panels, resources, forms, tables, and custom pages.

## Quick Start

### Using Skills CLI (Recommended)

The easiest way to install is using the [Skills CLI](https://skills.sh):

```bash
# Install all skills from all frameworks
npx skills add lubusIN/agent-skills

# Install all Frappe skills
npx skills add lubusIN/agent-skills --skills=frappe-*

# Install specific skills from any framework
npx skills add lubusIN/agent-skills --skills=frappe-doctype-development,frappe-api-development

# Coming soon: Laravel and FilamentPHP skills
# npx skills add lubusIN/agent-skills --skills=laravel-*
# npx skills add lubusIN/agent-skills --skills=filament-*
```

The CLI automatically detects your AI assistant (Claude Code, Cursor, Codex, VS Code) and installs to the correct location.

### Manual Installation

If you prefer manual installation:

```bash
# Clone this repo
git clone https://github.com/lubusIN/agent-skills.git
cd agent-skills

# Copy all Frappe skills to your AI assistant's skills directory
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
skills/frappe/frappe-doctype-development/
├── SKILL.md              # Main instructions (when to use, procedure, verification)
└── references/           # Deep-dive docs on specific topics
    ├── doctypes.md
    ├── controllers.md
    └── ...
```

When you ask your AI assistant to work on framework code, it reads these skills and follows documented procedures rather than guessing.

### Skill Structure

Each SKILL.md follows a standard format:
- **When to use** — Trigger conditions for this skill
- **Inputs required** — What info the agent needs before starting
- **Procedure** — Step-by-step instructions
- **Verification** — Checklist to confirm success
- **Failure modes** — Common issues and fixes
- **Escalation** — When to consult docs or ask user

## Compatibility

### Frameworks
- **Frappe Framework** v13+ (ERPNext, HRMS, and custom apps)
- **Laravel** (Coming Soon)
- **FilamentPHP** (Coming Soon)

### AI Assistants
Compatible with any AI assistant that supports Agent Skills:
- Claude Code
- Cursor
- GitHub Copilot
- VS Code with compatible extensions

## Directory Structure

```
agent-skills/
├── README.md                                    # This file
├── skills/
│   ├── frappe/                                  # Frappe Framework skills
│   │   ├── README.md                            # Frappe-specific documentation
│   │   ├── frappe-router/
│   │   ├── frappe-project-triage/
│   │   ├── frappe-doctype-development/
│   │   ├── frappe-api-development/
│   │   ├── frappe-testing/
│   │   ├── frappe-manager/
│   │   ├── frappe-enterprise-patterns/
│   │   └── frappe-app-development/              # Legacy combined skill
│   ├── laravel/                                 # Coming soon
│   └── filamentphp/                             # Coming soon
├── CONTRIBUTING.md
└── LICENSE
```

## Contributing

Contributions welcome! To add or improve a skill:

1. Fork this repository
2. Create or modify skill in `skills/<framework>/<skill-name>/`
3. Ensure SKILL.md has all required sections
4. Test with your AI assistant
5. Submit a pull request

### Skill Authoring Guidelines

- Keep `SKILL.md` short and procedural
- Push detailed content into `references/`
- Include verification steps
- Document failure modes
- Link to official framework docs when appropriate

### Adding a New Framework

To add skills for a new framework (e.g., Django, Rails):

1. Create `skills/<framework>/` directory
2. Add `skills/<framework>/README.md` with framework-specific documentation
3. Create individual skill directories following the Agent Skills specification
4. Update the main README.md to list the new framework

## License

MIT

## Credits

- Inspired by [WordPress Agent Skills](https://github.com/WordPress/agent-skills)
- Built on the [Anthropic Agent Skills Specification](https://agentskills.io/)
- Maintained by [Lubus](https://github.com/lubusIN)
