# The design-only prompt

**Design defined ✅ · Requirements undefined ❌**

```
Build a landing page for Pulse, an analytics SaaS.

Make it look like this:
- Warm off-white background (#FAF9F5), near-black text (#14171D)
- One accent colour: lime #C6F24E. Use it as a solid block colour —
  filled buttons, icon chips, badges. Never as a gradient.
- Type: Inter Tight for headings with tight negative letter-spacing,
  Inter for body text, JetBrains Mono for small labels and eyebrows
- Generous white space. Large headline. Soft shadows, 20px radius cards.
- Restrained and premium — think Linear, not a template marketplace.
- Add a product mock in the hero with a big number and a bar chart.
```

This is a **real** design brief. It is specific, it has a point of view, it rules
things out. It is also about 40% of a prompt.

## What it gets right

Honestly — a lot. Open it at 1280px and it is arguably the best-looking page in
this folder. The palette is correct, the type is correct, the spacing has rhythm,
the hero mock is attractive. If you judged it from a screenshot you would ship it.

**That is exactly why this quadrant is dangerous.**

## What it never mentions, and therefore never gets

| Never asked for | What happened instead |
|---|---|
| Mobile / responsive behaviour | `width: 1120px` fixed, **zero** media queries |
| A type scale that adapts | `font-size: 64px`, fixed, at every viewport |
| Semantic HTML | `<div>` for the header, nav, sections and footer |
| Keyboard access | `<div class="btn">` — not focusable, not pressable |
| Focus styles | `outline: none` on buttons and inputs |
| Contrast ratios | body text `#A3A39B` on `#FAF9F5` ≈ **2.4:1** (needs 4.5:1) |
| Form labels | placeholder-only input, no `<label>` |
| Alt text | the hero mock is invisible to a screen reader |
| Which sections to include | the model's default four; no proof, no how-it-works, no FAQ |
| What the product actually does | "Analytics, reimagined." "Zero friction." Words that mean nothing |
| A token layer | `#C6F24E` pasted in literally, 30+ times |
| Dark mode | doesn't exist |

## The trap

> A design brief describes the **surface**. Requirements describe the **behaviour**.
> A model given only the first will produce a beautiful screenshot of a website
> rather than a website.

Note the detail that makes this quadrant sneaky: **the viewport meta tag is
present.** The model included it out of habit. Students often think that tag *is*
responsiveness. It isn't — it only tells the phone not to zoom out. With a fixed
1120px container, all the tag achieves is guaranteeing you see the broken layout
at full size instead of a shrunken-but-complete one.

## Where you'll meet this in real life

This is what happens when a designer hands over a Figma file and nobody writes a
ticket. The pixels are decided; the behaviour is assumed. Then it reaches QA on a
phone and the sprint has three days left.

**Demo in class:** show it at 1280px first and ask *"would you ship this?"*
Most students say yes. Then drag to 375px, then press <kbd>Tab</kbd>.
