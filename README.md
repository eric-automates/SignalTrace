# SignalTrace — research lab update

## Publish and use

1. Replace the existing `index.html` at the root of the SignalTrace GitHub repository with the `index.html` in this folder. Commit it, wait for GitHub Pages to redeploy, and refresh.
2. Enter a U.S. stock or company and analyze it as before. The default run loads a modest set of inputs selected using the company’s current sector and industry.
3. To broaden the search, click **Load expanded data**. The compact status display shows completed requests, elapsed time, per-category progress, and failed requests. Two requests run at a time with a short pause between jobs. **Stop** stops the queue after the in-flight requests finish; partial results remain. Analyze a new ticker after the scan stops or finishes. Results are held in the page session, not saved to a server.
4. The Together, Later and Earlier tabs chart up to three, two and three input lines respectively. Choose **Top 10** to list up to ten eligible candidates; the graph remains limited to the requested number. Explore lets you chart any individual available daily input. Expand input coverage to see attempted feeds and unavailable ones.
5. The capsule timeline below the chart shows the stock and the top three Earlier candidates in separate rows. Green denotes a rising regime and coral a falling regime. Hover over a capsule on desktop to see dates, duration, and excess area.
6. The annual World Context section becomes available after expanded data loads. Select an indicator and country to view its annual observations and annual comparison chart. It uses available stock history, independently of the chosen daily window.

Music: **Add songs** selects local audio on your own device; no upload is required. The player is below the page content so it does not obscure the graph.

## Input coverage and source categories

The ticker directory contains a company’s current sector and industry; a curated cross-reference chooses industry-related daily market and macro inputs. An unclassified company uses broad-market inputs. The expanded scan adds a larger, **finite, not exhaustive** collection of sector and international funds, bonds, rates, credit spreads, currencies, commodity futures and spot oil prices. It also tries:

- The AI-GPR daily newspaper-derived geopolitical risk indices, including general, threat, act and regional oil-news measures.
- Historical daily regional temperature and precipitation for Houston, Chicago, London and Singapore. These are generic proxies and are not verified locations of a given company's operations or suppliers.
- World Bank / UN international migrant stock and net-migration annual indicators for Canada, China, Germany, India, Mexico and the United States. Other countries, indicators, disasters and specific event-level feeds are not comprehensively covered.

The expanded catalog is global context, not a verified map of every company's suppliers, customers, production sites, or causal relationships. It does not pull all available global data, events, weather sites, tickers or economic indicators, and it is not possible to prove that it contains all relevant causes. Public sources can be unavailable, delayed, revised, rate-limited or change. A loaded source may lack enough aligned history to be ranked. The selected input list, warnings and per-category progress disclose coverage; failures do not generate invented data. Funds can contain the target stock, so those comparisons can be partly circular.

Annual migration estimates are **not** interpolated into daily signals or ranked as daily precursors. The annual chart separately scales the indicator and stock within their observed overlapping years to a 0–100 range, shows dots at observed years and breaks lines over missing years. The stock value is its last available close for each year; the current year may be incomplete. Observation years are not publication dates. Annual context is descriptive, not a test of migration's effect on a stock.

## Timing analysis

- **Together** ranks available inputs by positive same-session correlation of daily changes and stock returns over the selected window.
- **Earlier** chooses each input's strongest absolute correlation at lags of 1–10 trading sessions using the first 70% of the window, then reports correlation at the selected lag and direction on the final 30%. The top candidates are ranked using training correlation, not by looking at the holdout. Short windows permit fewer lags; fewer observations can yield no valid test. The holdout is a basic robustness check, not a trading backtest, causal test or guarantee of future performance. It is not immune to revisions, late publication, survivorship or date alignment problems.
- **Later** ranks positive or negative correlations over lags of 1–10 sessions on the selected window. The Later view is not split into training and holdout.

The main graph uses the actual observation dates without shifting or flipping input lines. Source changes are scaled to stock volatility using pre-window observations, a visualization only, not their original prices. Missing values create gaps; each segment after a gap restarts at 100. Larger search spaces make chance matches more likely, and similar funds or geopolitical sub-indices are not statistically independent. No multiple-testing adjustment or confidence interval is currently computed.

## Capsule method

This is a Seeq-*inspired* approximation, not Seeq software or a complete implementation of its formulas. For each stock or input:

1. Compute a trailing sum of five trading-session changes: stock and market percentage returns, or differences in a non-price input's native units.
2. Standardize against the mean and standard deviation of up to 504 valid observations **before** the displayed window (at least 40 are required). Different signals therefore have their own baseline.
3. Begin an up or down capsule after two consecutive observations exceed +0.6 or fall below −0.6 standard deviations. Once confirmed, the displayed start is the first of those two observations. End the capsule after two observations return inside the signed ±0.25 exit threshold; the exit-confirmation observations are not included. Missing data end a capsule; maximum length is 252 sessions.
4. Report duration in trading sessions and **excess area**, the discrete sum of standardized distance above the signed exit threshold across included sessions. It is a descriptive measure, not a dollar amount or an actual integral of the raw asset price.
5. For each earlier candidate, show a signed overlap statistic on the holdout only: compare its states shifted forward by its training-selected lag with the stock states, respecting positive or inverse association. The score is the number of sessions with matching active signed states divided by the number of valid sessions where either state is active. Timeline bars themselves stay on actual dates and are never shifted.

A higher overlap or matching capsule durations can be useful for exploration, but **does not prove that signals are equivalent, that one causes the other, or that future behavior will repeat**. A common driver, chance, revisions, changing thresholds or market composition can produce similar patterns. This tool cannot make causes “perfectly clear.” The supplied PDF's other formulas remain only partly implemented; this version does not claim full Seeq feature parity.

## Sources and usage limits

- Ticker metadata: [top-us-stock-tickers](https://github.com/zyhe16/top-us-stock-tickers), a third-party Nasdaq screener dataset. Nasdaq Trader and Twelve Data are fallback directories without sector/industry classification.
- Market/futures data: unofficial Yahoo Finance endpoints through public relays; futures and funds are proxies, not spot prices. Review Yahoo terms before deployment.
- Economic/commodity data: [FRED](https://fred.stlouisfed.org/); selected failed basic feeds have clearly named market fallbacks. U.S. Economic Policy Uncertainty Index by Scott Baker, Nicholas Bloom and Steven J. Davis, via FRED.
- Geopolitical data: Matteo Iacoviello and Jonathan Tong, [AI-GPR Index](https://www.matteoiacoviello.com/ai_gpr.html), daily newspaper-derived measures, cited per their request. These data are subject to revisions and may be published after their observation dates; they are not a complete event log.
- Weather: [Open-Meteo Historical Weather](https://open-meteo.com/en/docs/historical-weather-api), CC BY 4.0 with attribution. Free API access is for noncommercial use; commercial usage needs appropriate terms. Weather reanalysis is retrospective, can be late and can differ from information available at the time.
- Annual population and migration indicators: [World Bank Data API](https://datahelpdesk.worldbank.org/knowledgebase/articles/889392-about-the-indicators-api-documentation), based on UN estimates as documented by each indicator. Observation years are not release dates.
- cors.dev and Jina Reader public relays can see requests, cache, fail, rate-limit, or change. This GitHub Pages file needs no private API key or server, but relies on external providers. The app does not bundle provider datasets. Review terms, attribution and applicable licensing before public or commercial use.
