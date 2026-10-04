# Nium MCP Server

Build, test, and integrate with Nium using natural language.

The Nium MCP Server connects your AI coding agent directly to Nium's APIs, documentation, guides, and sandbox environment. Ask questions, generate production-ready integration code, troubleshoot errors, and execute sandbox workflows — without leaving your editor.

> **Current Scope:** The Nium MCP Server is optimized for sandbox development and integration testing, enabling you to safely build and validate your workflows before production deployment.

---

## Supported Features

* 📚 **Documentation Search** — Search Nium documentation, API references, guides, and integration resources.
* 🔍 **API Discovery** — Find APIs, endpoints, parameters, and implementation requirements using natural language.
* 💻 **Code Generation** — Generate integration code, SDK examples, and implementation snippets in multiple programming languages.
* 🚀 **Sandbox Actions** — Execute supported Nium Sandbox workflows directly from your AI assistant.
* 🛠️ **Integration Assistant** — Build end-to-end payment, payout, virtual account, card, and onboarding workflows.
* 🔄 **Error Resolution** — Understand API errors, validation requirements, and troubleshooting steps.
* 🌍 **Solution Discovery** — Explore Nium products and identify the right APIs for your use case.
* 🤖 **AI-Native Development** — Enable AI coding agents to build production-ready applications on top of Nium.

---

## What Can You Build?

The Nium MCP Server helps developers build applications for:

* Global Payouts
* Global Payroll
* Supplier Payments
* Travel Payments
* Virtual Cards
* Virtual Accounts
* Merchant Settlements
* Cross-Border Money Movement
* Treasury & Wallet Solutions

---

## Installation Guide

