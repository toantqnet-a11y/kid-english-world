# TASK 01.08 — Reference Baseline Lock Gate

**Status: BLOCKED — OWNER APPROVED OPTION A; BINARY PUBLICATION PENDING**  
**Approved reference choice:** Option A — use the existing SRC-03 composite and its 13 extracted crops, accepting current resolution limitations (owner's explicit reply: `A`).  
**Candidate baseline ID:** KEW-REF-v1.0.0-rc1 (not yet locked)  
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

- [x] Owner approves Option A, the existing SRC-03 composite and extracted panels, as the reference choice; approval evidence: user's reply `A` in this conversation. Final lock still depends on durable publication.
- [x] Owner resolves D-0002 by choosing low-resolution collage crops as the canonical working reference (Option A).
- [ ] Canonical original and 13 reference crops are stored in a durable, versioned location accessible to the project; verify binary SHA-256 against manifest.
- [ ] If owner expects GitHub as source of truth, commit original and crop binaries and update `SCREEN_ID_REGISTRY.csv` from `NOT_IN_GITHUB` only after verification.
- [ ] Confirm all registered crop IDs and names are correct against the actual source composite.
- [ ] Record lock approval date, approver, exact version, commit SHA, and immutable file checksums.

**Not required to lock visual evidence itself:** resolution of D-0001 viewport and D-0003 Figma method, provided both remain explicitly open and no implementation treats them as approved.

## Review request to owner

**Owner response received:** `A` — use existing SRC-03 and extracted crops, with known resolution limits. No further choice between A/B is needed. Remaining action: publish original and 13 PNG binaries durably and verify checksums.

## Status conclusion

Owner has approved Option A, but this document is **not a completed baseline lock**: image binaries are still absent from GitHub and not verified in durable repository storage. Do not mark 01.08 `DONE` until publication and integrity gates are satisfied. Task register status: `BLOCKED`.


## Verification update — 2026-10-08

- Verified **all 22 files** directly from the mounted original JPEGs and the previously generated ZIP using SHA-256, byte lengths, and Pillow dimensions against `REFERENCE_CHECKSUMS.csv`: **22/22 PASS, 0 mismatches**.
- Verified source crop ZIP has **13 PNGs + manifest.json**.
- Packaged **9 original JPEGs + 13 cropped PNGs + manifest + checksum CSV** into the conversation artifact `KEW_REFERENCE_BASELINE_A_APPROVED.zip` (8,355,872 bytes), for owner download and durable storage.
- Tested container Git network access: `git ls-remote` failed because `github.com` cannot be resolved in the container. Available GitHub connector binary API accepts base64 text but has no supported local-file-to-connector bridge for these images. **No image binaries were committed to GitHub.**
- Option A approval remains valid; **baseline lock remains BLOCKED** only on durable source image publication and repository integrity verification. The bundled ZIP itself is **not** a GitHub baseline lock.
