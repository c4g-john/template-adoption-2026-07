---
kind: charter
project: PRJ-001-DEMO
id: DEMO-charter
title: Demo — Replace Me With Your First Project
sponsor: your.name
budget:
  amount: 100000
  currency: USD
dates:
  created: 2026-07-01
  target: 2026-12-31
status: draft
---

## Objective

Show a working PMO-as-Code repository: a versioned charter that is validated on
every pull request, so the team replaces slide-hunting with a single source of
truth within the first week of adoption.

## Success Criteria

- The audit passes on 100% of merged pull requests.
- Median time to answer "what's the current status?" drops below 1 minute.
- At least 2 real projects are onboarded within 30 days.

## Scope

In scope: this repository, its checks, and the derived status page. Out of
scope: your organization's real projects — add them with `docassert new`.

## Milestones

- First real project onboarded — 2026-07-31
- Demo project deleted — 2026-08-15

## Risks

- The demo project lingers after real ones exist. Owner: your.name. Mitigation: delete PRJ-001-DEMO once your first real project passes the audit.

## Approval

Approved by the sponsor (your.name) on merge of this charter.
