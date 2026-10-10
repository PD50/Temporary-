# Instacart Agent-Readiness — Deck Content & Layout Spec (v2)
*Reading deck: 13 slides + appendix, 16:9 (1920 × 1080). Every word in quotes or inside a block is final slide copy. Text in *(italics)* is a layout instruction, not slide copy.*

**What changed from v1:** your per-question structure is built in (Q1–Q6 + NSM). Q3, Q4 and Q5 are now two slides each. Every question slide opens with the brief's own question. Q2 uses a pre-mortem. Q3 gains a "when would checkout win?" what-if exhibit. Q4 uses a fishbone plus 5 Whys. Q5 has a sourced guesstimate and a precision/recall matrix. Q6 adds a situation analysis. The roadmap slide is gone; its "what we're not doing" moved to the exec summary.

---

## Part A — Design system (paste into Figma Make first)

### A1. Master prompt
> Design a 16:9 presentation slide at 1920×1080 for a consulting-style *reading* deck. It will be exported to PDF and read without a presenter, so it should be dense but scannable. Use Inter only. Margins 64 px left/right, 48 px top/bottom; a 12-column grid with 24 px gutters.
> **Fixed chrome on every content slide, top to bottom:**
> (1) **Nav bar**, 40 px tall, full width, nine text tabs: Summary · Context · Q1 Market · Q2 Demo · Q3 Build · Q4 Contract · Q5 Guardrails · Q6 Risk · Metrics. The active tab is a filled pill in #003D29 with white text; inactive tabs are #6B7280 at 13 px. A 2 px #003D29 rule sits under the bar.
> (2) **Question strip** (question slides only): a 1-line-high #F3F4F6 bar with a bold "THE QUESTION ·" label followed by the question text verbatim, 13 px italic #374151, max 2 lines.
> (3) **Action title**: 32 px, bold, #1A1A1A, max 2 lines.
> (4) **Takeaway line**: 17 px, medium, #0A8A0A, max 2 lines.
> (5) **Pillar chips**, top-right of the title area: rounded tags LEGIBLE #2563EB, BOUNDED #0A8A0A, REVERSIBLE #D97706, ACCOUNTABLE #7C3AED (white 11 px caps).
> (6) **"So what" callout** at the bottom: full-width box, #FFF4EC background, 6 px #FF7009 left border, a bold "SO WHAT →" label, then one sentence at 16 px.
> (7) **Footer**: 10 px #6B7280 source line on the left, page number on the right.
> **Components:** panels are #F6F7F5, 12 px radius, no shadow. Table headers are #003D29 with white 13 px bold text; body cells 12–14 px with 1 px #E5E7EB lines. Heat-map cells: 8–10 #D1FAE5, 5–7 #FEF3C7, 1–4 #FEE2E2. The recommended row or column gets a 2 px #0A8A0A outline and a small "RECOMMENDED" tag. Code blocks use JetBrains Mono 12–13 px on #0F172A with light text. Max two accent colours per slide besides the pillar chips. Prefer tables, matrices and diagrams to bullets; no text box over ~80 words.

### A2. Per-slide prompt template
> Using the design system above, build slide [N]. Active nav tab: [TAB]. Pillar chips: [CHIPS]. Layout: [paste the LAYOUT sketch]. Content: [paste the blocks exactly]. Keep all copy verbatim; don't add or rewrite text. Render tables as real tables, not images.

Build one slide per prompt. The densest slides are 5, 8, 11 and 12; expect to tighten their fonts by hand.

### A3. Block legend
`[Q]` question strip · `[TITLE]` action title · `[TAKEAWAY]` · `[TABLE]` · `[CHART]` · `[DIAGRAM]` · `[CARD]` · `[CODE]` · `[QUOTE]` · `[CALLOUT]` · `[FOOTER]`

---

## Part B — Storyline check (titles only)

1. Making Instacart Agent-Ready: The Delegation Contract
2. Agents earn autonomy only as fast as Instacart makes intent legible, bounded, reversible and accountable
3. The agent isn't ours: Instacart controls only the contract and the guardrails, so we design for three users
4. **Q1** — Groceries score 91.5% on agentic readiness and lead on every criterion, so they're the right place to start under any weighting
5. **Q2** — Push back on the scope, not the date: the board gets its demo in six weeks, built on the real foundation
6. **Q3** — Pick the Substitution-Preference API: in grocery, substitution is the leak, and checkout already has a working path
7. **Q3** — Two engineers can ship a v1 Substitution-Preference API in four weeks, seeded with data only Instacart has
8. **Q4** — Neither agent is wrong: the root cause is a design error, a contract built for humans who see context and consumed by agents who don't
9. **Q4** — Make the contract strict, make the server read back what it understood, and certify agents before they can write
10. **Q5** — Start at 5 autonomous orders per user per month — a weekly shop plus one top-up — because a missed bad order costs far more than an extra question
11. **Q5** — Above any limit the agent asks, it isn't blocked: six layers of guardrails that loosen only when the data earns it
12. **Q6** — Yes, take it seriously: they stalled on the problems we've built for first, and here's exactly where we're still exposed
13. One North Star, Trusted Agent Orders, driven by four input dimensions and kept honest by counter-metrics with hard thresholds

---

## Part C — Slide-by-slide content

---

### SLIDE 1 — Cover
*No nav bar, no question strip, no chips, no so-what box.*

**LAYOUT**
```
┌──────────────────────────────────────────────────────────────┐
│  [EYEBROW]                                                   │
│  [TITLE]                               ┌─────────────────┐   │
│  [SUBTITLE]                            │  [DIAGRAM]      │   │
│  [THESIS LINE]                         │  delegation flow│   │
│                                        └─────────────────┘   │
│  [Name · ID · College]                         [glance logo] │
└──────────────────────────────────────────────────────────────┘
 Left 55%: text on white. Right 45%: #003D29 panel with the diagram.
```

**[EYEBROW]** "InMobi Glance · APM Case Study · Shortlist Round · October 2026"

**[TITLE]** "Making Instacart Agent-Ready"

**[SUBTITLE]** "The Delegation Contract: six decisions for letting a user's AI assistant shop on their behalf"

