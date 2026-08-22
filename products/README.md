# products/ — Product Data & Specifications

**Responsibility:** authoritative, non-invented product facts used by
`veldorahaven-product-experience` and consumers (PDP, collection, SEO). One file per
product or product family.

## Rules

- **Never invent specifications.** If a spec is unknown, record it as `TBD (source
  needed)` rather than guessing.
- Facts here should trace to a real source: the Shopify product, the manufacturer
  (Auroom) brochures/manuals in `AuroomWellness/`, or the pricing model workbook.
- Category-appropriate spec sets (see `veldorahaven-product-experience`): saunas
  (materials, capacity, heating, dimensions, installation, interior experience); outdoor
  kitchens (modules, appliances, materials, configurations, dimensions, installation,
  delivery, customization); cold plunges (temperature, capacity, filtration, materials,
  maintenance, installation); hot tubs / fire features accordingly.

## Suggested file shape

```yaml
product: Auroom Halo <variant>
category: sauna
shopify_gid: gid://shopify/Product/...
status: DRAFT|ACTIVE
specs: { material: , capacity: , heating: , dimensions: , ... }
sources: [AuroomWellness/..., Shopify]
open_questions: []
```

> Not yet populated. Populate from confirmed sources; align with existing Shopify
> product records rather than duplicating them.
