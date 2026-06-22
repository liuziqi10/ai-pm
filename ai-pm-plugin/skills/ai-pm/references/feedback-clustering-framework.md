# User Feedback Clustering Framework — Detailed Methodology

## When to Read This

Read this reference when:
- The feedback dataset is large or messy and needs structured processing
- The user needs specific prioritization methodology (RICE-Kano hybrid)
- The user asks about methodology rigor or inter-rater reliability
- You need to process Chinese-language feedback (special considerations below)

---

## Phase 1: Data Preparation

### Parsing & Normalization

Before clustering, normalize the raw data:

1. **Deduplication:** Remove exact or near-duplicate entries. Flag near-duplicates for review.
2. **Language detection:** Identify primary language per item. Group by language for separate analysis if mixed.
3. **Length filtering:** Flag ultra-short items (< 5 words) as "low signal" — keep them but weigh lightly. Flag ultra-long items (> 500 words) as "narrative" — may contain multiple themes.
4. **Noise removal:** Strip signatures, timestamps, auto-generated footers, email headers.
5. **De-identification:** Note if feedback contains PII (names, emails, phone numbers) and handle per privacy requirements.

### Unitization

Split long feedback into atomic units — each unit expresses exactly ONE idea.

**Example:**
> Input: "The onboarding was confusing and took too long, but once I got through it the dashboard is great."
>
> Unit 1: "The onboarding was confusing and took too long" → Theme: Onboarding UX, Sentiment: Negative
> Unit 2: "The dashboard is great" → Theme: Dashboard, Sentiment: Positive

**Unitization rules:**
- Split on: but, however, on the other hand, also, another thing, 但是, 不过, 另外
- Each unit must be independently understandable (if a pronoun refers to a previous unit, keep them together)
- Mark units that came from the same original item with a parent ID for traceability

---

## Phase 2: Theme Extraction (Affinity Mapping)

### Bottom-Up Clustering Process

1. **First pass — Surface reading:** Read through all units to build intuition about the thematic landscape.
2. **Second pass — Open coding:** Assign an initial descriptive tag to each unit. Use the user's own language where possible (in-vivo coding).
3. **Third pass — Axial clustering:** Group tags into 5-12 theme clusters. Merge clusters that overlap > 50%. Split clusters that are too broad (> 25% of all units in one cluster).
4. **Fourth pass — Theme naming:** Give each cluster a concise, descriptive name. Good names are specific enough to be actionable ("Onboarding Step 3 Confusion" not "UX Issues").

### Theme Quality Checklist

| Criterion | Good | Bad |
|-----------|------|-----|
| Specificity | "Checkout payment method errors" | "Payment issues" |
| Actionability | "Missing dark mode causes eye strain" | "UI could be better" |
| Mutual exclusivity | Each unit clearly belongs to ONE cluster | Units could fit in 2+ clusters equally |
| Coverage | 90%+ of units fit into a named cluster | Large "Other" bucket (>15%) |
| Groundedness | Cluster name uses user language | Academic/abstract names |

### Cluster Granularity Guide

| Dataset Size | Recommended Clusters |
|-------------|---------------------|
| < 50 items | 3-6 clusters |
| 50-200 items | 5-10 clusters |
| 200-1000 items | 8-15 clusters |
| 1000+ items | 10-20 clusters with sub-themes |

---

## Phase 3: Sentiment Analysis

### Grading Rubric

| Sentiment | Definition | Example Signals |
|-----------|-----------|-----------------|
| **Very Positive** | Enthusiastic praise, recommends to others, emotional language | "Love", "best ever", "life-changing", "recommend to everyone" |
| **Positive** | Satisfied, meets expectations, would continue using | "Works well", "good", "useful", "like it" |
| **Neutral** | Factual, no emotional valence, or mixed equal parts | "It does X", feature requests without praise/complaint |
| **Negative** | Dissatisfied, frustrated, considering alternatives | "Frustrating", "doesn't work", "waste of time", " annoying" |
| **Very Negative** | Angry, churning, warning others, emotional language | "Terrible", "worst", "deleting my account", "do not use" |
| **Mixed** | Contains both significant positive and negative sentiment in one unit | "Great feature but the pricing is ridiculous" |

### Sentiment by Cluster

For each cluster, calculate:
- **Sentiment distribution:** % Positive, % Neutral, % Negative, % Mixed
- **Sentiment intensity:** Average sentiment score on a -2 to +2 scale
- **Sentiment trend:** Is this cluster getting more positive or more negative over time? (if timestamps available)

**Interpretation guide:**
- High Negative % + High Frequency → 🔴 Critical pain point — fix ASAP
- High Positive % + High Frequency → 🟢 Key strength — protect and amplify
- Low Frequency + Very Negative → 🟡 Investigate — could be early warning signal
- High Frequency + Neutral → 🟡 Opportunity — users care but aren't delighted

---

