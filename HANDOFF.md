# Aisle ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â Bridal Beauty Analysis Landing Page

Handoff document for the developer taking this to production.

---

## 1. What this is

A direct-response landing page for a $97 digital product: a personalized AI bridal beauty analysis. Customer uploads photos, receives a multi-page mood-board PDF (face features, color analysis, skin analysis, hairstyle board, capsule styling) within 24 hours.

**Goal of v1:** ad-ready landing page for Meta/Instagram traffic that validates demand and pushes toward a purchase CTA. Payment + product fulfillment are not yet wired up ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â the checkout is a mock that captures intent.

**Brand placeholder:** "Aisle." Easy global find/replace if you change it.

---

## 2. What's built

### Files
- `index.html` ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â full landing page, single file (HTML + embedded CSS + minimal JS)
- `checkout.html` ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â mock checkout form + success state
- No external sample images are required; live previews are original HTML/CSS mockups.

### Stack
- Pure static HTML/CSS/JS. No build step, no framework, no dependencies beyond Google Fonts (Cormorant Garamond + Inter).
- Drop onto Netlify, Vercel, Cloudflare Pages, or any static host.

### Sections on `index.html` (top to bottom)
1. **Announcement bar** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â limited spots / $97 / 24h delivery
2. **Sticky nav** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â logo + persistent CTA
3. **Hero** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â headline, subhead, primary CTA, social-proof bar (4.9/5, 1,200+ brides), styled bridal-photo placeholder with two floating analysis cards
4. **Problem agitation** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â Pinterest paradox, expensive trials, MUA briefs, photo regret (2x2 grid)
5. **How it works** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â 3 steps (upload, analyze, receive)
6. **What you get** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â 7 cards mirroring the deliverable structure (face features, color analysis, skin analysis, hairstyle board, makeup analysis, capsule styling, + "you in every look" feature card)
7. **Deliverable preview** - clarity cards plus 6 original HTML/CSS mock boards explaining what arrives in the PDF
8. **Testimonials** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â 3 placeholder testimonials with initials avatars
9. **Cost comparison** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â reframes $97 against color analyst ($300ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Å“$600), trials ($300ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Å“$500), beauty consultant ($500+)
10. **Founder note** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â short story for trust
11. **Loved-it guarantee** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â redo + 14-day refund
12. **FAQ** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â 7 questions (accuracy, photos to upload, delivery time, sharing with MUA, privacy, refund)
13. **Final CTA** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â dark section with high-contrast button
14. **Footer** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â minimal

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
   - Optional original hero photo or finished branded report preview
   - Optional original/licensed sample board images if you decide to replace the CSS mockups
   - Real testimonial photos + names + locations (or keep initials)
   - Favicon (`favicon.ico` + `apple-touch-icon.png`)
   - OG image for social shares (1200x630, referenced in `<meta property="og:image">` ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â currently missing)
2. **Confirm brand name** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â "Aisle" is a placeholder. Lock the name, then global find/replace.
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
   - Recommend **Stripe Checkout** for fastest path ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â single redirect, handles cards/Apple Pay/Google Pay, PCI-compliant
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
8. **Fulfillment workflow** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â decide and document
   - Fully AI-generated, human-reviewed, or hybrid?
   - What tools/templates produce the actual mood-board PDFs?
   - SLA: 24h is promised on the page ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â is that realistic for v1 volume?
   - Who handles refund/redo requests?

### Strongly recommended before scaling spend
9. **Demand-validation ethics**
   The current checkout shows a fake success without charging. This is fine for early demand-signal tests, but **before running paid ads at scale**, decide one of:
   - **(a)** Wire up real Stripe and start fulfilling orders
   - **(b)** Switch the success screen to a waitlist / "we're at capacity this week" pattern that captures email without taking money. Ethically safer if fulfillment isn't ready.
10. **Ad creative + UGC**
    - Meta ad copy + creative variants
    - UGC from real brides (post-launch)
    - Landing page should match ad creative ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â keep the brand consistent
11. **Email/SMS list capture**
    - Exit-intent popup or scroll-triggered email capture
    - Abandoned-checkout sequence
