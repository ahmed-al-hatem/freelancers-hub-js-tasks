# The prompt matrix — a frontend teaching demo

Four landing pages for the **same product**, built by the **same model**, in the
**same session**. The only variable is the prompt.

Most "AI prompting" lessons teach a binary: vague prompt bad, detailed prompt good.
That's true but useless, because it doesn't tell a student **what** to be detailed
*about*. So these four pages split it along two independent axes:

|                     | **Requirements ❌** | **Requirements ✅** |
|---------------------|---------------------|---------------------|
| **Design ❌** | [`bad/`](bad/) — the one-liner. Ugly *and* broken. | [`requirements-only/`](requirements-only/) — works perfectly. Utterly forgettable. |
| **Design ✅** | [`design-only/`](design-only/) — gorgeous screenshot. Falls apart on a phone. | [`good/`](good/) — the one you'd ship. |

Two axes, four outcomes. Students can locate their own prompting habits on it,
which is the part that actually changes behaviour.

```
prompting-landing-pages/
├── index.html                    ← START HERE: live 2×2 with a width slider
├── bad/index.html                design ❌ requirements ❌
├── design-only/index.html        design ✅ requirements ❌   (single file, <style> block)
├── requirements-only/            design ❌ requirements ✅
│   ├── index.html
│   └── styles.css
├── good/                         design ✅ requirements ✅
│   ├── index.html
│   └── styles.css                commented in 16 sections for reading in class
├── prompts/
│   ├── bad-prompt.md
│   ├── design-only-prompt.md
│   ├── requirements-only-prompt.md
│   └── good-prompt.md
└── README.md
```

## Running it

```bash
cd prompting-landing-pages
python3 -m http.server 8000
# then open http://localhost:8000
```

Opening `index.html` directly usually works, but some browsers block `file://`
iframes — if the panes are blank, use the server.

---

## The four prompts in one line each

| Page | Prompt |
|---|---|
| `bad` | `make me a landing page for my analytics app` |
| `design-only` | A real art-direction brief — palette, type, spacing, reference feel. Nothing about behaviour. |
| `requirements-only` | The good prompt **with the art-direction block deleted**. Everything else identical. |
| `good` | Context → Constraints → Structure → Definition of done. |

The middle two are the interesting ones, and they're each a *reasonable* prompt.
Neither is lazy. Each is just half a brief — and each half fails differently.

---

## What each quadrant teaches

### `bad/` — design ❌ requirements ❌
**The lesson:** a prompt with no decisions in it gets you the statistical average
of every landing page on the internet.

That average is a purple gradient, three emoji feature cards, lorem ipsum, and
John Doe, CEO. Nothing on the page says what the product does — it could be a CRM,
a VPN, or a dog-walking app.

### `design-only/` — design ✅ requirements ❌
**The lesson:** a design brief describes the *surface*. You get a beautiful
screenshot of a website rather than a website.

At 1280px this is arguably the best-looking page in the folder — correct palette,
correct type, real rhythm. Then:

- `width: 1120px` fixed, **zero** media queries
- `font-size: 64px` hard-coded — one word is wider than a phone screen
- `<div class="btn">` — not focusable, not pressable, invisible to a keyboard
- `outline: none` on buttons and inputs
- body text `#A3A39B` on `#FAF9F5` ≈ **2.4:1** (AA needs 4.5:1)
- no `<label>`, no alt text, no `<header>`/`<main>`/`<footer>`
- no dark mode, no token layer — `#C6F24E` pasted in literally 30+ times

The sneaky detail: **the viewport meta tag is present.** Students often think that
tag *is* responsiveness. It isn't — it only stops the phone zooming out. Paired
with a fixed 1120px container, all it guarantees is that you see the broken layout
at full size.

### `requirements-only/` — design ❌ requirements ✅
**The lesson:** requirements describe what must be *true*. You get something
correct that nobody remembers.

Run the good prompt's checklist against it — it passes every line. No horizontal
scroll at 320px, full keyboard access, AA contrast in both themes, semantic
landmarks, working dark mode, real copy, every section in order. **It is more
shippable than the beautiful one.**

It's also `system-ui`, `#2563eb`, `#f8f9fa` cards with 6px radius, and one `.grid`
rule reused for features, steps, stats, pricing *and* the footer. Swap the logo and
it's a healthcare startup.

