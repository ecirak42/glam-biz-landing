# Aisle - Bridal Beauty Analysis Landing Page

Handoff document for the current static site.

## What This Is

A direct-response landing page for a $97 digital product: a personalized AI bridal beauty analysis / Wedding Day Preview. The customer pays through Square, then receives instructions to submit photos and wedding details. The final deliverable is a personalized PDF beauty brief covering face features, color, skin prep, makeup, hair, and styling.

## Files

- `index.html` - landing page, single static file
- `checkout.html` - Square payment handoff page for Wedding Day Preview ($97)
- `assets/hero-product-preview.svg` - original hero product preview graphic
- `assets/deliverable-pages-preview.svg` - original deliverable pages preview graphic
- `HANDOFF.md` - this handoff doc

No borrowed sample images are used on the live page. The product visuals are original SVG mockups inspired by beauty-analysis board layouts.

## Current Checkout

`checkout.html` embeds the Square Payment Link in an iframe:

- Product: Wedding Day Preview
- Price: $97.00
- URL: `https://square.link/u/p4RSAP6I?src=embed`

The checkout page keeps users on-site by embedding Square checkout. A fallback link appears under the iframe in case a browser blocks the embedded checkout.

## Still Needed Before Paid Traffic

1. Confirm fulfillment flow after Square purchase: intake email, upload form, and delivery workflow.
2. Add legal pages: privacy policy, terms, refund policy.
3. Add favicon, Apple touch icon, and an original OG image.
4. Install tracking: Meta Pixel / GA4 and test checkout events.
5. Confirm refund / redo policy language matches what you can operationally support.

## Editing Notes

- Static HTML/CSS/JS only; no build step.
- Main brand tokens live in the `:root` blocks of `index.html` and `checkout.html`.
- Landing CTA links point to `checkout.html`.
- Keep future visuals original, licensed, or client-approved.

