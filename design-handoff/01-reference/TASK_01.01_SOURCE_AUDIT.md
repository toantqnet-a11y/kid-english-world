# TASK 01.01 — Count Source Mockups

**Status: DONE — inventory of user-uploaded sources completed.**  
**Scope:** Count and map uploaded references; no image edits or screen implementation.  
**Approval caveat:** SRC-03 matches the previously finalized 13-screen mockup; the eight supplementary images are inventoried as additional references, not automatically approved replacements.

## Physical source files

**9 distinct JPEG files received in this conversation.** All nine were opened for image metadata inspection and have distinct SHA-256 checksums. Original filenames, dimensions and hashes:

| ID | Uploaded filename | Pixels | SHA-256 | Content |
|---|---|---|---|---|
| SRC-01 | `F5C24538-F2AE-4293-84FC-B40E7A3F2754.jpeg` | 1536×1024 | `5d30df94d2e9c5e328405f4de2a889e5c4f803215b1f1414ed3fca811dec8a89` | Parent Studio: Game Builder, Story Builder, Vocabulary Library, Media, Preview, Progress |
| SRC-02 | `A4EF1DCE-A0EA-4AEB-A647-27A9EF89C62E.jpeg` | 1536×1024 | `9a2fa44f799c8211ffa91e6fb256ab05270eac7b7b5696a873e66292f8138203` | Parent Studio: Dashboard, Curriculum, Lesson Builder, Activity Editor, AI, Reminders |
| SRC-03 | `ED0FF5A1-F9DC-4ADB-8D9E-8B951841297B.jpeg` | 1536×1024 | `0bf3d6f78fc0933a322835022bb09e59888c05191415f252e34e21f14cfd1a8f` | Canonical 13-screen child-app overview (S01–S13) |
| SRC-04 | `B34D6AD1-97D9-4DB8-AAFE-E4A5AC73E3F6.jpeg` | 1536×1024 | `63368ba6e0efb755da6967130ba5933b18792a5d0559553e76bd72361e6c4d0c` | Workshop / activity flows (9 panels) |
| SRC-05 | `45E0AD8A-8F23-4708-A058-DCD13EA16193.jpeg` | 1536×1024 | `c243dfc63522cfafc6c9c576eef26cd55ebc4240062a956aa3df5401b2d02c5f` | Story screen + 4 scene interaction panels |
| SRC-06 | `E0EC3DA0-9A79-47D0-83B8-DC3936651EF6.jpeg` | 1536×1024 | `c29e7aa738314d64a972237d28b46a201c66715f2880bc9ae5d2d4fc22c83cab` | Play hub / game catalog |
| SRC-07 | `E8BA3952-8DDD-46C9-91B0-06F3116B94B4.jpeg` | 1536×1024 | `56473a1bdf43c6a5a471eee642244dd30197408cf4f4a593954c4550cf6b7a3c` | Play mini-game flow (9 panels) |
| SRC-08 | `730CD809-F941-4CAF-8405-985BC01CB852.jpeg` | 1536×1024 | `210dcdcae877d0c618786643948853ea2d5be1d6b7780f673a9de7e9a9d2152a` | Home World, Unit Map, lesson/game/story flow (13 panels) |
| SRC-09 | `EAD8AE44-45C2-4FA2-8FA3-3732456EB9AC.jpeg` | 1448×1086 | `1d093ef089bf84ec52656724430e4f17e5d9a8f58f2e8e6fa1b3e656ff4c7591` | Detailed Unit 1 School Time progress map |

## Canonical 13-screen child mockup mapping

**SRC-03** is one composite JPEG containing all 13 labeled child screens. The 13 screens are **panels, not 13 separate uploaded image files**.

| Screen ID | Approved screen name | Source image |
|---|---|---|
| S01 | Chapter Overview | SRC-03 (panel 1) |
| S02 | Lesson Detail | SRC-03 (panel 2) |
| S03 | Quick Review | SRC-03 (panel 3) |
| S04 | Daily Challenge | SRC-03 (panel 4) |
| S05 | Unit Complete | SRC-03 (panel 5) |
| S06 | My Words | SRC-03 (panel 6) |
| S07 | Achievements | SRC-03 (panel 7) |
| S08 | My Stuff | SRC-03 (panel 8) |
| S09 | Onboarding | SRC-03 (panel 9) |
| S10 | Learning Guard | SRC-03 (panel 10) |
| S11 | Offline Download | SRC-03 (panel 11) |
| S12 | Progress Map | SRC-03 (panel 12) |
| S13 | Settings | SRC-03 (panel 13) |

Additional visual references: SRC-04 workshop/activity, SRC-05 story, SRC-06/SRC-07 play, SRC-08 home-world/learning flow, SRC-09 detailed progress map, SRC-01/SRC-02 parent studio. These are not replacements for SRC-03 without owner approval.

## Inventory result

- **9** original composite JPEG uploads received.
- **1** composite image (SRC-03) contains the canonical **13/13** named child-screen panels.
- **8** additional reference images received.
- **0** individual screen image files uploaded as separate files; splitting/cropping is a future task.
- **0** image assets currently committed under `design-handoff/01-reference/` at the time of this audit.
- **0** duplicate byte-identical images among the nine uploads (distinct SHA-256).
- **No claim** that uploaded images have been committed to GitHub: this Markdown report is the repository evidence; the image bytes remain conversation attachments until a separate upload/asset task.

## Verification and limitations

1. All nine files were available in the current conversation's mounted file set.
2. Dimensions and SHA-256 were computed from the original uploaded bytes.
3. Panels were identified by reading their visible screen headings.
4. SHA-256 identifies these uploaded JPEGs, not earlier historical image variants.
5. Exact crop coordinates, reference baseline version, owner approval of supplementary images, and GitHub binary storage remain for subsequent tasks.

## Acceptance — 01.01

- [x] Count uploaded physical mockup files.
- [x] Identify canonical composite and all 13 screen names.
- [x] Distinguish supplementary references from canonical screens.
- [x] Record original filenames, dimensions, and SHA-256 checksums.
- [x] Note limitations and outstanding future work without inventing approval.
- [x] Persist audit in GitHub and update Task Register.

**Next task:** 01.02 (not executed here).
