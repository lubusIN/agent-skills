---
name: frappe-manager
description: Use Frappe Manager (FM) for Docker-based development and testing environments. Use when setting up local dev, running isolated tests, or managing agent-driven Frappe development workflows.
---

# Frappe Manager

Manage Docker-based Frappe development environments using Frappe Manager (FM).

## When to use

- Setting up a local Frappe development environment
- Creating isolated test environments
- Agent-driven development (vibe coding) workflows
- Quick prototyping without full bench setup
- Reproducible environments across machines

## Inputs required

- Docker installed and running
- Python 3.11+ with pipx
- Site/bench name
- Apps to install (frappe, erpnext, hrms, custom)
- Environment type (dev/prod)

## Procedure

### 0) Guardrails

- FM sites are Docker-based—ensure Docker daemon is running
- Each site runs isolated; changes don't affect host
- For production, use proper SSL and backup strategies
- FM is third-party (rtCamp), not official Frappe

### 1) Install Frappe Manager

```bash
# Install via pipx
pipx install frappe-manager

# Enable shell completion
fm --install-completion
```

### 2) Create a site

```bash
# Basic site (frappe only)
fm create mysite

# Site with ERPNext
fm create mysite --apps erpnext:version-15

# Site with multiple apps
fm create mysite --apps erpnext --apps hrms --environment dev

# Production site with SSL
fm create example.com --apps erpnext --env prod --ssl letsencrypt
```

### 3) Manage sites

```bash
# List all sites
fm list

# Start/stop site
fm start mysite
fm stop mysite

# View site info
fm info mysite

# View logs (follow)
fm logs mysite -f

# Delete site
fm delete mysite
```

### 4) Development workflow

```bash
# Access shell inside container
fm shell mysite

# Inside container - common commands:
bench new-app my_custom_app
bench --site mysite install-app my_custom_app
bench --site mysite migrate
bench build --app my_custom_app
bench --site mysite run-tests --app my_custom_app

# Exit shell
exit

# Open in VSCode
fm code mysite

# Open with debugger
fm code mysite --debugger
```

### 5) Agent-driven development

Perfect for AI agents developing Frappe apps:

```bash
# 1. Setup: Create fresh environment
fm create testsite --apps erpnext:version-15 --environment dev
fm start testsite

# 2. Develop: Enter shell, create app
fm shell testsite
bench new-app my_app
bench --site testsite install-app my_app
# ... make code changes ...
exit

# 3. Test: Run tests
fm shell testsite
bench --site testsite run-tests --app my_app
exit

# 4. Verify: Check logs
fm logs testsite -f

# 5. Reset if needed: Start fresh
fm stop testsite
fm delete testsite
fm create testsite --apps erpnext:version-15 --environment dev
```

### 6) Internal service management (fmx)

Inside the container, use `fmx` for service control:

```bash
fm shell mysite

fmx status      # Check service status
fmx restart     # Restart Frappe services
fmx start       # Start services
fmx stop        # Stop services
```

## Verification

- [ ] Site accessible at http://mysite.localhost
- [ ] Can login with admin credentials (default: admin/admin)
- [ ] Custom app installed and visible
- [ ] Tests run successfully inside container
- [ ] Logs show no critical errors

## Failure modes / debugging

- **Docker not running**: Start Docker daemon
- **Port conflict**: Use different site name or check port 80/443
- **Site not accessible**: Check `fm list` for status, try `fm start`
- **App not installing**: Check `fm logs` for errors
- **Slow startup**: First run downloads images—be patient

## Escalation

- For advanced Docker config, see [references/docker-config.md](references/docker-config.md)
- For SSL issues, see [references/ssl-setup.md](references/ssl-setup.md)
- For bench commands, see [references/bench-commands.md](references/bench-commands.md)

## References

- [references/fm-commands.md](references/fm-commands.md) - Full FM command reference
- [references/agent-workflow.md](references/agent-workflow.md) - Agent development patterns
- [references/bench-commands.md](references/bench-commands.md) - Bench CLI inside container
- https://github.com/rtCamp/Frappe-Manager
