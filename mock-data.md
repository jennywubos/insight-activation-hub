# Insight Activation Hub — Mock Research Data (Zillow-style)

Purpose: seed data for the interview prototype. Paste this file into Claude Code as the
content source for the `insights`, `sources`, and `qa_scenarios` (simulated agent) sections.
All data is fictional but designed to feel like real UXR output.

---

## Schema reference

**insights**: id, title, insight_statement, evidence_summary, confidence (High / Medium / Emerging),
confidence_rationale, product_area, research_method, source_id, date, owner

**sources**: source_id, study_name, method, sample, fielded_date, team

**Confidence rubric** (display in UI tooltip — shows research rigor):
- High = triangulated across 2+ methods or n>500 quant
- Medium = single robust study, directional agreement
- Emerging = small-n qualitative or single signal, needs validation

---

## Sources (8 studies)

| source_id | study_name | method | sample | fielded_date | team |
|---|---|---|---|---|---|
| S-01 | First-Time Buyer Journey Diary Study | 4-week longitudinal diary + exit interviews | n=24 buyers, 6 metros | 2025-09 | Foundational Research |
| S-02 | Tour Experience Intercept Survey | In-product intercept survey | n=1,847 | 2025-11 | Activation Research |
| S-03 | Seller Pricing Mental Models Interviews | 60-min semi-structured interviews | n=18 sellers | 2025-08 | Foundational Research |
| S-04 | Search & Discovery Usability Benchmark | Moderated usability, task-based | n=16 | 2026-01 | Activation Research |
| S-05 | NPS Verbatim Analysis Q4 | LLM-assisted thematic coding of verbatims | n=12,400 comments | 2026-01 | Insights Ops |
| S-06 | Affordability Concept Test | Unmoderated concept test, 3 variants | n=312 | 2025-10 | Activation Research |
| S-07 | Rental Application Funnel Mixed-Methods | Funnel analysis + 12 follow-up interviews | n=12 qual / 40k sessions quant | 2025-12 | Activation Research |
| S-08 | Natural Language Search Beta Feedback | Beta user survey + session replays | n=486 survey / 200 replays | 2026-02 | AI Product Research |

---

## Insights (18)

### INS-001 · Tour response-time uncertainty drives abandonment
- **Insight**: First-time buyers abandon tour requests when they cannot see an expected response time; uncertainty, not delay itself, is the primary driver.
- **Evidence**: 14 of 24 diary participants described "not knowing if anyone got my request" as the moment they switched to a competitor or called an agent directly. Intercept survey: 38% of abandoners cited "no confirmation of when I'd hear back."
- **Confidence**: High — triangulated (S-01 + S-02)
- **Product area**: Touring | **Method**: Diary study + intercept survey | **Date**: 2025-11 | **Owner**: M. Chen

### INS-002 · Buyers conflate pre-qualification with pre-approval
- **Insight**: 60%+ of first-time buyers believe pre-qualification carries the same weight as pre-approval, leading to failed offers and trust erosion attributed to the platform.
- **Evidence**: Diary study: 15 of 24 participants used the terms interchangeably; 6 lost an offer after discovering the difference late. NPS verbatims show 214 comments tagged "financing confusion."
- **Confidence**: High — triangulated (S-01 + S-05)
- **Product area**: Financing | **Method**: Diary study + verbatim analysis | **Date**: 2026-01 | **Owner**: M. Chen

### INS-003 · Saved-search notification fatigue causes silent churn
- **Insight**: Users receiving >2 saved-search alerts/day mute notifications within 3 weeks, then disengage entirely; they prefer a daily digest with "only meaningful changes."
- **Evidence**: Verbatim analysis: "too many emails" is the #3 detractor theme (n=387 comments). Usability sessions: 11 of 16 participants had notifications muted and didn't realize new matches existed.
- **Confidence**: Medium — consistent but needs behavioral validation
- **Product area**: Search & Discovery | **Method**: Verbatim analysis + usability | **Date**: 2026-01 | **Owner**: R. Okafor

### INS-004 · Sellers anchor on automated estimates before agent input
- **Insight**: Sellers form a list-price expectation from the automated home value estimate before ever speaking to an agent; a lower agent recommendation is experienced as "the agent lowballing me," not the estimate being high.
- **Evidence**: 13 of 18 seller interviews showed estimate-first anchoring; 9 described agent conflict over price. Sellers asked for "what drives this number" transparency.
- **Confidence**: Medium — single robust qualitative study (S-03)
- **Product area**: Seller Experience | **Method**: Interviews | **Date**: 2025-08 | **Owner**: L. Park

### INS-005 · Monthly-payment framing outperforms list-price framing
- **Insight**: Displaying affordability as estimated monthly payment (incl. taxes/insurance) increases buyer confidence and filter usage vs. list-price-only framing.
- **Evidence**: Concept test: monthly-payment variant scored +18 pts on "I understand what I can afford" and drove 2.1x more interactions with the affordability filter (S-06).
- **Confidence**: Medium — concept test, pre-launch
- **Product area**: Financing | **Method**: Concept test | **Date**: 2025-10 | **Owner**: D. Alvarez

