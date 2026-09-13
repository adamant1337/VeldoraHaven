# VeldoraHaven — Live State

_Last updated: 2026-09-13 — Nav fix: Outdoor Kitchens collection handle renamed from `outdoor-kitchens-1` → `outdoor-kitchens` to match live nav links (dead link resolved). EcoSmart Fire "Fire Features" product gallery refresh COMPLETE (all Fire Tables). Manhattan 50, Martini 50, Daiquiri 70L, Vertigo 50VL, Gin 90 Low/Chat/Bar/Dining all refreshed: plain-colour no-glass webps + bad 1200×742 primary thumbnails deleted, new 2200×1360 studio shots uploaded via staged-upload flow, reordered studio-first. See ECOSMARTFIRE-GALLERY-001 below._

_Previous update: 2026-09-05 — EcoSmartFire green light received; 6 Designer Fireplace products (Mini T, Ghost, Igloo, T-Lite 3/8, Pop 3T) added to Shopify as DRAFT with MSRP pricing and images, added to Fire Features collection; 8 pre-existing EcoSmart Fire Pit DRAFT products repriced from stale ad-hoc prices down to MSRP per the confirmed pricing engine formula; outdoor-only brand rule compliance fix applied to the 6 new products' copy/images/tags (see `veldorahaven-ecosmartfire-catalog-launch` memory for full detail). See prior update below._

