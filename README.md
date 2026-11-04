# QubitArt — app pages

The public support and privacy pages for apps published by Filippo B., served by GitHub Pages at
<https://fburattini.github.io/qubitart-apps/>.

Every app store wants two public URLs per app — a privacy policy and a support page — and wants
them to stay reachable for as long as the app is listed. This repository is that, and nothing else:
static HTML, no build step, no dependencies, no scripts, no analytics. A policy page that tracked
its readers would be its own joke.

## Layout

```
index.html               the site's front page: every app, with its links
assets/style.css         one stylesheet, shared by every page
<app-slug>/
  index.html             the app's own page
  privacy/index.html     its privacy policy      -> /<app-slug>/privacy/
  support/index.html     its support page        -> /<app-slug>/support/
```

Each page is served at its directory, so the URLs have no `.html` in them and stay stable if a page
is ever rewritten.

## Adding an app

1. Copy an existing app folder and rename it to the new app's slug (lowercase, hyphens).
2. Rewrite the three pages. Keep the `../` and `../../` stylesheet paths as they are: these are
   project Pages, served from a subdirectory, so a root-relative path would break.
3. Add a row to `index.html`.
4. Commit and push. Pages redeploys on its own, usually within a minute.

## Rules worth keeping

- **No build step.** Anyone should be able to fix a typo from the GitHub web editor.
- **No external resources.** No fonts, no CDNs, no scripts. Every page must render with the network
  off after first load, and must never make a request a privacy policy would have to disclose.
- **Say the effective date on every policy**, and change it whenever the text changes.
- **Never delete a policy URL.** A store listing points at it for as long as the app is listed.
  Rewrite the page in place instead.

## Where the facts come from

For Nobody Comes Back, the privacy policy is the player-facing rendering of `docs/privacy.md` in
that game's own repository, which holds the same facts in the vocabulary the two store consoles
ask for. If one changes, change the other.
