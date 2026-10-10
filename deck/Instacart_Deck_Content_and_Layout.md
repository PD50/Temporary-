# Instacart Agent-Readiness — Deck Content & Layout Spec
*Reading deck, 12 slides + appendix, 16:9 (1920 × 1080). Every word in quotes or inside a block is final slide copy. Text in *(italics)* is a layout instruction, not slide copy.*

---

## Part A — Design system (paste this into Figma Make first)

### A1. Master prompt for Figma Make
> Design a 16:9 presentation slide at 1920×1080 for a consulting-style *reading* deck (it will be exported to PDF and read without a presenter, so it should be dense but scannable). Use the Inter font only. Margins 64 px left/right, 48 px top/bottom, a 12-column grid with 24 px gutters.
> **Fixed chrome on every slide:**
> (1) Top nav bar, 40 px tall, full width: ten text tabs — Summary · Context · Q1 Market · Q2 Demo · Q3 Build · Q4 Contract · Q5 Guardrails · Q6 Risk · Metrics · Roadmap. The active tab is a filled pill in #003D29 with white text; inactive tabs are #6B7280 at 13 px. A 2 px #003D29 rule sits under the bar.
> (2) Action title: 34 px, bold, #1A1A1A, max 2 lines, left-aligned under the nav.
> (3) Takeaway line under the title: 18 px, medium, #0A8A0A, max 2 lines.
> (4) Top-right "pillar chips": small rounded tags showing which pillars of the Delegation Contract the slide uses — LEGIBLE #2563EB, BOUNDED #0A8A0A, REVERSIBLE #D97706, ACCOUNTABLE #7C3AED (white text, 11 px, caps).
> (5) "So what" callout at the bottom: full-width box, background #FFF4EC, 6 px left border #FF7009, a bold "SO WHAT →" label, then one sentence at 17 px.
> (6) Footer: 10 px #6B7280 source line on the left, page number on the right.
> **Components:** panels are #F6F7F5 with 12 px radius and no shadow. Table headers are #003D29 with white 13 px bold text; body cells are 13–14 px with 1 px #E5E7EB lines. Heat-map cells: 8–10 = #D1FAE5, 5–7 = #FEF3C7, 1–4 = #FEE2E2. The recommended row/column gets a 2 px #0A8A0A outline and a small "RECOMMENDED" tag. Code blocks use JetBrains Mono 13 px on #0F172A with light text. Maximum two accent colours per slide besides the pillar chips. Prefer tables, matrices and diagrams to bullets; never put more than ~80 words in one text box.

### A2. Per-slide prompt template
> Using the design system above, build slide [N]. Active nav tab: [TAB]. Pillar chips: [CHIPS]. Layout: [paste the slide's LAYOUT sketch]. Content: [paste the slide's blocks exactly]. Keep all copy verbatim; don't add or rewrite text. Render tables as real tables, not images.

Generate one slide per prompt and fix spacing by hand afterwards. Expect to tighten fonts on slides 7, 9 and 10, which are the densest.

### A3. Block legend used below
`[TITLE]` action title · `[TAKEAWAY]` green line under the title · `[TABLE]` · `[CHART]` · `[DIAGRAM]` · `[CARD]` · `[CODE]` · `[QUOTE]` · `[CALLOUT]` so-what box · `[FOOTER]` source line

---

## Part B — Storyline check (titles only, read top to bottom)

1. Making Instacart Agent-Ready: The Delegation Contract
2. Agents earn autonomy only as fast as Instacart makes intent legible, bounded, reversible and accountable
3. The agent isn't ours: Instacart controls only the contract and the guardrails, so we design for three users
4. Groceries score 91.5% on agentic readiness, the highest on every criterion, so the case holds under any weighting
5. Protect the board demo, but build it on the real foundation: 80% of capacity on production APIs, 20% on a demo layer that runs on them
6. Pick the Substitution-Preference API: checkout is being standardised by ACP/AP2, substitution is Instacart's moat
7. The bug isn't in either agent: it's an ambiguous contract — a unitless quantity, silent defaults and name-based matching
8. Start at 5 autonomous orders per user per month — a weekly shop plus one top-up — and let evidence move the number
9. Above any limit the agent asks, it isn't blocked: a risk-response engine that loosens only when the data earns it
10. Yes, take it seriously: here's where we're exposed, what we're doing about it, and the signals we'll watch together
11. One North Star, Trusted Agent Orders, fed by four dimensions and kept honest by counter-metrics with hard thresholds
12. Six decisions, one 90-day plan: ship trust in thin slices and widen autonomy only when the numbers earn it

---

## Part C — Slide-by-slide content

---

### SLIDE 1 — Cover
*No nav bar, no pillar chips, no so-what box.*

**LAYOUT**
```
┌──────────────────────────────────────────────────────────────┐
│  [eyebrow]                                                   │
│  [TITLE]                               ┌─────────────────┐   │
│  [SUBTITLE]                            │  [DIAGRAM]      │   │
│                                        │  delegation     │   │
│  [THESIS LINE]                         │  flow           │   │
│                                        └─────────────────┘   │
│  [Name · ID · College]                          [glance logo]│
└──────────────────────────────────────────────────────────────┘
 Left 55%: text on white. Right 45%: #003D29 panel with the diagram.
```

**[EYEBROW]** "InMobi Glance · APM Case Study · Shortlist Round · October 2026"

**[TITLE]** "Making Instacart Agent-Ready"

**[SUBTITLE]** "The Delegation Contract: six decisions for letting a user's AI assistant shop on their behalf"

