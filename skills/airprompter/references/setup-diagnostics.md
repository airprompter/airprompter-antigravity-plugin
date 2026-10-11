# Setup Diagnostics

Use this reference when AirPrompter tools are missing, or when the user asks
to diagnose, repair, reconnect, or reinstall AirPrompter in Antigravity.

## Readiness Layers

Treat the plugin, MCP server registration, OAuth session, and current
Antigravity session as separate states. An installed plugin does not by
itself prove that OAuth completed or that the current session has refreshed
its tool inventory.

1. Run `agy plugin list` in the shell and confirm the AirPrompter plugin is
   installed and enabled.
2. Confirm the plugin's `mcp_config.json` names `airprompter`
   with `serverUrl` `https://mcp.airprompter.com/mcp`.
3. Sign in. Antigravity does not open the sign-in by itself:
   - Antigravity app: Customizations > Installed > AirPrompter, then
     Set up authentication (or the MCP tab's Authenticate button).
   - agy CLI: type `/mcp`, select the AirPrompter server, choose
     Authenticate.
   Finish the AirPrompter sign-in in the browser. If the browser shows a
   code to paste, paste it back into Antigravity.
4. Start a new conversation after signing in so it loads the AirPrompter
   tools. The app's MCP tab shows how many tools are enabled.
5. Run `diagnose_connection` before executing a saved workflow. Tool
   discovery alone does not prove the authenticated account is ready.

The Antigravity app and the `agy` CLI keep separate sign-ins. Signing in
from one does not sign in the other; authenticate in the one that reports
AirPrompter as unauthorized ("Setup required" or "Auth Needed").

## Customer Installation

Install the plugin from its public GitHub repository:

```bash
agy plugin install https://github.com/airprompter/airprompter-antigravity-plugin
```

The command installs the plugin for both the Antigravity app and the agy
CLI. Antigravity discovers AirPrompter OAuth from the remote MCP server.
Do not ask customers to paste a token, add a client id, add an `oauth`
block, or register a second server.

## Manual MCP Fallback

If the user explicitly wants the MCP connection without the plugin's Skill,
add the same server to `~/.gemini/config/mcp_config.json`:

```json
{
  "mcpServers": {
    "airprompter": {
      "serverUrl": "https://mcp.airprompter.com/mcp"
    }
  }
}
```

Use `serverUrl`; Antigravity does not accept `url` or `httpUrl` for remote
servers. Never print or request the token stored by Antigravity.

## Gemini CLI

Gemini CLI no longer serves free, Google AI Pro, or Google AI Ultra
accounts. Customers coming from the AirPrompter Gemini CLI extension should
install this plugin instead.
