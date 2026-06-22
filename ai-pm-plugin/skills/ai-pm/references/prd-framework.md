# PRD Framework — Detailed Section Guide

## When to Read This

Read this reference when:
- The user wants unusually deep detail in a specific PRD section
- The product type needs specialized treatment (B2B SaaS, Consumer, Internal Tool, Platform/API)
- The user asks "how should I think about [section X]?"
- You need to apply a specific framework (JTBD, Kano, RICE) in depth

## Section-by-Section Writing Guide

### Executive Summary

**Purpose:** Give a VP-level reader enough context in 30 seconds to decide whether to read further.

**Formula:** What + Why + Expected Impact + Ask

**Writing tips:**
- Start with the problem, not the solution
- Include the north star metric target
- Keep it to 4-6 sentences
- Write this section LAST (after everything else is drafted)

**Example:**
> "Users abandon our checkout flow 67% of the time, costing an estimated $2.3M in lost revenue annually. This PRD proposes a redesigned checkout experience with saved payment methods, address autocomplete, and a guest checkout option. We project a 40% reduction in abandonment, generating $920K incremental revenue in the first year. This requires one backend squad and one frontend squad for an estimated 8-week build."

### Problem Statement

**Framework:** Jobs-to-be-Done (JTBD)

Go beyond surface-level descriptions. Use this structure:

1. **Current state:** What happens today? Be specific with numbers and quotes.
2. **Pain points:** What sucks about the current state? Rank by severity.
3. **Evidence:** Survey data, support tickets, session recordings, revenue impact.
4. **Why existing solutions fall short:** What have users tried? Why didn't it work?
5. **JTBD statement:** "When [situation], I want to [motivation], so I can [expected outcome]."

**Writing tips:**
- Include direct user quotes when available
- Quantify pain whenever possible ("users spend 3 minutes on..." not "users spend a long time...")
- Describe the emotional state, not just the functional gap

### Goals & Success Metrics

**Framework:** OKRs + North Star + Counter Metrics

Structure goals in three tiers:

**Tier 1 — North Star Metric:** The one metric that best captures user value.
- Consumer: DAU/MAU, retention, time spent
- B2B SaaS: WAUs per account, feature adoption %, NPS
- Marketplace: GMV, transaction volume, liquidity

**Tier 2 — Primary Metrics (3-5):** Direct measures of success.
- Must be specific, measurable, time-bound
- Include baseline and target

**Tier 3 — Counter Metrics (2-3):** Things that should NOT worsen.
- E.g., "Checkout conversion improvement should not increase support tickets by >5%"
- E.g., "New onboarding flow should not drop activation rate for non-target personas"

**Metric quality checklist:**
- [ ] Each metric has a baseline value
- [ ] Each metric has a target value with timeline
- [ ] Each metric has a defined measurement method
- [ ] Counter metrics are included to catch unintended consequences

### User Personas

**Framework:** Persona Spectrum (not just happy-path users)

Include 3-5 personas covering the full spectrum:

1. **Primary persona:** The main target. Your design optimizes for this person.
2. **Secondary persona:** Also benefits, but with different needs.
3. **Edge-case persona:** Has accessibility needs, unusual workflow, or constrained environment.
4. **Anti-persona:** Someone who might use the product but you're explicitly NOT designing for (prevents scope creep).
5. **Internal persona:** Admin, support agent, or ops person who manages the feature.

**Each persona card:**
- Name/Role (make it memorable: "Manager Maria", "Freelancer Frank")
- Demographics and context
- Goals (functional, emotional, social)
- Current pain points and workarounds
- Tech comfort level
- Quote that captures their mindset

### User Stories

**Format:** Standard "As a [persona], I want to [action], so that [outcome]."