## Phase 4: Impact Estimation

### Impact Scoring Rubric

For each cluster, estimate impact on a 1-5 scale:

| Score | Label | Criteria |
|-------|-------|----------|
| 5 | Critical | Directly causes churn, blocks core workflow, security/privacy issue |
| 4 | High | Significantly degrades experience, mentioned by power users, affects conversion |
| 3 | Medium | Noticeable friction, users find workarounds, affects satisfaction |
| 2 | Low | Minor annoyance, cosmetic issue, mentioned in passing |
| 1 | Negligible | Edge case, single mention, no measurable impact |

**Impact dimensions to consider:**
- **Retention impact:** Does this affect whether users stay or leave?
- **Conversion impact:** Does this affect trial-to-paid or upgrade decisions?
- **Satisfaction impact:** Does this affect NPS or review scores?
- **Support impact:** Does this drive support ticket volume?
- **Acquisition impact:** Does this affect word-of-mouth or review-based discovery?

### The RICE-Kano Hybrid

Combine RICE scoring with Kano model classification for richer prioritization:

**Step 1 — Kano Classification:**
Classify each theme cluster into a Kano category:
- **Must-Be (Basic Expectations):** Users expect this. Absence = extreme dissatisfaction. Presence = neutral (table stakes).
- **Performance (One-Dimensional):** The better you do this, the more satisfied users are. Linear relationship.
- **Attracter (Delighter):** Absence = neutral. Presence = high satisfaction. Unexpected value.
- **Indifferent:** Users don't care either way. Low ROI.

**Step 2 — RICE Scoring:**
| Cluster | Reach | Impact | Confidence | Effort | RICE Score | Kano Type |
|---------|-------|--------|------------|--------|------------|-----------|
| ... | [% of users affected] | [1-5] | [% certainty] | [Person-weeks] | [R×I×C/E] | [Type] |

**Step 3 — Priority Matrix:**
- **Quadrant 1 (Top Priority):** High RICE + Must-Be or Performance → Fix now
- **Quadrant 2 (Invest):** High RICE + Attracter → Competitive differentiator
- **Quadrant 3 (Maintain):** Low RICE + Must-Be → Keep meeting baseline expectations
- **Quadrant 4 (Deprioritize):** Low RICE + Indifferent → Don't waste resources

---

## Phase 5: Insights & Recommendations

### From Clusters to Action

For each cluster, generate:

1. **Root cause hypothesis:** Why might this pattern exist? (Not just "users want X" but "users want X because the current workflow forces them to...")
2. **Recommended action:** What should the team DO?
3. **Expected impact of action:** What changes if we do this?
4. **Validation method:** How do we confirm the action worked? (Specific metric + target + timeline)

### Recommendation Quality Checklist

Good recommendations are:
- **Specific:** "Add address autocomplete to checkout field #3 using Google Places API" not "Improve checkout"
- **Owned:** Clear which team/role would execute
- **Scoped:** Rough effort estimate (days/weeks/months)
- **Testable:** Success criteria defined
- **Sequenced:** What should be done first, second, third?

### The "Three Horizons" Framework for Recommendation Sequencing

- **Horizon 1 (Now — Next Sprint):** Quick wins — high impact, low effort. Build momentum.
- **Horizon 2 (Next Quarter):** Strategic investments — high impact, high effort. Core roadmap.
- **Horizon 3 (Future):** Transformational — speculative, long-term. Plant seeds.

---

## Chinese-Language Feedback Considerations

When processing Chinese user feedback (用户反馈), account for:

### Language-Specific Patterns
- **Implicit sentiment:** Chinese feedback often expresses dissatisfaction indirectly. "还行" (it's okay) often masks dissatisfaction. Look for hedging language: 有点 (a bit), 稍微 (slightly), 可能 (maybe).
- **Context-heavy:** Chinese feedback may reference shared cultural context without stating it explicitly. A complaint about "客服" (customer service) may reference standards set by platforms like Taobao or WeChat.
- **Platform-specific norms:** App reviews on Chinese app stores (Huawei, Xiaomi, OPPO) differ in tone and expectation from Apple App Store reviews. Xiaomi reviews tend to be more technical and feature-focused.
- **Emoji and stickers:** Chinese feedback may use platform-specific emoji. Note common complaint markers: 😡, 💔, 👎.
- **Score inflation:** On some Chinese platforms, anything below 4.5/5 is considered poor. Account for platform-specific rating distributions.

### Chinese-Specific Clusters to Watch For
- **Privacy/Data concerns (隐私/数据):** Heightened sensitivity in Chinese market
- **Localization quality (本地化):** UI translations, date formats, payment methods (WeChat Pay, Alipay)
- **Performance on domestic devices:** Huawei HarmonyOS, Xiaomi MIUI, OPPO ColorOS compatibility
- **Compliance/Regulatory:** ICP备案, real-name verification, content moderation expectations
