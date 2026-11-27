# Audit Report: Plateful Responsive Food Ordering Page

**Live site:** https://whimsical-duckanoo-713432.netlify.app/
**Tech:** HTML5, CSS Flexbox, CSS Grid, media queries, container queries (no frameworks)
**Tools:** Google Lighthouse (Chrome DevTools), WAVE (WebAIM)

---

## 1. WAVE Accessibility Audit (https://wave.webaim.org)

| Metric | Result |
|---|---|
| Errors | **0** |
| Contrast Errors | **0** |
| Alerts | 1 (fixed, see below) |
| Features | 1 (page language declared: `en`) |
| Structural elements | 20 |
| ARIA elements | 24 |
| AIM score | **10 / 10** |

### Alert found and resolved
| Alert | Cause | Fix |
|---|---|---|
| Broken same-page link | Nav link "Offers" pointed to `#offers`, but no element had `id="offers"` | Added a `<section id="offers">` banner so the link has a target |

---

## 2. Lighthouse Audit (Chrome DevTools)

| Category | Mobile | Desktop |
|---|---|---|
| Performance | ___ | ___ |
| **Accessibility** | ___ | **100** |
| Best Practices | ___ | ___ |
| SEO | ___ | ___ |

Reports are saved in the `audit/` folder.

---

## 3. Accessibility features implemented
- Semantic landmarks: `header`, `nav`, `main`, `footer`; one `h1`, ordered `h2`/`h3` headings
- `lang="en"` on `<html>`
- Labelled search field (`aria-label`), `role="search"`
- Menu button with `aria-expanded` / `aria-controls`; category chips with `aria-pressed`
- Current page link marked with `aria-current="page"`
- Decorative emoji hidden with `aria-hidden="true"`
- Visible `:focus-visible` outline on all interactive elements
- Text contrast of at least 4.5:1 (WAVE: 0 contrast errors)
- `prefers-reduced-motion` respected
- Viewport meta tag; no horizontal scrolling at 375px

## 4. SEO / best-practice items
- `<title>` and meta description present
- Responsive viewport meta tag
- Inline favicon (avoids 404 in console)
- HTTPS via Netlify

---

## 5. Cross-device testing

| Device | Width | Header / nav | Restaurant grid | Result |
|---|---|---|---|---|
| Mobile (iPhone SE) | 375px | Logo + buttons, nav behind Menu button | 1 column, stacked cards | Pass |
| Large phone / small tablet | 640px | Same as mobile; search bar inline | 2 columns | Pass |
| Tablet (iPad Mini) | 768px | Inline nav, Menu button hidden | 2 to 3 columns, cards re-layout by container width | Pass |
| Desktop | 1280px | Logo, centred nav, buttons right | 3 columns, featured card spans 2 | Pass |
| Wide desktop | 1440px | Wider max-width container | 4 columns | Pass |

Screenshots are saved in the `screenshots/` folder.

---

## 6. Issues found and fixed during testing
| # | Issue | Tool | Fix |
|---|---|---|---|
| 1 | Broken same-page link (`#offers`) | WAVE | Added offers section with matching id |
| 2 | Sign in / Cart buttons displayed beside logo instead of at the right on desktop | Visual test | Added `order: 2` to `.actions` in the 768px media query |

## 7. Conclusion
The page meets the brief: Flexbox header and navigation, a Grid-based listing of 8 restaurant cards with hover effects, and mobile-first styling using media queries and container queries. Accessibility is strong (Lighthouse 100, WAVE 0 errors, AIM 10/10) and the layout was tested across mobile, tablet and desktop widths.