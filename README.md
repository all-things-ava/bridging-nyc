# Bridging NYC

**An agentic system for navigating the opportunity landscape.**

Given a user's origin neighborhood and travel-time constraint, this prototype uses LLM-based agents grounded in structured socioeconomic and transit data to generate itineraries to New York City neighborhoods associated with stronger upward mobility outcomes, with real-time venue discovery.

**Read the full write-up:** https://all-things-ava.github.io/bridging-nyc/

## Repository contents

| Path | Contents |
|---|---|
| `index.html` | The full paper (methods, appendix, notes, data sources) |
| `figures/` | All figures referenced in the paper |
| `data_raw/` | Source datasets and the processing notebook |
| `data_raw/bridging_networks.ipynb` | End-to-end pipeline that reproduces the agent knowledge base |
| `data_raw/PROMPTS.MD` | Verbatim system prompts for the four LLM agents |
| `data_raw/results/` | Exported knowledge base tables |

## Data sources

All input data is public: Opportunity Atlas mobility estimates (Opportunity Insights), the 2010–2020 Census Tract Crosswalk (HUD), 2020 Decennial Census PL 94-171 population counts (U.S. Census Bureau), 2020 Neighborhood Tabulation Area boundaries and equivalency files (NYC Department of City Planning), and the NYC subway GTFS feed (MTA). Full citations are in the paper's Data Sources section.

## Reproducing the system

The knowledge base is fully reproducible from `bridging_networks.ipynb`. The multi-agent workflow itself is implemented in Langflow; the three MCP tools used (tabular query, web search, current date) were served by a proprietary internal platform and are not distributed. To reproduce the agents, compose equivalent tool integrations and supply your own model configuration and API credentials. System prompts are in `PROMPTS.MD`.

## Status

Research prototype (2026). Not a deployed service.
