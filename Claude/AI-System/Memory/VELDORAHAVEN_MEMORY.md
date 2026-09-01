# VELDORAHAVEN — PROJECT MEMORY
## AI Agency Source of Truth

**Project:** VeldoraHaven  
**Primary domain:** https://www.veldorahaven.com/  
**Project root:** `C:\VeldoraHaven\AuroomWellness`

**Purpose:**  
This document is the persistent memory and source of truth for all AI agents working on VeldoraHaven.

Agents MUST read this document before making significant changes to the project.

---

# 1. BRAND

## Brand

**VeldoraHaven**

VeldoraHaven is a premium outdoor living and wellness ecommerce brand.

Core categories include:

- Premium outdoor kitchens
- Saunas
- Cold plunges
- Hot tubs
- Fire features
- Outdoor living products
- Accessories

The brand should feel:

- Premium
- Scandinavian
- Architectural
- Sophisticated
- Natural
- Minimal
- Timeless
- Wellness-focused
- High-end

VeldoraHaven should never feel like a generic Shopify store.

---

# 2. AUROOM RELATIONSHIP

VeldoraHaven is an authorized **Auroom Wellness retailer**.

We are permitted to use approved Auroom branding, product photography, videos and other assets according to our retailer agreement.

Auroom is therefore not merely an inspiration.

Auroom is an important product brand that VeldoraHaven officially represents.

However:

**VeldoraHaven is the retailer.**

The website must therefore feel like:

> A premium VeldoraHaven showroom featuring Auroom Wellness.

It should NOT simply look like a copy of Auroom's official website.

---

# 3. AUROOM REFERENCE

Primary reference:

https://auroomwellness.com/

Important reference pages:

https://auroomwellness.com/our-products/

https://auroomwellness.com/product/nora/

Auroom is the primary benchmark for:

- Product presentation
- Photography
- Product storytelling
- Interaction quality
- Editorial layouts
- Product grids
- Image transitions
- Visual hierarchy
- Premium whitespace
- Product-page structure
- Wellness/lifestyle presentation

When improving VeldoraHaven, ask:

> "What is Auroom doing that makes their experience feel more premium than ours?"

Then identify the specific gap.

Do not blindly copy the entire site.

---

# 4. PROJECT DIRECTORY

Primary project/resource directory:

`C:\VeldoraHaven\AuroomWellness`

This directory contains VeldoraHaven and Auroom-related resources.

Potential contents include:

- Shopify project
- Images
- Renders
- Product photography
- Auroom assets
- Videos
- Design files
- Product information
- Previous Claude work
- Agent documentation
- Supporting files

Agents MUST inspect this directory before searching externally for assets.

---

# 5. ASSET PRIORITY

When looking for an asset:

## Priority 1

Use an approved asset already available locally in:

`C:\VeldoraHaven\AuroomWellness`

## Priority 2

Use an existing asset already implemented on VeldoraHaven.

## Priority 3

Use an approved asset from Auroom's official website/resources where permitted.

Do NOT:

- use random stock photography
- use third-party Auroom assets
- create fake product imagery when official imagery exists
- replace approved Auroom photography unnecessarily

When an official Auroom image exists, prefer it over generic imagery.

---

# 6. EXISTING WEBSITE

The VeldoraHaven webshop is already substantially built.

Agents must assume that significant work has already been completed.

DO NOT treat the project as a blank slate.

Before changing anything:

1. Inspect existing architecture.
2. Inspect existing components.
3. Inspect existing styling.
4. Inspect existing functionality.
5. Identify what is already working.
6. Identify exactly what is missing.
7. Change only what is necessary.

---

# 7. DESIGN PHILOSOPHY

VeldoraHaven should feel closer to:

**Luxury architecture showroom**

+

**Premium Scandinavian furniture**

+

**Luxury wellness brand**

+

**High-end ecommerce**

than a conventional Shopify store.

The website should use:

- Large imagery
- Generous whitespace
- Editorial layouts
- Strong typography
- Natural materials
- Subtle motion
- Cinematic photography
- Quiet interactions
- Premium spacing

