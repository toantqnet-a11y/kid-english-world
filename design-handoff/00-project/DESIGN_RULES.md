# Kids English World — Design Rules

**Document ID:** KEW-DR-001  
**Version:** 1.0.0  
**Task:** 00.06  
**Status:** ACTIVE — process rules; not a substitute for approved screen specifications  
**Scope:** Child-facing iPad-first PWA, 13 approved mockup screens  
**Authority:** Approved mockup references > explicitly approved design decisions > approved screen specifications > approved component specifications > implementation defaults.

## 1. Non-negotiable source of truth

- The approved 13-screen mockup is the visual reference. Do not redesign it, simplify away distinctive elements, or treat the current app as a superior design reference.
- Approved screens: **S01** Chapter Overview; **S02** Lesson Detail; **S03** Quick Review; **S04** Daily Challenge; **S05** Unit Complete; **S06** My Words; **S07** Achievements; **S08** My Stuff; **S09** Onboarding; **S10** Learning Guard; **S11** Offline Download; **S12** Progress Map; **S13** Settings.
- Do not assume that these 13 mockups cover all app flows. Unmocked Home World, Play, Story, Workshop, and Parent Admin views require separately approved designs.
- Never invent exact colors, font families, dimensions, shadows, motion parameters, or interactions based on an unreadable image. Mark `UNKNOWN` or `NEEDS_APPROVAL`.
- Store and reference the approved image manifest and checksums once TASK 01.08 is completed. Until then, reference locking is **pending**.

## 2. Visual identity and composition

1. **Style:** soft colorful illustrated 3D-style scenes; polished, modern, expressive, child-friendly but not cluttered or generic.
2. **Palette direction:** blue / violet / yellow with white rounded cards. Exact hex values must come from approved design tokens, not guesses.
3. **Characters:** keep the child-character identity and recognizable tiger mascot consistent across screens; do not replace them with another tiger, a robot, stock characters, or emoji.
4. **Illustrations:** use approved source assets when available. A recreated/cropped asset is not automatically identical; label provenance and require comparison/approval.
5. **Backgrounds:** preserve the reference composition, layering, depth, and negative space; avoid adding busy patterns not shown in the mockup.
6. **Cards:** preserve proportions, radius, shadows, content alignment, and overlap according to screen specs.
7. **Icons:** use approved vector icons or explicitly approved replacements. **Never use emoji as icon substitutes.**
8. **Text:** reproduce visible wording and hierarchy where readable. Do not invent or translate labels silently. Do not bake ordinary UI text into image assets.
9. **Spacing:** match measured positions, gaps, alignment, and content density; do not rearrange elements merely to simplify CSS.
10. **Responsive:** iPad landscape is the first validation target. Do not infer the exact CSS viewport from the pixel dimensions of a mockup. Safe areas and alternate orientations must be specified separately.

## 3. Asset rules

- Each asset must have a unique ID, file path, source/provenance, screen usage, license/ownership notes where relevant, approval status, and optional checksum.
- Keep mascot, characters, scene backgrounds, icons, and UI primitives as distinct categories.
- Complex 3D illustrations may remain raster (e.g., transparent PNG/WebP); editable text, cards, buttons, and navigation should remain native Figma/UI layers.
- No hotlinking random external images or substituting third-party branded characters.
- No upscaling, generative reconstruction, background removal, or color grading that materially changes an approved asset without comparison and approval.
- Missing required assets must be logged in `ISSUE_REGISTER.csv`; if blocking fidelity, stop the affected task.

## 4. Screen and component rules

- One screen has one stable screen ID and its own reference, specification, states, acceptance checklist, and visual QA report.
- Components have stable IDs, documented props, states, variants, dependencies, and token mapping.
- Shared components must be reused only where their appearance matches the approved reference; do not force visual uniformity that changes a mockup.
- Do not modify an approved shared component without documenting affected screens and re-running their visual regression tests.
- Separate content data from presentation. Do not hardcode curriculum structures into layout components.
- Content authoring hierarchy is **Map → Stage (Chặng) → Unit → Lesson**; do not flatten it into a single list.
- AI-generated learning content is **draft-only** until a parent reviews, edits if needed, and explicitly approves publication.

## 5. Interaction and child-experience rules

