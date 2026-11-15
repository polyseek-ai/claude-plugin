# polyseek for Claude

Run executive-search candidate searches in Claude with [polyseek](https://polyseek.ai). The plugin pairs the polyseek connector with a skill that guides Claude through the consultant's workflow: take the briefing, show the search plan for corrections, run the search only after your confirmation, present the ranked and verified candidates, refine them in a second pass and get verified business contacts for the candidates you choose. It works in German and English.

Access to polyseek is by request only, for executive-search firms; polyseek sets up every account personally. You need a personal polyseek access code; firms without one can request access on the sign-in screen when they connect.

## What's inside

| Part | What it does |
| --- | --- |
| Connector `polyseek` (`.mcp.json`) | Connects Claude to the polyseek MCP server at `https://mcp.polyseek.ai/mcp`. You sign in once with your personal polyseek access code (OAuth). |
| Skill `candidate-search` | The candidate search workflow: briefing, plan, corrections, confirmation, run, result, second pass, verified contacts. It asks for what a short briefing leaves open before it plans, points out what decides the result when it shows the plan, and reads every candidate with what speaks for and against and what no source evidences. Loaded when you ask for a candidate search, a longlist, a second pass or contacts for candidates, in German or English. In Claude Code and Cowork you can also start it with `/polyseek:candidate-search`. |

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
4. Ask "What can polyseek do?" or "Wie viele Credits haben wir noch?" for a guide, your search depths and your firm's credit balance. Paid actions draw credits from your firm's balance; the price of a search run is shown with the plan before you confirm it. When the balance does not cover an action, nothing starts; Claude then shows how your firm gets credits.

Every candidate list is research from public sources, verified per candidate. Check each candidate before an approach. polyseek never contacts candidates.

## Data

The plugin itself stores and sends nothing and contains no scripts. Everything goes through the polyseek connector: job descriptions, briefings, corrections and your selections are sent to `mcp.polyseek.ai`, operated by int32 solutions GmbH, Villach, Austria, and stored in Frankfurt (AWS, eu-central-1). polyseek's research provider in the United States carries out the research; contact details come from a specialist contact-data provider. Privacy policy: https://polyseek.ai/privacy-policy-mcp/ (German: https://polyseek.ai/de/privacy-policy-mcp/).

## Support

office@polyseek.ai, reply within one business day. Security reports: office@polyseek.ai (see https://polyseek.ai/.well-known/security.txt).

## License

MIT, see [LICENSE](LICENSE).
