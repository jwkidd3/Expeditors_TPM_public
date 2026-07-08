# Standup-Prep AI Prompt

> **Day 2 · Activity 4 handout.** A reusable prompt that turns yesterday's ADO activity into a 5-bullet standup summary. AI is a standup *aid* — it does not replace the team.

The pattern: AI summarizes the past day's ADO activity, surfaces anomalies, and drafts the "what's blocking us" framing. You paste the raw query results; it produces the bullets.

## The prompt

```
Role: Standup-prep assistant for a TPM.
Context: <paste yesterday's ADO query results — items moved
         state, items added, items closed, comments added>
Task: Produce a 5-bullet standup summary:
  1. Top 2 things shipped
  2. Top 2 things blocked or stuck (>2 days no movement)
  3. 1 anomaly (pattern that's unusual for this team)
Constraints:
  - Only use information in the provided data
  - Flag anything you can't determine
Format: 5 numbered bullets. Each bullet under 15 words.
```

---

## Validation discipline

Same as Week 5 Day 5: **cross-check the AI's claims against the actual ADO data** before you take them into standup. If the AI asserts something the query results don't support, drop it. If it flags something it "can't determine," that's a real gap — go find the answer, don't paper over it.
