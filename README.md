# hinkson.github.io

The root of `hinkson.github.io`. The real sites are GitHub Pages project sites in their own
repos (`everyday-apps`, `altas-affirmations`); a project site cannot serve files at the
host root, so this repo exists for the two things that must live there:

- **`.well-known/apple-app-site-association`**: lets iOS open Heartprint friend links
  (`/everyday-apps/heartprint-match.html#<code>`) straight in the app (universal links,
  Heartprint 1.2, 2026-11-05). The app's half is the `applinks:hinkson.github.io` entitlement
  in `Heartprint/Heartprint.entitlements` in the projects monorepo. Apple reads this file
  through its CDN when the app installs: `https://app-site-association.cdn-apple.com/a/v1/hinkson.github.io`.
  It must stay valid JSON, served over HTTPS with no redirect. To add another app, add a
  `details` entry with its `<team>.<bundle id>` and the paths it owns.
- **`index.html`**: sends the bare root to the Everyday site instead of a 404.

`.nojekyll` is load-bearing: Jekyll skips dot-folders, so without it `.well-known/` is never
published.
