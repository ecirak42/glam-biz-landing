# Aisle — Bridal Beauty Analysis Landing Page

Handoff document for the developer taking this to production.

---

## 1. What this is

A direct-response landing page for a $97 digital product: a personalized AI bridal beauty analysis. Customer uploads photos, receives a multi-page mood-board PDF (face features, color analysis, skin analysis, hairstyle board, capsule styling) within 24 hours.

**Goal of v1:** ad-ready landing page for Meta/Instagram traffic that validates demand and pushes toward a purchase CTA. Payment + product fulfillment are not yet wired up — the checkout is a mock that captures intent.

**Brand placeholder:** "Aisle." Easy global find/replace if you change it.

---

## 2. What's built

### Files
- `index.html` — full landing page, single file (HTML + embedded CSS + minimal JS)
- `checkout.html` — mock checkout form + success state
- `samples/` — sample mood-board JPGs added from the provided inspiration references

### Stack
- Pure static HTML/CSS/JS. No build step, no framework, no dependencies beyond Google Fonts (Cormorant Garamond + Inter).
- Drop onto Netlify, Vercel, Cloudflare Pages, or any static host.

### Sections on `index.html` (top to bottom)
1. **Announcement bar** — limited spots / $97 / 24h delivery
2. **Sticky nav** — logo + persistent CTA
3. **Hero** — headline, subhead, primary CTA, social-proof bar (4.9/5, 1,200+ brides), styled bridal-photo placeholder with two floating analysis cards
4. **Problem agitation** — Pinterest paradox, expensive trials, MUA briefs, photo regret (2x2 grid)
5. **How it works** — 3 steps (upload, analyze, receive)
6. **What you get** — 7 cards mirroring the deliverable structure (face features, color analysis, skin analysis, hairstyle board, makeup analysis, capsule styling, + "you in every look" feature card)
7. **Sample gallery** — 6-frame asymmetric grid using the provided sample mood-board references
8. **Testimonials** — 3 placeholder testimonials with initials avatars
9. **Cost comparison** — reframes $97 against color analyst ($300–$600), trials ($300–$500), beauty consultant ($500+)
10. **Founder note** — short story for trust
11. **Loved-it guarantee** — redo + 14-day refund
12. **FAQ** — 7 questions (accuracy, photos to upload, delivery time, sharing with MUA, privacy, refund)
13. **Final CTA** — dark section with high-contrast button
14. **Footer** — minimal

### Design system
Defined as CSS variables in `:root` at the top of `index.html`:
- Background: `#FBF7F3` (warm ivory)
- Surface: `#FFFFFF`
- Ink: `#2A2521` (warm near-black)
- Blush: `#D9A7A0` / Blush deep: `#B8807A`
- Gold: `#9C7E4F` / Gold soft: `#C4A878`
- Display font: Cormorant Garamond (italic for accents)
- Body font: Inter

### Mobile responsiveness
Two breakpoints: 880px and 480px. Tested layout for hero, boards grid, sample gallery, and testimonials.

### CTA tracking (commented, ready to enable)
In both files, look for:
```js
// window.fbq && fbq('track', 'InitiateCheckout', { value: 97, currency: 'USD' });
// window.gtag && gtag('event', 'begin_checkout', { value: 97, currency: 'USD' });
```
Uncomment once Meta Pixel + GA4 are installed.

---

## 3. Next steps (in priority order)

### Critical for launch
1. **Add real assets**
   - Hero bridal photo or finished board preview — currently uses `samples/07-complete-beauty-guide.jpg`
   - Sample mood-board JPGs are in `samples/` (see §5 for filenames)
   - Real testimonial photos + names + locations (or keep initials)
   - Favicon (`favicon.ico` + `apple-touch-icon.png`)
   - OG image for social shares (1200x630, referenced in `<meta property="og:image">` — currently missing)
2. **Confirm brand name** — "Aisle" is a placeholder. Lock the name, then global find/replace.
3. **Domain + hosting**
   - Register the domain
   - Deploy to Netlify/Vercel/Cloudflare Pages (drag-and-drop works)
   - Configure SSL (auto on those hosts)
4. **Install tracking**
   - Meta Pixel (the `fbq` calls are pre-wired, just drop in the Pixel ID and uncomment)
   - GA4 or Plausible
   - Test that `InitiateCheckout` fires on every CTA and `Purchase` fires on submit
5. **Payment integration**
   - Replace mock submit handler in `checkout.html` (look for the `TODO: replace with real Stripe / payment processor integration` marker)
   - Recommend **Stripe Checkout** for fastest path — single redirect, handles cards/Apple Pay/Google Pay, PCI-compliant
   - Alternative: Stripe Payment Element for inline form (keeps the existing checkout UI)
   - Ensure success URL routes to the existing success-state pattern (or a dedicated `/thank-you` page)
