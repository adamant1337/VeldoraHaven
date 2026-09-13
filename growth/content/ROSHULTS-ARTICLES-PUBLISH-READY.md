# Röshults Blog Articles — Publish Ready

**Status:** Content complete. Blocked on `write_content` API scope.
**Date prepared:** 2026-09-01
**Articles:** 2

---

## BLOCKER

The `veldora-upload` custom Shopify app (client_id: 86c76a799b0fbd6f1c1fc93ea0180ada) has scopes:
`write_files`, `write_products` only. Blog article creation requires `write_content`.

**To unblock:** Shopify Admin > Apps > App and sales channel settings > veldora-upload > Configuration > Add scopes: `read_content`, `write_content` > Save > reinstall.

**Alternatively:** Use the connected Shopify MCP session (which is always authed and may have the right scopes) to execute the mutations below directly.

---

## STEP 1 — Find the Outdoor Living blog GID

Run via Shopify MCP `graphql_query`:
```graphql
{ blogs(first: 10) { edges { node { id title } } } }
```
Expected result: blog with title "Outdoor Living", GID = `gid://shopify/Blog/<id>`

---

## STEP 2 — Create Article 1 (Essentials vs Kitchen Island)

Run via Shopify MCP `graphql_mutation` — substitute `BLOG_GID` with the real GID:

```graphql
mutation {
  articleCreate(article: {
    blogId: "BLOG_GID"
    title: "Röshults Essentials vs Kitchen Island: Which Outdoor Kitchen Format Is Right for You?"
    body: "<article body — see growth/content/blog-roshults-essentials-vs-kitchen-island.md>"
    author: { name: "Veldora Haven" }
    tags: ["outdoor-kitchen", "roshults", "buyers-guide"]
    isPublished: true
    publishedAt: "2026-09-01T00:00:00Z"
    summary: "Comparing the Röshults Essentials Set and Kitchen Island — two distinct outdoor kitchen formats for different spaces, budgets, and ambitions."
  }) {
    article { id handle publishedAt }
    userErrors { field message }
  }
}
```

Then update featured image (substitute ARTICLE_GID):
```graphql
mutation {
  articleUpdate(id: "ARTICLE_GID", article: {
    image: {
      src: "https://cdn.shopify.com/s/files/1/1029/5620/4374/files/Roshults-Outdoor-Kitchen_11064-LowRes.webp?v=1788296441"
      altText: "Röshults outdoor kitchen — Essentials vs Kitchen Island comparison"
    }
  }) {
    article { id image { url } }
    userErrors { field message }
  }
}
```

---

## STEP 3 — Create Article 2 (Finishes guide)

Run via Shopify MCP `graphql_mutation` — substitute `BLOG_GID`:

```graphql
mutation {
  articleCreate(article: {
    blogId: "BLOG_GID"
    title: "Stainless Steel, Beluga Black or Anthracite: Choosing the Right Finish for Your Outdoor Kitchen"
    body: "<article body — see growth/content/blog-roshults-finishes-guide.md>"
    author: { name: "Veldora Haven" }
    tags: ["outdoor-kitchen", "roshults", "materials-guide", "finishes"]
    isPublished: true
    publishedAt: "2026-09-01T00:00:00Z"
    summary: "A guide to the three Röshults finishes — marine-grade stainless, Beluga Black powder coat, and Anthracite — covering outdoor performance, maintenance, and which settings suit each."
  }) {
    article { id handle publishedAt }
    userErrors { field message }
  }
}
```

Then update featured image (substitute ARTICLE_GID):
```graphql
mutation {
  articleUpdate(id: "ARTICLE_GID", article: {
    image: {
      src: "https://cdn.shopify.com/s/files/1/1029/5620/4374/files/Roshults_Outdoor-Kitchen_Kitchen-Island_Principle_03-Finish.webp?v=1788296438"
      altText: "Röshults outdoor kitchen finishes — stainless steel, Beluga Black, Anthracite"
    }
  }) {
    article { id image { url } }
    userErrors { field message }
  }
}
```

---

## HTML BODY — Article 1

