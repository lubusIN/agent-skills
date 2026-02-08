---
name: frappe-router
description: Route to the appropriate Frappe skill based on task type. Use as the entry point when working on Frappe projects to determine which specialized skill to apply.
---

# Frappe Router

Route to the appropriate Frappe skill based on your task.

## When to use

- First step when starting any Frappe-related work
- To determine which specialized skill applies to your task

## Procedure

### 1) Identify task type

| Task | Skill |
|------|-------|
| Understand project structure, versions, apps | → `frappe-project-triage` |
| Scaffold new app, hooks, architecture, background jobs | → `frappe-app-development` |
| Create/modify DocTypes, fields, controllers | → `frappe-doctype-development` |
| Build REST/RPC APIs, webhooks, integrations | → `frappe-api-development` |
| Customize Desk UI, form scripts, list views, JS API | → `frappe-desk-customization` |
| Build Vue 3 frontends with Frappe UI, portals | → `frappe-frontend-development` |
| Create print formats, email templates, Jinja, PDFs | → `frappe-printing-templates` |
| Build reports (Builder, Query, Script) | → `frappe-reports` |
| Create public web forms for data collection | → `frappe-web-forms` |
| Write or run tests | → `frappe-testing` |
| Set up dev environment with Docker/FM | → `frappe-manager` |
| Build CRM/Helpdesk/enterprise systems | → `frappe-enterprise-patterns` |

### 2) Run triage first (recommended)

Before deep work, run `frappe-project-triage` to understand:
- Project type (bench/FM/standalone)
- Frappe version
- Installed apps
- Available tooling

### 3) Combine skills as needed

Complex tasks may require multiple skills:
- New app = `frappe-app-development` + `frappe-doctype-development` + `frappe-api-development` + `frappe-testing`
- Feature with UI = `frappe-doctype-development` + `frappe-desk-customization` + `frappe-api-development`
- Custom frontend = `frappe-frontend-development` + `frappe-api-development`
- Document workflow = `frappe-doctype-development` + `frappe-printing-templates` + `frappe-reports`
- Enterprise app = `frappe-enterprise-patterns` + `frappe-doctype-development`

## Quick decision tree

```
Is this about understanding the project?
  → frappe-project-triage

Is this about creating a new app or app architecture?
  → frappe-app-development

Is this about data models or DocTypes?
  → frappe-doctype-development

Is this about APIs or external access?
  → frappe-api-development

Is this about Desk UI, form scripts, or client-side JS?
  → frappe-desk-customization

Is this about a Vue 3 frontend or portal?
  → frappe-frontend-development

Is this about print formats, PDFs, or Jinja templates?
  → frappe-printing-templates

Is this about reports or data analysis views?
  → frappe-reports

Is this about public web forms?
  → frappe-web-forms

Is this about testing?
  → frappe-testing

Is this about local dev environment?
  → frappe-manager

Is this a complex enterprise system?
  → frappe-enterprise-patterns
```
