# Collection copy — voice audit and rewrite

**Date:** 2026-09-02
**Source text:** `C:\VeldoraHaven\cache\current-collection-copy.md` (live `descriptionHtml`, fetched today)

## How to use this file

Nothing here is pushed automatically. Each `## ` section below contains one complete,
paste-ready `descriptionHtml` block. In Shopify: **Products → Collections → [collection] →
Description → `< >` (Edit HTML)** → select all → paste the block → Save.

Paste the **whole** block each time, including the `<h2>` guide section at the end. Do not
merge old and new by hand — the old paragraph breaks and `<strong>` tags are the problem
being fixed.

The "before" text is not duplicated here. Read it in `current-collection-copy.md` if you want
to diff.

---

## The voice problem, and the rule applied

Four collections (`saunas`, `barrel-saunas`, `fire-features`, `sauna-accessories`) were
written in a different pass from the rest, in a performance-marketing register: a
"Discover/Shop/Complete/Create…" opener, then keyword phrases bolded inside running
sentences — product names, feature phrases, category terms. On a €4,000–€14,000 sauna page
that reads as SEO tagging rather than a catalogue, and it makes the page look busy before a
buyer has read a word. The clean references (`cabin-saunas`, `outdoor-kitchens`,
`complete-bundles`, `cold-plunge-ice-baths`, `outdoor-furniture-pergolas`) never do this.

**The rule:** `<strong>` is reserved for two structural jobs only — a **status disclosure**
("Our assortment is being finalised", as in Cold Plunge and Outdoor Furniture) and a **run-in
label at the head of a list item** (as in Complete Bundles). Everywhere else in running prose:
zero bold. Product names read as names. Every opener is an observation or a fact stated
calmly, not an invitation to shop. Every existing internal link is preserved; a few were
added where the convention called for one. Rewritten copy is 15–25% shorter.

---

## Verdicts

| handle | verdict | reason |
|---|---|---|
| `saunas` | **REWRITE** | "Discover VeldoraHaven's curated range of…" opener; bold on category keywords. |
| `barrel-saunas` | **REWRITE** | The screenshot page. Seven decorative `<strong>` including all four model names. |
| `fire-features` | **REWRITE** | "Create warmth and atmosphere…" opener; bolded category phrase; padded middle. |
| `sauna-accessories` | **REWRITE** | "Complete your sauna with…" opener; three bolded keyword phrases; no guide block. |
| `infrared-saunas` | **REWRITE (light)** | Coming-soon line earns emphasis, but "Register your interest below →" is promotional in register and promises a notify form the page does not have (the link itself did point at /pages/consultation). Restructured to match the Cold Plunge pattern. |
| `outdoor-baths-hot-tubs` | **REWRITE (restructure)** | Substance and voice are largely sound; the markup is wrong. See Part 3 reasoning below. |
| `outdoor-kitchens-1` | **FLAG** | Copy is on-voice and needs no edit. The duplicate collection is the problem. |
| `cabin-saunas` | KEEP AS-IS | Tone reference. |
| `outdoor-kitchens` | KEEP AS-IS | Tone reference. |
| `complete-bundles` | KEEP AS-IS | Tone reference. Sanctions the list-label `<strong>` pattern. |
| `cold-plunge-ice-baths` | KEEP AS-IS | Tone reference. Sanctions the status-line `<strong>` pattern. |
| `outdoor-furniture-pergolas` | KEEP AS-IS | Tone reference. |

---

## `saunas`

**What changed:** the marketing opener becomes a manufacturing fact, then a single organising
observation (barrel = object, cabin = building) that mirrors the Cabin Saunas voice. All bold
removed. Added cross-links to the two sub-collections, which the page was missing. All four
model names, sizing, factory, delivery countries, DIY/pre-assembled and heater types preserved.

```html
<p>Auroom builds saunas in Estonia to Scandinavian standards, in thermally modified timber chosen for the Northern European climate. The range divides in two: barrels, which sit in the garden as objects, and cabins, which read as buildings.</p>
<p>The <a href="/collections/barrel-saunas">barrel range</a> covers four models — Halo, Luma with its outdoor porch, the square-section Nora, and the larger Sola — in several sizes and configurations. The <a href="/collections/cabin-saunas">cabin range</a> adds full-height glazing, a proper doorway and room for a changing area.</p>
<p>Every sauna ships from the Auroom factory in Estonia to Denmark, Germany, the Netherlands and France. Each model is available as a DIY self-assembly kit or pre-assembled, with electric or wood-fired heaters.</p>
<p><a href="/pages/faq">Read the FAQ</a> or <a href="/pages/consultation">speak with a specialist</a>.</p>
<h2>Before you order</h2>
<p>Our <a href="/blogs/outdoor-living/outdoor-sauna-buying-guide">outdoor sauna buying guide</a> works through barrel versus cabin, interior sizing, heater output, the electrical supply you need in the garden, the base it stands on and long-term maintenance.</p>
```

