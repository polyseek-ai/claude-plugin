# polyseek for Claude

Run executive-search candidate searches in Claude with [polyseek](https://polyseek.ai). The plugin adds the polyseek connector and the skill `market-signals`. The candidate search skill `candidate-search` now comes from the connector itself (Skills over MCP) and guides Claude through the consultant's workflow: take the briefing, show the search plan for corrections, run the search only after your confirmation, present the ranked and verified candidates, refine them in a second pass and get contact details for the candidates you choose (business email, and mobile number and private email where your firm has enabled them). It works in German and English.

Access to polyseek is by request only, for executive-search firms; polyseek sets up every account personally. You need a personal polyseek access code; firms without one can request access on the sign-in screen when they connect.

## What's inside

| Part | What it does |
| --- | --- |
| Connector `polyseek` (`.mcp.json`) | Connects Claude to the polyseek MCP server at `https://mcp.polyseek.ai/mcp`. You sign in once with your personal polyseek access code (OAuth). |
| Skill `candidate-search` (from the connector) | No longer part of the plugin. The polyseek server serves it over MCP to clients that load skills from connectors (Claude and Claude Code; on Team plans an Owner turns on "Skills over MCP" first), so it stays current with the server. Without it, the connector's instructions and tool descriptions guide the search. |
| Skill `market-signals` | Business development: companies in your regions and industries where a reported event of the last week, two weeks or month likely creates a need for executive search (leadership changes, new owners, acquisitions, restructuring, expansion), each with its source and the need it likely creates. It asks for what the request leaves open, names the price before it starts, shows the signals and follows a chosen one up with a company profile, contact details and a draft of the first message, each only when you ask. It also helps you set the query up as a weekly task of your assistant. In Claude Code and Cowork you can start it with `/polyseek:market-signals`. |

The connector also offers company profiles, person profiles, identifying the employer behind an anonymous job posting, earlier work and a guide to polyseek; Claude uses them directly from the connector.

## Install

- **claude.ai, Claude Desktop and Cowork:** Customize > Plugins, find polyseek in the directory, or add this repository as a marketplace (Add > Add marketplace, `polyseek-ai/claude-plugin`).
- **Claude Code:**

```
/plugin install polyseek --marketplace polyseek-ai/claude-plugin
```

## Use it

1. Add the plugin and connect the polyseek connector from the plugin's **Connectors** tab. On Team and Enterprise plans an Owner adds the connector for the organization first.
2. Ask, for example: "Here is the job description for a Head of Finance at a family-owned industrial company in Styria. Plan a candidate search and show me the plan." Or in German: "Plane eine Kandidatensuche für diese CFO-Rolle und zeig mir den Plan."
3. Correct the plan in plain words, confirm it, and read the result when the search has finished (30 to 60 minutes; it keeps running on polyseek's servers if you close the chat).
4. For business development ask, for example: "Where did leads for new mandates come up in mechanical engineering in Austria and Germany last week?" Or in German: "Wo gab es letzte Woche im Maschinenbau in Österreich und Deutschland Ansatzpunkte für neue Mandate?" A query takes about 20 minutes; Claude names its price in credits before it starts.
5. Ask "What can polyseek do?" or "Wie viele Credits haben wir noch?" for a guide, your search depths and your firm's credit balance. Paid actions draw credits from your firm's balance; the price of a search run is shown with the plan before you confirm it. When the balance does not cover an action, nothing starts; Claude then shows how your firm gets credits.

Every candidate list is research from public sources, verified per candidate. Check each candidate before an approach. polyseek never contacts candidates.

## Data

The plugin itself stores and sends nothing and contains no scripts. Everything goes through the polyseek connector: job descriptions, briefings, corrections and your selections are sent to `mcp.polyseek.ai`, operated by int32 solutions GmbH, Villach, Austria, and stored in Frankfurt (AWS, eu-central-1). polyseek's research provider in the United States carries out the research; contact details come from a specialist contact-data provider. Privacy policy: https://polyseek.ai/privacy-policy-mcp/ (German: https://polyseek.ai/de/privacy-policy-mcp/).

## Support

office@polyseek.ai, reply within one business day. Security reports: office@polyseek.ai (see https://polyseek.ai/.well-known/security.txt).

## License

MIT, see [LICENSE](LICENSE).
