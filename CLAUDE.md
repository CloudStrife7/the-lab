# The Lab — Project Context

## What this is
A personal 3D printing hobby donation page. Not a business. The owner runs a Bambu Lab P1S and prints things for people for free. The page is styled as a printer enclosure / ghost-in-the-machine terminal UI.

**Owner's name does not appear anywhere on the page.** Do not add it.

## Live site
- URL: https://cloudstrife7.github.io/the-lab
- Repo: https://github.com/CloudStrife7/the-lab
- Deploy: push to `main` → GitHub Actions builds and deploys to GitHub Pages (~60s)

## Tech stack
- Astro 5 (static output), **Node 22 required** (Node 20 will fail the build)
- Single page: `src/pages/index.astro` — all CSS, HTML, and JS are intentionally inline. Do not split into separate files.
- Static assets in `public/` are served at `/the-lab/<filename>` due to `base: '/the-lab'` in `astro.config.mjs`
- No framework, no components, no TypeScript beyond the default tsconfig

## Deploy workflow
```
git add <files>
git commit -m "message"
git push origin main
```
GitHub Actions handles the rest. Watch at https://github.com/CloudStrife7/the-lab/actions

## Current design state (as of 2026-05-29)
**Theme:** Ghostly dark — near-black background, off-white/grey content text, muted teal/amber/green accents (not neon). Dark bg + white glitchy fonts was the direction.

**Color palette (key vars):**
- `--accent-teal: #48b8b0` — machine-id, section labels, path highlight, tier amounts, button, cursor
- `--accent-amber: #b89050` — table $ values, featured tier amount, footer temps
- `--accent-green: #52a868` — status dot, PRINTER LED
- `--accent-dim: #a8a8c0` — "THE MACHINE" color, secondary labels
- `--text-bright: #ececf4` — "THE GHOST IN" color, h1, tier names

**Scan lines:** Applied only to `.enc-rail`, `.enc-side`, `.enc-footer` (the chrome frame). NOT a full-page overlay — it made text hard to read.

**Page sections (top to bottom):**
1. Status bar (BAMBU_P1S // ONLINE, clock, enclosure temp)
2. Enclosure rail (THE LAB machine-id, PRINTER/AMS/NET LEDs)
3. Side panels (decorative, scan lines)
4. Build plate content area:
   - Path line + H1 "THE GHOST IN THE MACHINE"
   - NEXT PRINTER FUND progress bar (hardcoded 34%)
   - // MISSION STATEMENT (quiet, no shouting, no owner name)
   - // WHERE IT GOES (cost table)
   - // SUPPORT TIERS (4 tier cards)
   - // LIVE STREAM (looping GIF from `public/stream.gif`)
   - // SUPPORT LINK (Ko-fi button — placeholder URL, no account yet)
   - Terminal typewriter line
5. Enclosure footer (firmware/temp readouts)

**GIF stream:** `public/stream.gif` — converted from `C:\Users\cloud\Downloads\1779454976660_0.mp4` at 320px wide, 10fps. Referenced in HTML as `/the-lab/stream.gif`.

**Ko-fi:** Button links to `https://ko-fi.com` — placeholder. Owner has no Ko-fi account yet.

## Hard rules (learned from owner)
- **Never add features that weren't asked for.** A viewer count was added to the stream unprompted and immediately removed.
- **No owner name anywhere** — not in copy, rail, title, footer, side labels.
- **Keep copy quiet** — no bold declarations, no all-caps emphasis in the info block. Conversational tone.
- **CSS/JS stays inline** in `index.astro`. No refactoring.
- **Don't add comments** to code unless the why is non-obvious.

## Last session (2026-05-29)
- Built site from scratch: scaffolded Astro, fixed Node 20→22 deploy failure, got GitHub Pages live
- Overhauled theme from cyan/neon hacker to ghostly white/grey muted palette
- Moved scan lines from full-page to chrome-only
- Removed owner name from all locations
- Softened copy (removed "THIS ISN'T A BUSINESS" strong tags, sub-title)
- GHOST word glitch effect (VT323 font flicker) — added then reverted on request
- Fixed many dim text colors that were near-invisible (#3a3a48 on near-black bg)
- Added // LIVE STREAM section with GIF from owner's MP4
- Installed FFmpeg via winget for the MP4→GIF conversion