### INS-006 · Repeated rental application fees are the top rental detractor
- **Insight**: Renters applying to multiple units perceive per-application fees as exploitative; "apply once, reuse everywhere" is the single most requested rental improvement.
- **Evidence**: Funnel analysis: 41% drop-off at the second application's payment step. All 12 interviewees independently raised fee fatigue (S-07). #1 rental detractor theme in NPS verbatims.
- **Confidence**: High — triangulated (S-07 + S-05)
- **Product area**: Rentals | **Method**: Funnel + interviews + verbatims | **Date**: 2025-12 | **Owner**: R. Okafor

### INS-007 · Natural-language search loses trust when results feel opaque
- **Insight**: Beta users revert to traditional filters when NL search returns results they can't explain ("why am I seeing this house?"). Showing interpreted criteria ("we searched: 3bd, under $650k, near parks") restores trust.
- **Evidence**: Session replays: 62% of reverters did so after an unexplained result set. Survey: "show me how you understood my search" was the top requested fix (S-08).
- **Confidence**: Medium — beta population may skew tech-savvy
- **Product area**: AI Search | **Method**: Beta survey + session replays | **Date**: 2026-02 | **Owner**: T. Nguyen

### INS-008 · Buyers evaluate agents by neighborhood-level track record
- **Insight**: When choosing an agent, buyers want transaction history in the specific neighborhood — not star ratings. "5 stars means nothing; 12 closings on this side of town means everything."
- **Evidence**: 17 of 24 diary participants researched agents off-platform to find local track records (S-01).
- **Confidence**: Medium — strong qual signal, no quant validation yet
- **Product area**: Agent Connection | **Method**: Diary study | **Date**: 2025-09 | **Owner**: M. Chen

### INS-009 · Post-tour recall decays within 48 hours
- **Insight**: Buyers touring 3+ homes in a weekend cannot reliably recall differentiating details by Monday; structured post-tour notes (photos + prompts) are wanted at the moment of leaving the home.
- **Evidence**: Intercept survey: 54% agreed "homes blur together"; diary participants improvised spreadsheets and photo albums as workarounds (S-01 + S-02).
- **Confidence**: High — triangulated
- **Product area**: Touring | **Method**: Survey + diary study | **Date**: 2025-11 | **Owner**: L. Park

### INS-010 · Climate-risk data changes shortlists in exposed markets
- **Insight**: In flood/fire-exposed metros, buyers who notice climate-risk scores remove homes from their shortlist — but most don't notice the scores exist.
- **Evidence**: Usability benchmark: only 4 of 16 participants found climate data unprompted; 3 of those 4 changed a decision after seeing it (S-04).
- **Confidence**: Emerging — small n, big behavioral effect when seen
- **Product area**: Search & Discovery | **Method**: Usability benchmark | **Date**: 2026-01 | **Owner**: D. Alvarez

### INS-011 · Co-decision households need shareable, commentable shortlists
- **Insight**: First-gen and multigenerational buyers make decisions with family members who aren't on the account; they want shareable shortlists with comments, not screenshots over text.
- **Evidence**: 9 of 24 diary participants shared listings via screenshot to family group chats daily; 5 described decision delays from fragmented feedback (S-01).
- **Confidence**: Medium — clear qual pattern in key segment
- **Product area**: Search & Discovery | **Method**: Diary study | **Date**: 2025-09 | **Owner**: M. Chen

### INS-012 · Map gestures conflict with scroll on mobile
- **Insight**: On mobile, one-finger map panning hijacks page scroll, causing rage-taps and accidental searches; two-finger pan with a visual hint resolves it.
- **Evidence**: Usability benchmark: 13 of 16 participants triggered accidental map moves within 2 minutes; 6 verbalized frustration (S-04).
- **Confidence**: High — near-universal in test, matches support tickets
- **Product area**: Mobile UX | **Method**: Usability benchmark | **Date**: 2026-01 | **Owner**: R. Okafor

### INS-013 · Sellers want one timeline, not five tools
- **Insight**: Sellers juggling estimate, agent comms, showings, offers, and closing want a single chronological "what happens next" view; fragmentation drives anxiety calls to agents.
- **Evidence**: 14 of 18 seller interviews sketched some version of a timeline unprompted when asked to describe their ideal experience (S-03).
- **Confidence**: Medium — single study, strong convergence
- **Product area**: Seller Experience | **Method**: Interviews | **Date**: 2025-08 | **Owner**: L. Park

### INS-014 · Rate volatility creates "rate watch" behavior
- **Insight**: In volatile rate environments, serious buyers check rates near-daily and delay offers on rate spikes; they want rate-drop alerts tied to specific saved homes ("tell me when this home's payment drops below $3,200/mo").
- **Evidence**: Verbatim analysis: rate-related comments up 3.4x YoY (n=1,120); concept test variant with payment-threshold alerts scored highest purchase-intent (S-05 + S-06).
- **Confidence**: High — triangulated
- **Product area**: Financing | **Method**: Verbatims + concept test | **Date**: 2026-01 | **Owner**: D. Alvarez