---

## `barrel-saunas`

**What changed:** all seven `<strong>` removed. The four models are now described in plain
sentences rather than a single bolded list-sentence, so each name lands as a name. "Free
delivery" becomes "delivery is included" — same fact, no discount register. Every size,
finish, heater brand and country preserved.

**On linking the model names:** deliberately not linked here. The four products sit in the
grid immediately below this text — linking them in the paragraph duplicates the grid and
reintroduces visual noise in a different colour. They *are* linked in `saunas`, where they
are one subset among several. That is the right split.

```html
<p>Four Auroom barrel saunas, built for year-round outdoor use in Northern European weather. Each is made from thermally modified timber and finished in natural, dark oil, light oil or brushed black.</p>
<p>Halo is the compact one, in 120, 150 and 180cm diameters. Luma adds an outdoor porch and comes in 225, 260 and 300cm lengths. Nora takes a square section for a more contemporary footprint. Sola is the largest of the four.</p>
<p>Every model can be ordered as a DIY self-assembly kit or fully pre-assembled, with HUUM or Harvia heaters in electric or wood-burning form. Delivery to Denmark, Germany, the Netherlands and France is included.</p>
<p>If you are unsure which model suits your garden, <a href="/pages/consultation">speak with a specialist</a> or read the <a href="/pages/faq">FAQ</a>.</p>
<h2>Before you order</h2>
<p>The <a href="/blogs/outdoor-living/outdoor-sauna-buying-guide">outdoor sauna buying guide</a> covers sizing, heater output and installation requirements.</p>
```

If you would rather the names did link, this is the drop-in replacement for the **second `<p>`
only — do not paste this block on its own.** Replace that one paragraph inside the full block
above; it links each model once and nothing else:

```html
<p><a href="/products/auroom-halo-barrel-sauna">Halo</a> is the compact one, in 120, 150 and 180cm diameters. <a href="/products/auroom-luma-barrel-sauna">Luma</a> adds an outdoor porch and comes in 225, 260 and 300cm lengths. <a href="/products/auroom-nora-outdoor-barrel-sauna">Nora</a> takes a square section for a more contemporary footprint. <a href="/products/auroom-sola-square-barrel-sauna">Sola</a> is the largest of the four.</p>
```

---

## `fire-features`

**What changed:** "Create warmth and atmosphere in any outdoor space with…" replaced by a
plain observation about why fire is there at all. Bolded category phrase removed. The
middle paragraph was doing two jobs and is now one. The sauna cross-link and the buying-guide
block are unchanged in function, tightened in wording.

```html
<p>Fire is what keeps an outdoor space in use after the light goes. The range runs to bioethanol burners, fire pits and fire bowls — pieces that can be placed and lived around rather than designed into the structure of a terrace.</p>
<p>The selection runs from sculptural bioethanol for a contemporary terrace to plainer fire pits suited to a naturalistic garden. Each piece is chosen for design quality, outdoor performance and year-round use in Northern European conditions, and ships directly to addresses in Denmark, Germany, the Netherlands and France.</p>
<p>Fire belongs with heat and cold water. It is the part of the Nordic ritual that holds people in one place between rounds — see the <a href="/collections/barrel-saunas">barrel sauna range</a>, or <a href="/pages/consultation">speak with a specialist</a> about a complete wellness area.</p>
<h2>Choosing a fire feature</h2>
<p>Our guide to <a href="/blogs/outdoor-living/bioethanol-fire-pits-explained">bioethanol fire pits</a> explains real heat output, fuel consumption, ventilation and clearance requirements, and how to choose the right scale for your terrace.</p>
```

---

## `sauna-accessories`

**What changed:** "Complete your sauna with premium accessories…" replaced with a claim about
the heater itself, which is what this collection actually is. All three bolded keyword phrases
removed. Heater brands, named models, the 45–60 minute figure, the 230V rating, the
barrel/cabin sizing note and the wood-burning installation service are all kept. Added a
`<h2>` guide block so this page matches the structural convention of every other collection —
it was the only one without one.

