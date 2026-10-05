# The bad prompt

```
make me a landing page for my analytics app
```

That's it. That's the whole prompt.

## Why it fails

It isn't rude, or badly spelled, or too short in terms of word count. It fails
because **it contains no decisions**. Every question that matters is left open:

| The model has to guess | What it guessed | What you actually wanted |
|---|---|---|
| Who is this for? | "everyone" → generic copy | Heads of Product at B2B SaaS companies |
| What does the app do? | nothing specific → "fast, easy, secure" | Answers product questions from your warehouse |
| What's the brand? | default purple gradient | Warm paper + a sharp lime accent |
| Which sections? | the most common five | hero, proof, features, how, pricing, FAQ, CTA |
| Desktop or mobile first? | desktop, 960px fixed | mobile-first, fluid to 1140px |
| Plain HTML? React? Tailwind? | plain HTML, inline styles | semantic HTML + a tokenised stylesheet |
| Real copy or placeholder? | Lorem ipsum | real copy, in the product's voice |
| Accessibility? | not mentioned → not done | keyboard, contrast, landmarks, reduced motion |
| When is it done? | unknowable | the checklist at the end of the good prompt |

A model that has to guess nine times will guess "the statistical average of every
landing page on the internet." That average is a purple gradient, three emoji
feature cards, and John Doe, CEO.

**The output is not the model's fault. It answered the question that was asked.**

## The tell

If you can paste your prompt into a different project and it still makes sense,
your prompt is too vague. "Make me a landing page for my analytics app" would work
just as well for a dog-walking app. That's the problem.
