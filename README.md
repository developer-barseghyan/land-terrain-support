# Land Terrain support site

Support, privacy policy and terms of use for **Land Terrain: Topo & Drainage**, in the same Jekyll layout as the
other apps' support sites (Deed to Map's `deed-to-map-support`), with Land Terrain's own colors
(`docs/design-tokens.md`), light and dark. This folder is the source; it is published as its own GitHub
repository, `land-terrain-support`. (This README is excluded from the published site in `_config.yml`.)

| Page | File | URL | App Store Connect field |
|---|---|---|---|
| Support | `index.md` | https://developer-barseghyan.github.io/land-terrain-support/ | Support URL (and Marketing URL, optional) |
| Privacy | `privacy.md` | https://developer-barseghyan.github.io/land-terrain-support/privacy | Privacy Policy URL |
| Terms | `terms.md` | https://developer-barseghyan.github.io/land-terrain-support/terms | License Agreement: leave Apple's standard EULA; the terms link is in the app and the description |

The app opens exactly these three URLs (`LandTerrainApp/LandTerrain/Support/SupportLinks.swift`: Settings › About ›
Help and support and Terms of use, the Privacy page's "Read the full privacy policy", and the paywall's Terms of
Use and Privacy Policy links). If the repository name or the account ever changes, change both.

The Universal Links files are **not** here: they belong to the root site and are in `../site-root/` (part 3).

## Before publishing

- The effective date is 23 November 2026 on `privacy.md` and 24 November 2026 on `terms.md`. Change it to the release date if you prefer.
- The contact address is developer.barseghyan@gmail.com on every page.
- Section 9 of the terms assumes you publish from Armenia, as in Deed to Map's terms.

## 1. Create the repository and publish

Run from the root of the Land Terrain repository. The site gets its own checkout next to this project (like
`../developer-barseghyan.github.io`), so the support repository is never nested inside this one.

```bash
rsync -a --delete --exclude README.md --exclude .git site/ ../land-terrain-support/
```

```bash
cd ../land-terrain-support && git init -b main && git add . && git commit -m "Land Terrain support site"
```

With the GitHub CLI (signed in as developer-barseghyan):

```bash
gh repo create developer-barseghyan/land-terrain-support --public --source . --push
```

Without it: on github.com create a **public** repository named `land-terrain-support` with no README, then:

```bash
git remote add origin https://github.com/developer-barseghyan/land-terrain-support.git && git push -u origin main
```

Then on github.com: the repository › **Settings › Pages › Build and deployment** › Source **Deploy from a branch**,
Branch **main**, folder **/ (root)**, **Save**. After a minute or two all three pages answer 200:

```bash
for p in "" privacy terms; do curl -s -o /dev/null -w "%{http_code} $p\n" "https://developer-barseghyan.github.io/land-terrain-support/$p"; done
```

If `/privacy` or `/terms` gives 404 while `/` works, wait another minute (Pages builds the site once per push).

## 2. Later changes

Edit the files here in `site/`, commit them in the Land Terrain repository, then copy and push:

```bash
rsync -a --delete --exclude README.md --exclude .git site/ ../land-terrain-support/
```

```bash
cd ../land-terrain-support && git add -A && git commit -m "Update support site" && git push
```

## 3. Turning on Universal Links (later, optional)

Shared parcel links (`https://developer-barseghyan.github.io/landterrain/parcel?kml=…`) open the app directly once
this is done. Until then the app still opens `landterrain://parcel?…` links. Do it in this order, so signing
never breaks:

1. **App ID.** In the Apple Developer portal, Certificates, Identifiers & Profiles › Identifiers ›
   `com.tigranbarseghyan.landterrain` › enable **Associated Domains** › Save. (Xcode's automatic signing
   regenerates the profiles on the next build.)
2. **The root site.** Copy the two files from `site-root/` into the root site's checkout and publish. That site
   already has a `.nojekyll` file, so the `.well-known` folder is served as is.

   ```bash
   rsync -a site-root/.well-known site-root/landterrain ../developer-barseghyan.github.io/
   ```

   ```bash
   cd ../developer-barseghyan.github.io && git add .well-known landterrain && git commit -m "Land Terrain Universal Links" && git push
   ```

3. **Check the file.** Both must return the JSON with `38Y5ZDNXS5.com.tigranbarseghyan.landterrain`. The second is
   Apple's CDN, which is what iPhones actually read; it can take a day to refresh. GitHub Pages serves the
   extensionless file as `application/octet-stream`; if Apple's CDN returns the JSON, that is accepted.

   ```bash
   curl -s https://developer-barseghyan.github.io/.well-known/apple-app-site-association
   ```

   ```bash
   curl -s https://app-site-association.cdn-apple.com/a/v1/developer-barseghyan.github.io
   ```

4. **The entitlement.** Add this to `LandTerrainApp/Config/LandTerrain.entitlements`, inside the `<dict>` (the
   project already points at that file, so `gen_project.py` needs no change):

   ```xml
   <key>com.apple.developer.associated-domains</key>
   <array><string>applinks:developer-barseghyan.github.io</string></array>
   ```

5. **Test on a phone.** Build and run on a device, put a link such as
   `https://developer-barseghyan.github.io/landterrain/parcel?name=Test&geojson=…` in Notes and tap it: the app
   opens with the import sheet. Without the app, the same link shows the page from `site-root/landterrain/parcel/`.
   Then run `scripts/run-all-tests.sh`, remove the "placeholder" note in `Input/DeepLink.swift`, and commit.
