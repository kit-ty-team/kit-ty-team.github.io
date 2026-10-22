<p align="center">
  <img src="assets/cat-heads/kitty-head-happy.svg" alt="kit+ty cat" width="96">
</p>

<h1 align="center">kit+ty · links</h1>

<p align="center">
  <strong>kit plus thank you</strong>: the shared common fund for group trips, with no one holding the money.<br>
  <a href="https://kit-ty-team.github.io"><strong>kit-ty-team.github.io</strong></a> ·
  <a href="https://github.com/marco-pedron/kit-ty">main repo</a>
</p>

---

The link page we hand out at events through a QR code: team, project and socials in one place.
One static `index.html`, no frameworks, no trackers, no external requests.

Psst: there are a few easter eggs hidden in the page. 🐾

## Update the links

1. Edit the `href` of the button in `index.html`. Placeholders look like `[URL_INSTAGRAM]`; find what's left with
   ```bash
   grep -n '\[[A-Z0-9_]*\]' index.html
   ```
2. To drop a button, delete its whole `<li> … </li>` block.
3. Commit and push to `main`. GitHub Pages republishes in about a minute.

The QR code points to the page, not to the single links, so it never needs to be reprinted when links change.

## Security

The page ships a Content Security Policy that only allows its own inline script and style, pinned by SHA-256 hash.

- Changing links or text: nothing to do.
- Changing the `<script>` or `<style>` block: recompute the hashes, or the browser will block your changes.
  ```bash
  python3 -c "import re,hashlib,base64;s=open('index.html').read();[print(t,base64.b64encode(hashlib.sha256(re.search('<'+t+'>(.*?)</'+t+'>',s,re.S).group(1).encode()).digest()).decode()) for t in ('style','script')]"
  ```
  Then paste the two values into the `Content-Security-Policy` meta tag.

## What's inside

| Path | What |
|---|---|
| `index.html` | The whole page: markup, CSS, JS, the animated mascot and the *Fill the kitty* mini game |
| `assets/cat-heads/` | Pixel-art cat heads. `kitty-head-*` come from the main repo, `dev-*` are the team avatars |
| `assets/og-image.png`, `favicon-32.png`, `apple-touch-icon.png` | Social preview and icons |
| `qr/` | QR codes to the page (error correction H): `kit-ty-qr.svg` for print, `kit-ty-qr.png` for screens, `kit-ty-qr-logo.png` with the cat |
| `.nojekyll` | Serves files as they are, without Jekyll |
