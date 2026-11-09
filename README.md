# Ciftelia: ePortfolio of Klodiana Kamberi (LE/COOP 3100)

A static ePortfolio site: plain HTML, CSS and a little JavaScript. There's no build step, so
GitHub Pages can serve the folder exactly as it is.

## Pages

| File | Page |
|---|---|
| `index.html` | Home: intro, program, what I love about it, co-op experience, career goal |
| `about.html` | About: photo, short background, About Me video |
| `resume.html` | Resume: embedded PDF preview and download button |
| `projects.html` | Projects: Navi, TV-Fun, RescueDispatch (hackathon) |
| `contact.html` | Contact: email only |

```
ciftelia.github.io/
├── index.html  about.html  resume.html  projects.html  contact.html
├── css/styles.css        one theme: colour tokens, fonts, type scale, light + dark mode
├── js/main.js            theme toggle (remembered per browser) and mobile menu
└── assets/
    ├── img/              photo, project screenshots, video poster
    ├── video/            About Me video
    └── docs/             resume PDF (phone number removed)
```

## Before you publish

1. **Read the reflections.** The Home page texts and the three "What I learned" paragraphs are
   based on your COOP 2100 site. Make sure each one still sounds like you.
2. **About Me video:** this is `assets/video/about-me.mp4` (on the About page, with no preview
   image). To use YouTube instead, replace the `<video>` element with a
   `https://www.youtube-nocookie.com/embed/VIDEO_ID` iframe.
3. **Resume:** the LaTeX source is kept outside this repository (in
   `e-portfolio/resume/` on your computer) so it isn't published. Build it with `pdflatex Klodiana-Kamberi-Resume.tex`, keep it **without phone number
   or address**, and replace `assets/docs/Klodiana-Kamberi-Resume.pdf` (keep the same file name). Phones show
   page images instead of the embedded PDF, so re-render those too:
   ```bash
   pdftoppm -r 110 -jpeg assets/docs/Klodiana-Kamberi-Resume.pdf assets/img/resume-page
   ```
   (`pdftoppm` comes with Poppler: `brew install poppler`.)

## Preview locally

Open `index.html` in a browser, or run a tiny local server (this makes the PDF preview behave
the way it will on GitHub Pages):

```bash
python3 -m http.server 8000
```

Then visit <http://localhost:8000>.

## Deployment

The site is live at <https://ciftelia.github.io/>. Every push to `main` redeploys it through
`.github/workflows/static.yml` (Actions tab shows progress).

## Accessibility and design notes

- Semantic landmarks (`header`, `nav`, `main`, `footer`), a skip link, one `h1` per page,
  `aria-current` on the active menu item.
- Every image has alt text, and diagrams are inline SVG with a `<title>` and `<desc>`.
- Colours are tokens in `css/styles.css` for both themes, with text contrast at WCAG AA or
  better. Dark mode follows the system setting until the visitor uses the toggle.
- Layout works from 320 px phones to wide desktops; the menu collapses below 720 px.
- Fonts: Space Grotesk (headings), Inter (body), JetBrains Mono (code and labels), loaded
  from Google Fonts.

## Privacy

The site contains no home address, phone number, date of birth or age. Contact is by email
only. The TV-Fun repository is private, so the Projects page shows code excerpts and
diagrams instead of a repository link. No employer code or data is included.
