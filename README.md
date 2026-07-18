# Lampyre MCP setup

This repo ships a project-scoped MCP configuration (`.mcp.json`) that connects
Claude Code to the Lampyre API through the [`mcp-remote`](https://www.npmjs.com/package/mcp-remote)
stdio bridge (requires Node.js/`npx`).

The Lampyre endpoint is `https://account.lampyre.io/api/v2/mcp`; `mcp-remote`
proxies it as a local stdio server and passes your API token via the
`Authorization` header. The `Authorization:${AUTH_HEADER}` form (no space
after the colon) is intentional — it works around argument-splitting issues
with header values that contain spaces.

## Setup

The config expects your Lampyre API token in the `LAMPYRE_TOKEN` environment
variable — the token itself is never committed to the repo.

1. Get your API token (`lpr_...`) from your [Lampyre account](https://account.lampyre.io).
2. Export it before starting Claude Code:

   ```sh
   export LAMPYRE_TOKEN=lpr_your_token_here
   ```

   For Claude Code on the web, set `LAMPYRE_TOKEN` as a secret in your
   environment settings instead.

3. Start Claude Code in this project. Approve the `lampyre` server when
   prompted, then verify with:

   ```sh
   claude mcp list
   ```

   It should report the `lampyre` server as Connected.
