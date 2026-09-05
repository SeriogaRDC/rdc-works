# Research Synthesis: The 4-AI Method
*How one human + four AI models produced a professional-grade investment analysis — and what we learned about each model's "personality."*

## The Problem

Real financial decisions need more than one opinion. But consulting four different AIs manually, keeping track of who said what, spotting where they disagree, and synthesizing it all — that's hours of copy-paste work most people never do. So most people get ONE AI's opinion and call it research.

We built a better loop.

## The Method

1. **Frame the question** with full personal context (holdings, constraints, goals) — written once, reused
2. **Ask each AI in its own UI** (browser automation via CDP — no APIs, no costs, the real logged-in experience)
3. **Capture full responses** — including the model that keeps writing after you think it's done (it always knows more)
4. **Compare structurally**: where do all four agree? Where does one dissent? What did three miss that one caught?
5. **Synthesize with attribution** — consensus items become high-confidence, unique findings get flagged for verification
6. **Write the final report** with disagreements preserved, not averaged away

## Case Study: Norwegian Portfolio Rebalancing (Sept 2026)

**Input:** Real holdings — 11 funds (73% tech concentration), cash position, mortgage, property situation.

**The four voices:**

| AI | Strength shown | Unique contribution |
|----|---------------|---------------------|
| ChatGPT | Clean structure, verified sources | Found the tax-free switching rule, named the exact defense fund (ISIN included) |
| DeepSeek | Math precision, 80+ sources | Caught a double-counting error in allocation, corrected remaining-cash arithmetic, suggested gold pairing for defense satellite |
| Claude | Epistemic honesty, gap-spotting | Identified the missing "third bucket" for 3-5 year needs (hardware + renovation costs) |
| Kimi | Norwegian tax depth (31 sources searched) | **The game-changer:** found the wealth tax layer everyone missed — ASK is tax-DEFERRED not tax-free (37.84% exit), the proportional debt reduction rule, rental-income timing effects |

**Key lesson:** The first three AIs agreed on a plan. The fourth demolished half of it with primary-source tax law. **Consensus without diversity is just shared blind spots.**

## What We'd Sell

The same method, pointed at your domain:
- Technology/vendor selection (compare 4 AIs' takes on Build-vs-buy)
- Market research with cross-validation
- Due diligence summaries with disagreement flags
- Policy/regulation analysis in specialized jurisdictions

**Deliverable:** synthesis report with per-source attribution, confidence levels, and a "what nobody agrees on" section.

## Honest Limitations

- Browser automation needs the human's logged-in sessions (we use the operator's own machine with consent)
- Rate limits and UI changes require maintenance
- Web-search-backed models can still hallucinate specifics — critical facts get manually verified against primary sources
