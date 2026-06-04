# CAST Prompt Library for MCP

A community prompt library for [CAST Imaging](https://www.castsoftware.com/imaging), [CAST Highlight](https://www.castsoftware.com/highlight), and CAST Gatekeeper — designed for use with VS Code Copilot Chat and the CAST MCP servers.

**🔗 Live portal: [https://cast-extend.github.io/cast-prompt-library/](https://cast-extend.github.io/cast-prompt-library/)**

---

## What is this?

When you connect CAST Imaging (or Highlight / Gatekeeper) to VS Code via the MCP protocol, you can ask questions about your application directly in Copilot Chat. The AI uses CAST's code intelligence data to answer.

This library gives you **50+ ready-to-use prompts** organized by use case, so you don't have to write them from scratch. Browse, fill in your application name, copy, and paste into Copilot Chat.

---

## How to use

### 1. Open the portal

Go to **[https://cast-extend.github.io/cast-prompt-library/](https://cast-extend.github.io/cast-prompt-library/)**

### 2. Connect CAST Imaging MCP to VS Code

Create or update `.vscode/mcp.json` in your repo:

```json
{
  "servers": {
    "cast-imaging": {
      "type": "sse",
      "url": "http://<YOUR-CAST-IMAGING-SERVER>/mcp/",
      "headers": {
        "x-api-key": "<YOUR-API-KEY>"
      }
    }
  }
}
```

Replace `<YOUR-CAST-IMAGING-SERVER>` with your server address and `<YOUR-API-KEY>` with your CAST Imaging API key.

### 3. Pick a prompt

Use the left panel to filter by:
- **Category** — App Discovery, Code Quality, Impact Analysis, Architecture, Modernization, Documentation, Legacy Onboarding, Security & OSS
- **CAST Product** — Imaging, Highlight, Gatekeeper
- **User Profile** — Architect, Developer, Dev Manager

Or use the search bar to find prompts by keyword.

### 4. Fill in variables and copy

Click a prompt card to open it. Fill in any required variables (like `APP_NAME`) and click **Copy Prompt**. The prompt is ready to paste into VS Code Copilot Chat.

### 5. Paste in Copilot Chat

Open Copilot Chat in VS Code (`Ctrl+Alt+I`) and paste. The CAST MCP server will handle all data retrieval automatically.

---

## Prompt categories

| Category | What it covers |
|---|---|
| App Discovery | List apps, transaction inventory, portfolio overview |
| Code Quality & Tech Debt | ISO 5055, structural flaws, deprecated methods, dead code |
| Impact Analysis | Blast radius, cross-app dependencies, database change impact |
| Architecture Analysis | Domain grouping, dependency matrices, architectural integrity |
| Modernization & Cloud | Microservices decomposition, cloud readiness, migration planning |
| Documentation & Biz Rules | API docs, business rule extraction, COBOL mapping |
| Legacy Onboarding | App walkthroughs, tech inventory, epics discovery |
| Security & OSS | CVE scanning, end-of-life libraries |

---

## Contributing

Prompts that work well for you are worth sharing. To add a prompt:

1. Fork this repo
2. Open `index.html` and add your prompt to the `P` array in the `<script>` section following the existing format
3. Submit a pull request

Prompt format:

```js
{
  id: "unique-id",
  cat: "quality",           // category id
  prod: "imaging",          // imaging | highlight | gatekeeper
  title: "Your Prompt Title",
  profile: ["Architect"],   // Developer | Architect | Dev Manager
  complexity: "Intermediate", // Simple | Intermediate | Advanced
  tier: "power",            // starter | power
  vars: [
    { name: "APP_NAME", desc: "Application name in CAST Imaging", ex: "MyApp" }
  ],
  chain: {},                // { prev: "id", next: "id" } for linked prompts
  tags: ["quality", "java"],
  prompt: `Your prompt text with {{APP_NAME}} variables.`,
  expected: "Optional: what a good response looks like"
}
```

---

## Requirements

- VS Code with GitHub Copilot
- CAST Imaging, Highlight, or Gatekeeper with MCP enabled
- Network access from your machine to the CAST server (VPN is fine — MCP calls run locally from VS Code, not via the cloud)

---

*Maintained by the CAST Extend community. For questions or issues, open a GitHub issue.*
