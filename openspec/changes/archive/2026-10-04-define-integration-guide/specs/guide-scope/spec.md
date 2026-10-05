## Purpose

Defines what the integration guide is for, who it serves, where readers start, and what it deliberately excludes, so that every chapter can be judged against a shared scope.

## ADDED Requirements

### Requirement: Guide purpose
The guide SHALL state its purpose: connecting a brownfield Fabric workspace to Git and adopting OpenSpec gradually in the resulting Fabric repository, starting with testing. It SHALL state that a high level of human involvement is recommended in that repository. The guide SHALL NOT describe how the guide's own repository is managed.

#### Scenario: Reader checks what the guide is for
- **WHEN** a reader opens the scope page
- **THEN** it states the purpose and the recommended human involvement, and says nothing about how the guide itself is produced

### Requirement: Named audiences and their questions
The guide SHALL identify two audiences, the client and the internal team. For the client, it SHALL answer how OpenSpec enables testing and improved code, how AI agents work with their code, and what the risks are. For the internal team, it SHALL answer how to carry out the implementation and how to work through testing.

#### Scenario: Client reader finds their questions answered
- **WHEN** a client reader opens the guide
- **THEN** they can locate material answering each of the three client questions without needing procedural detail

#### Scenario: Team reader finds their questions answered
- **WHEN** a team member opens the guide
- **THEN** they can locate material answering both team questions

### Requirement: Stated starting point
The guide SHALL state its assumed starting point: GitHub as the Git provider and a brownfield Fabric workspace that is not yet connected to a repository.

#### Scenario: Reader's situation differs
- **WHEN** a reader's situation does not match the assumed starting point
- **THEN** the guide's stated assumptions let them recognize this before following the steps

### Requirement: Verified Fabric claims
The guide SHALL verify claims about Fabric and related tooling against current Microsoft documentation before they are accepted into the specs or the guide text.

#### Scenario: Claim about Fabric behavior is added
- **WHEN** a Fabric or tooling claim is added to the guide
- **THEN** it has been checked against current Microsoft documentation and the source is identifiable

### Requirement: Inline examples
The guide SHALL present examples within its text and SHALL NOT ship a sample Fabric project.

#### Scenario: Example is needed
- **WHEN** a chapter needs an illustration of an artifact such as a spec or a test
- **THEN** it appears inline in the guide and no sample Fabric project is provided
