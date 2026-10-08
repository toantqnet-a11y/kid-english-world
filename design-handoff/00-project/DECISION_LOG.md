# Kids English World — Design Decision Log

**Document ID:** KEW-DL-001  
**Version:** 1.0.0  
**Status:** ACTIVE  
**Owner:** Product owner (parent)  
**Purpose:** Track every design or implementation decision that may affect fidelity to the approved mockups.

## 1. Decision policy

1. The 13 approved screen mockups are the visual source of truth. Do not silently replace layout, mascot, character artwork, icons, colors, or typography.
2. A proposal is **not** an approval. AI may document options and recommendations but must not mark a product-owner decision `APPROVED`.
3. If evidence is insufficient, use `UNKNOWN` or `NEEDS_APPROVAL`; never fabricate measurements, fonts, assets, or Figma capabilities.
4. Each decision affecting a locked design must identify affected screens, components, and assets.
5. Record the approval evidence (link, file, or explicit user instruction) before implementing a deviation.
6. Superseded decisions remain in the log; do not delete history.

## 2. Status vocabulary

| Status | Meaning |
| --- | --- |
| PROPOSED | Option raised but not evaluated |
| NEEDS_REVIEW | Options and impact ready for owner review |
| APPROVED | Explicitly approved by the authorized reviewer |
| REJECTED | Explicitly rejected |
| SUPERSEDED | Replaced by a newer decision, with reference |
| BLOCKED | Cannot decide until required evidence/input exists |

## 3. Decision record template

Copy this block for every new decision. Do not reuse an existing Decision ID.

```yaml
decision_id: D-0001
date: YYYY-MM-DD
topic: "Specific decision question"
context: "What problem must be resolved?"
source_reference: "Mockup/file/requirement reference or UNKNOWN"
options:
  - id: A
    description: "Option A"
    benefits: []
    tradeoffs: []
  - id: B
    description: "Option B"
    benefits: []
    tradeoffs: []
selected_option: null
reason: null
status: NEEDS_REVIEW
proposed_by: AI
approved_by: null
approval_date: null
approval_evidence: null
affected_screens: []
affected_components: []
affected_assets: []
implementation_tasks: []
supersedes: null
notes: ""
```

## 4. Initial decision queue

These are **unresolved** project decisions, not approved design changes.

| Decision ID | Topic | Options / next action | Status | Affected scope |
| --- | --- | --- | --- | --- |
| D-0001 | Primary iPad model and reference CSS viewport | Confirm actual iPad model, orientation, browser/PWA mode, and reference dimensions; do not infer CSS viewport from mockup pixels | NEEDS_REVIEW | S01–S13 |
| D-0002 | Canonical high-resolution mockups | Confirm 13 individual approved images or explicitly approve extracted crops from the composite | NEEDS_REVIEW | S01–S13 |
| D-0003 | Figma authoring method | Confirm authorized editable Figma workflow/tool; fallback to intermediate SVG/specs must be labeled as non-native Figma | NEEDS_REVIEW | Figma handoff |
| D-0004 | Approved original asset sources | Identify source files for tiger mascot, children, scenes and icons; reconstructed assets require comparison and approval | NEEDS_REVIEW | Assets, S01–S13 |

## 5. Change control

1. Create a decision record with context, evidence, and alternatives.
2. Identify the exact difference from the approved reference and all affected elements.
3. Set `NEEDS_REVIEW` and request explicit product-owner decision.
4. On approval, record selected option, rationale, approver, date, and evidence.
5. Link implementation task IDs and update the appropriate screen/component specification.
6. Re-run visual regression for affected screens.
7. Record a new decision if the approved choice changes later; mark the prior record `SUPERSEDED`.

## 6. Acceptance checklist for TASK 00.04

- [x] Decision ID convention defined.
- [x] Required fields: date, topic, options, selected option, reason, approved by, affected screens.
- [x] Decision statuses defined.
- [x] Approval evidence and traceability defined.
- [x] Initial unresolved decisions recorded without fabricated approvals.
- [x] Change-control process documented.

> This log documents pending choices. Its existence does not mean those choices are approved.
