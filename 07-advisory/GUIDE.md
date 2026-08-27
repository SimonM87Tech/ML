# Advisory

The consulting layer: turning ML skill into paid engagements. Read after Phase 1, reread after Phase 5.

## The advisor's core loop

1. **Diagnose** — what business decision are they trying to improve? (Not "what model do they want.")
2. **Map** — does data exist for it? Labeled? How much? How clean?
3. **Recommend** — cheapest thing that could work: buy/API/prompt → classical ML → deep learning → custom research. In that order.
4. **Scope** — small paid pilot with a measurable success criterion, then the real project.

## When NOT to build a model (saying this earns trust and referrals)

- The decision could be a rule: "flag orders over ₪5,000 from new accounts" needs an `if`, not a model.
- No labeled data and labeling is expensive → scope a data-collection phase first, or walk away.
- An existing API/product already solves it (OCR, transcription, translation, generic vision).
- The business impact of a correct prediction is too small to cover the build + maintenance cost.

## Scoping questions for every client meeting

- What decision will this prediction change, and what's a wrong prediction cost? (Chooses the metric — precision vs recall — for you.)
- Where does the data live, who owns it, how far back does it go?
- How will we know it worked? Get a number they agree to *before* building.
- Who maintains it after handoff? (Retainer conversation.)
- Latency/privacy constraints? (On-prem fine-tuned model vs cloud API.)

## Engagement shapes that fit M87

- **AI audit** (1–2 weeks, fixed price): inventory their data + processes, deliver a ranked list of ML opportunities with effort/impact estimates. Low risk for them, great funnel into builds.
- **Pilot model** (2–4 weeks): one problem, one metric, works-on-their-data proof. Success criterion agreed upfront.
- **Production build** (1–3 months): pilot model + serving + monitoring (your `06-mlops` advantage).
- **Retainer**: monitoring, retraining, and next-opportunity scouting.

## Credibility assets to build as you go

Each mission should end with a short case-study writeup (problem → approach → honest numbers → business framing). Three of those beat any certificate. Your existing client work (Gentrix RAG, Zesty optimization, VeryChess) already counts as AI delivery — frame it that way.

## What to master

Explaining every technique in this workspace in two sentences a CFO understands. The missions' "explain-back" checkpoints train exactly this.
