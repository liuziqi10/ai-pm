# Example PRD: AI-Powered Search for a Knowledge Base

> **Note:** This is a condensed example demonstrating the expected quality level and format. Real PRDs would be longer and more detailed.

---

**Author:** AI-generated | **Date:** 2026-06-22 | **Version:** 1.0 | **Status:** Draft

## Executive Summary

Internal knowledge base search at Acme Corp returns relevant results only 34% of the time, causing employees to waste an estimated 4.2 hours/week each recreating information that already exists. This PRD proposes an AI-powered semantic search system using embeddings-based retrieval with a hybrid BM25+vector approach. We project 85%+ search relevance within 3 months, saving ~2,200 person-hours/month across the organization. Requires one ML Engineer, one Backend Engineer, and 12 weeks for MVP.

## Problem Statement

**Current State:** Employees search the internal wiki (Confluence) using keyword search. The search treats queries as literal string matches against document titles and body text.

**Evidence:**
- Internal survey (N=247): 72% of employees say "finding existing information" is their top workflow frustration
- Search analytics: 34% of searches result in a click on a top-3 result; 41% of searches are abandoned with no click
- IT support tickets: 18 tickets/week requesting "where is the X document?"
- Time audit: Average employee spends 4.2 hrs/week searching for or recreating internal information

**JTBD Statement:** "When I need to find internal documentation to do my job, I want to describe what I'm looking for in natural language, so I can find the right information in under 30 seconds without knowing the exact title or author."

## Goals & Success Metrics

| Goal | Metric | Baseline | Target | Timeline |
|------|--------|----------|--------|----------|
| Search relevance | % of searches with relevant top-3 result | 34% | 85% | 3 months post-MVP |
| Search efficiency | Median time-to-find | 4.2 min | <30 sec | 3 months post-MVP |
| User satisfaction | Search NPS | 12 | 50+ | 6 months |
| Content reuse | % of docs accessed via search | 18% | 60% | 6 months |

**Counter Metrics:**
- Search latency must stay under 500ms p95 (vs. current 200ms — acceptable tradeoff for relevance)
- Search abandonment rate must not increase (currently 41%)
- Support tickets about "can't find X" must decrease

## User Personas

### Persona 1: "New-Hire Noah"
- Joined < 3 months ago, doesn't know document naming conventions
- Searches with natural language questions: "how do I set up my dev environment"
- Currently asks colleagues in Slack, feeling like a burden
- Tech comfort: High (engineer), but unfamiliar with internal tooling

### Persona 2: "Veteran Vera"
- 5+ years tenure, knows the wiki structure but can't keep up with growth
- Searches with acronyms and project codenames
- Frustrated that search doesn't understand internal jargon
- Tech comfort: Medium (PM)

### Persona 3: "External Erin"
- Contractor/partner with limited wiki access
- Doesn't know internal terminology at all
- Currently emails their Acme contact for every document need
- Tech comfort: Varied

## User Stories

| ID | As a... | I want to... | So that... | Priority | Effort |
|----|---------|-------------|------------|----------|--------|
| US-01 | All users | Type a natural language question and get relevant results | I don't need to know exact keywords | P0 | L |
| US-02 | New-Hire Noah | See search results ranked by relevance, not by recency | I find what I need without scrolling through outdated docs | P0 | M |
| US-03 | Veteran Vera | Search using internal acronyms and have them expanded | The search understands our internal language | P0 | M |
| US-04 | All users | See a snippet preview of the relevant paragraph in search results | I can judge relevance without opening every document | P1 | S |
| US-05 | External Erin | Search across only the documents I have permission to see | I don't see results I can't access (and get frustrated) | P1 | M |
| US-06 | All users | Filter results by document type, author, date range | I can narrow down when I know partial context | P2 | M |

## Functional Requirements

### FR-1: Semantic Search
- **Description:** Users submit a natural language query and receive relevance-ranked results
- **Acceptance Criteria:**
  - Given a user enters "how to deploy to staging", when they submit the search, then the top result should be the staging deployment runbook
  - Given a user enters "PTO policy", when they submit, then results containing "vacation policy" and "time off request" should appear (semantic matching, not just keyword)
- **Edge Cases:** Empty query → show search tips. Query in non-English language → detect and translate before embedding. Very long query (> 500 chars) → truncate and warn.

### FR-2: Hybrid Retrieval
- **Description:** Combine BM25 (keyword) and vector (semantic) retrieval with weighted ranking
- **Acceptance Criteria:**
  - Exact title matches ("Deployment Runbook") always rank above purely semantic matches
  - Semantic matches surface relevant documents even when keywords don't overlap ("time off" matches "vacation policy")
- **Edge Cases:** Very rare terms with no semantic neighbors → fall back to BM25 only. All-emoji query → treat as empty.

## Non-Functional Requirements

- **Performance:** p95 latency < 500ms end-to-end (query → results displayed)
- **Security:** Search respects existing Confluence page-level permissions. No privilege escalation via search.
- **Scalability:** Support 100K documents at launch, 1M within 12 months. 500 concurrent searches at peak.
- **Accessibility:** WCAG 2.1 AA. Full keyboard navigation for search results. Screen reader announces result count and relevance.
- **Internationalization:** Support queries in English, Spanish, and Mandarin (our three office languages). Cross-lingual search: Spanish query should match English documents.

## Dependencies & Risks

| Dependency/Risk | Impact | Likelihood | Mitigation |
|----------------|--------|------------|------------|
| Confluence API rate limits | High | Medium | Implement caching layer; pre-build embedding index nightly |
| Embedding model quality for internal jargon | Medium | Medium | Fine-tune on internal corpus of 10K documents; human eval of top-100 queries |
| User adoption (habit change) | Medium | High | Keep existing search as fallback tab; measure and communicate improvements |
| Permission model complexity | High | Low | Audit existing permissions before launch; integration tests per permission level |

## Release Plan

| Milestone | Deliverables | Success Criteria | Timeline |
|-----------|-------------|-----------------|----------|
| Alpha | Internal dogfooding with IT team (50 users) | Search relevance > 60%, latency < 1s | Week 8 |
| Beta | Rollout to Engineering org (500 users) | Search relevance > 75%, NPS > 20 | Week 10 |
| GA | Full company rollout | All metrics at target | Week 14 |
