# Project Management

This skill helps you manage projects in the consultants database. Use it to look up, add, update, or remove projects using natural language.

## Available Actions

Use the `consultants` MCP tools to fulfill any project-related request:

- **list_projects** — retrieve all projects; use this whenever the user asks to see, show, or list projects
- **get_project** — fetch a single project by ID; use when the user asks about a specific project
- **create_project** — add a new project; requires a client_id and name, description and mode are optional
- **update_project** — update an existing project; always fetch the project first and follow the Update Workflow below
- **delete_project** — remove a project by ID; always confirm with the user before deleting

## How to Respond

When listing projects, present the results as a clean table with columns: ID, Client ID, Name, Description, Mode.

When creating a project, confirm success by showing the saved record.

## Update Workflow

When the user wants to update any field on a project, follow these steps exactly:

1. Fetch the current project using get_project
2. Show the proposed changes in this exact format:

```
📝 Update Project: [project name]

Field        | Current                | Proposed
-------------|------------------------|------------------------
description  | [current value]        | [proposed value]

What would you like to do?
1. Approve
2. Reject
3. Modify (tell me what to change)
```

Only include fields that are actually changing. Do NOT call update_project until the user explicitly approves. If the user picks "Modify", apply their changes and show the comparison again.

When the user asks to delete a project, show the project details first and ask for explicit confirmation before calling delete_project.

If a project is not found, say so clearly and offer to list all projects so the user can find the right one.

## Triggers

This skill activates when the user mentions projects, engagements, or asks to manage, add, update, find, or remove a project.
