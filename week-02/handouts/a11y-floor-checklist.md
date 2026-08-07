# A11y Floor Checklist

> **Day 3 · Activity 2 handout.** The non-negotiable accessibility floor — the small set of checks a TPM runs before *any* PRD ships. Rate each pass / partial / fail on your chosen surface, and cross-link a UX heuristic for every fail.

## The 8 checks

| # | Check | Tool | What "fail" looks like | Result |
|---|-------|------|------------------------|--------|
| 1 | All interactive elements keyboard-focusable | Tab through the page | Focus disappears or skips elements | |
| 2 | Visible focus indicator | Tab through the page | No outline or visible state when focused | |
| 3 | Color contrast 4.5:1 (text), 3:1 (large text) | Browser devtools / WebAIM | Light gray on white, blue-on-blue | |
| 4 | Form fields have associated labels | Screen reader / inspect | "Edit text, blank" announced | |
| 5 | Images have alt text | View source | `<img alt="">` on meaningful images | |
| 6 | Page has a logical heading hierarchy | Outline tool | Jumps from `<h1>` to `<h4>` | |
| 7 | Error messages identify the field | Submit a broken form | "Error" with no field reference | |
| 8 | Touch targets ≥ 44px on mobile | DevTools mobile view | Buttons too small to tap reliably | |

---

## How to run it (quad protocol)

1. Open the FieldPulse mobile app (or your chosen surface) on each member's device.
2. Split the checks so all 8 are covered, plus one overlap — each member runs 3 of the 8.
3. Pool findings. For each fail, identify which UX heuristic is *also* being violated.
4. Output a one-page A11y Floor Audit: each check rated pass / partial / fail, heuristic cross-link on every fail.

## Why TPMs care

Accessibility is a regulatory floor (ADA / Section 508 / EAA), an SEO floor, and a usability ceiling — fixes for keyboard focus often fix mouse-user errors too. This is the kind of artifact TPMs are expected to surface unsolicited.
