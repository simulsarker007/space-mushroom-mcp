# Space Mushroom MCP server

A free, read-only [Model Context Protocol](https://modelcontextprotocol.io) server for engineering materials. Every number it returns comes with its unit, the conditions it was measured under, the method and the source it was read from, so an AI assistant can quote a value and prove where it came from.

- **Endpoint (Streamable HTTP):** `https://spacemushroom.com/mcp`
- **No API key, no sign-in.** Read-only.
- **Data:** about 600 material profiles (metals, polymers, ceramics, composites, semiconductors, thermal protection, shielding, regolith and more, with a focus on space materials), licensed [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
- **Docs and setup page:** <https://spacemushroom.com/mcp-server/>
- **Website:** <https://spacemushroom.com> · **Open dataset:** [Zenodo](https://zenodo.org/records/23718226), [Hugging Face](https://huggingface.co/datasets/Simul007/open-materials-database), [GitHub](https://github.com/simulsarker007/open-materials-database)

## Tools

| Tool | What it does |
|---|---|
| `find_materials` | Requirements in, candidates out. Each material gets pass, fail or unknown, with the evidence |
| `search_materials` | Find materials by name, abbreviation or formula |
| `get_material` | The sourced record of one material: values, conditions, uses, hazards, failure modes, corrosion, supply |
| `compare` | Line several materials up on one property, each value with its conditions and source |
| `list_properties` | Property names in use, with canonical units |
| `list_claims` | Every current sourced value for a material, with an evidence level and a claim id |
| `prove_claim` | Everything behind one value: as printed, converted, conditions, and where in each source |
| `what_is_missing` | Which properties have sourced data and which have none (not covered yet, not "safe") |
| `resolve_designation` | Which material a code names: UNS, EN, DIN, JIS, AISI/SAE, ASTM, AMS or a trade name |
| `search_sources` | Full-text search over short quoted passages from the sources |
| `get_term` | Plain-language definition of a technical term |

## Add it to a client

Claude Desktop, Cursor, VS Code and other clients that accept a remote server:

```json
{
  "mcpServers": {
    "space-mushroom": { "url": "https://spacemushroom.com/mcp" }
  }
}
```

Claude Code:

```
claude mcp add --transport http space-mushroom https://spacemushroom.com/mcp
```

## Example questions

- "Which stainless steels have a sourced minimum yield strength above 400 MPa, and what are the conditions?"
- "What material is UNS S31600 and what is its density, with the source?"
- "Compare PEEK, PEI and PPS on continuous service temperature."
- "What does Space Mushroom have no data on for Ti-6Al-4V?"

## How accurate is it?

Profiles are drafted with AI assistance from cited sources and then checked automatically: every value must be found in its cited source, and every designation must be printed there. Values marked `ai_checked` were re-read by an AI assistant, not a person. See the [methodology](https://spacemushroom.com/methodology/) and [editorial policy](https://spacemushroom.com/editorial-policy/). Check the source before using a value in a safety-critical design.

## Citation

Space Mushroom contributors (2026). *Space Mushroom: open materials database.* https://spacemushroom.com/ (CC BY 4.0)

## Contact

hello@spacemushroom.com · [Report a wrong value](https://spacemushroom.com/contact/)
