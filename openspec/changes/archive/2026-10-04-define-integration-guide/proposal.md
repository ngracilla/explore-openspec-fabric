## Why

We want to connect a brownfield Microsoft Fabric workspace to Git and adopt OpenSpec gradually, starting with testing. No guide exists yet for doing this, and the team and the client need one. This repo exists to produce that guide, so its scope and audiences need to be defined before any chapters are written.

## What Changes

- Define this repo's purpose: it holds the integration guide only. It contains no sample Fabric project. OpenSpec fully manages this repo, including agent-assisted apply, to specify the guide and to support exploration.
- Distinguish two repos. This repo (full OpenSpec) produces the guide. The Fabric repo (the reader's project) adopts OpenSpec gradually and keeps a high level of human involvement. The guide recommends the Fabric repo's rules, and does not apply them to itself.
- Define two audiences and the questions the guide must answer for each:
  - Client (overview): how OpenSpec enables testing and improved code; how AI agents work with their code; what the risks are.
  - Internal team (procedural): how to carry out the implementation; how to work through testing.
- Scope the team guide to five chapters: Prepare, Connect, Baseline, Init OpenSpec, and Testing (ending at characterizing one existing slice). Branch-per-workspace flow, CI and promotion, and new feature development are out of scope.
- Fix the assumed starting point for readers: GitHub as the Git provider, and a brownfield Fabric workspace not yet connected to a repo.
- Require that Fabric and tooling claims be verified against current Microsoft documentation before they enter the specs.

## Capabilities

### New Capabilities
- `guide-scope`: purpose of the guide, the two audiences, the questions each must have answered, the assumed starting point, and what is out of scope.
- `guide-client-overview`: the structure of the client-facing overview, and its role as the single source for the agent involvement levels and the risk and control pairs.
- `guide-team-implementation`: the structure of the team-facing guide (five chapters ending at characterization), its out-of-scope topics, and the scenario-to-test naming convention. Chapter content is added by later changes, which extend these specs.

### Modified Capabilities

None. No specs exist yet.

## Impact

- New specs under `openspec/specs/` once this change is archived.
- No code and no Fabric artifacts are affected.
- Later changes add the guide chapters themselves. This change defines only scope and the capability structure.