```html
<p>Röshults makes two distinct families of outdoor kitchen. One is a composed, modular set you can order and install without an architect. The other is a bespoke built-in system designed to fill a terrace the way a kitchen fills a room. Both are Swedish. Both are built in 316L marine-grade stainless steel or powder-coated aluminium. The comparison between them is less about quality — which is uniformly high — and more about how you want your outdoor space to function.</p>

<h2>The Essentials Set — A Complete Kitchen, Ready to Configure</h2>

<p>The <a href="/products/roshults-essentials-set-stainless-steel-amp-charcoal-grill">Röshults Essentials Set</a> is a three-module freestanding outdoor kitchen. It arrives as a coordinated collection: a storage and preparation unit, a sink unit, and a grill — charcoal or gas depending on the configuration you choose. The units connect to form a coherent run, but each piece is independent. You can rearrange them, separate them, move them if you change your garden layout.</p>

<p>This is the format for people who want a serious outdoor kitchen without the commitment of a permanent installation. There's no groundwork. No structural integration. No need to co-ordinate with a landscape architect. The Essentials arrives, you position it, and the terrace becomes a kitchen.</p>

<p>Two finish families: <a href="/products/roshults-essentials-set-stainless-steel-amp-charcoal-grill">Stainless Steel with a charcoal grill</a>, or <a href="/products/roshults-essentials-set-beluga-black-amp-gas-grill">Beluga Black with a gas grill</a>. The stainless version reads as a professional kitchen translated outdoors — cool, precise, reflective. The Beluga Black version is quieter. It reads less as equipment and more as furniture. The gas grill in the black configuration makes it a practical choice for anyone who cooks regularly and values ignition speed.</p>

<p>Who the Essentials suits best: the homeowner with a well-finished terrace who wants a permanent kitchen presence without permanent installation. Garden renters. People who might move. Those who want full outdoor kitchen capability at a more contained footprint and a lower entry cost than a full island run.</p>

<h2>The Kitchen Island — A Permanent Outdoor Room</h2>

<p>The Kitchen Island is a different proposition entirely. Available in a <a href="/products/roshults-kitchen-island-5m-bar-stainless-steel">5-metre stainless steel bar configuration</a> and a <a href="/products/roshults-kitchen-island-4m-wall-anthracite">4-metre wall-mounted anthracite configuration</a>, it's designed to be integrated into architecture — set against a wall, running along a terrace perimeter, or installed as the centrepiece of a purpose-built outdoor room.</p>

<p>The scale changes the relationship to the space. A five-metre run of stainless steel with integrated grill, refrigeration, and preparation zones isn't an accessory to a terrace — it is the terrace. The space organises itself around the kitchen rather than the other way around. This is the format for serious outdoor cooking, frequent entertaining, and homes where the garden is treated as a genuine extension of the interior.</p>

<p>The 4M Wall Anthracite configuration leans more architectural. It sits flat against a structure, conserves terrace depth, and in anthracite — a matte, near-charcoal powder coat — it disappears into its surroundings in a way that stainless never will. It reads as a feature of the building rather than a piece of equipment placed against it.</p>

<p>Who the Kitchen Island suits best: the homeowner undertaking a landscaping project and treating the outdoor kitchen as a structural element from the start. Those with large terraces where the kitchen will anchor the entertaining zone. Anyone whose outdoor cooking is serious enough to require the full-width of a professional-grade installation.</p>

<h2>The Honest Comparison</h2>

<p>There's no correct choice between the two — only the right choice for your space, your habits, and your plans.</p>

<p>The Essentials is the more flexible, more immediately accessible format. It delivers the full outdoor kitchen experience — cooking, preparation, storage — without requiring you to commit to a permanent installation. The tradeoff is scale: three modules, even well-configured, don't give you the continuous multi-metre workflow of a full island.</p>

<p>The Kitchen Island is the more ambitious format. It requires planning, positioning, and in most cases a degree of landscape integration. The reward is a space that functions like an interior kitchen — and a terrace that operates as a room.</p>

<p>If you're starting to think about an outdoor kitchen and want to understand which format fits your project, <a href="/pages/contact">we're available for a conversation</a>. We work with a small number of clients at a time and can help you think through both the kitchen and the wider terrace context it sits within.</p>
```

---

## HTML BODY — Article 2

