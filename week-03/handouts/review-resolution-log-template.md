# Review-Resolution Log Template

> **Day 5 · Activity 3 handout.** The author quad's log of what happened to every review finding: adopted, deferred, or pushed back — each with reasoning. This is the evidence of the process, and it's what the secondary reviewer honesty-checks in the afternoon.

---

## Resolution log

```markdown
## Friday review-resolution log

**Reviewers (AM):** Quad B, Quad C
**Total scores:** B = 3.1 / C = 2.8 → addressed below

### Adopted (changes made)
- B/Finding 2: Section 6 AC #4 was untestable. Rewrote with explicit observable.
- C/Finding 1: Section 7 missing Compliance NFR. Added retention + audit-trail NFRs.
- B/Finding 5: Section 9 risk "tech adoption" had no mitigation. Added optional toggle.
- (etc.)

### Deferred
- C/Finding 3: Multi-shop manager view scope. DEFERRED to Section 11 follow-up + ticket.

### Pushed back
- B/Finding 4: Reviewer suggested splitting AC #2; we declined because the
  "ands" describe one observable state. Reasoning preserved here.
```

---

## Revision protocol (reference)

1. **Sort findings by category** — adopt / defer / push back.
2. **Revise in priority order** — coherence fixes first, specificity second, prose last.
3. **Update this log** — every finding lands in one of the three buckets, with reasoning.

> A push-back without reasoning is score-defense. Force the rationale into the log. Deferred items must be tracked *somewhere* (ticket / Section 11 follow-up / Week-4 backlog).

---

## Status flip

After the revision pass, flip the PRD status:

> **In review** → **Revised — secondary pending**

Then hand off to the secondary reviewer.
