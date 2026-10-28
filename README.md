# SignalTrace — GitHub Pages edition

The website is the single file `index.html`. It does **not** need a Python server, build process, API key, or installed packages.

## Put it on GitHub Pages

1. In your GitHub repository, choose **Add file → Upload files**. Upload this version of **index.html** to the repository's top level, replacing the old `index.html` if necessary, and commit the change.
2. In the repository, open **Settings → Pages**. Under **Build and deployment**, choose **Deploy from a branch**. Select your default branch (usually `main`) and **/(root)**, then click **Save**.
3. Wait for GitHub to publish the site. The Pages screen will show the website address. Open it, type a U.S. ticker, and press Enter or **Analyze**. GitHub Pages availability can depend on repository visibility and your GitHub plan.

If your repository already uses a different Pages branch or folder, put `index.html` in that configured publishing location instead. This package has not been pushed to your repository for you.

## Use

The page automatically loads a U.S. stock directory. Choose a time range, type a ticker or company name, and select a suggestion or press Enter on a ticker. It gathers stock and comparison data in the browser and displays the three closest eligible price lines. Changing the range reuses the downloaded data. Up to five years are displayed when available.

To play songs, click **Add songs**, select audio files on your device, and press play. Your files stay on your device and must be selected again after reloading. **Loops** returns to the built-in generated music. Only use recordings you have rights to play.

## Data and limitations

The browser fetches the Nasdaq Trader stock directory and unofficial Yahoo Finance adjusted prices through public cors.dev or Jina Reader relays. It automatically tries the other relay if one fails or returns an unusable response, and temporarily reuses successful results in browser memory to reduce repeated requests. It fetches FRED economic data through cors.dev, with explicitly labeled Yahoo market proxies if FRED is unavailable. A ticker directory from Twelve Data is used if the Nasdaq directory cannot be fetched. These third-party services can see requests, cache data, rate-limit, go offline, or change; Yahoo's endpoint is unofficial and generally intended for personal use. Review the data sources' terms before public or commercial deployment. The page reports failures instead of inventing data. No uptime or complete-market coverage is guaranteed.

This Pages edition no longer includes the Fama–French five-factor data source present in the earlier Python-server version, because the static browser cannot reliably retrieve that source's ZIP file through the available public relays. It uses the other available lines and diagnostics; missing sources can reduce the number of candidates. The original Python-server version remains separate if you prefer that source.

The closest-line ranking covers **only implemented models** with complete observations in the selected range. Many are derived from the stock's own earlier prices, and some are retrospective; closeness is not proof of cause or a forecast. Only a subset of the formulas in the supplied PDF has been implemented and some other methods, including ones that might use public data, remain to be built. This tool is not investment advice.