```html
<p>The accessories that matter most are the heaters. A sauna is only as good as the one it is built around, and we stock HUUM and Harvia — the two names Scandinavian sauna building keeps returning to — sized for outdoor barrel and cabin volumes and rated for 230V European supply.</p>
<p>Electric heaters, among them the HUUM Drop and the Harvia range, reach temperature in 45 to 60 minutes and suit residential use where a dedicated circuit is available. Wood-burning stoves, among them the HUUM Hive Wood, give the traditional Scandinavian session — a slower rise to temperature, and the sound of the fire in the room. We arrange installation for wood-burning models.</p>
<p><a href="/pages/faq">Our FAQ</a> covers heater sizing, fuel type and installation requirements. For a full system specification, <a href="/pages/consultation">speak with a specialist</a>.</p>
<h2>Sizing a heater</h2>
<p>The <a href="/blogs/outdoor-living/outdoor-sauna-buying-guide">outdoor sauna buying guide</a> sets out heater output against interior volume, and the electrical supply a garden sauna needs.</p>
```

---

## `infrared-saunas`

**What changed:** the coming-soon bold stays, because it is a status disclosure and earns its
weight — but it moves into the exact position the Cold Plunge and Outdoor Furniture pages use,
after an opening observation rather than as a headline. "Register your interest below and we'll
notify you" plus the arrow link is dropped: it is promotional in register and, unless there is
a form on that page, it points at nothing. The consultation link is preserved, and a "what is
available today" block is added — the same device Outdoor Furniture uses to stop an empty
collection being a dead end.

```html
<p>Infrared heats the body directly rather than the air around it. The session runs cooler and longer than a traditional sauna, and the installation is simpler, which makes it viable in rooms where a steam sauna is not.</p>
<p><strong>Our infrared range is being finalised.</strong> We are applying the same tests we apply elsewhere: emitter type and coverage, cabin construction, published rather than claimed electromagnetic figures, and delivery to your address.</p>
<h2>If you are planning an infrared sauna now</h2>
<p>Tell us the room, the ceiling height and the supply available, and we will come back to you when we have something we can stand behind. <a href="/pages/consultation">Speak with a specialist</a>.</p>
<h2>What is available today</h2>
<p><a href="/collections/barrel-saunas">Barrel saunas</a> and <a href="/collections/cabin-saunas">cabin saunas</a> from Auroom, in electric and wood-fired configurations.</p>
```

---

## `outdoor-baths-hot-tubs` — Part 3 judgment

**Does it belong on a collection page?** Yes, mostly. The substance is genuinely good and it is
the most differentiated writing on the site — "the reduction of the world to the edge of a tub"
and "we do not list inflatable products or unbranded imports" are both exactly right for a
high-ticket buyer. What is wrong is not the content, it is the markup and one structural error.

**Is the voice consistent?** Closer than it first appears. It is longer and more explanatory
than the others, but the register — declarative, unhurried, willing to state what we refuse to
sell — is the same register as Cold Plunge. The parts that drift are the opening `<h2>Outdoor
Baths &amp; Hot Tubs — A Considered Guide</h2>`, which is a title, not a description, and which
duplicates the page's own H1 (a real on-page SEO fault, not just a cosmetic one), and
"products of equivalent craft and durability", which is slightly brochure-ish.

**Do the bold pseudo-labels stay?** Split decision, and the two halves go opposite ways.

- The three decision axes — Wood-fired vs electric, Material, Capacity — are structural, not
  decorative, and run-in labels are a legitimate catalogue device. They stay bold, but they
  move into a `<ul>` with the label at the head of each `<li>`. That is not a new invention: it
  is precisely the pattern Complete Bundles already uses and which reads clean. Putting them in
  a list is what makes the bold defensible rather than arbitrary.
- The five FAQ questions do **not** stay bold. A question in an FAQ is a heading — it is the
  one thing on this page that is genuinely a heading — and marking it up as bold body text is
  the single heaviest block of emphasis anywhere in the store. They become real `<h3>`s under an
  `<h2>`. This also makes the block eligible for FAQ structured data later, which bolded
  paragraphs are not.

**Also changed:** duplicate title heading removed; `<h3>` section headings promoted to `<h2>` to
match every other collection; intro cut by roughly a fifth; three internal links added, because
this and `outdoor-kitchens-1` were the only collection descriptions on the site with zero — a
real gap on a page this long.

