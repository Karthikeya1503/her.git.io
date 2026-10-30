# A little world for Lasya ♡

A bespoke, girly-pop romantic proposal experience built with **React + Vite + JavaScript**, not a static HTML template. Soft pink stationery, expressive typography, original editorial imagery, real interactions, and a hopeful little question.

## Open it locally — one command

1. Install **Node.js 20.19+ or 22.12+** (Node 24 LTS recommended), which includes npm.
2. Extract the ZIP. Open a terminal inside the `laasya-love-letter` folder (the folder containing `package.json`).
3. Run:

```sh
npm run dev
```

On the first run, the startup script automatically runs `npm ci` if dependencies are missing. **Internet is needed for that first installation.** It then starts Vite. Open the address printed in the terminal, normally **http://localhost:5173** (http://127.0.0.1:5173 also works). If 5173 is occupied, Vite prints the next available port. Press Ctrl+C to stop.

Prefer the conventional setup? `npm ci` followed by `npm run dev` works too. Dependencies are intentionally not zipped: that keeps the download small and avoids shipping platform-specific binaries. After installation, images and fonts are local and no external services are required by the site.

## Windows / npm download failure: open it offline

If installation reports `ENOTFOUND registry.npmjs.org`, npm could not resolve its download server. You can still run the complete included production build using Node alone:

```sh
npm run offline
```

Or use `npm run dev -- --offline`. Neither command downloads packages, requires node_modules, or uses an npm registry connection. Open the localhost address printed in the terminal. Extract the entire ZIP, including `dist/` and `scripts/`. No administrator rights are normally needed.

**Offline mode serves the included build; edits to src/ do not appear until you successfully install dependencies and run npm run build.** The temporary device-song chooser still works offline. Permanent soundtrack/source changes require a rebuild.

To restore live development mode, check your connection/VPN/proxy with `Resolve-DnsName registry.npmjs.org` and `npm ping`, then run `npm ci` followed by `npm run dev`. `EPERM` cleanup warnings can occur when Windows holds partially installed files open. Close other terminals/editors using this folder before retrying; if needed, extract a fresh copy into a new folder. Do not delete package-lock.json or disable security software to work around a DNS failure.

## The soundtrack — ready for the song you choose

No song has been selected, so **no audio file is bundled** and the site doesn't pretend music is playing.

1. Put your licensed song at `public/music/our-song.mp3`.
2. Edit `src/config.js`:

```js
song: {
  src: '/music/our-song.mp3',
  title: 'Your chosen song title',
  volume: 0.45
},
```

The opening **“Open your love letter”** button calls `audio.play()` during the same user gesture that enters the experience. Playback loops; the music control pauses and resumes it. Browsers may still restrict unsupported audio formats; failures are handled without blocking the experience. MP3 is the safest general choice.

Want to try a track now? Click **“sound on?”**, then **“Choose a song”**. A selected device file plays for that visit only; it is not uploaded, stored, or added to the project. Reloading clears it.

## Make it more personal

Edit **`src/config.js`** for:
- Her name, the letter's sign-off, proposal wording, letter paragraphs.
- Three flip-card notes and five date ideas.
- The permanent song and volume.

The default question is **“Will you be mine?”**, not an assumption about marriage. Replace it with your actual question if you want. The copy does not invent shared memories or pretend the still-life is a photo of either of you. Before sharing, replace the generic sign-off with your own name if desired. Page title/description in `index.html` can also be edited.

## What’s inside

- Opening invitation and user-initiated soundtrack hookup.
- GSAP ScrollTrigger entrances and a restrained desktop photo parallax.
- Lenis smooth scrolling, synchronized with GSAP's ticker.
- Motion for React button feedback, invitation transition, dialog entrance, and date-ticket transitions.
- Three flip-open notes and a wax-sealed letter.
- Optional constellation puzzle with a “show me” alternative.
- Animated date-idea roulette that always picks a different next idea.
- Three hidden collectible stars, a clue pocket, and a reward note.
- Keyboard-name Easter egg and a touch-friendly equivalent.
- Original ribbon-and-heart motion-graphics finale and a downloadable love-letter keepsake.
- A cinematic “you + me” ending, with no yes/no response buttons.
- Native focus-trapped dialogs, Escape to close, keyboard controls, reduced-motion support, and an animation-pause control.

## Privacy & response behavior

This is a frontend-only website. **No analytics, forms sent to servers, backend, accounts, or response notifications.** There are no response buttons or remote response notifications. The downloaded keepsake is local. Only the three collectible-star IDs are saved in localStorage to remember discoveries on that browser; no proposal response is recorded.

To reset the stars: open DevTools → Application → Local Storage → delete `laasya-stars-v1`, or clear this site's storage. LocalStorage being unavailable does not break the site.

## Production build

```sh
npm run build
npm run preview
```

Serve `dist/` using any static host. `npm run preview` is for local verification, not a production server. Don't open `index.html` or `dist/index.html` directly as a file; ES modules need a web server. Vite uses a relative asset base for the built app. If deploying under a subdirectory, update absolute public-asset paths in `src/main.jsx`, `src/style.css`, `index.html`, and your song URL accordingly.

## Skills & research

The repository includes **project-local agent skills** in `.agents/skills/`:
- `motion-design/`: the requested LottieFiles motion-design skill, including its director, pattern and reference guides.
- `motion/`: the official Motion AI skill and supporting guidance.

These are files usable by coding agents; nothing has been installed into your Notion workspace. Lenis is a library, not a skill repository; it is installed as an npm dependency, with its upstream reference in `docs/LENIS-REFERENCE.md`. GSAP ScrollTrigger is likewise installed as a dependency. The linked repositories were downloaded and reviewed; this does not claim every source/test file in each library was audited.

Read `docs/DESIGN-RESEARCH.md` for inspiration, palette, fonts, motion decisions, source URLs, and provenance. Read `docs/SECRETS.md` only if you want spoilers. `docs/QA.md` records the tested scope and known limits.

## Structure

```text
src/config.js          Personal text, dates, soundtrack
src/main.jsx           React experience and interaction logic
src/style.css          Responsive stationery design
scripts/dev.mjs        One-command install/start bootstrap
public/images/         Original still-life and subtle paper texture
public/music/          Add your chosen track here
.agents/skills/         Installed project-local motion skills
research/              Selected desktop/mobile previews
```

Original generated artwork is included locally. Fonts and open-source dependencies retain their own licenses. Review `THIRD_PARTY_NOTICES.md` before redistributing.
