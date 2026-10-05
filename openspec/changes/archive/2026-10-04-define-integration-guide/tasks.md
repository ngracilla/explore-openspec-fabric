## 1. Shared scope page

- [x] 1.1 Create `docs/scope.md` covering guide purpose and recommended human involvement, the two audiences and their questions, the assumed starting point (GitHub, unconnected brownfield workspace), and the out-of-scope topics; verify each guide-scope requirement and the out-of-scope requirement has matching text by checking the file against both specs
- [x] 1.2 State in `docs/scope.md` that examples appear inline and no sample Fabric project is shipped; verify the sentence is present

## 2. Document skeletons

- [x] 2.1 Create `docs/client-overview.md` with headings for how OpenSpec enables testing and improved code, how AI agents work with client code, and risks with controls, plus a sources appendix heading; verify the headings match the three guide-client-overview requirements
- [x] 2.2 Create `docs/team-guide.md` with the five chapter headings (Prepare, Connect, Baseline, Init OpenSpec, Testing) and a short out-of-scope note; verify the headings match the design's chapter list
- [x] 2.3 Add a single-source section for the involvement levels and the risk and control pairs, and link to it from the other document; verify each document links to the one source and neither repeats it

## 3. Conventions

- [x] 3.1 Document the sourcing convention in `docs/scope.md` (inline citations in the team guide, appendix in the client overview, a "verified on" date on every verified claim); verify the convention matches design decision 5
- [x] 3.2 Document the scenario-to-test naming convention as the recommended Fabric-repo default, with stable IDs noted as the upgrade path, in the Testing chapter skeleton; verify it matches design decision 4

## 4. Validation

- [x] 4.1 Run `openspec validate define-integration-guide --strict` and verify it reports the change as valid
- [x] 4.2 Review the three documents against the specs and verify no spec requirement lacks a home, then confirm with the user before archiving