- A static mockup does not prove tap targets, animations, transitions, sound effects, or error states. Specify these independently and flag unapproved assumptions.
- All interactive elements need documented tap behavior, state feedback, and accessibility considerations.
- Child-facing screens must remain readable and touch-friendly; do not reduce hit areas to match a tiny visual icon.
- Preserve approved learning flow, reward affordances, and guard/rest reminders without introducing intimidating progress reporting or unnecessary dialogs.
- Offline, loading, error, empty, and locked states must be separately specified; never claim they are covered solely by the 13 reference images.

## 6. Figma-to-code fidelity contract

For each screen, follow this order:

1. Validate source reference and its version.
2. Produce measured screen specification; tag every property `EXACT`, `MEASURED`, `INFERRED`, or `UNKNOWN`.
3. Resolve or explicitly accept blocking unknowns.
4. Identify approved assets and component dependencies.
5. Build editable Figma structure if an authorized Figma workflow is available.
6. Export Figma screenshot and compare with the approved mockup.
7. Obtain required product-owner approval for the Figma screen.
8. Implement the code screen using approved specs/assets/tokens.
9. Capture deterministic browser screenshot at the approved viewport with fixed mock data.
10. Compare against reference, log deviations, fix defects, and repeat.
11. Request screen acceptance; only then mark screen `DONE`.

**Golden Screen:** S01 Chapter Overview must pass this process before the other screens are used to claim end-to-end handoff fidelity.

**Tool limitation:** An SVG/JSON/export is not a native editable Figma file. If direct Figma authoring is unavailable, report `BLOCKED` for the Figma task rather than claiming completion.

## 7. Visual QA and defect policy

- Every coded screen must have a reference screenshot, actual screenshot, comparison evidence, issue list, and final acceptance record.
- Use the same viewport, device scale, fonts, state, content, and animation-free capture conditions for comparable screenshots.
- Record mismatches in `design-handoff/00-project/ISSUE_REGISTER.csv` with `issue_id`, `screen_id`, `component_id`, `severity`, `description`, `expected`, `actual`, `evidence`, `status`.
- Severity definitions: `CRITICAL` (unusable or major reference violation), `HIGH` (major layout/asset/behavior mismatch), `MEDIUM` (visible spacing/type/color discrepancy), `LOW` (minor cosmetic discrepancy).
- No open `CRITICAL` or `HIGH` issue may remain when a screen is submitted for final acceptance.
- A visual similarity percentage is not proof by itself; include the method and actual evidence. Never assert “pixel-perfect” without review.

## 8. Decision and change control

- Log proposed deviations in `DECISION_LOG.md` before changing an approved reference.
- Record alternatives, rationale, affected screens/assets/components, and approval evidence.
- Only the authorized product owner can approve design changes requiring owner review. AI must not self-approve.
- If the owner rejects a deviation, restore fidelity to the approved reference.
- If the reference changes, update its version/checksum, invalidate affected approvals, and rerun relevant visual tests.

## 9. Task execution and reporting

- Perform **one atomic task at a time**. Do not combine design analysis, asset creation, Figma authoring, coding, and QA under one task.
- Before acting: read task dependency, input, and expected output in `TASK_REGISTER.csv`.
- After acting: verify the actual artifact, record evidence, and update the task status.
- Valid task statuses: `TODO`, `IN_PROGRESS`, `BLOCKED`, `NEEDS_REVIEW`, `REJECTED`, `APPROVED`, `DONE`.
- Never mark a task `DONE` merely because a file was drafted if its acceptance criteria require approval or functional validation.
- Do not silently modify application source code during documentation-only tasks.
- If an input, repository permission, image, tool, or approval is missing, report `BLOCKED` and the exact missing requirement.

## 10. Acceptance checklist — TASK 00.06

- [x] Approved mockups established as visual authority.
- [x] Tiger mascot and child character identity protected.
- [x] Emoji substitutions prohibited.
- [x] Layout redesign and unapproved UI additions prohibited.
- [x] Missing measurements/assets handled without fabrication.
- [x] Screen-by-screen visual comparison required.
- [x] Parent review of AI-generated content preserved.
- [x] Shared component change-impact and regression checks defined.
- [x] Decision approval and issue tracking integrated.
- [x] Figma capability and evidence limitations documented.

**Next task:** 00.07 — Create Definition of Done.