**Prioritization Framework:** RICE (Reach × Impact × Confidence / Effort) or MoSCoW (Must/Should/Could/Won't)

**Quality checklist for user stories:**
- [ ] Each story maps to a specific persona
- [ ] Each story has clear acceptance criteria (Given/When/Then)
- [ ] P0 stories cover the MVP — nothing more
- [ ] P1 stories cover the polished experience
- [ ] P2 stories are nice-to-haves explicitly deferred
- [ ] Edge cases are documented per story

**Story splitting:** If a story is estimated L (large), split it:
- By workflow step (Create → Edit → Delete)
- By platform (Web → Mobile → API)
- By data complexity (Simple fields → Rich media → Collaborative editing)

### Functional Requirements

**Structure by feature area, not by technical component.**

For each requirement:
- **Description:** What the system must do
- **Acceptance Criteria:** Given/When/Then format
- **Edge Cases:** What happens when things go wrong?
- **Priority:** P0 (MVP must-have) / P1 (should-have) / P2 (nice-to-have)

**Edge case checklist per requirement:**
- Empty state (no data)
- Error state (API fails, timeout)
- Loading state (slow connection)
- Extreme data (very long text, very large numbers, special characters)
- Permission state (user lacks access)
- Concurrency (two users acting simultaneously)

### Non-Functional Requirements

Cover these dimensions, marking N/A if truly not applicable:

| Dimension | Questions to Address |
|-----------|---------------------|
| Performance | Page load target, API response time, throughput |
| Security | Auth model, data encryption, PII handling, OWASP top 10 |
| Scalability | Expected user count, data volume growth, peak traffic |
| Reliability | Uptime SLA, error budget, disaster recovery |
| Accessibility | WCAG level, screen reader support, keyboard navigation |
| Internationalization | Languages, RTL support, date/number/currency formats |
| Compliance | GDPR, SOC2, HIPAA, PCI (be specific about what applies) |

### Technical Architecture

Include these elements at minimum:
- **System diagram** (described in text — components + arrows showing data flow)
- **API contracts** (endpoint, method, request/response shape for key endpoints)
- **Data model** (key entities, relationships, fields)
- **Third-party services** (what they do, why chosen, cost implications, fallback plan)
- **Migration plan** (if modifying existing systems)

### Dependencies & Risks

**Risk framework:** For each risk, assess:
- **Impact:** If this goes wrong, how bad is it? (High/Medium/Low)
- **Likelihood:** How likely is it to go wrong? (High/Medium/Low)
- **Detection:** How will we know early?
- **Mitigation:** What are we doing now to reduce likelihood or impact?
- **Contingency:** If it happens anyway, what's plan B?

**Common risk categories:**
- Technical risk (new technology, integration complexity)
- People risk (key person dependency, hiring timeline)
- Market risk (competitor launch, user adoption uncertainty)
- Regulatory risk (compliance changes)
- Dependency risk (blocked on another team/platform)

### Release Plan

Use a phased approach:

| Phase | Scope | Success Criteria | Go/No-Go Decision |
|-------|-------|-----------------|-------------------|
| Alpha | Internal dogfooding | Zero critical bugs, NPS > 20 from internal users | Move to Beta? |
| Beta | 10% of users | Metrics within 80% of target, < 2% error rate | Move to GA? |
| GA | Full rollout | All targets met, counter metrics stable | Iterate or move on? |

---

## Industry-Specific Templates

### B2B SaaS PRD Additions
- **Admin/Configuration section:** How do admins set up and manage this? Permission models, workspace settings.
- **Onboarding & Adoption:** How do new users discover and learn this feature?
- **Reporting & Analytics:** What dashboards/reports does this feed?
- **Sales & CS Enablement:** What do sales and CS need to sell/support this?
- **Enterprise Readiness:** SSO, audit logs, data export, SLA commitments.

### Consumer Mobile PRD Additions
- **Platform-specific considerations:** iOS vs Android differences, tablet support.
- **Offline behavior:** What works without connectivity?
- **Push notifications:** Triggers, content, frequency, opt-out.
- **App Store considerations:** Rating impact, review prompts, ASO keywords.
- **Battery/Data impact:** Any concerns with background processing or data usage?

### Internal Tools PRD Additions
- **Workflow integration:** How does this fit into existing internal processes?
- **Training & Documentation:** What do internal users need to learn?
- **Error forgiveness:** Internal tools need higher tolerance for mistakes (undo, confirmation dialogs).
- **Efficiency metrics:** Time saved per task, reduction in manual steps.

### Platform/API PRD Additions
- **API Design:** Endpoint specifications, authentication, rate limiting, versioning.
- **Developer Experience:** SDKs, documentation, sandbox environment, getting-started time.
- **Breaking Changes Policy:** How are developers protected?
- **Dogfooding:** Will an internal consumer use this API first?

---

## Common PRD Mistakes to Avoid

1. **Solution-first writing.** Describe the problem and goals before jumping to implementation. A PRD that starts with "Build a dashboard with 7 charts" skips the most important question: why?
2. **Vague success criteria.** "Improve user satisfaction" is not measurable. "Increase NPS from 32 to 40 within 3 months of GA" is.
3. **Missing edge cases.** Happy path only. Every PRD should have an explicit edge cases section.
4. **No counter metrics.** Optimizing for one metric without guarding others leads to local optimization at the expense of the whole system.
5. **Over-specification of UI.** Describe WHAT the user needs to accomplish and WHY. Leave HOW it looks to design unless there are specific constraints.
6. **Ignoring internal stakeholders.** Support, Sales, CS, Legal, and Security all have requirements. Ignoring them until the end causes last-minute redesigns.
7. **No go/no-go criteria.** Without explicit launch criteria, features ship when they "feel done" rather than when they're proven to work.
