# funklunsford.com

The owner's own domain, served by GitHub Pages from this repo (`main`, at its root; `CNAME` names the domain).

- **/** — the home page: a hello, and the way into each section (the about section is commented out until it has words).
- **/substack/**, **/puzzles/**, **/poetry/** — the three sections. Puzzles links to each game through its short link below.
- **/strokes** forwards to https://strokes.fun/.
- **/mountweazel** forwards to https://funklunsford.github.io/mountweazel/.
- **/puzzleplaylist** forwards to https://funklunsford.github.io/playlist/ (the Puzzle Playlist's home; there's no strokes.fun/playlist).

Each forward uses `location.replace`, so it doesn't stay in the browser's history (Back from a game returns to the
playlist, not here), and it keeps the address's `?search` and `#hash`, so a playlist link like
`funklunsford.com/puzzleplaylist#add=…` still adds its puzzles. `404.html` forwards deeper addresses under each short
link the same way (and `/playlist` as `/puzzleplaylist`).

## The pages

Plain HTML, no build step: every page links `/style.css` (warm paper and earth tones, the Fraunces font from Google
Fonts, hand-drawn lines and loose shapes) and repeats the same header. Light and dark follow the device.

- **A post** lives at `substack/<slug>/index.html`. Copy `templates/post.html` there, change the title, description,
  date and words, delete its `robots` line, and add the post to the top of the list in `substack/index.html` (the
  comment there shows the shape).
- **A poem** lives at `poetry/<slug>/index.html`, from `templates/poem.html` the same way. Each `<p>` is a stanza and
  its line breaks are kept as written.
- The "Nothing planted yet" note on each list hides itself once the list has an item.
- `images/` holds each game's own icon, copied from its repo.

This is an ordinary project repo with its own custom domain, not the account's user site
(`funklunsford.github.io`). A domain on the user site would move every project site under it, and the playlist and
Mountweazel stay at their github.io addresses.

## DNS (Cloudflare, all **DNS only**, not proxied)

`funklunsford.com-dns.txt` holds these as a zone file, to import in Cloudflare (DNS > Records > Import and Export),
with "Proxy imported DNS records" left unticked.

| Type | Name | Content |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| AAAA | @ | 2606:50c0:8000::153 |
| AAAA | @ | 2606:50c0:8001::153 |
| AAAA | @ | 2606:50c0:8002::153 |
| AAAA | @ | 2606:50c0:8003::153 |
| CNAME | www | funklunsford.github.io |
