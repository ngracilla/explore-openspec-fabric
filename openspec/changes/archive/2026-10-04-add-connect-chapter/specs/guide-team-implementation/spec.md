## ADDED Requirements

### Requirement: Connect chapter prerequisites
The Connect chapter SHALL list the Fabric prerequisites (a Fabric capacity and the tenant switches that must be enabled), the GitHub prerequisites (an account and a token), and the workspace role required to connect.

#### Scenario: Reader checks readiness before connecting
- **WHEN** a reader opens the Connect chapter
- **THEN** they can tell which tenant switches, accounts, and roles they need before starting

#### Scenario: Reader is not a workspace admin
- **WHEN** a reader without the workspace admin role follows the chapter
- **THEN** the chapter tells them that an admin must perform the connection

### Requirement: Fabric content in a subfolder
The Connect chapter SHALL recommend connecting the workspace to a `fabric/` subfolder of the repository, so that other repository content such as `openspec/`, tests, and docs sits alongside it. It SHALL describe what happens if a team connects at the repository root instead.

#### Scenario: Reader chooses a folder
- **WHEN** a reader reaches the folder choice during connection
- **THEN** the chapter recommends `fabric/` and states the consequence of using the repository root

### Requirement: Per-user fine-grained tokens
The Connect chapter SHALL instruct each user to create and add their own fine-grained GitHub token scoped to the one repository with Contents read and write permission. It SHALL state that tokens and accounts are not shared between users.

#### Scenario: Second user joins a connected workspace
- **WHEN** a second user opens a workspace that is already connected
- **THEN** the chapter tells them to add their own account and token and not reuse another user's

### Requirement: Integration branch connection
The Connect chapter SHALL recommend connecting the workspace to a dedicated integration branch and merging to `main` through a reviewed pull request. It SHALL state that Fabric commits go directly to the connected branch, so that branch has to allow direct commits. It SHALL NOT describe how changes move between environments.

#### Scenario: Reader chooses a branch
- **WHEN** a reader reaches the branch choice during connection
- **THEN** the chapter recommends a dedicated integration branch and explains why connecting to a protected `main` would block commits

#### Scenario: Reader asks about promotion between environments
- **WHEN** a reader looks for how changes move between staging and production
- **THEN** the chapter states that this is outside its scope

### Requirement: First sync and verification
The Connect chapter SHALL explain the initial sync for each case: workspace has content and the branch is empty, branch has content and the workspace is empty, and both have content, where the reader must choose a direction and the consequences of each direction are stated. It SHALL give a way to verify that the first sync succeeded.

#### Scenario: Brownfield workspace and empty branch
- **WHEN** a reader connects a workspace with items to an empty branch
- **THEN** the chapter states that workspace content is copied to the branch, and how to confirm the items appear in the repository and the workspace shows as synced

#### Scenario: Both sides have content
- **WHEN** both the workspace and the branch have content
- **THEN** the chapter explains each sync direction and warns which one overwrites workspace content

### Requirement: Expected limits and unsupported items
The Connect chapter SHALL tell the reader that unsupported items are ignored and not deleted, and SHALL state the limits that can block a first sync or commit, including commit size, file size, path length, and item count. It SHALL note dated changes to permissions that affect access.

#### Scenario: Reader's workspace contains an unsupported item
- **WHEN** a reader's workspace includes an item type that Git integration does not support
- **THEN** the chapter explains that the item is ignored and appears in the source control panel without being committable

### Requirement: Dated sources and unverified claims
Every Fabric claim in the Connect chapter SHALL cite its Microsoft Learn source inline with a "verified on" date. A claim that could not be verified SHALL be marked as unverified instead of stated as fact.

#### Scenario: Chapter states a Fabric behavior
- **WHEN** the chapter states a Fabric behavior
- **THEN** the statement links to the Microsoft Learn page it came from and carries a verified-on date

#### Scenario: Behavior could not be verified
- **WHEN** a behavior such as who is recorded as commit author cannot be confirmed from the documentation
- **THEN** the chapter marks it as unverified
