# Tejasvi Kumar — Portfolio

Personal portfolio site. Plain HTML, CSS and JavaScript — no frameworks, no build step, no dependencies (only Google Fonts).

## Run it

Open `index.html` in a browser, or serve the folder (recommended, so everything behaves like it will in production):

```bash
cd portfolio
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploy

It's a static folder, so any static host works:

- **GitHub Pages:** push this folder to a repo → Settings → Pages → deploy from the `main` branch root.
- **Netlify / Vercel:** drag-and-drop the folder, or import the repo with no build command.

After deploying, set your real URL in the `og:url` meta tag in `index.html`.

## Things to fill in

| What | Where |
|---|---|
| Project links (Repairo Moto, Library Sathi, Glow Lakshmi, Aurex Beverages, Chrome AI Extension) | `index.html` → the `href` on each project card's button |
| Add a new project | Copy an existing `<article class="project">` card in `index.html`, edit the text and link, and keep the `project--reverse` class on every other card |
| Resume | Put the PDF in `assets/resume/`, then set `RESUME_URL` in `js/script.js` (currently `"assets/resume/Tejasvi_Kumar_Resume_B.pdf"`) |
| Project screenshots | Put images in `assets/images/`, then add them to the project card's `data-shots` attribute, comma separated. The first one becomes the main image; two or more get thumbnails. Cards without `data-shots` show a placeholder mockup. |
| Contact form recipient | `js/script.js` → `EMAIL_TO` |
| Availability badge | `index.html` → the `<p class="status">` in the hero. Edit the text or delete the line. |
| Photos | `assets/images/tejasvi-kumar.JPG` (hero and About). Keep the file name and extension case identical to the path in `index.html`, since many hosts are case-sensitive. |

A button with a `data-link` attribute and an empty value in `PROJECT_LINKS` shows a disabled state with a small "soon" tag, so the live site never has a broken link.

## Structure

```
portfolio/
├── index.html          all content
├── css/style.css       theme tokens at the top, then components, then breakpoints
├── js/script.js        editable links at the top, then behaviour
├── assets/
│   ├── images/         favicon.svg, og-image.png (social preview), photos, project screenshots
│   └── resume/         your resume PDF
└── README.md
```

## Notes

- **Theme:** dark by default; the choice is saved in `localStorage`. Colours are CSS variables (`--background`, `--text`, `--secondary-text`, `--border`, `--card-background`, `--accent`) defined once per theme at the top of `style.css`.
- **Contact form:** frontend-only. It validates, then opens the visitor's email app with the message pre-filled (`mailto:`). Nothing is sent to or stored on a server. To receive messages directly, swap the submit handler for a service like Formspree.
- **Motion:** all animations respect the system "reduce motion" setting, and the hero background pauses when it's off-screen.
- **Content:** every company, project and figure comes from Tejasvi's own details. Nothing is invented; missing items are left out rather than guessed.