12. **Sticky mobile CTA bar**
    - On mobile, a thin fixed-bottom bar with "Get my analysis ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â $97" can lift conversion 10ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Å“20% on long pages

### Nice to have
13. Second pricing tier ($147 with live consultant review) for upsell
14. Wedding date countdown / urgency element
15. Press logos ("As seen in") row under hero ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â only if real
16. Real logo design (currently the brand uses Cormorant Garamond serif text)
17. PDF sample download ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â let prospects download a redacted sample analysis to lower purchase friction
18. Performance polish ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â convert Google Fonts to self-hosted with `font-display: swap` for faster LCP

---

## 4. Important context / decisions made

- **No backend yet.** Everything is static HTML. Form submissions are mocked client-side.
- **CTA destination.** Every CTA on `index.html` points to either `#buy` (anchor) or `checkout.html`. The final-CTA section uses `id="buy"` so anchor links land there.
- **Guarantee positioning.** "Loved-it guarantee" = redo first, then full refund within 14 days. Reduces purchase anxiety without inviting abuse.
- **Social proof numbers (4.9/5, 1,200+ brides) are placeholder.** Replace with real numbers once you have them. Until then, consider testing copy that doesn't lean on these stats ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â Meta will flag inflated claims.
- **Testimonial names + photos are placeholder.** Get real customer testimonials before scaling ads ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â both for ethics and ad-account safety.
- **Live previews are original.** The user-provided inspiration boards were removed from the published site to avoid using other people's generated work.
- **Aesthetic direction** should stay editorial, organized, premium, and beauty-report focused, but any future visual assets should be original, licensed, or client-approved.
- **Single-file by design.** Easier to deploy, easier to iterate, faster page load. Don't break it apart unless you're moving to a framework.

---

## 5. Asset checklist

Current asset paths expected by the page:

`	ext
/                           (project root)
Ã¢â€Å“Ã¢â€â‚¬Ã¢â€â‚¬ index.html              (built)
Ã¢â€Å“Ã¢â€â‚¬Ã¢â€â‚¬ checkout.html           (built)
Ã¢â€Å“Ã¢â€â‚¬Ã¢â€â‚¬ HANDOFF.md              (this file)
Ã¢â€Å“Ã¢â€â‚¬Ã¢â€â‚¬ favicon.ico             TODO
Ã¢â€Å“Ã¢â€â‚¬Ã¢â€â‚¬ apple-touch-icon.png    TODO (180x180)
Ã¢â€â€Ã¢â€â‚¬Ã¢â€â‚¬ og-image.jpg            TODO (1200x630)
` 

Hero visual and deliverable previews are CSS/HTML mockups, so there are no image licensing dependencies on the live page.

---

## 6. Where to find things in the code

- **All copy** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â directly in `index.html`, no CMS. Search by section heading to find any block.
- **Color tokens** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â `:root` block at the top of `index.html` and `checkout.html`. Change once, applies everywhere.
- **CTA button text** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â search for "Get my bridal analysis"
- **Pricing** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â search for "$97" (appears in: announcement bar, hero meta, comparison table, final CTA, checkout summary, button text)
- **Tracking hooks** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â search for `fbq` or `gtag`
- **Mock submit logic** ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â bottom of `checkout.html`, inside the `<script>` block

---

## 7. Quick reference: DOs and DON'Ts for whoever takes this over

**Do**
- Keep the warm-ivory + blush + gold palette. It signals "premium bridal" and matches reference boards.
- Test on mobile first. ~80%+ of Meta traffic is mobile.
- Wire up Meta Pixel + GA4 before the first ad runs.
- Lead with the sample gallery in conversion tests ÃƒÂ¢Ã¢â€šÂ¬Ã¢â‚¬Â it's the strongest selling element once real images are in.
- Keep copy in active voice and second-person ("you," "your"). Direct response.

**Don't**
- Add a heavy framework (React, Next.js) unless you're building real product features. Static HTML is faster and easier to iterate for a landing page.
- Replace serif headlines with sans-serif. The display serif is doing brand work.
- Take real money through `checkout.html` until Stripe (or equivalent) is properly wired and fulfillment is ready.
- Inflate the social proof numbers further. Meta enforces this.
