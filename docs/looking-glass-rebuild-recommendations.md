# Looking Glass Creamery — Front-End Rebuild Recommendations

**Companion to:** [`looking-glass-audit.md`](./looking-glass-audit.md)
**Architecture:** Headless — **Astro 5 front-end + Shopify Storefront API**, with **Shopify
hosted checkout retained**.
**Target codebase:** this repo (`astro-platform-starter`).

The goal of a headless rebuild is full design/performance control of the front-end **without
touching the Shopify backend that processes money, inventory, and orders**. The rule of
thumb: **read** catalog data and **build** cart state via the Storefront API, then **hand
off** to Shopify for checkout, payments, accounts, taxes, and shipping. Never re-implement
those.

---

## Safe-to-rebuild vs. backend-tied

<a id="safe-to-rebuild-vs-backend-tied"></a>

| Area | Safe to rebuild (pure front-end) | Tied to Shopify backend — read/hand-off only |
|---|---|---|
| **Marketing pages** | Home, Our Story/About, History, Meet our Cheese, Visit/Farm Store (hours, map, directions), Press, blog/recipes | — |
| **Catalog UI** | Product cards, product detail layout, image galleries, collection/listing pages, variant selector UI, filtering/sorting UI | Product/variant/price/inventory **data** → Storefront API (don't fork the catalog) |
| **Cart** | Cart drawer/page UI, line-item UI, quantity controls | Cart **state & mutations** → Storefront API Cart API (`cartCreate`, `cartLinesAdd/Update/Remove`) |
| **Checkout** | "Checkout" button styling | **Checkout itself** → redirect to Shopify `cart.checkoutUrl` (hosted). Do **not** rebuild payment. |
| **Accounts** | Account entry-point UI | Login/orders → Shopify (link out, or Customer Account API later) |
| **Commerce rules** | — | Discounts, taxes, shipping rates, gift cards, checkout apps → stay in Shopify admin |
| **SEO/markup** | Titles, meta, OG, JSON-LD, sitemap, canonical, robots | — |
| **Nav/footer/branding** | Everything | — |

**Hard rules**
- Don't store prices/inventory in the front-end; always reflect Storefront API responses.
- Always redirect to `checkoutUrl` from the live cart — never collect payment in Astro.
- Keep one canonical domain; map the headless site to it and 301 legacy domains
  (`lookingglasscheese.com`, the Square site).
- Inventory, fulfillment, and any **perishable-shipping** logic remain backend/ops scope.

---

## Current starter state (from codebase exploration)

- **Stack:** Astro `^5.5.3`, `@astrojs/react`, **Tailwind v4** (`@tailwindcss/vite`),
  `@astrojs/netlify` adapter. (`astro.config.mjs`, `package.json`)
- **Pages:** only Netlify platform demos (`src/pages/index.astro`, `revalidation.astro`,
  `image-cdn.astro`, `blobs/`, `edge/`) — **no commerce code exists yet** (clean slate).
- **Layout/SEO:** `src/layouts/Layout.astro` has only basic `<title>`/viewport meta —
  **no OG, no JSON-LD, no sitemap**.
- **Styling:** `src/styles/globals.css` with Tailwind `@theme` tokens (currently a coral
  `--color-primary: #f67280`) — re-theme to the creamery brand.
- **Assets available to exploit:** Astro `<Image>` + **Netlify Image CDN** (great for
  product/farm photography and Core Web Vitals).

---

## Build plan

### 1. Storefront API client
- Add env vars `SHOPIFY_STORE_DOMAIN` and `SHOPIFY_STOREFRONT_TOKEN` (Storefront API
  access token from a Shopify custom app). Document in `.env.example`; never commit secrets.
- Create `src/lib/shopify.ts` — a thin GraphQL client (`fetch` against
  `https://{domain}/api/2024-10/graphql.json`). Optionally use `@shopify/hydrogen-react`
  for cart/money/image helpers and types.

### 2. Routes & pages
- `src/pages/index.astro` — home (hero, featured cheeses, press band, visit CTA).
- `src/pages/collections/[handle].astro` — collection/listing (SSR or build-time).
- `src/pages/products/[handle].astro` — product detail (gallery, variants, add-to-cart).
- Content pages as Astro pages or sourced from Shopify Pages: `/about`, `/history`,
  `/meet-our-cheese`, `/visit`, `/press`.
- Preserve existing public URL paths (`/collections/...`, `/pages/...` → decide on
  redirects) to retain SEO equity; map old → new with 301s.

### 3. Cart (React island)
- A single interactive island (`client:load`) for the cart drawer; persist `cartId` in
  `localStorage`; state via **Nanostores** (lightweight, Astro-recommended) or React
  context.
- Mutations via Storefront Cart API; "Checkout" routes the user to `cart.checkoutUrl`.

### 4. SEO foundation (the starter has ~none)
- Add `@astrojs/sitemap`; add `public/robots.txt`.
- Extend `Layout.astro` with per-page `<title>`/meta description, canonical, and Open Graph
  / Twitter cards.
- JSON-LD: `Organization` + `LocalBusiness` (site-wide, with the **canonical NAP**, hours,
  geo) and `Product` (per product, from Storefront data).
- Surface awards/press as visible content + structured credibility.

### 5. Performance
- Use Astro `<Image>` + Netlify Image CDN for all photography; lazy-load below the fold.
- Keep JS minimal — islands only where interactive (cart, variant selector). Astro ships
  zero JS by default, which should beat the current Shopify theme on CWV.
- Validate against the audit's **[Verify in session]** PSI/CWV baseline before/after.

### 6. Branding
- Replace starter theme tokens in `src/styles/globals.css` with the creamery palette and
  typography; build a small component kit (buttons, product card, section headers).

---

## Migration & launch checklist
- [ ] Storefront API custom app created; token in env (not committed).
- [ ] Catalog restructured in admin (Cheese / Cider / Gifts / Merch; future: shipping +
      CSA/subscription collections).
- [ ] Old URL → new URL 301 map; legacy domains 301'd to canonical.
- [ ] JSON-LD, OG, sitemap, robots verified in Google Search Console.
- [ ] PSI/Lighthouse before vs. after captured.
- [ ] Checkout hand-off tested end-to-end (cart → Shopify checkout → order in admin).
- [ ] DNS/hosting cutover plan (Netlify) with rollback.

---

## Out of scope for the front-end rebuild (flagged, but ops/backend)
- **Perishable cold-chain shipping** and subscription/CSA fulfillment — the biggest revenue
  opportunity (see audit §6), but it's a backend/ops decision (packaging, carriers, or a
  channel like Goldbelly). Design the front-end so adding shippable products + a
  subscription collection is a content change, not a re-architecture.
