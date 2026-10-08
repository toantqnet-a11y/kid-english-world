# TASK 01.07 — Specify Safe Areas

**Status:** DONE — provisional engineering specification documented; device-specific values remain pending owner approval and hardware QA.  
**Depends on:** 01.06. **Applies to:** S01–S13, iPad-first landscape PWA.

## 1. Source and confidence

The approved SRC-03 collage does **not** show native iPad system bars or reveal browser versus standalone PWA mode. Therefore **no exact physical top/bottom inset can be measured from the mockup**. The primary CSS viewport decision D-0001 remains `NEEDS_REVIEW`.

| Requirement | Value | Confidence |
| --- | --- | --- |
| App orientation target | Landscape-first | Product requirement |
| Actual iPad model, browser/PWA display mode | UNKNOWN | Pending owner |
| Native safe-area inset top/right/bottom/left | Runtime `env(safe-area-inset-*)` | Runtime, not hardcoded |
| Primary reference viewport | UNKNOWN | D-0001 open |
| Internal content gutter | 24 CSS px proposed | PROPOSED, not mockup-measured |
| Compact fallback gutter | 16 CSS px proposed | PROPOSED |
| Minimum interactive target | 44×44 CSS px proposed | Engineering accessibility baseline, not measured |
| Floating navigation bottom spacing | Safe-area inset + proposed 16 CSS px | PROPOSED |
| Full-bleed illustrated backgrounds | May extend edge-to-edge | Allowed only if content remains safe |

**Do not claim** that 24px/16px or 44px values were extracted from the design. They are implementation candidates for owner review.

## 2. Safe-area zones

1. **System zone** — device cutouts, home indicator, status/UI overlays; use browser-reported `env()` values when available.
2. **Content zone** — essential text, cards, navigation, primary buttons, progress indicators, and tappable controls stay within both the system zone and internal content gutter.
3. **Decorative bleed zone** — noninteractive illustrations, scenery and backgrounds may extend to the physical viewport edge; keep key character faces, labels and instructional elements inside content zone.
4. **Overlay zone** — dialogs, learning guard reminders, offline prompts and bottom sheets must account for safe-area insets, dynamic viewport changes and keyboard.
5. **Scroll zone** — scrolling content must have enough bottom padding to clear persistent navigation and the system bottom inset; do not hide final action buttons behind a home indicator.

## 3. CSS contract (provisional, implementation-ready)

Include viewport metadata in the application HTML head (verify with device tests):

```html
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover" />
```

Proposed CSS variables and usage:

```css
:root {
  --safe-top: env(safe-area-inset-top, 0px);
  --safe-right: env(safe-area-inset-right, 0px);
  --safe-bottom: env(safe-area-inset-bottom, 0px);
  --safe-left: env(safe-area-inset-left, 0px);
  --content-gutter: 24px; /* PROPOSED — owner review */
  --bottom-ui-gap: 16px; /* PROPOSED — owner review */
  --nav-height: 72px; /* PLACEHOLDER — not mockup-derived */
}
.app-shell {
  min-height: 100vh;
  min-height: 100dvh;
  padding:
    calc(var(--safe-top) + var(--content-gutter))
    calc(var(--safe-right) + var(--content-gutter))
    calc(var(--safe-bottom) + var(--content-gutter))
    calc(var(--safe-left) + var(--content-gutter));
}
.full-bleed-scene {
  position: absolute;
  inset: 0;
  pointer-events: none;
}
.floating-bottom-nav {
  position: fixed;
  left: calc(var(--safe-left) + var(--content-gutter));
  right: calc(var(--safe-right) + var(--content-gutter));
  bottom: calc(var(--safe-bottom) + var(--bottom-ui-gap));
}
.scroll-content.with-bottom-nav {
  padding-bottom: calc(var(--nav-height) + var(--bottom-ui-gap) + var(--safe-bottom) + 24px);
}
@media (max-width: 700px) {
  :root { --content-gutter: 16px; }
}
```

**Integration caution:** Do not apply shell padding and child-level inset padding twice. The code above illustrates the contract, **not a committed application change**. `env()` can resolve to 0 on browsers/devices without inset exposure. `100dvh` should be checked against Safari toolbar expansion/collapse. Avoid global `overflow: hidden` when keyboard or short landscape height requires scrolling.

## 4. Screen-specific considerations

| Screens | Risk | Proposed handling |
| --- | --- | --- |
| S01–S05 lessons, reviews and completion | CTA/footer hidden behind navigation or bottom inset | Keep CTA inside scroll-safe region; ensure scroll end is reachable |
| S06–S08 Words, Achievements, My Stuff | Grid/card edges clipped at corners or under system UI | Respect left/right insets and content gutters |
| S09 Onboarding | Selection/continue action obstructed | Center within safe content zone; permit vertical scroll |
| S10 Learning Guard | Modal close/acknowledge controls near unsafe edges | Position modal inside safe region; focus management |
| S11 Offline Download | Bottom action or progress text obstructed | Keep progress and download CTA clear of insets |
| S12 Progress Map | Map art may bleed; labels/nodes must remain tappable | Separate decorative map layer from safe interactive overlay |
| S13 Settings | Long settings list or toggles clipped | Scroll with bottom padding and keyboard-aware focus |

## 5. QA acceptance criteria (for later implementation)

- [ ] Capture landscape screenshots on the **owner-approved** primary iPad device and one alternate viewport.
- [ ] Test both Safari tab and installed standalone PWA if both are supported.
- [ ] Log `window.innerWidth`, `window.innerHeight`, `visualViewport` dimensions and CSS safe-area inset readings in each mode.
- [ ] Test all four edges with actual device inset behavior; **never assume fixed top/bottom numbers**.
- [ ] No essential text, navigation, controls, progress labels or mascot instructional cues overlap system bars/home indicator.
- [ ] Every primary CTA is visible or scroll-reachable; test bottom sheets and long settings content.
- [ ] Test virtual keyboard open/close and rotation; do not rely on only a static screenshot.
- [ ] Validate minimum touch target and spacing on real hardware.
- [ ] Verify backgrounds can bleed without moving interactive elements into unsafe regions.
- [ ] Record evidence screenshots per S01–S13 and log deviations.

These QA checks are **not yet executed**; this task delivers a written specification, not a running PWA test.

## 6. Open decisions and handoff

- **D-0001 OPEN:** owner to confirm device model, CSS viewport, orientation policy, browser vs standalone mode, zoom and DPR capture convention.
- Proposed content gutters, nav height, and target sizes require confirmation or adjustment during screen/component design.
- Safe-area values are runtime-derived; do not hardcode 20px/34px/other iPhone-style insets for iPad.
- **Task 01.08** may lock the *reference evidence* and unresolved flags; it must not pretend that D-0001 has been approved.

**Result:** TASK 01.07 specification authored. **No code or images were modified.**
