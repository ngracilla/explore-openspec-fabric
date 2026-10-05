## Why

The team guide has a Connect chapter heading but no content. Readers need a verified procedure for connecting a brownfield Fabric workspace to GitHub, covering the choices that cannot be undone casually: where Fabric content sits in the repo, whose credentials are used, and which branch is connected.

## What Changes

- Add the content requirements for the Connect chapter of the team guide, resting on three decisions:
  - Fabric content is connected to a `fabric/` subfolder of the repository, so `openspec/`, tests, and docs sit alongside it and are not touched by Fabric commits.
  - Each user adds their own fine-grained GitHub token scoped to the one repository (Contents read and write). Tokens and accounts are not shared.
  - The workspace connects to a dedicated integration branch, and changes reach `main` through a reviewed pull request.
- Require the chapter to cover prerequisites, the connection steps, the first sync (including choosing a direction when both sides have content) and how to verify it, and the limits a reader should expect.
- Require every Fabric claim in the chapter to cite its Microsoft Learn source inline with a "verified on" date, and to mark claims that could not be verified.
- Keep the existing out-of-scope boundary: how changes move between branches and environments (staging versus production) remains out of scope and is a separate later piece of work.

## Capabilities

### New Capabilities

None.

### Modified Capabilities
- `guide-team-implementation`: adds requirements for the content of the Connect chapter. Existing requirements are unchanged.

## Impact

- `openspec/specs/guide-team-implementation/spec.md` gains Connect-chapter requirements once archived.
- `docs/team-guide.md` gets the Connect chapter text during apply.
- No Fabric items or code are affected.
