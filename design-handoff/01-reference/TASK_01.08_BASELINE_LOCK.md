# TASK 01.08 — Reference Baseline Lock Gate

**Status: NEEDS_REVIEW — NOT LOCKED**  
**Proposed baseline ID:** KEW-REF-v1.0.0-rc1  
**Owner:** Product owner (parent)  
**Scope:** 13 canonical Child App screens S01–S13, plus eight supplementary reference JPEGs.

## Baseline inventory

| Evidence | Location | State |
| --- | --- | --- |
| Source inventory and visual audit | `TASK_01.01_SOURCE_AUDIT.md`, `TASK_01.02_QUALITY_AUDIT.md` | Documented |
| Cropping specification and panel coordinates | `TASK_01.03_SPLIT_REPORT.md` | Documented |
| Canonical screen-to-source mappings | `SCREEN_ID_REGISTRY.csv` | 13 entries |
| File checksum manifest | `REFERENCE_CHECKSUMS.csv` | 9 originals + 13 crops listed |
| Viewport analysis | `TASK_01.06_VIEWPORT_ANALYSIS.md` | Documented; D-0001 open |
| Safe-area engineering proposal | `TASK_01.07_SAFE_AREAS.md` | Documented; unapproved provisional values |
| Product-owner design decisions | `../00-project/DECISION_LOG.md` | D-0001–D-0004 pending |

## Lock rules proposed

1. **Canonical:** SRC-03 original `ED0FF5A1-F9DC-4ADB-8D9E-8B951841297B.jpeg`; S01–S13 are its panels as registered in `SCREEN_ID_REGISTRY.csv`. This is the approved visual *direction*, not proof of pixel-level geometry.
2. **Supplementary:** SRC-01/02/04/05/06/07/08/09 inform supporting flows; they do not replace SRC-03 without explicit owner decision.
3. **Integrity:** Any future original/crop replacement must preserve prior SHA-256 records, register a new baseline version, document source provenance, and receive owner approval.
4. **No silent edits:** Never reinterpret illustration, mascot, palette, typography, layout, or screen ordering as an approved deviation.
5. **Unresolved decisions remain unresolved:** D-0001 (iPad target viewport), D-0002 (individual full-resolution references/crop acceptance), D-0003 (native Figma), D-0004 (original asset sources).
6. **Reference image files are not in GitHub:** only manifests and reports are currently versioned in the repository. Conversation ZIP is not a durable repository artifact. The checksum manifest is not proof that GitHub stores the binaries.

## Blocking gates for declaring LOCKED / DONE

- [ ] Owner explicitly approves this baseline version and reference hierarchy, with evidence.
- [ ] Owner resolves D-0002: accepts low-resolution collage crops as the canonical working reference **or** supplies approved individual high-resolution images.
- [ ] Canonical original and 13 reference crops are stored in a durable, versioned location accessible to the project; verify binary SHA-256 against manifest.
- [ ] If owner expects GitHub as source of truth, commit original and crop binaries and update `SCREEN_ID_REGISTRY.csv` from `NOT_IN_GITHUB` only after verification.
- [ ] Confirm all registered crop IDs and names are correct against the actual source composite.
- [ ] Record lock approval date, approver, exact version, commit SHA, and immutable file checksums.

**Not required to lock visual evidence itself:** resolution of D-0001 viewport and D-0003 Figma method, provided both remain explicitly open and no implementation treats them as approved.

## Review request to owner

**Approve KEW-REF-v1.0.0-rc1 as the visual baseline using the 13 extracted SRC-03 panels, subject to durable image publication; or supply high-resolution individual screens.** Approval of the *concept* alone does not satisfy the durable-image gate.

## Status conclusion

This document is a **baseline lock proposal**, not a completed lock. No image files were changed. Do not mark task 01.08 `DONE` until the gates above are satisfied. Task register status: `NEEDS_REVIEW`.
