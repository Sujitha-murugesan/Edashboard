# Enterprise Dashboard: Semantic HTML5 and Accessible Components

A multi-page, framework-free dashboard foundation built to WCAG 2.1 AA practices and validated with the official W3C Nu HTML Checker (0 errors, 0 warnings).

## Pages
| File | Purpose |
|---|---|
| `index.html` | Overview: KPI `article` cards, activity data table, `aside` notice |
| `users.html` | User directory table, "Add user" modal with validated form, confirmation modal |
| `reports.html` | Report `article`s, data table with `tfoot`, `aside` |
| `settings.html` | Comprehensive form: fieldsets, radios, checkboxes, range, error summary |

## Structure
```
├── index.html users.html reports.html settings.html   (generated, committed)
├── css/styles.css
├── js/app.js                     menu toggle, dialogs, form validation
├── src/
│   ├── components/               head, header, sidebar, footer partials
│   └── pages/                    page sources with <!-- @include name --> markers
├── scripts/build.js              assembles partials into root pages
├── scripts/validate.js           runs W3C Nu checker locally
└── docs/                         validation + accessibility notes
```

## Semantic landmarks used
`header` (banner), `nav` (top, main, footer, each with a unique `aria-label`), `aside` (sidebar and notices), `main`, `section` (each labelled by its heading), `article` (self-contained cards), `footer`, plus `dialog`, `fieldset`/`legend`, `caption`, `th scope`, `time`, `output`.

## Accessibility features
- Skip link, one `h1` per page, no skipped heading levels, `lang="en"`.
- `aria-current="page"` on active nav links.
- Native `<dialog>` + `showModal()`: focus trapped, Esc closes, focus returns to the trigger, labelled with `aria-labelledby`.
- Every control has a visible `<label>`; hints and errors linked with `aria-describedby`; `aria-invalid` set on errors.
- Validation attributes: `required`, `minlength`, `maxlength`, `pattern`, `type=email/tel/date`, `min`/`max`, `autocomplete`.
- Error summary (`role="alert"`) with links to each invalid field.
- Scrollable table regions are keyboard focusable; icon-only text hidden with `.visually-hidden`.
- Visible focus ring, high-contrast colours, responsive layout, reduced-motion support.

## Run
```bash
npm install
npm run build       # regenerate pages from src/ (after editing components)
npm run serve       # http://localhost:8080
npm run validate    # W3C Nu checker (needs Java 11+)
```
Or just open `index.html` in a browser.

## Edit workflow
Change shared markup in `src/components/*.html` or page content in `src/pages/*.html`, then `npm run build`.

## Publish
```bash
git init && git add . && git commit -m "Semantic accessible dashboard"
git remote add origin <repo-url> && git push -u origin main
```
