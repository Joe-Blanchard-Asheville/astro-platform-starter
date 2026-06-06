# Looking Glass Creamery — Quick-Wins Action Checklist

**Companion to:** [`looking-glass-audit.md`](./looking-glass-audit.md)
**Scope:** Low-effort, high-impact fixes on the **existing Shopify site + listings** — **no
rebuild required.** Do these first; they deliver most of the near-term ROI.

**How to use:** each task has an owner, concrete steps, an effort estimate, and a "done
when" acceptance check. Tackle in order — they're sequenced so earlier tasks unblock later
ones (e.g. lock the canonical NAP before updating every listing).

**Suggested sequence / sprint:**
- **Week 1:** Tasks 1–4 (foundational: NAP, GBP, domain consolidation, listings)
- **Week 2:** Tasks 5–8 (schema, on-page geo, reviews, press band)
- **Ongoing:** Task 9 (review generation), Task 10 (measurement)

---

## 0. Prerequisite — lock the canonical business identity (15 min)
Everything else references this. Decide and write down the **one** official version of:
- **Name:** `Looking Glass Creamery` (decide if `, LLC` is included publicly — pick one)
- **Address:** one exact spelling — e.g. `115 Harmon Dairy Lane, Columbus, NC 28722`
  (resolve "Harmon" vs "Harmons", and Columbus vs Green Creek vs Landrum)
- **Phone:** `(828) 222-0751`
- **Hours:** Thu–Sat 11am–5pm, Sun 12–5pm
- **Primary domain:** `lookingglasscreamery.com`

> **Done when:** a one-line "official NAP" is saved somewhere the team shares (this file or a pinned note).

---

## 1. Fix NAP consistency across the web — **Owner: Marketing · Effort: M · Impact: High**
Inconsistent name/address/city across listings confuses Google and hurts local ranking.
- [ ] Audit current listings: Google, Bing Places, Apple Maps, Yelp, Tripadvisor, Facebook, Nextdoor, Foursquare, data aggregators (Data Axle, Localeze).
- [ ] Update each to **exactly** match the canonical NAP from Task 0.
- [ ] Note logins/claim status for each (some need claiming first — see Task 4).
- **Done when:** name, address, phone, hours are identical on every listing you control.

## 2. Claim & optimize Google Business Profile — **Owner: Marketing · Effort: M · Impact: High**
GBP is the #1 local-SEO and discovery surface.
- [ ] Confirm the profile is **claimed/verified** (google.com/business).
- [ ] Set primary category `Cheese shop`; add secondary `Farm`, `Ice cream shop`, `Creamery`.
- [ ] Set correct hours (+ holiday hours), service area, and "from the business" description with current geography (Polk County / near Tryon & Landrum).
- [ ] Upload 15–20 current photos (farm, store, cheeses, ice cream, charcuterie).
- [ ] Add Products (cheeses, cider, gifts) and enable messaging if you'll monitor it.
- [ ] Post a few Google Posts (events, seasonal offerings).
- **Done when:** profile is verified, fully categorized, with current hours/photos/products.

## 3. Consolidate to one domain — **Owner: Dev · Effort: S · Impact: High**
Multiple live sites split SEO authority and confuse customers.
- [ ] Decide canonical = `lookingglasscreamery.com`.
- [ ] **301 redirect** `lookingglasscheese.com` → canonical (page-to-page where possible).
- [ ] Retire/redirect the legacy `looking-glass-creamery-llc-2.square.site` (or at minimum unlist it and point links to canonical).
- [ ] Update any printed/profile links that point to old domains.
- **Done when:** old domains 301 to the canonical site; no duplicate live storefront.

## 4. Clean up legacy / duplicate listings — **Owner: Marketing · Effort: S–M · Impact: High**
- [ ] Mark the **old Fairview location CLOSED/permanently closed** on Yelp and anywhere it still appears as active.
- [ ] Merge duplicate Google/Tripadvisor entries if more than one exists.
- [ ] Remove stale "Asheville/Fairview" wording that implies the wrong location.
- **Done when:** only the current Columbus location appears as open across major sites.

