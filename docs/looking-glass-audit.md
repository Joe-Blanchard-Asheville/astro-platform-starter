# Looking Glass Creamery — Web & Online Presence Audit

**Prepared:** June 2026
**Subject:** Looking Glass Creamery, LLC — Columbus / Green Creek (Polk County), NC
**Primary site:** [lookingglasscreamery.com](https://www.lookingglasscreamery.com/) (Shopify)
**Purpose:** Inform a front-end rebuild on the existing Shopify backend (headless Astro + Shopify Storefront API). See the companion doc: [`looking-glass-rebuild-recommendations.md`](./looking-glass-rebuild-recommendations.md).

> **Method & caveats.** This audit was assembled from **free / public sources** (live web
> search, public review/citation sites, and structural evidence from public URLs). The
> live Shopify site blocks automated crawlers, and this environment's network policy
> blocks direct `curl`/fetch, so items requiring a live crawl, Lighthouse run, Google
> Search Console, or Shopify admin are explicitly marked **[Verify in session/admin]**.
> Numbers from third-party sites (followers, review counts) drift over time — treat as of
> mid-2026. Replace estimates with Google Search Console + PageSpeed Insights + Shopify
> Analytics data when access is available.

---

## 1. Executive summary

Looking Glass Creamery is a **well-respected, award-winning** artisan creamery (Good Food
Award 2018, World Championship Cheese medals, Williams-Sonoma, Garden & Gun, NY Times,
USA Today) with **strong brand equity and genuine press assets**. The weakness is **digital
execution, not reputation**: the web presence is **fragmented across 3–4 properties**, local
SEO signals are **inconsistent and geographically stale** ("Asheville"-era branding for a
business that moved to Polk County), and the storefront **monetizes almost none of the
brand's national demand** (no perishable shipping; online store = jam, hats, shirts, gift
cards only).

**Posture:** Strong brand + content assets, weak technical/SEO hygiene, large untapped
DTC opportunity.

### Top 5 quick wins (low effort, high impact)
1. **Fix NAP consistency** everywhere (one exact name, address, phone). Today: "Harmon"
   vs "Harmons Dairy Ln," city listed as Columbus / Green Creek / Landrum SC across sites.
2. **Claim/clean up legacy listings** — the old Fairview location still shows on Yelp as
   *CLOSED*, and stale "Asheville" references confuse Google's location signals.
3. **Consolidate to one canonical domain** — 301 `lookingglasscheese.com` and the
   `looking-glass-creamery-llc-2.square.site` into `lookingglasscreamery.com`.
4. **Add structured data** (LocalBusiness/Organization + Product JSON-LD) and Open Graph
   tags — currently minimal/absent.
5. **Launch a review-generation routine** at the farm store (QR → Google) to lift review
   *volume* (sentiment is already excellent but counts are small).

### Top 3 bigger lifts (higher effort, high impact)
1. **Headless front-end rebuild** (Astro + Shopify Storefront API) for speed, design
   control, and modern SEO — the subject of this engagement.
2. **Enable perishable DTC shipping** (cold-chain or Goldbelly-style) — the single largest
   revenue lever; regional peers ship and Looking Glass does not. *(Backend/ops scope, not
   front-end — but the rebuild should be designed to support it.)*
3. **Build a content/SEO engine** (cheese education, recipes, agritourism/"visit" content)
   to capture the search demand the brand's press already proves exists.

---

## 2. Current site & platform

