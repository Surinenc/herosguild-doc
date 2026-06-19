# Crises

Periodically, the realm decides the Guild has been managing too well, and arranges for a Crisis. The Guild Clerk has, after extensive study, identified fourteen distinct varieties. None of them are good news. Several of them are categorically worse than the others. All of them last for several weeks.

This guide covers when crises happen, how they progress, what each of the fourteen does to the guild, and how to survive the three that can kill a hero outright.

---

## When Crises Happen

Crises are gated to prevent the early game from being unplayable. The realm respects:

- **Day Gate** — no crisis fires before **day 45.** Before that, the Guild Clerk's only emergencies are the financial ones.
- **Cooldown** — a **30-day cooldown** after any crisis ends before another can fire.
- **Trigger probability** — once eligible, the daily roll is **5% + 2% per day past the cooldown**, capped at **60%.** The longer you go without one, the more likely the next one becomes.

When a crisis fires, the realm picks a type, picks a duration (8 to 20 days depending on type), and announces it via a modal. From that day on, the crisis is in effect.

---

## How a Crisis Progresses

Every crisis runs through up to four **severity tiers**: Mild, Moderate, Severe, and Critical. The tier governs how heavy the penalties are, what extra effects kick in, and — for three specific crises — whether a permadeath moral event becomes available.

**Escalation:**
- Crises start at **Mild.**
- At the halfway point, if no **resolution missions** have been completed, severity bumps once.
- If the crisis runs its full duration with **zero resolution missions completed**, it ends at **Critical** automatically — the worst possible outcome.

**De-escalation:**
- Completing a **resolution mission** (a mission flagged as relevant to the active crisis) drops severity by one tier.
- Stack resolution missions and you can hold a crisis at Mild for its entire duration.

**End conditions** are one of:
- **Engaged** — the player completed at least one resolution mission. The best outcome.
- **Partial** — some resolution missions completed but not enough to fully resolve. Middle outcome.
- **Ignored** — zero resolution missions completed. Worst outcome, and the one that triggers the heavy consequences listed below.

The Guild Clerk maintains a small mental ledger of crises survived. Heroes who have survived a Critical crisis tend to mention it, unprompted, for the rest of their careers.

---

## The Fourteen Crises

The realm rotates through fourteen named crises, grouped into four categories. Each crisis has its own duration range, its own modifier pattern, and its own way of being deeply unhelpful.

### Economic

| Crisis | Icon | Duration | Effect |
|--------|------|----------|--------|
| **The Creeping Plague** | 🦠 | 12–18 | Upkeep ×1.2–2.0 (worsens with severity), recruitment frozen at Moderate+, mission rewards ×0.5–0.9, sick thoughts on heroes |
| **The Great Famine** | 🌾 | 14–20 | Upkeep ×1.05–2.5, recruitment frozen at Severe+ |

### Military

| Crisis | Icon | Duration | Effect |
|--------|------|----------|--------|
| **The Guild Wars** | ⚔️ | 10–14 | Mission rewards ×0.4–0.8, rival-guild combat missions injected |
| **The Bandit Raids** | 🗡️ | 8–14 | Mission rewards ×0.65–0.85, large reputation swings on resolution outcomes (±50 to −100) |
| **The Iron Pact** | ⚙️ | 10–14 | **Hero physical damage ×1.25; hero non-physical damage ×0.90.** Steel is in fashion; magic is out |
| **Beast Rampage** | 🐺 | 8–12 | **Beast-category enemies deal +25% physical damage** |

### Political

| Crisis | Icon | Duration | Effect |
|--------|------|----------|--------|
| **The Dragon's Tithe** | 🐉 | 8–12 | Tribute moral event (currently a **flat -500 gold** in production code; the 25% vault-percentage config is present but the production tribute handler that would read it is not wired up). Ignore the crisis and the dragon damages your highest non-Barracks facility by 2 levels |
| **The Royal Levy** | 👑 | 8–12 | Tribute moral event (configured for 15% of vault capped at 20,000 in the data layer, but the production handler is **not wired up** — the current moral event uses a sentinel gold cost rather than the percentage). A smaller tax with a more official letter |

<!-- TODO: verify - The Dragon's Tithe and Royal Levy specialEffect configs (25% of vault, 15% of vault capped 20k) live in crisisDefinitions.ts but the production tribute handler that would consume them does not appear to exist. The moral events use flat gold values instead. Re-verify whether a tribute handler exists in a code path the audit missed, or remove the percentage framing entirely. -->


