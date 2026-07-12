# FieldPulse Research Pack — Voice-of-Customer Slack Export

> **Day 4 · Research Pack (5 of 6).** An export of ~33 messages from FieldPulse's internal `#voice-of-customer` channel, where CS, sales, and support relay what they hear from customers. This is second-hand, unstructured, and contradictory — a mix of **Reported** (a customer said) and **Inferred** (an employee's read). Cite by channel + date. Do not treat a colleague's opinion as a customer fact.

*Anonymized: employee names replaced with roles; customer/shop identifiers removed. Threading flattened to a running log. Fictional, for training.*

---

`#voice-of-customer` — export

**2025-09-08**
- **[CS-1]** Kicking off the week. Three separate reconcile complaints over the weekend, all from shops over 100 techs. Pattern or coincidence?
- **[Support-2]** Not coincidence. Reconcile is our #1 ticket driver this month by volume. Mostly "too many steps" and "crashed and I lost it."
- **[CS-3]** The 90-tech HVAC account (the one with the paper notebook lady) escalated again — app froze mid-reconcile three nights. She's keeping paper "just in case" now. That's a churn tell.
- **[Sales-1]** Losing a deal partly on this too — prospect demoed the reconcile flow and said "my dispatcher would never finish that."

**2025-09-09**
- **[Support-2]** The offline thing keeps coming up. Techs in basements/crawlspaces can't submit, so they hand paper to the dispatcher who retypes at night. That's *creating* the reconcile pile.
- **[CS-1]** So reconcile pain is partly downstream of field-capture failure. Worth saying out loud.
- **[Eng-liaison]** Careful — we don't actually have data on how often submits fail offline. It's plausible but it's anecdote right now.
- **[CS-3]** Fair. Reported, not measured.

**2025-09-10**
- **[Sales-1]** Competitive note: two prospects this week compared us to ServiceTitan and said we're "lighter, faster to start." That's the good version of the story.
- **[Sales-1]** The bad version: one of them then asked about "completed vs billed" reporting and we don't have it cleanly. They shortlisted ServiceTitan for that.
- **[CS-1]** The "completed vs billed" gap comes up from owners specifically, not dispatchers. Different persona, same report.

**2025-09-11**
- **[Support-2]** New-dispatcher onboarding: another account says new hires stall at the same setup screen. This is the third account this quarter naming the setup flow.
- **[CS-3]** The 160-tech account trains every new dispatcher by hand because of that screen. She's stopped filing tickets about it — just works around it. (So it's underreported in ticket volume.)
- **[Design-liaison]** Noting that. Underreported ≠ low severity. People stop reporting the things they've given up on.

**2025-09-12**
- **[CS-1]** Long thread from the 160-tech account worth capturing. Her real deadline is **Wednesday payroll**, not the Friday owner report. Jobs not reconciled by Wed don't make the pay/bill cycle.
- **[CS-1]** Quote: "If this told me Wednesday morning what I find out Friday, I'd get two days back." That's a North-Star-shaped sentence if I ever heard one.
- **[Sales-1]** +1. Every shop has a version of that cutoff. It's not always Wednesday but there's always a wall.
- **[Support-2]** So the pain isn't "reconcile is slow" in the abstract — it's "reconcile isn't done before the money cutoff." Sharper.

**2025-09-15**
- **[CS-3]** Mid-day re-route complaints from the 75-tech electrical account again. Board lags the reassign so the dispatcher calls to confirm — does it twice.
- **[Support-2]** Same shape as the notification-latency tickets from the tech app. Might be one underlying sync issue wearing two costumes.
- **[Eng-liaison]** Might be. Or might be two things. Don't collapse them until we've looked.

**2025-09-16**
- **[Sales-1]** Housecall Pro came up in a loss review. Smaller prospect chose them for "set up in minutes, no training." Our onboarding lost us that one.
- **[CS-1]** Interesting — onboarding costs us at the *small* end (vs Housecall) and reporting costs us at the *large* end (vs ServiceTitan). Squeezed in the middle.

**2025-09-17**
- **[Support-2]** Dark mode request again. Third this quarter. Low sev, but people keep asking.
- **[CS-3]** Filing it, not prioritizing it. Please don't let this become the thing we build because it's easy.
- **[Design-liaison]** Agreed. The easy-but-irrelevant trap.

**2025-09-18**
- **[CS-1]** Accounting-integration requests keep trickling in. Owners want to stop re-entering invoices.
- **[Sales-1]** It's a retention ask more than an acquisition ask — nobody's picked us *because* of it, but a couple renewed partly hoping for it.
- **[Eng-liaison]** Big lift though. Let's not promise it in a deck.

**2025-09-19**
- **[CS-3]** Wrapping the week: if I had to name the one thing, it's close-out. Every persona touches it — dispatcher (too slow), owner (revenue leaks), tech (can't submit from the field). Different words, same wound.
- **[Support-2]** Second that. Reconcile/close-out is the throughline.
- **[CS-1]** Counter-take, gently: is close-out the problem, or is close-out the *symptom* of the field-capture and sync problems upstream? Genuinely unsure. Flagging for whoever picks this up.
- **[Design-liaison]** That's exactly the question a strategy brief should answer instead of assume. 👏

---

### Reading note

The channel doesn't agree with itself — is close-out the root problem or a downstream symptom? Is the sync/latency issue one bug or two? Is onboarding low-severity because tickets are low, or underreported because people gave up? Those unresolved tensions are yours to synthesize, not the AI's to paper over.