---

# 8. PRODUCT-FIRST DESIGN

Products are the heroes.

The website should not visually overpower the products with UI.

Preferred hierarchy:

IMAGE

↓

PRODUCT

↓

STORY

↓

DETAILS

↓

CTA

Avoid:

- excessive cards
- excessive borders
- excessive shadows
- giant buttons
- excessive badges
- unnecessary UI decoration

---

# 9. PRODUCT GRID PHILOSOPHY

The product grid should NOT look like:

4 small Shopify cards across the screen.

Preferred:

Large editorial product presentation.

Typical desktop direction:

2-column layout

with:

- large images
- generous spacing
- visual rhythm
- consistent proportions
- occasional feature layouts
- strong typography

The goal:

**product showroom**

not:

**product database**

---

# 10. PRODUCT CARD STANDARD

Preferred structure:

LARGE IMAGE

AUROOM

PRODUCT NAME

PRODUCT TYPE

Short description

Price / commercial information

EXPLORE →

The image should dominate.

Product information should support the visual rather than compete with it.

---

# 11. HOVER EXPERIENCE STANDARD

This is a major VeldoraHaven design requirement.

Where multiple approved product images exist:

PRIMARY IMAGE

→

SECONDARY IMAGE

on hover.

Use layered images.

Never instantly swap the image.

Preferred transition:

500–700ms

Preferred easing:

`cubic-bezier(0.22, 1, 0.36, 1)`

The image should crossfade smoothly.

---

# 12. CINEMATIC IMAGE MOVEMENT

Hover should include subtle movement.

Preferred:

scale:

`1.015–1.025`

then return toward:

`1`

The effect must be subtle.

The goal is:

**cinematic**

not:

**animated**

Never use:

- aggressive zoom
- bounce
- flash
- spinning
- excessive parallax

---

# 13. PRODUCT MICRO-INTERACTIONS

On hover:

Product name may move:

`translateY(-2px)`

Explore arrow may move:

`translateX(4–8px)`

Everything should feel coordinated.

Animations should be restrained.

---

# 14. SCROLL ANIMATION

Preferred product entrance:

Image:

opacity 0 → 1

translateY:

25px → 0

Text:

opacity 0 → 1

translateY:

12px → 0

Use subtle stagger.

Avoid animating every element.

---

# 15. PARALLAX / CINEMATIC SCROLL

If used:

Keep movement extremely subtle.

Approximately:

5–15px.

Performance takes priority.

Avoid heavy continuous scroll calculations.

Prefer:

- IntersectionObserver
- CSS transforms
- requestAnimationFrame only when necessary

---

# 16. PRODUCT STORYTELLING

Products should feel like objects with a story.

Auroom product pages are an important benchmark.

Typical structure:

HERO

↓

PRODUCT INTRODUCTION

↓

PRODUCT STORY

↓

KEY FEATURES

↓

MATERIALS

↓

DIMENSIONS

↓

CUSTOMIZATION

↓

GALLERY

↓

VIDEO

↓

RELATED PRODUCTS

↓

INQUIRY / PURCHASE

This is the preferred direction for future VeldoraHaven product pages.

---

# 17. SAUNA CATEGORY

Saunas are a major VeldoraHaven category.

Relevant Auroom structures include:

- Indoor
- Outdoor
- Designer
- Essential
- Barrel
- Custom / Tailor-made

Use actual Shopify collections/data where available.

Do not invent product categories if the real catalogue differs.

---

# 18. BARREL SAUNAS

Current reference collection:

https://www.veldorahaven.com/collections/barrel-saunas

Current known products include:

- Nora
- Halo
- Luma
- Sola

The collection already contains product images.

Many products have multiple images.

These should be used intelligently for the hover system.

Example:

Primary image:

strongest product/hero image

Secondary image:

best complementary image

The second image should reveal something different:

- interior
- alternate angle
- porch
- lifestyle
- detail

Do not simply use the next image blindly.

