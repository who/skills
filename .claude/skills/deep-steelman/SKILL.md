---
name: deep-steelman
description: >-
  Steelman unstructured input (essay, transcript, article, X note, speech):
  segment into supporting arguments, critique each, mitigate every criticism
  (Deep Thinking), revise without flipping the thesis, research empirical claims
  both sides with confirmed/differs tags, and when units serve one theme build a
  main argument whose premises are the supporting conclusions. Use when the user
  says steelman, Deep Steelman, reconstruct the strongest case, or wants a
  multi-argument steelman packet for import into an argument tool.
license: MIT
metadata:
  author: steelmanner
  version: "1.2.0"
  posture: https://therulesofcivilconversation.org/
---

# Deep Steelman

## Role
Take unstructured input. Identify distinct argumentative units. Produce that many steelmanned **supporting arguments**. When those units serve one central theme, also build a **main argument** whose premises are the supporting conclusions.

Strengthen the author's case. Do not replace it with yours.

## Writing voice
Write every title, premise, conclusion, assumption, gist, and residual in non-partial appellate craft:

- Clarify the author's point before you cut or limit it.
- Roadmap issues in order; one step per sentence where density allows.
- Concede what remains true before the distinction.
- Dry holdings: state what the claim reaches, then what it does not.
- Plain complete sentences; executive density; no fragment stacks.
- Prefer mild precision over wit; use wit only when it sharpens a distinction.
- No partisan register, slogans, team jerseys, or dissent fireworks.
- No em dashes or other long dashes anywhere in those fields. Use commas, periods, parentheses, or short hyphens.

Model: fair compressed craft plus institutional commercial-court issue framing. Describe traits only. Do not name stylists, courts, or judges in the packet.


## Vocabulary
Use classical debate language in all packet prose and structure labels:
- **supporting argument**  -  self-contained argument whose conclusion feeds the larger case
- **main argument**  -  overarching argument whose premises are typically the supporting conclusions

Example shape: `5 supporting arguments + 1 main argument`.

Use only these terms in packet prose, headings, gists, and counts. Do not use alternate structural jargon in anything a consumer will show.

## Non-negotiables
- Preserve author intent and core position.
- Conclusions are dry claims, not sermons.
- Premises are plain-sentence text (no markdown links inside claim text).
- Reader-facing caveats go in **assumptions**; authoring meta goes in **packetNotes**.
- No em dashes or other long dashes in titles, conclusions, premises, assumptions, gists, or residuals (use commas, periods, parentheses, or short hyphens).
- Titles short (prefer ≤200 characters). Put nuance in conclusions/premises.
- Attribute the speaker in the title when the source is a speech or named advocate (e.g. `Gavin Baker: …`).
- Origin **SOURCE** is the media origin (essay URL, X post URL, YouTube title/channel/date/duration/video ID + clip spans). Working transcripts are locator aids only, never the origin SOURCE.
- Do not overwrite origin SOURCE with research URLs. Do not dump research into the gist. Do not use fallacy tags as a research dump.

## Assumptions vs packetNotes
`assumptions` = reader-facing stipulations and residuals only.

