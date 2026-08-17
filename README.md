# DriveText — Auto Dealers SMS Landing Page (US)

Single-file, dependency-free landing page for a TCPA / A2P 10DLC compliant SMS outreach
service aimed at US auto dealerships.

## What's here

| File | Purpose |
| --- | --- |
| `index.html` | The entire page — HTML, CSS and JS inlined. No build step, no CDN calls. |

Open `index.html` in a browser and it works. Nothing to install.

## Sections

1. **Hero** — headline, sub, primary CTA, compliance badges, animated SMS thread mock, stat strip
2. **Pain points** — 4 cards (cold leads, ad cost, compliance risk, stretched sales team)
3. **How it works** — 4 process steps (contact base → compliant outreach → response filtering → sales handoff)
4. **Pricing** — table plus a live campaign-cost estimator
5. **Why us** — 4 differentiators
6. **FAQ** — 5 accordion items
7. **Final CTA** — lead form with success state
8. **Footer** — compliance disclosure

## Pricing (single source of truth)

| Service | Price |
| --- | --- |
| SMS outreach | **$0.30** / SMS |
| Targeted phone number (city / state / profession) | **$0.15** / number |
| First trial | **100 free SMS** |

The estimator constants live at the top of the `<script>` block in `index.html`:

```js
var SMS_RATE = 0.30, NUM_RATE = 0.15, FREE_SMS = 100;
```

Change those and the table markup together if rates ever move.

## Before going live

- [ ] **Wire the lead form.** `#leadForm` currently just shows a success state client-side.
      Replace the handler with a `fetch()` POST to your CRM, Formspree, HubSpot or similar
      (marked with a comment in the script).
- [ ] **Replace the brand.** "DriveText" is a placeholder — swap the name, logo mark
      (inline SVG in the nav, footer and favicon) and the accent color `--accent: #FF4A1C`.
- [ ] **Add real OG image.** `og:image` is not set; add one for link previews.
- [ ] **Legal review.** The FAQ and footer describe a consent-confirmation process. Have
      counsel confirm the copy matches how you actually source and document consent —
      cold texting purchased lists without a valid consent basis is a TCPA exposure
      regardless of A2P 10DLC registration.
- [ ] **Privacy policy / terms** links in the footer if you run paid traffic to this page.

## Deploy

Any static host. It's one file.

```bash
npx serve .
```

GitHub Pages: push to `main`, then Settings → Pages → Source: `main` / root.

## Browser support

Modern evergreen browsers. Uses `IntersectionObserver` (graceful fallback: everything is
just visible), CSS grid, `backdrop-filter`, and `grid-template-rows` accordion animation.
Respects `prefers-reduced-motion`.