---

# 19. BARREL SAUNA COLLECTION EXPERIENCE

The desired experience is:

HERO

↓

EDITORIAL INTRO

↓

PRODUCT DISCOVERY

↓

HOVER / IMAGE TRANSITION

↓

PRODUCT STORY

↓

BUYING GUIDE

↓

CTA

The existing buying guide should be preserved.

Do not delete existing useful content merely to imitate Auroom.

---

# 20. INDIVIDUAL PRODUCT PAGE

Individual sauna product pages should eventually become premium editorial product experiences.

The hero should be visually dominant.

Preferred:

AUROOM

PRODUCT NAME

PRODUCT TYPE

Large image/video

Short statement

Then:

Story

Features

Materials

Dimensions

Customization

Gallery

Video

Related products

CTA

---

# 21. CUSTOMIZATION

Customization is an important part of premium Auroom positioning.

Where supported by actual product data, highlight:

- Wood
- Glass
- Benches
- Lighting
- Heater
- Accessories
- Other options

Do not create fake configuration functionality.

---

# 22. CTA PHILOSOPHY

VeldoraHaven should feel premium, not aggressive.

Preferred CTAs:

- Explore
- Discover
- Request a Quote
- Enquire
- Book a Consultation
- View Product
- Discover Options

Avoid:

- BUY NOW!!!
- excessive urgency
- aggressive sales language

Unless a product genuinely requires direct ecommerce purchase.

---

# 23. TYPOGRAPHY

Typography should feel:

- Editorial
- Architectural
- Scandinavian
- Premium
- Restrained

Use:

large headings

small uppercase labels

generous spacing

limited font weights

Avoid excessive typography styles.

---

# 24. COLOR

VeldoraHaven's visual language should remain compatible with the established brand.

General direction:

- Forest / natural tones
- Warm neutrals
- Black / charcoal
- White / off-white
- Natural wood
- Stone

Do not turn the entire website green.

Color should support the products and photography.

---

# 25. IMAGE PHILOSOPHY

Images should feel:

- Architectural
- Cinematic
- Natural
- Premium
- Warm
- Aspirational

Use large image areas.

Do not crop products unnecessarily.

Do not distort images.

Respect important product geometry.

---

# 26. VIDEO

Where approved Auroom videos are available:

Use them strategically.

Potential locations:

- Hero
- Collection storytelling
- Product storytelling
- Gallery
- Brand sections

Video should be:

- muted
- looped
- playsinline
- appropriately lazy-loaded

Use poster images.

---

# 27. PERFORMANCE

Premium visual design must not destroy performance.

Always consider:

- LCP
- CLS
- image dimensions
- lazy loading
- responsive image sizes
- WebP/AVIF
- video loading
- JavaScript size
- animation cost

Do not introduce heavy libraries for small visual effects.

---

# 28. ANIMATION LIBRARIES

Do NOT automatically introduce:

- GSAP
- Lenis
- Three.js
- WebGL
- Framer Motion
- custom cursor libraries

First use:

CSS

+

small JavaScript

+

IntersectionObserver

Only introduce a library when clearly justified.

---

# 29. MOBILE

Mobile must be designed intentionally.

Never simply shrink desktop.

Preferred:

one-column product layout

large images

comfortable spacing

subtle scroll reveals

touch-friendly interactions

No critical information may depend on hover.

---

# 30. ACCESSIBILITY

Respect:

`prefers-reduced-motion`

When enabled:

disable/reduce:

- parallax
- cinematic movement
- scroll animation

Maintain:

- navigation
- readability
- product access
- keyboard functionality

---

# 31. PERFORMANCE > EFFECTS

If an animation looks impressive but negatively affects:

- LCP
- CLS
- scrolling
- mobile performance

remove or simplify it.

The site must feel premium AND fast.

---

# 32. DEVELOPMENT PRINCIPLE

Agents should follow:

**Inspect → Understand → Compare → Identify Gap → Implement → Test → Refine**

NOT:

**Guess → Rebuild → Break existing work**

