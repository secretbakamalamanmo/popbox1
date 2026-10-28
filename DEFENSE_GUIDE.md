# Pop Box Cafe: defense notes

These notes describe the current prototype. Use them to explain the actual implementation in your own words.

## Main flow

- The customer page displays and filters the menu, manages a cart, and creates an order.
- The order is saved as JSON in browser `localStorage` using `popbox_orders_v1`.
- The staff page reads that same order list and updates order status. Product availability is stored under `popbox_menu_v1`.
- Both pages must run in the same browser profile and under the same origin for this prototype to share data.

## Menu Guide

The Menu Guide is a deterministic client-side matcher. It compares preference words with each available item's name, category, and description; applies weights for food or drink intent and preference groups; and uses a budget ceiling when one is provided. It shows up to three highest-ranked items. It does not call an external AI model.

Voice input uses the browser's Web Speech API when supported. The image option only previews the selected photo; image recognition is not implemented.

## Product photos

The supplied menu photos are stored in `customer/assets/menu/`. The customer page maps 43 matched food and drink photos to menu IDs in `MENU_PHOTO_OVERRIDES`. The remaining included image is a general Espresso Based reference. Other menu entries use remote reference photos and a Wikimedia fallback. Product photos are visual references, so actual cafe portions and plating may differ.

## Design choices

The pages use a warm coffee-and-caramel palette, consistent buttons and panels, responsive card grids, and visible keyboard focus states. Local photos are preferred where available so key products do not depend on a remote image host.

## Limits and next steps

This is a front-end demonstration, not a production ordering system. `localStorage` only works across pages in one browser profile and origin. A deployed version would need a shared backend, authentication, server-side validation, payment handling, and a managed photo source.

## Questions to be ready for

**Why use localStorage?** It is a simple way to demonstrate customer-to-staff order flow in a single-browser prototype. It is not suitable for cross-device deployment.

**How are suggestions selected?** A weighted rule set scores menu text, food or drink intent, preference terms, and budget, then returns the top matches.

**What happens if a photo is missing?** The page tries its configured reference-photo fallback. The 43 matched photos are local in `customer/assets/menu/`; other fallback URLs need internet access.