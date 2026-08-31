# Court Rules MCP Server

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

No install. Connect to the hosted server:

```bash
claude mcp add --transport http court-rules https://mcp.courtrules.app/mcp
```

Or in any MCP client config:

```json
{
  "mcpServers": {
    "court-rules": {
      "url": "https://mcp.courtrules.app/mcp",
      "transport": "streamable-http"
    }
  }
}
```

Sample data works with no account: 3 courts, EDNY holidays, and 3 enforcement
events. Every response carries an `access` field so a client can tell sample
data from live data. Full coverage is behind OAuth.

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
