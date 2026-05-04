# Member Tracker — Tier System and GitHub Assignments

## Purpose

This document explains how members are identified, tiered, tracked, and given responsibilities as the community grows.

---

## Phase 1: The Tagging Sheet (Google Sheets)

Before anyone is invited, every potential member from the IE cohort is tagged in a private Google Sheet.

### Column Structure

| Column | Values | Notes |
|--------|--------|-------|
| Name | Full name | |
| LinkedIn URL | URL | For background check |
| Pre-MBA Industry | FMCG / Pharma / Logistics / Consulting / Tech / Finance / Other | |
| Pre-MBA Function | SC / Ops / Procurement / Logistics / BD / Finance / Other | |
| Pre-MBA Years Exp | Number | |
| Target Post-MBA | SC / Ops Consulting / Strategy Consulting / Finance / Other | |
| Tier | A / B / C | See tier criteria below |
| Status | Not contacted / DM sent / Call done / Invited / Confirmed / Declined | |
| Notes | Free text | Anything useful from 1:1 conversation |

### Tier Criteria

**Tier A — Direct SC practitioners**
Criteria: Pre-MBA role directly in supply chain, operations, procurement, logistics, or manufacturing. Or targeting these roles post-MBA with strong conviction.
Action: Personal 1:1 invite from the founder. Priority for founding session.

**Tier B — Adjacent professionals**
Criteria: Consulting, tech, finance, or BD background with meaningful SC exposure. Would add a useful lens but are not SC-first.
Action: Group invite after founding session is confirmed. Valuable at scale.

**Tier C — No SC relevance**
Criteria: No current or future SC connection evident from background.
Action: Do not invite in Phase 1. Revisit at Phase 3 if community broadens.

---

## Phase 2: Active Member Tracking (GitHub Issues)

Once the community has 20+ active members, use GitHub Issues to track member contributions and assignments.

### How It Works

- Each open role (Case Archivist, Frameworks Curator, Newsletter Lead, etc.) becomes a GitHub Issue
- The assigned member is tagged as the assignee
- Progress is tracked via issue comments and checkboxes
- Completed outputs (write-ups, frameworks) are linked in the issue before it is closed

### Example Issue: Case Archivist
```
Title: [Role] Case Archivist — SC Deep Dive #3
Assignee: @member-github-handle
Description:
- [ ] Attend SC Deep Dive #3
- [ ] Draft write-up within 48 hours using /docs/case-writeup-template.md
- [ ] Push to /updates/2026-07-deep-dive-3.md
- [ ] Notify Telegram group (GitHub Update Bot will do this automatically)
- [ ] Send LinkedIn summary to founder for review
```

---

## Phase 3: Folder Ownership Model

As the community matures, active members are given ownership of specific folders in the repo. This is how GitHub becomes a contributor model, not just a document store.

| Folder | Owner Role | Responsibilities |
|--------|-----------|------------------|
| `/updates/` | Case Archivist | Publish write-up within 48h of every session |
| `/resources/frameworks.md` | Frameworks Curator | Add new frameworks after sessions where one is used |
| `/resources/reading-list.md` | Reading List Curator | Monthly additions, remove outdated items |
| `/chapters/INDIA-CHAPTER.md` | India Chapter Co-Lead (Satya) | Update status, events, member list |
| `/chapters/MADRID-CHAPTER.md` | Madrid Chapter Co-Lead | Update status, events, partner updates |
| `/operations/CONTENT-ENGINE.md` | Content Steward | Update LinkedIn post log, newsletter archive |
| `/newsletter/` (future) | Newsletter Lead | Monthly issue files |

---

## Membership Definition (First 3 Months)

Membership is not a form or a payment. It is earned through participation.

A person is a **member** if they:
- Are in the Telegram group, AND
- Have attended at least one session OR contributed to one GitHub output

A person is a **founding member** if they:
- Attended the first or second session
- Are explicitly named in `TEAM.md` or the founding session write-up

---

## Growth Gates

The community should not grow faster than its ability to maintain quality.

| Member Count | Gate |
|---|---|
| 0–20 | Invite-only. Every person personally known to founder or India co-lead. |
| 20–50 | Referral from existing member required. No cold applications. |
| 50–100 | Short application form. One question: "What SC problem would you bring to a session?" |
| 100+ | Review with advisory board. Consider chapter-based caps. |
