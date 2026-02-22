---
name: product-research
description: Uses web search, URL fetch, browser MCP, and GitHub/Linear MCPs to gather market, customer, competitor, and ecosystem evidence. Use before or during product-discovery to validate problems and opportunities.
---

# Product Research

## Available tools (use as needed)

- **Web search** — market trends, user pain, competitor positioning, benchmarks.
- **URL fetch** — read specific articles, docs, landing pages, reports.
- **Browser MCP** (`cursor-ide-browser`) — interactive sites, competitor flows, signup/pricing pages.
- **GitHub MCP** (`user-github`) — OSS ecosystem, adoption, alternatives, dependency/usage patterns via `search_repositories`, `search_code`, `search_issues`.
- **Linear MCP** (`user-Linear`) — internal backlog, existing issues, roadmap context via `list_issues`, `list_projects`, `search_documentation`.

## Instructions

1. State the research question (e.g. “Who else solves X?”, “What do users say about Y?”, “How does Z position this?”).
2. Gather evidence using the tools above; prefer multiple sources.
3. Synthesize findings: what’s validated, what’s assumed, confidence level.
4. Feed results into product-discovery (problem statement, value hypothesis, PRD inputs).

## Output template

- Research question
- Sources used (search, URLs, browser, GitHub, Linear)
- Key findings
- Implications for problem/opportunity
- Gaps and recommended next research
