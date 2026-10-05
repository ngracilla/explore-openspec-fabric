## Context

The Connect chapter lives in `docs/team-guide.md` and extends the archived `guide-team-implementation` spec. See proposal.md - Why for motivation. The chapter's facts come from three Microsoft Learn pages: Get started with Git integration, Overview of Fabric Git integration, and Git integration process. All three were read on 2026-10-04 and were last updated between 2026-06-15 and 2026-09-29. The guide's team readers are Nick and Robert, each able to create a GitHub token.

## Goals / Non-Goals

**Goals:**
- A procedure a workspace admin can follow to connect a brownfield workspace to GitHub and confirm the first sync.
- Making the three irreversible-feeling choices (folder, credentials, branch) explicit with a recommended default.

**Non-Goals:**
- Staging versus production workflow and any movement of changes between environments. That is deferred and conflicts with the current out-of-scope requirement, so it needs its own change.
- Branching strategy beyond the single integration branch the workspace connects to.

## Decisions

### 1. Connect to a `fabric/` subfolder
Fabric connects to one branch and one folder. A subfolder keeps item folders apart from `openspec/`, tests, and docs. On commit Fabric deletes only unrelated files inside an item's own folder, and does not touch files outside item folders, so repository content outside `fabric/` is not at risk.
*Alternative: connect at the repository root.* Rejected as the default: item folders would mix with everything else. The chapter still explains it.

### 2. Per-user fine-grained tokens
The Git connection is per user, and Microsoft advises each user to configure their own connection and not share a token. Each user creates a fine-grained token scoped to the one repository with Contents read and write.
*Alternative: one shared token, or a dedicated bot account.* Rejected: it conflicts with Microsoft's guidance and ties the connection to one credential. *Alternative: classic token with repo scope.* Not recommended: it is broader than needed.

### 3. Dedicated integration branch
Commits from Fabric go directly to the connected branch, so that branch must allow direct commits. A dedicated branch lets `main` require reviewed pull requests, which matches the recommended high level of human involvement in the Fabric repository. Fabric only writes under `fabric/`, so conflicts with changes elsewhere in the repository should be rare.
*Alternative: connect to `main`.* Rejected as the default: it requires switching off review on `main`. The cost accepted is one extra branch to merge regularly.

### 4. Sourcing and unverified claims
Following the guide's sourcing convention, the team guide cites each Microsoft Learn page inline with a "verified on" date. Claims that could not be confirmed are marked unverified. Two are known today: whether a repository with no branch can be selected, and whose identity is recorded as commit author. Apply is to try verifying these before writing them as fact, and otherwise mark them.

## Risks / Trade-offs

- [Microsoft changes the procedure or limits] → Dated claims make staleness visible; re-verify when a date is old.
- [A dated permissions change on 1 December 2026 limits who can use Git integration] → The chapter states it explicitly with its date so readers can plan for it.
- [Two unverified behaviors enter the chapter as facts] → The spec requires them to be marked unverified unless confirmed.
- [The integration branch drifts from `main`] → The chapter recommends regular merging through the reviewed pull request.
