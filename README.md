# Nium MCP Server

Build, test, and integrate with Nium using natural language.

The Nium MCP Server connects your AI coding agent directly to Nium's APIs, documentation, guides, and sandbox environment. Ask questions, generate production-ready integration code, troubleshoot errors, and execute sandbox workflows — without leaving your editor.

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

### Install on Claude

#### Using Connectors (Requires Claude Subscription)

1. Open Claude
2. Navigate to **Settings → Connectors**
3. Click **Add Custom Connector**
4. Use the URL:

```
https://mcp.nium.com/mcp
```

5. Save and restart Claude

---

#### Using Manual Configuration

Open your `claude_desktop_config.json` file and add:

```json
{
  "mcpServers": {
    "nium-mcp": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://mcp.nium.com/mcp"
      ]
    }
  }
}
```

---

### Install in VS Code

#### One-Click Installation

[![Install Nium MCP](https://img.shields.io/badge/Install-Nium_MCP-0052CC)](https://insiders.vscode.dev/redirect?url=vscode:mcp/install?%7B%22type%22%3A%22http%22%2C%22name%22%3A%22nium-mcp%22%2C%22version%22%3A%221.0.0%22%2C%22description%22%3A%22Build%20and%20integrate%20with%20Nium%20using%20natural%20language%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.nium.com%2Fmcp%22%2C%22author%22%3A%22Nium%22%2C%22tags%22%3A%5B%22nium%22%2C%22payments%22%2C%22mcp%22%5D%2C%22categories%22%3A%5B%22mcp%22%5D%7D)

---

#### Manual Installation

Add the following to your `mcp.json` file:

```json
{
  "servers": {
    "nium-mcp": {
      "url": "https://mcp.nium.com/mcp",
      "type": "http"
    }
  }
}
```

---

### Install in Cursor

Add the following configuration:

```json
{
  "mcpServers": {
    "nium-mcp": {
      "url": "https://mcp.nium.com/mcp"
    }
  }
}
```

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

## Security & Access

* Sandbox actions are executed only within authorized Nium Sandbox environments.
* Access is governed by your Nium account permissions.
* Production actions may require additional authentication and approvals.
* Never share API keys, client credentials, or sensitive customer data with AI tools.

---

## Disclaimer

The Nium MCP Server is provided to accelerate development and testing on Nium's platform. Generated code and AI responses should be reviewed and validated before use in production environments. Nium does not guarantee the accuracy, completeness, or suitability of AI-generated outputs.
