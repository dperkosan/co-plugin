# Project Management

This skill helps you manage projects in the consultants database. Use it to look up, add, update, or remove projects using natural language.

## Available Actions

Use the `consultants` MCP tools to fulfill any project-related request:

- **list_projects** — retrieve all projects; use this whenever the user asks to see, show, or list projects
- **get_project** — fetch a single project by ID; use when the user asks about a specific project
- **create_project** — add a new project; requires a client_id and name, description and mode are optional
- **update_project** — update an existing project; always fetch the project first to confirm it exists
- **delete_project** — remove a project by ID; always confirm with the user before deleting

## How to Respond

When listing projects, present the results as a clean table with columns: ID, Client ID, Name, Description, Mode.

When creating or updating a project, confirm success by showing the saved record.

When the user asks to delete a project, show the project details first and ask for explicit confirmation before calling delete_project.

If a project is not found, say so clearly and offer to list all projects so the user can find the right one.

## Triggers

This skill activates when the user mentions projects, engagements, or asks to manage, add, update, find, or remove a project.