```html
<p>When you're choosing an outdoor kitchen, the finish decision is more consequential than it might initially appear. Outdoors, a material doesn't just look a certain way — it ages a certain way, responds to weather a certain way, and interacts with its setting differently across seasons. The three finishes across the Röshults range — Stainless Steel, Beluga Black, and Anthracite — are each purpose-built for outdoor use, but they serve different aesthetics, suit different settings, and ask different things of you over time.</p>

<h2>Stainless Steel — Precise, Marine-Grade, Enduring</h2>

<p>The stainless steel across the Röshults range is 316L marine grade. The L designation matters: it indicates a lower carbon content that improves weld integrity and corrosion resistance in aggressive environments. Marine-grade 316L is the standard for coastal installations, boat fittings, and outdoor installations where salt air is a genuine consideration rather than a theoretical one.</p>

<p>Visually, stainless is reflective and precise. It carries the vocabulary of a professional kitchen — the brushed steel of a serious cooking environment — outdoors. In strong sunlight it gains warmth; in overcast northern light it reads cooler and more architectural. Against limestone or concrete terrace materials it has a particular authority. Against timber or natural stone it creates a deliberate contrast between industrial precision and natural texture.</p>

<p>The maintenance question with stainless outdoors is honest: it will develop surface marks and fingerprints with use, and in coastal environments, regular wiping with a fresh-water cloth is good practice. Over time, stainless develops a natural patina — slightly warmer and more matte than new — that most owners consider an improvement. It doesn't corrode in the structural sense; surface discolouration is aesthetic, not material. The <a href="/products/roshults-essentials-set-stainless-steel-amp-charcoal-grill">Essentials in Stainless Steel</a> and the <a href="/products/roshults-kitchen-island-5m-bar-stainless-steel">Kitchen Island 5M Bar</a> are available in this finish.</p>

<p>Stainless suits: coastal homes, spaces with stone or concrete architecture, owners who want their outdoor kitchen to read as a serious culinary installation, and projects where longevity in demanding environments is the primary concern.</p>

<h2>Beluga Black — Recessive, Furniture-Like, UV-Stable</h2>

<p>Beluga Black is a powder-coated finish applied to aluminium. Powder coating bonds electrostatically and is cured under heat, producing a finish that is harder and more durable than liquid paint — it resists chipping, scratching, and UV degradation in ways that conventional outdoor paint cannot. The black in Beluga Black is deep and near-matte: it absorbs light rather than reflecting it.</p>

<p>Where stainless makes a kitchen statement, Beluga Black makes a furniture statement. It reads like a high-quality outdoor chair or a premium architectural cladding panel — present, intentional, but not announcing itself. In a garden setting, this quality is valuable. The kitchen doesn't compete with the planting, the view, or the landscape. It integrates.</p>

<p>Beluga Black is UV-stable and does not fade in the way that conventional black finishes do. In direct summer sun it will absorb heat — this is worth considering when thinking about placement relative to seating areas. It does not develop a patina in the traditional sense; it maintains its appearance over time with minimal intervention. <a href="/products/roshults-essentials-set-beluga-black-amp-gas-grill">The Essentials in Beluga Black</a> pairs with a gas grill, making it a practical format for frequent cooking.</p>

<p>Beluga Black suits: gardens where the kitchen should integrate rather than dominate, projects with existing dark furniture or architectural ironwork, owners who want the lowest-maintenance finish in terms of visible surface marks, and those who want the kitchen to read as a furniture piece rather than a piece of equipment.</p>

<h2>Anthracite — Architectural, Matte, Site-Integrated</h2>

<p>Anthracite is a matte powder coat — a near-charcoal tone that sits between grey and black, closer to the colour of natural slate or charred timber than to a conventional dark grey. Like Beluga Black it is applied to aluminium and offers strong UV stability, but the tone is distinctly different: cooler, more architectural, less furniture-forward.</p>

<p>Where Beluga Black has a quality that reads as deliberate design, anthracite has a quality that reads as belonging. Against stone terrace flooring, rendered exterior walls, or dark timber cladding, it can appear almost to disappear — not in a way that diminishes the kitchen, but in a way that makes it feel like it was always part of the building. The <a href="/products/roshults-kitchen-island-4m-wall-anthracite">Kitchen Island 4M Wall in Anthracite</a> uses this quality deliberately: positioned against a wall, in this finish, it integrates into the architecture rather than standing apart from it.</p>

<p>Maintenance requirements are similar to Beluga Black: minimal. The matte surface is less likely to show fingerprints than a gloss or near-gloss finish. The colour's neutrality means it works across light and dark settings without imposing a dominant visual note.</p>

<p>Anthracite suits: homes with architectural exteriors in stone, concrete, or render, terrace projects where the kitchen is treated as infrastructure rather than a focal point, and large-format installations where the finish needs to be site-specific rather than self-referential.</p>

<h2>Choosing Between Them</h2>

<p>The finish decision is best made in context. A stainless kitchen photographs well and reads as a statement from across the garden; a black or anthracite kitchen integrates and reads as part of the space when you're within it. Neither is a better choice in the abstract.</p>

<p>If you're deciding between finishes and would find it useful to talk through the specific context of your terrace — the materials, orientation, and how the kitchen will sit within the wider design — <a href="/pages/contact">we're happy to have that conversation</a>. It's a decision worth getting right.</p>
```
