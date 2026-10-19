# Kegler website

The home page, support page and privacy policy of [Kegler](https://kegler.ratsep.org), a bowling
score log for iPhone. The app itself lives in
[doofyus/kegler-app](https://github.com/doofyus/kegler-app).

Live at <https://kegler.ratsep.org>.

## Pages

| Path | Page |
|---|---|
| `/` | Home: what the app does, its screens, the price |
| `/support/` | Contact and common questions |
| `/privacy/` | Privacy policy |

The App Store listing and the app's Settings link to the support page and the privacy policy, so
those two URLs must keep working.

## Files

```
index.html          home page
support/index.html  support
privacy/index.html  privacy policy
style.css           every page's styles, light and dark
images/             the app's screens, a light and a dark version of each
icon.png            the app icon (also the touch icon)
favicon.png
CNAME               the custom domain for GitHub Pages
.nojekyll           serve the files as they are, without Jekyll
```

Plain HTML and CSS, with a little JavaScript on the home page for its animations. There is no
build step and nothing to install.

## Working on it

Serve the folder and open <http://localhost:8765>:

```sh
python3 -m http.server 8765
```

- **Light and dark:** the pages follow the system appearance. Each screenshot comes in
  `images/<name>-light.jpg` and `images/<name>-dark.jpg`, picked with `<picture>`.
- **Screenshots:** taken from the app's demo season (`-demoSeason` launch argument in a Debug
  build) on an iPhone 17 Pro Max simulator, then resized to 1300 px high.
- **The pin sweep** on the entry screen is placed in percent of the screenshot. If that screenshot
  changes, measure the pins again and update `data-pin` positions in `index.html` and the sizes in
  `style.css`.
- **Cache:** the pages load `style.css?v=N`. Raise `N` on every page whenever `style.css` changes,
  so browsers fetch the new one.
- **Motion:** every animation is skipped under Reduce Motion and without JavaScript.

## Publishing

GitHub Pages serves the `main` branch from the repository root. A push to `main` is live within a
minute or two.

The domain is set in `CNAME` and in the repository's Pages settings. DNS (Namecheap): a `CNAME`
record from `kegler` to `doofyus.github.io.`. HTTPS is enforced.

## Contact

<kegler@ratsep.org>
