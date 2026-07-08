# Integration Checklist + AI-Prose Tell List

> **Day 4 · Activity 4 handout.** Read the whole PRD top-to-bottom, fix incoherences, then lock the version that goes into Friday's review. Coherence fixes first, prose fixes last. Includes the eight-item integration checklist and the AI-generic-prose tell list.

---

## The integration checklist

| Check | Pass criterion | ✓ |
|-------|----------------|:-:|
| **§1 → §2 flow** | Reader is motivated to keep reading | |
| **§3 goals tied to §8 metrics** | Each goal references a metric; each metric references a goal | |
| **§5 sketch consistent with §6 AC** | Each happy-path AC corresponds to a step in the sketch | |
| **§6 AC vs §7 NFRs** | NFRs cover what AC don't (system *properties* vs system *behavior*) | |
| **§7 NFRs reference §8 observability** | An observability NFR enables every Tier Sheet metric | |
| **§4 scope-out feeds §11 follow-ups** | Items deliberately left out appear in the follow-ups list | |
| **§9 risks named, owned, mitigated** | No "no risks" | |
| **No AI-generic prose** | Consistent triad voice; no fortune-cookie sentences | |

---

## The "no AI-generic prose" tell list

Eliminate these on sight:

- "It is important to note that…"
- "By leveraging X, we can unlock Y…"
- "This robust solution will empower stakeholders to…"
- "In today's fast-paced environment…"
- Three adjectives in a row when one would do
- Sentences that sound true but say nothing specific

> **The test:** if a section could appear in *any* PRD for *any* product, rewrite it for **your** product.

---

## Integration protocol (reference)

1. **Solo read-through** — each member reads the whole PRD top-to-bottom, marks issues in the margins.
2. **Pool issues** — de-dupe what each member caught.
3. **Fix in priority order** — coherence first, then specificity, then prose.
4. **Lock the version** — set **Status: In review**, save a copy as **"v0 — for Friday"**.

---

## Lock confirmation

- [ ] All eight integration checks pass
- [ ] No AI-generic prose remains
- [ ] Status set to **In review**
- [ ] Copy saved as **"v0 — for Friday"**