6. **Post-purchase email automation**
   - Send "upload your photos" email immediately after purchase (Klaviyo, ConvertKit, Resend, or Stripe's built-in receipts)
   - Photo upload form (separate page, possibly behind a tokenized link)
   - Internal notification when a new order arrives
7. **Legal pages**
   - Privacy policy (required for Meta ads)
   - Terms of service
   - Refund policy detail page
   - Currently linked from footer as `#` placeholders
8. **Fulfillment workflow** — decide and document
   - Fully AI-generated, human-reviewed, or hybrid?
   - What tools/templates produce the actual mood-board PDFs?
   - SLA: 24h is promised on the page — is that realistic for v1 volume?
   - Who handles refund/redo requests?

### Strongly recommended before scaling spend
9. **Demand-validation ethics**
   The current checkout shows a fake success without charging. This is fine for early demand-signal tests, but **before running paid ads at scale**, decide one of:
   - **(a)** Wire up real Stripe and start fulfilling orders
   - **(b)** Switch the success screen to a waitlist / "we're at capacity this week" pattern that captures email without taking money. Ethically safer if fulfillment isn't ready.
10. **Ad creative + UGC**
    - Meta ad copy + creative variants
    - UGC from real brides (post-launch)
    - Landing page should match ad creative — keep the brand consistent
11. **Email/SMS list capture**
    - Exit-intent popup or scroll-triggered email capture
    - Abandoned-checkout sequence
12. **Sticky mobile CTA bar**
    - On mobile, a thin fixed-bottom bar with "Get my analysis — $97" can lift conversion 10–20% on long pages

### Nice to have
13. Second pricing tier ($147 with live consultant review) for upsell
14. Wedding date countdown / urgency element
15. Press logos ("As seen in") row under hero — only if real
16. Real logo design (currently the brand uses Cormorant Garamond serif text)
17. PDF sample download — let prospects download a redacted sample analysis to lower purchase friction
18. Performance polish — convert Google Fonts to self-hosted with `font-display: swap` for faster LCP

---

## 4. Important context / decisions made

- **No backend yet.** Everything is static HTML. Form submissions are mocked client-side.
- **CTA destination.** Every CTA on `index.html` points to either `#buy` (anchor) or `checkout.html`. The final-CTA section uses `id="buy"` so anchor links land there.
- **Guarantee positioning.** "Loved-it guarantee" = redo first, then full refund within 14 days. Reduces purchase anxiety without inviting abuse.
- **Social proof numbers (4.9/5, 1,200+ brides) are placeholder.** Replace with real numbers once you have them. Until then, consider testing copy that doesn't lean on these stats — Meta will flag inflated claims.
- **Testimonial names + photos are placeholder.** Get real customer testimonials before scaling ads — both for ethics and ad-account safety.
- **Sample gallery has graceful fallback.** If the real sample images are missing, each frame shows a styled label instead of a broken image. Won't look broken if assets are delayed.
- **Aesthetic direction comes from real reference boards** (Hairstyle Analysis Board, Color Analysis Warm Autumn, Face Features Analysis, Skin Analysis, Color Comparison, Makeup Analysis). Match this style for any new visuals.
- **Single-file by design.** Easier to deploy, easier to iterate, faster page load. Don't break it apart unless you're moving to a framework.

---

## 5. Asset checklist

Current asset paths referenced by the page:

```
/                           (project root)
├── index.html              (built)
├── checkout.html           (built)
├── HANDOFF.md              (this file)
├── favicon.ico             ← TODO
├── apple-touch-icon.png    ← TODO (180x180)
├── og-image.jpg            ← TODO (1200x630)
└── samples/
    ├── 01-hairstyle-board.jpg
    ├── 02-color-analysis.jpg
    ├── 03-face-features.jpg
    ├── 04-skin-analysis.jpg
    ├── 05-color-comparison.jpg
    ├── 06-makeup-analysis.jpg
    └── 07-complete-beauty-guide.jpg
```

Hero visual: currently uses `samples/07-complete-beauty-guide.jpg` as a polished report preview. Replace with a finished branded hero board or bridal photo once the final product sample is locked.

---

## 6. Where to find things in the code

- **All copy** — directly in `index.html`, no CMS. Search by section heading to find any block.
- **Color tokens** — `:root` block at the top of `index.html` and `checkout.html`. Change once, applies everywhere.
- **CTA button text** — search for "Get my bridal analysis"
- **Pricing** — search for "$97" (appears in: announcement bar, hero meta, comparison table, final CTA, checkout summary, button text)
- **Tracking hooks** — search for `fbq` or `gtag`
- **Mock submit logic** — bottom of `checkout.html`, inside the `<script>` block

---

## 7. Quick reference: DOs and DON'Ts for whoever takes this over

**Do**
- Keep the warm-ivory + blush + gold palette. It signals "premium bridal" and matches reference boards.
- Test on mobile first. ~80%+ of Meta traffic is mobile.
- Wire up Meta Pixel + GA4 before the first ad runs.
- Lead with the sample gallery in conversion tests — it's the strongest selling element once real images are in.
- Keep copy in active voice and second-person ("you," "your"). Direct response.

**Don't**
- Add a heavy framework (React, Next.js) unless you're building real product features. Static HTML is faster and easier to iterate for a landing page.
- Replace serif headlines with sans-serif. The display serif is doing brand work.
- Take real money through `checkout.html` until Stripe (or equivalent) is properly wired and fulfillment is ready.
- Inflate the social proof numbers further. Meta enforces this.
