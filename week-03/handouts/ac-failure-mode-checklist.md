# Acceptance Criteria — Failure-Mode Checklist

> **Day 2 handout.** The mental model for writing and triaging Acceptance Criteria: what an AC is, the 5 failure modes to check every AC against, and the happy / sad / weird coverage shape. Run every AC you write through the 5-failure list.

---

## What an AC is (and isn't)

An AC is a **testable assertion** about the system's behavior in a specific situation:

```
Given <a precondition / starting state>
When  <an action or event happens>
Then  <an observable, falsifiable result>
```

| Is | Is not |
|----|--------|
| Testable (you can write a test that passes/fails) | "The system should be intuitive" |
| Specific to one behavior | "The system handles errors well" |
| Implementation-agnostic | "Use Redis to cache the response" |
| Falsifiable (you can prove it wrong) | "Performance should be good" |

---

## The 5 AC failure modes

Check every AC against all five. A good AC fails **none** of them.

| # | Failure | What it looks like | Fix |
|---|---------|--------------------|-----|
| 1 | **Vague** ("intuitive", "fast", "easy") | "Then the user has a good experience" | Replace with a measurable outcome |
| 2 | **Untestable** (no observable result) | "Then the user feels confident" | Anchor to a system-visible action or state |
| 3 | **Restating the goal** | "Then dispatchers reconcile faster" | Pin to a specific in-system event, not a metric |
| 4 | **Multi-condition (AND-soup)** | "Then X and Y and Z and W happen" | Split into multiple ACs |
| 5 | **Implementation-prescriptive** | "Then a Redis cache hit returns…" | Describe behavior, not implementation |

> The trickiest is **#3, Restating the goal**. Ask: *could this be tested without running an A/B against the metric?* If not, it's restating the goal.

---

## Coverage shape — happy / sad / weird

A complete AC section covers three scenario categories. Aim for **8–12 AC total** with this shape:

| Path | Question | Typical count |
|------|----------|:---:|
| **Happy** | What does success look like end-to-end? | 3–5 |
| **Sad** | What happens when the user does the wrong thing or input is invalid? | 2–4 |
| **Weird** | Network drops, partial data, race conditions, edge cases the user wouldn't think of? | 2–4 |

The **weird path** is where TPMs earn their seat. PMs who don't think technically miss it; engineers who don't think about users miss it differently.

---

## Quick pass/fail sheet

| AC # | Path (H/S/W) | ①Vague | ②Untestable | ③Restates goal | ④AND-soup | ⑤Impl-prescriptive | Clean? |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 1 | | | | | | | |
| 2 | | | | | | | |
| 3 | | | | | | | |
