# AI Pattern-Detection Prompt

> **Day 3 · Activity 4 handout.** A reusable prompt that scans a sprint's work for the three patterns most worth catching. Run it weekly or per sprint review — then validate.

The pattern: AI reads a sprint's ADO output plus leading-indicator readings and flags where the numbers are drifting the wrong way, where a category of work is over- or under-represented, and any anomaly worth investigating.

## The prompt

```
Role: Senior PM doing pattern detection across a sprint's work.
Context: <ADO query results — items shipped, items blocked,
         leading indicator readings>
Task: Identify the top 3 patterns:
  1. A leading indicator moving the wrong direction (or flat
     when expected to move)
  2. A category of work over- or under-represented in this sprint
  3. An anomaly worth investigating (specific stories /
     timing / volume)
Constraints:
  - Use only the data provided
  - For each pattern, name the specific items / numbers
  - Suggest one investigation step per pattern
Format: 3 numbered patterns; each with: pattern / evidence / suggested investigation.
```

---

## Validation discipline

**Cross-check every claim against the actual ADO query results.** A pattern the AI names but the data doesn't support gets dropped. The value is the specific "go look at this" — not the prose.
