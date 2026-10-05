## 1. Verification

- [x] 1.1 Try to verify, from Microsoft documentation, whether a repository with no branch can be selected during connection; record the answer and source with a verified-on date, or record that it remains unverified
- [x] 1.2 Try to verify whose identity is recorded as commit author for commits made from Fabric; record the answer and source with a verified-on date, or record that it remains unverified
- [x] 1.3 Re-check that the three Microsoft Learn pages used (Get started, Overview, Git integration process) have not changed in the facts the chapter relies on; verify by recording each page's last-updated date next to the verified-on date

## 2. Chapter content

- [x] 2.1 Write the prerequisites section in the Connect chapter of `docs/team-guide.md` (capacity, tenant switches, GitHub account and token, workspace admin role), each claim cited inline with a verified-on date; verify against the prerequisites requirement and its two scenarios
- [x] 2.2 Write the folder and credentials sections (the `fabric/` subfolder and what happens at the repository root; per-user fine-grained tokens with Contents read and write and no sharing); verify against those two requirements and their scenarios
- [x] 2.3 Write the integration-branch section (recommendation, direct-commit requirement, pull request to `main`, and an out-of-scope note on moving changes between environments); verify against that requirement and its two scenarios
- [x] 2.4 Write the first-sync and verification section covering the three cases and how to confirm success; verify against that requirement and its two scenarios
- [x] 2.5 Write the expected-limits section (unsupported items ignored, commit size, file size, path length, item count, the dated permissions change); verify against that requirement and its scenario
- [x] 2.6 Mark any claim still unverified as unverified in the text; verify by searching the chapter for each unverified item from group 1 and confirming it is marked

## 3. Validation

- [x] 3.1 Run `openspec validate add-connect-chapter --strict` and verify it reports the change as valid
- [x] 3.2 Review the Connect chapter against every requirement in the delta spec and verify none lacks matching text, then confirm with the user before archiving
