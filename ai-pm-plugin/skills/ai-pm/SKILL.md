---
name: ai-pm
description: This skill should be used when the user asks to "write a PRD", "create a product requirements document", "do competitive analysis", "analyze competitors", "cluster user feedback", "categorize feedback", "summarize user research", "generate a PRD for", "compare competitors", "SWOT analysis for", "feature comparison", "user feedback analysis", or mentions being a PM / product manager working on product requirements, competitor research, or user feedback. Also use when the user says they need to "organize feedback", "understand what users want", "benchmark competitors", "write product spec", or "do market analysis". This skill covers the core workflows of an AI-powered product manager.
version: 1.0.0
license: MIT
---

# AI PM — AI-Powered Product Manager Skill

Accelerate core product management workflows with structured frameworks for PRD generation, competitive analysis, and user feedback clustering. This skill provides battle-tested templates, guided workflows, and quality standards so every output is actionable and executive-ready.

## Overview

Three core workflows are supported. When invoked, first determine which workflow the user needs (ask clarifying questions if ambiguous), then follow the corresponding workflow section below. Each workflow references detailed frameworks in `references/` for deeper guidance.

**Workflow selection guide:**
- User mentions "PRD", "product requirements", "spec", "product doc", "feature brief" → PRD Generation
- User mentions "competitor", "competitive", "benchmark", "SWOT", "market analysis", "替代品" → Competitive Analysis
- User mentions "feedback", "user feedback", "reviews", "complaints", "feature requests", "用户反馈", "评价" → Feedback Clustering
- If ambiguous, ask: "Are you looking for PRD generation, competitive analysis, or user feedback clustering?"

## General Principles

Apply these principles across all workflows:

