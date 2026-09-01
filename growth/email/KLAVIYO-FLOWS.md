# VeldoraHaven — Klaviyo Email Flows

**Created:** 2026-08-31  
**KPIs unlocked:** G5, G6  
**Phase:** 1 — Commercial Foundation  
**Status:** DRAFT — ready to import once Klaviyo confirmed live (see queue #18)

---

## FLOW 1 — WELCOME SEQUENCE (2 emails)

**Trigger:** Subscribe to list (footer signup or popup)  
**Delay:** Email 1 → immediate; Email 2 → 3 days after Email 1

---

### Email 1 — Welcome (send immediately on subscribe)

**Subject:** Welcome to VeldoraHaven — where Scandinavian wellness meets your garden  
**Preview text:** A different way to think about outdoor living.

---

Hi {{first_name|default:"there"}},

Thank you for subscribing to VeldoraHaven.

We exist for one reason: to bring the kind of outdoor wellness experience that Scandinavians have built their lives around — to gardens across Europe.

That means premium barrel saunas, built for the outdoors, designed without compromise.

Every product we carry is vetted, EU-made where possible, and backed by proper warranty and support. We don't sell things we wouldn't put in our own garden.

Over the next few days, we'll share a few things worth knowing — about sauna culture, about choosing the right setup for your space, and about how the process works from first enquiry to first steam.

In the meantime, if you have a question — about sizing, installation, delivery, or anything else — reply to this email. We read every one.

[Explore our sauna collection →](https://www.veldorahaven.com/collections/barrel-saunas?utm_source=klaviyo&utm_medium=email&utm_campaign=welcome-flow&utm_content=email1-cta)

Warmly,  
The VeldoraHaven team

---

### Email 2 — Product education + CTA (3 days later)

**Subject:** Which barrel sauna is right for your garden?  
**Preview text:** Two people or six — the answer changes the model.

---

Hi {{first_name|default:"there"}},

The most common question we get: *which size?*

Here's a quick way to think about it:

**For 2–4 people** — the Auroom Luma (240cm) is our most popular. It fits comfortably in most gardens, requires no planning permission in most EU countries, and is available as a DIY kit or fully pre-assembled.

**For 4–6 people** — the Auroom Nora (250cm diameter) or Sola (250cm diameter) gives you the space for a proper group session without crowding.

**For a smaller footprint** — the Auroom Halo (140–180cm) delivers the full sauna experience in a compact form factor that fits almost any garden.

All are Estonian-made. All are available with electric or wood-fired heaters. All ship directly to your address.

[See the full barrel sauna range →](https://www.veldorahaven.com/collections/barrel-saunas?utm_source=klaviyo&utm_medium=email&utm_campaign=welcome-flow&utm_content=email2-range)

Or if you'd rather talk through the options first:  
[Book a quick consultation →](https://www.veldorahaven.com/pages/consultation?utm_source=klaviyo&utm_medium=email&utm_campaign=welcome-flow&utm_content=email2-consult)

The VeldoraHaven team

---

## FLOW 2 — ABANDONED CART (3 emails)

**Trigger:** Customer adds to cart but does not complete checkout  
**Delays:** Email 1 → 1 hour; Email 2 → 24 hours; Email 3 → 72 hours

---

### Cart Email 1 — Reminder (1 hour)

**Subject:** You left something behind  
**Preview text:** Your {{cart_item_names}} is still waiting.

---

Hi {{first_name|default:"there"}},

It looks like you started an order but didn't complete it.

Your cart still has **{{cart_item_names}}** in it — and we've held it for you.

If you ran out of time, or had a question come up, you can pick up exactly where you left off:

[Return to your cart →]({{abandoned_checkout_url}})

If something gave you pause — delivery, assembly, sizing — reply here and we'll give you a straight answer.

The VeldoraHaven team

---

### Cart Email 2 — Trust + education (24 hours)

**Subject:** A few things worth knowing before you decide  
**Preview text:** Delivery, assembly, warranty — answered honestly.

---

Hi {{first_name|default:"there"}},

Before a purchase like this, it's reasonable to want certainty. Here are the most common questions — answered plainly.

**How does delivery work?**  
Your sauna ships directly from the Auroom factory in Estonia. Typical lead time is 4–8 weeks. Delivery is kerbside to your address. We confirm every detail before dispatch.

**What's involved in assembly?**  
The DIY kit requires two people and approximately 1–2 days. Full written instructions and video guides are included. Pre-assembled options are also available — they arrive ready to connect and use.

**What warranty applies?**  
All Auroom products come with a manufacturer warranty covering materials and construction defects. We handle any warranty claims directly.

**Can I pay in instalments?**  
We accept all major cards. Payment plans may be available — contact us to discuss.

Still thinking? We're here:  
[Talk to us first →](https://www.veldorahaven.com/pages/consultation?utm_source=klaviyo&utm_medium=email&utm_campaign=abandoned-cart&utm_content=email2-consult)

Or go ahead when you're ready:  
[Complete your order →]({{abandoned_checkout_url}})

The VeldoraHaven team

---

### Cart Email 3 — Consultation offer (72 hours)

**Subject:** Would it help to talk it through?  
**Preview text:** No pressure. Just a conversation.

---

Hi {{first_name|default:"there"}},

We noticed you haven't completed your order yet. That's completely fine — a sauna is a considered purchase, and we'd rather you feel certain than rush.

If there's anything specific holding you back — sizing, site prep, budget, delivery logistics — we're happy to talk it through directly.

No sales script. Just honest answers.

[Book a short consultation →](https://www.veldorahaven.com/pages/consultation?utm_source=klaviyo&utm_medium=email&utm_campaign=abandoned-cart&utm_content=email3-consult)

Or if you're ready:  
[Return to your cart →]({{abandoned_checkout_url}})

The VeldoraHaven team

---

## FLOW 3 — POST-PURCHASE SEQUENCE (2 emails)

**Trigger:** Order placed (purchase event)  
**Delays:** Email 1 → immediately (order confirmation supplement); Email 2 → 21 days after delivery (estimated)

---

### Post-Purchase Email 1 — Order confirmation supplement (immediate)

**Subject:** Your VeldoraHaven order is confirmed — here's what happens next  
**Preview text:** Everything you need to know about your delivery and assembly.

---

Hi {{first_name|default:"there"}},

Your order is confirmed. Thank you for choosing VeldoraHaven.

Here's what to expect:

**1. Order processing (1–3 business days)**  
We'll confirm your order with the Auroom production team and send you a dispatch notification with estimated delivery window.

**2. Delivery (4–8 weeks typically)**  
Your sauna ships from Estonia. You'll receive tracking details ahead of dispatch. Delivery is kerbside — please ensure vehicle access to your delivery address.

**3. Assembly**  
If you ordered a DIY kit: your assembly guide and hardware are included in the delivery. Set aside 1–2 days with a helper. If you ordered pre-assembled: your unit arrives built and requires only connection to your power supply.

**4. First use**  
Before your first session, season your heater stones at low temperature for 1 hour. This is explained in full in the care guide included with your delivery.

Any questions in the meantime — reply here. We'll respond promptly.

The VeldoraHaven team

---

### Post-Purchase Email 2 — Care guide + review request (21 days after order)

**Subject:** How's the sauna? (+ a care note for your first season)  
**Preview text:** Protect the wood, extend the life.

---

Hi {{first_name|default:"there"}},

We hope your sauna is everything you wanted.

A few notes for the first season that make a real difference to longevity:

**Wood care**  
Untreated spruce or pine will grey naturally outdoors. If you prefer to preserve the original colour, apply a breathable, UV-resistant exterior wood oil (not varnish — it traps moisture) in the first 2–3 weeks after installation. Reapply annually.

**Interior**  
Keep the interior untreated — no oils or varnishes inside. After each session, leave the door ajar for 20–30 minutes to allow moisture to escape.

**Heater stones**  
Inspect stones every 6 months. Replace any that have cracked or crumbled — fractured stones reduce efficiency and can spit.

**Winter use**  
Your Auroom is designed for year-round outdoor use in Northern European climates. Winter sessions are entirely normal. After heavy snowfall, clear the snow from the roof to reduce long-term structural load.

---

If your experience has been good, we'd genuinely appreciate a review — it helps other buyers make a confident decision.

[Leave a review →](https://www.veldorahaven.com?utm_source=klaviyo&utm_medium=email&utm_campaign=post-purchase&utm_content=review-cta)

Thank you for choosing VeldoraHaven.

The VeldoraHaven team

---

## IMPLEMENTATION NOTES

- Replace all `{{abandoned_checkout_url}}` with Klaviyo's built-in checkout URL variable
- Replace `{{first_name}}` and `{{cart_item_names}}` with Klaviyo profile/event properties
- Review request link → update to Judge.me review link once configured
- Consultation links → update to final URL once `/pages/consultation` is live
- All email links must include UTM parameters (convention defined in ANALYTICS-PLAN.md)

---

*Ready to import into Klaviyo. Activate once queue #18 (Klaviyo verification) is confirmed.*
