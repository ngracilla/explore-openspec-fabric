# Integration Guide: Scope

## Purpose

This guide helps you connect a brownfield Microsoft Fabric workspace to Git and adopt OpenSpec in the resulting Fabric repository gradually, starting with testing. It recommends a high level of human involvement in that repository, and describes the options in the [Client overview](client-overview.md#agent-involvement-levels).

## Audiences

| Audience | Document | Questions it answers |
|---|---|---|
| Client | [Client overview](client-overview.md) | How will OpenSpec enable testing and improved code for us? How do AI agents work with our code? What are the risks? |
| Internal team | [Team guide](team-guide.md) | How do I carry out the implementation? How do I work through testing? |

## Assumed starting point

- GitHub is the Git provider.
- The Fabric workspace is a brownfield workspace that is not yet connected to a repository.

If your situation differs, check whether the steps still apply before following them.

## Out of scope

- Branch-per-workspace flow
- CI and promotion
- New feature development

A reader looking for these topics will not find them in this guide.

## Examples

Examples appear inline in the guide text. The guide does not ship a sample Fabric project.

## Conventions

### Sourcing Fabric claims

Fabric and tooling claims are checked against current Microsoft documentation before they enter the guide.

- The team guide cites the Microsoft documentation inline, next to the step it supports.
- The client overview uses a sources appendix.
- In both styles, every verified claim carries a "verified on" date so that stale claims are visible.