### Supernatural

| Crisis | Icon | Duration | Effect |
|--------|------|----------|--------|
| **The Cult of the Unseen** | 👁️ | 12–16 | At Moderate+, the cult injects three moral events into the queue. Each comes with a difficult choice |
| **The Heretic Schism** | ✝️ | 12–18 | One moral event injected per severity step (`per-escalation` cadence) |
| **The Syzygy** | 🌕 | 10–14 | **Hero fire/cold/lightning ×1.30; enemy same ×1.15.** Both sides hit harder; the stars are aligning poorly |
| **Planar Interference** | 🌀 | 10–16 | **Hero fire/cold/lightning/holy/chaos ×0.70.** Magic suppressed. Bring physical damage or bring a Cleric who has accepted disappointment |
| **The Blood Moon** | 🌑 | 10–14 | **Both sides: chaos damage ×1.50, holy damage ×0.75.** Necromancers thrive; Clerics file complaints |
| **Necromancers Stir** | 💀 | 10–14 | **Undead-category enemies deal +40% chaos damage** |

---

## Crisis Chains

Four crises chain into other crises. If you let a chaining crisis end with an **Ignored** outcome, its successor fires earlier than the normal cooldown would allow — and starts at **Moderate** severity instead of Mild.

| Parent Crisis | Chains To | Cooldown Reduction (Ignored / Engaged) | Partial Outcome |
|---------------|-----------|----------------------------------------|-----------------|
| The Creeping Plague | The Great Famine | 15 days | 8 days |
| The Guild Wars | The Bandit Raids | 12 days | 6 days |
| The Cult of the Unseen | The Heretic Schism | 10 days | 5 days |
| The Dragon's Tithe | The Royal Levy | 10 days | 5 days |

A **Partial** outcome (some resolution missions completed but not enough to fully resolve) **halves the cooldown reduction** — the chained successor still fires sooner than normal, but you bought yourself roughly half the delay back compared to an outright Ignored result. The realm rewards partial competence with partial mercy.

A chain is announced in the Chronicle with a 🔗 log event. The Guild Clerk has filed papers, more than once, suggesting that the realm not be allowed to combo crises. The papers have been ignored.

Crises that resolve at **Engaged** still chain, but they chain into a Mild successor and earn the **Chain Breaker** milestone if the successor also resolves at Engaged. The other ten crises — including both spec-055 additions — do not chain onward.

---

## Permadeath Moral Events

Three crises can kill a hero outright via a Critical-severity moral event. This is the one Crisis mechanic the Guild Clerk consistently underlines in red.

The three crises with permadeath events are:

| Crisis | Event Title | Hero Selection |
|--------|-------------|----------------|
| The Creeping Plague | Healer's Sacrifice | Highest morale → most bonds → highest level (any class — the narrative implies a healer, but mechanically no class filter is applied) |
| The Cult of the Unseen | Inquisition's Demand | Your **most disposable** hero — lowest morale, fewest bonds, lowest level |
| The Dragon's Tithe | Hero Tribute | Legendary-quality hero if any exist; otherwise lowest morale, fewest bonds, lowest level |

### How They Fire

A permadeath event becomes available when **all** of the following are true:
- Severity has reached **Critical**
- At least **one resolution mission** has been completed
- At least **two living heroes** remain in the guild

When the conditions hit, a pending moral event is queued with a deadline of the crisis end day. You'll see a modal in Guild Events with two options.

### The Choice

Permadeath moral events are deliberately binary. **There is no gold or material buy-off.** Your choices are:

- **Accept** — the chosen hero permadies. The crisis force-ends at **Engaged**, you skip whatever was coming next, and you earn the **Sacrificial Lamb** milestone. The hero is dead. Permanently.
- **Refuse** — the hero lives. The crisis continues at Critical until its normal end day, with all the consequences that implies.

Refusing the Dragon's Tithe tribute event additionally sets a `tributeRefused` flag and earns the **Defiant Refusal** milestone — a recognition that you, specifically, told the dragon to go away.

If you let the modal time out, the default is **Refuse.** The Guild Clerk considers this the correct default and has never said otherwise.

---

## Building Damage

