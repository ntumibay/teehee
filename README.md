A hand-drawn, cream-paper love letter page with a runaway "No" button,
a date-type picker, and a calendar for picking a day — built as one
self-contained HTML file so it can run free on GitHub Pages.

## What's in here

```
index.html        ← the whole site (structure + style + behavior)
music/            ← put your background-music file here
README.md         ← this file
```

## 1. Add the music

The page is wired to look for a file at `music/fly-love.mp3` and loop it
in the background, triggered by the little speaker button (bottom-right).

I didn't bundle an actual audio file because "Fly Love" is a copyrighted
commercial track — I can't generate, embed, or pull a copy of it for you.
To add it yourself, legally:

- If you own the track (bought it on iTunes/Bandcamp, ripped your own CD,
  etc.), export/convert your copy to `.mp3` and drop it in `music/`,
  named exactly `fly-love.mp3`.
- If you'd rather not deal with rights at all, swap in a royalty-free
  "lounge/soul" instrumental from a site like Pixabay Music or
  Free Music Archive — same filename, same folder, zero risk.

You can rename the file/folder if you want — just update this line near
the top of `index.html`:

```html
<source src="music/fly-love.mp3" type="audio/mpeg">
```

**Note on autoplay:** browsers block audio from auto-starting before the
user interacts with the page. That's why there's a tap-to-play music
button rather than music starting automatically — it'll work the instant
Angie taps it.

## 2. Customize it for real

Open `index.html` in any text editor. Everything you'll want to tweak is
clearly grouped:

- **The headline / letter text** — search for `id="askHeadline"` and the
  `<p class="sub">` tags, both in the "ask" screen and the "planner" screen.
- **"No" button captions** — the `captions` array in the `<script>` near
  the bottom. Add your own lines, in your own voice.
- **Date-type cards** — the `dateTypes` array. Each entry has an `id`,
  a `label`, and an inline SVG (`svg`) for the icon. Swap labels, add/remove
  entries, or replace the SVG path data with your own doodles.
- **Your free days** — look for:
  ```js
  const CAL_YEAR = 2026;
  const CAL_MONTH = 6; // 0-indexed, 6 = July
  const FREE_DAYS = [3, 4, 10, 11, 17, 18, 19, 24, 25, 31];
  ```
  Change the month/year and list the day numbers you're actually free —
  those are the only days that light up as clickable on the calendar.
- **Colors** — at the very top of the `<style>` block, the `:root` CSS
  variables (`--paper`, `--ink`, `--rose`, `--sage`, `--gold`). Change any
  hex value and it cascades through the whole page.

## 3. Put it on GitHub Pages (free hosting)

1. Create a new repository on GitHub (public is fine, and free).
2. Upload `index.html` and the `music/` folder (with your mp3 inside) to
   the root of that repo.
3. Go to the repo's **Settings → Pages**.
4. Under "Build and deployment", set **Source** to "Deploy from a branch",
   branch `main`, folder `/ (root)`. Save.
5. GitHub gives you a URL like:
   `https://yourusername.github.io/your-repo-name/`
   It usually takes a minute or two to go live.
6. Send Angie that link.

No server, no cost, no account needed on her end — she just opens the link.

## How the "No" button works

It doesn't actually reject anything — there's no path where clicking it
counts as "no." On hover (or tap, on mobile) it teleports to a random spot
on screen, leaves a little ink "skid mark," and cycles through a list of
playful captions. After a few dodges it nudges toward just hitting "Yes."

## Browser support

Plain HTML/CSS/JS, no build step, no dependencies except two Google Fonts
loaded over a CDN link. Works in any modern browser, phone or desktop.
