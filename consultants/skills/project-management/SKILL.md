# Project Management

This skill helps you manage projects in the consultants database. Use it to look up, add, update, or remove projects using natural language.

## Available Actions

Use the `consultants` MCP tools to fulfill any project-related request:

- **list_projects** — retrieve all projects; use this whenever the user asks to see, show, or list projects
- **get_project** — fetch a single project by ID; use when the user asks about a specific project
- **create_project** — add a new project; requires a client_id and name, description and mode are optional
- **propose_project_update** — propose changes to a project; returns a diff of current vs proposed values
- **confirm_project_update** — apply a proposed update after user approval (requires proposal_token)
- **discard_project_update** — cancel a proposed update without applying (requires proposal_token)
- **delete_project** — remove a project by ID; always confirm with the user before deleting

## How to Respond

When listing projects, present the results as a clean table with columns: ID, Client ID, Name, Description, Mode.

When creating a project, confirm success by showing the saved record.

## Updating Projects

To update a project, call **propose_project_update** with the project_id and all fields (including unchanged ones). The tool returns a diff showing what will change.

Present the diff to the user as a table:

| Field | Current | Proposed |
|-------|---------|----------|
| description | old value | new value |

Then ask the user to Approve, Reject, or Modify.

- **Approve**: call **confirm_project_update** with the proposal_token
- **Reject**: call **discard_project_update** with the proposal_token
- **Modify**: call **propose_project_update** again with adjusted values

## Deleting Projects

Show project details first and ask for explicit confirmation before calling delete_project.

If a project is not found, say so clearly and offer to list all projects so the user can find the right one.

## Triggers

This skill activates when the user mentions projects, engagements, or asks to manage, add, update, find, or remove a project.
