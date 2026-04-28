# Aisle - Bridal Beauty Analysis Landing Page

Handoff document for the current static site.

## What This Is

A direct-response landing page for a $97 digital product: a personalized AI bridal beauty analysis / Wedding Day Preview. The customer pays through Square, then receives instructions to submit photos and wedding details. The final deliverable is a personalized PDF beauty brief covering face features, color, skin prep, makeup, hair, and styling.

## Files

- `index.html` - landing page, single static file
- `checkout.html` - Square payment handoff page for Wedding Day Preview ($97)
- `HANDOFF.md` - this handoff doc

No external sample images are required on the live page. The hero and deliverable previews are original HTML/CSS mockups, so there are no image licensing dependencies.

## Current Checkout

`checkout.html` links to Square Payment Links:

- Product: Wedding Day Preview
- Price: $97.00
- URL: `https://square.link/u/p4RSAP6I?src=embed`

The checkout page opens the Square payment link in a centered popup when possible, with a normal link fallback if the popup is blocked.

## Still Needed Before Paid Traffic

1. Confirm fulfillment flow after Square purchase: intake email, upload form, and delivery workflow.
2. Replace placeholder testimonials and social proof with real numbers or remove them.
3. Add legal pages: privacy policy, terms, refund policy.
4. Add favicon, Apple touch icon, and an original OG image.
5. Install tracking: Meta Pixel / GA4 and test checkout events.
6. Confirm refund / redo policy language matches what you can operationally support.

## Editing Notes

- Static HTML/CSS/JS only; no build step.
- Main brand tokens live in the `:root` blocks of `index.html` and `checkout.html`.
- Landing CTA links point to `checkout.html`.
- Keep future visuals original, licensed, or client-approved.