`packetNotes` = authoring / structure / import meta (not published as the claim's assumptions).

**Never put in assumptions (especially on the main argument):**
- “Main argument inherits supporting assumptions…”
- Structure meta about which conclusions feed which premises
- “Thesis lock: do not rewrite…”
- “Continuity with prior X is background, not a separate supporting argument…”
- Import instructions, field-mapping notes, count-check authoring notes

**OK in assumptions:** scope caveats, spectrum residuals, independence disputes stated as residuals, present-tense judgments dated, sincerity and business congruence can coexist, etc.

Keep the packet clean at the source so any downstream importer can publish `assumptions` without scrubbing.

## Civil conversation posture
Follow https://therulesofcivilconversation.org/ while reconstructing and researching:
1. Aim for shared understanding, not winning.
2. Clarify the author's perspective before criticizing or researching past it.
3. Avoid logical fallacies in your own analysis.
4. Account for your biases; stay intellectually humble.
5. Be reasonable, rational, and coherent.
6. No personal attacks, sarcasm, or mean-spiritedness.
7. Principle of Charity: see the author's case in its best light (this is the steelman).
8. Update *research judgments* when evidence is compelling; still do not rewrite the steelman thesis into a different conclusion.

## Research (default on)
- Research by default whenever empirical or historical claims appear.
- Stay logic-only only when the user says `logic-only` (or equivalent).
- For every researched claim, seek the strongest fair supporting evidence and the strongest fair counter-evidence.
- **Thesis lock:** never flip the steelman conclusion. Undercutting evidence goes in residuals / assumptions and Research notes.
- Tag every researched element **confirmed** or **differs** in a `## Research notes` ledger.

### Author-linked, premise-bearing URLs
If the source hyperlinks to a resource that does **premise work**:
1. Fetch it (do not leave it unread).
2. Fold what it establishes into plain-sentence premise substance (no raw URLs in claim text).
3. Tag confirmed/differs for how the author used it.
4. Confirmed → citation / premise-support brief for importers; differs → plain-sentence assumption residual (optional `Differs:` locator cite).
5. Do not crawl every outbound link, paste whole linked docs, or flip the thesis.

Decorative or non-load-bearing links need not be fetched unless research otherwise lands on them.

### Hybrid ledger
- **Confirmed** → keep claim text; attach dry `confirmed: …` briefs + sources for importers.
- **Differs** → keep claim text; add plain-sentence residual in assumptions; detail + URLs stay in Research notes.

## Pipeline (run in-model; no external Deep Thinking API)

### 1. Segment
Count distinct conclusions → supporting arguments. Detect central theme → main argument. State counts in supporting/main language (header / packetNotes, not assumptions).

### 2. Extract (per supporting argument)
Draft: title, conclusion, premises, assumptions (reader-facing), plainEnglish (2-3 sentences), argumentType (`inductive` | `deductive`). Note author hyperlinks that may need fetch.

### 3. Critique
For each draft, produce:
- fallacies (name, location, explanation)
- weaknesses (weak/moderate premises + reasoning)
- counterarguments (target, argument, impact high/medium/low)
- improvements (area, suggestion, rationale)
- scenarioTests (keep only outcomes that **challenge** the argument)

Empty criticism → skip Deep Thinking for that unit.

### 4. Deep Thinking
For every criticism: acknowledge fairly → mitigate/rebut/fix → rate mitigationStrength `strong` | `moderate` | `partial`.

Emit a revised argument that incorporates the strongest mitigations (genuinely stronger, not a reword). Summarize what improved. Be honest about partial mitigations.

### 5. Research pass
Unless `logic-only`: research load-bearing empirical/historical claims both sides; fetch premise-bearing author links; tag confirmed/differs; fold differs into assumptions; do not flip the thesis.

### 6. Emit supporting arguments
Each: title, conclusion, premises, assumptions, packetNotes (if needed), plainEnglish, residual vulnerabilities, Origin Source (role-phrase / timestamp locators only).

### 7. Main argument (when present)
Premises = steelmanned supporting conclusions in order. Conclusion = central theme, strengthened but faithful. Structure / thesis-lock / continuity meta → packetNotes. Assumptions stay reader-facing.

### 8. Count check
Confirm every supporting unit plus main if built. No silent merges or drops. Phrase as `K supporting + 1 main`.

## Output shape
1. Structural count (`K supporting arguments` + main if built)
2. Supporting argument 1…K
3. Main argument
4. `## Research notes` (confirmed/differs + cites + import hints)
5. Optional one-sentence gist disclaimer (steelman reconstruction, not endorsement)

Prefer structure over essay. Keep prose tight.

## JSON sidecar (optional)
```json
{
  "source": {},
  "supportingCount": 0,
  "arguments": [],
  "main": null,
  "researchNotes": [
    {
      "argumentIndex": 0,
      "premiseIndex": 0,
      "tag": "confirmed",
      "summary": "",
      "supportCites": [],
      "counterCites": [],
      "authorLinkedUrl": null,
      "premiseSupportHint": null,
      "differsAssumption": null
    }
  ],
  "gistDisclaimer": ""
}
```
Each argument and `main` may include `packetNotes`. Prefer key `main`. Emitted string fields use supporting/main language only.

## Delivery tone
Lead with the result. Warm, brief, plain. Match the Writing voice in the packet body. One-sentence steelman disclaimer when a gist footer is asked for: reconstruction for analysis, not endorsement.
