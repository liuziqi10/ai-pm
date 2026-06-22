# Competitive Analysis Framework — Detailed Methodology

## When to Read This

Read this reference when:
- The user needs a specific framework applied (Porter's Five Forces, Blue Ocean, etc.)
- The competitive landscape is complex with many players
- The user asks for methodology justification
- You need to produce a battle card or executive-ready summary

---

## Framework 1: Porter's Five Forces

Use when: Analyzing market attractiveness and competitive intensity for strategic decisions (market entry, pricing strategy, investment).

**Apply it:**

1. **Threat of New Entrants**
   - Barriers to entry (capital requirements, regulation, network effects, switching costs)
   - Incumbent retaliation history
   - Rating: High / Medium / Low

2. **Bargaining Power of Suppliers**
   - Number and concentration of suppliers
   - Uniqueness of their offering
   - Switching cost to alternatives
   - Rating: High / Medium / Low

3. **Bargaining Power of Buyers**
   - Buyer concentration vs fragmentation
   - Switching costs for buyers
   - Price sensitivity
   - Rating: High / Medium / Low

4. **Threat of Substitutes**
   - Alternative solutions (not just direct competitors)
   - Price-performance trade-off of substitutes
   - Buyer propensity to substitute
   - Rating: High / Medium / Low

5. **Industry Rivalry**
   - Number and diversity of competitors
   - Industry growth rate
   - Exit barriers
   - Rating: High / Medium / Low

**Output:** A summary paragraph per force with the rating and the key evidence. Conclude with: "This market is [attractive/challenging/dangerous] because..."

---

## Framework 2: Feature Comparison Matrix

Use when: Comparing specific product capabilities across competitors.

**Scoring systems (pick one):**

**Simple (3-value):**
- ✓ = Fully supported
- Partial = Limited or poor implementation
- ✗ = Not supported

**Detailed (5-value):**
- ★★★ = Best-in-class
- ★★ = Solid
- ★ = Basic
- ○ = Not available
- ? = Unknown (couldn't verify)

**Best practices for feature matrices:**
1. **Group features by category** (Core, Collaboration, Integration, Security, etc.)
2. **Avoid feature stuffing** — only include features that matter to the target user's decision process
3. **Note recency** — mark features added in last 6 months with `[new]`
4. **Include "table stakes"** features so the matrix doesn't look cherry-picked to favor one competitor
5. **Add a "Why it matters" column** explaining the user benefit of each feature

**After the matrix, always include:**
- **Coverage summary:** Raw count and percentages
- **Gap analysis:** Where does our product have unique strengths? Where are we behind?
- **Differentiation assessment:** Are the differences meaningful to customers or just checkbox items?

---

## Framework 3: SWOT Analysis

Use when: Synthesizing internal and external factors for strategic planning.

**Quality checklist for each quadrant:**

**Strengths (Internal / Positive):**
- Must be truly distinctive — not "good UX" unless backed by evidence
- Ask: "Do competitors also have this?" If yes, it's table stakes, not a strength
- Include specific evidence (awards, reviews, benchmarks)

**Weaknesses (Internal / Negative):**
- Be honest — sugarcoating weaknesses leads to bad strategy
- Distinguish between fixable (missing features) and structural (business model limitation)
- Include user feedback citations

**Opportunities (External / Positive):**
- Must be external — market trends, regulatory changes, technology shifts
- Not "build feature X" (that's a strategy, not an opportunity)
- Include timeline (short-term < 6mo, medium-term 6-18mo, long-term 18mo+)

**Threats (External / Negative):**
- Competitor moves, market shifts, regulatory risk, talent competition
- Include leading indicators (what would we see first if this materialized?)

---

## Framework 4: Positioning Map

Use when: Visualizing competitive positioning and identifying market whitespace.

**Common axis pairs (pick the most revealing for the market):**

| X-Axis | Y-Axis | Best For |
|--------|--------|----------|
| Price (Low → High) | Features (Basic → Advanced) | General SaaS |
| Ease of Use (Simple → Complex) | Power/Depth (Shallow → Deep) | Tool/Platform markets |
| Individual (Solo) | Team/Enterprise (Large Orgs) | Collaboration tools |
| General Purpose | Specialized/Niche | Horizontal vs Vertical |
| Self-Serve | High-Touch/Managed | Service-heavy products |

**Method:**
1. Choose the 2 axes most relevant to the competitive dynamic
2. Place each competitor on the grid with a rationale
3. Identify whitespace (quadrants with no players) and overcrowded zones
4. Draw a "Vector of differentiation" arrow showing where the market is moving

**Output the map as a text description:**
```
                    High Features
                        |
    Competitor A ●      |      ● Competitor B
                        |
    ---------------------+----------------------
                        |
    Competitor C ●      |      ○ OUR PRODUCT
                        |
                    Low Features
```
Then explain: "The top-right quadrant is crowded. The bottom-right (our position) represents high ease-of-use with focused features — a differentiated position if we message it clearly."

---

## Framework 5: Blue Ocean Strategy Canvas

Use when: Looking for uncontested market space rather than competing head-to-head.

**Method:**
1. List 6-10 key competing factors in the industry
2. Score each competitor and your product on a 1-10 scale for each factor
3. Identify factors where you can:
   - **Eliminate:** What factors can be removed entirely? (features no one actually uses)
   - **Reduce:** What can be reduced well below industry standard? (complexity, cost)
   - **Raise:** What can be raised well above industry standard? (UX quality, speed)
   - **Create:** What new factors can be introduced? (community, AI assistance, API-first)

**Output as a table:**
| Competing Factor | Competitor A | Competitor B | Us | Action |
|-----------------|-------------|-------------|-----|--------|
| Price | 8 | 6 | 4 | Reduce (freemium) |
| Feature Depth | 9 | 8 | 5 | Reduce (simplify) |
| Ease of Use | 3 | 4 | 10 | Raise |
| AI Assistance | 0 | 0 | 9 | Create |

---

## Battle Card Format

When the user needs a portable, sales-ready summary:

```markdown
# Battle Card: [Competitor Name]

## At a Glance
- **Competitor:** [Name]
- **Category:** [Direct/Indirect/Aspirational]
- **Threat Level:** 🔴 High / 🟡 Medium / 🟢 Low
- **Last Updated:** [Date]

## Their Pitch
[How do they describe themselves? Copy from their website.]

## Where They Win
1. [Scenario where they beat us]
2. ...

## Where We Win
1. [Scenario where we beat them]
2. ...

## Competitive Objection Handling
| Customer Says | We Say |
|--------------|--------|
| "[Competitor] has feature X" | [Response with specific counter] |
| "[Competitor] is cheaper" | [Value-based response, not price war] |

## Key Differentiators
- **Us:** [What makes us unique]
- **Them:** [What makes them unique]

## Recent Intel
- [Product updates, funding, leadership changes, pricing changes]
```

---

## Sources & Research Methods

**Priority order for research quality:**
1. **Primary:** Product usage (trial accounts, demos, screenshots), official docs
2. **Secondary:** G2/Capterra reviews, ProductHunt, Reddit, Hacker News
3. **Tertiary:** Press coverage, analyst reports (Gartner, Forrester), funding announcements
4. **Inference:** Job listings (reveals tech stack and roadmap), engineering blogs, patent filings

**For each claim in the analysis:**
- If from primary source → no citation needed (state "from direct product testing")
- If from secondary/tertiary → cite with URL
- If inferred → flag with `[inferred]` marker

**Common research blind spots:**
- Over-relying on competitor marketing (they exaggerate)
- Ignoring international/regional competitors
- Missing stealth startups (pre-launch, private beta)
- Not checking recency (a 2-year-old review may describe a product that no longer exists)
