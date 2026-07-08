# Warm-up Pack — Healthcare Scheduling

> **Day 4 · Activity 1 handout.** A small, deliberately off-domain pack — two interview transcripts and four support tickets from a clinic-scheduling SaaS — for practicing the summarize-with-evidence-tags prompt before you touch the real FieldPulse pack. Different domain on purpose: it forces the pattern to generalize.

*Fictional product: **ClinicQueue**, an appointment-scheduling and check-in app for multi-provider outpatient clinics. Names and details are invented for training.*

The pack is noisy and partly redundant — like the real thing. Your job: prompt an AI to extract the top 5 themes **with a source citation on each**, then inspect the output for invented citations, over-generalized "mush" themes, and themes you spotted that the AI missed.

---

## Interview 1 — Front-desk coordinator, 6-provider family clinic

1. "The double-bookings are what kill me. Two patients show up for the same 10:15 slot because the online booking and the phone line don't lock the slot at the same time."
2. "I spend the first hour every Monday untangling the weekend's online bookings against what the providers actually blocked off for vacation."
3. "When a provider calls out, I have to cancel and rebook by hand, one patient at a time. There's no 'move this whole day' button."
4. "Patients don't read the reminder texts. Or they get two — one from us, one from the system — and they think one is a scam."
5. "The waitlist is a sticky note on my monitor. The app has a waitlist screen but it never actually offers the open slot to anyone automatically."

## Interview 2 — Practice manager, 12-provider specialty group

1. "My no-show rate is the number the partners ask about every month. Right now I can't even pull it cleanly out of the system — I count it in a spreadsheet."
2. "The check-in kiosk is nice when it works, but half our older patients just walk past it to the desk anyway, so we staff the desk the same as before."
3. "Rescheduling is where we lose money. A canceled slot inside 24 hours almost never gets refilled, and the app doesn't help me refill it."
4. "We turned off the automated reminder calls because they were going out at 6 a.m. and patients complained. Now we get more no-shows. Pick your poison."
5. "The reporting is built for one clinic. We have three locations and I can't see them side by side without exporting each one."
6. "Honestly the scheduling engine is fine. It's the *changes* — cancellations, call-outs, walk-ins — where everything falls apart."

---

## Support tickets

**H-01 — Double-booking between online and phone.** "Online booking and the front-desk system don't lock a slot together, so we routinely get two patients for one appointment. Happens a few times a week." *(6-provider family clinic)*

**H-02 — No bulk reschedule when a provider is out.** "When a doctor calls in sick we have to cancel and rebook every appointment individually. A half-day out is an hour of my morning." *(9-provider urgent care)*

**H-03 — Duplicate appointment reminders confuse patients.** "Patients get a reminder from us and another from the app, worded differently. Several thought the second one was a phishing text and ignored both." *(12-provider specialty group)*

**H-04 — Can't pull a clean no-show rate.** "The one metric leadership asks for — no-show rate by provider — isn't in any report. I rebuild it in Excel every month." *(12-provider specialty group)*

---

### Deliverable

A **two-paragraph diagnosis** of the failure modes you observed in the AI's first pass (invented citations, theme inflation, missed themes), plus the iterated prompt that worked.
