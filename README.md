# ILAD 2026 Seating Lookup

Static, single-page seating lookup tool. No backend, no build step.

## How the lookup behaves

- Guest types their name and presses **Find my table** (or hits Enter) — no live-as-you-type search.
- If it's an exact match to a full name, their table shows immediately.
- If it's a partial match (missing middle name, name typed in a different order,
  a nickname, etc.) and only one guest matches, it still shows their table.
- If a partial match hits more than one guest (e.g. typing just "Tan"), **no
  names are shown** — the guest is asked to type more of their name instead.
- No match at all points them to the registration desk.

This means common surnames stay protected, while guests with rarer or
partially-remembered names still get through without extra typing.

## Branding

`assets/bg.png` and `assets/title.png` are your actual ILAD 2026 event banner
and wordmark. The page uses `bg.png` as a full-bleed background and overlays
`title.png` plus the search box on a translucent dark panel, so the text
stays legible against the gold light streaks on the right side of the banner.

## Swap in real guest data

Open `index.html`, find this block near the top of the `<script>` section:

```js
const GUESTS = [
  { name: "Tan Wei Ming", table: "12" },
  ...
];
```

Replace it with your actual list, one line per guest:

```js
const GUESTS = [
  { name: "Full Name", table: "12" },
  { name: "Another Guest", table: "4" },
];
```

If your list is in Excel/CSV, sort it by name column and table column, then
paste into this format — happy to convert a CSV into this array for you if
you share the file.

## Deploy to GitHub Pages (unlisted)

1. Create a new **public** GitHub repo (e.g. `ilad-2026-seating`).
2. Upload `index.html`, `robots.txt`, and the whole `assets/` folder
   (`assets/bg.png`, `assets/title.png`) to the repo root, keeping the same
   folder structure as here.
3. Go to **Settings → Pages**, set source to the `main` branch, root folder.
4. GitHub gives you a URL like:
   `https://<your-username>.github.io/ilad-2026-seating/`
5. Share that link directly with guests (email/QR code). It won't show up
   in Google search results because of `robots.txt`, but anyone with the
   exact link can open it — it is not password-protected.

## Notes

- "Unlisted" ≠ private. Don't put anything more sensitive than full names
  in the guest list (no NRIC, contact numbers, dietary/medical notes) since
  the repo itself is technically public, and the full guest list is visible
  in the page's source code to anyone who looks.
- To take it down after the event, just delete the repo or disable Pages
  in Settings.
