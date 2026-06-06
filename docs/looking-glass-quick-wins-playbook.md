# Looking Glass Creamery — Quick-Wins Playbook (Detailed Instructions)

**Companion to:** [`looking-glass-quick-wins-checklist.md`](./looking-glass-quick-wins-checklist.md)
**What this is:** step-by-step instructions, click-paths, and copy-paste-ready assets for
each quick win. A non-developer can do most of this; tasks needing Shopify theme edits are
marked **[Dev]**.

> **Before you start — confirm these facts (they appear everywhere below):**
> - Exact street: **"Harmon Dairy Lane"** vs **"Harmons Dairy Ln"** — check your mail/deed
>   and pick the legal spelling. *(Examples below use "Harmon Dairy Lane" — change if wrong.)*
> - City for mailing/Google: **Columbus, NC 28722** (the USPS city). "Green Creek" is the
>   township; don't mix them in listings.
> - Confirm phone **(828) 222-0751** and hours **Thu–Sat 11–5, Sun 12–5** are still current.

---

## Task 0 — Lock the canonical business identity

Fill this in once and paste it identically everywhere:

```
Name:    Looking Glass Creamery
Address: 115 Harmon Dairy Lane, Columbus, NC 28722      ← confirm spelling
Phone:   (828) 222-0751
Email:   <your public email>
Hours:   Thu–Sat 11:00 AM–5:00 PM; Sun 12:00–5:00 PM; Mon–Wed closed
Domain:  https://www.lookingglasscreamery.com
```
Save it where staff can see it. Use **this exact text** in every listing — same
abbreviations, same punctuation. Google rewards consistency.

---

## Task 1 — Fix NAP across the web

**Goal:** identical Name/Address/Phone everywhere.

1. **Find your listings.** Google each of these and note the URL + whether you can log in:
   Google Business Profile, Bing Places, Apple Business Connect, Yelp, Tripadvisor,
   Facebook, Instagram (bio), Nextdoor, Foursquare, Yellow Pages, Data Axle, Localeze,
   `firstpeaknc.com`, `romanticasheville.com`, `ashevillegoods.com`, `visitncfarms.com`.
2. **Make a tracking sheet** with columns: Site | URL | Claimed? | NAP correct? | Fixed date.
3. **Edit each** to match Task 0 exactly. For directories you don't control, use their
   "suggest an edit" / "claim this business" link, or email them.
4. **Tip:** a free scan at Moz Local Check or Yext's free scan will list inconsistencies
   fast — use it to build your sheet, but you don't need to buy the paid product.

**Done when:** your sheet shows every controllable listing = correct.

---

## Task 2 — Claim & optimize Google Business Profile (GBP)