**Theme coupling — read this before pasting.** `sections/vh-collection-guide.liquid:16` splits
the collection description on `<h3` and renders **every `<h3>` chunk as a collapsed `<details>`
accordion**. So the five FAQ questions below will render as five accordions, not as headings.
That is intended and it is a good outcome for an FAQ — but it has one consequence: anything
placed after the final `<h3>` is swallowed into that last accordion and hidden by default. The
closing "Further detail is in the FAQ / speak with a specialist" CTA has therefore been moved up
to sit after the Delivery and installation paragraph, before `<h2>Common questions</h2>`. Do not
move it back to the end — both of the page's high-intent links would disappear under "Is
white-glove placement available?". The `<h2>`-only structure of every other block on this page
is unaffected by the split.

**Longer term:** the five Q&As are the part that least belongs on a collection page. Once
`/pages/faq` carries them, cut the block here to two questions and link out. Not urgent.

```html
<p>There is a quality to bathing outdoors that no indoor room reproduces — warm water against cold air, the shift in atmosphere from dusk to dark, the reduction of the world to the edge of a tub. It is an old habit in Nordic and Japanese life, and the European market now builds for it properly.</p>
<p>Our range comes from a small number of manufacturers, selected against the criteria we apply across the store: construction quality, an honest materials specification, and documented performance in year-round outdoor use. Wood-fired cedar tubs for those who want the fire alongside the soak, and outdoor showers built for use after a <a href="/collections/saunas">sauna</a> or beside a pool. We do not list inflatable products or unbranded imports.</p>
<h2>Choosing a bath or tub</h2>
<ul>
<li><strong>Wood-fired or electric</strong> — wood-fired systems need no mains connection and suit rural or off-grid sites. They take two to three hours to reach temperature and reward the preparation. Electric systems hold a set temperature and are ready on demand.</li>
<li><strong>Material</strong> — Western red cedar is the standard: naturally rot-resistant, aromatic and dimensionally stable outdoors. Stainless steel reads more architectural and is easier to clean. Both carry warranties appropriate to outdoor exposure.</li>
<li><strong>Capacity</strong> — a standard cedar tub seats four to six adults. Consider the movement around the tub as well as the seating inside it.</li>
</ul>
<h2>Delivery and installation</h2>
<p>All baths and tubs ship by pallet freight on a date confirmed with you in advance. Wood-fired cedar tubs need a level base, a cold-water supply and a drainage solution; the full requirements are set out on each product page. We confirm access and placement by telephone before dispatch.</p>
<p>Further detail is in the <a href="/pages/faq">FAQ</a>, or <a href="/pages/consultation">speak with a specialist</a>.</p>
<h2>Common questions</h2>
<h3>Does a wood-fired hot tub require planning permission?</h3>
<p>Regulations vary. In most cases a freestanding garden installation does not require a permit, but we recommend confirming with your local authority.</p>
<h3>How long does a cedar tub last?</h3>
<p>Cedar tubs from reputable manufacturers regularly last 20 to 30 years with appropriate care. The staves expand and seal naturally when the tub is filled.</p>
<h3>How often should the water be changed?</h3>
<p>Without chemical treatment, weekly changes are advisable. With appropriate sanitisation, water can be held for longer.</p>
<h3>Can the tub be left outside in winter?</h3>
<p>Yes, provided it is either kept filled — the water weight stabilises the staves — or fully drained and dried. Winterisation guidance is included with delivery.</p>
<h3>Is white-glove placement available?</h3>
<p>Placement beyond the kerbside is quoted at the time of order, subject to access and terrain. Tell us the site conditions and we will confirm what is possible and what it costs.</p>
```

---

## `outdoor-kitchens-1` — flagged, not rewritten

The copy itself is fine. It is on-voice, has zero bold, and the closing one-word sentence
("Röshults.") is a good piece of writing. No edit needed.

The problem is that two live collections both called Outdoor Kitchens will compete with each
other in search, split any internal links you build, and let a buyer land on whichever one
Google prefers rather than the one you maintain. Recommendation: treat `outdoor-kitchens` as
canonical — it is the fuller entry and it carries the planning-guide link — and unpublish
`outdoor-kitchens-1` with a 301 redirect to `/collections/outdoor-kitchens`. Before you do,
check which handle current navigation, homepage sections and any live ads point at; if traffic
is going to `-1`, redirect in that direction instead and move the longer copy across. This is a
merchandising fix, not a copy fix, and is out of scope for this file.

