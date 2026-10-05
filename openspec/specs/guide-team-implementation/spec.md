# guide-team-implementation Specification

## Purpose

Defines the structure of the team-facing guide, its boundary at characterization, and the recommended convention for linking tests to spec scenarios.

## Requirements

### Requirement: Team guide chapters
The team guide SHALL contain five chapters in this order: Prepare, Connect, Baseline, Init OpenSpec, and Testing. The Testing chapter SHALL end at characterizing one existing slice.

#### Scenario: Team reader looks for the procedure
- **WHEN** a team member opens the team guide
- **THEN** it has the five chapters in order, and the Testing chapter ends at characterizing one existing slice

### Requirement: Out-of-scope topics
The guide SHALL NOT cover branch-per-workspace flow, CI and promotion, or new feature development.

#### Scenario: Reader looks for an excluded topic
- **WHEN** a reader looks for branch flow, CI and promotion, or feature development
- **THEN** the guide states that these topics are out of scope

### Requirement: Scenario-to-test convention
The team guide SHALL recommend that tests are named by the spec scenario they cover, with stable scenario IDs described as the upgrade for teams where scenario renames break the link.

#### Scenario: Reader links a scenario to a test
- **WHEN** a reader writes a test for a spec scenario
- **THEN** the guide's convention tells them to name the test by the scenario and says what to do if renames break the link