### Platform — confirmed Shopify
Evidence: canonical Shopify URL patterns across the public site —
`/collections/all` (products), and `/pages/<handle>` for content:
[Products](https://www.lookingglasscreamery.com/collections/all),
[Meet our Cheese](https://www.lookingglasscreamery.com/pages/meet-our-cheese),
[About/Staff](https://www.lookingglasscreamery.com/pages/about-us),
[Visit Us](https://www.lookingglasscreamery.com/pages/farm-store-in-columbus),
[History](https://www.lookingglasscreamery.com/pages/history),
[Press](https://www.lookingglasscreamery.com/pages/press-page).

### Page / navigation inventory (public)
| Page | URL | Type |
|---|---|---|
| Home | `/` | Shopify |
| Products | `/collections/all` | Collection |
| Meet our Cheese | `/pages/meet-our-cheese` | Content page |
| About / Staff | `/pages/about-us` | Content page |
| History | `/pages/history` | Content page |
| Press | `/pages/press-page` | Content page |
| Visit Us (farm store) | `/pages/farm-store-in-columbus` | Content page |
| Cart / Checkout / Account | `/cart`, `/checkout`, `/account` | **Backend (Shopify)** |

### Theme, apps, checkout, product/collection setup — **[Verify in session/admin]**
Theme name, installed apps (reviews, popups, subscriptions), checkout customizations, and
the product/variant/collection taxonomy require the live DOM or Shopify admin. Capture via
a networked Lighthouse/crawl run or admin access. *What is knowable now:* the catalog is
**shallow** — the public store sells **jam, hats, shirts, and gift cards** only; cheese,
cider, ice cream, and meat are **in-person only** (no shipping).

### Mobile responsiveness — **[Verify in session]**
Not directly testable here; flag for a real-device + Lighthouse mobile pass.

### What's safe to rebuild vs. tied to the backend
See the matrix in [`looking-glass-rebuild-recommendations.md`](./looking-glass-rebuild-recommendations.md#safe-to-rebuild-vs-backend-tied).

**Findings → Severity → Recommendation**
- Shallow online catalog (no perishables) → **High** → *Bigger lift:* enable DTC shipping; restructure collections (Cheese, Cider, Gifts/CSA, Merch).
- Theme/app stack unknown → **Medium** → *Quick win:* audit installed apps in admin; remove unused apps (each adds JS weight) before/at rebuild.
- Content lives in Shopify Pages → **Low** → *Quick win:* these are pure front-end and safe to redesign.

---

## 3. Performance & technical SEO

> **[Verify in session]** Core Web Vitals (LCP/INP/CLS), Lighthouse scores, and field
> (CrUX) data could not be captured (PageSpeed API rate-limited without a key; live crawl
> blocked). **Action:** run PageSpeed Insights (mobile + desktop) on home, a product, and
> a collection page, and pull CrUX/Core Web Vitals from **Google Search Console** once
> access is available. The headless rebuild (section in companion doc) is the structural
> fix for most performance findings.

Knowable / high-probability technical items to confirm and address:
- **HTTPS** — present (site served over HTTP/2 + TLS).
- **Schema/structured data** — appears minimal; add `LocalBusiness`, `Organization`,
  `Product`, and `BreadcrumbList` JSON-LD. **Severity: Medium.**
- **Sitemap/robots** — Shopify auto-generates `/sitemap.xml` and `/robots.txt`; confirm
  they're submitted in Google Search Console. **Severity: Low.**
- **Duplicate-domain / canonical risk** — `lookingglasscheese.com` + the Square site
  competing with the Shopify domain dilutes authority and can cause duplicate-content and
  citation confusion. **Severity: High → quick win (301 + canonical).**
- **Broken links / crawl health** — **[Verify in session]** run a crawler (e.g.
  Screaming Frog free tier) post-access.

---

## 4. On-page & content

**Strengths:** genuinely strong story and credentials (farm, family, awards, named
cheeses like **Ellington**, **Ridgeline**, **Bear Wallow**, **Drovers Road**). Press page
and history page exist.

**Gaps:**
- **Keyword targeting / metadata** — **[Verify in session]** titles & meta descriptions
  per page; likely generic/theme-default. Target local + product intent:
  *"artisan cheese near Tryon/Landrum,"* *"NC farmstead cheese,"* *"Polk County creamery,"*
  *"cheese gift box NC."*
- **Geo signals are stale** — lingering "Asheville/Fairview" language (and the
  `@ashevillecheese` social handles) fight the current Columbus/Polk County location.
  **Severity: High → quick win** (align copy + metadata to current geography).
- **Thin product copy** — merch/jam product descriptions are an SEO and conversion
  opportunity (tasting notes, pairings, provenance).
- **No content engine** — competitors and the brand's own press prove demand for cheese
  education, recipes, and agritourism content; there's no blog/recipe hub capturing it.
  **Severity: Medium → bigger lift.**

---

## 5. Off-site presence

### Google Business Profile & reviews
- **GBP** — exists (drives the Tripadvisor/Yelp/maps entries); **[Verify]** confirm it's
  claimed, categorized ("Cheese shop" + "Farm" + "Ice cream shop"), with current hours
  (Thu–Sat 11–5, Sun 12–5), photos, and products. **Quick win.**
- **Sentiment is excellent, volume is low:** Tripadvisor **5.0** but ranked **#14 of 18**
  Columbus restaurants; Facebook **~96% recommend (18 reviews)**; Yelp **~16 reviews**;
  an aggregate **~94% recommend (25 reviews)**. → **Run a review-generation program.**
  Sources:
  [Tripadvisor farmstore](https://www.tripadvisor.com/Restaurant_Review-g49046-d19711366-Reviews-Looking_Glass_Creamery_Farmstore-Columbus_North_Carolina.html),
  [Tripadvisor attraction](https://www.tripadvisor.com/Attraction_Review-g49046-d19792538-Reviews-Looking_Glass_Creamery-Columbus_North_Carolina.html),
  [Yelp](https://www.yelp.com/biz/looking-glass-creamery-green-creek),
  [Facebook](https://www.facebook.com/ashevillecheese/).

### Social
- **Instagram** [@ashevillecheese](https://www.instagram.com/ashevillecheese/) (~8.1k) and
  **Facebook** [@ashevillecheese](https://www.facebook.com/ashevillecheese/) (~10.5k).
  Decent reach, but the **handle is off-brand** post-move. **Severity: Medium** —
  rebranding handles is disruptive (loses URL equity); at minimum add clear current-location
  info and link to the canonical domain.

### Local citations / NAP — **High severity, quick wins**
- **Name/address inconsistencies:** "Harmon Dairy Lane" vs "Harmons Dairy Ln"; city as
  **Columbus** vs **Green Creek** vs **Landrum, SC** across Yelp, Tripadvisor, Nextdoor,
  Wheree, ZoomInfo, etc.
- **Legacy listings:** old **Fairview** location shows **CLOSED** on
  [Yelp](https://www.yelp.com/biz/looking-glass-creamery-fairview) — clean up/merge.
- **Fix:** lock one canonical NAP, then update Google, Bing, Apple Maps, Yelp,
  Tripadvisor, and data aggregators.

### Backlinks / PR — **underleveraged asset**
Strong earned coverage: **NY Times, USA Today, Garden & Gun** (Ellington named a Top 10
Southern cheese), **Cooking Light**, **Traditional Home**, **Williams-Sonoma**, **American
Cheese Society**, **Good Food Award 2018**, **World Championship Cheese Competition**, plus
regional ([Carolina Epicurean](https://carolinaepicurean.com/looking-glass-creamery-wins-2018-good-food-award-announces-farm-expansion/),
[NCDA&CS Flavor NC](https://blog.ncagr.gov/2014/03/20/flavor-nc-looking-glass-creamery/),
[Tryon Daily Bulletin](https://tryondailybulletin.com/2024/08/07/life-in-our-foothills-august-2024-a-taste-of-tradition-the-journey-of-looking-glass-creamery/)).
**Severity: Medium → quick win:** surface these as a credibility band on the rebuilt site
and pursue link reclamation (ensure each outlet links to the canonical domain).

---

## 6. Competitive snapshot

| Creamery | Platform | Ships cheese? | Notable strengths | Where LGC loses |
|---|---|---|---|---|
| **Boxcarr Handmade Cheese** (Cedar Grove, NC) — [site](https://www.boxcarrhandmadecheese.com) | Squarespace (`/onlineshop`, `/shipping`, `/farmpickup`) | **Yes** (nationwide) + **Cheese CSA** + Whole Foods | National DTC shipping, CSA subscription, retail distribution | LGC has **no shipping**, no subscription, narrow retail |
| **Chapel Hill Creamery** (Chapel Hill, NC) — [site](https://www.chapelhillcreamery.com/) | WordPress + **Square** store ([orders](https://chapelhillcreamery.square.site/)) | Pre-order pickup + markets | Clean weekly pre-order pickup flow, strong market presence | LGC pickup/online ordering flow is thinner |
| **Jasper Hill Farm** (VT) — *aspirational DTC benchmark* — [shop](https://www.jasperhillfarm.com/shop) | DTC + Goldbelly | **Yes** (nationwide, gift boxes, **Cheese Club**) | Gift boxes, monthly club, affineur brand storytelling | LGC monetizes none of its national brand demand |

**Takeaway:** Looking Glass's **brand and product credentials rival or exceed** these
peers, but it **trails on e-commerce capability** — every comparable ships and/or runs a
subscription; Looking Glass sells merch and jam. Closing the shipping/subscription gap is
the biggest competitive move; the front-end rebuild is the enabler.

---

## 7. Prioritized roadmap (quick wins → bigger lifts)

| # | Action | Effort | Impact | Type | Owner |
|---|---|---|---|---|---|
| 1 | Lock canonical NAP; fix all listings (incl. CLOSED Fairview on Yelp) | Low | High | SEO/local | Marketing |
| 2 | 301 `lookingglasscheese.com` + Square site → canonical domain | Low | High | Tech SEO | Dev |
| 3 | Add LocalBusiness/Organization/Product JSON-LD + Open Graph | Low | High | Tech SEO | Dev |
| 4 | Claim/optimize GBP (categories, hours, photos, products) | Low | High | Local | Marketing |
| 5 | Review-generation routine (in-store QR → Google) | Low | Med-High | Reputation | Ops |
| 6 | Align copy/metadata to current Columbus/Polk geography | Low | Med | On-page SEO | Marketing |
| 7 | Surface press/awards credibility band + link reclamation | Low | Med | Off-site | Marketing |
| 8 | Run PSI/Lighthouse + GSC; fix CWV/broken links | Med | High | Performance | Dev |
| 9 | Audit & prune Shopify apps; tidy collections/product copy | Med | Med | Tech/SEO | Dev |
| 10 | **Headless front-end rebuild** (Astro + Storefront API) | High | High | Build | Dev |
| 11 | Content/recipe/agritourism engine | High | Med-High | Content/SEO | Marketing |
| 12 | **Enable perishable DTC shipping** + subscription/CSA | High | High | Revenue/Ops | Ops/Dev |

---

## Sources
- [lookingglasscreamery.com](https://www.lookingglasscreamery.com/) and public pages (`/collections/all`, `/pages/meet-our-cheese`, `/pages/about-us`, `/pages/history`, `/pages/press-page`, `/pages/farm-store-in-columbus`)
- [lookingglasscheese.com](https://www.lookingglasscheese.com/) · [Square site](https://looking-glass-creamery-llc-2.square.site/)
- [Instagram @ashevillecheese](https://www.instagram.com/ashevillecheese/) · [Facebook @ashevillecheese](https://www.facebook.com/ashevillecheese/)
- [Tripadvisor (farmstore)](https://www.tripadvisor.com/Restaurant_Review-g49046-d19711366-Reviews-Looking_Glass_Creamery_Farmstore-Columbus_North_Carolina.html) · [Tripadvisor (attraction)](https://www.tripadvisor.com/Attraction_Review-g49046-d19792538-Reviews-Looking_Glass_Creamery-Columbus_North_Carolina.html) · [Yelp (Green Creek)](https://www.yelp.com/biz/looking-glass-creamery-green-creek) · [Yelp (Fairview, CLOSED)](https://www.yelp.com/biz/looking-glass-creamery-fairview)
- [Carolina Epicurean — Good Food Award](https://carolinaepicurean.com/looking-glass-creamery-wins-2018-good-food-award-announces-farm-expansion/) · [Carolina Epicurean — World Championship medals](https://carolinaepicurean.com/looking-glass-creamery-medals-in-world-championship-cheese-competition/) · [NCDA&CS Flavor NC](https://blog.ncagr.gov/2014/03/20/flavor-nc-looking-glass-creamery/) · [Tryon Daily Bulletin (2024)](https://tryondailybulletin.com/2024/08/07/life-in-our-foothills-august-2024-a-taste-of-tradition-the-journey-of-looking-glass-creamery/) · [Perishable News — Ellington](https://perishablenews.com/deli/looking-glass-creamerys-ellington-cheese-getting-lots-of-attention/)
- Competitors: [Boxcarr Handmade Cheese](https://www.boxcarrhandmadecheese.com) · [Chapel Hill Creamery](https://www.chapelhillcreamery.com/) ([Square orders](https://chapelhillcreamery.square.site/)) · [Jasper Hill Farm](https://www.jasperhillfarm.com/shop)