**[THESIS LINE]** *(16 px italic #6B7280)* "Being agent-ready isn't about letting agents click faster. It's about making a user's intent legible, bounded, reversible and accountable, so an agent Instacart doesn't own can act on it safely."

**[DIAGRAM]** *(horizontal flow, white line icons on the dark panel)* "User" → "Phone's AI assistant" → **"Instacart contract layer"** *(highlighted box made of 4 stacked chips: LEGIBLE · BOUNDED · REVERSIBLE · ACCOUNTABLE)* → "Shopper & store" → "Doorstep"

**[NAME BLOCK]** "[Your Name]" / "[Roll No.] · [College]"

---

### SLIDE 2 — Executive Summary
*Nav: Summary · Chips: all four · No question strip.*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌LEGIBLE─┐ ┌BOUNDED─┐ ┌REVERSIBLE┐ ┌ACCOUNTABLE┐   4 cards     │
│ ┌ TABLE: Q | Question | Our answer | Slide | Pillar ────────┐ │
│ │ 6 rows                                                    │ │
│ └───────────────────────────────────────────────────────────┘ │
│ ┌ WHAT WE'RE DELIBERATELY NOT DOING (one slim strip) ───────┐ │
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[TITLE]** "Agents earn autonomy only as fast as Instacart makes intent legible, bounded, reversible and accountable"

**[TAKEAWAY]** "Instacart doesn't own the agent. It owns the contract the agent reads and the guardrails the agent can't bypass, so that's where every decision below is made."

**[CARDS — The Delegation Contract]** *(4 equal cards, top border in the pillar colour)*

| Pillar | Card body | Card footer: Instacart's lever |
|---|---|---|
| **LEGIBLE** | "Every field, unit and preference has exactly one machine meaning." | "Schema, enums, MCP tool descriptions" |
| **BOUNDED** | "Agents act only inside limits the user has set." | "Preference API, spend and frequency caps" |
| **REVERSIBLE** | "Every agent mistake is cheap to undo." | "Cancel window, one-tap Undo" |
| **ACCOUNTABLE** | "Every agent action is attributable, logged and explainable." | "Signed mandates, per-platform monitoring" |

**[TABLE — Six decisions]** *(column widths 5% / 20% / 57% / 6% / 12%)*

| # | Question | Our answer | Slide | Pillar |
|---|---|---|---|---|
| Q1 | Why start with groceries? | "Groceries score **91.5%** on our Agentic Readiness Score and lead on all five criteria, so they win under any weighting. Mistakes are cheap, frequent and visible." | 4 | REVERSIBLE |
| Q2 | Build the flashy demo, or push back? | "**Push back on the scope, not the date.** 80% of capacity stays on production APIs; 20% builds a demo layer on top of them. The flashy feature appears only as a labelled prototype." | 5 | ACCOUNTABLE |
| Q3 | Checkout API or Substitution-Preference API? | "**Substitution-Preference API** (4.50 vs 2.75). Checkout already works via ACP; substitutions happen ~once per order. We'd flip if agent checkout success fell below 90%." | 6–7 | BOUNDED |
| Q4 | Why do agents read `quantity: 2` differently? | "**A design error in our contract**, not a bad agent. Make units mandatory, match on `product_id`, read back what the server understood, and certify agents before they can write." | 8–9 | LEGIBLE |
| Q5 | Orders-per-user-per-month threshold? | "**5 autonomous orders/month** (weekly shop + 1 top-up). Above it the agent asks for one-tap approval; it isn't blocked. Loosen only while the unintended-order rate stays below 0.5%." | 10–11 | BOUNDED · REVERSIBLE |
| Q6 | "Should we be worried?" | "**Yes, honestly.** They stalled on grocery's known hard problems, which we've built for first. Here's where we're still exposed, and the three signals we'll review with you every week." | 12 | ACCOUNTABLE |

**[STRIP — What we're deliberately not doing]** *(slim grey strip, 3 items separated by dots)* "**Deliberately not doing:** building a custom checkout protocol (we adopt ACP/AP2) · shipping the flashy demo feature to production · letting agents substitute allergen-flagged items without asking"

**[CALLOUT]** "SO WHAT → Each answer trades a little speed now for trust that compounds: an agent gets more autonomy every time the data shows it hasn't misused what it already has."

**[FOOTER]** "ACP = Agentic Commerce Protocol (OpenAI/Stripe) · AP2 = Agent Payments Protocol (Google) · MCP = Model Context Protocol. Full glossary on slide 3."

---

### SLIDE 3 — Context, Personas, Assumptions & Glossary
*Nav: Context · Chips: LEGIBLE, BOUNDED · No question strip.*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ DIAGRAM: control ─┐ ┌CARD 1 ─┐ ┌CARD 2 ─┐ ┌CARD 3 ─┐          │
│ │ boundary (30%)    │ │ User   │ │ Agent  │ │ Board  │          │
│ └───────────────────┘ └────────┘ └────────┘ └────────┘          │
│ ┌ ASSUMPTIONS (50%) ──────────┐ ┌ GLOSSARY (50%) ────────────┐ │
│ └─────────────────────────────┘ └────────────────────────────┘ │
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[TITLE]** "The agent isn't ours: Instacart controls only the contract and the guardrails, so we design for three users"

**[TAKEAWAY]** "A third-party agent will read our API literally and act at scale. That makes the agent a user persona, and the API the product."

**[DIAGRAM — Control boundary]** *(two columns split by a dashed vertical line labelled "API / MCP boundary"; left column greyed, right column in a #003D29 tint)*
- "**Outside our control**": "The user's intent and phrasing" · "The agent's LLM reasoning" · "Which agent platform shows up" · "How the agent reads our docs"
- "**Inside our control**": "API / MCP schema and tool descriptions" · "Server-side validation and guardrails" · "Preference and mandate store" · "Catalogue data (units, pack sizes)" · "Monitoring and a per-platform kill switch"

**[CARD 1 — The User]** *(icon: person with basket)*
- "**Meera, 34 — working parent, weekly shopper**"
- "**Wants**: the weekly shop done without opening the app · her rules respected ("never substitute baby formula", "organic milk only") · to see what was bought, and undo it if wrong"
- "**Pain points**: 10+ minutes picking substitutes item by item · fear of the agent buying something she didn't mean · surprises at the door"
- "**What it means for us**: preferences and the cancel window are product, not settings."

**[CARD 2 — The Agent]** *(icon: phone with sparkle)*
- "**The phone's AI assistant — a literal-minded new hire who reads our docs once**"
- "**Wants**: unambiguous fields with enums and examples · error messages it can self-correct from · a way to ask the user when unsure"
- "**Pain points**: unitless fields and silent defaults · products matched by name · no read-back of what the server understood"
- "**What it means for us**: treat the LLM reading our MCP docs as a user. Any ambiguity we allow becomes errors at scale."

**[CARD 3 — The Business]** *(icon: chart)*
- "**Instacart product VP & board**"
- "**Wants**: proof that agentic commerce is a growth channel vs ChatGPT and Amazon · an impressive board demo in 6 weeks · no public incident"
- "**Pain points**: a competitor stalled publicly · agents skip sponsored placements, while ad revenue grows faster than GTV · zero data on agent-placed orders"
- "**What it means for us**: show progress on real rails, with guardrails visible."

**[ASSUMPTIONS]** *(numbered list, 12 px)*
1. "Agents act for users at scale within 12 months (the brief's thesis)."
2. "Agents connect via Instacart's API/MCP; checkout rails partly exist (ChatGPT checkout via ACP, Dec 2025)."
3. "US market; ~$115 average order (Q2 2026: $10.35B GTV ÷ 90.3M orders)."
4. "No historical data on agent-initiated orders exists."
5. "The Q2 demo team and the Q3 team (2 engineers × 4 weeks) are the same team."

**[GLOSSARY]** *(two-column definition list, 11 px)*
- "**ACP** — OpenAI/Stripe protocol that lets an AI agent complete a checkout"
- "**AP2** — Google's agent-payments protocol; a signed *Intent Mandate* (the user's standing rules) and *Cart Mandate* (the exact cart)"
- "**MCP** — Model Context Protocol; how an agent discovers and calls our tools"
- "**Wizard-of-Oz prototype** — a demo where some steps are mocked behind the scenes; staging only"
- "**Idempotency key** — an ID that stops a retried request from creating a duplicate order"
- "**Conformance suite** — test cases an agent platform must pass before it can place real orders"
- "**P90** — the value 90% of users fall at or below"

**[CALLOUT]** "SO WHAT → We can't make agents smarter. We can make our contract impossible to misread and our guardrails impossible to bypass."

**[FOOTER]** "Sources: Instacart Q2 2026 results; Digital Commerce 360 (Dec 2025); Instacart Developer Platform docs (MCP)."

---

### SLIDE 4 — Q1: Why groceries
*Nav: Q1 Market · Chips: REVERSIBLE, BOUNDED*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [Q]                                                            │
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ TABLE: ARS criteria + scoring (62%) ┐ ┌ CHART: XY (38%) ───┐ │
│ │ 5 criteria × 5 domains, with "why"  │ │ frequency vs cost  │ │
│ └─────────────────────────────────────┘ ├ ROBUSTNESS box ────┤ │
│ ┌ STRATEGIC VERDICT (full width): verdict | expansion path | caveat ┐│
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[Q]** "THE QUESTION · Make the case for why groceries are a good place to start."

**[TITLE]** "Groceries score 91.5% on agentic readiness and lead on every criterion, so they're the right place to start under any weighting"

**[TAKEAWAY]** "Start where agents fail cheaply, often and visibly: that's where trust gets built fastest."

**[TABLE — Agentic Readiness Score (ARS): weighted decision matrix, 1–10 scale]** *(heat-map colours; Groceries column outlined as RECOMMENDED; the bracketed "why" sits under the Groceries number in 11 px grey)*

| Criterion — *why it matters* | Weight | **Groceries** | Food delivery | Travel & flights | Consumer electronics | Fashion & apparel |
|---|---|---|---|---|---|---|
| **Transaction frequency & repetition** — *more transactions = faster learning and trust* | 25% | **9.0** (weekly shop; 65%+ repeat items) | 8.0 | 3.0 | 2.0 | 5.0 |
| **Rule-expressibility** — *can intent become machine-unambiguous rules?* | 20% | **9.0** (brand lock, size, diet, price ceiling) | 5.0 | 6.0 | 7.0 | 3.0 |
| **Cost of error & reversibility** — *blast radius of a wrong action* | 25% | **9.0** (~$115 basket, free cancel before picking) | 6.0 | 1.0 ($1,500 non-refundable fare) | 2.0 | 5.0 |
| **Existing delegation model** — *do users already let someone pick for them?* | 15% | **10.0** (Instacart shoppers do today) | 6.0 | 5.0 | 2.0 | 2.0 |
| **Drudgery & automation demand** — *how much users want to hand it off* | 15% | **9.0** (76% struggle with substitution flows) | 4.0 | 7.0 | 3.0 | 2.0 |
| **Weighted total** | 100% | **9.15 / 10** | 6.00 | 4.00 | 3.15 | 3.70 |
| **Agentic Readiness Index** | — | **91.5%** | 60.0% | 40.0% | 31.5% | 37.0% |

**[CHART — XY: frequency vs cost of a wrong decision]** *(small scatter plotted from the table: x = frequency score; y = 11 − cost-of-error score)*
- X axis: "Transaction frequency →". Y axis: "Cost of a wrong decision →".
- Quadrant labels: bottom-right "**Learn here first**" · top-left "**Go last**" · top-right "**Gate every action**" · bottom-left "**Low learning value**".
- Points (x, y): **Groceries (9, 2)** *(large green dot)* · Food delivery (8, 5) · Fashion (5, 6) · Travel (3, 10) · Electronics (2, 9).

**[ROBUSTNESS BOX]**
- "**Does the answer depend on our weights? No.**"
- "Groceries score highest on **all five** criteria, so they rank #1 under *any* weighting. Weights change the margin, never the winner."
- "Equal weights: Groceries 9.2 · Food 5.8 · Travel 4.4 · Fashion 3.4 · Electronics 3.2."
- "Closest possible call: 100% weight on frequency → Groceries 9 vs Food delivery 8."

**[STRATEGIC VERDICT]** *(full-width panel in 3 parts)*
- **Part 1 — Verdict** *(bold, 15 px)*: "**Start with the weekly reorder.** The agent rebuilds the user's usual basket, substitutes within their rules, and every order stays cancellable until picking begins. Instacart is already a delegation business: ~300M replacements in 2024 at 95% satisfaction. The agent replaces the *relay* between user and shopper, not the trust model."
- **Part 2 — Expansion path** *(chevron row)*: "Groceries" → "Household essentials & pharmacy refills" → "Food delivery" → "Fashion" → "Electronics & travel". Caption: "**Move right only when** the unintended-order rate stays below 0.5% and the contract passes conformance in the current category."
- **Part 3 — Honest caveat** *(amber left border)*: "Perishables, allergens and hourly stock changes are hard, but any agent-ready platform must solve them anyway. **Hard rule: no autonomous substitution on allergen-flagged items.**"

**[CALLOUT]** "SO WHAT → Groceries are hard enough to matter and safe enough to fail: the cheapest place to learn how agents break before moving to higher-stakes categories."

**[FOOTER]** "Scores are team estimates (1–10) anchored on cited proxies. Sources: Instacart Q2 2026 results; CXM World (2024 replacements); Baymard Institute (substitution UX); Wave Grocery (repeat purchase)."

---

### SLIDE 5 — Q2: The flashy board demo
*Nav: Q2 Demo · Chips: ACCOUNTABLE, REVERSIBLE*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [Q]                                                            │
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ KEY ASSUMPTIONS (4 chips in one row) ──────────────────────┐ │
│ ┌ PRE-MORTEM table (50%) ────────┐ ┌ OPTIONS table (50%) ────┐ │
│ └────────────────────────────────┘ └─────────────────────────┘ │
│ ┌ LEAN MVP / WIZARD-OF-OZ (35%) ┐ ┌ EXECUTION PLAN: 6-week bar ┐│
│ │ 3 demo moments                │ │ 80/20 + timeline (65%)     ││
│ └───────────────────────────────┘ └────────────────────────────┘│
│ ┌ QUOTE: what I'd tell the PM (full width, 1–2 lines) ───────┐ │
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[Q]** "THE QUESTION · Instacart's product team wants to prioritise a flashier feature for a board demo in six weeks, even though you believe it'll be thrown out in three months once real agent traffic exposes its flaws. Will you build what they asked for, or push back and delay?"

**[TITLE]** "Push back on the scope, not the date: the board gets its demo in six weeks, built on the real foundation"

**[TAKEAWAY]** "The board isn't buying a feature; it's buying confidence the bet is real. A demo on real rails delivers that, and it's still standing when agent traffic arrives."

**[KEY ASSUMPTIONS]** *(4 chips)*
1. "The flashy feature is e.g. 'one voice command plans and checks out a full month of meals', built on mocked inventory with no guardrails"
2. "The board's decision after the demo: keep funding the agent programme"
3. "The six-week date is fixed; the scope isn't"
4. "The demo team = the Q3 team"

**[TABLE — Pre-mortem: "It's three months later and the flashy feature has been pulled. Why?"]**

| What broke under real agent traffic | Because the demo assumed… | What we build instead (the foundation) |
|---|---|---|
| Out-of-stock items stalled orders | A fully in-stock catalogue | Substitution-Preference API (Q3) |
| Users got duplicate orders | One agent, no retries | Idempotency keys + duplicate check (Q5) |
| Quantities came out wrong | Free-text product names | Unit-safe contract (Q4) |
| "I didn't mean to order that" | A human approving every step | Guardrails + undo window (Q5) |
| API throttled at peak | No rate limits | Per-platform limits + monitoring |

*Caption under the table (11 px):* "Why a pre-mortem rather than RICE: we have no reach data for agent traffic yet, but we can name exactly how this feature fails."

**[TABLE — Strategic options]** *(Option C outlined as RECOMMENDED)*

| Option | Demo in 6 wks | Foundation | Client relationship | Verdict |
|---|---|---|---|---|
| A. Build as asked | ✅ Wow | ❌ ~6 weeks lost + ~3-month rebuild | ✅ now, ❌ when it's pulled | "Short-term win, long-term loss" |
| B. Push back and delay | ❌ No demo | ✅ Protected | ❌ Sponsor embarrassed | "Right on the merits, politically naive" |
| **C. Reframe the scope** | ✅ Wow, on real rails | ✅ ~80% of capacity protected | ✅ Sponsor wins twice | "**Recommended**" |

**[LEAN MVP — Wizard-of-Oz demo, 3 moments]** *(3 mini chat-bubble frames)*
1. "**"Do my weekly shop."** The agent rebuilds the usual basket in seconds." *(real API)*
2. "**Organic milk is out of stock.** The agent substitutes within the user's rule (same brand, ≤ +5% price) and says why." *(real API)*
3. "**The agent tries to add 10 kg of flour (5× normal).** The guardrail pauses and asks. *Trust is the wow moment.*" *(real API)*
- Tag under the frames: "The flashy 'month of meals' feature → shown as a Wizard-of-Oz prototype, labelled **'Vision: next quarter'**"

**[EXECUTION PLAN]** *(one 100% bar, then a 6-week strip)*
- Bar: **80% Foundation** (#003D29): "Substitution-Preference API · unit-safe cart · guardrail service" | **20% Demo layer** (#FF7009): "demo script on staging · labelled prototype"
- Weeks: "**Wk 0:** agree scope with the PM; share the pre-mortem" → "**Wk 1–4:** build the Substitution API (Q3)" → "**Wk 5:** demo script on staging + 3 dry runs" → "**Wk 6:** board demo" → "**Wk 7+:** rebuild plan for the prototype, if the board wants it"

**[QUOTE — What I'd tell the PM]** "Let's make sure the board sees something impressive in six weeks, and that it's still standing when real agent traffic arrives. If you still want the original feature after seeing this pre-mortem, we'll build it, with the rebuild plan agreed upfront." *(tag: "Disagree and commit")*

**[CALLOUT]** "SO WHAT → A labelled prototype protects credibility; an unlabelled one becomes the over-promise risk we flag in Q6."

**[FOOTER]** "The flashy feature is an assumption; the brief doesn't name it. Frameworks: pre-mortem, one-way vs two-way doors, disagree-and-commit."

---

### SLIDE 6 — Q3a: The decision
*Nav: Q3 Build · Chips: BOUNDED, LEGIBLE*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [Q]                                                            │
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ OPTION A def ──────────┐ ┌ OPTION B def ──────────┐  2 cards │
│ ┌ TABLE: weighted matrix (50%) ┐ ┌ CHART: decision map (50%) ┐ │
│ │                              │ │ 2×2 when-each-wins         │ │
│ └──────────────────────────────┘ └────────────────────────────┘ │
│ ┌ TABLE: what-if scenarios (full width, 5 rows) ─────────────┐ │
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[Q]** "THE QUESTION · You have 2 engineers and 4 weeks. You can make the checkout API agent-readable, or the substitution-preference API agent-readable. Which one will you pick?"

**[TITLE]** "Pick the Substitution-Preference API: in grocery, substitution is the leak, and checkout already has a working path"

**[TAKEAWAY]** "Without preferences, an agent either pings the user on almost every order or guesses. Either way, it stops being a trusted shopper."

**[OPTION CARDS]**
- **A — Checkout API, agent-readable:** "An agent can price, pay for and place an order programmatically."
- **B — Substitution-Preference API, agent-readable:** "An agent can read and write the user's rules for what to do when an item is unavailable." *(RECOMMENDED tag)*

**[TABLE — Weighted decision matrix, 1–5]** *(column B outlined)*

| Criterion | Weight | A. Checkout | **B. Substitution** |
|---|---|---|---|
| Unblocks autonomy | 30% | 3 — completes the order, but a human can already confirm it | **5** — without it, the agent asks or guesses on ~every order |
| Moat | 20% | 2 — being commoditised by ACP, AP2, Visa and Mastercard rails | **5** — built on Instacart's substitution history |
| Risk in 4 weeks | 20% | 2 — money path, irreversible, fraud surface | **4** — rules API, small blast radius |
| Feasible: 2 eng × 4 wks | 15% | 3 — payments, auth, compliance | **4** — schema + endpoints + escalation hook |
| Measurability | 15% | 4 | **4** |
| **Weighted score** | | **2.75 (55%)** | **4.50 (90%)** |

**[CHART — Decision map: when does each option win?]** *(2×2)*
- X axis: "**Agent checkout readiness →**" (can an agent already complete a purchase reliably? low → high)
- Y axis: "**Substitution frequency →**" (replacements per order, low → high)
- Quadrants:
  - Top-right: "**Substitution first** — checkout works; stockouts are the leak"
  - Top-left: "**Checkout first, then substitution** — fix the leak, then save the cart"
  - Bottom-left: "**Checkout first** — nothing else matters if orders can't complete"
  - Bottom-right: "**Neither is the bottleneck** — invest in recurring lists or discovery"
- Points: "★ **Instacart today**" in the top-right *(ACP checkout live; ~1 replacement per order)*. Faded reference dots: "Early-stage agent startup" (bottom-left), "Electronics retailer" (bottom-right), "New quick-commerce app" (top-left).

**[TABLE — What-if scenarios: when would we flip?]**

| Scenario | Pick | Why |
|---|---|---|
| **Today:** ACP checkout live, ~1 replacement per order | **Substitution** | Checkout has a workaround (one-tap confirm); substitutions don't |
| Agent checkout success rate < 90% across platforms | Checkout | "Fix the leak before you buy more water" |
| The phone's agent has no ACP / hand-off path at all | Checkout | Nothing completes, so nothing else matters |
| Real-time inventory cuts replacements below 0.1 per order | Checkout | Substitution stops being the bottleneck |
| Board insists on fully autonomous checkout in the demo | **Still Substitution** | The demo uses one-tap confirm; safe sequencing beats a demo wish |

**[CALLOUT]** "SO WHAT → 'Fix the leak first' is the right rule, and in grocery the leak is substitution: about one replacement per order. Checkout earns priority only if agent checkout success falls below 90%."

**[FOOTER]** "Sources: Instacart × ChatGPT checkout via ACP (Dec 2025); Google AP2 (Sep 2025); CXM World (~300M replacements in 2024 vs ~290M orders)."

---

### SLIDE 7 — Q3b: The 4-week plan
*Nav: Q3 Build · Chips: BOUNDED, LEGIBLE, ACCOUNTABLE*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [Q]                                                            │
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ CODE: preference schema (40%) ┐ ┌ CHART: Gantt, E1/E2 (60%) ┐ │
│ └───────────────────────────────┘ └───────────────────────────┘ │
│ ┌ COLD START (33%) ┐ ┌ NOT IN v1 (33%) ┐ ┌ SUCCESS METRICS (33%)┐│
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[Q]** *(short form)* "THE QUESTION · 2 engineers, 4 weeks: checkout API or substitution-preference API? *(continued)*"

**[TITLE]** "Two engineers can ship a v1 Substitution-Preference API in four weeks, seeded with data only Instacart has"

**[TAKEAWAY]** "Scope it as rules plus escalation, not ML. The data moat comes from seeding it with each user's substitution history."

**[CODE — Preference schema v1]**
```
PUT /v1/users/{id}/substitution-preferences
{
  "category_defaults": {
    "dairy": { "on_unavailable": "substitute",
               "brand_lock": false, "price_ceiling_pct": 10 }
  },
  "items": [{
    "product_id": "55021",            // Organic 2% milk, 1 gal
    "allow_substitution": true,
    "ranked_alternates": ["55034", "55090"],
    "constraints": { "size_tolerance_pct": 0,
                     "price_ceiling_pct": 5,
                     "must_have": ["organic"] },
    "on_unavailable": "substitute"     // substitute | skip | ask_user
  }],
  "allergen_rule": "always_ask_user"
}
```

**[CHART — Gantt]** *(rows = workstreams; columns Wk 1–4 + faded Wk 5–6)*

| Workstream | Wk 1 | Wk 2 | Wk 3 | Wk 4 | Wk 5–6 *(faded)* |
|---|---|---|---|---|---|
| Schema & defaults *(E1+E2)* | ███ "Per-item rules, ranked alternates, constraints, category defaults; seed from history" | | | | |
| API + MCP tools | | ███ E1: "read/write endpoints v1" · E2: "MCP tool definitions with enums and worked examples" | | | |
| Explain + escalate | | | ███ E1: "explanation payload: 'X → Y: same brand, +4% price, within your rule'" · E2: "`ask_user` escalation webhook" | | |
| Test + pilot *(E1+E2)* | | | | ███ "Conformance tests with 2 agent platforms · 100-case eval set · pilot cohort" | "Powers the board demo (Q2)" |

**[COLD START]** "**Day-1 preferences without asking users:** seed each user's rules from their history of accepting and rejecting substitutions in the Instacart app. No competitor has this data, and it's the moat in the matrix."

**[NOT IN v1]** "**Deliberately cut:** ML-ranked alternates · substitutions across stores · a new preferences UI (agents write rules on the user's behalf) · checkout changes (keep ACP + one-tap confirm)"

**[SUCCESS METRICS]** *(3 KPI tiles)*
- "**≥ 95%** substitution acceptance (human-shopper baseline)"
- "**↓ week over week** `ask_user` escalations per order"
- "**≤ baseline** refunds on substituted items"

**[CALLOUT]** "SO WHAT → The Substitution-Preference API *is* the 'boundaries the user has set' in the brief. It turns the agent from an assistant that asks into a shopper that knows."

**[FOOTER]** "Product IDs and values are illustrative. Schema pattern follows Instacart Developer Platform conventions."

---

### SLIDE 8 — Q4a: Diagnose (RCA)
*Nav: Q4 Contract · Chips: LEGIBLE, ACCOUNTABLE*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [Q]                                                            │
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ DIAGRAM: fishbone, 6 MECE bones (full width, ~40% height) ─┐ │
│ │                                         ──► [EFFECT box]    │ │
│ └─────────────────────────────────────────────────────────────┘ │
│ ┌ 5 WHYS chain (55%) ───────────┐ ┌ ROOT CAUSE + KEY INSIGHTS ┐│
│ │ 5 stacked steps                │ │ (45%)                     ││
│ └────────────────────────────────┘ └───────────────────────────┘│
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[Q]** "THE QUESTION · Two agent platforms integrate with the new Instacart API/MCP and interpret an ambiguous field (`quantity: 2`) differently: one orders 2 units, the other 2 packs of wheat (1 kg). Where could the problem be, and how will you fix it?"

**[TITLE]** "Neither agent is wrong: the root cause is a design error, a contract built for humans who see context and consumed by agents who don't"

**[TAKEAWAY]** "We walked every layer (MECE) and asked 'why' five times. Two layers fail, both inside Instacart's control."

**[DIAGRAM — Fishbone]** *(spine running left to right into an effect box on the right; 3 bones above, 3 below; each bone has 2 small cause labels. The Contract and Resolution bones are drawn in red and tagged "ROOT CAUSE"; Controls is tagged "WHY IT WENT UNNOTICED".)*
- **Effect box:** "Same intent ('2 wheat') → two different orders"
- Bone **User intent**: "'2 wheat' is genuinely ambiguous" · "No unit in natural speech"
- Bone **Agent interpretation**: "Each LLM maps intent differently" · "Neither asks a clarifying question"
- Bone **API / MCP contract** 🔴: "`quantity` has no unit; `unit` optional, silently defaults to 'each'" · "Prose tool docs, no enums or examples"
- Bone **Product resolution** 🔴: "Products matched by `name`" · "'wheat' → single unit vs 1 kg pack SKU"
- Bone **Catalogue data**: "Unit of sale (each / weight / pack) not machine-readable" · "Pack size buried in the title"
- Bone **Controls** 🟠: "No read-back of the normalised line item" · "No conformance tests, no per-platform monitoring"

**[5 WHYS]** *(5 stacked boxes joined by down arrows; each line starts with "Why…?" in bold)*
1. "**Why did two agents order different amounts?** They sent different payloads, which resolved to different products, for the same intent."
2. "**Why could they?** `quantity` carries no unit, and the product is matched by free-text `name`."
3. "**Why did the server accept that?** `unit` is optional and silently defaults to 'each'; nothing checks it against the product's unit of sale."
4. "**Why was it designed that way?** The contract was built for Instacart's own app, where a human sees the photo and pack size before tapping '+2'. The context lived on the screen, not in the payload." *(tag: hypothesis to verify)*
5. "**Why wasn't it caught?** No read-back, no conformance tests for agent consumers, and no per-platform monitoring."

**[ROOT CAUSE + KEY INSIGHTS]**
- **Root cause** *(red-bordered box, bold)*: "**Design error:** a human-context contract was exposed to context-blind agents."
- **Key insights:**
  1. "**Diagnostic rule:** same payload, different result → server bug. Different payloads → contract and documentation bug. Here it's the second."
  2. "**It's real:** Instacart's own `LineItem` schema defaults `quantity` to `1.0` and `unit` to 'each', matches products by `name`, and has deprecated both fields for `line_item_measurements`."
  3. "**Given our contract, neither agent was wrong.** That's the point: the fix is ours to make."

**[CALLOUT]** "SO WHAT → If two agents can read one field two ways, at scale they will. Any field that relies on screen context is a bug waiting for an agent."

**[FOOTER]** "Frameworks: Ishikawa (fishbone) across MECE layers + 5 Whys. Source: Instacart Developer Platform — Create shopping list page (LineItem schema)."

---

### SLIDE 9 — Q4b: Fix (three horizons)
*Nav: Q4 Contract · Chips: LEGIBLE, ACCOUNTABLE, REVERSIBLE*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [Q]                                                            │
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ CODE: before → after payload (45%) ┐ ┌ 4 HORIZONS (55%) ────┐ │
│ │ dark block                          │ │ Day 0 | Days | Weeks │ │
│ │                                     │ │ | Quarter            │ │
│ └─────────────────────────────────────┘ └──────────────────────┘ │
│ ┌ DESIGN PRINCIPLES (2 boxes side by side, full width) ──────┐ │
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[Q]** *(short form)* "THE QUESTION · `quantity: 2` read two ways — where's the problem, and how will you fix it? *(continued)*"

**[TITLE]** "Make the contract strict, make the server read back what it understood, and certify agents before they can write"

**[TAKEAWAY]** "Contain the damage today, remove the ambiguity this week, and make it structurally impossible this quarter."

**[CODE — Before → after payload]**
```
// BEFORE — ambiguous, accepted silently
POST /cart/items
{ "name": "wheat", "quantity": 2 }
→ Agent A: 2 units        → Agent B: 2 × 1 kg packs

// AFTER — strict request
POST /v2/cart/items
{ "product_id": "88123", "quantity": 2, "unit": "pack",
  "idempotency_key": "a7f3-…" }

// AFTER — server read-back
200 OK
{ "resolved": "2 × Whole Wheat Flour (1 kg pack) = 2 kg",
  "line_total": "$7.98", "requires_confirmation": false }

// AFTER — self-correcting error
422 { "error": "unit_required",
      "hint": "Sold by pack (1 kg). Did you mean
               quantity=2, unit=pack (2 kg total)?" }
```

**[4 HORIZONS]** *(4 columns with header pills)*
- **DAY 0 — Contain**
  - "Pull agent orders whose resolved quantity is > 2× the user's norm, by platform"
  - "Refund or credit affected users proactively"
  - "Hold ambiguous lines from the affected platform for confirmation"
  - "Notify both platforms with examples"
- **DAYS — Stop the bleeding**
  - "`unit` mandatory: `each · pack · kg · g · lb · l`; no silent defaults"
  - "Self-correcting 422 errors an LLM can act on"
  - "Read-back on every cart write"
  - "Anomaly guard: > 3× usual quantity → confirm"
- **WEEKS — Fix the contract**
  - "`product_id` / UPC required to order; names for search only"
  - "JSON Schema / OpenAPI enums; MCP docs with worked ambiguous examples"
  - "Dry-run quote endpoint before commit (AP2 Cart Mandate pattern)"
  - "Partner changelog + 30-day migration window to v2"
- **QUARTER — Make it structural**
  - "Canonical units on every SKU: `sold_by`, `pack_size`, `net_content`"
  - "Conformance suite gates production write access"
  - "Per-platform monitoring + divergence alerts"
  - "Versioned API; deprecate the name-based order path"

**[DESIGN PRINCIPLES]** *(2 boxes)*
- "**1. Be strict in what you accept from agents, and explicit in what you send back.** This inverts Postel's law: liberal acceptance turns into silent divergence at scale."
- "**2. The API is the product; the LLM reading our docs is a user.** If a field needs a screen to make sense, it isn't agent-ready."

**[CALLOUT]** "SO WHAT → We can't fix two agents we don't own, but we can make one contract that no agent can misread, and prove every agent passes it before it touches a real order."

**[FOOTER]** "Product, price and IDs in the payload are illustrative."

---

### SLIDE 10 — Q5a: The number
*Nav: Q5 Guardrails · Chips: BOUNDED, REVERSIBLE*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [Q]                                                            │
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ BIG "5" ┐ ┌ GUESSTIMATE: anchoring ladder from real data (45%)┐│
│ └─────────┘ └──────────────────────────────────────────────────┘│
│ ┌ CONFUSION MATRIX: cost of error (45%) ┐ ┌ SENSITIVITY 3/5/10 ┐│
│ │ precision vs recall                    │ │ (55%)              ││
│ └────────────────────────────────────────┘ └────────────────────┘│
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[Q]** "THE QUESTION · Agents placing orders for users will increase orders, but some users may complain they 'didn't mean to place the order', and there's no historical data on agent-initiated purchases. What should the threshold of orders per user per month be, and why?"

**[TITLE]** "Start at 5 autonomous orders per user per month — a weekly shop plus one top-up — because a missed bad order costs far more than an extra question"

**[TAKEAWAY]** "The goal isn't fewer orders, it's fewer *unintended* ones. The cap applies only to orders placed without approval; order #6 isn't blocked, the agent just asks."

**[BIG NUMBER]** *(huge "5", ~150 px, #003D29)* Caption: "autonomous agent orders / user / month at launch"

**[GUESSTIMATE — Anchoring ladder from Instacart data]** *(4 ascending steps; each shows the maths in small grey text)*
1. "**~1.2 / month** — average Instacart customer" *(grey: ~361M orders/yr (Q2'26 × 4) ÷ 26M+ customers (2025) ≈ 14/yr)*
2. "**~3 / month** — average monthly active orderer" *(grey: ~$317 monthly spend ÷ ~$115 order (S-1, 2023; dated))*
3. "**4.3 / month** — a weekly shop, the brief's core use case" *(grey: 52 ÷ 12)*
4. "**5 / month** — weekly shop + one mid-week top-up" *(grey: ~40% of online grocery shoppers order weekly; many top up)*
- Side note: "5 is ~1.7× a typical active orderer, so most users never hit it. Those who do are heavy shoppers, for whom one tap is trivial."

**[CONFUSION MATRIX — Cost of error: precision vs recall]** *(2×2 grid. Rows = "What the user actually intended"; columns = "What the guardrail did". The FN cell is red, the FP cell amber.)*

| | **Guardrail: let it through** | **Guardrail: ask first** |
|---|---|---|
| **Order was intended** | ✅ True negative: autonomy works | 🟠 **False positive: one tap, ~5 seconds** |
| **Order was unintended** | 🔴 **False negative: ~$115 refund + wasted perishables + shopper time + support ticket + lost trust** | ✅ True positive: caught before it cost anything |

- Under the grid: "**At launch, optimise recall (catch unintended orders) over precision (avoid extra asks).** As data arrives, raise precision with personalised caps without letting recall drop."

**[TABLE — Sensitivity: why not 3 or 10?]** *(the 5/month row outlined as CHOSEN)*

| Cap | A genuine weekly shopper… | A misfiring agent… | Verdict |
|---|---|---|---|
| 3 / month | gets asked from week 4, every month | is caught fast | ❌ Breaks the weekly-shop promise |
| **5 / month** | **gets a fully autonomous weekly shop + 1 top-up** | **is caught by the weekly cap and duplicate check (next slide)** | ✅ **Chosen** |
| 10 / month | is almost never asked | can place ~2× a normal month before anyone notices | ❌ Too loose with zero data |

**[CALLOUT]** "SO WHAT → With no data, anchor on how people already shop and on what each kind of mistake costs. Then let the unintended-order rate, not our opinion, move the number."

**[FOOTER]** "Sources: Instacart Q2 2026 results (GTV $10.35B, 90.3M orders); 2025 customer count per management (Q4 2025 call, via Barchart); Instacart S-1 (2023: 7.7M monthly active orderers, ~$317/month); Wave Grocery (weekly ordering)."

---

### SLIDE 11 — Q5b: The guardrail system
*Nav: Q5 Guardrails · Chips: BOUNDED, REVERSIBLE, ACCOUNTABLE*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [Q]                                                            │
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ TABLE: multi-layer guardrails (58%) ┐ ┌ RESPONSE TIERS (42%) ┐│
│ │ 6 layers                             │ ├ MANDATE + NOTIF. ────┤│
│ └──────────────────────────────────────┘ └──────────────────────┘│
│ ┌ CHART: phased rollout with gates (full width) ─────────────┐ │
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[Q]** *(short form)* "THE QUESTION · Threshold of agent orders per user per month, and why? *(continued)*"

**[TITLE]** "Above any limit the agent asks, it isn't blocked: six layers of guardrails that loosen only when the data earns it"

**[TAKEAWAY]** "Order count is only a proxy. We pair it with spend, basket, item, identity and safety checks, an undo window and a signed mandate."

**[TABLE — Multi-layer proxy guardrails]** *(the Layer column uses coloured row labels)*

| Layer | Guardrail | Launch default | When crossed |
|---|---|---|---|
| **1. Frequency** | Autonomous orders / month · / week | 5 / month · 2 / week (1 scheduled + 1 top-up) | One-tap approval; order held |
| **2. Spend** | Monthly agent spend | ≤ 1.25× trailing 3-month grocery spend, or the user's own cap | One-tap approval |
| **3. Basket** | Value per order | ≤ 1.5× the user's typical basket | One-tap approval |
| **4. Item** | Quantity of one item (Q4) | ≤ 3× the user's usual | Confirm that line, with read-back |
| **5. Identity** | Duplicate within 24 h · new address · new payment method | Always flagged | Explicit confirmation; idempotency key required |
| **6. Safety** | Allergen-flagged substitution | Never autonomous | `ask_user` |
| **Undo** | Cancel window | Free until the shopper starts picking (≥ 30 min) | "Undo" in every notification |

**[RESPONSE TIERS]** *(4 coloured tiles)*
- **GREEN — inside the mandate:** "Placed autonomously + notification with Undo"
- **AMBER — soft limit (layers 1–3):** "Order held; one-tap approval"
- **RED — hard rule (layers 4–6):** "Explicit confirmation with a plain-language read-back"
- **STOP — platform unintended rate > 1%:** "That agent platform drops to confirm-every-order"

**[MANDATE CARD]** *(styled like a signed ticket)* "**Standing mandate (AP2-style Intent Mandate):** weekly shop · Saturdays · up to $150 · substitutions per my rules · max 5 autonomous orders/month." Footer: "Signed mandate + signed cart = evidence when a user says 'I didn't mean to'."

**[NOTIFICATION MOCK]** "🛒 Your assistant ordered your weekly shop — $112, arriving Sat 10 am. **[View] [Undo]**"

**[CHART — Phased rollout]** *(3 chevrons with gate diamonds)*
- **Phase 0 · Weeks 0–2 · Dogfood:** "Employees only; every order confirmed; baseline data"
- ◆ "Unintended-order rate < 1%"
- **Phase 1 · Weeks 3–10 · Launch:** "5/month autonomous for a 1–5% cohort; undo live"
- ◆ "< 0.5% for 4 consecutive weeks"
- **Phase 2 · Week 10+ · Personalise:** "Cap = max(5, user's P90 monthly orders + 1)"
- Legend: "**Loosen** < 0.5% · **Hold** 0.5–1% · **Roll back** > 1%"
- Definition (11 px): "Unintended-order rate = (cancellations inside the window + 'didn't intend' complaints) ÷ agent-placed orders"

**[CALLOUT]** "SO WHAT → Instacart earns more when agents order more, so the guardrail must sit on unintended orders, not volume. Automate what can be undone; gate what can't."

**[FOOTER]** "Sources: Google AP2 (Intent and Cart Mandates); Visa Intelligent Commerce / Mastercard Agent Pay (agent tokens with spending limits)."

---

### SLIDE 12 — Q6: "Should we be worried?"
*Nav: Q6 Risk · Chips: ACCOUNTABLE*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [Q]                                                            │
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ SITUATION ANALYSIS (40%) ─────┐ ┌ STATEMENT TO THE POC (60%) ┐│
│ │ know | don't know | means     │ │ large quote panel          ││
│ └───────────────────────────────┘ └────────────────────────────┘│
│ ┌ TABLE: risk register, tied to Q1–Q5 (full width) ──────────┐ │
│ ┌ NO-REGRET MOVES (60%) ─────────┐ ┌ 3 SIGNALS WE WATCH (40%) ┐ │
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[Q]** "THE QUESTION · A competitor's agent-readiness project at another grocery app stalls publicly after four months: bad press, and the client blames the consulting team. Your Instacart contact asks, point blank: 'Should we be worried? Will this happen to us?' What will you say, given your project faces uncertainty too?"

**[TITLE]** "Yes, take it seriously: they stalled on the problems we've built for first, and here's exactly where we're still exposed"

**[TAKEAWAY]** "Honest beats reassuring. Turn the client's anxiety into a shared risk plan, and never bad-mouth the competitor or their consultants."

**[SITUATION ANALYSIS]** *(3 stacked mini-panels)*
- "**What we know:** same category, same hard parts (quantities, substitutions, unintended orders); a public stall after 4 months; the client blamed the consultants."
- "**What we don't know:** their scope, their team, what actually broke. *So we won't speculate.*"
- "**What it means for us:** their likely failure points are our known risks, and Q3–Q5 were chosen to address them first. Gartner expects > 40% of agentic AI projects to be cancelled by end-2027, citing cost, unclear value and weak risk controls."

**[STATEMENT TO THE POC — verbatim]** *(large quote panel, 15 px)*
"It's a fair question, and I won't pretend there's no risk. We have real uncertainty too: how fast agent traffic actually arrives, and how differently each agent platform behaves.
They're a grocery app, so their problems are likely ours: quantities, substitutions, orders users didn't mean. That's exactly why we built those defences first.
Projects like theirs usually stall for predictable reasons: nothing shipped for months, demos that over-promise, no guardrails so the first incident goes public, and unclear ownership so people blame each other. Here's how we're set up against each one, and where I think we're still exposed.
I'd suggest a joint pre-mortem this week, and three signals we review together every week, so neither of us is ever surprised."

**[TABLE — Risk register, tied to this deck]** *(Exposure uses chips; HIGH rows get a light red tint)*

| Failure mode | Our exposure | Mitigation | Where in this deck | Early-warning signal |
|---|---|---|---|---|
| Big-bang rewrite, nothing shipped | MED | Thin slices every 2–4 weeks, each measurable | Q3 (4-week v1) | No shipped slice in 4 weeks |
| Over-promised demo | **HIGH** | Demo on real rails; prototypes labelled | Q2 | Board asks for a launch date on a prototype |
| No guardrails → public incident | MED | Six guardrail layers, staged cohorts, incident playbook | Q5 | Unintended-order rate > 0.5% |
| Ambiguous contract breaks with real agents | MED | Strict v2 contract + conformance gate | Q4 | Per-platform divergence alert |
| Agent adoption slower than the thesis | **HIGH** | No-regret moves (below) | Q1 (start where value is fastest) | Agent orders below plan two months running |
| Unclear ownership → blame | LOW–MED | Joint RACI, shared weekly risk register, pre-agreed kill/pivot criteria | — | Decisions slipping > 1 week |

**[NO-REGRET MOVES]** "**Even if agents arrive late, the work isn't wasted.** Structured units → fewer wrong-quantity refunds · preference API → better human-shopper substitutions · idempotent cart → fewer duplicate orders. The downside is bounded."

**[3 SIGNALS WE WATCH TOGETHER]** *(3 KPI tiles)* "Unintended-order rate" · "Conformance pass rate per agent platform" · "% of milestones shipped on time"

**[CALLOUT]** "SO WHAT → Teams get blamed for surprises, not for risks. A shared, written risk register removes the surprise."

**[FOOTER]** "Sources: Gartner via Outlook Business (Jun 2025); MIT NANDA via Fortune (Aug 2025: ~95% of GenAI pilots stall before scaled impact)."

---

### SLIDE 13 — North Star Metric & Dashboard
*Nav: Metrics · Chips: all four · No question strip. Layout modelled on the "Initiatives → KPI → Dimension → North Star" tree.*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ DIAGRAM: NSM tree (full width, ~42% height) ───────────────┐ │
│ │ Initiatives → Input metric (KPI) → Dimension ⟶ (NORTH STAR) │ │
│ └─────────────────────────────────────────────────────────────┘ │
│ ┌ COUNTER-METRICS (36%) ┐ ┌ GUARDRAIL METRICS (32%) ┐ ┌ BUSINESS (32%) ┐│
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[TITLE]** "One North Star, Trusted Agent Orders, driven by four input dimensions and kept honest by counter-metrics with hard thresholds"

**[TAKEAWAY]** "We count only orders that land as the user intended. Volume without trust is how agentic programmes get cancelled."

**[DIAGRAM — NSM tree]** *(4 columns: "Initiatives (this deck)" · "Input metric (KPI)" · "Dimension" · "North Star". Initiative boxes teal #A7D8DE, KPI pills light blue #CFE3FA, dimension pills lavender #D9D2F5, North Star a large blue circle with a star icon; curved arrows from each dimension converge on it.)*

| Initiatives (this deck) | Input metric (KPI) | Dimension |
|---|---|---|
| • Mandate onboarding • ACP / MCP partnerships • Conformance certification (Q4) | # users with an active agent mandate | **Breadth** |
| • Substitution-Preference API (Q3) • Category defaults • Cold-start seeding | % of basket completed with no user interruption | **Depth** |
| • Recurring list • Standing weekly mandate • Smart top-ups | Agent orders per user per month | **Frequency** |
| • Unit-safe contract (Q4) • Six-layer guardrails (Q5) • Undo window | % of agent orders delivered as intended | **Trust** |

- North Star circle: "**Trusted Agent Orders / week**"
- Definition (12 px): "Agent-initiated orders that were delivered and *not* cancelled, refunded for intent reasons, or complained about."

**[COUNTER-METRICS — catch harm from chasing the North Star]**

| Metric | Threshold | If breached |
|---|---|---|
| Unintended-order rate | < 0.5% | > 1% → roll back the cap (Q5) |
| Substitution complaint rate | ≤ human-shopper baseline | Default the category to `ask_user` |
| Wrong-quantity refund rate | ≤ app baseline | Suspend that platform's write access |

**[GUARDRAIL METRICS — the system must not break]**

| Metric | Threshold |
|---|---|
| Conformance pass rate per platform | ≥ 90% before write access |
| Self-corrected 422 rate (agent fixes its call on retry) | Rising week over week |
| Cart API p95 latency | < 500 ms |
| Support tickets / 1,000 agent orders | ≤ app baseline |

**[BUSINESS METRICS]**
- "GTV through the agent channel"
- "90-day retention: agent users vs app-only users"
- "**Open question: ad revenue at risk.** Agents skip sponsored placements, and ads grow faster than GTV. Test: sponsored results exposed via the API, with disclosure."

**[CALLOUT]** "SO WHAT → A guardrail has a threshold and a consequence. A counter-metric you only watch is just another chart."

**[FOOTER]** "Framework: North Star → input metrics → counter-metrics and guardrails (IIMA Product Casebook). Latency target is an assumption."

---

### APPENDIX — Sources & Calculations
*Small "Appendix" tag instead of the nav bar. Two columns, 12 px.*

**Left column — Calculations**
- "**Average order value:** $10.351B GTV ÷ 90.3M orders (Q2 2026) = **~$115**"
- "**Annual run-rate:** 90.3M × 4 ≈ **361M orders/yr**"
- "**Orders per customer:** 361M ÷ 26M+ customers (2025) ≈ **14/yr ≈ 1.2/month**"
- "**Orders per monthly active orderer:** ~$317 spend/month ÷ ~$115 ≈ **~3/month** (S-1, 2023; dated)"
- "**Weekly cadence:** 52 ÷ 12 = **4.33/month**"
- "**Replacements per order:** ~300M replacements ÷ ~290M orders (2024, approx.) ≈ **1**"
- "**ARS (Q1):** Groceries = 9×0.25 + 9×0.20 + 9×0.25 + 10×0.15 + 9×0.15 = **9.15 → 91.5%**; Food 6.00 · Travel 4.00 · Fashion 3.70 · Electronics 3.15"
- "**ARS, equal weights:** Groceries 9.2 · Food 5.8 · Travel 4.4 · Fashion 3.4 · Electronics 3.2"
- "**Q3 matrix:** Checkout = 3×0.30 + 2×0.20 + 2×0.20 + 3×0.15 + 4×0.15 = **2.75**; Substitution = 5×0.30 + 5×0.20 + 4×0.20 + 4×0.15 + 4×0.15 = **4.50**"

**Right column — Sources**
- "Instacart Q2 2026 financial results (Aug 6, 2026)"
- "Instacart Q4 2025 earnings call, via Barchart (26M+ customers in 2025)"
- "Instacart S-1 (2023): 7.7M monthly active orderers, ~$317 monthly spend"
- "Instacart × ChatGPT checkout via ACP (Digital Commerce 360, Dec 2025)"
- "Instacart Developer Platform: MCP guide; Create shopping list page (LineItem schema)"
- "CXM World: 2024 replacements & satisfaction"
- "Baymard Institute: grocery substitution UX"
- "Wave Grocery: repeat-purchase and weekly-ordering behaviour"
- "Google AP2 (Sep 2025); Visa Intelligent Commerce / Mastercard Agent Pay (May 2025)"
- "McKinsey: The agentic commerce opportunity"
- "Gartner agentic AI forecast (Outlook Business, Jun 2025); MIT NANDA (Fortune, Aug 2025)"
- "IIMA Product Casebook 2026–27"

---

## Part D — Pre-submission checklist
- [ ] Read only the 13 titles: does each one answer its question in the brief's own words?
- [ ] Every number appears in the appendix calculations or has a footer source.
- [ ] Estimates are marked "~", "est." or "dated".
- [ ] Q2, Q3 and Q5 each state a clear choice *and* a flip or rollback condition.
- [ ] Consistency: checkout stays human-confirmed early (Q3 what-if table, Q5 tiers, exec summary strip).
- [ ] The densest slides (5, 8, 11, 12) are readable at 100% zoom in the exported PDF.
- [ ] Open every source link once and confirm the figure.
