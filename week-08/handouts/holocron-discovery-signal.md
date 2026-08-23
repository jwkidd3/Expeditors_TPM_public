# Holocron — Discovery Signal Pack

> **Day 2 handout.** The customer signal gathered for the Holocron project — interview notes, support-ticket patterns, observations, and indirect signal — pooled for your discovery. Use it in **Activity 1 (Compressed Customer Discovery)** to ground your persona, name the top pains, and trace the journey friction. This is a **starting set**: it is real signal on record, but it is not complete — validate and extend it with the stakeholders named in the problem brief. Do not invent beyond what's here or what you confirm firsthand.

---

## Direct customer signal

Interviews, support tickets, observation, and usage data — organized by role.

### Content Owner — owns the UI text, blocked behind engineering today
- *"A one-word fix to a legal disclaimer is a ticket, an engineering sprint slot, a review, and a release. It's live two weeks later."*
- *"When Legal asks me 'who approved this, and when?', I'm digging through old email — there's no record I can point to."*
- **Observation:** content teams keep a running "text changes waiting on engineering" list; some items have sat more than 30 days.
- **Ticket pattern:** recurring weekly "please update the copy on screen X" requests — none of them require technical judgment.

### Engineer (consuming application) — integrates the rendered text, wants to stop hardcoding
- *"Every app hardcodes its own strings. When a standard changes, we retrofit dozens of apps by hand."*
- *"I get pulled off feature work to change a button label — it's the lowest-value interrupt I have."*
- *"There's no shared way to fetch strings, so each team reinvents string loading."*

### Legal / Compliance reviewer — must approve compliance-sensitive text
- *"Strings ship without us seeing them. We find out a disclaimer is wrong after it's already in production."*
- *"Approval evidence is scattered across email and chat — I can't produce a durable, centralized record for an audit."*
- **Data point:** several past releases with legally sensitive wording had no recorded review gate.

### Translator / vendor — produces locale content through file exchange
- *"There's no single source of truth, so the same term gets translated three different ways across products."*
- *"We work off exchange files; when the source string changes after we start, we end up translating text that's already stale."*

### Architecture / Review Administrator — governance and routing
- *"Without key and namespace governance, changing a shared string cascades in ways nobody predicts."*
- *"Review requests land on a generic admin inbox — there's no way to route them to the right authorized reviewer."*

## Indirect signal

Public/observed signal, internal chatter, and patterns.

- **Internal Slack:** recurring threads — *"who owns this string?"* and *"can someone push a copy change for me?"*
- **Improvised tooling:** teams have worked around the gap with spreadsheets, per-app text files, and one-off admin scripts — a clear sign of unmet demand.
- **Compounding debt:** every new application still ships with hardcoded strings, so the future retrofit burden keeps growing.

## What's missing — confirm with stakeholders

These are genuinely open. Name them; don't paper over them. (They mirror the open questions in the problem brief.)

- How fast a published change must reach consuming applications (propagation target).
- The peak demand the delivery mechanism must sustain.
- Whether — and how — right-to-left (RTL) languages are in scope for this version.
- How shared/reused terminology is governed across products (the master-data / reference-data operating model).
- How success and value will be measured for the governance and rollback capabilities.

---

## How to use this in Activity 1

1. **Pool** these into your Day-2 buckets: **Direct signal**, **Indirect signal**, **What's missing** — adding anything you confirm firsthand with the real stakeholders.
2. **Name the persona** — the one role whose pain anchors your release (start from the Content Owner unless your evidence points elsewhere).
3. **Rank the top 3 pains** (severity × frequency × addressability) and trace the **journey friction** — where the current process breaks down.
4. Carry the result into your **discovery summary**, which feeds PRD-light Sections 1–2.

**The rule still holds:** ground every claim in this signal or in a source you confirm — do not invent customer signal.
