# AirPrompter for Antigravity

Run your saved AirPrompter prompts and workflows from Antigravity.

## Install

```bash
agy plugin install https://github.com/airprompter/airprompter-antigravity-plugin
```

This one command adds AirPrompter to both the Antigravity app and the
agy command line.

## Sign in

- **Antigravity app:** open Customizations, select AirPrompter under
  Installed, and click **Set up authentication**.
- **agy command line:** type `/mcp`, select AirPrompter, and choose
  **Authenticate**.

Sign in to AirPrompter in the browser window that opens. Then start a new
conversation and ask it to list your AirPrompter workflows. The app and
the command line sign in separately, so sign in from each one you use.
Antigravity stores the token, not this plugin.

## Without the plugin

Add the same server to `~/.gemini/config/mcp_config.json`:

```json
{
  "mcpServers": {
    "airprompter": {
      "serverUrl": "https://mcp.airprompter.com/mcp"
    }
  }
}
```

The plugin adds the AirPrompter Skill on top of that, so Antigravity
reaches for AirPrompter when you mention a saved prompt or workflow
instead of answering from scratch.

## Coming from Gemini CLI

Google replaced Gemini CLI with Antigravity for free, Google AI Pro, and
Google AI Ultra accounts. Install this plugin in place of the AirPrompter
Gemini CLI extension.

## What this plugin contains

- `plugin.json` -- plugin name and description.
- `mcp_config.json` -- names the AirPrompter MCP server.
- `skills/airprompter/` -- routing rules for saved prompts and workflows.

No credential, client id, or customer identifier is packaged here.
