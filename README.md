# SignalTrace — Precursor Focus

## Install on GitHub Pages

1. In your existing `SignalTrace` GitHub repository, replace the root **`index.html`** with the `index.html` in this folder. Keep the filename exactly `index.html`.
2. Commit the change to the branch GitHub Pages publishes, wait for the Pages deployment, and refresh the site. No server or API key is required for the site itself.
3. Enter a U.S. company or ticker, select a range, then press **Analyze**. Select **Load expanded data** only if you want the larger, slower finite catalog. Data-provider outages and rate limits are possible; coverage reports what loaded.

The patch was prepared against the live `eric-automates.github.io/SignalTrace/` file observed on October 31, 2026. It is **not automatically deployed** to your repository.

## What changed

- **Prior movement first.** The visible same-session, later-movement, and unrestricted input-explore views are removed. The main rankings show only source inputs whose lag was selected on the first 70% of the chosen window and whose separate last-30% sample has at least 15 pairs, the same correlation sign, and an absolute correlation of at least 0.03. The threshold is a minimal display screen, not a statistical-significance claim. If no candidate qualifies, the app says so.
- **Earlier-matched capsule rows.** Only inputs with at least one selected-window source-confirmation-to-later-stock-confirmation match are shown, in addition to the stock row. Other loaded inputs remain in coverage counts and are still considered by the independent combination analysis. Not showing an input does not prove it has no relationship.
- **Combination results.** The worker still screens individual signals, pairs and a smaller set of triples, with positive 1–10-session leads and separate chronological training, validation and final holdout intervals. Cards with zero final-holdout matches are hidden. **Because the display filter uses the holdout too, displayed cards are selected partly on holdout results:** do not treat the displayed set as an untouched final test. The false-alert counts remain visible. The worker is finite and not an exhaustive search.
- **Color meaning.** Green stock segments and capsules indicate rises; red indicates drops. Gold identifies earlier candidates and outlines matched capsules. Matching numbers connect earlier and later historical events. A gold border is a visual connection, **not evidence that the source caused the move**.
- **Combination visual.** The gold dots at the top of the chart mark the earlier source observation dates for up to 20 visible held-out matches; dotted lines connect to the later stock-event dates. The indexed lines themselves keep their actual dates. Multiple components can have different selected lags. The chart is a visual guide, not a forecast.
- **Thumb controls.** The small floating buttons go to the top, combination research, capsule timeline and bottom. Press **⇄** to move the controls between the right and left edge; the preference is kept in your browser. Until a ticker is analyzed, research/timeline controls return focus to the ticker field.
- **Music.** Select **Add songs** at the bottom and choose audio files from your device. They stay on that device and are not uploaded. The built-in loop remains available; audio is off until you press play.

## Research attempted for one new public-data family

Two exploratory public-data families were tested across whole groups rather than being added for a single symbol:

1. **Wikipedia attention:** Daily user pageviews for four energy-related topics were compared with SPY-adjusted returns of eight U.S. energy stocks; four technology topics were also checked against eight semiconductor stocks. The topic change was compared at a two-trading-session lag, using chronological 60/20/20 training, validation and holdout periods, approximately November 2021–October 2026. The energy-topic relationships changed sign in validation or were weak in the final period. The technology results were also weak or inconsistent. This limited screen did not establish a useful reproducible directional precursor.
2. **TSA passenger counts:** A daily TSA checkpoint-count mirror was checked against eight airline stocks, using same-weekday/rolling changes dated at least four calendar days before the stock session and the same chronological split. The resulting relationships were weak or inconsistent across periods. The mirror reports an approximately two-day publication lag; four days is a conservative proxy, not proof of historic availability at that time.

Neither family was added as a validated precursor. These are exploratory tests, not definitive proof that the data cannot be useful. The sample used present-day symbols (survivorship bias), the eight stocks share sector shocks, and simple correlation p-values assume independence. The holdouts were inspected and should not be reused as untouched discovery tests. No demonstrated causal effect, profitable strategy, point-in-time feed, or trading recommendation was established. Wikimedia data can have naming, redirect, timezone and revision issues; the TSA mirror may fail or revise historical data.

References: [Wikimedia Pageviews API](https://wikimedia.org/api/rest_v1/), [Trading on Attention walk-forward study](https://github.com/lucasdmruga/trading-on-attention), [TSA passenger volumes](https://www.tsa.gov/travel/passenger-volumes), [TSA data mirror](https://github.com/bcantoni/tsa-data), and [airline/passenger-volume paper](https://www.accessecon.com/Pubs/EB/2021/Volume41/EB-21-V41-I3-P182.pdf).

## Important limitations

This remains an exploratory historical signal screen, not a causal model, execution backtest, or investment recommendation. Public weather and economic series may be revised, reflect a different timezone, or be published after the observation date; an observation dated earlier than a stock movement is not necessarily information that was actually available earlier. Stocks can share a common driver; a sector fund can contain the stock being studied; stock-derived inputs are not independent. Trying many series, lags and combinations can create chance matches. Percentages are historical match fractions, not probabilities of future success or profit. A small sample or an uncorrected p-value is not strong evidence. No correction for the full search or trading costs is included, and repeatedly changing the range reuses data.

The current sector/industry cross-reference and weather regions are broad proxies, not verified facilities, suppliers or customers. The expanded data catalog is finite, not exhaustive. Only part of the originally supplied PDF formulas is implemented. Open-Meteo historical data require attribution and its free API is intended for noncommercial use. Yahoo endpoints are unofficial; provider terms, availability and rate limits apply. Some sources use third-party relays that can see requests. The application and downloaded music have no relationship to a brokerage account.
