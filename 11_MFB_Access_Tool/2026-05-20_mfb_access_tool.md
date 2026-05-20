# [Rehab Tool] ARC-EX Candidacy Screener — Week 21

**Date:** 2026-05-20  
**ISO Week:** 21  
**Topic Index:** 9 of 12 (index 8, 0-based)  
**Tool:** ARC-EX Transcutaneous Spinal Cord Stimulation — Upper Extremity Candidacy Screener  
**Delivery:** Weekly MFB Rehab Tool Build · Jon VandenBerg

---

## Problem Statement

Clinicians at Mary Free Bed encounter cervical SCI patients across multiple care settings — acute hospital, inpatient rehab, outpatient — who may be candidates for ARC-EX transcutaneous spinal cord stimulation (tSCS) therapy targeting upper extremity motor recovery. Without a structured screening tool, candidacy decisions are inconsistent, referral timing is delayed, and eligible patients may be missed or evaluated without full documentation of criteria. This screener provides a fast, structured, evidence-aligned workflow that ends in an Epic-ready documentation block.

---

## Tool Design

| Field | Detail |
|---|---|
| **Target User** | Physiatrists, APPs, SCI coordinators, inpatient rehab team |
| **Use Context** | Bedside, team conference, outpatient intake, phone triage |
| **Inputs** | Injury level, AIS class, time post-injury, age, UEMS bracket, care setting, inclusion criteria (8 items), exclusion criteria (10 items, 5 absolute + 5 relative), contextual factors (caregiver, transport, goals, prior stim) |
| **Logic** | Hard exclusions → NOT a candidate; missing core inclusions → NOT a candidate; subacute timing / soft exclusions / contextual risks → CONDITIONAL; all core criteria met, no exclusions → CANDIDATE |
| **Output** | Three-tier verdict (Yes / Conditional / No) + rationale list + prioritized next steps + Epic SmartPhrase block |
| **Downstream Action** | Physician documents via Copy → paste into Epic note; refers to ARC-EX coordinator if candidate |

---

## Epic SmartPhrase Pairing

Suggested SmartPhrase name: `.MFBARCEX`

Paste the copied output directly into an H&P, Rehab Progress Note, or SCI Consult note. The output block includes:
- Injury profile summary
- Inclusion criteria met
- Exclusion criteria present (or none identified)
- Review flags
- Three-tier candidacy determination
- Numbered next-step action list
- Contextual support factors

---

## Testing Checklist

- [ ] Select T1+ injury level → verdict = NOT a candidate, reason includes thoracic SCI
- [ ] Select pacemaker exclusion alone → verdict = NOT a candidate
- [ ] Check all 8 inclusion criteria, select C5-C6 / AIS C / >12 months / age adult, no exclusions → verdict = CANDIDATE
- [ ] Select 6–12 months post-injury but do NOT check the "≥ 6 months" inclusion box → verdict = CONDITIONAL
- [ ] Select uncontrolled AD (relative exclusion) with otherwise clean profile → verdict = CONDITIONAL
- [ ] Select age = minor → verdict = NOT a candidate
- [ ] Select acute (<1 month) post-injury → verdict = NOT a candidate
- [ ] Click "Copy as Epic SmartPhrase" → text copies to clipboard, toast appears and fades
- [ ] Click Reset → all fields clear, results panel hides, scrolls to top
- [ ] Resize to 375px width → form grid collapses to single column, readable
- [ ] Print preview → PHI banner visible at top, buttons hidden, results show fully

---

## Next Iteration Ideas

1. **GRASSP integration** — add a mini GRASSP score calculator sub-panel so baseline data populates the SmartPhrase automatically
2. **Stimulation site skin map** — visual diagram showing posterior cervical, thoracic, and dorsal hand electrode zones with contraindication overlay
3. **Subacute protocol branch** — separate criteria pathway for 1–6 month patients enrolled in emerging early-intervention tSCS trials
4. **Re-screen timer** — flag date for reassessment based on selected barrier type (e.g., "Re-screen in 8 weeks after wound closure")
5. **Batch export** — allow team conference use with tabular output of multiple patients screened in one session (no PHI mode)
6. **ARC-EX vs. Halo tSCS comparison** — split-panel for programs offering multiple tSCS device options

---

## Standalone Tool HTML

> Full working HTML is attached as `2026-05-20_arcex-candidacy.html`
> Single file · No external dependencies · MFB navy/gold · Mobile + print responsive

```
[See attached HTML file: 2026-05-20_arcex-candidacy.html]
```

---

*MFB Rehab Tool Builder — automated weekly delivery*  
*Archive: `11_MFB_Access_Tool/2026-05-20_mfb_access_tool.md`*
