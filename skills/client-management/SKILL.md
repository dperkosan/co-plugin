# Client Management

This skill helps you manage clients in the consultants database. Use it to look up, add, update, or remove clients using natural language.

## Available Actions

Use the `consultants` MCP tools to fulfill any client-related request:

- **list_clients** — retrieve all clients; use this whenever the user asks to see, show, or list clients
- **get_client** — fetch a single client by ID; use when the user asks about a specific client
- **create_client** — add a new client; requires a name, description is optional
- **update_client** — update an existing client's name or description; always fetch the client first to confirm it exists
- **delete_client** — remove a client by ID; always confirm with the user before deleting

## How to Respond

When listing clients, present the results as a clean table with columns: ID, Name, Description.

When creating or updating a client, confirm success by showing the saved record.

When the user asks to delete a client, show the client details first and ask for explicit confirmation before calling delete_client.

If a client is not found, say so clearly and offer to list all clients so the user can find the right one.

## Triggers

This skill activates when the user mentions clients, customer records, or asks to manage, add, update, find, or remove a client.