Say this part out loud in class: **this is what most AI-generated frontend actually
looks like**, because developers naturally prompt in requirements. They specify
behaviour, because behaviour is what they think about. Then they wonder why every
project comes out looking the same.

### `good/` — design ✅ requirements ✅
Both halves. Tokens, fluid `clamp()` type, `auto-fit` grids, dark mode from the
same tokens, skip link, `:focus-visible`, `prefers-reduced-motion`, working mobile
menu, real copy — *and* a palette and type system that belong to this product and
no other.

---

## The measurable diff

Numbers verified against the actual files, not asserted:

| | `bad` | `design-only` | `requirements-only` | `good` |
|---|---|---|---|---|
| viewport meta | ❌ | ✅ | ✅ | ✅ |
| media queries | 0 | **0** | 4 | 9 |
| `<h1>` count | 5 | 1 | 1 | 1 |
| inline `style=` | 58 | 7 | 0 | 0 |
| CSS custom properties | 0 | **0** | 20 | 35 |
| semantic landmarks | ❌ | ❌ | ✅ | ✅ |
| focusable CTAs | ❌ | ❌ | ✅ | ✅ |
| dark mode | ❌ | ❌ | ✅ | ✅ |
| body text contrast | 2.85:1 | **2.41:1** | 4.69:1 | 5.64:1 |

Note the `design-only` column: on the two rows a *screenshot* can show, it wins.
On every row a screenshot can't show, it ties with the worst page in the folder.

---

## Three demos that land hardest

1. **Drag the slider to 320px.** `bad` and `design-only` both need sideways
   scrolling to read one sentence. `design-only` breaking is the surprise —
   students assumed pretty meant finished.
2. **Press <kbd>Tab</kbd> repeatedly in each pane.** In `good` and
   `requirements-only` you reach every control and always see where you are. In
   `bad` and `design-only` the CTAs are simply unreachable — they're divs.
3. **Ask "which of these would you ship?"** before showing the 320px view. Most
   students pick `design-only`. Then break it. That gap between *looks finished*
   and *is finished* is the whole session in one move.

---

## Suggested 60-minute session

1. **(5 min)** Show `design-only` alone, full screen, at desktop width.
   *"Would you ship this?"* Let them say yes.
2. **(5 min)** Drag to 375px. Then <kbd>Tab</kbd> through it. Let that land.
3. **(3 min)** Reveal its prompt. It's a *good* brief — just half a brief.
4. **(5 min)** Show `bad/`. *"What's wrong with it?"* Collect answers on the board.
   Reveal the one-line prompt.
5. **(7 min)** Show `requirements-only`. It passes every test. Ask why it still
   feels wrong. This is the hardest one for students to articulate — that's why
   it's worth the time.
6. **(5 min)** Open the full 2×2. The matrix does the summarising for you.
7. **(10 min)** Read `prompts/good-prompt.md` together. Map each block of the
   prompt to something visible on the page.
8. **(12 min)** Walk `good/styles.css` sections 1–4 — tokens, reset, layout,
   buttons. Then diff it against `requirements-only/styles.css`: same skeleton,
   different decisions. This is where "modern CSS" becomes concrete.
9. **(8 min)** Land the point below, then set the homework.

---

## The point

> The model didn't get better across these four pages. **The instructions did.**
>
> And the two axes fail in opposite directions. Requirements without design gets
> you something correct and anonymous. Design without requirements gets you
> something beautiful and broken. You need both, every time, and neither one
> implies the other.
>
> You can only write instructions this specific for something you understand. The
> good prompt names `clamp()`, `auto-fit`, `prefers-reduced-motion`,
> `:focus-visible` and a 4.5:1 contrast ratio — you cannot ask for those if you've
> never learned them, and more importantly **you cannot tell whether you got them.**
>
> AI raised the floor for people who know frontend. It did nothing for people who
> don't. That's the job now: **be the person who writes the spec and reviews the
> output.**

## Homework

Pick any product. Write a prompt covering **both axes** —
*Context → Art direction → Structure → Constraints → Definition of done* — then
generate a page and audit your own result against the table above.

Bring the page **and** the prompt. We'll review the prompts, not the pages.
