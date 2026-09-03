# Manasa J — Product Manager Portfolio

A static portfolio site (HTML / CSS / vanilla JS, no build step) for product management job search.

## Structure

```
.
├── index.html                              # Homepage: hero, about, contact
├── experience.html                         # Roles, skills, certifications, education
├── case-studies/
│   └── starbucks-mood-drinks.html          # "Sip Your Vibe" — Starbucks mood-based drink recommendations
├── assets/
│   ├── css/style.css                       # Shared design system (dark forest + amber, Playfair + Inter)
│   ├── js/main.js                          # Mobile nav, scroll reveal, scroll-spy, mood tabs
│   └── files/Manasa_J_Resume.docx          # Downloadable resume
├── .nojekyll                               # Tells GitHub Pages to serve files as-is
└── README.md
```

## Run locally

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploy to GitHub Pages

Full step-by-step instructions — account, push, authentication, Pages setup and
custom domains — are in **[DEPLOY.md](DEPLOY.md)**.

Short version, once the remote is set up:

```bash
git add .
git commit -m "Describe what changed"
git push
```

Every push updates the live site within about a minute.


## Before you publish — fill these in

- [ ] Replace `YOUR-LINKEDIN` with the real LinkedIn handle (appears in `index.html` and `case-studies/starbucks-mood-drinks.html`)
- [ ] Optionally export the resume to PDF and swap `Manasa_J_Resume.docx` for `Manasa_J_Resume.pdf` — PDFs open in the browser, DOCX files download
- [ ] Add a headshot if you want one in the hero or About section
- [ ] Replace the "Next case study" placeholder card once a second case study is ready

## Adding a case study

1. Copy `case-studies/starbucks-mood-drinks.html` as a starting point.
2. Add a matching `.work-card` link in the `#work` section of `index.html`.
