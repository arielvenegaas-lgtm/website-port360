# 360 Ports

A small, read-only library of unofficial Xbox 360 homebrew ports.

The whole site is one static HTML file (`index.html`) plus game downloads and cover images. No build step, no framework, no backend.

## Games

| Game | Original game by | Download | Size |
| --- | --- | --- | --- |
| Patrick's Parabox | Patrick Traynor | [`games/patricks-parabox-xbox360.zip`](games/patricks-parabox-xbox360.zip) | 3.4 MB |
| Sort the Court | Graeme Borland | [`games/sort-the-court-xbox360.zip`](games/sort-the-court-xbox360.zip) | 7.5 MB |

Both downloads contain an ELF32 build for a homebrew-enabled Xbox 360.

## Project layout

```
index.html                     The site (styles, game data and script inline)
360 Ports.html                 Redirect to index.html for the old filename
games/                         Downloadable ZIP files
covers/                        600x900 cover images (WebP)
.nojekyll                      Tells GitHub Pages to serve files as-is
```

## Add or update a game

1. Put the ZIP in `games/` and use a clean lowercase filename, for example `games/my-port-xbox360.zip`.
2. Optional: add a 600x900 cover to `covers/` (WebP or JPEG).
3. Edit the JSON inside `<script type="application/json" id="library">` in `index.html`.
4. Update the top-level `"updated"` date.

Each game entry supports:

```json
{
  "id": "my-port",
  "title": "My Port",
  "author": "Original developer",
  "bytes": 12345678,
  "url": "games/my-port-xbox360.zip",
  "cover": "covers/my-port.webp",
  "desc": "Short description shown in the details sheet.",
  "tags": ["Puzzle"],
  "added": "2026-10-24",
  "sha256": "sha256 of the zip"
}
```

Keep `url` and `cover` relative so the site works from any path. The site is read-only on purpose: there is no editor or `system` tab, so visitors cannot change the library.

Generate the size and checksum with:

```sh
stat -c %s games/my-port-xbox360.zip
sha256sum games/my-port-xbox360.zip
```

## Preview locally

```sh
python3 -m http.server 8080
```

Then open <http://localhost:8080/>.

## Publish with GitHub Pages

1. Push this repository to GitHub.
2. Open **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Select branch **main** and folder **/ (root)**, then save.

The site will be available at <https://arielvenegaas-lgtm.github.io/website-port360/>.

## Credits and legal

These are unofficial fan ports shared for preservation. The original games, cover art, and trademarks belong to their respective creators. This project is not affiliated with Microsoft, Xbox, or the original developers. Support the original games where you can.
