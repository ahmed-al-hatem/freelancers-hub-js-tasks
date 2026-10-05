# The requirements-only prompt

**Requirements defined ✅ · Design undefined ❌**

```
Build a landing page for Pulse, a product-analytics SaaS.

Audience: Heads of Product at B2B SaaS companies. Their pain is that every
product question becomes a ticket for the data team. Pulse reads their
warehouse and returns the chart + the affected cohort + ranked likely causes.

SECTIONS, IN ORDER
header, hero with product panel, customer logos, 4 features, 3-step
how-it-works, 4 metrics, testimonial, 3-tier pricing, 4-question FAQ,
email capture, footer with 3 link columns.

COPY
Real copy in the product's voice. No lorem ipsum, no "John Doe",
no "we are the best". Specific claims with specific numbers.

TECHNICAL
- Plain HTML + CSS + vanilla JS. index.html + styles.css.
- Mobile-first. Base styles are the phone layout; media queries only add.
- Design tokens as CSS custom properties. No magic numbers in component rules.
- Fluid type with clamp(). Grids with repeat(auto-fit, minmax(...)).
- Dark mode via prefers-color-scheme from the same tokens.
- Semantic HTML: header/nav/main/section/footer. One h1. Headings in order.
- Accessibility: skip link, :focus-visible rings, labelled form field,
  aria-expanded on the menu toggle, aria-label on the product panel,
  body text contrast >= 4.5:1 in both themes.
- Respect prefers-reduced-motion. The mobile menu must actually open and close.

DEFINITION OF DONE
- No horizontal scroll at 320px.
- Correct at 320 / 768 / 1440px.
- Every interactive element reachable by keyboard alone.
- Nothing in the page is a placeholder.
```

Notice what this is: **the good prompt with the entire art-direction block
deleted.** That is the only difference. Everything else is identical.

## What it gets right — all of it

Run the checklist. It passes every line:

- ✅ No horizontal scroll at 320px
- ✅ Tab reaches every control, focus is always visible
- ✅ Contrast passes AA in light **and** dark mode
- ✅ Semantic landmarks, one `h1`, headings in order
- ✅ Labelled form field, working `aria-expanded` menu
- ✅ Dark mode, driven by the same tokens
- ✅ Real copy, no placeholders
- ✅ Every section you asked for, in the order you asked

Measured against the definition of done, **this page is a pass.** It is genuinely
shippable. It is more shippable than the beautiful one.

## What it never gets

A reason to look at it.

| Decision nobody made | The default that filled the gap |
|---|---|
| Palette | `#2563eb` — the default blue, on `#f8f9fa` grey |
| Typeface | `system-ui` — whatever the visitor's OS decides |
| Hierarchy | size and boldness only; no tracking, no weight contrast, no colour |
| Composition | one `.grid` reused for features, steps, stats, pricing *and* the footer |
| Rhythm | uniform `--space-7` between every section |
| Personality | none was requested, so none arrived |

Swap the logo and the copy and this is a healthcare startup, a logistics tool, a
tax filing service. There is nothing in the pixels that belongs to Pulse.

## The trap

> Requirements describe what must be **true**. Design describes what must be
> **felt**. A model given only the first will build something correct that
> nobody remembers.

## Where you'll meet this in real life

This is the internal tool that works perfectly and that everyone quietly hates.
It is also — and say this part out loud to the class — **what most AI-generated
frontend actually looks like**, because developers naturally prompt in
requirements. They specify behaviour, because behaviour is what they think about.
Then they wonder why every project comes out looking the same.

The default blue is not the model having bad taste. It is the model having
**no instructions**, and defaulting to the average of its training data.