_Previous update: 2026-09-03 — Perplexity/Comet incident cleanup PUBLISHED (theme 206148993366 is now MAIN/live — STATE.md's old "awaiting manual publish" note below is stale, corrected here); /pages/shipping-delivery freight/country contradiction fixed (see SHIPPING-PAGE-FIX-001 below); Halo font/price audit complete (see HALO-FONT-PRICE-CHECK-001 below); PDP section-order + Customisation-options font fix staged in a new preview theme, awaiting manual publish (see PDP-STORY-FEATURES-SWAP-001 below)_

## Active tasks

```yaml
- task_id: ECOSMARTFIRE-GALLERY-001
  title: EcoSmart Fire "Fire Features" product gallery refresh — studio-first order + alt text
  status: COMPLETE (2026-09-13)
  scope: Fire Pits + Fire Tables only. Designer Fireplaces and other categories not touched.
  products_updated:
    fire_pits:
      - Nova 850 (gid://shopify/Product/9464488829270): 5 new studio/install images, studio-first order
      - Nova 600 (gid://shopify/Product/9464492859734): 4 new images, studio-first
      - Stix (gid://shopify/Product/9464492924270): 3 new images, studio-first
      - Stix 8 (gid://shopify/Product/9464493022550): 5 new images, studio-first
      - Mix 600 (gid://shopify/Product/9464493088086): 5 new images, studio-first
      - Mix 850 (gid://shopify/Product/9464493152022): 5 new images, studio-first
      - Pod 30: SKIPPED — no local assets at C:\VeldoraHaven\EcoSmartFire\Product Images\Fire Pits\Pod\Pod 30
      - Pod 40: SKIPPED — no local assets at C:\VeldoraHaven\EcoSmartFire\Product Images\Fire Pits\Pod\Pod 40
    fire_tables:
      - Ark 40: 6 new studio/install images prepended, gallery now 13 images, studio-first
      - Mojito 40: 19 blank alt texts fixed with descriptive copy
      - Manhattan 50 (gid://shopify/Product/11233858162006): 3 plain no-glass webps deleted,
          13 new studio shots uploaded (2200×1360), studio-first order
      - Martini 50 (gid://shopify/Product/11233859734870): same — 3 deleted, 13 new studio shots
      - Daiquiri 70L (gid://shopify/Product/11233860849046): 3 plain webps deleted, 7 images
          uploaded (includes patio install), studio-first. Bad SS file skipped (corrupt).
      - Vertigo 50VL (gid://shopify/Product/11233862455638): 2 indoor lifestyle images deleted
          (brand violation), 1 patio install (2880×1700) added as hero. Studio shots skipped
          (1100×680 — lower-res than existing store images).
      - Gin 90 Low (gid://shopify/Product/11233900822870): 5 deleted (bad 742px primary +
          3 plain webps + drawing), 6 new studio shots uploaded and reordered studio-first
      - Gin 90 Chat (gid://shopify/Product/11233902199126): 5 deleted (bad 742px primary +
          3 plain webps + drawing), 7 new studio+install shots uploaded and reordered studio-first
      - Gin 90 Bar (gid://shopify/Product/11233903706454): 5 deleted (bad 742px primary +
          3 plain webps + drawing), 6 new studio shots uploaded and reordered studio-first
      - Gin 90 Dining (gid://shopify/Product/11233904492886): 4 deleted (3 plain webps +
          drawing), 6 new studio shots uploaded and reordered studio-first
      - Mimosa 40: not touched — no local assets found
  upload_method: stagedUploadsCreate → GCS upload (multipart POST for Batch 2a,
    pre-signed PUT for Batch 2b) → productCreateMedia with resourceUrl
  reorder_method: productReorderMedia mutation (moves array with newPosition)
  alt_text_method: productUpdateMedia mutation (alt field)
  assets_source: C:\VeldoraHaven\EcoSmartFire\Product Images\ (pre-organized by range/model/type)
  images_skipped: packaging shots, spec/technical-drawing assets, Nova 850 install images >25MP,
    ESF_Ark_40_Teak_Outdoor_Elegance.jpg (24MP — safely skipped)
  pdp_verification: spot-checked via Shopify Admin GraphQL + accessibility tree; all 6
    verified products confirmed leading with correct studio shots
  next_action: Consider Daiquiri 70L and other Fire Table gallery upgrades; consider
    Pod 30/40 once local assets are available
- task_id: PDP-STORY-FEATURES-SWAP-001
  title: Swap PDP section order (dark story band vs. light features band) +
    fix Customisation-options font drift
  status: STAGED — awaiting manual publish by user (themePublish is blocked
    by the Shopify connector's safety policy, same as PERPLEXITY-INCIDENT-001)
  context: while checking this, discovered theme 206148993366 ("VeldoraHaven
    — pre-Perplexity revert") is now role MAIN (live) — the user must have
    published it manually since the last STATE.md update, which still said
    "awaiting manual publish." Corrected here. Full theme list as of
    2026-09-03: 206148993366 MAIN; everything else (205129482582,
    205414105430, 205583221078, 205638533462, 205649445206, 206158266710)
    UNPUBLISHED.
  what_changed: user felt the dark green "AN AUROOM PRODUCT / Outdoor Barrel
    Sauna" story band (vh-product-story, background var(--vh-forest-deep))
    looked wrong sitting directly under the gallery renders. Swapped its
    position with the light "Included as standard" features band
    (vh-product-features) in templates/product.json's section order — features
    now renders first (right after the buy box), story band second. This is
    the shared product template, so it affects every barrel-sauna PDP, not
    just Halo.
  font_fix_found_during_review: while previewing the swap, spotted the
    "Customisation options" checkbox grid (Roof shingles, PVC roof cover,
    etc.) rendering in browser-default styling (13.6px / weight 400 / pure
    black) instead of matching "Included as standard" above it (15.2px /
    weight 300 / var(--vh-stone)). Root cause: theme drift — the LIVE
    sections/vh-product-features.liquid still had an older .vh-addon-card
    CSS rule (font-size: 0.85rem, no font-weight override, color:
    var(--color-foreground)), while the local git clone
    (theme/sections/vh-product-features.liquid) already had the corrected
    rule matching .vh-feature exactly. Pushed the git version's full file
    to the preview theme, which fixed the font AND aligned the checkbox
    grid's column rhythm/hairline dividers/check-mark styling to match the
    inclusions list above it (comment in the file already documented this
    as the intent — the live version had just drifted from it).
  where_staged: new theme "VeldoraHaven — preview: PDP section order swap"
    (206166131030), created via themeDuplicate from the live theme
    (206148993366) specifically so this work would NOT touch production —
    user had asked for "a preview." Two files pushed there via
    themeFilesUpsert: templates/product.json (section order) and
    sections/vh-product-features.liquid (font fix, full file replace).
  verified: computed styles checked live on the preview URL before/after —
    .vh-addon-card text went from 13.6px/400/rgb(0,0,0) to
    15.2px/300/rgb(42,42,34), matching .vh-feature exactly. Section order
    visually confirmed via screenshot (features band now directly under
    gallery, story band second).
  preview_url: https://www.veldorahaven.com/products/auroom-halo-barrel-sauna?preview_theme_id=206166131030
  next_action: user publishes theme 206166131030 manually (Admin → Online
    Store → Themes → "VeldoraHaven — preview: PDP section order swap" →
    Actions → Publish). Not done yet as of this update. NOTE: local git
    clone (theme/templates/product.json) already has the section-order
    change committed to the working tree but not yet committed to git or
    pushed to GitHub — do that once the user confirms the preview looks
    right, to keep git/live in sync (this project has a recurring
    git/live drift problem, see PERPLEXITY-INCIDENT-001 and the font-drift
    root cause just above).
```

```yaml
- task_id: HALO-FONT-PRICE-CHECK-001
  title: Font/size check on SHIPPING-PAGE-FIX-001 edits + full Halo price audit
  status: DONE
  font_check: inspected computed styles (font-family/size/weight/line-height)
    on the live /pages/shipping-delivery page — the two rewritten "Delivery
    cost" paragraphs are pixel-identical to every untouched paragraph on the
    page (Inter 17px/400 body, Cormorant Garamond 38.4px/300 headings). No
    drift. Separately discovered the "Why buy from VeldoraHaven" footer edits
    made to Nora/Halo/Luma/Sola descriptions (same session, prior task) are
    NOT rendered anywhere on the live PDP — no theme section pulls that
    chapter via vh-desc-chapter, so there was nothing to visually check there;
    the fix is correct in the underlying Shopify data but currently invisible
    on the storefront. Flag if that content should actually be surfaced.
  price_audit: recomputed all 28 live Halo variant prices against
    pricing/PRICING-ENGINE-HANDOFF.md's formula (base EXW + finish uplift +
    assembly + logistics reserve, target 52.5% GM). User's recalled
    "~€7,350" price matches Halo Cosy 150 NW DIY = €7,300 live, which is
    correct (GM 63.4%, within the documented 56-66% Natural-price range) —
    not an error.
  found_and_fixed: Halo Extra Comfy / Brushed Black / DIY kit was live at
    €11,600 but the approved Group A mutation table
    (PRICING-ENGINE-HANDOFF.md) specifies €11,500 (GM exactly 52.5%, the
    documented floor case). Corrected live price to €11,500 via
    productVariantsBulkUpdate (variant 55032453923158).
  commercial_decision: Halo Cosy 120 Pre-assembled (NW €8,700 / BB €9,000)
    was flagged as Group C BLOCKED (no verified Auroom assembly cost) but was
    already live and selling. User decided 2026-09-03 to keep both prices,
    assuming an assembly cost similar to the other small models (~€300,
    matching Cosy 150/Sola 140) rather than waiting on supplier confirmation.
    Updated PRICING-ENGINE-HANDOFF.md to record this as a commercial decision
    (GM 65.6% NW / 61.3% BB at the assumed cost) and moved Halo Cosy 120 out
    of the Group C blocked table — Nora 210 and Sola 250 Pre-assembled remain
    blocked/unpriced, not addressed this session.
```

```yaml
- task_id: SHIPPING-PAGE-FIX-001
  title: Fix contradictory freight/country claims on /pages/shipping-delivery
  status: DONE — published live via Admin API pageUpdate (Shopify Page, not theme code)
  what_was_wrong: user flagged "some information is not true" without specifying
    which lines. Investigation found two real contradictions, not assumptions:
    1) Freight: templates/product.json's text_lead_facts block ("Freight
       included") and every barrel-sauna's own "Why buy from VeldoraHaven"
       description footer ("The price you see is the price you pay... freight...
       included. Nothing added at checkout") both said freight is included in
       price — confirmed TRUE by pricing/PRICING-ENGINE-HANDOFF.md's Logistics
       reserve (EUR600 DIY / EUR850 pre-assembled) baked into landed cost. But
       the SAME product description's footer, two bullets above, also said
       "freight quoted per delivery address and confirmed before your order is
       placed" — a self-contradiction on one page, and it matched what the old
       shipping-delivery page said ("Freight is quoted per order... confirmed
       with you before your order is dispatched"). The shipping page was the
       wrong one; rewrote its "Delivery cost" section to match the included-
       freight reality.
    2) Countries: shipping page implied broad/vague reach ("Nordic region...
       further into Europe... worldwide by arrangement"); one PDP footer said
       "Delivered across the EU and EEA". STATE.md's prior known-good note
       (barrel saunas ship from Estonia/Latvia to Denmark, Germany, Netherlands,
       France only) turned out to be the STALE fact, not the shipping page —
       user confirmed 2026-09-03 that EU-wide delivery is live today, quoted
       case-by-case, with DK/DE/NL/FR as the fastest/cheapest core routes.
       Correcting the prior "confirmed barrel-sauna delivery countries" claim
       in this file accordingly — treat DK/DE/NL/FR as core/included routes,
       not a hard ship-to limit.
  new_page_copy: "Delivery cost" section now reads: freight to Denmark,
    Germany, Netherlands, France is included in the product-page price with
    nothing added at checkout; other EU countries are delivered on request
    with freight quoted individually and confirmed before dispatch. Rest of
    the page (freight mechanics, kerbside, placement quotes, lead times,
    booking, damage reporting, worldwide-by-arrangement outside EU) untouched
    — none of it contradicted anything.
  followup_done_same_session: fixed the matching self-contradiction inside
    each barrel-sauna product's own "Why buy from VeldoraHaven" description
    footer (live per-product via Admin API productUpdate, not theme code) —
    Nora (11159107862870), Halo (11190367125846), Luma (11191458234710),
    Sola (11198241407318), all ACTIVE. The "Delivered across the EU and EEA —
    freight quoted per delivery address and confirmed before your order is
    placed" bullet was replaced with "Delivered across the EU — freight
    included to Denmark, Germany, the Netherlands and France; other EU
    destinations delivered on request, quoted before your order is placed" —
    now consistent with the neighboring "price you see is the price you
    pay... nothing added at checkout" bullet two lines below, and with the
    shipping page. Kaia (11199563071830, DRAFT) has a different, shorter
    description with no "Why buy" footer — not touched, nothing to fix there.
  not_done: did not re-verify whether "Freight included" in
    templates/product.json's text_lead_facts applies sensibly to non-sauna
    products (fire features) sharing the same product.json template — same
    template, no per-category override found.
    scope_check: also flagged Rosnhults (ROSHULTS-001, still WAITING/not
    ACTIVE) has a different, unresolved freight model (FCA Jonkoping /
    DAP-to-distributor) — this page's claims don't cover it yet since it
    isn't live; revisit shipping-delivery copy once Röshults launches.
```

```yaml
- task_id: PERPLEXITY-INCIDENT-001
  title: Clean up after an unsupervised Perplexity/Comet agent session on the live store
  status: MOSTLY COMPLETE — one manual step outstanding (theme publish)
  what_happened: an autonomous Perplexity "Comet" browser agent was given access to
    Shopify Admin outside this project's governance and made live edits on 2026-09-02:
    published 4 blog articles (SEO buying guides), rewrote the consultation page,
    rewrote/added copy on every collection description, edited ~20 product
    descriptions (added a "Why buy from VeldoraHaven" footer block incl. a
    "VAT... included" claim that contradicts the site's actual excl-VAT checkout —
    this specific claim pre-existed in the original template, not introduced by
    Perplexity), and drifted 21 theme files live vs git (never committed anywhere).
    Session ran out of credits mid-task; user asked for full cleanup.
  containment: user instructed to close the browser session / rotate Shopify admin
    password if Comet still had access. Not verified from this session — confirm
    with user if unsure.
  theme_file_revert: all 21 drifted files (config/settings_data.json,
    footer-group.json, main-collection-list.liquid, vh-brand-story.liquid,
    vh-cart-trust.liquid, vh-footer-partners.liquid, vh-heater-picker.liquid,
    vh-product-addons/-arrival/-materials/-spec/-story.liquid,
    breadcrumb-json-ld.liquid, meta-tags.liquid, vh-desc-chapter/-heater-map/
    -media-pick.liquid, templates/cart/collection/index/product.json) restored to
    last-known-good git content (main HEAD ed05b59 at the time). Verified via
    per-file checksum diff against git blobs, not assumed.
  pages_unpublished: /pages/trade and /pages/consultation unpublished per explicit
    user instruction ("perplexity crap... has to be taken away"). Both had
    coherent, non-embarrassing content on inspection, but user wanted them gone.
  link_cleanup_after_unpublish: every /pages/trade and /pages/consultation
    reference site-wide was found and repointed to /pages/contact-us (the one
    real, populated contact page — NOT /pages/contact, which is empty, see
    known_issue below): 20 product descriptions, 8 collection descriptions, the
    FAQ page, 5 blog articles, and the site-wide footer "Book a Consultation" nav
    link (footer-about menu). Verified via full product/collection/page/article/
    menu sweep, not spot-checked.
  blog_articles_unpublished: the 4 Perplexity-authored guides unpublished
    (Outdoor Sauna Buying Guide, Outdoor Kitchen Planning, Bioethanol Fire Pits
    Explained; a 4th Danish guide was already draft/unpublished).
  new_bugs_found_and_fixed_during_cleanup:
    - vh-product-addons.liquid: add-on checkbox cards rendered with invisible
      borders (rgba(var(--color-foreground-rgb), 0.14) — var() resolves to a
      space-separated triplet, making the rgba() invalid, so the whole border
      computed to nothing) and full-bleed/uncontained layout (.page-width is a
      dead Dawn-era class Horizon doesn't define). Also fixed: keyboard-
      unreachable checkboxes (display:none removed them from tab order), and an
      order-accuracy bug where bfcache restore could desync the visible
      checked-state from the actual submitted value. Root-caused against live
      rendered DOM/CSS, not just code review — see commit 55dd41c (theme repo).
    - Site-wide faux-bold RTE emphasis: assets/veldora-custom.css's @import
      loads Inter at weights 300/400/500 only, but sections/vh-collection-guide.
      liquid (and the site-wide <strong> default) requested/resolved to 600/700
      — a face Inter doesn't ship, so browsers synthetically bolded (smeared) it.
      This was the actual cause of the "fat/messy" text the user flagged, not a
      simple weight preference. Fixed: capped RTE <strong>/<b> at real Inter
      Medium (500) + an ink-density shift (--vh-stone-mid → --vh-stone) instead
      of weight, with font-synthesis-weight:none as a durable guard against
      future 600/700 creeping back in. Footer/hero opted out (dark-scheme
      contrast trap, see code comment). Commit 9076704 (theme repo).
    - Sola product PDP "Choosing your finish" card showed the wrong photo for
      Brushed Black (a garden lifestyle shot, not the product photo) because
      vh-media-pick's finish-card alt-text scoring matched a lifestyle image
      whose alt text happened to contain both "Brushed" and "Black" and which
      sits earlier in the gallery than the real product shot. Fixed by editing
      that image's alt text via Admin API (MediaImage 64689457103190 and
      64689457135958) to remove the ambiguous phrase — a data fix, not a code
      fix. Worth checking other products for the same alt-text collision risk
      if it recurs (Halo/Luma/Nora all use the same finish-card mechanism).
    - Footer showed a redundant "Auroom Wellness" partner blurb (vh-footer-
      partners.liquid via footer-group.json's vh_partners_fP3kx2 block) that
      duplicated the same content already on /pages/partners. Removed the
      section from footer-group.json per user request — Partners page
      untouched. Commit b4a63fb (theme repo).
  git_state: all fixes merged to `main` and pushed to GitHub
    (github.com/adamant1337/VeldoraHaven1). Commits: ed05b59 (baseline) →
    55dd41c (addons fix) → 9076704 (RTE fix) → b4a63fb (footer partners
    removal) → 9a5d3e0 (homepage kitchen card image + collections-index
    hide list, see pre_publish_review_round below).
  pre_publish_review_round: user did a visual pass on the staged theme
    before publishing and caught 3 more things (2026-09-03), all fixed:
    - /pages/privacy-policy (Shopify Page, NOT theme code — edited live via
      Admin API pageUpdate, takes effect immediately regardless of theme
      publish state): "Shopify Inc. — our e-commerce platform provider" →
      "our platform provider" (dropped "e-commerce" per user instruction).
    - Homepage "02 — Outdoor Kitchens" category card (vh-category-cards.
      liquid) was showing a Röshults Wood Oven product photo
      (Roshults-Outdoor-Kitchen_10412-02-LowRes.webp, from
      Röshults/WoodOven/) under the Outdoor Kitchens label — user caught
      this as wrong (oven ≠ kitchen). Fixed by reusing the Kitchen Island
      lifestyle shot already correctly used on that collection's own hero
      (vh-collection-hero.liquid's outdoor-kitchens case):
      Roshults-Outdoor-Kitchen_10261-02-LowRes.webp (lakeside deck scene,
      from Röshults/Kitchen Island/) — already on the CDN, no new upload
      needed. Commit 9a5d3e0.
    - /collections index (main-collection-list.liquid) was listing every
      collection via `collections | reject: 'handle', 'infrared-saunas'`.
      User: not cleared to sell Cold Plunge, Complete Bundles, Outdoor
      Furniture & Pergolas, or Cabin Saunas yet — added 4 more `reject`
      filters (handles: cold-plunge-ice-baths, complete-bundles,
      outdoor-furniture-pergolas, cabin-saunas) to the same chain. Commit
      9a5d3e0. NOTE: this only hides them from the /collections INDEX
      grid — the collection pages themselves (e.g. /collections/
      cold-plunge-ice-baths) are still reachable directly/via search, and
      outdoor-kitchens + fire-features still carry `vhc_coming_soon: true`
      in vh-collection-hero.liquid despite being left visible in the index
      per user's explicit list — not touched, flagged here in case that's
      an oversight rather than intentional.
    - user asked to go further: fully unlist those same 4 collections
      (not just hide from the index grid). Attempted via Admin API
      publishableUnpublish (Online Store publication
      gid://shopify/Publication/343904747862) on all 4 collection GIDs
      (Cold Plunge 700504342870, Complete Bundles 700504473942, Outdoor
      Furniture & Pergolas 700504441174, Cabin Saunas 704643957078) —
      BLOCKED by the Shopify connector's own safety policy (category:
      destructive, "prevent accidental storefront catalog removal"), not
      by our project's rules. User chose to do it manually rather than
      have a theme-side 404-guard workaround built.
      next_action: user unchecks "Online Store" under Sales channels and
      apps for each of the 4 collections above (Admin → Products →
      Collections → [collection] → Sales channels and apps → Save). Not
      done yet as of this update.
  soft_unlist_workaround_shipped: since the real unpublish is blocked and
    the user couldn't find the manual toggle either, built a theme-side
    stand-in instead (commit bc9ba47, pushed to theme 206148993366):
    vh-collection-hero.liquid, main-collection.liquid and
    vh-collection-guide.liquid all check the same 4-handle list
    (cold-plunge-ice-baths, complete-bundles, outdoor-furniture-pergolas,
    cabin-saunas) and render nothing / a "This page no longer exists"
    panel with <meta name="robots" content="noindex, nofollow"> instead of
    real content. NOT a true 404 (URL still returns 200) — a real
    unpublish in Admin is still the correct long-term fix; this just
    closes the gap until that happens.
    gotcha_hit_twice: `{% assign x = y contains z %}` is invalid Liquid —
    `contains` only works inside `{% if %}`/`{% unless %}` conditions, not
    as an assign expression. Also `{% javascript %}` cannot be nested
    inside a `{% unless %}` block. Both caused themeFilesUpsert failures
    before landing on the final structure — if extending this pattern,
    keep the handle-list check inline in `{% if %}`/`{% unless %}`, never
    pre-computed into a boolean via assign.
  pdp_duplication_pass_2026-09-03: user did a second visual pass, this
    time on a barrel-sauna PDP, and caught the same "written twice"
    pattern in two more places (commit bc9ba47, pushed to theme
    206148993366):
    - "Included in the price" (Freight/VAT/factory oiling) existed in TWO
      places: templates/product.json's text_lead_facts block (a static
      text block that is the LAST block in the buy column, right after
      buy_buttons_eYQEYi — i.e. literally under the payment options) and
      vh-product-addons.liquid's badge row (a separate full-width section
      below the buy column). User: keep the one under the payment options,
      remove the other. Deleted the badge row + its CSS from
      vh-product-addons.liquid.
    - vh-product-features.liquid's "Available options" tier duplicated
      vh-product-addons.liquid's "Add to your order" checkbox grid
      (same 6-7 option names, just grouped differently) — but the
      features-tier version was a static list with no functionality,
      while addons' version is the real interactive selector that posts
      properties[Add-ons] to cart. Removed the "Available options" tier
      from vh-product-features.liquid entirely (code now only renders
      "Included as standard"); also dropped the now-unused
      options_heading schema setting and the dead .vh-feature-grid--opt
      CSS.
    - "Remove the boxes... make it look good": vh-product-addons.liquid's
      add-on checkbox cards and "We can also arrange" service cards had
      full 1px bordered boxes (border-radius: 2px). Restyled both to
      hairline rows (border-bottom / border-top only, no radius),
      matching vh-product-features.liquid's existing unboxed list style
      elsewhere on the same PDP — checkbox interactivity/functionality
      unchanged, purely a style change.
    - Also fixed while in this file: two "Contact us for pricing" links
      in vh-product-addons.liquid pointed to /pages/contact (the known
      empty page) — repointed to /pages/contact-us, matching the
      site-wide repoint already done for the Perplexity cleanup.
    not_done: the empty /pages/contact page itself is still not fixed —
    only individual links to it keep getting repointed as they're found.
    A full site-wide link sweep for any remaining /pages/contact
    references (not /pages/contact-us) has not been re-run since the
    original Perplexity cleanup sweep; worth doing once, properly, rather
    than fixing them one at a time as they surface.
  duplication_pattern_worth_generalizing: three separate duplicate-content
    bugs found and fixed in one session (collections-index vs unlisted
    handles was a visibility bug, not this pattern, but the PDP ones
    were) all had the same shape: the barrel-sauna PDP's ~10 sections
    each independently parse product.description into chapters via
    snippets/vh-desc-chapter.liquid, so the same authored chapter
    (Included as standard / Available options / delivery facts) can
    easily end up rendered by two sections that don't know about each
    other. vh-product-spec.liquid's show_included setting was already a
    precedent for solving this via an explicit off-switch; the fixes this
    session instead just deleted the losing side outright. If more
    duplicates turn up, check every vh-product-*.liquid section's
    `render 'vh-desc-chapter'` calls against each other before assuming
    a fix is needed in only one place.
    - Liquid syntax gotcha hit and fixed during this: `{% liquid %}` block
      tags are one-statement-per-line — a `| reject:` filter chain broken
      across multiple lines inside `{% liquid %}` throws "Unknown tag" on
      the continuation line. Chain stayed single-line.
  shopify_deploy_state: **NOT LIVE YET.** All revert + fix files (including
    the pre_publish_review_round fixes above) pushed via Admin API
    themeFilesUpsert to unpublished theme 206148993366
    ("VeldoraHaven — pre-Perplexity revert"). The Claude Shopify connector
    blocks writes AND publish actions on the live/MAIN theme (205638533462) as
    a safety guard, so this last step needs a human:
    Shopify Admin → Online Store → Themes → "VeldoraHaven — pre-Perplexity
    revert" → Actions → Publish. Old live theme becomes unpublished (one-click
    rollback available if anything looks wrong post-publish).
  known_issue_not_fixed: /pages/contact (handle "contact", distinct from
    /pages/contact-us) has an EMPTY body. Several product/collection links
    ("Ask a question about this product") point there and currently land on a
    blank page. Not touched this session — flagged for a follow-up.
  draft_pending_user_review: C:\VeldoraHaven\cache\collection-copy-rewrite.md —
    a debold/rewrite pass on 6 collection descriptions (saunas, barrel-saunas,
    fire-features, sauna-accessories, infrared-saunas, outdoor-baths-hot-tubs),
    drafted by the orchestrator against the CURRENT (Perplexity-era) copy in
    C:\VeldoraHaven\cache\current-collection-copy.md. NOT pushed to Shopify —
    needs user sign-off, and the file itself flags two unresolved factual
    disagreements between the brand brief and live copy (Halo/Luma sizing,
    Auroom's country of manufacture) plus a pre-existing contradiction in
    vh-collection-guide.liquid's hardcoded comparison table.
  also_flagged_not_actioned: two separate "Outdoor Kitchens" collections exist
    (handles outdoor-kitchens and outdoor-kitchens-1) with different
    descriptions — likely a duplicate from earlier work, not part of this
    incident. Not investigated or merged.
  next_action: (1) user publishes theme 206148993366 to go live with all fixes;
    (2) verify the add-ons card, RTE emphasis and Sola finish-card fixes render
    correctly on the live site post-publish; (3) user reviews and approves (or
    edits) collection-copy-rewrite.md before it's pushed; (4) decide what to do
    about the empty /pages/contact page; (5) confirm Perplexity/Comet no longer
    has store access if that wasn't independently verified.
  porch_table_fix_2026-09-03: fixed a pre-existing (not Perplexity-caused) bug
    flagged by the collection-copy-rewrite draft: vh-collection-guide.liquid's
    hardcoded barrel-sauna comparison table listed both Luma AND Nora as having
    a porch. Confirmed against growth/content/blog-halo-vs-luma.md (dedicated
    "The Luma — With a Porch" section, explicit Halo/Luma comparison table) that
    only Luma has one — Nora's distinguishing feature is its square
    cross-section, not a porch. Fixed the "Porch" row (Nora cell Yes -> —).
    Committed to theme repo main (08e20bd), pushed to GitHub, and pushed
    directly to unpublished theme 206148993366 via themeFilesUpsert (0
    userErrors) so it's included in the pending manual publish.
```

## Active tasks (pre-existing)

```yaml
- task_id: AI-ARCH-001
  title: Establish agent system + source-of-truth scaffolding
  status: complete
- task_id: THEME-INT-001
  title: Confirm + clone theme, read-only integration audit, extract real tokens
  status: complete
  notes: theme at C:\VeldoraHaven\theme (HEAD 15eba70, main)
- task_id: AUDIT-001
  title: Master store audit (live + local), baseline scores, roadmap
  status: complete
  baseline_score: 70/100
- task_id: R0
  title: Reconcile local <-> live + set up dev workflow
  status: complete (CLI pull pending user auth)
  branch: fix/reconcile-local-live
  finding: source of truth = LIVE 205129482582 + spec.* metafields; local/GitHub stale (Aug 2)
  decision: v28 (205283819862) = working draft; live (205129482582) = reference
  captured: real design tokens + custom-source knowledge via Admin API
  outputs: shopify/LIVE-LOCAL-RECONCILIATION.md, shopify/THEME-DEV-WORKFLOW.md, theme/shopify.theme.toml
  pull: COMPLETE 2026-08-22 — v28 verified (byte-match) + committed as baseline on fix/reconcile-local-live
  next_action: R0 complete.
- task_id: R1
  title: Typography audit (roadmap P0)
  status: complete — NO CHANGE REQUIRED. Custom-CSS layer already authoritative
    (Cormorant/Inter), correct across all surfaces. See ADR (typography).
- task_id: R2
  title: Hero + fonts perf (roadmap P0)
  status: complete. Hero PNG→CDN-resized WebP (~90% smaller), preload/preconnect
    added. Branch perf/r2-lcp-optimization (theme repo). Merged into
    integration/dev-preview.
- task_id: R5
  title: JSON-LD structured data (roadmap P1)
  status: partial-complete. Product + Organization JSON-LD already existed via
    Horizon (`structured_data` filter, header.liquid) — kept as-is. Added
    BreadcrumbList (new, `snippets/breadcrumb-json-ld.liquid`). FAQPage
    explicitly skipped — no real FAQ content exists anywhere on the site;
    do not add until real content exists.
- task_id: R7
  title: Cart AOV (roadmap P2)
  status: partial-complete, scope-narrowed. No real accessory/care/install
    products exist in Shopify (checked — Sauna Accessories collection empty,
    zero matches store-wide) — upsell half is blocked on missing product data,
    a merchandising decision, not implementable without inventing products.
    Implemented the trust half only: `sections/vh-cart-trust.liquid` reassurance
    strip (secure checkout / delivery process / contact), added to
    templates/cart.json.
- task_id: BARREL-SAUNA-FAMILY
  title: Complete + polish the Barrel Sauna product family (Halo/Luma/Nora/Sola)
  status: complete. Outside strict roadmap numbering but foundational — this
    IS the roadmap's "first real implementation phase." Covers Nora/Sola
    content authored from verified Auroom sheets, all 4 products built/fixed
    in Shopify (variants, spec.* metafields, images, publication, inventory
    tracking), variant-image mapping for all 4, PDP buy-box trust fix,
    Barrel Saunas collection buying-guide + comparison table, homepage
    category-card typography pass (numbered index + italic accent + gold
    rule), collections-index entrance motion, sticky-add-to-cart disabled,
    spec section converted to a dropdown, repeated price near buy buttons,
    variant-picker label font fixed, Infrared Saunas removed from nav +
    collections index. All on theme-repo branch `integration/dev-preview`,
    pushed to Shopify dev theme v28 (unpublished). See memory
    `veldorahaven-nora-sola-products.md`.
  next_action: R3 (Reviews / social proof) is next in roadmap priority order —
    R4 (premium polish) and R6 (contrast AA) still pending in P1 too.
    R8-R13 (P2/P3) not started except R7 above.
- task_id: JUDGEME-EMBED-001
  title: Fix Judge.me app-embed parity gap (dev theme was missing it)
  status: partial-complete. Judge.me app-embed was live on MAIN
    (205129482582, disabled:false) but absent from dev theme v28
    (205283819862) — reviews would never have rendered when v28 ships.
    Added matching block to theme/config/settings_data.json, committed
    on integration/dev-preview, and pushed directly to the v28 Shopify
    theme via themeFilesUpsert (CLI still unauthenticated). No manual
    judgeme_widgets.liquid snippet exists on either theme — Judge.me
    is running purely on its own app-embed CSS-selector injection.
  next_action: Widget placement rules, star styling, and review-request
    email settings live inside Judge.me's own app dashboard (Shopify
    Admin > Apps > Judge.me) — needs the user's live login, not
    reachable from here. This is also the real prerequisite for R3.
  follow_up: user chose manual widget placement over dashboard config.
    Added theme's native `review` star block (reads
    product.metafields.reviews.rating/rating_count) to PDP (under
    title, templates/product.json group_icgrde) and to collection
    product cards (templates/collection.json, between title and
    price). Pushed to v28 + committed (ca1ebb5). Verified live on
    preview_theme_id=205283819862: PDP (auroom-luma-barrel-sauna) and
    /collections/barrel-saunas both render clean, no Liquid/JSON
    errors. Renders nothing yet — confirmed zero products store-wide
    have reviews.rating metafield data, so no reviews have synced/been
    collected. Will "just work" the moment Judge.me populates that
    metafield; no further code needed for the star summary. The full
    review-list/write-a-review widget (actual review text, submission
    form) is Judge.me's own proprietary widget markup, not covered by
    this native block — still needs their dashboard/install flow.
- task_id: R4
  title: Premium polish pass (hierarchy, spacing, photography treatment)
  status: complete. Ran veldorahaven-brand-director (audit) then
    veldorahaven-visual-designer (implementation) per the roadmap's
    assigned agents. Headline finding: much of the intended premium
    treatment was already written but never rendered, because
    veldora-custom.css targeted Dawn-era class names Horizon doesn't
    emit (dead CSS), plus a real hierarchy bug (PDP title 32px smaller
    than its own description's rendered <h2>s at 48px) and a duplicate
    price both flattened to 13px. Fixed in two groups, both verified
    live on preview_theme_id=205283819862 (not just theme-check):
    Group A — PDP title h3->h2; RTE headings in the buy column capped;
    retargeted dead .card__media/.card__title/.product__vendor
    selectors to Horizon's actual product-card/text-block markup;
    card_hover_effect lift->none; removed duplicate PDP price block;
    PDP gallery aspect_ratio adapt/contain->4/3 cover (added 4:3 as a
    real schema option on core blocks/_product-media-gallery.liquid).
    Group B — new --vh-container/-read/-editorial, --vh-gutter,
    --vh-section-y, --vh-h2, --vh-eyebrow-* tokens replacing 5 hardcoded
    container widths / 4 gutters / 5 h2 sizes / 4 eyebrow specs across
    6 vh-* sections; hero/story/category CSS background-images given
    &width= params (were shipping full-res masters to phones), hero
    preload in theme.liquid split to match per-breakpoint; collection +
    PDP-recommendation card image_ratio portrait->landscape; homepage
    hero's two near-identical ghost buttons collapsed to one primary +
    a text link.
  bug_caught_in_verification: the implementing agent's vendor-mark and
    hero-secondary-link CSS used [class*='text-block--vendor_block'] /
    [class*='text-block--cta2'], assuming Horizon emits
    `text-block--{block_id}`. Live DOM check found the real pattern is
    `text-block--{random-prefix}__{block_id}` — those selectors matched
    nothing, so 2 of 9 punch-list items were silently inert despite
    being reported as done. Caught only because every item was checked
    against the live rendered DOM (computed styles / class names), not
    just theme-check + code review. Fixed (commit e19b9ed) and
    reverified live. Lesson: for any future Liquid CSS that targets a
    Horizon-generated block-id class, verify the actual rendered class
    string on the live preview before trusting the selector.
  pushed: all files committed on integration/dev-preview (7ce8da4,
    e19b9ed) and pushed to Shopify dev theme v28 via themeFilesUpsert
    (CLI still unauthenticated).
  not_done: item 4's content-ops half (Nora's source images are only
    720px vs 1800px+ elsewhere) — flagged, not fixed, not a theme
    change. vh-collection-hero.liquid's background-image (`vhc_img`)
    still has no &width= param, same class of issue as the R4 fix in
    vh-category-cards — worth a follow-up, not done here.
  next_action: R6 (contrast AA) is the remaining P1 item. R3 (reviews)
    still blocked on Judge.me's own dashboard config, see
    JUDGEME-EMBED-001 above.
- task_id: HEATER-BUNDLE-001
  title: Add HUUM/Harvia electric + wood-burning heater bundle pricing (Barrel Sauna family)
  status: complete. PDP heater picker section live on dev theme v28 (205283819862).
    Commit e40baf9 on integration/dev-preview.
  source: AuroomWellness/Price list Q4 2026/Auroom Barrel Saunas price list Q4 2026.pdf
    (pages 7-8, heater price tables).
  outputs:
    - VeldoraHaven_Pricing_Model.xlsx — 4th sheet "Heater Bundle Pricing" with EXW
      catalog, retail add-on (cost-plus 35%, rounded EUR10), and Complete Bundle totals
      in EU EUR ex-VAT and DK DKK incl.VAT.
    - sections/vh-heater-picker.liquid — new PDP section. Renders below the buy box on
      barrel sauna PDPs only (products with a "Size" option). Shows HUUM + Harvia
      electric heaters for all models. Wood-burning shown only where space allows
      (excluded on Halo Cosy 120, Halo Cosy 150, Sola 140). Every heater bundle includes
      sauna stones, digital control panel, and safety railing. Wood-burning options note
      optional EUR180 installation service. Sola 250 renders a "contact us" fallback
      (no heater confirmed with Auroom yet). Cart add POSTs sauna variant + heater
      variant as two separate line items via /cart/add.js.
    - templates/product.json — vh_heater_picker section added between main and
      vh_product_spec.
  data_gaps_open:
    - SOLA 250: no heater option in Q4 2026 price list — do NOT sell as bundle until
      Auroom/Silga confirms. Section renders contact-us fallback.
    - HALO Cosy 180 wood-burning: ambiguous (page-2 checkbox = dash/unavailable,
      page-7 price table lists real prices). Went with price-table; flagged in xlsx
      Notes column. Verify with Auroom.
  next_action: Verify on live preview (preview_theme_id=205283819862) — confirm heater
    picker renders on a barrel sauna PDP, variant change updates heater options, bundle
    price shows correctly, CTA posts both items to cart. Then push integration/dev-preview
    to main when ready to publish.
- task_id: R6
  title: Contrast to WCAG AA (footer/vendor/nav)
  status: complete. Ran veldorahaven-accessibility-specialist per the
    roadmap's assigned agent. Computed real alpha-blended WCAG contrast
    ratios (not guesses) for every footer/vendor/nav text-background
    pair; orchestrator hand-verified 2 of the calculations by hand
    (matched exactly). Fixed: footer body/copyright text 0.35/0.18 alpha
    (~2.96:1 / ~1.69:1, both fail) -> 0.55; newsletter-button border
    0.18 (~1.69:1, fail) -> 0.4; vendor mark's plain --vh-gold on
    scheme-1's actual #f7f7f5 background (~2.09:1, fail) -> new
    --vh-gold-ink (#83673B) token (~4.93:1). Nav already passed
    (~4.62-4.94:1 across menu items/icons/hover) — left untouched.
  bug_caught_in_verification: same class of bug as R4's vendor-mark
    fix (see that task's bug_caught_in_verification) — checked live
    and found EVERY `.footer`-scoped selector matched zero elements.
    `document.querySelectorAll('.footer').length === 0` on the live
    preview; Horizon's real footer has no element with class "footer"
    anywhere. So the agent's alpha-tuning (correct math, wrong target)
    never actually applied: the footer heading
    (`<summary class="menu__heading h3">`) was rendering pure black
    (rgb(0,0,0)) and the address text was inheriting the unrelated
    global `.rte` color (--vh-stone-mid #4A4A40) — both against the
    real #152e25 (native color-scheme-4) background, ~1.3-1.6:1, worse
    than what was being fixed. Retargeted to real elements/classes
    (bare `<footer>`, `.menu__heading`, `.email-signup__button`) and
    re-verified the alpha math against the REAL #152e25 background
    (0.5 only reached ~4.33:1 there, still failing 4.5:1 — bumped to
    0.55, ~4.92:1). Old `.footer`-prefixed selectors kept alongside as
    a harmless no-op hedge. Reverified live post-fix: heading/link/
    address all render rgba(245,240,232,0.55) as intended. Nav's
    `.header__menu-item` class also doesn't exist, but that rule's
    other selector branch (`.header a:not(.header__logo)`) still
    caught every link via the real `.header` ancestor — no fix needed
    there, confirmed live.
  lesson: this is the SECOND time in this session a sub-agent shipped
    CSS whose selectors didn't match Horizon's real generated markup
    (class names differ from what both agents assumed/guessed). Any
    future Liquid/CSS work on this theme MUST verify selectors against
    actual rendered DOM classes (querySelectorAll counts, computed
    styles) before trusting them — code-level review and even correct
    math are not sufficient on their own.
  pushed: committed on integration/dev-preview (cb2a703, 780a8e5),
    pushed to Shopify dev theme v28 via themeFilesUpsert.
  next_action: R6 complete. R3 (reviews) still blocked on Judge.me's
    dashboard, see JUDGEME-EMBED-001. No P1 roadmap items remain open.
    P2/P3 (R7 partial, R8-R13 not started) are next if continuing.
- task_id: PDP-SHOWROOM-001
  title: Product page showroom layer (Barrel Sauna PDPs)
  status: RESUMED 2026-08-24. Phase C committed, CSS reconciled; theme push running
    to unpublished copy 205414105430 (themeFilesUpsert blocks MAIN 205283819862).
  branch: integration/dev-preview (theme repo). Rollback point = 6259774.
  committed:
    - 17ae661 "feat: PDP showroom layer -- gallery motion, editorial sections,
      section rhythm, buy hierarchy" (2026 insertions across 13 files)
    - 570eb39 "fix: split chained variant.options assignment in vh-media-pick"
  uncommitted_working_tree: YES — the orchestrator's Phase C integration is on
    disk but NOT committed. Do not discard. Files:
    - templates/product.json (registers the 5 new sections + all gallery diffs)
    - assets/veldora-reveal.js (VT exclusion guard + per-item observation)
    - assets/veldora-pdp.css (lead-block selector reconciliation)
    - assets/veldora-custom.css (2 dead-selector removals)
    - blocks/vh-product-lead.liquid (NEW, untracked)
    - sections/vh-product-story.liquid + snippets/vh-size-cards.liquid — NOT the
      orchestrator's edits; an implementer refined these after its own commit.
      Content: `| escape` hardening on the badge logo src, an aria-labelledby fix
      (heading now always renders so the reference always resolves), and its lead
      CSS comment/selectors retargeted from the abandoned custom-liquid approach
      to blocks/vh-product-lead.liquid. Legitimate — keep.
  RESUME_CHECK_FIRST: lead-block CSS now exists in TWO places — the orchestrator's
    `.vh-lead p` addition in assets/veldora-pdp.css AND a block of lead rules
    emitted inside sections/vh-product-story.liquid. Both were written against the
    same final markup so they should agree, but they have never been rendered
    together. Reconcile/deduplicate before or immediately after the first push.
  approach: agents used = product-experience + visual-designer (parallel design),
    then component-builder + liquid-engineer (parallel implementation, Opus,
    disjoint file ownership). shopify-architect deliberately SKIPPED — the
    architecture was already fixed by the vh-product-spec.liquid precedent.
  key_findings:
    - Root defect: the entire 4,400-5,800 char description rendered as ONE text
      block (text_aEtTtq) inside the narrow buy column. That is why the PDP did
      not read as a showroom.
    - All 4 barrel-sauna descriptions share an IDENTICAL 10-part structure, which
      is what makes one shared template possible with no new metafields. Parser
      centralised in snippets/vh-desc-chapter.liquid.
    - Admin API token in .env is EXPIRED ("Invalid API key or access token"), so
      no new metafields could be created and no images can be uploaded by script.
      The primary session's Shopify MCP could do this instead.
    - Correct way to fetch the draft theme for DOM verification:
      curl -sL -c cj.txt -b cj.txt "<url>?preview_theme_id=205283819862"
      WITHOUT the cookie jar Shopify silently serves the LIVE theme. This is the
      trap behind the R4/R6 dead-CSS incidents.
  decisions:
    - REJECTED the designed templates/product.barrel-sauna.json. Stayed on the
      shared templates/product.json: the objective mandates one template, and a
      new template only renders after a manual admin assignment that the expired
      Admin API token makes impossible — the preview would have shown no change.
      Consequence: every new section self-gates to nothing on non-sauna products.
    - Lead block built as a real theme block (blocks/vh-product-lead.liquid), NOT
      Horizon's custom-liquid block: Shopify's `liquid` setting type forbids
      {% render %}, which would have forced the parser to be inlined as an escaped
      string in JSON. _product-details accepts {"type": "@theme"} so this is legal.
    - Lead block has a MANDATORY fallback: when a description carries neither <h2>
      nor vh-brand-badge it prints the full description verbatim. Without this,
      removing text_aEtTtq would have silently stripped all copy from every
      non-sauna PDP (the heater products).
    - KEPT the review_pdp block (renders nothing without data; removing it would
      undo the explicit user decision in JUDGEME-EMBED-001).
  third_dead_selector_incident: found and fixed a THIRD instance of the R4/R6 bug
    class. veldora-custom.css shipped `.product-form__submit` (dark/gold CTA) and
    `.product__title, .product-form h1` (PDP title type) — verified 0 matches on
    the PDP, the collection page AND the homepage. Neither had ever rendered. Both
    removed with a comment; real hooks are `.add-to-cart-button` and
    `main[data-template^='product'] .product-details h1` in veldora-pdp.css.
  integration_conflict_caught: veldora-pdp.css styled the lead via
    `rte-formatter.rte:not(...)` ("lead by elimination"), assuming the lead stayed
    an rte text block. The lead is now `.vh-lead > p.vh-lead__p`, so that selector
    matched nothing. Reconciled by adding `.vh-lead p` alongside — the rte branch
    is retained because it still fires for the raw-description fallback case.
  validated_so_far: product.json parses; order/sections fully reconciled (no
    missing keys, no orphans); buy block_order correct; all gallery settings
    applied; anchor targets #vh-sizes / #vh-spec confirmed present in the sections;
    grid classes and .product-information__media confirmed against real v28 DOM.
  css_reconciliation_done_2026-08-24: vh-product-story.liquid lead-block <style>
    pruned — removed duplicate .vh-lead__p typography (veldora-pdp.css owns it),
    all .vh-lead__link rules (conflict with a[href^='#vh-'] canonical style), and
    ::after arrow pseudo-content (double-arrow bug). Commit 0be7851.
  theme_check_2026-08-24: 30 warnings, 0 errors (baseline 29, new OrphanedSnippet
    for vh-coming-soon.liquid is pre-existing and harmless).
  critic_review_2026-08-24: final-critic returned REQUEST CHANGES. P1 fixes applied
    in commit 64b286b and pushed to main:
    - vh-product-spec: section now self-gates (was rendering empty 130-210px band
      on heater PDPs); description-chapter fallbacks added for Not included / Base
      requirements / Delivery when spec.* metafields are blank
    - vh-desc-chapter: story head guarded on '<h2' so drafts without '<details>'
      can't bleed Assembly paragraphs into story index 2
    - vh-product-arrival: Assembly chapter fallback tries 'Assembly and installation'
      and 'Assembly and delivery' before giving up
    - layout/theme.liquid: veldora-pdp.css gated to product template only (45 KB
      off collection/homepage LCP path)
  status: COMPLETE — deployed to main (dfd15b9→64b286b). GitHub→Shopify auto-deploy
    will propagate to live theme 205283819862.
  open_p2_items:
    - veldorahaven-final-critic P2 #6: bundle CTA renders above lead paragraph
    - P2 #8: spec band heading hierarchy (summary needs an h2 wrapper)
    - P2 #9: dead scroll-margin-top: 96px in vh-product-sizes.liquid
    - P2 #10: .vh-mat__swatches materials div missing .rte class
    - P2 #11: para_count max: 3 invites ¶2 duplication with arrival section
    - P2 #7: C:\VeldoraHaven\cache\pdp-data-map.md stale
  next_action: P2 items are polish, not regressions. Address when convenient.
- task_id: KLAVIYO-FLOWS-001
  title: Build Klaviyo email flows (Welcome Series + Post-Purchase)
  status: IN PROGRESS
  copy_source: growth/email/KLAVIYO-FLOWS.md
  flows:
    welcome_series:
      trigger: Subscribe to list
      email_1: LIVE at klaviyo.com/flow/UTyBUX/edit — Brand intro (immediate)
      email_2: NOT YET ADDED — "Which barrel sauna is right for your garden?" (3-day delay)
        copy: growth/email/KLAVIYO-FLOWS.md → Flow 1 Email 2
    abandoned_cart:
      status: not started — 3 emails drafted in KLAVIYO-FLOWS.md
    post_purchase:
      trigger: Placed Order
      status: NOT YET BUILT — 2 emails drafted in KLAVIYO-FLOWS.md
        email_1: "Your VeldoraHaven order is confirmed" (immediate)
        email_2: "How's the sauna?" — care guide + review request (21 days after order)
  next_action: In Klaviyo — (1) add 3-day delay + Email 2 to UTyBUX Welcome flow;
    (2) create Post-Purchase flow with Placed Order trigger + 2 emails.
    Use copy verbatim from KLAVIYO-FLOWS.md.
- task_id: ROSHULTS-001
  title: Röshults outdoor furniture — products + collection + nav
  status: WAITING — partnership terms confirmed by Röshults (2026-09-01, Niklas
    Sahlqvist COO): 30% trade discount off retail price list, direct ordering via
    order@roshults.com, Online Builder tool access, freight quoted per project
    (DAP), marketing materials provided. Scope: Kitchen Island + Essentials lines,
    plus Wood Oven and Brazier Fire pit added at our request. Contract is NOT yet
    signed — this is the blocking step.
  reference_quotes: 4 example configs received 2026-08-19 (valid until
    ~2026-11-19, EXW Jönköping, EUR, 30% off): Essentials SS (#9436, €5,839.40),
    Kitchen Island 5M Bar (#9433, €24,734.50), Essentials Beluga Black (#9434,
    €6,119.40), Kitchen Island 4M Wall Anthracite (#9432, €21,035.00). Matching
    Röshults Builder spec sheets (renders + dimensions) in hand for each.
  products_created: 4 DRAFT products in Shopify (2026-09-01), added to Outdoor
    Kitchens collection, zero images, tagged pending-contract:
    - Essentials Set SS + Charcoal Grill — €8,342 (11217676534102)
    - Essentials Set Beluga Black + Gas Grill — €8,742 (11217676566870)
    - Kitchen Island 5M Bar SS — €35,335 (11217676599638)
    - Kitchen Island 4M Wall Anthracite — €30,050 (11217676632406)
    Pricing CONFIRMED (2026-09-01): parity with Röshults' own suggested retail
    (sum of quote unit prices pre-discount), no markup — formalized as
    pricing/ROSHULTS-PRICING-ENGINE.md (Röshults counterpart to the sauna
    pricing engine; different formula because the 30% trade discount off
    Röshults' own retail IS the dealer margin, not a base to mark up further).
    Use that file's SKU formula for any future Röshults product.
  freight: CONFIRMED separate-at-checkout via zone-based Shopify shipping
    profile (~3 zones by distance from Jönköping, Sweden) — BLOCKED pending
    user's call with Niklas (Röshults COO) for real DAP freight-by-zone
    figures. Do not build the shipping profile or invent zone rates before
    that call — shipping profiles are live storefront-wide immediately.
  contract_status: RESOLVED — no bespoke contract exists. Röshults confirmed
    (2026-09-01) "we don't use a unique agreement, but follow a general
    distribution settlement" (roshults.com/distribution-terms-conditions).
    Orders become binding on written/electronic order confirmation — no
    signature step. `pending-contract` tag on the 4 products is stale
    terminology; replaced by 2 real blockers below.
  blockers:
    - TERRITORY: standard terms limit distribution rights to "the
      distributor's registered country" — VeldoraHaven is DK-registered.
      UNCONFIRMED whether this restricts online sale to Danish customers
      only. Must confirm with Niklas before selling to non-DK customers.
    - E-COMMERCE CLAUSE: standard terms prohibit "resale through external
      retailers, e-commerce platforms, or third-party companies... without
      written consent." Likely aimed at marketplaces (Amazon etc.), not
      VeldoraHaven's own Shopify store, but get explicit written confirmation
      rather than assume.
    - SHIPPING MODEL: standard terms describe FCA Jönköping or DAP to the
      *distributor's* location (VeldoraHaven), not necessarily to the end
      customer — conflicts with Niklas's earlier email implying per-order
      drop-ship to the customer. Confirm which model applies alongside the
      freight-by-zone question.
  marketing_guidelines: read in full (Roshults-Marketing-Guidelines.pdf).
    Toolbox images pre-approved/use-as-is, never edited. Own photography:
    tidy, lavish, outdoor settings only. Logo: B/W, fixed clearance, never
    altered. Tone: confident, laid-back, "you"/"we", no exclamation marks.
    HARD CONSTRAINT: never present Röshults products with discount
    communication (no %, no crossed-out price, no "deal"/"campaign" wording) —
    confirms the parity-pricing decision in ROSHULTS-PRICING-ENGINE.md was
    correct.
  next_action: User to raise 3 items with Niklas in one conversation:
    freight-by-zone rates, territory scope (DK-only vs. EU-wide), and
    e-commerce/resale written consent. User also needs to create their own
    builder.roshults.com account (Röshults will then enable dealer pricing).
    Do NOT set any product ACTIVE, do NOT share on social (Niklas asked),
    until those 3 are resolved. After that: build the shipping profile with
    real numbers, add product photography once Ida sends assets, write PDP
    copy + SEO meta + collection SEO description per the marketing guidelines
    above, set status ACTIVE.
- task_id: SEO-CONTENT-001
  title: SEO blog + social content pipeline
  status: IN PROGRESS
  done:
    - Blog: "Halo vs Luma" — live with featured image
    - Blog: "DIY vs Pre-assembled" — live with featured image
    - September social calendar: growth/content/SOCIAL-CALENDAR-SEP-2026.md
        (12 IG posts, 20 Pinterest pins, 2 TikToks planned)
  next_actions:
    - Publish Halo vs Luma carousel to Instagram — slot Fri 2026-09-05
    - Draft Denmark buyers guide blog article from growth/content/CONTENT-BACKLOG.md
- task_id: REVIEWS-001
  title: Accumulate first product reviews (prerequisite for Meta ads)
  status: BLOCKED — 0 reviews; need ≥ 3 before Meta ads launch
  infra: Judge.me live — auto-requesting reviews 21 days after fulfillment
  next_action: Identify contacts who have used Auroom saunas and ask them to leave
    a review directly on the PDPs. Do not run Meta ads until 3 reviews are live.
- task_id: HEATER-IMAGES-001
  title: Upload HUUM/Harvia heater images + thumbnail in bundle picker/cart
  status: not started — reconnaissance only (secondary task, deliberately not
    allowed to block the PDP work).
  found: local images exist at
    AuroomWellness/HUUM & Harvia/Pictures/ and AuroomWellness/Bundle Pictures/
    Coverage is PARTIAL — roughly 4 of the 14 heater models listed in
    snippets/vh-heater-map.liquid (HUUM Drop + Uku control, HUUM Hive Flow Mini,
    HUUM Hive Wood 17, Harvia Cilindro PC90). No images for the Harvia The Wall
    SW45/SW60/SW80, Cilindro PC110E, HUUM CORE Wall Mini, Hive Wood 13,
    Harvia M3 Steel or 20 PRO Steel.
  blocker: .env SHOPIFY_ADMIN_TOKEN is expired, so the documented Node
    staged-upload path (memory: shopify-image-upload-method) cannot run until the
    token is reissued. The primary session's Shopify MCP is an alternative route.
- task_id: NORA-IMAGE-001
  title: Fix Nora PDP gallery rendering — wrong aspect ratio images
  status: complete (2026-08-24).
  root_cause: NOT theme settings, NOT Shopify image settings. Two source images had
    wrong aspect ratios for the 4:3 cover gallery — a 600×600 square PNG (1:1) and
    a 400×600 portrait JPEG (2:3). Cover-cropped to 4:3, both were destructively
    cropped.
  fix_applied:
    - All 4 Natural Wood variants re-mapped to the Spain lifestyle shot
      (gid://shopify/MediaImage/64686949957974, 4800×3584, native ~4:3). Used
      productVariantDetachMedia + productVariantAppendMedia, split into TWO separate
      calls (Nora 250 group first, Nora 210 group second) to avoid the
      mixed-variant batch-rollback bug.
    - Portrait 400×600 image deleted from product entirely (productDeleteMedia /
      fileUpdate deprecation path).
  notes: Product still has ~19 images (portrait deleted = 18 remaining). Full
    8-image consolidation to the gallery standard is a separate follow-up task.
    Brushed Black variants retain their own hero (gid://shopify/MediaImage/63852482330966).
- task_id: ACCESSORIES-HERO-001
  title: Upload hero/banner image for Sauna Accessories collection
  status: complete (2026-08-24).
  collection_gid: gid://shopify/Collection/704675643734
  source_image: AuroomWellness\ (wellness area lifestyle — sauna + ice bath + shower)
  processed_to: sauna-accessories-hero.jpg (1800×1208, 653KB, JPEG-85)
  upload_path: stagedUploadsCreate → GCS POST (Node ES module) → collectionUpdate
    mutation with imageInput. Completed without Admin API token (used Shopify MCP).
  notes: Previous collection image was a reused Sola 210 lakeside product render.
    Replaced with a dedicated wellness-area lifestyle scene that better represents
    the Accessories collection concept.
```

- task_id: PRICING-ENGINE-001
  title: Barrel Sauna Pricing Engine — correct all 72 configurations
  status: PHASE 1 COMPLETE (2026-08-27). Group A — 33 Black finish variants repriced,
    all verified by independent read-back. Zero drift. Zero failures. 6 BLOCKED configs
    remain untouched pending Auroom assembly cost confirmation.
  stop_gate: CLEARED for Phase 1 Group A. Phase 2 (Group C unblock) requires new
    supplier data from Silga/Auroom before any further mutations are authorized.
  phases_complete:
    - Phase 0A: pre-implementation audit + architecture (published artifact)
    - Phase 0B: corrected supplier-cost matrix; uncovered tax model ambiguity
    - Phase 0C: tax model confirmed live (ADD_TAXES_AT_CHECKOUT, ex-VAT prices);
        Black finish commercial decision made (tiered: +€600/€800/€1,000 ex-VAT);
        full 72-config matrix computed with correct ex-VAT GM formula.
  key_finding_tax: Shopify variant price = ex-VAT. Phase 0B Phase had incorrect
    incl-VAT assumption. Corrected: GM = (price − landed) / price (not price/1.25).
    All Natural configs now 56–66% GM (not 50–65% as previously shown).
  key_finding_black: All Black configs were priced €0–€300 above Natural despite
    €490–€875 Auroom EXW uplift. 0 of 36 Black variants were at target.
  decision_black: Tiered retail premium (ex-VAT):
    - Tier 1 (EXW uplift €490–€540): +€600 — Halo Cosy 120/150, Sola 140
    - Tier 2 (EXW uplift €590–€725): +€800 — Halo Cosy 180/225, Luma Cosy 225/260
    - Tier 3 (EXW uplift €795–€875): +€1,000 — all Comfy, Nora, Sola 210/250
  decision_natural: KEEP ALL — all Natural configs above 52.5% target, no changes.
  mutation_groups:
    - Group A (safe, 33 configs): all Black finish increases — apply in Phase 1
    - Group B (review, 0 configs): none
    - Group C (blocked, 6 configs): Pre-assembled for Halo Cosy 120, Nora 210,
        Sola 250 — Auroom assembly cost absent from PDF; do not price.
  outputs:
    - pricing/PRICING-ENGINE-HANDOFF.md — authoritative Phase 1 handoff
    - artifact: https://claude.ai/code/artifact/166aaa68-ddb0-4f12-82ce-606ed506ebbb
  phase1_outputs:
    - pricing/snapshots/snapshot-20260827-120000.json — pre-mutation snapshot (all 72 variants)
    - pricing/PHASE-1-MUTATION-REPORT.md — permanent Phase 1 mutation report
  next_action: Request Halo Cosy 120 / Nora 210 / Sola 250 assembly costs from
    Silga/Auroom to unblock the 6 Group C (BLOCKED) Pre-assembled configs.
  supplier_data_blockers:
    - Halo Cosy 120 assembly cost: email sent to Silga 2026-08-31 — AWAITING REPLY
    - Nora 210 assembly cost: email sent to Silga 2026-08-31 — AWAITING REPLY
    - Sola 250 assembly cost: email sent to Silga 2026-08-31 — AWAITING REPLY
  next_action: When Silga replies with the 3 figures, activate the 6 Group C Pre-assembled
    variants (Halo 120 / Nora 210 / Sola 250 — Black + Natural each) and reprice.
- task_id: AUROOM-PARTNER-001
  title: Auroom partner logo + footer partners section + /pages/partners
  status: complete (2026-08-26). All pushed to live theme 205414105430 via CLI.
  outputs:
    - sections/vh-brand-story.liquid — Auroom gold logo (66px) added below
      "Our story" link with "Manufacturing partner" label + gold hairline separator
    - sections/vh-footer-partners.liquid — new footer section: Auroom logo (not
      linked) + Auroom Wellness description + auroomwellness.com external link.
      Sits between main footer and utilities strip. Corrected facts: barrel saunas
      from Latvia, cabin saunas from Estonia, all wood = Thermory, 20+ years
      experience, no exclusive distributor claim, no founding year.
    - assets/veldora-custom.css — partner badge styles (.vh-story-partner etc.)
    - sections/footer-group.json — vh_partners_fP3kx2 section added to footer order
    - Shopify page gid://shopify/Page/192484475222 created at /pages/partners
      (published, ready to receive more partners)
    - Menu gid://shopify/Menu/325581570390 (footer-about) updated: added
      "Partners → /pages/partners" as third item after Our Story + How It Works
  git: main HEAD 7f79d5e
  deploy_method: shopify theme push --allow-live (CLI now authenticated)

## Theme snapshot

```yaml
root: C:\VeldoraHaven\theme
remote: https://github.com/adamant1337/VeldoraHaven1.git
branch: main
head: 7f79d5e
base_theme: Shopify Horizon 3.5.1
```

## Theme IDs (IMPORTANT)

```yaml
live_theme:        205414105430  # "Copy of VeldoraHaven — v28 Vendor + Footer" (MAIN/published)
github_connected:  205283819862  # "VeldoraHaven — v28 Vendor + Footer" (UNPUBLISHED — GitHub auto-deploy target)
```

GitHub auto-deploy pushes to 205283819862 (NOT the live theme).
To push to live: `shopify theme push --theme 205414105430 --allow-live --only <files>`
Shopify CLI is now authenticated.

## File-ownership locks

_PDP-SHOWROOM-001 is complete and deployed. All locks released._

## Blockers / cautions

- GitHub auto-deploy goes to unpublished theme 205283819862, NOT the live theme
  205414105430. Always use `shopify theme push --allow-live` for live deploys.
- Shopify CLI **authenticated** as of 2026-08-26.
