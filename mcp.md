---
title: "Data Galactica MCP server and API quickstart"
---

This page explains how to connect AI assistants to [Data Galactica](https://datagalactica.com/). Source and issues: [datagalactica-mcp-server on GitHub](https://github.com/rchtjn2-gif/datagalactica-mcp-server). Back to the [Data Galactica guide](./).

<p align="center"><img src="logo.png" alt="Data Galactica MCP server logo" width="120"></p>

# Data Galactica MCP Server: resolve any person or company to one permanent ID

> Verify companies, check people in their roles, resolve CIN, LEI, SEC CIK or Wikidata IDs to one record, and size markets, from Claude, ChatGPT, Cursor or any MCP client.

**MCP endpoint:** `https://api.datagalactica.com/mcp` · **Transport:** Streamable HTTP · **Tools:** 28 · **Website:** [datagalactica.com](https://datagalactica.com)

This repository is the public listing for the **hosted** Data Galactica MCP server: connection instructions, the registry manifest (`server.json`) and client config files. There is nothing to install or self-host; the server runs at the URL above.

## Connect in one step

Add this URL to any MCP client that supports remote servers:

```
https://api.datagalactica.com/mcp
```

### Claude (claude.ai, Claude Desktop, Claude mobile)
Settings → Connectors → **Add custom connector** → paste the URL above → Connect.

### Claude Code
```bash
claude mcp add --transport http datagalactica https://api.datagalactica.com/mcp
```
With an API key instead of OAuth:
```bash
claude mcp add --transport http datagalactica https://api.datagalactica.com/mcp --header "Authorization: Bearer YOUR_KEY"
```

### ChatGPT
Settings → Apps & Connectors → Advanced → enable Developer mode → **Create** a connector → paste the URL above.

### Cursor, Windsurf, Cline and other JSON-config clients
```json
{
  "mcpServers": {
    "datagalactica": {
      "url": "https://api.datagalactica.com/mcp"
    }
  }
}
```

### VS Code (GitHub Copilot)
Add to `.vscode/mcp.json`:
```json
{
  "servers": {
    "datagalactica": {
      "type": "http",
      "url": "https://api.datagalactica.com/mcp"
    }
  }
}
```

### Gemini CLI
```bash
gemini extensions install https://github.com/rchtjn2-gif/datagalactica-mcp-server
```

## Authentication
OAuth 2.1 (scope `api`): sign in with your Data Galactica account when your client asks. Or send an API key: `Authorization: Bearer YOUR_KEY`. AI agents can sign a person up with only their e-mail: https://datagalactica.com/auth.md.

## What data it covers
- **15.5M organisations and 30.6M people** across 252 countries, each with a permanent Galactica ID (DGC- for organisations, DGP- for people)
- Accepts **CIN, LLPIN, LEI, UK company number, SEC CIK and Wikidata Q-ids**: every one resolves to the same record
- Every record **graded** (verified, gold, silver, bronze) with a sourcing grade and sources on every section
- **762 ranked lists** by industry (ISIC Rev.4), country, city and function
- KYB verification with a confidence score and field-by-field checks, people-in-role checks, due-diligence packs, hiring and talent maps
- Owners can claim their record and keep it current through their own agent (OAuth), with every change reviewed

## Tools (28)
| Group | Tools |
|---|---|
| Search | `search`, `search_companies`, `search_people`, `search_people_in_city`, `top_companies` |
| Records | `get_company`, `get_person`, `get_company_people`, `get_contact` |
| Verification and diligence | `verify_company`, `check_person`, `check_identity`, `check_email`, `company_diligence`, `person_diligence` |
| Hiring and markets | `company_hiring`, `hire_check`, `talent_map`, `research_market`, `about_dataset` |
| Wallet | `get_wallet`, `top_up_wallet`, `get_payment` |
| Owner tools (OAuth) | `whoami`, `get_my_profile`, `propose_profile_update`, `add_note`, `list_my_contributions` |

## Example prompts
- "Verify that 'Infosys Ltd' at infosys.com is a real, operating company and give me its Galactica ID."
- "Resolve LEI 335800TYLGG93MM7PR89 and list the board and leadership."
- "Is Jane Doe really the CFO of Example Corp? Check the public record."
- "How many software companies are there in Pune, and which are the top 20?"
- "Run a due-diligence pack on this supplier and tell me what was not checked."

## Pricing
₹50 free credit on signup (about 312 calls), then ₹0.16 per answered call from a prepaid wallet. Errors, not-found, wallet and code lists are free. No subscription.

## FAQ
### Is there an MCP server for company verification and KYB?
Yes. Data Galactica runs a hosted MCP server at https://api.datagalactica.com/mcp with verify_company, company_diligence and check_person over 15.5M organisations and 30.6M people.

### Can I resolve a CIN, LEI or SEC CIK to one company record?
Yes. Every supported identifier resolves to the same permanent Galactica ID, so you can join data that never shared a key.

### How do I know a record is right?
Every record carries an overall grade and per-section sources. Names collide, so check place and identifiers before treating two records as the same.

### How much does it cost?
₹50 free credit on signup, then ₹0.16 per answered call. Errors and not-found are free.

## Links
- [API and MCP overview](https://datagalactica.com/api)
- [API reference](https://datagalactica.com/api/docs)
- [OpenAPI 3.1](https://datagalactica.com/api/openapi.json)
- [llms.txt](https://datagalactica.com/llms.txt)
- [Server card](https://datagalactica.com/.well-known/mcp.json)
- [Sign up (₹50 free)](https://datagalactica.com/signup)
- [Privacy policy](https://datagalactica.com/privacy)
- [Terms](https://datagalactica.com/terms)

## About this repository
This repo holds listing and configuration files only. The Data Galactica MCP server is a hosted service operated by Data Galactica; its use is governed by the terms linked above. The files in this repository are released under the MIT licence.
