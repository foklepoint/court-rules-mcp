# Court Rules MCP Server

[![Court Rules MCP connector: tool definition quality and endpoint health on Glama](https://glama.ai/mcp/connectors/app.courtrules/court-rules/badges/score.svg)](https://glama.ai/mcp/connectors/app.courtrules/court-rules)

Judge-level court filing rules, court holiday calendars, and privacy enforcement
data for US federal and state courts, as an MCP server.

Court rules are the part of legal work that models get wrong most confidently.
Standing orders and individual practices live as PDFs on hundreds of separate
court websites, change without notice, and are not in any model's training data.
Ask an unaided model what page limit applies in front of a named judge and it
will usually invent a plausible number.

This server answers from the actual documents, and every rule carries a citation
back to the page and section of the order it came from.

## Quick start

No install. Add the hosted server, then sign in once when your client asks. It
opens the Court Rules console in your browser; approve the connection and the
client stays signed in.

Claude Code:

```bash
claude mcp add --transport http court-rules https://mcp.courtrules.app/mcp
```

Then run `/mcp`, select `court-rules`, and choose **Authenticate**.

- **Claude Desktop and claude.ai:** Settings > Connectors > Add custom
  connector, URL `https://mcp.courtrules.app/mcp`, then Connect.
- **Cursor:** add the server to `~/.cursor/mcp.json` and click the sign-in
  prompt in Cursor Settings > MCP.

  ```json
  {
    "mcpServers": {
      "court-rules": {
        "url": "https://mcp.courtrules.app/mcp"
      }
    }
  }
  ```

- **VS Code, Codex CLI, and others:** see the
  [quick start](https://docs.courtrules.app/guides/mcp-court-rules#quick-start).

Scripts, backends, and clients without sign-in can send the API key from
https://console.courtrules.app as `Authorization: Bearer <api_key>`. Keys do not
expire.

## Coverage

| | |
| --- | --- |
| Federal judges with extracted filing rules | 1,000+ |
| State and local courts with resources | 692 |
| Court holiday calendars | through 2027 |
| Privacy and regulatory enforcement actions | 1,504 across 16 jurisdictions |

Rules are machine-extracted from each court's own published documents, then
verified by a human against the source before they go live.

## Tools

All nine tools are read-only.

| Tool | What it answers |
| --- | --- |
| `list_courts` | Which courts are covered, with judge counts |
| `search_judges` | Find a judge by district, name, or type |
| `get_judge_rules` | Every extracted rule for one judge |
| `search_filing_rules` | Search rules across judges and districts |
| `check_compliance` | Does this document meet this judge's requirements |
| `list_court_holidays` | Closure dates, for deadline math |
| `search_enforcement_actions` | Privacy and regulatory enforcement by jurisdiction, industry, entity |
| `get_enforcement_details` | Full record for one enforcement action |
| `get_enforcement_stats` | Aggregate enforcement statistics |

## Example prompts

- "What are the page limits for a summary judgment brief in front of Judge Amon?"
- "Does Judge Block require a pre-motion conference letter before a motion to dismiss?"
- "What courtesy copies do I need to file in EDNY, and where do they go?"
- "Is the court closed any day next week that would move my deadline?"
- "What privacy enforcement actions hit healthcare companies in California this year?"

## Registry

Listed in the official MCP Registry as `app.courtrules/court-rules`.

## Links

- Documentation: https://docs.courtrules.app
- Site: https://www.courtrules.app
- Privacy policy: https://www.courtrules.app/privacy
- Terms: https://www.courtrules.app/terms
- Support: api@courtrules.app

## Privacy Policy

This connector sends your queries to the courtrules.app API to retrieve court
rules and enforcement data. Full policy, covering what is collected, how it is
stored, retention, and third-party sharing: https://www.courtrules.app/privacy

## License

MIT for this repository's contents. The hosted service is governed by the terms
at https://www.courtrules.app/terms
