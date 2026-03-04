---
description: Add a new client to the consultants database
argument-hint: <client name>
disable-model-invocation: true
---

# /add-client — Add New Client

Add a new client to the consultants database using the consultants MCP tools.

## Workflow

### Step 1: Gather Client Information

Collect the following from the user:

1. **Client name** (required): The official name of the client organization
2. **Description** (optional): A brief description of the client, their industry, and the engagement

If a client name was provided as an argument ($ARGUMENTS), use it. Otherwise, ask for it.

### Step 2: Create the Client

Use the `create_client` MCP tool to add the client with the provided information.

### Step 3: Confirm

Display the created client as a table with columns: ID, Name, Description.
