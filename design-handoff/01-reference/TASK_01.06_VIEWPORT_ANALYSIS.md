# TASK 01.06 — Analyze Source Viewport

**Status:** DONE — source geometry analyzed; target viewport remains **UNRESOLVED** and must be approved separately.  
**Dependency:** 01.05 DONE.  
**Source of truth:** `SRC-03` (canonical 13-panel JPEG) and `SCREEN_ID_REGISTRY.csv`.

## 1. Scope and method

This task measures **the source image and extracted panel geometry**, not the native screen size of a running app. Dimensions are exact pixel counts from the supplied raster files; layout/viewport conclusions are labeled as inferences. No artwork or screen implementation is changed.

- Canonical composite: **1536 × 1024 px**, landscape, aspect ratio **3:2 (1.500)**.
- The composite is an **editorial contact sheet**, not an iPad screenshot. Its 3:2 aspect ratio must **not** be treated as the app viewport.
- Cropped panels have different aspect ratios because their widths/heights reflect collage placement. They do not establish intended iPad breakpoints.
- User's established product direction is **iPad-first, landscape**, but a specific CSS viewport / hardware device / DPR is **not approved**.
- Reference decision **D-0001** (target iPad viewport) remains unresolved; do not close it or invent owner approval.

## 2. Exact source-panel geometry

Coordinates and sizes are reproduced from `SCREEN_ID_REGISTRY.csv` and the cropped image manifest; aspect ratio = width ÷ height, rounded to 3 decimals.

| Screen | Source crop (px) | Ratio W:H | Geometry classification |
| --- | ---: | ---: | --- |
| S01 Chapter Overview | 389×473 | 0.822 | Tall collage panel |
| S02 Lesson Detail | 362×473 | 0.765 | Tall collage panel |
| S03 Quick Review | 315×473 | 0.666 | Tall collage panel |
| S04 Daily Challenge | 236×473 | 0.499 | Narrow collage panel |
| S05 Unit Complete | 224×473 | 0.474 | Narrow collage panel |
| S06 My Words | 414×367 | 1.128 | Near-square collage panel |
| S07 Achievements | 339×367 | 0.924 | Near-square collage panel |
| S08 My Stuff | 412×367 | 1.123 | Near-square collage panel |
| S09 Onboarding | 362×367 | 0.986 | Near-square collage panel |
| S10 Learning Guard | 409×173 | 2.364 | Wide strip in collage |
| S11 Offline Download | 361×173 | 2.087 | Wide strip in collage |
| S12 Progress Map | 541×173 | 3.127 | Panoramic strip in collage |
| S13 Settings | 216×173 | 1.249 | Small collage panel |

**Important:** No two panels share a universal native viewport. Their dimensions must not be scaled into fixed CSS coordinates or used to infer font sizes without further evidence.

## 3. Additional reference dimensions and layout implications

| Source | Actual raster | Observation | Viewport certainty |
| --- | --- | --- | --- |
| SRC-01 / SRC-02 (Parent Studio collages) | 1536×1024 each | Multi-panel admin UI reference | UNKNOWN |
| SRC-04 (Workshop collage) | 1536×1024 | Multiple learning activity scenes | UNKNOWN |
| SRC-05 (Story collage) | 1536×1024 | One large horizontal story composition and four smaller states | UNKNOWN |
| SRC-06 (Play hub) | 1536×1024 | A **single landscape tablet-frame composition** is shown | INFERRED landscape; CSS pixels UNKNOWN |
| SRC-07 (Play game collage) | 1536×1024 | Multiple scenes and game states | UNKNOWN |
| SRC-08 (Home World / unit flow collage) | 1536×1024 | Multiple views with different crop sizes | UNKNOWN |
| SRC-09 (detailed Progress Map) | 1448×1086 | One broad map scene; 4:3 raster ratio | INFERRED iPad-like composition; CSS pixels UNKNOWN |

**Reference priority:** SRC-03 remains canonical for S01–S13. The more detailed SRC-09 map and SRC-06 Play hub may inform composition only; do not replace S12 or other approved screens without owner decision.

## 4. Target viewport — candidates for future owner approval

The following are **test candidates**, not asserted original mockup dimensions:

| Candidate | CSS viewport | Orientation | Why consider |
| --- | --- | --- | --- |
| A | 1024 × 768 | Landscape (4:3) | Common iPad layout baseline; supports reproducible screenshot QA |
| B | 1180 × 820 | Landscape (~1.439) | Larger iPad class; checks additional horizontal space |
| C | 1366 × 1024 | Landscape (~1.334) | Large iPad class; checks density and scaling |

The product owner must select a **primary CSS viewport**, supported devices, minimum width, zoom/DPR capture convention, and whether specific screens may be portrait/modal views. This requires a decision in `DECISION_LOG.md` (D-0001), not a silent default.

## 5. Preliminary responsive / QA rules (not approved specifications)

1. Use fluid layout constraints and tokens rather than assigning collage-panel pixels as CSS dimensions.
2. Test at an approved primary iPad landscape viewport plus at least one alternate width after D-0001 is resolved.
3. Keep illustrated backgrounds separate from legible UI text and controls; do not stretch reference panels to fill the viewport.
4. Treat safe-area insets, browser chrome, display zoom, notch/home indicator, and keyboard overlays as unknown until task 01.07 and device QA.
5. Visual comparisons must state **reference type** (collage crop versus full-screen approved mockup), viewport, DPR, and render state; do not claim pixel-perfect from a low-resolution crop.

## 6. Evidence, acceptance, and handoff

- [x] Read original reference dimensions (SRC-03 and supplementary images).
- [x] Record exact crop width/height and aspect ratio for S01–S13.
- [x] Distinguish composite canvas from native app viewport.
- [x] Record landscape-first intent separately from measured pixels.
- [x] Identify unresolved target viewport decision D-0001.
- [x] Provide explicitly nonbinding QA candidates.
- [x] Record downstream dependencies without claiming owner approval.
- [x] Preserve all images unchanged.

**Result:** Source viewport analysis completed. **Decision D-0001 is still OPEN** and must be resolved before setting the authoritative Figma frame, screenshot QA viewport, or responsive acceptance criteria.

**Next task:** 01.07 — Specify safe areas (not executed).
