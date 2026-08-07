# AI Spec Template (8 sections)

> **Day 1 handout.** The engineering-ready integrated spec you assemble from the 5-prompt sequence. It is *shorter* than the sum of its inputs — the synthesis an engineer reads first, with citations back to the deeper artifacts (PRD / TCD / TMD / SEP / DP). Every AI-drafted line must be validated against a source and logged in Section 8.

---

```markdown
# AI Spec — <feature>
**Sibling to:** PRD <link>, TCD <link>, TMD <link>, SEP <link>, DP <link>
**Authors:** <quad>  |  **Status:** Draft / Reviewed
**AI Provenance:** see end-of-doc log

## 1. Headline
One sentence: what is this feature, who is it for, what outcome does it produce?

## 2. Engineering-ready summary
3–5 paragraphs that an engineer could scope from without a clarifying call.
Synthesizes: PRD Sections 1–5, TCD Section 1, TMD Section 3.

## 3. Data + API contract
The shape an engineer needs to start coding. Synthesizes:
TMD Section 1 (data) + TMD Section 3 (API).

## 4. Sequence + failure handling
Happy / sad / weird path summary. Synthesizes: TMD Section 4.

## 5. Constraints
Performance / availability / security / compliance / accessibility.
Synthesizes: TCD Section 3 + TCD Section 4 + PRD Section 7.

## 6. Decisions made (and not made)
Top trade-offs (TCD Section 5) + open questions still requiring decision.

## 7. Stakeholders + sign-off
Who must sign off on what. From SEP Section 1 + TCD Section 6.

## 8. Provenance log
Every AI prompt + validation status.
```

---

### Section-to-source map

| Section | Synthesizes |
|---|---|
| 1. Headline | PRD Sections 1–5 |
| 2. Engineering-ready summary | PRD Sections 1–5, TCD Section 1, TMD Section 3 |
| 3. Data + API contract | TMD Section 1 + TMD Section 3 |
| 4. Sequence + failure handling | TMD Section 4 |
| 5. Constraints | TCD Section 3 + TCD Section 4 + PRD Section 7 |
| 6. Decisions made (and not made) | TCD Section 5 + open questions |
| 7. Stakeholders + sign-off | SEP Section 1 + TCD Section 6 |
| 8. Provenance log | every prompt + its validation status |

### The bar to clear
The AI drafts the spec; **your judgment shapes every section.** AI accelerates the typing, not the thinking. If an AI Spec ships without Section 8, it ships fiction.
