# DaycareConnect Ontario

**A two-sided platform concept for childcare discovery, waitlist transparency, and enrollment in Ontario.**

🔗 **Live prototype:** [https://m3dya.github.io/DaycareConnect](https://m3dya.github.io/DaycareConnect)

> A service design project exploring how to make childcare waitlists honest for parents and manageable for providers — without taking allocation control away from the people who run the centres. Built to the **Ontario Design System** and to **AODA / WCAG 2.1 AA** accessibility standards.

---

## The problem

Finding licensed childcare in Ontario is a maze. Parents apply to centre after centre with no idea where they actually stand, while the same families clog provider waitlists long after they've found care elsewhere. The pain concentrates in one phase:

- **Opaque waitlists** — parents wait months in an information blackout, never knowing if they're next or nowhere close.
- **Fragmented discovery** — licensed centres, licensed home daycares, and legal home care live in separate, hard-to-compare silos.
- **Administrative burden** — providers lose hours to outdated lists, families who've aged out, and chasing confirmations.
- **A confusing entry point** — first-time parents don't know what CWELCC is, or what "licensed" even means, before they can begin.

The waitlist phase is the core opportunity: maximum stress for parents, maximum wasted effort for providers.

---

## Approach

This project follows the **Double Diamond** methodology, spanning Discover → Define → Develop:

**Discover & Define** — Surveys, interviews, and synthesis with parents and a licensed provider produced parent and provider journey maps, an NNg-format service blueprint, five parent personas (including *The Lost Beginner*), a provider persona, and a future-state journey map.

**Develop** — Ideation across seven *How Might We* statements (44 ideas), a Feature × Value × Difficulty prioritization, and the interactive wireframe prototype in this repository.

> ⚠️ **Research caveat:** Provider insight currently rests on a single in-depth response (a licensed centre, n=1). Provider-side claims are directional and flagged accordingly. Parent-side findings draw on a wider sample.

---

## Core design principles

These came directly out of research and govern every screen.

| Principle | What it means in the design |
|---|---|
| **Provider control is non-negotiable** | The platform surfaces and organizes; it never auto-allocates. Providers always decide who gets a spot. |
| **Honesty over false precision** | Parents see *group-level standing* ("first third · 18 families in range"), not a fake "#7 in queue" — because the real rules differ at every centre. |
| **Reflection over volume** | The system reflects a parent's stated priorities back to them rather than burying them in more options. |
| **Operational truth over star ratings** | Real signals — openings, daily outdoor time, licensed capacity, CWELCC status — replace vanity ratings. |
| **Zero-assumption onboarding** | Nothing assumes the parent already knows CWELCC, licensing types, or how seasonal intake works. |

---

## Design system & accessibility

This is a public-service concept, so it is built to the standards a real Ontario government product would have to meet.

### Ontario Design System (ODS)

The prototype links the **official compiled ODS theme and fonts** directly from Ontario's CDN, rather than imitating the look:

```html
<link rel="stylesheet" href="https://unpkg.com/@ongov/ontario-design-system-global-styles@latest/dist/styles/css/compiled/ontario-theme.css">
<link rel="stylesheet" href="https://unpkg.com/@ongov/ontario-design-system-global-styles@latest/dist/misc/ontario-design-system-fonts.css">
```

- **Type:** Raleway (modified) for headings, Open Sans for body — the official ODS faces.
- **Colour:** ODS system colours only. Near-black text (`#1A1A1A`) on white, Ontario blue links (`#0066CC`), and colour used solely where the system assigns meaning — success green, alert red, warning yellow, information teal. Accent colours are never used as page backgrounds, per ODS rules.
- **Components:** real ODS patterns — application header, primary buttons, callouts, summary lists, badges, and fieldsets.

### Accessibility — AODA / WCAG 2.1 AA

- **Colour is never the only signal.** Every status colour is paired with text, so the design works for colourblind and screen-reader users.
- **Real form semantics.** Filters are true checkboxes inside a fieldset/legend — keyboard- and screen-reader-operable, not styled `<div>`s.
- **Keyboard support.** A "Skip to main content" link and a visible `#009ADB` focus ring on every interactive element.
- **Contrast.** All text meets or exceeds the 4.5:1 minimum required by law for Ontario public services.
- **Structure.** Proper heading hierarchy, landmarks, descriptive `aria-label`s, and respect for `prefers-reduced-motion`.

> **Note:** Because the ODS theme loads from a CDN, the full Ontario styling requires an internet connection. The page also contains its own internal stylesheet, so layout and content remain usable offline. A production build would install the ODS packages locally and pass a full accessibility audit.

---

## What the prototype shows

A clickable, three-screen parent-facing flow. The tabs in the header switch between views.

**1. Find care** — A unified map and list of nearby options across all care types. Priority chips ("Infant," "CWELCC fees," "Daily outdoor time") drive a *match summary* on every result that names what fits and, honestly, what doesn't.

**2. My applications** — The honest-standing view. Each application shows where the parent stands in plain language, an estimated-standing range (explicitly "not a promise"), real recent activity from that centre, and prompts to confirm continued interest — the mechanism that keeps lists clean.

**3. My profile** — One profile that feeds every application. Documents are tracked with expiry warnings, so an out-of-date file never silently stalls a live application.

### Prioritized feature set (FVD)

- **Ship first:** Waitlist transparency · Provider-controlled allocation · Inactive waitlist management · Zero-assumption onboarding
- **Sequence next:** CWELCC eligibility surfacing · Seasonal intake flows
- **Defer:** AI-assisted messaging

---

## Built with

Single-file prototype — HTML + the official ODS theme + a small project stylesheet, with vanilla JavaScript for tab switching. No build step.

```
index.html   →  the entire prototype
README.md    →  this file
```

## Run it locally

Open `index.html` in any browser (connect to the internet for the full Ontario styling).

---

## Roadmap

- [ ] Onboarding / first-run flow for *The Lost Beginner* persona
- [ ] "Spot offered" screen — the accept/decline moment, currently the biggest journey gap
- [ ] Apply flow from the discovery screen
- [ ] Provider side: dashboard, waitlist manager (inactive-family flagging), 2-minute availability update, offer tool
- [ ] Broaden provider research beyond n=1
- [ ] Instrument KPI logging events (session_start, form_submitted, queue_entry, placement_offered, availability_updated)
- [ ] Migrate from CDN to locally installed ODS packages + formal accessibility audit

---

## Status & credits

Volunteer initiative, in the **Develop** phase of the Double Diamond. Research, synthesis, and design by a five-person team. This repository holds the parent-facing prototype; provider-side screens are next.

*This is a concept project and is not affiliated with the Government of Ontario or the CWELCC program.*
