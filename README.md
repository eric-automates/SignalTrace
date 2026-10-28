# SignalTrace — industry input update

## Publish

Replace the existing `index.html` at the root of the GitHub repository with the `index.html` in this folder, commit the change, wait for GitHub Pages to deploy, and refresh the site. No server or API key is required. This package has not been uploaded to GitHub automatically.

Enter a U.S. stock ticker or choose a company from autocomplete and press Analyze. Choose a period before or after the analysis. The app retrieves its directory on page open, including sector and industry when available. You can add your own local audio files using **Add songs**; they stay on your device.

## How the input selection works

The app attempts one Nasdaq-derived ticker-directory download containing company names, current sector and industry. It selects a curated collection of plausible inputs by sector, refines it using broad industry-name patterns, and adds some loosely related inputs. It never claims these are the company's verified suppliers, customers, operating locations, or actual causes. The current classification is applied to the entire displayed history. If classification is missing or the directory fallback lacks it, only broad-market inputs are selected and the limitation is shown. This is not an exhaustive list of possible influences.

Every analysis starts with the broad market, Nasdaq 100, 10-year Treasury yield, VIX, and the U.S. news-based economic policy uncertainty index when available. The cross-reference then adds, for example:

| Type | Examples of additional candidates |
| --- | --- |
| Energy | Energy and producer funds, WTI and Brent crude spot prices, natural-gas futures, copper futures, Houston regional mean temperature |
| Technology | Technology and semiconductor funds, copper futures, euro exchange rate |
| Materials and mining | Materials fund, copper futures, gold fund, WTI spot |
| Finance | Financial and regional-bank funds, small caps, euro exchange rate |
| Industrials | Industrial fund, copper futures, WTI spot, small caps |
| Utilities | Utilities fund, natural gas, WTI, copper, Houston regional temperature |
| Health care | Health-care and biotechnology funds, euro exchange rate |
| Consumer discretionary | Consumer and retail funds, WTI, euro exchange rate |
| Consumer staples | Staples fund, corn and wheat futures, WTI |
| Real estate | Real-estate and industrial funds, copper futures, small caps |
| Telecommunications | Communications, technology, and semiconductor funds; copper futures |

Industry patterns add possible links for areas such as airlines, agriculture, autos, banks, oil, mining, semiconductors, and biotechnology. Agricultural, food, and transportation industries may receive Chicago regional temperature. These single-city weather series are coarse regional proxies, not locations verified for each company. Weather is historical reanalysis, can arrive late, and is not a forecast of what the market knew at the time. The policy uncertainty series is a news-based index, not a comprehensive database of world events. There is no company-specific event matching, global weather network, full supplier graph, or exhaustive feed of commodities.

## The four views

- **Together:** up to three eligible inputs with the strongest positive same-session correlation of source changes with stock returns.
- **Later:** up to two eligible inputs whose changes have the strongest absolute correlations at 1–10 sessions after stock changes.
- **Earlier:** up to three eligible inputs whose changes have the strongest absolute correlations at 1–10 sessions before stock changes.
- **Explore:** select any loaded input to plot individually, provided it has enough pre-window history for scaling. The coverage section lists attempted feeds and whether they loaded; a loaded feed can still lack sufficient aligned data for ranking or scaling.

Together looks for movement in the same direction. Earlier and Later consider positive and negative correlations; a negative result is labeled inverse. Each source is represented once per view at its strongest lag. The app requires at least 40 pre-window pairs to estimate a source-to-stock volatility ratio and enough paired observations in the selected period for ranking. Lag searches are shorter in short windows. Insufficient history and missing observations can mean fewer than the maximum number of lines.

The displayed graph keeps observations on their original dates; it does not shift or invert the inputs to fit. Source changes are scaled to stock volatility using the period before the visible window. Missing observations leave gaps; each segment after a gap is rebased to 100. The scale is only a way to compare shapes, not the source's actual price. Funds can hold the analyzed stock, so their correlations may be partly circular. FRED observations can be revised, and their observation dates are not necessarily when information was available. Selecting the best lag over the same period and trying multiple inputs can produce chance results. **These are descriptive in-sample associations, not forecasts, evidence of causation, investment advice, or a complete explanation of the stock.**

The previous PDF model and diagnostic code remains in the file; the ranked charts now compare external inputs rather than modeled price paths. Some PDF frameworks are not implemented.

## Sources and availability

- Directory/classification: [top-us-stock-tickers](https://github.com/zyhe16/top-us-stock-tickers), a third-party Nasdaq screener dataset. Nasdaq Trader and Twelve Data are fallback directories but do not supply this classification.
- Stock/fund and commodity futures history: unofficial Yahoo Finance endpoints accessed through public relays. Futures and funds are proxies and can behave differently from physical spot prices. Yahoo data may have use restrictions.
- WTI/Brent spot, rates, currencies, VIX, and economic policy uncertainty: [FRED](https://fred.stlouisfed.org/). The U.S. daily news-based Economic Policy Uncertainty Index is by Scott Baker, Nicholas Bloom, and Steven J. Davis. Selected FRED series have labeled Yahoo fallbacks; the fallback is not the same series. FRED economic data can be revised and time-stamped by observation period rather than release date.
- Regional historical mean temperature: [Open-Meteo Historical Weather](https://open-meteo.com/en/docs/historical-weather-api), Open-Meteo weather data under CC BY 4.0 with required attribution; its free API is for noncommercial use. Check Open-Meteo's terms for commercial use.
- Yahoo/FRED access uses public relays, including cors.dev and Jina Reader, which can see requests and may cache, fail, rate-limit, or change. Yahoo is unofficial. Availability, coverage, and results cannot be guaranteed. No provider credentials are stored in this file.