---

# 33. CHANGE MANAGEMENT

Before significant changes:

Identify:

- what exists
- what is missing
- why the change is necessary

Prefer small, controlled changes.

Do not modify unrelated systems.

Protect existing:

- Shopify functionality
- navigation
- cart
- checkout
- pricing
- product data
- analytics
- SEO
- existing performance work

---

# 34. DESIGN DECISION RULE

When uncertain between:

### A

More animation

### B

More whitespace

Choose:

**B**

When uncertain between:

### A

More UI

### B

More product imagery

Choose:

**B**

When uncertain between:

### A

Complex implementation

### B

Simple implementation that looks equally good

Choose:

**B**

---

# 35. QUALITY STANDARD

The target is not:

"Looks good for a Shopify store."

The target is:

**"Could this sit beside a world-class luxury wellness brand and look credible?"**

The answer should eventually be:

**YES.**

---

# 36. CURRENT PRIORITY

The current highest-priority visual improvement is:

## Auroom-Level Product Experience

Specifically:

1. Product grid
2. Hover experience
3. Secondary-image transition
4. Cinematic image movement
5. Product micro-interactions
6. Scroll reveal
7. Editorial spacing
8. Better product storytelling

---

# 37. CURRENT BARREL SAUNA PRIORITY

First focus on:

https://www.veldorahaven.com/collections/barrel-saunas

The desired interaction:

PRODUCT IMAGE

↓

HOVER

↓

SECONDARY IMAGE

↓

CINEMATIC TRANSITION

↓

SUBTLE MOVEMENT

↓

PRODUCT INFORMATION

↓

EXPLORE →

This should feel exceptional.

---

# 38. AVOID DESIGN DRIFT

Over time, AI agents may unintentionally change the visual direction.

This document prevents that.

Whenever an agent proposes a significant design change, it should ask:

Does this strengthen:

- premium positioning?
- Scandinavian aesthetic?
- product-first design?
- Auroom-level quality?
- VeldoraHaven identity?

If not:

Do not implement it.

---

# 39. DO NOT DESTROY EXISTING WORK

A future agent MUST assume that previous agents may have implemented important functionality.

Before modifying an existing component:

Inspect it.

Understand it.

Preserve useful work.

Improve it instead of replacing it unnecessarily.

---

# 40. MEMORY UPDATE RULE

This file should evolve.

When a major project decision is made, update this document.

Examples:

- New design system
- New typography
- New animation standard
- New product structure
- New Auroom asset strategy
- New technical architecture
- Important performance decision
- Important retailer/brand rule

Do NOT fill this document with temporary tasks.

This is persistent project memory, not a todo list.

---

# 41. SOURCE OF TRUTH HIERARCHY

When sources conflict, use this hierarchy:

### 1.

Current production VeldoraHaven functionality

### 2.

Current VeldoraHaven project files

### 3.

This MEMORY document

### 4.

Approved Auroom assets/product information

### 5.

Auroom website visual reference

### 6.

General web/design trends

Never sacrifice established VeldoraHaven functionality merely to imitate a visual reference.

---

# 42. AGENT MINDSET

Every AI agent working on VeldoraHaven should think:

> "I am working on an already-established premium ecommerce brand."

Not:

> "I am starting a new website."

The objective is continuous improvement.

Every iteration should make the website:

- more premium
- more coherent
- more beautiful
- more useful
- faster
- more conversion-focused

without unnecessary destruction.

---

# 43. FINAL NORTH STAR

VeldoraHaven should become:

## A PREMIUM DIGITAL SHOWROOM FOR OUTDOOR LIVING & WELLNESS

Where:

Auroom products feel luxurious.

Photography feels cinematic.

Interactions feel expensive.

Information feels effortless.

Navigation feels intuitive.

The brand feels Scandinavian.

The site feels fast.

And the entire experience feels intentional.

---

# END OF MEMORY

This document is a living source of truth.

Read it before major implementation work.

Update it when major permanent decisions are made.

Do not turn it into a temporary task list.