1. **Ask before generating.** Before producing a full output, ask 2-4 clarifying questions to scope the work. Context matters more than speed — a well-scoped analysis beats a generic one every time.
2. **Use web search when appropriate.** For competitive analysis and market context, use WebSearch to gather real data. For PRDs, search for industry benchmarks and existing solutions. Cite sources.
3. **Output in the user's language.** Match the language the user communicates in. If they write in Chinese, output in Chinese. If mixed, default to the dominant language.
4. **Structured markdown output.** Every deliverable uses consistent markdown formatting with a table of contents. The format makes outputs easy to read in terminal, paste into Notion/Confluence, or export to PDF.
5. **Cite frameworks, not just opinions.** Ground analysis in established PM frameworks (Jobs-to-be-Done, Kano Model, RICE prioritization, Porter's Five Forces, etc.). Reference which framework is being applied and why.

---

## Workflow 1: PRD Generation

### Process

Follow this sequence when generating a PRD. Do not skip steps.

#### Step 1: Gather Context

Ask these clarifying questions (pick the most relevant 3-4, not all):

- What is the product/feature? What problem does it solve?
- Who is the target user? (Persona, role, demographics)
- What are the business goals? (Revenue, engagement, retention, etc.)
- What is the timeline and resource constraint?
- Are there existing products/features this builds upon?
- What are the known technical constraints or dependencies?
- What does success look like? (Metrics, OKRs)
- Who are the key stakeholders?

#### Step 2: Research (Optional but Recommended)

When the product domain is public-facing, use WebSearch to gather:
- Industry benchmarks and market data
- Existing solutions or competitors in the space
- Relevant regulations or compliance requirements
- Technology best practices for the domain

Flag any data gathered from web search with `[source]` notations.

#### Step 3: Generate the PRD

Use the template structure below. Read `references/prd-framework.md` for detailed section-by-section guidance, including writing tips, common pitfalls, and framework applications (Jobs-to-be-Done, Kano Model, RICE).

**Required PRD Structure:**

```markdown
# PRD: [Product/Feature Name]

**Author:** AI-generated | **Date:** [date] | **Version:** 1.0 | **Status:** Draft

## Table of Contents
1. [Executive Summary](#executive-summary)
2. [Problem Statement](#problem-statement)
3. [Goals & Success Metrics](#goals--success-metrics)
4. [User Personas](#user-personas)
5. [User Stories](#user-stories)
6. [Functional Requirements](#functional-requirements)
7. [Non-Functional Requirements](#non-functional-requirements)
8. [UX/Design Considerations](#uxdesign-considerations)
9. [Technical Architecture](#technical-architecture)
10. [Dependencies & Risks](#dependencies--risks)
11. [Release Plan & Milestones](#release-plan--milestones)
12. [Appendix](#appendix)

## Executive Summary
[One paragraph: what this is, why it matters, expected impact. Write this so a VP can understand it in 30 seconds.]

## Problem Statement
[Clear articulation of the problem. Include: current state, pain points, evidence (data/quotes), why existing solutions fall short.]

## Goals & Success Metrics
| Goal | Metric | Target | Measurement Method |
|------|--------|--------|-------------------|
| ... | ... | ... | ... |

**North Star Metric:** [The one metric that best captures the value]

## User Personas
### Persona 1: [Name/Role]
- **Description:** ...
- **Goals:** ...
- **Pain Points:** ...
- **Current Workaround:** ...

## User Stories
| ID | As a... | I want to... | So that... | Priority | Effort |
|----|---------|-------------|------------|----------|--------|
| US-01 | ... | ... | ... | P0/P1/P2 | S/M/L |

## Functional Requirements
### FR-1: [Feature Area]
- **Description:** ...
- **Acceptance Criteria:** ...
- **Edge Cases:** ...

## Non-Functional Requirements
- **Performance:** ...
- **Security:** ...
- **Scalability:** ...
- **Accessibility:** ...
- **Internationalization:** ...

## UX/Design Considerations
[Key flows, wireframe descriptions, design principles. Link to Figma/mocks if available.]

## Technical Architecture
[High-level architecture description. Components, data flow, API contracts, third-party services.]

## Dependencies & Risks
| Dependency/Risk | Impact | Likelihood | Mitigation |
|----------------|--------|------------|------------|
| ... | High/Med/Low | High/Med/Low | ... |

## Release Plan & Milestones
| Milestone | Deliverables | Date | Owner |
|-----------|-------------|------|-------|
| MVP | ... | ... | ... |
| V1.0 | ... | ... | ... |

## Appendix
[Glossary, references, research notes, stakeholder feedback]
```

#### Step 4: Review & Iterate

After generating the PRD, offer to:
- Deep-dive into any section
- Add/remove personas or user stories
- Adjust priority based on stakeholder input
- Generate a one-page executive summary version
- Convert to a different format (e.g., Confluence markup, Google Docs import-ready)

---

## Workflow 2: Competitive Analysis

### Process

#### Step 1: Scoping

Ask these clarifying questions:

- What product/domain are we analyzing? (Be specific — e.g., "Notion for enterprise wiki" not just "productivity tools")
- Which competitors should be included? (Direct, indirect, aspirational)
- What dimensions matter most? (Features, pricing, UX, market share, target audience, tech stack)
- Any specific lens? (For a feature launch? For pricing strategy? For market entry?)

#### Step 2: Research

Use WebSearch aggressively here. For each competitor, search for:
- Product features and recent updates
- Pricing and business model
- Market positioning and messaging
- User reviews (G2, ProductHunt, App Store)
- Funding and company size (Crunchbase, LinkedIn)
- Technical architecture (engineering blogs, developer docs)

#### Step 3: Generate the Analysis

Use the structure below. Read `references/competitive-analysis-framework.md` for frameworks (Porter's Five Forces, Feature Matrix methodology, SWOT best practices, Blue Ocean Strategy).

**Required Competitive Analysis Structure:**

```markdown
# Competitive Analysis: [Product/Domain]

**Date:** [date] | **Scope:** [direct/indirect/aspirational] | **Analyst:** AI-generated

## Table of Contents
1. [Executive Summary](#executive-summary)
2. [Market Landscape](#market-landscape)
3. [Competitor Profiles](#competitor-profiles)
4. [Feature Comparison Matrix](#feature-comparison-matrix)
5. [SWOT Analysis](#swot-analysis)
6. [Positioning Map](#positioning-map)
7. [Pricing Comparison](#pricing-comparison)
8. [User Sentiment Summary](#user-sentiment-summary)
9. [Strategic Recommendations](#strategic-recommendations)

## Executive Summary
[Key findings in 3-5 bullet points. Who leads? Where are the gaps? What is the top recommendation?]

## Market Landscape
[Market size, growth rate, key trends, major players. Cite sources.]

## Competitor Profiles
### [Competitor Name]
- **Website:** [url]
- **Founded:** [year] | **HQ:** [location] | **Size:** [employees, funding]
- **Target Audience:** ...
- **Value Proposition:** ...
- **Key Differentiators:** ...
- **Recent Updates:** ...
- **Strengths:** ...
- **Weaknesses:** ...

*(Repeat for each competitor)*

## Feature Comparison Matrix
| Feature | Our Product | Competitor A | Competitor B | Competitor C |
|---------|------------|-------------|-------------|-------------|
| ... | ✓/✗/Partial | ✓/✗/Partial | ✓/✗/Partial | ✓/✗/Partial |

**Coverage Summary:**
- **Our Product:** X/Y features (Z%)
- **Competitor A:** X/Y features (Z%)
- *Gap analysis narrative...*

## SWOT Analysis
### Our Product
| Strengths | Weaknesses |
|-----------|------------|
| ... | ... |
| **Opportunities** | **Threats** |
| ... | ... |

*(Repeat SWOT for each major competitor)*

## Positioning Map
[Describe a 2x2 positioning matrix. Axes examples: Price vs Features, Ease-of-use vs Power, Consumer vs Enterprise. Explain where each competitor sits and where the whitespace is.]

## Pricing Comparison
| Competitor | Free Tier | Starting Price | Enterprise | Pricing Model |
|------------|----------|---------------|------------|---------------|
| ... | ... | ... | ... | Per-seat/Usage/Flat |

## User Sentiment Summary
| Competitor | Overall Rating | Top Praise | Top Complaint | Sample Size |
|------------|---------------|------------|---------------|-------------|
| ... | ⭐X.X/5 | ... | ... | N reviews |

## Strategic Recommendations
1. **[Recommendation Title]**
   - **Rationale:** ...
   - **Expected Impact:** ...
   - **Effort Required:** S/M/L
   - **Urgency:** High/Medium/Low

2. *(Repeat for 3-5 recommendations)*

### Sources
[List all URLs and references used]
```

#### Step 4: Review & Iterate

Offer to:
- Deep-dive into a specific competitor
- Add/remove competitors from the analysis
- Focus on a specific dimension (e.g., pricing only, UX only)
- Generate a battle card summary (1-page version)

---

## Workflow 3: User Feedback Clustering

### Process

#### Step 1: Collect Feedback Data

Accept feedback in these formats:
- **Pasted text:** User can paste reviews, survey responses, support tickets directly
- **CSV/Excel file:** Read the file and auto-detect columns containing feedback text
- **Described verbally:** User describes the feedback themes and asks for structuring help
- **URL:** Point to a review page (App Store, G2, ProductHunt) and use WebFetch to pull data

#### Step 2: Clarify Scope

Ask:
- What is the source/context of this feedback? (App reviews, NPS survey, support tickets, user interviews)
- Are there any specific questions you want answered? (e.g., "What do users hate about onboarding?")
- How should the output be used? (Roadmap prioritization, bug triage, stakeholder presentation)

#### Step 3: Cluster and Analyze

Read `references/feedback-clustering-framework.md` for methodology details (affinity mapping, sentiment grading, RICE adaptation for feedback, the Kano lens).

Process:
1. **Parse** all feedback items into individual units
2. **Theme extraction** — group into thematic clusters (aim for 5-12 clusters)
3. **Sentiment grading** — mark each cluster as Positive/Neutral/Negative/Mixed
4. **Frequency counting** — how many feedback items per cluster
5. **Impact estimation** — assess each cluster's potential impact on retention/conversion/satisfaction
6. **Representative quotes** — pick 1-3 verbatim quotes per cluster

#### Step 4: Generate the Report

**Required Feedback Clustering Structure:**

```markdown
# User Feedback Analysis: [Product/Source]

**Date:** [date] | **Total Items:** [N] | **Source:** [type] | **Analyst:** AI-generated

## Table of Contents
1. [Executive Summary](#executive-summary)
2. [Overview & Methodology](#overview--methodology)
3. [Theme Clusters](#theme-clusters)
4. [Sentiment Distribution](#sentiment-distribution)
5. [Priority Matrix](#priority-matrix)
6. [Detailed Cluster Analysis](#detailed-cluster-analysis)
7. [Actionable Recommendations](#actionable-recommendations)
8. [Raw Data Appendix](#raw-data-appendix)

## Executive Summary
- **Total feedback items analyzed:** [N]
- **Theme clusters identified:** [N]
- **Top positive theme:** [theme] ([N] mentions, [X]%)
- **Top pain point:** [theme] ([N] mentions, [X]%)
- **Key takeaway:** [One sentence on the most important insight]

## Overview & Methodology
[Source description, collection period, clustering approach, limitations.]

## Sentiment Distribution
| Sentiment | Count | Percentage |
|-----------|-------|------------|
| Positive | ... | ...% |
| Neutral | ... | ...% |
| Negative | ... | ...% |
| Mixed | ... | ...% |

## Theme Clusters

### Cluster 1: [Theme Name]
- **Frequency:** [N] mentions ([X]% of total)
- **Sentiment:** [Positive/Neutral/Negative/Mixed]
- **Impact:** [High/Medium/Low] — [rationale]
- **Representative Quotes:**
  > "[verbatim quote]" — User context
- **Sub-themes:** [breakdown of variants within this cluster]
- **Affected User Segments:** [which personas/user types]

*(Repeat for each cluster, sorted by frequency × impact)*

## Priority Matrix
| Priority | Cluster | Frequency | Impact | Sentiment | Recommended Action |
|----------|---------|-----------|--------|-----------|-------------------|
| 🔴 P0 | ... | ... | High | Negative | Fix immediately |
| 🟡 P1 | ... | ... | Medium | Mixed | Plan next sprint |
| 🟢 P2 | ... | ... | Low | Positive | Monitor |

## Actionable Recommendations
1. **[Action Item]** — targets [cluster], expected impact [description], effort [S/M/L]
2. *(3-7 actionable items, directly tied to clusters)*

## Raw Data Appendix
[Summary statistics, data cleaning notes, full feedback-to-cluster mapping if manageable]
```

#### Step 5: Review & Iterate

Offer to:
- Re-cluster with different granularity (broader or finer)
- Focus on a specific sentiment (negative only, positive only)
- Generate a stakeholder-ready slide deck outline
- Export cluster-to-feedback mapping as CSV

---

## Reference Files

For deeper guidance on each workflow, consult these references when the user needs more detail or when handling edge cases:

- `references/prd-framework.md` — Detailed PRD section writing guide, framework applications (JTBD, Kano, RICE), common mistakes, and industry-specific templates (B2B SaaS, Consumer Mobile, Internal Tools, Platform/API)
- `references/competitive-analysis-framework.md` — Porter's Five Forces methodology, feature matrix scoring systems, SWOT quality checklist, positioning map construction, Blue Ocean Strategy canvas, battle card format
- `references/feedback-clustering-framework.md` — Affinity mapping process, sentiment analysis methodology, impact scoring rubric, RICE-Kano hybrid prioritization, inter-rater reliability for multi-analyst teams

## Examples

For reference outputs demonstrating quality expectations:

- `examples/prd-example.md` — Example PRD for a hypothetical feature
- `examples/competitive-analysis-example.md` — Example competitive analysis output

---

## Quality Checklist

Before presenting any output to the user, verify:

- [ ] All sections of the template are filled (no placeholder text)
- [ ] Specific, concrete claims are made (not vague generalities)
- [ ] Numbers and data points are included where possible
- [ ] Language matches the user's language
- [ ] Sources are cited for any externally-sourced data
- [ ] The output is self-contained — someone outside this conversation can understand it
- [ ] Recommendations are actionable (have clear owners, timelines, and success criteria)
