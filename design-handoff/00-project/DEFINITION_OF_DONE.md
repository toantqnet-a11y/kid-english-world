# Kids English World — Definition of Done (DoD)

**Document ID:** KEW-DOD-001  
**Version:** 1.0.0  
**Task:** 00.07  
**Status:** ACTIVE  
**Applies to:** Design-to-Code Handoff Package and its atomic tasks  
**Owner:** Product owner (parent)

## 1. Core principle

**A created file is not automatically a completed deliverable.** A task is `DONE` only after its own acceptance criteria, evidence, dependencies, and required approvals are satisfied. AI must not substitute its own approval for the product owner's approval.

## 2. Task-level exit gate (all tasks)

For every task in `TASK_REGISTER.csv`, verify:

- [ ] Correct task ID and expected output path.
- [ ] All declared dependencies are `DONE` or explicitly authorized exceptions are recorded in `DECISION_LOG.md`.
- [ ] Input references exist and are versioned where applicable.
- [ ] Output exists in the agreed location and is readable.
- [ ] Output satisfies the task's specific acceptance checklist.
- [ ] Required quality checks have run; record results, not assertions.
- [ ] Known defects/unknowns are documented in `ISSUE_REGISTER.csv` or `DECISION_LOG.md`.
- [ ] Required reviewer has reviewed the deliverable; attach approval evidence where required.
- [ ] Evidence path and, when verifiable, completion timestamp are written to `TASK_REGISTER.csv`.
- [ ] No unrelated source files or artifacts were modified.

If any mandatory check fails, the task is **not DONE**. Use `BLOCKED` for missing prerequisites, `NEEDS_REVIEW` for pending human approval, or `IN_PROGRESS` for unfinished work.

## 3. Asset DoD

- [ ] Stable asset ID and semantic filename.
- [ ] Source/provenance documented (approved original, crop, traced, reconstructed, or newly proposed).
- [ ] Usage mapped to screen IDs and/or component IDs.
- [ ] Correct export format, dimensions, transparency, and color handling for intended use.
- [ ] Inspect visually at intended display size and against source reference.
- [ ] No accidental halos, clipping, unwanted background, broken alpha, or rasterized UI text.
- [ ] File exists, loads, and has recorded path; optimize without visible degradation.
- [ ] Ownership/license status recorded; unapproved external copyrighted substitutes excluded.
- [ ] If reconstructed or materially altered, obtain explicit owner approval and link evidence.
- [ ] Asset manifest updated; no unresolved critical/high visual issues.

**Evidence:** manifest entry, asset file, reference crop, visual comparison, approval if needed.

## 4. Component Specification DoD

- [ ] Stable component ID, name, purpose, and screen usage.
- [ ] Approved reference(s) linked; no unapproved standardization across visually different screens.
- [ ] Dimensions, spacing, alignment, typography, colors, radii, and shadows recorded with confidence labels (`EXACT`, `MEASURED`, `INFERRED`, `UNKNOWN`).
- [ ] Component hierarchy, dependencies, tokens, and asset IDs recorded.
- [ ] Props, content slots, states, variants, and edge cases specified.
- [ ] Interaction and accessibility requirements specified where applicable.
- [ ] Responsive rules documented, or explicitly flagged for approval.
- [ ] Acceptance criteria testable and linked to reference evidence.
- [ ] No blocking unknowns or unapproved deviations remain.

**Evidence:** component spec, dependency links, annotated reference, review record.

## 5. Screen Specification DoD (S01–S13)

- [ ] Correct screen ID and approved reference version/checksum.
- [ ] Reference viewport, orientation, and capture conditions documented or explicitly marked unresolved.
- [ ] Regions, layers, z-order, bounding boxes, alignment, spacing, and scroll behavior specified.
- [ ] Text, icons, images, and content state inventoried.
- [ ] Typography, palette, radii, and shadows mapped to tokens or flagged as unknown.
- [ ] All assets and component IDs linked; missing items tracked.
- [ ] Visible state distinguished from inferred loading, empty, error, locked, and success states.
- [ ] All measurements labeled by evidence/confidence; no invented precision.
- [ ] Differences from approved mockup entered into Decision Log and approved if necessary.
- [ ] Reviewer can reproduce intended screen without guessing.

**Evidence:** approved reference, measurements/annotations, screen spec, open issue list.

## 6. Figma Screen DoD

- [ ] Authorized Figma file exists and exact file/page/frame identifiers are recorded.
- [ ] Frame dimensions correspond to approved target viewport.
- [ ] Native editable text, cards, buttons, layout, and components used where feasible.
- [ ] Approved complex illustration assets placed without identity drift.
- [ ] Components/variants/tokens linked consistently; layers named meaningfully.
- [ ] No missing fonts, broken images, hidden critical layers, or clipping.
- [ ] Screenshot exported from actual Figma frame at the agreed dimensions.
- [ ] Side-by-side or overlay comparison with approved mockup performed and archived.
- [ ] Critical/high discrepancies resolved; medium/low deviations logged with owner disposition.
- [ ] Product owner explicitly approves screen fidelity; approval evidence recorded.

