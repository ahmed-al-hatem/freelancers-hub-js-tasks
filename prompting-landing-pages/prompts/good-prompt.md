# The good prompt

Same model. Same task. Roughly ninety seconds more typing.

```
Build a landing page for Pulse, a product-analytics SaaS.

CONTEXT
- Audience: Heads of Product and PMs at B2B SaaS companies, 50-500 employees.
  They're technical enough to read a chart, not technical enough to write SQL.
  Their pain: every product question becomes a ticket for the data team.
- Positioning: "answers the question, not the query." Pulse reads their existing
  warehouse and returns the chart + the affected cohort + ranked likely causes.
- Competitors are Amplitude and Mixpanel. Do NOT look like them: no indigo/violet,
  no glassmorphism, no floating 3D blobs.
- Goal of the page: get a work email into the trial form. One primary CTA,
  repeated at top, middle and bottom.

BRAND + ART DIRECTION
- Warm off-white paper (#FAF9F5), near-black ink text, one sharp accent: lime #C6F24E.
- Accent is used as a BLOCK colour (filled buttons, badges, icon chips), never as
  a gradient and never as body text.
- Type: Inter Tight for headings (tight negative tracking), Inter for body,
  JetBrains Mono for labels, eyebrows and numbers.
- Tone: confident, concrete, slightly dry. No exclamation marks. No "revolutionise".
- Reference feel: Linear's restraint, not a template marketplace.

SECTIONS, IN ORDER
1. Sticky header — logo, 4 nav links, "Sign in" + "Start free"
2. Hero — eyebrow badge, H1, 2-line subhead, dual CTA, trust line,
   and a product mock on the right showing a real question and its answer
3. Logo bar — 6 fictional customer names
4. Features — 4 cards, each with an inline SVG icon (no emoji, no icon font)
5. How it works — 3 numbered steps
6. Metrics band — 4 numbers on a dark panel
7. Testimonial — one quote, attributed, with initials avatar
8. Pricing — 3 tiers, middle one highlighted
9. FAQ — 4 questions, native <details>/<summary>
10. Final CTA — email capture
11. Footer — 3 link columns

COPY
Write real copy, in the voice above. No lorem ipsum, no "John Doe",
no "we are the best". Specific claims with specific numbers.

TECHNICAL CONSTRAINTS
- Plain HTML + CSS + a little vanilla JS. No frameworks, no build step, no CDN
  except Google Fonts. Two files: index.html and styles.css.
- Mobile-first. Base styles are the phone layout; media queries only add.
- Design tokens as CSS custom properties: colour, spacing scale, radius, type.
  No magic numbers in component rules.
- Fluid type with clamp(). Grids with repeat(auto-fit, minmax(...)), not
  breakpoint-by-breakpoint column counts.
- Dark mode via prefers-color-scheme, driven by the same tokens.
- Semantic HTML: header/nav/main/section/footer, one h1, headings in order.
- Accessibility: skip link, visible :focus-visible rings, labelled form field,
  aria-expanded on the mobile menu toggle, alt/aria-label on the product mock,
  body text contrast at least 4.5:1 in both themes.
- Respect prefers-reduced-motion: kill the scroll reveal and hover transforms.
- The mobile menu must actually open and close.

DEFINITION OF DONE
- No horizontal scroll at 320px.
- Readable and correctly laid out at 320 / 768 / 1440px.
- Every interactive element reachable and operable by keyboard alone.
- Nothing in the page is a placeholder.

Comment the CSS in sections so a student can read it top to bottom.
```

## What each block is doing

| Block | Job | What breaks without it |
|---|---|---|
| **Context** | Tells the model *who is reading and why* | Generic copy aimed at nobody |
| **Brand + art direction** | Removes the aesthetic guess | The default purple gradient |
| **Negative constraints** (`do NOT look like`) | Rules out the average | Looks like every other SaaS page |
| **Sections, in order** | Makes the structure yours, not the model's | Random five-section template |
| **Copy instruction** | Forbids filler | Lorem ipsum, John Doe |
| **Technical constraints** | Encodes your team's standards | Inline styles, magic numbers, no dark mode |
| **Definition of done** | Gives the model something to check against | "Responsive" that isn't |

## The pattern to remember

> **Context → Constraints → Structure → Definition of done.**

Everything above fits that shape. It is not about length — it is about how many
decisions you made *before* pressing enter. A model can only be as specific as
you were.

## What is still yours to do

The good prompt gets a strong first draft, not a finished product. You still:
- check it at 320px yourself
- tab through it with the keyboard
- fix the two or three things you disagree with
- and **know enough CSS to tell whether the output is good**

That last one is the whole reason this course exists. A prompt is a spec, and you
can only write a spec for something you understand.
