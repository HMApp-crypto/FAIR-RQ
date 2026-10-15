# FAIR Risk Calculator

A cyber risk quantification calculator based on the FAIR model. Enter each factor as a min / most likely / max range and the annual loss exposure recalculates as you type (10,000 simulated years per run).

It is a static web app: no server, no database, no sign-in. Everything runs in the browser, and scenarios are saved in that browser. Nothing is sent anywhere.

## What's in this folder

| File | What it does |
|---|---|
| `index.html` | The whole app: page, styles and calculation engine |
| `manifest.webmanifest` | Lets browsers install it as an app (name, icon, colours) |
| `sw.js` | Keeps a copy of the app so it opens offline |
| `icons/` | App and browser-tab icons |
| `fonts/` | IBM Plex fonts, served with the app (no calls to Google) |

Keep the files together. The app needs to be served over `https://` (any host below does this) for install and offline mode to work. Double-clicking `index.html` also opens a working calculator, just without install or offline support.

## Put it online

### Option A: GitHub Pages (recommended)

Free for public repositories, and the repository shows your work to anyone you share it with.

1. Sign in at github.com and create a new **public** repository, for example `fair-risk-calculator`.
2. On the repository page choose **Add file → Upload files**, drag in everything from this folder (keep the `icons` and `fonts` folders), and commit.
3. Go to **Settings → Pages**. Under *Build and deployment*, set *Source* to **Deploy from a branch**, branch **main**, folder **/ (root)**, and save.
4. After a minute or two the site is live at `https://<your-username>.github.io/fair-risk-calculator/`.

To update later, upload the changed files again. The app picks up the new version the next time it is opened online.

### Option B: Netlify

1. Create a free account at netlify.com.
2. Go to **Sites → Add new site → Deploy manually** and drag this folder onto the page.
3. You get a URL straight away. You can rename it under **Site configuration**.

## Install it as an app

Open your site's URL, then:

- **Chrome or Edge (Windows, Mac, Linux):** click the install icon at the right of the address bar, or open the browser menu and choose **Install FAIR Risk Calculator**. It opens in its own window with its own icon.
- **Safari on Mac:** **File → Add to Dock**.
- **iPhone or iPad (Safari):** tap **Share → Add to Home Screen**.
- **Android (Chrome):** menu → **Install app**.

Once installed, it opens without an internet connection.

## Your scenarios

- Scenarios save automatically in the browser you use. Another browser or device starts with an empty list.
- Use **Export** to save all scenarios to a `.json` file, and **Import** to load them into another browser or device. Export now and then as a backup: clearing your browser data removes saved scenarios.
- Inside Claude, the same calculator saves to your Claude account instead, so Export and Import are hidden there.

## How the numbers are made

Each simulated year draws every factor from a PERT distribution over your range, counts loss events with a Poisson distribution, and adds primary and secondary losses per event. The page's *Model notes* section lists the assumptions and limits. Read results to two significant figures; sampling noise for rare scenarios is about ±3% between seeds.

Based on the FAIR model published by the FAIR Institute. Personal tool; not affiliated with or endorsed by the FAIR Institute. Fonts: IBM Plex, SIL Open Font License 1.1 (see `fonts/OFL-LICENSE.txt`).