> **Before you start:** Get your API key from the [Nium Portal](https://app.nium.com) under **Settings → API Keys** (sandbox access is instant). Replace `YOUR_NIUM_API_KEY` in the configs below with it. Live API calls require the `x-api-key` header on the MCP HTTP request.
>
> After using a one-click **Install** button, replace the `YOUR_NIUM_API_KEY` placeholder in the generated server entry with your key.

### Quick Install

[![Install in Cursor](https://img.shields.io/badge/Install-Nium_MCP_Cursor-00A67E?style=for-the-badge)](https://cursor.com/en/install-mcp?name=Nium_Sandbox&config=eyJ1cmwiOiJodHRwczovL21jcC1zYW5kYm94Lm5pdW0uY29tL21jcCIsImhlYWRlcnMiOnsieC1hcGkta2V5IjoiWU9VUl9OSVVNX0FQSV9LRVkifX0%3D)
[![Install in VS Code](https://img.shields.io/badge/Install-Nium_MCP_VSCode-0078D4?style=for-the-badge)](https://insiders.vscode.dev/redirect/mcp/install?name=Nium_Sandbox&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp-sandbox.nium.com%2Fmcp%22%2C%22headers%22%3A%7B%22x-api-key%22%3A%22YOUR_NIUM_API_KEY%22%7D%7D)

---

### Cursor

[![Install Now](https://img.shields.io/badge/Install_Now-Cursor-00A67E?style=flat-square&logo=cursor)](https://cursor.com/en/install-mcp?name=Nium_Sandbox&config=eyJ1cmwiOiJodHRwczovL21jcC1zYW5kYm94Lm5pdW0uY29tL21jcCIsImhlYWRlcnMiOnsieC1hcGkta2V5IjoiWU9VUl9OSVVNX0FQSV9LRVkifX0%3D)

**Files:** Project `.cursor/mcp.json`, or global `~/.cursor/mcp.json`

**UI:** Cursor Settings → Tools & MCP → add a new MCP server, then paste JSON.

Put the API key in `env` and reference it from `headers`:

```json
{
  "mcpServers": {
    "nium": {
      "url": "https://mcp-sandbox.nium.com/mcp",
      "headers": {
        "x-api-key": "${env:NIUM_API_KEY}"
      },
      "env": {
        "NIUM_API_KEY": "YOUR_NIUM_API_KEY"
      }
    }
  }
}
```

---

### Claude Desktop

**File:**

- macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
- Windows: `%APPDATA%\Claude\claude_desktop_config.json`

**UI:** Settings → Developer → Edit Config. Fully quit and relaunch after saving.

Remote HTTP is not a native `url` entry in this file (Claude Desktop may strip it). Bridge with `mcp-remote` or add a **custom connector** under Settings → Connectors.

```json
{
  "mcpServers": {
    "Nium_Sandbox": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://mcp-sandbox.nium.com/mcp",
        "--header",
        "x-api-key:${NIUM_API_KEY}"
      ],
      "env": {
        "NIUM_API_KEY": "YOUR_NIUM_API_KEY"
      }
    }
  }
}
```

⚠️ Keep `x-api-key:${NIUM_API_KEY}` with **no space around `:`**. Put the key (and any spaces) in `env`.

---

### Claude Code

**Files:** Project `.mcp.json`, or user `~/.claude.json` under top-level `mcpServers`

**CLI:**

```bash
claude mcp add-json nium '{"type":"http","url":"https://mcp-sandbox.nium.com/mcp","headers":{"x-api-key":"${NIUM_API_KEY}"},"env":{"NIUM_API_KEY":"YOUR_NIUM_API_KEY"}}'
```

**Project `.mcp.json`:**

```json
{
  "mcpServers": {
    "Nium_Sandbox": {
      "type": "http",
      "url": "https://mcp-sandbox.nium.com/mcp",
      "headers": {
        "x-api-key": "${NIUM_API_KEY}"
      },
      "env": {
        "NIUM_API_KEY": "YOUR_NIUM_API_KEY"
      }
    }
  }
}
```

> `"type": "streamable-http"` is accepted as an alias for `"http"`. Entries with `url` but no `type` are treated as stdio and skipped.

---

### VS Code

[![Install Now](https://img.shields.io/badge/Install_Now-VS_Code-0078D4?style=flat-square&logo=visualstudiocode)](https://insiders.vscode.dev/redirect/mcp/install?name=Nium_Sandbox&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp-sandbox.nium.com%2Fmcp%22%2C%22headers%22%3A%7B%22x-api-key%22%3A%22YOUR_NIUM_API_KEY%22%7D%7D)

After clicking, VS Code asks you to confirm the install. Then run **MCP: Open User Configuration** from the Command Palette and replace `YOUR_NIUM_API_KEY` in the `headers` section with your API key.

**Or configure manually** — add to `.vscode/mcp.json` in your workspace:

```json
{
  "servers": {
    "nium": {
      "url": "https://mcp-sandbox.nium.com/mcp",
      "type": "http",
      "url": "https://mcp-sandbox.nium.com/mcp",
      "headers": {
        "x-api-key": "${env:NIUM_API_KEY}"
      }
    }
  }
}
```

Set `NIUM_API_KEY` in your shell environment or in a `.env` file at the workspace root.

---

### Antigravity

Add to your Antigravity workspace settings or config file, then restart Antigravity or reload the workspace:

```json
{
  "mcpServers": {
    "Nium_Sandbox": {
      "url": "https://mcp-sandbox.nium.com/mcp",
      "headers": {
        "x-api-key": "${env:NIUM_API_KEY}"
      }
    }
  }
}
```

Set `NIUM_API_KEY` in your environment, or replace the header value with your key directly.

---

### Codex

**File:** `~/.codex/config.toml` (or trusted-project `.codex/config.toml`)

Codex uses **TOML**, not JSON. Read the key from the environment at request time:

```toml
[mcp_servers.nium]
url = "https://mcp-sandbox.nium.com/mcp"
env_http_headers = { "x-api-key" = "NIUM_API_KEY" }

[mcp_servers.Nium_Sandbox.env]
NIUM_API_KEY = "YOUR_NIUM_API_KEY"
```

> The top-level key is `mcp_servers` (snake_case), not `mcpServers`.

**CLI:**

```bash
codex mcp add nium --url https://mcp-sandbox.nium.com/mcp
```

Then manually add `env_http_headers` and the `[mcp_servers.Nium_Sandbox.env]` entry to `config.toml`.

---

### ChatGPT (Developer Mode)

ChatGPT does not load a project `mcp.json`. Use a remote Streamable HTTP URL.

**Setup:**

1. Settings → Connectors / Apps → enable **Developer mode** (workspace admins may need to allow this)
2. Create a custom connector / app
3. MCP server URL: `https://mcp-sandbox.nium.com/mcp`
4. Authentication: custom header — name `x-api-key`, value `YOUR_NIUM_API_KEY`
   - If the UI only supports OAuth or Bearer, ChatGPT cannot send Nium's `x-api-key` as expected
5. Scan tools, then enable the connector in chat

> ChatGPT does not support an `env` field for custom connector headers, so store credentials securely outside of JSON configuration.

---

### Gemini CLI

**Files:** `~/.gemini/settings.json`, or project `.gemini/settings.json`

Put the API key in `env` and reference it from `headers`. Gemini expands `$NIUM_API_KEY` / `${NIUM_API_KEY}` (and `%NIUM_API_KEY%` on Windows):

```json
{
  "mcpServers": {
    "nium": {
      "httpUrl": "https://mcp-sandbox.nium.com/mcp",
      "headers": {
        "x-api-key": "$NIUM_API_KEY"
      },
      "env": {
        "NIUM_API_KEY": "YOUR_NIUM_API_KEY"
      }
    }
  }
}
```

> Use `httpUrl` for Streamable HTTP. `url` is for SSE — use `httpUrl` for this server.

---

### Any other MCP client

If your client supports Streamable HTTP servers, use:

| Setting | Value |
|---|---|
| Nium MCP Server URL | `https://mcp-sandbox.nium.com/mcp` |
| Header name | `x-api-key` |
| Header value | your Nium API key |

If your client only supports stdio, use `mcp-remote` as a proxy (see the Claude Desktop section).

---

### Configuration Reference

| Client | Config File | HTTP Field | API Key Header |
|---|---|---|---|
| **Cursor** | `.cursor/mcp.json` | `url` + `headers` + `env` | `"x-api-key"` |
| **Claude Desktop** | `claude_desktop_config.json` | `npx mcp-remote` + `--header` + `env` | `x-api-key:${NIUM_API_KEY}` |
| **Claude Code** | `.mcp.json` | `"type": "http"`, `url`, `headers` + `env` | `"x-api-key"` |
| **VS Code** | `.vscode/mcp.json` | `servers` → `"type": "http"`, `url` + `headers` | `"x-api-key"` |
| **Antigravity** | workspace MCP config | `url` + `headers` | `"x-api-key"` |
| **Codex** | `~/.codex/config.toml` | `url` + `env_http_headers` | `"x-api-key"` |
| **ChatGPT** | Connectors UI | Custom header (no env-backed JSON) | `x-api-key` |
| **Gemini CLI** | `~/.gemini/settings.json` | `httpUrl` + `headers` + `env` | `"x-api-key"` |

---

## Example Prompts

### Documentation & Discovery

* "How do I create a payout using Nium APIs?"
* "Show me all APIs related to global payroll."
* "Which API should I use to onboard a business customer?"
* "Find the documentation for virtual account creation."

### Integration Development

* "Generate a Node.js application that sends payouts using Nium."
* "Build a React frontend for payroll disbursement."
* "Generate a Python SDK example for creating a payout."
* "Create a webhook handler for payout status updates."

### Troubleshooting

* "Why am I getting this validation error?"
* "Explain the required fields for creating a payout."
* "Show me common causes of payout failures."
* "How should I implement idempotency for payouts?"

### End-to-End Workflows

* "Build a Global Payroll application using Nium APIs."
* "Create a supplier payments workflow."
* "Generate an onboarding flow from KYC to first payout."
* "Build a travel payments platform using Nium."

---

## Documentation & Resources

For comprehensive documentation, guides, and best practices, visit the official Nium MCP Server documentation:

📖 **[Nium MCP Server Docs](https://docs.nium.com/docs/developers/building-with-ai/nium-mcp-server)** — Complete guides, API references, and integration examples.

---

## Security & Access

* Sandbox actions are executed only within authorized Nium Sandbox environments.
* Access is governed by your Nium account permissions.
* Production actions may require additional authentication and approvals.
* Never share API keys, client credentials, or sensitive customer data with AI tools.

---

## Disclaimer

The Nium MCP Server is provided to accelerate development and testing on Nium's platform. Generated code and AI responses should be reviewed and validated before use in production environments. Nium does not guarantee the accuracy, completeness, or suitability of AI-generated outputs.
