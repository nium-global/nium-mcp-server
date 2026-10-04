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

## Supported APIs

The Nium MCP Server allows you to integrate with Nium APIs through LLM function calling, using the MCP clients listed below. It currently supports the whitelisted APIs listed here: all `GET` endpoints from the [Nium API Reference](https://docs.nium.com/api), plus a limited set of `POST` endpoints for onboarding, beneficiaries, payouts, and sandbox simulation. Endpoints are grouped by API reference section, and `{...}` values in each path are path parameters.

Only the five `POST` endpoints below are supported for writes (Create Customer v5, Create a Session, Add Beneficiary V2, Transfer Money, and the sandbox-only Simulate Receiving a Transaction). All other `POST`, `PUT`, `PATCH`, and `DELETE` operations are not supported.

**Client Prefund Account**

* Fetch Client Prefund Request - `GET /api/v1/client/{clientHashId}/prefundList`
* Client Prefund Balances - `GET /api/v1/client/{clientHashId}/balances`

**Client Settings**

* Client Details - `GET /api/v1/client/{clientHashId}`
* Fee Details V3 - `GET /api/v3/client/{clientHashId}/fees`
* Get Maximum and Available Limits of Direct Debit - `GET /api/v1/client/{clientHashId}/payin/limits`

**Client Transactions**

* Client Transactions - `GET /api/v1/client/{clientHashId}/transactions`

**User Management**

* List Users - `GET /api/v1/client/{clientHashId}/users`
* Get User - `GET /api/v1/client/{clientHashId}/user/{userHashId}`

**Customer Onboarding V5**

* List Customers v5 - `GET /api/v5/client/{clientHashId}/customers`
* List Hosted Form Applications - `GET /api/v5/client/{clientHashId}/applications`
* Get Customer v5 - `GET /api/v5/client/{clientHashId}/customer/{customerHashId}`
* Fetch Public Corporate Details - `GET /api/v5/client/{clientHashId}/corporate/publicDetails`
* Fetch Exhaustive Corporate Details - `GET /api/v5/client/{clientHashId}/corporate/exhaustiveDetailsSearch`
* Create Customer v5 - `POST /api/v5/client/{clientHashId}/customers`

**Customer Account - Individual**

* Fetch Individual Customer RFI Details - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/rfi`

**Customer Account - Corporate**

* Exhaustive Corporate Details using Business ID - `GET /api/v2/client/{clientHashId}/corporate/lookup`
* Fetch Corporate Customer RFI Details - `GET /api/v1/client/{clientHashId}/corporate/rfi`
* Fetch Corporate Constants - `GET /api/v2/client/{clientHashId}/onboarding/constants`

**Customer Management**

* Customer List V3 - `GET /api/v3/client/{clientHashId}/customers`
* Customer Details V2 - `GET /api/v2/client/{clientHashId}/customer/{customerHashId}`
* Account Statement - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/accounts/statement`
* Account Statement for the Specified Wallet - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/statement`

**Customer Terms and Conditions**

* Terms and Conditions - `GET /api/v1/client/{clientHashId}/termsAndConditions`

**Open Banking (Onboarding)**

* Account Details By Customer Consent ID. - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/consent/account`
* Payment Details by System Reference Number - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/consent/payment`

**Accounts**

* Fetch linked bank accounts - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/bankAccounts`
* Fetch linked bank account - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/bankAccounts/{bankAccountId}`

**Onboarding Forms - Corporate**

* Regenerate Onboarding Form URL - `GET /api/v1/client/{clientHashId}/applications/{applicationId}/regenerateURL`
* Fetch Application Details - `GET /api/v1/client/{clientHashId}/application/{applicationId}`

**Sessions**

* Create a Session - `POST /api/v1/client/{clientHashId}/sessions`

**Files**

* Fetch File Details - `GET /api/v1/client/{clientHashId}/files/{fileId}`

**Customer Wallet Balance**

* Wallet Balance - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}`
* Fetch Wallet - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet`

**Customer Wallet Transactions**

* Transactions - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/transactions`
* Download Transaction Receipt - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/transactions/{systemReferenceNumber}/receipt`

**Customer Funding**

* Get Funding instrument details - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/fundingInstruments/{fundingInstrumentId}/fundingInstrumentDetails`
* Get Funding Instrument List - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/fundingInstruments`

**Customer Virtual Accounts**

* Virtual Account Details V2 - `GET /api/v2/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/paymentIds`
* Account Ownership Certificate - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/accountOwnershipCertificate`

**Rates**

* Exchange Rate V2 - `GET /api/v2/exchangeRate`
* Fetch historic aggregated exchange rates - `GET /api/v1/exchangeRates/aggregate`

**Quotes**

* Fetch Quote by ID - `GET /api/v1/client/{clientHashId}/quotes/{quoteId}`

**Conversions**

* Fetch Conversion by id - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/conversions/{conversionId}`

**Quotes (Previous Version)**

* Exchange Rate With Markup - `GET /api/v1/client/{clientHashId}/exchangeRate`
* Exchange Rate Lock and Hold - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/lockExchangeRate`

**Beneficiary**

* Beneficiary List V2 - `GET /api/v2/client/{clientHashId}/customer/{customerHashId}/beneficiaries`
* Beneficiary Details V2 - `GET /api/v2/client/{clientHashId}/customer/{customerHashId}/beneficiaries/{beneficiaryHashId}`
* Beneficiary Validation Schema V2 - `GET /api/v2/client/{clientHashId}/customer/{customerHashId}/currency/{currencyCode}/validationSchemas`
* Add Beneficiary V2 - `POST /api/v2/client/{clientHashId}/customer/{customerHashId}/beneficiaries`

**Reference Data**

* Search Routing Code Using Bank Name - `GET /api/v2/client/{clientHashId}/payout/banks`
* Search Routing Code Using Branch Name - `GET /api/v2/client/{clientHashId}/payout/branches`
* Fetch Bank Details using Routing Code - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/country/{countryCode}/routingCodeType/{routingCodeType}/routingCodeValue/{routingCodeValue}/routingCode`

**Payout**

* Fetch Remittance Life Cycle Status - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/remittance/{systemReferenceNumber}/audit`
* Purpose of Transfer - `GET /api/v1/remittance/purposeCodes`
* Get Proof Of Payment - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/remittance/{systemReferenceNumber}/receipt`
* Fetch Supported Corridors V3 - `GET /api/v3/client/{clientHashId}/supportedCorridors`
* List Payouts in a Batch - `GET /api/v1/client/{clientHashId}/payout/bulk/{batchId}`
* Fetch Batch Payout Status - `GET /api/v1/client/{clientHashId}/payout/bulk/{batchId}/status`
* Transfer Money - `POST /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/remittance`

**Nium Verify**

* Fetch Verification - `GET /api/v1/client/{clientHashId}/verifications/{verificationId}`
* List Verifications - `GET /api/v1/client/{clientHashId}/verifications`
* Fetch validation schema for Nium Verify - `GET /api/v1/client/{clientHashId}/schema`

**Lifecycle**

* Card Details V2 - `GET /api/v2/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/card/{cardHashId}`
* Card List V2 - `GET /api/v2/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/cards`

**Security**

* Fetch card data encrypted - `GET /api/v2/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/card/{cardHashId}/retrieve`
* Fetch Pin Status - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/card/{cardHashId}/pin/status`
* Fetch ATM Pin V2 - `GET /api/v2/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/card/{cardHashId}/pin`
* Show Security Details Encrypted - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/card/{cardHashId}/showSecurityDetails`

**3DS**

* 3DS Passcode Enrollment Status - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/3ds/passcode/status`

**Controls**

* Get Channel Restriction - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/card/{cardHashId}/channels`
* Get MCC Channel Restrictions - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/card/{cardHashId}/channels/mcc`
* Fetch Card Limits - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/card/{cardHashId}/limits`
* Limits For All Cards For A Customer - `GET /api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/limits`

**Cards Reference Data**

* Reference Exchange Rate - `GET /api/v1/client/{clientHashId}/referenceRate`

**Request for Information**

* Fetch Single RFI - `GET /api/v5/client/{clientHashId}/rfi/{rfiId}`
* Fetch RFI Details - `GET /api/v5/client/{clientHashId}/customer/{customerHashId}/rfis`

**Reports**

* Download generated report - `GET /api/v1/client/{clientHashId}/report/{reportRequestId}/download`

**Payin**

* Simulate Receiving a Transaction _(Sandbox only)_ - `POST /api/v1/inward/payment/manual`

**Customer**

* Fetch micro-deposit details _(Sandbox only)_ - `GET /api/v1/simulations/client/{clientHashId}/customer/{customerHashId}/bankAccounts/{bankAccountId}/microDeposits`

---

## Installation Guide

> **Before you start:** Get your API key from the [Nium Portal](https://app.nium.com) under **Settings → API Keys** (sandbox access is instant). Replace `YOUR_NIUM_API_KEY` in the configs below with it. Live API calls require the `x-api-key` header on the MCP HTTP request.
>
> After using a one-click **Install** button, replace the `YOUR_NIUM_API_KEY` placeholder in the generated server entry with your key.

### Quick Install

[![Install in Cursor](https://img.shields.io/badge/Install-Nium_MCP_Cursor-00A67E?style=for-the-badge)](https://cursor.com/en/install-mcp?name=nium&config=eyJ1cmwiOiJodHRwczovL21jcC1zYW5kYm94Lm5pdW0uY29tL21jcCIsImhlYWRlcnMiOnsieC1hcGkta2V5IjoiWU9VUl9OSVVNX0FQSV9LRVkifX0%3D)
[![Install in VS Code](https://img.shields.io/badge/Install-Nium_MCP_VSCode-0078D4?style=for-the-badge)](https://insiders.vscode.dev/redirect/mcp/install?name=Nium_Sandbox&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp-sandbox.nium.com%2Fmcp%22%2C%22headers%22%3A%7B%22x-api-key%22%3A%22YOUR_NIUM_API_KEY%22%7D%7D)

---

### Cursor

[![Install Now](https://img.shields.io/badge/Install_Now-Cursor-00A67E?style=flat-square&logo=cursor)](https://cursor.com/en/install-mcp?name=nium&config=eyJ1cmwiOiJodHRwczovL21jcC1zYW5kYm94Lm5pdW0uY29tL21jcCIsImhlYWRlcnMiOnsieC1hcGkta2V5IjoiWU9VUl9OSVVNX0FQSV9LRVkifX0%3D)

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
