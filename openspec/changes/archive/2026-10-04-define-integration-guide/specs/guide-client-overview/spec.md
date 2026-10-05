## Purpose

Defines the structure of the client-facing overview and its role as the single source for the agent involvement levels and the risk and control pairs.

## ADDED Requirements

### Requirement: Client overview structure
The client overview SHALL contain a section for each client question: how OpenSpec enables testing and improved code, how AI agents work with client code, and what the risks and controls are. It SHALL also contain a sources section.

#### Scenario: Client reader looks for their questions
- **WHEN** a client reader opens the overview
- **THEN** it has a section for each of the three client questions and a sources section

### Requirement: Single source for involvement levels and risk and control pairs
The client overview SHALL be the single source for the agent involvement levels and the risk and control pairs. It SHALL present the available involvement levels for the Fabric repository, name agents writing all tests and running the local ones as the recommended starting point, and state for each level what agents may do, what humans do, and what access is needed. Other documents SHALL link to these sections and SHALL NOT restate them.

#### Scenario: Reader needs the involvement levels
- **WHEN** a reader of another guide document needs the involvement levels
- **THEN** the document links to the client overview section and does not repeat the levels

#### Scenario: Reader compares levels
- **WHEN** a reader reviews the involvement levels in the client overview
- **THEN** each level states what agents may do, what humans do, and what access it needs, and the recommended starting point is named
