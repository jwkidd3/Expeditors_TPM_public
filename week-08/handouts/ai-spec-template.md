# AI Spec Template (8 sections)

> **Day 1 handout.** The engineering-ready integrated spec you assemble from the 5-prompt sequence. It is *shorter* than the sum of its inputs — the synthesis an engineer reads first, with citations back to the deeper artifacts (PRD / TCD / TMD / SEP / DP). Every AI-drafted line must be validated against a source and logged in §8.

---

```markdown
# AI Spec — <feature>
**Sibling to:** PRD <link>, TCD <link>, TMD <link>, SEP <link>, DP <link>
**Authors:** <triad>  |  **Status:** Draft / Reviewed
**AI Provenance:** see end-of-doc log

## 1. Headline
One sentence: what is this feature, who is it for, what outcome does it produce?

## 2. Engineering-ready summary
3–5 paragraphs that an engineer could scope from without a clarifying call.
Synthesizes: PRD §§1–5, TCD §1, TMD §3.

## 3. Data + API contract
The shape an engineer needs to start coding. Synthesizes:
TMD §1 (data) + TMD §3 (API).

## 4. Sequence + failure handling
Happy / sad / weird path summary. Synthesizes: TMD §4.

## 5. Constraints
Performance / availability / security / compliance / accessibility.
Synthesizes: TCD §3 + TCD §4 + PRD §7.

## 6. Decisions made (and not made)
Top trade-offs (TCD §5) + open questions still requiring decision.

## 7. Stakeholders + sign-off
Who must sign off on what. From SEP §1 + TCD §6.

## 8. Provenance log
Every AI prompt + validation status.
```

---

### Section-to-source map

| Section | Synthesizes |
|---|---|
| 1. Headline | PRD §§1–5 |
| 2. Engineering-ready summary | PRD §§1–5, TCD §1, TMD §3 |
| 3. Data + API contract | TMD §1 + TMD §3 |
| 4. Sequence + failure handling | TMD §4 |
| 5. Constraints | TCD §3 + TCD §4 + PRD §7 |
| 6. Decisions made (and not made) | TCD §5 + open questions |
| 7. Stakeholders + sign-off | SEP §1 + TCD §6 |
| 8. Provenance log | every prompt + its validation status |

### The bar to clear
The AI drafts the spec; **your judgment shapes every section.** AI accelerates the typing, not the thinking. If an AI Spec ships without §8, it ships fiction.
