# SignalTrace timing update

## Install the update

1. Replace the existing `index.html` at the top level of your SignalTrace GitHub repository with the `index.html` in this folder and commit it.
2. Wait for GitHub Pages to redeploy, then refresh your website. If the old view persists, try a hard refresh.

The site remains a single static file. No server, API key, or new dependency is required. The file has not been uploaded to GitHub automatically.

## Use the new views

Run a stock analysis as usual. Above the chart, choose:

- **Together:** the three existing closest price lines, ranked by price-index RMSE.
- **Later:** up to two independent market or economic signals whose daily changes show the strongest positive correlation after stock movements.
- **Earlier:** up to three independent signals whose daily changes show the strongest positive correlation before stock movements.

The timing views scan lags of 1–10 trading sessions (less for short windows), rank each source by its strongest positive correlation in the selected window, and show each source once per view. The correlation and matched sample count are displayed. Results are recalculated when the range changes; fewer than the requested number of lines may be shown if there is insufficient history or a source is unavailable.

For the timing charts, source movements stay on their **actual dates**; they are not shifted to force a match. Their changes are scaled using the ratio of stock and source volatility fitted before the displayed range, so different units can be viewed together. The lag is selected using the displayed window itself. This is an in-sample screening exercise, not a forecast or proof of causation. Testing many sources and lags can produce chance matches; FRED observation dates may not reflect when information became available. The app uses available market and macro proxies, not an exhaustive list of possible causes. Some formulas in the supplied PDF are not implemented.

The site still depends on external providers and public relays that may cache, rate-limit, fail, or change. Yahoo's unofficial data source may have use restrictions; review provider terms before public or commercial deployment.