---

## Please verify before publishing

**Product URLs** (only needed if you use the optional linked variant of the Barrel Saunas
second paragraph, and the two already in `saunas`):
- `/products/auroom-halo-barrel-sauna`
- `/products/auroom-luma-barrel-sauna`
- `/products/auroom-nora-outdoor-barrel-sauna`
- `/products/auroom-sola-square-barrel-sauna`

The first two are confirmed live in the Complete Bundles description. The Nora and Sola handles
came from your brief, not from live data — click them once before publishing.

**Factual points I carried over from the existing copy without independent confirmation:**

- **Halo and Luma sizes.** The live Barrel Saunas copy says Halo in 120/150/180cm diameters and
  Luma in 225/260/300cm lengths. Your brand brief says Halo has four sizes and Luma two. These
  disagree. I kept the live figures because they are on the customer-facing page today, but one
  of the two documents is wrong and it should be settled against the Auroom price list.
- **Auroom country of manufacture.** Live copy says Estonia; the brand brief says a Finnish
  brand manufacturing in Latvia and Estonia. I kept Estonia. Worth confirming — country of
  origin is a claim high-ticket buyers check.
- **HUUM and Harvia framing.** The original said "the two most trusted names in Scandinavian
  sauna heating". I softened it to "the two names Scandinavian sauna building keeps returning
  to" to avoid an unverifiable superlative. Adjust if you have a source for the stronger claim.
- **Thermally modified timber, applied to the whole `saunas` range.** The source states this for
  the **barrels only**; the cabin copy says nothing about timber treatment. The rewrite extends
  the claim to the cabin line as well. Confirm it holds for cabins, or narrow the sentence to
  the barrels — this is exactly the kind of materials claim a €14k buyer checks.
- **`fire-features` collection contents.** The first draft asserted "everything here is
  freestanding"; that was a categorical claim the source never made, and EcoSmart Fire does ship
  built-in fireboxes. It has been softened to describe the range rather than bound it. If the
  collection genuinely contains no built-in units, the stronger sentence is available again.
- **`sauna-accessories` scope.** The source said "accessories **and** heating equipment"; this
  rewrite is heater-led. If the collection also holds buckets, ladles, thermometers or stones,
  add a closing clause so the copy covers what is actually in the grid — e.g. append to the
  second paragraph: `We also stock the buckets, ladles, thermometers and stones that go with
  them.` If the collection is heaters-only today, no change is needed.
- **Electric heater 45–60 minute figure** and **230V rating** — carried over verbatim.
- **Cedar tub 20–30 year life, 4–6 adult capacity, 2–3 hour wood-fired heat-up** — all carried
  over verbatim from the existing Outdoor Baths copy.

**Two additions you may want to approve or remove:**

- I added an `<h2>Sizing a heater</h2>` block to `sauna-accessories` linking
  `/blogs/outdoor-living/outdoor-sauna-buying-guide`. It gives that page the structure every
  other collection has and adds one internal link. Delete the last two lines if you disagree.
- In `infrared-saunas` I wrote "published rather than claimed electromagnetic figures". EMF is a
  real infrared buying criterion and the line is a credible differentiator, but it commits you
  to actually publishing those figures when the range goes live. Cut it if you would rather not
  make the commitment.

**One thing I removed that you may want back:** the Infrared page's "Register your interest
below and we'll notify you when the range is live." If there is a working notify form on that
collection page, add a line pointing to it. If there is not, the line was promising something
the page did not deliver, which is why it went.

**Pre-existing contradiction on the Barrel Saunas page (not introduced here, but visible on the
same screen):** `sections/vh-collection-guide.liquid:117` hard-codes a comparison table that
asserts **Nora** has a porch, while both the old and the new description attribute the porch to
**Luma** only. Whichever is right, the page currently contradicts itself in two places a buyer
reads together. Worth fixing in the theme alongside this copy push.

**Brand names not asserted:** I did not name EcoSmart Fire in the Fire Features copy, although
both Complete Bundles and Outdoor Furniture already state it is your fire brand. If EcoSmart is
the sole brand in that collection, opening with a maker fact would be stronger and would mirror
the Outdoor Kitchens opener — e.g. "EcoSmart Fire builds freestanding bioethanol burners, fire
pits and fire bowls…". Confirm sole-brand status first.