Four crises damage facilities if you let them resolve at Ignored. The damage applies on the day the crisis ends, recovers only through normal facility upgrades, and is announced in the log with a 🏚️ icon.

| Crisis | Facility Damaged | Levels Lost (Ignored / Partial) |
|--------|------------------|---------------------------------|
| The Creeping Plague | Infirmary | -2 / -1 |
| The Guild Wars | Training Yard | -2 / -1 |
| The Cult of the Unseen | Chapel | -1 / — |
| The Dragon's Tithe | Highest non-Barracks facility | -2 / — |

The Dragon's Tithe damage scans all facilities at runtime, excludes the Barracks, and picks the one at the highest level. This is the dragon's idea of fairness.

The Armory case is special: its level controls vault capacity, so damaging it triggers an automatic vault-capacity sync — a recent fix patched a stale-cap bug that previously left over-filled vault displays (e.g. "2409/2000") until the next save-load.

The other ten crises — including all spec-054 reskins and both spec-055 additions — do not damage facilities. The realm has decided, for now, that some things should stay standing.

---

## Combat During a Crisis

The Syzygy, Planar Interference, Iron Pact, Blood Moon, Necromancers Stir, and Beast Rampage crises all modify combat damage directly. Magnitudes do **not** scale with severity — the multipliers are the same at Mild as they are at Critical, by design.

**Damage-type multipliers (per side):**

```
Final Damage = Base Damage × Crisis Type Multiplier × Crisis Enemy-Category Multiplier
```

Both multipliers apply in sequence, so the Beast Rampage's "+25% beast physical" stacks with any active damage-type modifier from another crisis if two ever overlap (the cooldown gate makes overlap rare, but the formula composes regardless).

A crisis-time team build is a real decision. Iron Pact rewards physical-only parties. Planar Interference makes elemental Mages tragic. Blood Moon turns Necromancers into the obvious carry. The realm has, in essence, become an opinionated battle theatre with rotating rules.

---

## Milestones

The Guild Clerk maintains a quiet ledger of crisis-related achievements. Each is one-shot, and each is recorded as a `crisis_milestone` Chronicle entry on every living hero with a 💫 log event.

| Milestone | Condition |
|-----------|-----------|
| **Storm Survivor** | A crisis ended at Severe or higher with zero hero deaths |
| **Skin of Teeth** | A crisis ended at Critical, ≥1 resolution mission completed, zero hero deaths |
| **Chain Breaker** | A chained crisis resolved at Engaged |
| **Eye of the Storm** | A chained crisis resolved at Engaged with zero deaths, and the parent also had zero deaths |
| **Necromantic Drought** | Planar Interference ended with zero deaths |
| **Defiant Refusal** | The Dragon's Tithe tribute event was refused |
| **Sacrificial Lamb** | A permadeath event was accepted |
| **Tempest Conductor** | All 14 crisis types have been encountered at least once |

There is no mechanical reward and no unlock — milestones are recognition for the journal, not the vault. Some Guild Masters take this very seriously; the Guild Clerk understands.

---

## Where You See It

The Crisis system has a small UI surface:

- **Announcement modal** — fires on the day a crisis starts. Shows the crisis icon, severity badge (colour-coded Mild → Critical), duration, description, and a modifier summary listing upkeep multiplier, recruitment-frozen flag, reward multiplier, and any active damage-type multipliers ("Fire ×1.3" and similar). Uses a ceremonial scene shell with a bespoke background image.
- **Chronicle entries** — crisis start, severity changes, resolution mission completions, chain announcements, permadeath events, milestones, and crisis end all post to the Chronicle.
- **Log events** — the in-game log shows 🔗 for chain triggers, 🏚️ for facility damage, and 💫 for milestones.

There is **no always-on HUD banner or top-bar indicator.** Once you dismiss the announcement modal, you find out the crisis is still happening from the increased upkeep, the modal that pops up when you try to recruit during a freeze, and the resolution missions appearing in the mission queue. The Guild Clerk has, several times, suggested adding a status icon to the main bar. The suggestion has not yet been formalised.

---

## Related Guides

- [Combat System](combat.md) — the damage formulas the crisis modifiers plug into
- [Events](events.md) — moral events and the daily event queue
- [Guild Management](guild.md) — the facilities crises damage
- [Heroes & Classes](heroes.md) — the heroes crises occasionally kill

---

*"The realm does not declare war on you. It declares a Tuesday."*
