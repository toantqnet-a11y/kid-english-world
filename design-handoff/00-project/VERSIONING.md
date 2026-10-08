# Kids English World — Versioning Policy

**Document ID:** KEW-VP-001  
**Task:** 00.08  
**Version:** 1.0.0  
**Status:** ACTIVE  
**Owner:** Product owner  
**Scope:** Approved references, assets, design tokens, components, screen specifications, Figma, code, QA evidence, and handoff releases.

## 1. Objectives

- Trace exactly which approved visual reference produced each Figma frame and code screen.
- Make changes auditable and reversible.
- Never silently overwrite an approved mockup or its approval evidence.
- Prevent mixing incompatible reference, asset, token, component, and code versions.
- Keep each task atomic, with evidence in `TASK_REGISTER.csv`.

## 2. Version format and rules

Use semantic versions `MAJOR.MINOR.PATCH` for specifications, reusable components, assets with independently changing content, and handoff releases.

| Change type | Increment | Examples |
| --- | --- | --- |
| MAJOR | Breaking visual, structural, or API change | Approved screen redesign; incompatible component props; schema breaking change |
| MINOR | Backward-compatible addition | New component variant; new documented optional state |
| PATCH | Nonbreaking correction | Typo, metadata correction, minor asset optimization with verified unchanged appearance |

- Start a new independently managed artifact at `1.0.0` **only after its first approved baseline**. Drafts use `0.x.y` or `DRAFT` until approved.
- A version number is **not** proof of approval; track approval status separately.
- An approval of one artifact version does not automatically approve subsequent versions.
- If unsure whether a change breaks fidelity, use `NEEDS_REVIEW` and request owner approval before choosing a version bump.
- Git commit SHA identifies repository state; version identifies intended artifact compatibility. Record both.

## 3. Artifact identification and provenance

| Artifact | Stable ID example | Version / immutable reference | Required provenance |
| --- | --- | --- | --- |
| Mockup reference | `REF-S01` | `ref_version` + SHA-256 | Source image, approved-by, approval evidence |
| Asset | `AST-TIGER-001` | `asset_version` + SHA-256 | Source type, original/crop/reconstruction, usage |
| Token set | `TOKENS-CHILD` | Semantic version + Git SHA | Source reference(s), decisions |
| Component | `CMP-CHAPTER-CARD` | Semantic version + Git SHA | Props, tokens, asset dependencies |
| Screen specification | `SPEC-S01` | Semantic version + reference version | Measurements, confidence labels, approvals |
| Figma screen | `FIG-S01` | Figma file/page/frame ID + version | Linked spec/reference, export, owner approval |
| Code screen | `CODE-S01` | App version + Git SHA | Route, spec/Figma version, QA results |
| QA evidence | `QA-S01` | Immutable run ID + capture metadata | Compared reference, screenshots, issue links |
| Handoff release | `HANDOFF` | Semantic version + Git tag/SHA | Manifest of all included artifacts |

**Do not invent** a SHA-256, approval date, Figma URL, or source asset version. Mark `UNKNOWN` until verified.

## 4. Reference image immutability

1. Keep approved mockup originals in a versioned location under `01-reference/`; do not edit them in place.
2. Name screen images consistently, for example `REF-S01_v1.0.0.png`.
3. Record SHA-256 checksum, source, dimensions, approval status, and date in a reference manifest when created by later tasks.
4. Crops and annotated measurements are **derived** assets; store separately and link to the immutable original.
5. If the owner changes an approved reference, preserve the previous file and checksum; create a new version and decision record.
6. Mark downstream screen specs, Figma, code, and QA as **NEEDS_REVIEW** if their reference changes.

**Current state:** the canonical 13 individual source images and checksums have not yet been verified by EPIC 01. No baseline hash is asserted here.

## 5. Dependency lock and change impact

A screen implementation must record the exact versions it used:

```yaml
screen_id: S01
reference:
  id: REF-S01
  version: UNKNOWN
  sha256: UNKNOWN
spec:
  id: SPEC-S01
  version: DRAFT
figma:
  frame_id: UNKNOWN
  version: UNKNOWN
tokens:
  id: TOKENS-CHILD
  version: UNKNOWN
assets: []
components: []
code:
  git_commit: UNKNOWN
qa:
  run_id: UNKNOWN
approval:
  status: NEEDS_REVIEW
  evidence: null
```

- Changes to tokens require checking every dependent component and screen.
- Changes to a shared component require identifying every screen that uses it and rerunning their visual QA.
- Changes to an asset require checking all placements and sizes in affected screens.
- Changes to the reference require remeasurement, Figma revalidation, code comparison, and renewed owner acceptance when fidelity changes.
- A new app build does not automatically mean the design handoff is approved.

## 6. Figma and code synchronization

- Record exact Figma file, page, frame, version, and exported screenshot ID for each approved screen.
- Record the app route, branch, commit SHA, viewport, and deterministic screenshot for each coded screen.
- Link each code screen to its approved Figma version or explicit owner-authorized alternative.
- Never mark code `DONE` when it is based on an unapproved Figma revision.
- An SVG/JSON export is not evidence of a native editable Figma frame.
- If Figma access is missing, mark the corresponding task `BLOCKED` and document the limitation.

## 7. Branching, commits, and tags

- Follow existing repository conventions when available; do not assume a branch protection policy that has not been verified.
- Keep commits scoped to the current atomic task.
- Suggested commit format: `docs(handoff): ...`, `design(asset): ...`, `feat(screen): ...`, `fix(visual): ...`.
- Prefer feature branches and pull requests for app code or substantial visual changes when repository workflow permits.
- Use annotated release tags such as `handoff-v1.0.0` **only after** the final release gate passes.
- Never create a release tag merely because documentation exists.

## 8. Manifest and changelog requirements

For each released handoff, create a manifest containing:
- Release ID and semantic version.
- Git SHA and tag (if any).
- All 13 reference IDs, versions, checksums, and approval records.
- Design token version.
- Component and asset version manifest references.
- Per-screen spec/Figma/code/QA versions and approvals.
- Outstanding issues, accepted exceptions, and compatibility notes.

Maintain a changelog entry with date, author, reason, changed artifact IDs, version transitions, decision ID, and affected screens. **Do not backfill guessed dates or approvals.**

## 9. Rollback procedure

1. Identify last verified approved release and its manifest.
2. Restore the exact Git commit/tag and matching immutable references/assets.
3. Confirm dependency versions match the manifest.
4. Re-run build, device checks, and visual QA for affected screens.
5. Record rollback reason, issue/decision references, and owner approval when required.
6. Publish a new release version; do not silently rewrite an existing approved release.

## 10. Task 00.08 acceptance checklist

- [x] Semantic version policy defined.
- [x] Versioning for references, assets, components, tokens, Figma, code, QA, and releases defined.
- [x] Immutable mockup/reference handling specified.
- [x] Git SHA and asset checksums distinguished from semantic versions.
- [x] Dependency/change-impact checks documented.
- [x] Figma-to-code version traceability documented.
- [x] Release manifest and changelog fields defined.
- [x] Rollback procedure defined.
- [x] No fabricated baseline versions, checksums, or approvals.

**Next planned task:** 01.01 — Count source mockups, after EPIC 00 is complete.