**Click-path:** go to [google.com/business](https://www.google.com/business/) → sign in →
search your business → **Claim/Manage**. If someone else verified it, use "Request access."

Then complete every field:
- **Business name:** `Looking Glass Creamery` (no keyword stuffing).
- **Primary category:** `Cheese shop`. **Additional:** `Creamery`, `Farm`, `Ice cream shop`,
  `Gourmet grocery store`.
- **Address:** Task 0. Tick "I deliver/serve customers at my location" so the storefront shows.
- **Hours:** Task 0 + add special/holiday hours.
- **Phone / Website:** Task 0 (`https://www.lookingglasscreamery.com`).
- **Attributes:** "Family-owned," "Women-owned" (if applicable), "In-store pickup,"
  "Wheelchair accessible," outdoor seating, etc.
- **Photos:** upload 15–20 high-res — logo, exterior with signage, interior, cheese case,
  ice cream, charcuterie boards, the farm/cows, staff. Add a few each month.
- **Products:** add your sellable items (cheeses, cider, gifts) with photos + prices.
- **Google Posts:** publish a post (event, seasonal flavor, "now open Sundays"). Repeat
  ~monthly.

**Copy-paste "from the business" description (≤750 chars — edit to taste):**
```
Looking Glass Creamery is an award-winning farmstead creamery in Columbus, NC, in the
foothills near Tryon and Landrum. Since 2009 we've handcrafted small-batch cheeses from
our own herd, alongside hard cider, house-made ice cream, preserves, and pastured meats.
Visit our farm store for grilled cheese, charcuterie boards, ice cream by the scoop, and
tastings of our nationally recognized cheeses—featured by Garden & Gun, Williams-Sonoma,
and the Good Food Awards. Open Thursday–Sunday. Come taste why our cheese has earned a
place on tables across the country.
```

**Done when:** profile is verified, every field complete, 15+ photos, products added.

---

## Task 3 — Consolidate to one domain **[Dev]**

**Goal:** one canonical site; old domains redirect to it (preserves SEO, ends customer
confusion).

1. **Decide canonical:** `https://www.lookingglasscreamery.com`.
2. **`lookingglasscheese.com`** — wherever its DNS/host is managed, set up **301 (permanent)
   redirects**. Best: map each old page to its closest new page (e.g. old `/cheese` →
   `/pages/meet-our-cheese`). If that's too much, 301 the whole domain to the homepage.
   - If it's on Squarespace/another host: use that host's redirect/forwarding settings, or
     point the domain's DNS at the new site and add redirect rules.
3. **`looking-glass-creamery-llc-2.square.site`** — in Square Online, either unpublish it or
   set the site's domain to redirect; update any links/printed materials that point to it.
4. **Inside Shopify**, you can add URL redirects for any retired internal paths:
   Shopify admin → **Online Store → Navigation → URL Redirects → Create**. (Redirects for
   *other domains* must be done at that domain's host, not in Shopify.)
5. **Verify:** visit each old URL; confirm the browser lands on the canonical site with a
   301 (check in browser devtools → Network, or redirect-checker.org).

**Done when:** old domains/pages 301 to canonical; no second live storefront.

---

## Task 4 — Clean up legacy / duplicate listings

1. **Yelp (old Fairview location):** open the
   [Fairview listing](https://www.yelp.com/biz/looking-glass-creamery-fairview) → "Edit" /
   "Report" → mark **Permanently closed** (or "moved"). Make sure the
   [current listing](https://www.yelp.com/biz/looking-glass-creamery-green-creek) has the
   correct NAP (note it currently reads "Green Creek" + "Harmons Dairy Ln" — align to Task 0).
2. **Google:** search the old Fairview location on Maps → "Suggest an edit" → "Close or
   remove" → **Permanently closed**. If you see two profiles for the current location,
   request a **merge** (GBP support).
3. **Tripadvisor / Facebook:** ensure only the current location shows as open; close/merge
   stale Fairview entries.
4. **Sweep wording:** anywhere a listing says "Asheville/Fairview," update to Columbus/Polk
   County (the Instagram/Facebook handle `@ashevillecheese` is harder — see note below).

> **On the `@ashevillecheese` handle:** renaming loses follower-link equity and inbound
> links, so don't rush it. Minimum fix now: update the **bio/about** on both profiles to
> the current location + canonical link. A full rename is a separate branding decision.

**Done when:** only the Columbus location appears open across Google/Yelp/Tripadvisor/FB.

---

## Task 5 — Structured data (schema) + Open Graph **[Dev]**

**Where:** your Shopify theme. Edit in admin → **Online Store → Themes → ⋯ → Edit code**.
Add the site-wide JSON-LD to `layout/theme.liquid` just before `</head>`. *(Verify the theme
doesn't already output Product schema before adding the Product block, to avoid duplicates.)*

**LocalBusiness JSON-LD (paste in `theme.liquid`, edit values):**
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FoodEstablishment",
  "@id": "https://www.lookingglasscreamery.com/#business",
  "name": "Looking Glass Creamery",
  "url": "https://www.lookingglasscreamery.com",
  "telephone": "+1-828-222-0751",
  "image": "https://www.lookingglasscreamery.com/<path-to-logo-or-photo>.jpg",
  "priceRange": "$$",
  "servesCuisine": "Artisan cheese, ice cream, cider",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "115 Harmon Dairy Lane",
    "addressLocality": "Columbus",
    "addressRegion": "NC",
    "postalCode": "28722",
    "addressCountry": "US"
  },
  "geo": { "@type": "GeoCoordinates", "latitude": "35.25", "longitude": "-82.19" },
  "openingHoursSpecification": [
    { "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Thursday","Friday","Saturday"],
      "opens": "11:00", "closes": "17:00" },
    { "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Sunday"], "opens": "12:00", "closes": "17:00" }
  ],
  "sameAs": [
    "https://www.facebook.com/ashevillecheese/",
    "https://www.instagram.com/ashevillecheese/"
  ]
}
</script>
```
> Replace the `image` path and confirm the lat/long (right-click your spot in Google Maps →
> the coordinates are the first menu item).

**Open Graph + Twitter tags (in `<head>` of `theme.liquid`):**
```liquid
<meta property="og:site_name" content="Looking Glass Creamery">
<meta property="og:title" content="{{ page_title }}">
<meta property="og:description" content="{{ page_description | default: shop.description }}">
<meta property="og:type" content="website">
<meta property="og:url" content="{{ canonical_url }}">
<meta property="og:image" content="{{ '<default-share-image>.jpg' | asset_url | prepend: 'https:' }}">
<meta name="twitter:card" content="summary_large_image">
```

**Validate:** paste a URL into [Google Rich Results Test](https://search.google.com/test/rich-results)
and the [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/).

**Done when:** Rich Results Test passes for home + a product page; shared links show a card.

---

## Task 6 — Geo-aligned titles & meta descriptions

**Where (per page):** Shopify admin → **Online Store → Pages** (or Products/Collections) →
open the page → scroll to **Search engine listing → Edit** → set Page title + Meta
description. Keep titles ≤60 chars, descriptions ≤155 chars.

**Copy-paste drafts:**

| Page | Page title | Meta description |
|---|---|---|
| Home | `Looking Glass Creamery | Award-Winning NC Farmstead Cheese` | `Handcrafted farmstead cheese, cider & ice cream in Columbus, NC near Tryon & Landrum. Visit our farm store Thu–Sun. Featured in Garden & Gun.` |
| Visit / Farm Store | `Visit Our Farm Store | Looking Glass Creamery, Columbus NC` | `Find us at 115 Harmon Dairy Lane, Columbus, NC. Grilled cheese, charcuterie, ice cream & tastings. Open Thu–Sat 11–5, Sun 12–5. Directions & hours.` |
| Meet Our Cheese | `Our Cheeses | Handmade in Polk County, NC | Looking Glass` | `Meet our award-winning cheeses—Ellington, Ridgeline, Bear Wallow & more—handcrafted from our own herd in the NC foothills. Tasting notes & pairings.` |
| About / Staff | `Our Story | Family Farmstead Creamery in Western NC` | `Since 2009, the Perkins family has crafted small-batch cheese on our Polk County farm. Meet the team behind Looking Glass Creamery near Tryon, NC.` |
| Press | `Press & Awards | Looking Glass Creamery` | `Featured by Garden & Gun, Williams-Sonoma, NY Times & USA Today. See the press & awards behind our nationally recognized NC farmstead cheese.` |
| Products | `Shop Cheese, Gifts & More | Looking Glass Creamery` | `Shop preserves, gifts, merch & gift cards from our NC farmstead creamery. Cheese, cider & ice cream available at our Columbus farm store.` |

Also: search your site copy for "Asheville"/"Fairview" and replace with Columbus/Polk County
(except the social handles). Confirm the **Visit** page has full address, an embedded Google
Map, driving directions, and current hours.

**Done when:** each key page has a unique, geo-correct title + meta description live.

---

## Task 7 — Press/awards credibility band + link reclamation

1. **Homepage band [Dev or theme editor]:** add a simple logo strip "As Seen In" with
   Garden & Gun, Williams-Sonoma, NY Times, USA Today, Good Food Awards, American Cheese
   Society. Use text or grayscale logos; link to the Press page.
2. **Keep the Press page current** with links to each article (and a short pull-quote).
3. **Link reclamation:** Google `"Looking Glass Creamery"` and note sites that mention you.
   For ones linking to an **old domain** (or not linking at all), email a friendly request:
   > "Thanks for featuring us! Could you update the link to our current site,
   > https://www.lookingglasscreamery.com? We've consolidated our web address."
4. **Unlinked mentions** (press that names you without a link): ask for a link too.

**Done when:** awards/press visible on home; major mentions point to the canonical domain.

---

## Task 8 — Search Console & sitemap hygiene **[Dev-ish]**

1. **Verify the site** in [Google Search Console](https://search.google.com/search-console)
   → Add property → use the **Domain** option (add the TXT record at your DNS host) or the
   URL-prefix option (HTML tag in `theme.liquid`).
2. **Submit the sitemap:** GSC → **Sitemaps** → enter `sitemap.xml` (Shopify generates it at
   `/sitemap.xml`).
3. **Check Indexing/Pages** for errors (404s, "discovered not indexed"); fix or redirect.
4. **Core Web Vitals report** (GSC → Experience) — this gives you the **real CWV baseline**
   the audit marked as "to verify." Also run
   [PageSpeed Insights](https://pagespeed.web.dev/) on home + a product page (mobile &
   desktop) and save the scores.
5. Repeat for [Bing Webmaster Tools](https://www.bing.com/webmasters) (you can import from GSC).

**Done when:** verified, sitemap submitted, no critical coverage errors, CWV baseline saved.

---

## Task 9 — Review-generation routine

1. **Create your Google review short link:** GBP dashboard → **Ask for reviews** → copy the
   link (looks like `https://g.page/r/XXXX/review`). Shorten it if you like.
2. **Make a QR code** (free at qr-code-generator.com or qrcode.tec-it.com) pointing to that
   link. Print it for the counter, tables, receipts, and ice-cream window. Caption:
   *"Loved it? Leave us a Google review →"*
3. **Staff script:** "If you enjoyed today, a quick Google review really helps our small
   farm—there's a QR code right here." Ask at the moment of delight (after a great tasting).
4. **Respond to every review** within a few days—thank positives by name; respond calmly and
   helpfully to any negative ones.
5. Optional: add the review link to email receipts / order-confirmation emails.

**Done when:** QR + script live in-store; reviews trending up; all reviews answered.

---

## Task 10 — Measure

1. **Confirm GA4** is installed (Shopify admin → Online Store → Preferences → Google
   Analytics, or via the Google & YouTube channel app). 
2. **Record today's baseline:**
   - GBP Insights: profile views, searches, calls, direction requests, website clicks.
   - GA4: organic sessions / month, top landing pages.
   - Reviews: count + average on Google, Yelp, Tripadvisor, Facebook.
3. **Re-check at 30 / 60 / 90 days.** Expect GBP views/calls/directions and review counts to
   rise first (local fixes act fastest), then organic sessions.

**Done when:** baseline captured and a recurring monthly check is scheduled.

---

### Quick reference — where each task is done
| Task | Done in |
|---|---|
| 1, 4 | Each listing site (Yelp, GBP, directories) |
| 2, 9 | Google Business Profile dashboard |
| 3 | Old domains' DNS/host + Shopify URL Redirects |
| 5, 7(band) | Shopify theme code (`theme.liquid`) |
| 6 | Shopify admin → Pages/Products/Collections → SEO listing |
| 8, 10 | Google Search Console / PageSpeed / GA4 |
