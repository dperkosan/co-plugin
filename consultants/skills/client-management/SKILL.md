# Client Management

This skill helps you manage clients in the consultants database. Use it to look up, add, update, or remove clients using natural language.

## Available Actions

Use the `consultants` MCP tools to fulfill any client-related request:

- **list_clients** — retrieve all clients; use this whenever the user asks to see, show, or list clients
- **get_client** — fetch a single client by ID; use when the user asks about a specific client
- **create_client** — add a new client; requires a name, description is optional
- **propose_client_update** — propose changes to a client; returns a diff and a React artifact
- **confirm_client_update** — apply a proposed update after user approval (requires proposal_token)
- **discard_client_update** — cancel a proposed update without applying (requires proposal_token)
- **delete_client** — remove a client by ID; always confirm with the user before deleting

## How to Respond

When listing clients, present the results as a clean table with columns: ID, Name, Description.

When creating a client, confirm success by showing the saved record.

## Updating Clients

To update a client, call **propose_client_update** with the client_id and all fields (including unchanged ones). The tool returns a diff and a React artifact.

When the response contains an `artifact` field, render it as a **React artifact** using the `artifact_title` as the title. This shows the user an interactive diff view with Approve, Reject, and Modify buttons.

Wait for the user to respond:

- **Approve**: call **confirm_client_update** with the proposal_token
- **Reject**: call **discard_client_update** with the proposal_token
- **Modify**: call **propose_client_update** again with adjusted values

## Deleting Clients

Show client details first and ask for explicit confirmation before calling delete_client.

If a client is not found, say so clearly and offer to list all clients so the user can find the right one.

## Triggers

This skill activates when the user mentions clients, customer records, or asks to manage, add, update, find, or remove a client.