### INS-015 · New-construction discovery is an afterthought
- **Insight**: Buyers open to new construction don't think to filter for it; they discover new builds via off-platform ads and assume the platform "doesn't really do new homes."
- **Evidence**: 8 of 24 diary participants toured a new build found via social ads; only 2 had used the new-construction filter (S-01).
- **Confidence**: Emerging — needs quant sizing
- **Product area**: Search & Discovery | **Method**: Diary study | **Date**: 2025-09 | **Owner**: T. Nguyen

### INS-016 · Accessibility filters miss aging-in-place needs
- **Insight**: Buyers shopping for aging parents need "no-step entry, main-floor bedroom + full bath" as a combined concept; current single-feature filters force manual photo-inspection of every listing.
- **Evidence**: Usability benchmark: all 5 participants with this scenario failed the task within time; verbatims include 96 comments on accessibility filtering gaps (S-04 + S-05).
- **Confidence**: Medium — small but consistent across methods
- **Product area**: Search & Discovery | **Method**: Usability + verbatims | **Date**: 2026-01 | **Owner**: R. Okafor

### INS-017 · Trust transfers from estimate accuracy to whole platform
- **Insight**: When buyers see an estimate that contradicts a recent nearby sale they know about, trust in *all* platform data drops — search results, agent recommendations, everything. Estimate accuracy is a platform-trust issue, not a feature issue.
- **Evidence**: 11 of 18 seller interviews + 7 diary buyers described generalizing one "wrong number" to overall skepticism (S-01 + S-03).
- **Confidence**: Medium — consistent cross-audience qual
- **Product area**: Trust & Data | **Method**: Interviews + diary study | **Date**: 2025-09 | **Owner**: L. Park

### INS-018 · NL search shines for lifestyle queries, fails for hard constraints
- **Insight**: Natural-language search delights on fuzzy lifestyle intent ("quiet street, good light, walkable coffee") but frustrates on hard constraints (school district boundaries, exact HOA limits) — users want NL for vibe, filters for facts, working together.
- **Evidence**: Beta survey: lifestyle queries rated 4.4/5 vs constraint queries 2.6/5; replays show users repeating constraint queries with increasing specificity before giving up (S-08).
- **Confidence**: Medium — beta cohort only
- **Product area**: AI Search | **Method**: Beta survey + replays | **Date**: 2026-02 | **Owner**: T. Nguyen

---

## Simulated agent Q&A scenarios (4)

These power the "AI 问答" section. Each answer cites insight IDs — render citations as
clickable chips that scroll to the insight card.

### Q1 — "What do we know about why buyers drop off during tour scheduling?"
**Answer**: Research points to uncertainty, not speed, as the core driver. Buyers abandon when there's no visible expected response time [INS-001, High confidence]. The pain compounds downstream: buyers who do tour multiple homes lose recall within 48 hours and lack structured note-taking [INS-009, High]. Recommended activation: response-time SLA display + post-tour capture flow. Two triangulated studies support this (S-01, S-02).

### Q2 — "Is there evidence for investing in affordability features this half?"
**Answer**: Yes — three converging signals. Monthly-payment framing outperformed list-price framing by 18 pts on comprehension [INS-005, Medium]. Rate volatility has created daily "rate watch" behavior, with payment-threshold alerts scoring highest purchase intent [INS-014, High]. And pre-qualification confusion is causing failed offers attributed to the platform [INS-002, High]. Caveat: INS-005 is pre-launch concept data — recommend an A/B before full rollout.

### Q3 — "What are the biggest trust risks in our AI search experience?"
**Answer**: Opacity. Beta users revert to filters when they can't explain a result set; showing interpreted criteria restores trust [INS-007, Medium]. NL search performs well on lifestyle intent but fails on hard constraints — forcing one mode for both erodes confidence [INS-018, Medium]. Note the broader pattern: trust failures generalize across the platform [INS-017, Medium]. Both AI-search insights come from the beta cohort (S-08) — validate with mainstream users before GA decisions.

### Q4 — "We have one engineering sprint for rentals. What should it target?"
**Answer**: Application-fee fatigue is the highest-confidence, highest-severity rentals insight: 41% funnel drop-off at the second application's payment step, unanimous in follow-up interviews, and the #1 rental detractor theme [INS-006, High, triangulated across S-07 + S-05]. An "apply once, reuse everywhere" flow directly addresses it. This is the rare insight where quant severity, qual causality, and verbatim volume all align.

---

## usage_metrics seed (for the Adoption Dashboard)

Generate 10 weeks of data with an adoption-curve shape (slow start, inflection at week 4 after
"PM onboarding session", steady growth):

- weekly_queries: 12, 18, 25, 61, 84, 97, 110, 128, 135, 152
- insights_activated (inserted into PRDs/docs): 1, 2, 2, 7, 9, 11, 12, 15, 14, 18
- active_users: 4, 6, 7, 15, 19, 22, 24, 27, 29, 33
- avg_time_to_insight_minutes (down is good): 38, 35, 33, 22, 19, 17, 16, 14, 14, 12
- Annotate week 4 on the chart: "Embedded into sprint planning ritual" — this visually
  tells the JD's change-management story.
