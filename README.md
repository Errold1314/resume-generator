# resume-generator

# Resume Studio

An ATS-friendly, editorial resume builder. Fill in your details, pick from
12 typographically distinct templates across 6 professions, preview on a live
8.5×11 page, and export to **PDF** and **Word (.docx)**.

100% front-end. No backend, no API keys, no database, no tracking, no login.
Once built, it's a folder of static files you can host anywhere — or open
directly from disk.

---

## Quick start (run locally)

Requires [Node.js](https://nodejs.org) 18+.

```bash
npm install
npm run dev
```

Open the printed URL (usually http://localhost:5173).

## Build for production

```bash
npm run build
```

The finished site lands in `dist/`. Because asset paths are relative, the
`dist/` folder works two ways:

1. **Hosted** — upload `dist/` to any static host (Vercel, Netlify, GitHub
   Pages, Cloudflare Pages, an S3 bucket, etc.).
2. **Offline** — open `dist/index.html` directly in a browser. No server
   needed. (PDF/Word export libraries load from a CDN on first click, so the
   export buttons need an internet connection the first time.)

To preview the production build locally:

```bash
npm run preview
```

---

## Deploying to Vercel (recommended)

1. Push this folder to a GitHub repo.
2. Go to vercel.com → New Project → import the repo.
3. Framework preset: **Vite**. Build command `npm run build`, output dir
   `dist`. Click Deploy.

Or, from the command line:

```bash
npm install -g vercel
vercel
```

## Deploying to Netlify

Drag-and-drop the `dist/` folder onto app.netlify.com/drop, or connect the
repo with build command `npm run build` and publish directory `dist`.

---

## How it works

- `src/ResumeGenerator.jsx` — the entire app (one component file): the
  editable form, the 12 template renderers, the live preview, and the PDF +
  Word exporters.
- `src/main.jsx` — React entry point.
- `src/index.css` — Tailwind directives + print styles.

### Templates

Six categories, two variants each: Corporate, Tech, Creative, Health/Edu,
Academic, Trades/Service. Each is single-column, standard section names, no
text baked into images — i.e. ATS-safe. The Creative category has a Clay/Sage
color toggle.

### Export

- **PDF** via `html2pdf.js` (loaded from cdnjs at runtime). Letter size,
  selectable text.
- **Word** via the `docx` library (loaded from cdnjs at runtime). Real Word
  styles — shaded headings, tab-stop dates, bullet lists — so it stays
  editable in Microsoft Word.

Both libraries are pulled from a CDN the first time you click export, which
keeps the bundle small. If you need a fully offline build with no CDN calls,
install `html2pdf.js` and `docx` as npm dependencies and import them directly
instead of using the runtime loader in `ResumeGenerator.jsx`.

---

## Customizing

- **Colors / fonts per template** — edit the `TEMPLATES` map near the top of
  `ResumeGenerator.jsx`.
- **Add a template** — add an entry to `CATEGORIES` and a matching key in
  `TEMPLATES`.
- **Default sample data** — edit `SAMPLE_DATA`.
- **Background art** — the cream-mountain banner is the `ClimberBackground`
  component (inline SVG).

---

## License

See `LICENSE.txt`.
