# TASK 01.03 — Split Composite Mockups

**Status:** DONE — 13 reference panels cropped and packaged; **GitHub binary publication pending**.  
**Input:** SRC-03 canonical 13-screen composite, `ED0FF5A1-F9DC-4ADB-8D9E-8B951841297B.jpeg` (1536 × 1024).  
**Output:** `kew_01_03_13_screen_crops.zip` (conversation artifact) containing 13 PNG crops and `manifest.json`.  
**Method:** PIL pixel crop only; no resizing, redrawing, generative fills, sharpening, or typography replacement.

## Crop coordinates

Coordinates are source-image pixels `(left, top, right, bottom)`, right/bottom exclusive.

| ID | Screen | Bounding box | Output pixels |
|---|---|---|---|
| S01 | Chapter Overview | (0,0,389,473) | 389×473 |
| S02 | Lesson Detail | (391,0,753,473) | 362×473 |
| S03 | Quick Review | (756,0,1071,473) | 315×473 |
| S04 | Daily Challenge | (1073,0,1309,473) | 236×473 |
| S05 | Unit Complete | (1312,0,1536,473) | 224×473 |
| S06 | My Words | (0,478,414,845) | 414×367 |
| S07 | Achievements | (417,478,756,845) | 339×367 |
| S08 | My Stuff | (759,478,1171,845) | 412×367 |
| S09 | Onboarding | (1174,478,1536,845) | 362×367 |
| S10 | Learning Guard | (0,851,409,1024) | 409×173 |
| S11 | Offline Download | (412,851,773,1024) | 361×173 |
| S12 | Progress Map | (776,851,1317,1024) | 541×173 |
| S13 | Settings | (1320,851,1536,1024) | 216×173 |

## Acceptance evidence

- [x] Source composite read from the original user upload.
- [x] 13/13 labeled screens extracted into separate PNG files.
- [x] No image content altered; pixel crops exported losslessly as PNG.
- [x] Manifest records source filename, source SHA-256, bounding boxes, output filenames and SHA-256 for each crop.
- [x] ZIP created with all 13 PNGs and manifest.
- [x] Coordinates and output dimensions recorded here for reproducibility.
- [ ] Cropped PNG binaries committed to `design-handoff/01-reference/` on GitHub. **Not yet done:** GitHub connector text-file actions cannot directly read container-generated binary bytes; do not imply the PNGs are in the repository.

## Quality caveats

This step only isolates panels from the 1536×1024 composite. Crops are **not** full-resolution screen mockups and cannot restore missing detail. Titles and panels remain as in the source. For exact token measurement, prefer future high-resolution approved originals.

## Deliverables

- 13 PNGs: `S01_Chapter_Overview.png` through `S13_Settings.png`.
- `manifest.json`: source provenance and output checksums.
- `kew_01_03_13_screen_crops.zip`: downloadable artifact in the conversation.

**Next task:** 01.04 — Assign Screen IDs (not executed here).
