# The Lab — Zach's 3D Print Lab

[![Deploy to GitHub Pages](https://github.com/CloudStrife7/the-lab/actions/workflows/deploy.yml/badge.svg)](https://github.com/CloudStrife7/the-lab/actions/workflows/deploy.yml)
[![Live Site](https://img.shields.io/badge/live%20site-cloudstrife7.github.io%2Fthe-lab-00ffe0?style=flat&logo=github)](https://cloudstrife7.github.io/the-lab)

A hobby-funded 3D printing donation page. Not a business — just a guy with a Bambu Lab P1S who enjoys making things for people and wants to keep the machine running.

---

## Live Site

**[https://cloudstrife7.github.io/the-lab](https://cloudstrife7.github.io/the-lab)**

---

## Tech Stack

| Tool | Purpose |
|---|---|
| [Astro](https://astro.build) | Static site framework |
| GitHub Pages | Free static hosting |
| GitHub Actions | Auto-deploy on push to `main` |
| Ko-fi | Donation handling |
| Google Fonts | Orbitron, Share Tech Mono, VT323 |

---

## Design Concept

The site is themed around a **Bambu Lab P1S 3D printer**:

- The outer dark frame with corner bolts and side panels = **the enclosure**
- The inner grid-texture area = **the build plate** (where all content lives)
- Aesthetic draws from BasementOS — retro DOS terminal, CRT scanlines, monospace fonts

---

## Local Development

### Prerequisites
- Node.js 18+
- npm

### Setup

```bash
git clone https://github.com/CloudStrife7/the-lab.git
cd the-lab
npm install
npm run dev
```

Site will be available at `http://localhost:4321`

### Build

```bash
npm run build        # outputs to ./dist
npm run preview      # preview the production build locally
```

---

## Deployment

Deployment is fully automated via GitHub Actions. Every push to `main` triggers a build and deploys to GitHub Pages.

**Workflow file:** `.github/workflows/deploy.yml`

To deploy manually:
```bash
git add .
git commit -m "your message"
git push origin main
```

GitHub Actions handles the rest. The live site updates within ~60 seconds.

### First-time GitHub Pages setup (one-time only)

1. Go to your repo on GitHub → **Settings → Pages**
2. Under **Source**, select **GitHub Actions**
3. Save — the next push will deploy automatically

---

## Project Structure

```
the-lab/
├── .github/
│   └── workflows/
│       └── deploy.yml       # GitHub Actions deploy workflow
├── src/
│   └── pages/
│       └── index.astro      # Main page (all HTML, CSS, JS inline)
├── public/
│   └── last_print.jpg       # Drop your latest print photo here (optional)
├── astro.config.mjs          # Astro config (site + base for GitHub Pages)
├── package.json
└── README.md
```

---

## Updating the Last Print Photo

Drop a new `last_print.jpg` into the `public/` folder and push. The site will display it automatically once deployed.

```bash
cp ~/my-cool-print.jpg public/last_print.jpg
git add public/last_print.jpg
git commit -m "update last print photo"
git push
```

---

## Planned Features

- [ ] Live printer status panel via P1S MQTT (nozzle temp, bed temp, print progress, layer count)
- [ ] Last print photo display panel
- [ ] Ko-fi donation goal progress bar (live)
- [ ] Print request form

---

## License

Personal hobby project. Not for commercial use.

---

*Built with love and too much filament by [CloudStrife7](https://github.com/CloudStrife7)*
