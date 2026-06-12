# MoatScope — Equity Research Terminal

A single-file React + Tailwind web app that produces institutional-grade equity
research on any publicly traded company. It calls the Anthropic Claude API
(`claude-sonnet-4-6`) with the **web search tool** so the model retrieves real,
current data (filings, results, analyst consensus, peer multiples) before
generating the analysis.

## Usage

1. Open `index.html` in any modern browser (no build step required).
2. Paste your **Anthropic API key** (stored only in your browser's
   `localStorage`).
3. Pick a company from the dropdown (30+ across Tech, Finance, Industrials,
   Consumer, Healthcare, Energy and more) **or** type any custom company name.
4. Click **Analyze**. Live web research runs and the report renders below.

## The 7 analysis sections

1. **Business Model & Moat** — revenue streams, cost structure, moat type &
   strength badge (Wide / Narrow / None).
2. **Industry & Competitive Dynamics** — TAM, growth, Porter's Five Forces grid,
   market share, trends, cyclicality.
3. **Management & Governance** — CEO profile, board, capital allocation, insider
   alignment, ESG, alignment score (1–10) with color-coded flags.
4. **Historical Financials (5Y)** — revenue, margins, EBITDA/EBIT, net income,
   FCF, EPS, net debt, ROE, ROIC, with conditional formatting + commentary.
5. **Forecasts (3Y)** — revenue / EBITDA / EPS / FCF projections, assumptions,
   upside & downside scenarios.
6. **Valuation by Comparables** — peer multiples (EV/EBITDA, P/E, EV/Sales,
   P/FCF), peer medians, implied value range, premium/discount callout.
7. **Investment Thesis** — bull vs. bear columns + a prominent BULLISH /
   NEUTRAL / BEARISH verdict with confidence and synthesis.

## How it works

The app issues a single structured API call:

```js
tools: [{ type: "web_search_20250305", name: "web_search" }]
```

A carefully engineered system + user prompt instructs Claude to research the web
and return one strict JSON object, which the React UI parses and renders into the
seven cards.

## Notes

- The browser call uses the `anthropic-dangerous-direct-browser-access` header.
  For production, proxy the request through a backend so your key is never
  exposed client-side.
- AI-assisted research for informational purposes only — not investment advice.