**[THESIS LINE]** *(16 px, italic, #6B7280)* "Being agent-ready isn't about letting agents click faster. It's about making a user's intent legible, bounded, reversible and accountable, so an agent Instacart doesn't own can act on it safely."

**[DIAGRAM]** *(horizontal flow inside the dark panel, white line icons)*
"User" → "Phone's AI assistant" → **"Instacart contract layer"** *(highlighted box made of 4 stacked chips: LEGIBLE · BOUNDED · REVERSIBLE · ACCOUNTABLE)* → "Shopper & store" → "Doorstep"

**[NAME BLOCK]** "[Your Name]" / "[Roll No.] · [College]"

---

### SLIDE 2 — Executive Summary
*Nav: Summary · Chips: all four*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [TITLE 2 lines]                                       [chips] │
│ [TAKEAWAY]                                                    │
│ ┌LEGIBLE──┐ ┌BOUNDED──┐ ┌REVERSIBLE┐ ┌ACCOUNTABLE┐  ← 4 cards  │
│ └─────────┘ └─────────┘ └──────────┘ └───────────┘             │
│ ┌ TABLE: Q | Question | Our answer | Pillar ───────────────┐  │
│ │ 6 rows                                                   │  │
│ └──────────────────────────────────────────────────────────┘  │
│ [CALLOUT]                                                      │
│ [FOOTER]                                                       │
└────────────────────────────────────────────────────────────────┘
```

**[TITLE]** "Agents earn autonomy only as fast as Instacart makes intent legible, bounded, reversible and accountable"

**[TAKEAWAY]** "Instacart doesn't own the agent. It owns the contract the agent reads and the guardrails the agent can't bypass, so that's where every decision below is made."

**[CARDS — The Delegation Contract]** *(4 equal cards, coloured top border in the pillar colour)*

| Pillar | Definition (card body) | Instacart's lever (card footer) |
|---|---|---|
| **LEGIBLE** | "Every field, unit and preference has exactly one machine meaning." | "Schema, enums, MCP tool descriptions" |
| **BOUNDED** | "Agents act only inside limits the user has set." | "Preference API, spend and frequency caps" |
| **REVERSIBLE** | "Every agent mistake is cheap to undo." | "Cancel window, one-tap Undo" |
| **ACCOUNTABLE** | "Every agent action is attributable, logged and explainable." | "Signed mandates, per-platform monitoring" |

**[TABLE — Six decisions]** *(column widths 6% / 22% / 60% / 12%; the Pillar column uses coloured chips)*

| # | Question | Our answer | Pillar |
|---|---|---|---|
| Q1 | Why start with groceries? | "Groceries score **91.5%** on our Agentic Readiness Score and rank highest on all five criteria, so they win under any weighting. Mistakes are cheap, frequent and visible." | REVERSIBLE |
| Q2 | Flashy board demo, or push back? | "**Neither.** 80% of capacity stays on production APIs; 20% builds a demo layer *on* them. The flashy feature appears only as a labelled prototype." | ACCOUNTABLE |
| Q3 | Checkout API or Substitution-Preference API? | "**Substitution-Preference API** (4.50 vs 2.75). Checkout is converging on ACP/AP2; substitutions happen ~once per order and are Instacart's moat." | BOUNDED |
| Q4 | Why do agents read `quantity: 2` differently? | "**An ambiguous contract**, not a bad agent. Make units mandatory, match on `product_id`, and have the server read back what it understood." | LEGIBLE |
| Q5 | Orders-per-user-per-month threshold? | "**5 autonomous orders/month** (weekly shop + 1 top-up). Above it the agent asks for one-tap approval; it isn't blocked. Loosen when the unintended-order rate stays below 0.5%." | BOUNDED · REVERSIBLE |
| Q6 | "Should we be worried?" | "**Yes, honestly.** Show our exposure on each known failure mode, the mitigation, and three early signals we review with the client every week." | ACCOUNTABLE |

**[CALLOUT]** "SO WHAT → Each answer trades a little speed now for trust that compounds: an agent gets more autonomy every time the data shows it hasn't misused what it already has."

**[FOOTER]** "ACP = Agentic Commerce Protocol (OpenAI/Stripe); AP2 = Agent Payments Protocol (Google); MCP = Model Context Protocol."

---

### SLIDE 3 — Context, Assumptions & Personas
*Nav: Context · Chips: LEGIBLE, BOUNDED*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ DIAGRAM: control ──┐ ┌CARD 1 ─┐ ┌CARD 2 ─┐ ┌CARD 3 ─┐        │
│ │ boundary (32%)     │ │ User   │ │ Agent  │ │ Board  │        │
│ │                    │ │        │ │        │ │        │        │
│ └────────────────────┘ └────────┘ └────────┘ └────────┘        │
│ [ASSUMPTIONS STRIP: 4 numbered chips in one row]               │
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[TITLE]** "The agent isn't ours: Instacart controls only the contract and the guardrails, so we design for three users"

**[TAKEAWAY]** "A third-party agent will read our API literally and act at scale. That makes the agent a user persona, and the API the product."

**[DIAGRAM — Control boundary]** *(two columns separated by a dashed vertical line labelled "API / MCP boundary". Left column greyed out, right column in #003D29 tint.)*
- Left header: "**Outside our control**"
  - "The user's intent and phrasing"
  - "The agent's LLM reasoning"
  - "Which agent platform shows up"
  - "How the agent reads our docs"
- Right header: "**Inside our control**"
  - "API / MCP schema and tool descriptions"
  - "Server-side validation and guardrails"
  - "Preference and mandate store"
  - "Catalogue data (units, pack sizes)"
  - "Monitoring and per-platform kill switch"

**[CARD 1 — The User]** *(icon: person with a basket)*
- Header: "**Meera, 34 — working parent, weekly shopper**"
- "**Wants**: the weekly shop done without opening the app · her rules respected ("never substitute baby formula", "organic milk only") · to see what was bought, and undo it if it's wrong"
- "**Pain points**: 10+ minutes picking substitutes item by item · fear of the agent buying something she didn't mean · surprises at the door"
- "**What it means for us**: preferences and the cancel window are product, not settings."

**[CARD 2 — The Agent]** *(icon: phone with sparkle)*
- Header: "**The phone's AI assistant — a literal-minded new hire who reads our docs once**"
- "**Wants**: unambiguous fields with enums and examples · error messages it can self-correct from · a way to ask the user when unsure"
- "**Pain points**: unitless fields and silent defaults · products matched by name · no read-back of what the server understood"
- "**What it means for us**: treat the LLM reading our MCP docs as a user. Ambiguity we allow becomes errors at scale."

**[CARD 3 — The Business]** *(icon: chart)*
- Header: "**Instacart product VP & board**"
- "**Wants**: proof that agentic commerce is a growth channel vs ChatGPT and Amazon · an impressive board demo in 6 weeks · no public incident"
- "**Pain points**: a competitor stalled publicly · agents skip sponsored placements, while ad revenue is growing faster than GTV · zero data on agent-placed orders"
- "**What it means for us**: show progress on real rails, with guardrails visible."

**[ASSUMPTIONS STRIP]** *(4 numbered chips, 13 px)*
1. "Agents act for users at scale within 12 months (the brief's thesis)."
2. "Agents connect via Instacart's API/MCP; checkout rails partly exist (ChatGPT checkout via ACP, Dec 2025)."
3. "US market; ~$115 average order (Q2'26: $10.35B GTV ÷ 90.3M orders)."
4. "No historical data on agent-initiated orders; Q3 team = 2 engineers × 4 weeks."

**[CALLOUT]** "SO WHAT → We can't make agents smarter. We can make our contract impossible to misread and our guardrails impossible to bypass."

**[FOOTER]** "Sources: Instacart Q2 2026 results; Digital Commerce 360 (Dec 2025); Instacart Developer Platform docs (MCP)."

---

### SLIDE 4 — Q1: Why groceries
*Nav: Q1 Market · Chips: REVERSIBLE, BOUNDED*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ TABLE: ARS heat-map (62%) ─────────┐ ┌ CHART: 2×2 (38%) ──┐ │
│ │ 5 criteria × 5 domains             │ │                    │ │
│ │ + weighted score + ARS %           │ │                    │ │
│ └────────────────────────────────────┘ ├ ROBUSTNESS box ────┤ │
│ ┌ 3 REASONS (3 cards in a row) ──────────────┐ ┌ CAVEAT ───┐ │ │
│ └────────────────────────────────────────────┘ └───────────┘ │ │
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[TITLE]** "Groceries score 91.5% on agentic readiness, the highest on every criterion, so the case holds under any weighting"

**[TAKEAWAY]** "Start where agents fail cheaply, often and visibly: that's where trust gets built fastest."

**[TABLE — Framework 1: Agentic Readiness Score (ARS), weighted decision matrix, 1–10 scale]**
*(heat-map colours per the design system; Groceries column outlined as RECOMMENDED; the small grey text in brackets sits under the number at 11 px)*

| Evaluation dimension | Weight | **Groceries** | Food delivery | Travel & flights | Consumer electronics | Fashion & apparel |
|---|---|---|---|---|---|---|
| Transaction frequency & repetition | 25% | **9.0** (weekly shop; 65%+ repeat items) | 8.0 | 3.0 | 2.0 | 5.0 |
| Rule-expressibility & structure | 20% | **9.0** (brand, size, diet, price rules) | 5.0 | 6.0 | 7.0 | 3.0 |
| Cost of error & reversibility | 25% | **9.0** (~$115 basket, free cancel before picking) | 6.0 | 1.0 (high liability) | 2.0 | 5.0 |
| Existing delegation model | 15% | **10.0** (Instacart shoppers already pick for users) | 6.0 | 5.0 | 2.0 | 2.0 |
| Drudgery & automation demand | 15% | **9.0** (76% struggle with substitutions) | 4.0 | 7.0 | 3.0 | 2.0 |
| **Weighted total** | 100% | **9.15 / 10** | 6.00 / 10 | 4.00 / 10 | 3.15 / 10 | 3.70 / 10 |
| **Agentic Readiness Index** | — | **91.5%** | 60.0% | 40.0% | 31.5% | 37.0% |

*Table caption (11 px, grey):* "Criteria: Frequency builds trust fastest · Rule-expressibility = intent maps to machine-unambiguous parameters · Cost of error = blast radius of a wrong action ($115 basket vs $1,500 non-refundable flight) · Delegation model = users already let a third party pick for them · Drudgery = pain of the manual journey."

**[CHART — 2×2: Where to learn first]** *(scatter plotted from the table above: x = frequency score; y = cost of a wrong decision = 11 − cost-of-error score)*
- X axis: "Transaction frequency →" (low to high). Y axis: "Cost of a wrong decision →" (low to high).
- Quadrant labels: bottom-right "**Proving ground: learn here first**" · top-left "**Go last**" · top-right "**Gate every action**" · bottom-left "**Low learning value**".
- Points (x, y): Groceries (9, 2) *(large green dot, labelled)* · Food delivery (8, 5) · Fashion (5, 6) · Travel (3, 10) · Electronics (2, 9).

**[ROBUSTNESS BOX]** *(panel under the 2×2, header in bold)*
- "**Does the answer depend on our weights? No.**"
- "Groceries score highest on **all five** criteria, so they rank #1 under *any* weighting. Weights change the margin, never the winner."
- "Equal weights (20% each): Groceries 9.2 · Food 5.8 · Travel 4.4 · Fashion 3.4 · Electronics 3.2"
- "Closest call possible: 100% weight on frequency → Groceries 9 vs Food delivery 8. Still first."

**[3 REASONS]** *(3 cards in a row, each with a bold number)*
1. "**Instacart is already a delegation business.** ~300M replacements in 2024 at 95% satisfaction: users already trust a stranger to choose for them. The agent replaces the *relay* between user and shopper, not the trust model."
2. "**Repetition makes the agent right by default.** 65%+ of purchases are repeats, so the agent mostly *confirms* rather than *decides*."
3. "**Mistakes are cheap, visible and fixable.** ~$115 basket, low-ticket items, same-day feedback, and free cancellation until a shopper starts picking."

**[CAVEAT]** *(small panel with an amber left border)* "**Honest caveat:** perishables, allergens and hourly stock changes are hard, but an agent-ready platform must solve them anyway. **Hard rule: no autonomous substitution on allergen-flagged items. Always ask.**"

**[CALLOUT]** "SO WHAT → Groceries are hard enough to matter and safe enough to fail: the cheapest place to learn how agents break before moving to higher-stakes categories."

**[FOOTER]** "Scores are team estimates on a 1–10 scale, anchored on cited proxies. Sources: Instacart Q2'26 results; CXM World (2024 replacements); Baymard Institute (grocery substitution UX); Wave Grocery (repeat purchase)."

---

### SLIDE 5 — Q2: The board demo
*Nav: Q2 Demo · Chips: ACCOUNTABLE, REVERSIBLE*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ TABLE: 3 options (55%) ───────────┐ ┌ DEMO STORYBOARD (45%) ┐│
│ │                                   │ │ 3 numbered frames     ││
│ └───────────────────────────────────┘ │                       ││
│ ┌ CHART: 80/20 bar + 6-week strip ──┐ ├ WHY FLASHY BREAKS ────┤│
│ └───────────────────────────────────┘ └───────────────────────┘│
│ [QUOTE: what I'd say to the PM — full width]                   │
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[TITLE]** "Protect the board demo, but build it on the real foundation: 80% of capacity on production APIs, 20% on a demo layer that runs on them"

**[TAKEAWAY]** "The board isn't buying a feature; it's buying confidence the bet is real. A demo on real rails delivers that, and it's still standing when agent traffic arrives."

**[TABLE — Three options]** *(Option C row outlined as RECOMMENDED; ✅/❌ as coloured icons)*

| Option | Board demo in 6 weeks | Agent-ready foundation | Client relationship | Verdict |
|---|---|---|---|---|
| A. Build as asked | ✅ Wow | ❌ ~6 weeks lost, then a ~3-month rebuild | ✅ now, ❌ when the feature gets pulled | "Short-term win, long-term loss" |
| B. Push back and delay | ❌ No demo | ✅ Protected | ❌ Sponsor embarrassed in front of the board | "Right on the merits, politically naive" |
| **C. Reframe and time-box** | ✅ Wow, on real rails | ✅ ~80% of capacity protected | ✅ Sponsor wins twice | "**Recommended**" |

**[CHART — Capacity split]** *(one horizontal 100% bar, then a 6-column week strip underneath)*
- Bar segment 80% (#003D29): "**Foundation (80%)**: Substitution-Preference API (Q3) · unit-safe cart schema (Q4) · guardrail service (Q5)"
- Bar segment 20% (#FF7009): "**Demo layer (20%)**: scripted weekly shop by a real third-party agent on staging · labelled prototype of the flashy feature"
- Week strip: "Wk 1–4: Substitution API built (Q3)" · "Wk 5: demo script on staging + 3 dry runs" · "Wk 6: board demo"

**[DEMO STORYBOARD — 3 frames]** *(each frame = a small phone-chat bubble mock with a caption)*
1. "**"Do my weekly shop."** The agent builds the usual basket from purchase history in seconds."
2. "**Organic milk is out of stock.** The agent substitutes within the user's rule (same brand, ≤ +5% price) and explains why."
3. "**The agent tries to add 10 kg of flour (5× normal).** The guardrail pauses and asks the user to confirm. *Trust is the wow moment.*"
- Footer tag on the frame group: "Flashy feature → shown as a Wizard-of-Oz prototype, labelled **'Vision: next quarter'**"

**[WHY FLASHY BREAKS]** *(small panel, bullets)*
- "**Why the as-asked feature breaks under real traffic.** It assumes:"
  - "a human confirms every step"
  - "one agent at a time"
  - "everything is in stock"
  - "no retries or duplicate calls"
  - "no rate limits"

**[QUOTE — What I'd say to the PM]** *(large quote marks, 17 px italic)*
"Let's make sure the board sees something impressive in six weeks, and that it's still standing when real agent traffic arrives. Here's a demo that does both. If you still want the original feature after seeing the trade-offs, we'll build it, with the rebuild plan agreed upfront so nobody is surprised in three months."
*(small tag under the quote: "Disagree and commit")*

**[CALLOUT]** "SO WHAT → A labelled prototype protects credibility; an unlabelled one becomes the over-promise risk we flag in Q6."

**[FOOTER]** "Assumption: the 'flashier feature' is a demo-only capability that bypasses guardrails or uses mocked inventory. Frameworks: one-way vs two-way doors, disagree-and-commit, pre-mortem."

---

### SLIDE 6 — Q3: Which API to make agent-readable
*Nav: Q3 Build · Chips: BOUNDED, LEGIBLE*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ TABLE: weighted matrix (55%) ─────┐ ┌ 4 ARGUMENTS (45%) ────┐│
│ │                                   │ │ numbered list         ││
│ └───────────────────────────────────┘ ├ WOULD FLIP IF (box) ──┤│
│ ┌ CHART: 4-week Gantt, 2 engineers (full width) ─────────────┐ │
│ └────────────────────────────────────────────────────────────┘ │
│ [SUCCESS METRICS strip: 3 KPI tiles]                           │
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[TITLE]** "Pick the Substitution-Preference API: checkout is being standardised by ACP/AP2, substitution is Instacart's moat"

**[TAKEAWAY]** "Without preferences, an agent either pings the user on almost every order or guesses. Either way, it stops being a trusted shopper."

**[TABLE — Weighted decision matrix, 1–5 scale]** *(Substitution column outlined as RECOMMENDED)*

| Criterion | Weight | Checkout API | **Substitution-Preference API** |
|---|---|---|---|
| User value: unblocks autonomy | 30% | 3 — completes the purchase, but a human can already confirm it | **5** — without it, the agent interrupts or guesses on ~every order |
| Differentiation / moat | 20% | 2 — being commoditised by ACP, AP2, Visa and Mastercard agent rails | **5** — built on Instacart's preference data and replacement models |
| Risk & reversibility in 4 weeks | 20% | 2 — money path, irreversible, fraud surface | **4** — data/rules API, small blast radius |
| Feasible with 2 engineers × 4 weeks | 15% | 3 — payments, auth, idempotency, compliance | **4** — scoped schema + endpoints + escalation hook |
| Measurability | 15% | 4 | **4** |
| **Weighted score** | 100% | **2.75 / 5 (55%)** | **4.50 / 5 (90%)** |

**[4 ARGUMENTS]**
1. "**Checkout has a workaround; substitutions don't.** Agentic checkout already runs in ChatGPT (ACP), and a one-tap human confirmation at checkout is *desirable* early on (see Q5)."
2. "**Substitutions are the norm, not the edge case.** ~300M replacements in 2024, about one per order."
3. "**Sequencing.** Preferences make autonomous checkout safe. Shipping checkout first scales bad substitutions, which means complaints, and complaints get programmes killed."
4. "**Don't hand-build what the industry is standardising.** Adopt ACP/AP2 for checkout; spend scarce engineers on what only Instacart can build."

**[WOULD FLIP IF]** *(amber-bordered box)* "**I'd flip to checkout if** no agent can complete a purchase at all, i.e. no ACP or hand-off path exists. Then checkout is the binding constraint."

**[CHART — 4-week Gantt]** *(rows = workstreams, columns = Wk 1–4 plus a faded Wk 5–6 column; bars labelled E1 / E2 / E1+E2)*

| Workstream | Wk 1 | Wk 2 | Wk 3 | Wk 4 | Wk 5–6 *(faded)* |
|---|---|---|---|---|---|
| Preference schema *(E1+E2)* | ███ "Per item: `allow_substitution`, ranked alternates by `product_id`, brand lock, size ±%, price ceiling ±%, diet/allergen tags, `on_unavailable: substitute / skip / ask_user`; category defaults" | | | | |
| API + MCP tools | | ███ E1: "read/write endpoints, v1" · E2: "MCP tool definitions with enums and worked examples" | | | |
| Explain + escalate | | | ███ E1: "explanation payload ('X → Y: same brand, +4% price, within your rule')" · E2: "`ask_user` escalation webhook" | | |
| Test + pilot *(E1+E2)* | | | | ███ "Conformance tests with 2 agent platforms · 100-case substitution eval set · pilot cohort" | "Powers the board demo (Q2)" |

**[SUCCESS METRICS — 3 tiles]**
- "**≥ 95%** substitution acceptance (human-shopper baseline)"
- "**↓ trend** in `ask_user` escalations per order (more autonomy)"
- "**≤ baseline** refund rate on substituted items (guardrail)"

**[CALLOUT]** "SO WHAT → The Substitution-Preference API *is* the 'boundaries the user has set' in the brief. It turns the agent from an assistant that asks into a shopper that knows."

**[FOOTER]** "Sources: Instacart × ChatGPT checkout via ACP (Dec 2025); Google AP2 (Sep 2025); CXM World (2024 replacements, 95% satisfaction)."

---

### SLIDE 7 — Q4: The `quantity: 2` bug
*Nav: Q4 Contract · Chips: LEGIBLE, ACCOUNTABLE*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ DIAGRAM: 6-layer RCA stack (55%) ─┐ ┌ CODE: before/after ───┐│
│ │ layer | hypothesis | check | lik. │ │ (dark block, 45%)     ││
│ │                                   │ ├ DIAGNOSTIC RULE box ──┤│
│ └───────────────────────────────────┘ └───────────────────────┘│
│ ┌ 3 HORIZONS: Days | Weeks | Quarter (3 columns) ────────────┐ │
│ └────────────────────────────────────────────────────────────┘ │
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[TITLE]** "The bug isn't in either agent: it's an ambiguous contract — a unitless quantity, silent defaults and name-based matching"

**[TAKEAWAY]** "If two agents can read one field two ways, at scale they will. Make the contract strict, and make the server say back what it understood."

**[DIAGRAM — Layered RCA]** *(6 stacked horizontal bars, top = closest to the user. A likelihood chip sits on the right: LOW grey, MED amber, HIGH red. Layers 3 and 4 are outlined in red and labelled "ROOT CAUSE".)*

| Layer | What could be wrong | How we check | Likelihood |
|---|---|---|---|
| 1. User intent | "Get 2 wheat" is genuinely ambiguous | Compare both users' original instructions | LOW |
| 2. Agent interpretation | Each LLM maps intent to fields differently; neither asks | Diff the raw request payloads from both platforms | MED |
| **3. API / MCP contract** | `quantity` has no unit, or `unit` is optional with a silent default of `each`; tool docs are prose, with no enums or examples | Read the schema: does `quantity` alone have exactly one meaning? | **HIGH — root cause** |
| **4. Product resolution** | Product matched by name: "wheat" resolves to a single unit for one agent and a 1 kg pack SKU for the other | Compare the resolved `product_id`s | **HIGH — root cause** |
| 5. Catalogue data | Unit of sale (each / weight / pack) isn't machine-readable | Audit `sold_by` / `pack_size` coverage | MED |
| 6. Validation & feedback | Server accepted ambiguous input and never echoed its interpretation | Does the response return a normalised line item? | HIGH — why nobody noticed |

**[CODE — Before / after]**
```
// BEFORE — ambiguous, accepted silently
POST /cart/items
{ "name": "wheat", "quantity": 2 }
→ Agent A gets: 2 units      → Agent B gets: 2 × 1 kg packs

// AFTER — strict request
POST /cart/items
{ "product_id": "88123", "quantity": 2, "unit": "pack",
  "idempotency_key": "a7f3-…" }

// AFTER — server read-back
200 OK
{ "resolved": "2 × Whole Wheat Flour (1 kg pack) = 2 kg",
  "line_total": "$7.98", "requires_confirmation": false }

// AFTER — self-correcting error when the unit is missing
422 { "error": "unit_required",
      "hint": "Sold by pack (1 kg). Did you mean
               quantity=2, unit=pack (2 kg total)?" }
```

**[DIAGNOSTIC RULE BOX]** *(panel below the code)*
- "**Diagnostic rule:** same payload, different result → server bug. Different payloads → contract and documentation bug."
- "**It's real:** Instacart's own `LineItem` schema defaults `quantity` to `1.0` and `unit` to `"each"`, matches products by `name`, and has deprecated both fields in favour of `line_item_measurements`."

**[3 HORIZONS]** *(3 columns with header pills: "DAYS", "WEEKS", "QUARTER")*
- **Days — stop the bleeding**
  - "Make `unit` mandatory: enum `each · pack · kg · g · lb · l`; no silent defaults"
  - "Reject ambiguous input with self-correcting errors an LLM can act on"
  - "Read back every cart write in plain language"
  - "Anomaly guard: quantity > 3× the user's usual → confirm"
- **Weeks — fix the contract**
  - "`product_id` / UPC required on the order path (names only for search)"
  - "JSON Schema / OpenAPI enums; MCP descriptions with worked ambiguous examples"
  - "Dry-run quote endpoint: a priced, normalised cart before commit (AP2 Cart Mandate pattern)"
- **Quarter — make it structural**
  - "Canonical units on every SKU: `sold_by`, `pack_size`, `net_content`"
  - "Agent conformance suite gates production write access"
  - "Per-platform monitoring: quantity-edit rate, wrong-quantity refunds, divergence alerts"
  - "Versioned API, so fixes don't break live integrations"

**[CALLOUT]** "SO WHAT → Be strict in what you accept from agents. This inverts Postel's law: liberal acceptance turns into silent divergence at scale."

**[FOOTER]** "Source: Instacart Developer Platform API — Create shopping list page (LineItem schema). Product and price in the example are illustrative."

---

### SLIDE 8 — Q5a: The threshold
*Nav: Q5 Guardrails · Chips: BOUNDED, REVERSIBLE*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ BIG NUMBER "5" ┐ ┌ CHART: anchoring ladder (40%) ┐ ┌ COST OF ┐│
│ │  per user/mo   │ │ 4 steps to 5                  │ │ ERROR   ││
│ └────────────────┘ └───────────────────────────────┘ │ 2 cards ││
│ ┌ TABLE: sensitivity 3 / 5 / 10 (60%) ┐ ┌ INCENTIVE ─┘ conflict ┐│
│ └─────────────────────────────────────┘ └──────────────────────┘│
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[TITLE]** "Start at 5 autonomous orders per user per month — a weekly shop plus one top-up — and let evidence move the number"

**[TAKEAWAY]** "The goal isn't fewer orders, it's fewer *unintended* ones. With no agent data, anchor on human behaviour and on what each kind of mistake costs."

**[BIG NUMBER]** *(huge "5" in #003D29, ~160 px)* Caption: "autonomous agent orders / user / month at launch". Sub-caption: "Above it the agent **asks**. It isn't blocked."

**[CHART — Anchoring ladder: how we got to 5]** *(4 ascending steps, each with a number and a one-liner)*
1. "**~2–3** — orders/month by an average active Instacart customer *(est.)*"
2. "**4.3** — a weekly shop, the brief's core use case (52 ÷ 12)"
3. "**+1** — a mid-week top-up; ~40% of online grocery shoppers order weekly, many top up"
4. "**= 5** — covers a weekly shopper's normal month. Most users never hit it; in a 5-Saturday month a heavy user gets one one-tap ask."

**[COST OF ERROR — 2 cards side by side]**
- Card (green): "**False alarm** — we ask a genuine user to approve order #6" / "**Cost: one tap, ~5 seconds**"
- Card (red): "**Miss** — an unintended order goes through" / "**Cost: ~$115 refund + wasted perishables + shopper time + a support ticket + the user's trust in agent ordering**"
- Line under both cards: "When a miss costs orders of magnitude more than a false alarm, **start tight and loosen with evidence.**"

**[TABLE — Sensitivity: why not 3 or 10?]** *(the 5/month row is outlined as CHOSEN)*

| Cap | What a genuine weekly shopper experiences | What a misfiring agent can do | Verdict |
|---|---|---|---|
| 3 / month | Asked to approve from week 4, every month | Little | ❌ Breaks the weekly-shop promise |
| **5 / month** | **Weekly shop + 1 top-up fully autonomous** | **Caught by the weekly cap and duplicate check (next slide)** | ✅ **Chosen** |
| 10 / month | Almost never asked | Up to ~2× a normal month before anyone notices | ❌ Too loose with zero data |

**[INCENTIVE CONFLICT BOX]**
- "**Name the incentive conflict.** Instacart earns more when agents order more, but every unintended order is a refund plus churn risk."
- "So the guardrail sits on the **unintended-order rate**, not on order volume."

**[CALLOUT]** "SO WHAT → The number matters less than the system around it: ask instead of block, an undo window, and a feedback loop that moves the number."

**[FOOTER]** "~2–3 orders/month is an estimate from ~30M monthly orders across ~15M active customers. Sources: Instacart Q2'26 and Q3'25 results; Wave Grocery (weekly ordering)."

---

### SLIDE 9 — Q5b: The guardrail engine
*Nav: Q5 Guardrails · Chips: BOUNDED, REVERSIBLE, ACCOUNTABLE*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ TABLE: guardrails (55%) ──────────┐ ┌ DIAGRAM: 4 tiers ─────┐│
│ │ 9 rows                            │ │ green/amber/red/stop  ││
│ │                                   │ ├ MANDATE card + notif. ┤│
│ └───────────────────────────────────┘ └───────────────────────┘│
│ ┌ CHART: phase timeline 0 → 1 → 2 with gates ────────────────┐ │
│ └────────────────────────────────────────────────────────────┘ │
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[TITLE]** "Above any limit the agent asks, it isn't blocked: a risk-response engine that loosens only when the data earns it"

**[TAKEAWAY]** "Order count is only a proxy. We pair it with spend, anomaly and duplicate checks, an undo window, and a signed mandate."

**[TABLE — Launch guardrails]**

| Guardrail | Launch default | When crossed | Tier |
|---|---|---|---|
| Autonomous orders / month | 5 | One-tap approval; order held, not cancelled | AMBER |
| Autonomous orders / week | 2 (1 scheduled + 1 top-up) | One-tap approval | AMBER |
| Monthly agent spend | ≤ 1.25× trailing 3-month grocery spend, or the user's own cap | One-tap approval | AMBER |
| Basket value per order | ≤ 1.5× the user's typical basket | One-tap approval | AMBER |
| Quantity of one item | > 3× the user's usual (Q4) | Confirm that line, with read-back | RED |
| Duplicate order within 24 h | Always flagged | Confirm; idempotency key required | RED |
| New address or payment method | Always | Explicit confirmation | RED |
| Allergen-flagged substitution | Never autonomous | `ask_user` | RED |
| Cancel window | Free until the shopper starts picking (≥ 30 min) | "Undo" in every notification | — |

**[DIAGRAM — Response tiers]** *(4 stacked tiles, coloured)*
- **GREEN — Inside the mandate:** "Order placed autonomously + notification with Undo"
- **AMBER — Soft limit crossed:** "Order held; user approves with one tap"
- **RED — Hard rule hit:** "Explicit confirmation with a plain-language read-back"
- **STOP — Platform-level unintended rate > 1%:** "That agent platform drops to confirm-every-order until fixed"

**[MANDATE CARD]** *(styled like a signed ticket)*
- Header: "**Standing mandate (AP2-style Intent Mandate)**"
- Body: "Weekly shop · Saturdays · up to $150 · substitutions per my rules · max 5 autonomous orders/month"
- Footer: "Signed mandate + signed cart = non-repudiable evidence when a user says 'I didn't mean to'."

**[NOTIFICATION MOCK]** *(phone lock-screen banner)* "🛒 Your assistant ordered your weekly shop — $112, arriving Sat 10 am. **[View] [Undo]**"

**[CHART — Phased rollout]** *(3 chevrons with a gate diamond between each)*
- **Phase 0 · Weeks 0–2 · Dogfood:** "Employees only; every agent order confirmed; collect baseline data"
- ◆ Gate: "Unintended-order rate < 1%"
- **Phase 1 · Weeks 3–10 · Launch:** "5 autonomous orders/month for a 1–5% user cohort; undo window live"
- ◆ Gate: "< 0.5% for 4 consecutive weeks"
- **Phase 2 · Week 10+ · Personalise:** "Cap = max(5, user's P90 monthly orders + 1) once 8+ weeks of data exist"
- Gate legend (right of the timeline): "**Loosen** < 0.5% · **Hold** 0.5–1% · **Tighten / roll back** > 1%"
- Definition (11 px): "Unintended-order rate = (cancellations inside the window + 'didn't intend' complaints) ÷ agent-placed orders"

**[CALLOUT]** "SO WHAT → Reversibility is the deciding variable: automate what can be undone, gate what can't. Groceries' natural undo window is what lets us loosen the cap safely."

**[FOOTER]** "Sources: Google AP2 (Intent and Cart Mandates); Visa Intelligent Commerce / Mastercard Agent Pay (agent tokens with spending limits)."

---

### SLIDE 10 — Q6: "Should we be worried?"
*Nav: Q6 Risk · Chips: ACCOUNTABLE*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ QUOTE: what I'd say (40%) ─┐ ┌ TABLE: risk register (60%) ──┐│
│ │                            │ │ 6 rows                       ││
│ ├ BASE RATE box ─────────────┤ │                              ││
│ └────────────────────────────┘ └──────────────────────────────┘│
│ ┌ NO-REGRET MOVES (60%) ─────────┐ ┌ 3 SIGNALS WE WATCH (40%) ┐ │
│ └────────────────────────────────┘ └──────────────────────────┘ │
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[TITLE]** "Yes, take it seriously: here's where we're exposed, what we're doing about it, and the signals we'll watch together"

**[TAKEAWAY]** "Honest beats reassuring. Turn the client's anxiety into a shared risk plan, and never bad-mouth the competitor or their consultants."

**[QUOTE — What I'd say, verbatim]** *(large quote panel, 16 px)*
"It's a fair question, and I won't pretend there's no risk. We have real uncertainty too, mainly how fast agent traffic actually arrives and how differently each agent platform behaves.
Projects like that one usually stall for a few predictable reasons: a big-bang rewrite with nothing shipped for months, demos that over-promise, no guardrails so the first incident goes public, and unclear ownership so people blame each other.
Here's how we're set up against each of those, and where I think we're still exposed. I'd suggest we run a joint pre-mortem this week and agree on three signals that would tell us early if we're drifting."

**[BASE RATE BOX]**
- "**Base rate:** Gartner expects **> 40%** of agentic AI projects to be cancelled by end-2027, citing *cost, unclear value and inadequate risk controls.*"
- "Each of the three maps to a mitigation on the right."

**[TABLE — Risk register]** *(the Exposure column uses chips; HIGH rows get a light red row tint)*

| Common failure mode | Our exposure | Mitigation | Early-warning signal |
|---|---|---|---|
| Big-bang rewrite, nothing shipped for months | MED | Thin vertical slices every 2–4 weeks, each with a measurable outcome | No shipped slice in 4 weeks |
| Over-promised demo | **HIGH** (Q2) | Demo on real rails; prototypes labelled as prototypes | Board asks for a launch date on a prototype |
| No guardrails → public incident | MED | Q5 guardrails, staged cohorts, incident playbook | Unintended-order rate > 0.5% |
| Ambiguous contracts break with real agents | MED | Q4 conformance suite before production write access | Per-platform divergence alert |
| Agent adoption slower than the thesis | **HIGH** | No-regret moves (below) | Agent orders below plan two months running |
| Unclear ownership → blame | LOW–MED | Joint RACI, shared weekly risk register, pre-agreed kill/pivot criteria | Decisions slipping > 1 week |

**[NO-REGRET MOVES]** *(panel with a check-mark icon)*
- "**Even if agents arrive late, the work isn't wasted.** It improves the human app too:"
  - "Structured units → fewer wrong-quantity refunds"
  - "Preference API → better human-shopper substitutions"
  - "Idempotent cart and checkout → fewer duplicate orders"
- "The downside is bounded."

**[3 SIGNALS WE WATCH TOGETHER]** *(3 small KPI tiles)*
1. "Unintended-order rate"
2. "Conformance pass rate per agent platform"
3. "% of milestones shipped on time"

**[CALLOUT]** "SO WHAT → Teams get blamed for surprises, not for risks. A shared, written risk register removes the surprise."

**[FOOTER]** "Sources: Gartner via Outlook Business (Jun 2025); MIT NANDA via Fortune (Aug 2025: ~95% of GenAI pilots stall before scaled impact)."

---

### SLIDE 11 — Metrics & Dashboard
*Nav: Metrics · Chips: all four. Layout modelled on the "Product initiatives → KPI → Dimension → North Star" tree.*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ DIAGRAM: metric tree (full width, ~45% height) ────────────┐ │
│ │ Initiatives  →  KPI  →  Dimension  ⟶  ( NORTH STAR )        │ │
│ │ 4 rows                                                      │ │
│ └─────────────────────────────────────────────────────────────┘ │
│ ┌ TABLE: counter-metrics (60%) ─────┐ ┌ BUSINESS + OPEN Q (40%)┐│
│ └───────────────────────────────────┘ └────────────────────────┘│
│ [CALLOUT]                                                      │
└────────────────────────────────────────────────────────────────┘
```

**[TITLE]** "One North Star, Trusted Agent Orders, fed by four dimensions and kept honest by counter-metrics with hard thresholds"

**[TAKEAWAY]** "We count only orders that land as the user intended. Volume without trust is how agentic programmes get cancelled."

**[DIAGRAM — Metric tree]** *(4 columns with headers "Initiatives" · "KPI" · "Dimension" · "North Star". Initiative boxes in teal (#A7D8DE), KPI pills in light blue (#CFE3FA), dimension pills in lavender (#D9D2F5), North Star = large blue circle with a star icon. Curved arrows from each dimension converge on the circle.)*

| Initiatives (from this deck) | KPI | Dimension |
|---|---|---|
| • Mandate onboarding • ACP / MCP agent partnerships • Conformance certification | # users with an active agent mandate | **Breadth** |
| • Substitution-Preference API (Q3) • Category defaults • Substitution explanations | % of basket completed with no user interruption | **Depth (autonomy)** |
| • Recurring list • Standing weekly mandate • Smart top-up suggestions | Agent orders per user per month | **Frequency** |
| • Unit-safe contract (Q4) • Guardrail engine (Q5) • Undo window | % of agent orders delivered as intended | **Trust** |

- North Star circle text: "**Trusted Agent Orders / week**"
- Definition under the circle (12 px): "Agent-initiated orders that were delivered and *not* cancelled, refunded for intent reasons, or complained about."

**[TABLE — Counter-metrics: every guardrail has a threshold and a consequence]**

| Counter-metric | Threshold | If breached |
|---|---|---|
| Unintended-order rate | < 0.5% to loosen | > 1% → roll back the Q5 cap |
| Wrong-quantity refund rate | ≤ human-app baseline | Suspend that platform's write access |
| Substitution complaint rate | ≤ human-shopper baseline | Default affected categories to `ask_user` |
| Support tickets / 1,000 agent orders | ≤ human-app baseline | Incident review within 48 h |
| `ask_user` escalations / order | Falling week over week | Flat for 4 weeks → revisit preference defaults |

**[BUSINESS + OPEN QUESTION]** *(panel)*
- "**Business health**"
  - "GTV through the agent channel"
  - "90-day retention: agent users vs app-only users"
- "**Open strategic question: ad revenue at risk.** Agents skip sponsored placements, and ads are growing faster than GTV. Option to test: sponsored results exposed via the API, with disclosure."

**[CALLOUT]** "SO WHAT → A guardrail has a threshold and a consequence. A counter-metric you only watch is just another chart."

**[FOOTER]** "Framework: North Star → input metrics → counter-metrics (IIMA Product Casebook)."

---

### SLIDE 12 — Roadmap & Next Steps
*Nav: Roadmap · Chips: all four*

**LAYOUT**
```
┌ nav ───────────────────────────────────────────────────────────┐
│ [TITLE]                                               [chips] │
│ [TAKEAWAY]                                                    │
│ ┌ TABLE: phase grid — 4 workstreams × 3 periods (full width) ┐ │
│ └────────────────────────────────────────────────────────────┘ │
│ ┌ FIRST 30 DAYS: assumption → test → rethink if (60%) ┐ ┌ WE'RE ┐│
│ └─────────────────────────────────────────────────────┘ │ACCEPT.││
│ [CLOSING LINE — large, centred]                          └───────┘│
└────────────────────────────────────────────────────────────────┘
```

**[TITLE]** "Six decisions, one 90-day plan: ship trust in thin slices and widen autonomy only when the numbers earn it"

**[TAKEAWAY]** "Each workstream maps to one pillar of the Delegation Contract, and every phase ends in a measurable gate."

**[TABLE — 90-day phase grid]** *(row labels are vertical pillar-coloured tabs, like the Samsung deck's side labels; cells are rounded boxes)*

| Workstream | Weeks 0–4 | Weeks 5–8 | Weeks 9–12 |
|---|---|---|---|
| **Contract** (LEGIBLE · Q4) | Mandatory unit enum · read-back · self-correcting errors | `product_id`-only order path · dry-run quote endpoint | Canonical catalogue units · conformance certification |
| **Preferences** (BOUNDED · Q3) | Substitution-Preference API v1 | Pilot cohort · 100-case eval | Category defaults · personalisation |
| **Guardrails** (REVERSIBLE · Q5) | Phase 0 dogfood · undo notifications | Phase 1: 5/month for 1–5% of users | Phase 2: personalised caps if < 0.5% |
| **Client & board** (ACCOUNTABLE · Q2, Q6) | Joint RACI · weekly shared risk register | **Week 6: board demo on real rails** | Data-backed kill / pivot / scale review |

**[TABLE — First 30 days: what we'll validate]**

| Assumption | Test | Rethink if |
|---|---|---|
| Users will set preferences | % of pilot users who set ≥ 3 rules at onboarding | < 30% |
| 5/month fits real cadence | % of pilot users who hit the cap | > 15% |
| Agents honour a strict schema | Conformance pass rate of the first 2 agent platforms | < 90% |

**[WHAT WE'RE ACCEPTING]** *(amber-bordered panel)*
- "Checkout stays human-confirmed for the first months."
- "The flashy demo feature ships only as a labelled prototype."
- "Ad-revenue impact stays an open question this quarter."

**[CLOSING LINE]** *(22 px, #003D29, centred)* "Autonomy is earned, not granted. Instacart's job is to make it safe to earn."

**[FOOTER]** "Full sources and calculations in the appendix."

---

### APPENDIX — Sources & Calculations
*Nav: none (or a small "Appendix" tag). Two columns, plain text, 12 px.*

**Left column — Calculations**
- "**Average order value:** $10.35B GTV ÷ 90.3M orders (Q2 2026) = **~$115**"
- "**Replacements per order:** ~300M replacements ÷ ~290M orders (2024, approx.) ≈ **1 per order**"
- "**Weekly cadence:** 52 weeks ÷ 12 months = **4.33 orders/month**"
- "**ARS (Q1):** weighted sum of 1–10 scores. Groceries = 9×0.25 + 9×0.20 + 9×0.25 + 10×0.15 + 9×0.15 = **9.15 → 91.5%**. Food 6.00 · Travel 4.00 · Fashion 3.70 · Electronics 3.15."
- "**ARS robustness:** equal weights → Groceries 9.2 · Food 5.8 · Travel 4.4 · Fashion 3.4 · Electronics 3.2."
- "**Q3 matrix:** Checkout = 3×0.30 + 2×0.20 + 2×0.20 + 3×0.15 + 4×0.15 = **2.75**; Substitution = 5×0.30 + 5×0.20 + 4×0.20 + 4×0.15 + 4×0.15 = **4.50**."

**Right column — Sources**
- "Instacart Q2 2026 financial results (PR Newswire / Morningstar, Aug 2026)"
- "Instacart × ChatGPT checkout via ACP (Digital Commerce 360, Dec 2025)"
- "Instacart Developer Platform: MCP guide; Create shopping list page (LineItem schema)"
- "Instacart 2024 replacements & satisfaction (CXM World)"
- "Baymard Institute: grocery substitution UX"
- "Wave Grocery: repeat-purchase and weekly-ordering behaviour"
- "Google AP2 (Analytics Vidhya, Vellum, Sep 2025)"
- "Visa Intelligent Commerce / Mastercard Agent Pay (Digital Commerce 360, May 2025)"
- "McKinsey: The agentic commerce opportunity"
- "Gartner agentic AI forecast (Outlook Business, Jun 2025)"
- "MIT NANDA GenAI pilots (Fortune, Aug 2025)"
- "IIMA Product Casebook 2026–27"

---

## Part D — Pre-submission checklist
- [ ] Read only the 12 titles: do they tell the full story?
- [ ] Every number on a slide appears in the appendix calculations or has a source in the footer.
- [ ] Estimates are marked "~" or "est.".
- [ ] Q2, Q3 and Q5 each state a clear choice *and* a "would flip if" or a rollback condition.
- [ ] No text box over ~80 words; the densest slides (7, 9, 10) are still readable at 100% zoom in the PDF.
- [ ] Consistency: Q3 says checkout stays human-confirmed early, and Q5 and slide 12 say the same.
- [ ] Open every source link once and confirm the figure before submitting.
