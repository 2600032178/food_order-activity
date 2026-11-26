# Plateful – Responsive Food Ordering Page

Mobile-first restaurant discovery page built with CSS Flexbox, CSS Grid, media queries and container queries.

## Structure
```
index.html          markup
css/style.css       all styles (Flexbox header/nav, Grid listing, media + container queries)
screenshots/        cross-device evidence (mobile / tablet / desktop)
audit/              Lighthouse + WAVE reports
```

## Run in VS Code
1. Install the **Live Server** extension (Ritwick Dey).
2. File > Open Folder > select this folder.
3. Right-click `index.html` > **Open with Live Server** (http://127.0.0.1:5500).
   (No extension? Run `npx serve .` or `python -m http.server 8000` in the VS Code terminal.)

## Cross-device testing
Chrome DevTools (F12) > Toggle device toolbar (Ctrl+Shift+M). Save screenshots into `screenshots/`:
| Device | Width | File |
|---|---|---|
| Mobile (iPhone SE / 375) | 375px | mobile-375.png |
| Mobile menu open | 375px | mobile-menu-open.png |
| Tablet (iPad Mini / 768) | 768px | tablet-768.png |
| Desktop | 1280px | desktop-1280.png |
| Wide desktop | 1440px | wide-1440.png |
| Card hover state | 1280px | hover-card.png |

Expected behaviour: nav collapses behind Menu below 768px; grid is 1 col (phone), 2 cols (tablet), 3 cols with a double-width featured card (desktop), 4 cols (>=1440px); cards switch to a horizontal layout when their own container is >= 26rem.

## Lighthouse audit
1. Open the page in Chrome (Incognito, so extensions don't skew scores) via Live Server.
2. DevTools > **Lighthouse** tab > tick Performance, Accessibility, Best Practices, SEO.
3. Run once for **Mobile** and once for **Desktop**.
4. Save report: Lighthouse menu (three dots) > **Save as HTML** > `audit/lighthouse-mobile.html`, `audit/lighthouse-desktop.html`.
5. Or via CLI: `npx lighthouse http://127.0.0.1:5500 --view --output html --output-path audit/lighthouse-mobile.html`
Target: 90+ in every category.

## WAVE accessibility audit
1. Install the **WAVE Evaluation Tool** Chrome/Edge extension (WebAIM).
2. Open the page > click the WAVE icon > review Errors, Contrast Errors, Alerts, Structural Elements.
3. Screenshot the summary panel to `audit/wave-summary.png` (repeat at 375px width for mobile).
Target: 0 Errors, 0 Contrast Errors.
Already addressed in the code: landmarks (header/nav/main/footer), single h1 with ordered headings, labelled search field, `aria-expanded` on the menu button, `aria-pressed` on category chips, decorative emoji hidden with `aria-hidden`, visible focus outline, `prefers-reduced-motion`, text contrast >= 4.5:1.

## Audit results (fill in after running)
| Tool | Mode | Perf | A11y | Best Practices | SEO / WAVE errors |
|---|---|---|---|---|---|
| Lighthouse | Mobile | | | | |
| Lighthouse | Desktop | | | | |
| WAVE | Desktop | | | | Errors: / Contrast: / Alerts: |

## Git / Pull Request
```bash
git init   # skip if cloning an existing repo
git checkout -b feature/responsive-food-ordering
git add .
git commit -m "Add responsive food ordering page with Grid, Flexbox and container queries"
git remote add origin <your-repo-url>   # skip if cloned
git push -u origin feature/responsive-food-ordering
```
Open GitHub > **Compare & pull request**. Suggested description: summary, breakpoints (640 / 768 / 1024 / 1440), container query note, screenshots, Lighthouse + WAVE scores.
