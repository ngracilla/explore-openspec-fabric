# Team Guide

For scope, audiences, and assumptions, see [Scope](scope.md). For the agent involvement levels and the risks and controls, see the [Client overview](client-overview.md#agent-involvement-levels).

Out of scope: branch-per-workspace flow, CI and promotion, and new feature development.

## 1. Prepare

_To be written in a later change._

## 2. Connect

By the end of this chapter, a brownfield Fabric workspace is connected to an integration branch of your GitHub repository, its items sit under `fabric/`, and the first sync is verified.

Each Fabric claim below cites the Microsoft Learn page it came from and the date we checked it (2026-10-04). Anything we could not confirm is marked **Unverified**. The pages used are listed under [Sources](#sources).

### Prerequisites

**In Fabric**
- A Fabric capacity. A Power BI Premium capacity also works, but some Power BI SKUs support only Power BI items. ([Get started](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-get-started), verified 2026-10-04)
- These tenant switches enabled: *Users can create Fabric items*, *Users can synchronize workspace items with their Git repositories*, and, for GitHub, *Users can synchronize workspace items with GitHub repositories*. *Create workspaces* is needed only to branch out to a new workspace. Depending on your organization's settings, a tenant admin, capacity admin, or workspace admin can enable them. ([Get started](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-get-started), verified 2026-10-04)
- The **workspace admin** role for whoever performs the connection. Only a workspace admin can connect or disconnect a workspace. Once it is connected, anyone with the right permissions can work in it. If you are not an admin, ask one to do the connection. ([Get started](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-get-started), [Git integration process](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-integration-process), verified 2026-10-04)

**In GitHub**
- An active GitHub account for each person who will work in the workspace. ([Get started](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-get-started), verified 2026-10-04)
- A repository, and a fine-grained personal access token for each person (see [Credentials](#credentials)).
- Cloud GitHub only. GitHub Enterprise Server with a custom domain, or on a private network, is not supported, nor is an IP allowlist. ([Git integration process](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-integration-process), verified 2026-10-04)

### Where Fabric content goes

Connect the workspace to a **`fabric/` subfolder** of the repository. Fabric connects to one branch and one folder, so a subfolder keeps item folders apart from `openspec/`, tests, and docs. ([Get started](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-get-started), verified 2026-10-04)

- If `fabric/` does not exist yet, Fabric offers to create it (**Create and sync**). ([Troubleshooting](https://learn.microsoft.com/en-us/fabric/cicd/troubleshoot-cicd), verified 2026-10-04)
- On commit, Fabric deletes files that sit inside an item's own folder but are not part of its definition. Unrelated files outside item folders are not deleted. ([Git integration process](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-integration-process), verified 2026-10-04)
- Keep only Fabric items under `fabric/`. A folder that has subdirectories but no Fabric items fails to connect. ([Troubleshooting](https://learn.microsoft.com/en-us/fabric/cicd/troubleshoot-cicd), verified 2026-10-04)

**If you connect at the repository root instead:** if the folder name is left blank, content is created in the root folder, so item folders sit beside `openspec/`, `docs/`, and everything else. ([Get started](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-get-started), verified 2026-10-04) Our reading of the troubleshooting entry above is that a root already holding `openspec/` and `docs/` but no Fabric items could fail to connect. **Unverified** for the root case specifically; we did not test it.

### Credentials

The Git connection is per user. Each person who works in the workspace configures their own connection and does not share a personal access token. ([Git integration process](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-integration-process), verified 2026-10-04)

1. Each person creates a **fine-grained** token on GitHub, scoped to the one repository, with **Contents** read and write permission. Microsoft recommends fine-grained tokens over classic ones. ([Get started](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-get-started), verified 2026-10-04)
2. In Fabric, choose **Add account** and give a display name that is unique for each GitHub user, plus the token. If you connect with a token scoped to one repository, the repository URL is filled in and you can connect only to that repository. ([Get started](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-get-started), verified 2026-10-04)
3. A second person opening an already connected workspace adds their own account on the **Accounts** tab of the Source control panel, with their own token. They do not reuse anyone else's. ([Git integration process](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-integration-process), verified 2026-10-04)

Treat your token as expiring: when you create it, note the date it needs renewing.

Which GitHub identity appears as the author of commits made from Fabric is not stated in the pages we read. **Unverified.** After the first commit, look at it in GitHub to see.

### The integration branch

Connect to a **dedicated integration branch**, for example `fabric-dev`, and merge to `main` through a reviewed pull request. Do not connect to `main`.

- Fabric commits go directly to the connected branch. The documentation says the branch policy should allow direct commits, so a protected `main` that requires pull requests is expected to block commits from Fabric. ([Git integration process](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-integration-process), verified 2026-10-04)
- A workspace connects to one branch at a time. In the connect dialog you can pick an existing branch or select **+ New Branch**. ([Get started](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-get-started), verified 2026-10-04)
- Create `main` in the repository first, for example with a README. The pages we read do not say whether a repository with no branch at all can be connected. **Unverified.**

How changes then move between staging and production is outside this guide.

### Connect and sync

1. In Fabric, open the workspace, then **Workspace settings** and **Git integration**.
2. Choose **GitHub**, then add your account (see [Credentials](#credentials)) and select **Connect**.
3. Choose the repository, the integration branch, and the `fabric/` folder.
4. Select **Connect and sync**.

([Get started](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-get-started), verified 2026-10-04)

**What the first sync does**

| Situation | What happens |
|---|---|
| Workspace has items, branch is empty | Content is copied from the workspace to the branch |
| Branch has content, workspace is empty | Content is copied from the branch to the workspace |
| Both have content | You choose the direction |

([Git integration process](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-integration-process), verified 2026-10-04)

When both sides have content, the two directions are not equal. Committing the workspace to Git exports all supported workspace content and **overwrites the current Git content**. Updating the workspace from Git **overwrites the workspace content**, and you are asked to confirm because a workspace cannot be restored the way a Git branch can. Until you choose, you cannot continue working. ([Git integration process](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-integration-process), verified 2026-10-04) For a brownfield workspace, the workspace is the source of truth, so commit it to Git.

If your workspace has folders and the Git folder does not, Fabric shows uncommitted changes. Commit them before you update the workspace. Updating first overwrites the workspace's folder structure. ([Git integration process](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-integration-process), verified 2026-10-04)

**Verify the first sync**
- The Source control icon shows **0** and each item's Git status is **Synced**.
- The bottom of the screen shows the connected branch, the time of the last sync, and a link to the last commit.
- In GitHub, on the integration branch, the items appear under `fabric/`.

([Git integration process](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-integration-process), verified 2026-10-04)

### Limits and unsupported items

- **Unsupported items are ignored.** They are not saved or synced, and not deleted. They appear in the Source control panel, but you cannot commit or update them. Several item types, including semantic models and reports, are still marked as preview. ([Overview](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/intro-to-git-integration), verified 2026-10-04)
- **Commit size:** at most 50 MB of files per commit on GitHub. Commit in smaller batches if needed. ([Git integration process](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-integration-process), [Troubleshooting](https://learn.microsoft.com/en-us/fabric/cicd/troubleshoot-cicd), verified 2026-10-04)
- **File size:** at most 25 MB per file. **Path length:** at most 250 characters for a full path; longer names fail. ([Git integration process](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-integration-process), verified 2026-10-04)
- **Item count:** at most 1,000 items per workspace. If the branch holds more, syncing to the workspace fails. ([Git integration process](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-integration-process), verified 2026-10-04)
- **Folder depth:** structure is kept up to 10 levels. ([Git integration process](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-integration-process), verified 2026-10-04)
- **Sensitivity labels** are not supported, and exporting labelled items may be disabled until an administrator allows it. ([Git integration process](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-integration-process), verified 2026-10-04)
- **From 1 December 2026,** users without read-write permission on workspace items can no longer use Git integration. Check your team's roles before then. ([Git integration process](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-integration-process), verified 2026-10-04)

### Sources

All checked on 2026-10-04. The date in brackets is the page's last-updated date at that time.

- [Get started with Git integration](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-get-started) (updated 2026-09-29)
- [Overview of Fabric Git integration](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/intro-to-git-integration) (updated 2026-09-29)
- [Git integration process](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/git-integration-process) (updated 2026-09-08)
- [Troubleshoot the Fabric lifecycle management tools](https://learn.microsoft.com/en-us/fabric/cicd/troubleshoot-cicd) (updated 2026-09-29)

**Unverified in this chapter:** the root-folder connection behavior, connecting a repository with no branch, and who is recorded as commit author.

## 3. Baseline

_To be written in a later change._

## 4. Init OpenSpec

_To be written in a later change._

## 5. Testing

_To be written in a later change. The chapter ends at characterizing one existing slice._

### Linking tests to scenarios

The recommended convention for the Fabric repository is to name each test, or repeat in its docstring, the name of the spec scenario it covers. If scenario renames break this link, move to stable scenario IDs that tests cite.