**Evidence:** Figma file/frame link, exported screenshot, comparison image, QA report, approval.

**Important:** An SVG, PNG, HTML page, or Figma-like JSON does **not** count as a native editable Figma screen. If Figma editing is unavailable, mark the task `BLOCKED` rather than `DONE`.

## 7. Code Screen DoD

- [ ] Depends on an approved screen specification and approved Figma screen (or documented owner-authorized alternative).
- [ ] Screen route and expected interactions work; no placeholder masquerades as a finished feature.
- [ ] Approved shared components, tokens, icons, and illustrations are used.
- [ ] Curriculum data is separated from layout and respects Map → Stage → Unit → Lesson.
- [ ] AI-generated learning material cannot become child-visible without parent review and approval.
- [ ] Build/typecheck/lint and relevant tests pass; record actual commands and results.
- [ ] No runtime errors, broken asset requests, layout overflow, or unreadable text at target viewport.
- [ ] Touch targets, keyboard behavior, focus, accessibility, and loading/error states checked where relevant.
- [ ] Deterministic screenshot captured at reference viewport with known state/content.
- [ ] Screenshot comparison performed against approved reference; defects recorded and addressed.
- [ ] No open critical/high defects; other issues have documented owner disposition.
- [ ] Product owner explicitly approves final screen fidelity.

**Evidence:** commit SHA, test logs, screenshot, visual comparison, issue records, approval.

## 8. Visual QA DoD

- [ ] Reference and actual screenshots are clearly labeled with screen ID and version.
- [ ] Device/viewport, device-pixel ratio, orientation, zoom, font availability, and content state recorded.
- [ ] Screenshots use matching crop and stable render conditions (e.g., animations paused).
- [ ] Comparison evidence includes side-by-side and/or overlay; optional diff metric includes method.
- [ ] Inspect geometry, illustration identity, color, typography, layering, shadows, and clipping.
- [ ] Every material mismatch logged with severity, expected vs actual, and evidence.
- [ ] Re-test after fixes; preserve before/after evidence.
- [ ] Zero open `CRITICAL` or `HIGH` defects at final acceptance.
- [ ] Reviewer acceptance recorded; do not claim “pixel-perfect” from a subjective impression.

**Evidence:** captures, comparison files, issue register, test report, sign-off.

## 9. Documentation-only task DoD

- [ ] Required document/file exists in the specified repository path.
- [ ] Required schema/sections are present and internally consistent.
- [ ] Links and referenced files are checked when available.
- [ ] Commit SHA recorded and file re-fetched from GitHub.
- [ ] `TASK_REGISTER.csv` status/evidence updated after verification.
- [ ] No app source code changed.

For `TASK 00.07`, completion means this policy file has been created and verified; it **does not** imply that the future asset/Figma/code tasks have passed their DoD.

## 10. Review and sign-off matrix

| Deliverable | AI may validate | Owner approval required before final DONE |
| --- | --- | --- |
| Repository setup / documentation | Yes | Only if task explicitly requires it |
| Asset copied exactly from approved source | Yes | If provenance or fidelity is uncertain |
| New/reconstructed asset | Yes | **Yes** |
| Component spec | Yes | If design choices or deviations need owner decision |
| Screen spec | Yes | If assumptions or unresolved design decisions affect fidelity |
| Figma screen | Yes | **Yes** |
| Code screen | Yes | **Yes** |
| Visual QA final acceptance | Yes | **Yes** |
| Curriculum AI draft publication | No self-publication | **Yes, parent review and approval** |

## 11. Final handoff/release gate

Release is eligible only if:

1. All 13 screen references and approved versions are traceable.
2. Required assets, components, screen specs, Figma screens, code screens, and QA evidence exist.
3. All mandatory task dependencies and acceptance gates pass.
4. No unresolved critical/high issue exists.
5. Owner-required approvals are documented.
6. Code build and device tests pass with actual evidence.
7. The release manifest lists commit SHAs, version identifiers, known limitations, and outstanding approved exceptions.

**Do not mark the overall handoff `DONE` until every mandatory release condition is met.**

## 12. Acceptance checklist — TASK 00.07

- [x] Global task exit criteria defined.
- [x] Asset DoD defined.
- [x] Component Specification DoD defined.
- [x] Screen Specification DoD defined.
- [x] Figma Screen DoD defined.
- [x] Code Screen DoD defined.
- [x] Visual QA DoD defined.
- [x] Documentation-only DoD defined.
- [x] Reviewer/approval responsibilities defined.
- [x] Final release gate defined.

**Next task:** 00.08 — Create versioning policy.
