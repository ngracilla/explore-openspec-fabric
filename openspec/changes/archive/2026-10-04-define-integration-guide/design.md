## Context

This repo (full OpenSpec) produces an integration guide for readers who own a separate Fabric repo (gradual OpenSpec, high human involvement). See proposal.md - Why for motivation. Decisions below are labeled by the repo they concern: **guide repo** decisions govern how this repo is built; **Fabric repo** decisions are what the guide recommends to readers and do not constrain work here.

## Goals / Non-Goals

**Goals:**
- Give the client a standalone overview and the team a standalone procedure, without duplicated or conflicting content.
- Make every Fabric claim traceable to current Microsoft documentation and visibly dated.

**Non-Goals:**
- Phases beyond testing (branch flow, CI and promotion, feature development).
- Any sample Fabric project; examples live inline in the guide text.

## Decisions

### 1. Two documents plus a shared scope page (guide repo)
The client overview and team guide are separate documents, with a short shared scope page. Shared content (involvement levels, risk and control pairs) has one source, and the other document links to it.
*Alternative: one document with two parts.* Rejected: the client would receive procedural detail, and each audience's read would not stand alone. Cost accepted: drift risk between documents, mitigated by single-sourcing shared content.

### 2. Team guide chapters (guide repo)
Five chapters: Prepare, Connect, Baseline, Init OpenSpec, Testing. Testing ends at characterizing one existing slice. Branch flow, CI and promotion, and feature development are excluded.
*Alternative: eight phases including branch flow, automation, and features.* Rejected: those phases lead into OpenSpec-driven code development, which is not the guide's purpose.

### 3. Recommended default for agents and tests (Fabric repo)
The guide presents three levels - suggest only; agents write all tests and run local ones; agents also run in-Fabric tests against a dev workspace via a read-only identity - and recommends the second as the starting point. Humans place all production code and run in-Fabric tests.
*Why:* real agent help where the guide's value claim (testing) is delivered, human-placed production code, and no credentials, which keeps the client risk story simple. The third level is offered as a later step.

### 4. Scenario-to-test link (Fabric repo)
Tests are named by the scenario they cover (name or docstring repeats the scenario name). Stable scenario IDs are described as the upgrade for teams where renames break the link.
*Alternative: stable IDs from the start, or a manual traceability table.* Rejected for a gradual adoption: IDs add a convention to maintain, and a table goes stale.

### 5. Hybrid sourcing of Fabric claims (guide repo)
The team guide cites Microsoft documentation inline per step; the client overview uses a sources appendix. Every verified claim carries a "verified on" date in either style. Verification is done during apply using web search and fetch, and a person reviews sources in the PR.
*Alternative: inline everywhere, or appendix everywhere.* Rejected: inline clutters the client overview, and an appendix is weak for step-by-step procedure.

## Risks / Trade-offs

- [Documents drift apart] → Single source for involvement levels and risk and control pairs, linked from the other document.
- [Fabric behavior changes after verification] → Dated claims make staleness visible; re-verify when a date is old.
- [Claims written from memory enter the guide] → The verification requirement in guide-scope blocks claims without a source.
- [Convention A breaks silently when a scenario is renamed] → The guide notes stable IDs as the upgrade path.