## 5. Add structured data (schema) + Open Graph — **Owner: Dev · Effort: S · Impact: Med-High**
Helps Google understand the business and improves how links preview when shared.
- [ ] Add `LocalBusiness`/`Organization` JSON-LD site-wide (canonical NAP, hours, geo, logo, sameAs links to socials).
- [ ] Add `Product` JSON-LD on product pages (Shopify themes often include this — verify, don't double up).
- [ ] Add Open Graph + Twitter card tags (title, description, image) on key pages.
- [ ] Validate with Google's Rich Results Test.
- **Done when:** Rich Results Test passes for the homepage and a product page.

## 6. Align on-page copy & metadata to current geography — **Owner: Marketing · Effort: M · Impact: Med**
- [ ] Update page titles & meta descriptions for Home, Visit, Meet our Cheese, About — include local intent ("artisan cheese near Tryon/Landrum," "Polk County NC creamery," "NC farmstead cheese," "cheese gift box NC").
- [ ] Sweep site copy for outdated "Asheville/Fairview" references; replace with current location.
- [ ] Ensure the Visit page has full address, map embed, directions, and current hours.
- **Done when:** every key page has a unique, geo-correct title + meta description.

## 7. Surface press/awards as a credibility band — **Owner: Marketing · Effort: S · Impact: Med**
You have genuinely strong press (Garden & Gun, NY Times, USA Today, Williams-Sonoma, Good Food Award, World Championship medals) — most visitors never see it.
- [ ] Add an "As seen in / Awards" strip on the homepage and keep the Press page current.
- [ ] **Link reclamation:** check that outlets/directories linking to you point at the canonical domain; request fixes where they point to old domains.
- **Done when:** awards/press are visible above the fold-ish on home; key backlinks point to canonical domain.

## 8. Sitemap & Search Console hygiene — **Owner: Dev · Effort: S · Impact: Med**
- [ ] Verify the property in **Google Search Console** (and Bing Webmaster Tools).
- [ ] Submit `sitemap.xml` (Shopify auto-generates it).
- [ ] Check Coverage/Indexing for errors; check Core Web Vitals report for the real CWV baseline (this fills the audit's "[Verify in session]" gap).
- **Done when:** site verified, sitemap submitted, no critical coverage errors.

## 9. Launch a review-generation routine — **Owner: Ops · Effort: S, ongoing · Impact: Med-High**
Sentiment is excellent but volume is low — more reviews lift local ranking and trust.
- [ ] Create a short Google review link; print a **QR code** for the counter/receipts/tables.
- [ ] Train staff to invite happy customers to review.
- [ ] Respond to all reviews (positive and negative) within a few days.
- **Done when:** review count is trending up month over month; all reviews get a response.

## 10. Measure — **Owner: Marketing/Dev · Effort: S · Impact: (enables everything)**
- [ ] Confirm analytics (GA4) is installed and tracking.
- [ ] Note baseline now: GBP views/calls/directions, organic sessions, review counts.
- [ ] Re-check in 30/60/90 days to confirm the quick wins are moving the numbers.
- **Done when:** a simple baseline + monthly check is in place.

---

## What's intentionally NOT here (bigger lifts — separate decisions)
- **Headless Astro/Tailwind rebuild** (vs. a premium Shopify theme) — design/performance project; see [`looking-glass-rebuild-recommendations.md`](./looking-glass-rebuild-recommendations.md).
- **Perishable DTC shipping + subscription/CSA** — the biggest *revenue* lever, but an ops/backend decision (cold-chain, carriers, or Goldbelly), not a quick win.
- **Content/recipe/agritourism engine** — ongoing content investment.

> **Effort key:** S = under a day · M = a few days · (combine where one owner can batch them).
