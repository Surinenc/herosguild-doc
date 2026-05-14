# Hero Backgrounds & Life Histories

Every hero who walks through the tavern door has a past. Eight of them did something specific before they got here, and four things happened to them on the way — childhood, adolescence, young adulthood, and the years just before they signed your contract. None of it is decoration. All of it shapes the numbers.

This guide covers the **Background tag** (the broad-strokes "what they did before") and the **Lifecycle** (the four life events that flesh it out). The two systems compose: the tag biases which events get rolled, and the events make the tag feel like a specific person rather than a template.

---

## The Eight Backgrounds

Every recruit carries one background tag, assigned at generation alongside their class and quality. It is independent of both — a Noble Mage and a Noble Warrior share an axis the Cultist Cleric does not. The eight backgrounds are:

- **Noble** — raised on tutors, expectations, and family debt
- **Criminal** — pragmatic about consequences, rehearsed at improvising
- **Soldier** — knows what an actual fight looks like, often unwilling to talk about it
- **Peasant** — durable, distrustful of paperwork, the cheapest hire and frequently the steadiest
- **Scholar** — reads more than the Guild Clerk would like, occasionally to the point of usefulness
- **Merchant** — values returns; values them especially when they are personal
- **Cultist** — believed something. Some still do. The active-effects row will tell you which.
- **Outlander** — from somewhere the map sketches in dotted lines; arrives with stories nobody else can confirm

Each background grants a small permanent combat modifier (surfaced as a runtime active-effect on the hero card) and a tilt in which lifecycle events the hero is likely to have rolled. The mechanical effect is described on the **Background tab** of Hero Details — same information from two angles, intentionally duplicated: the active-effects row is *who's modifying combat right now*; the Background tab is *who this person is*.

---

## The Lifecycle: Four Stages, One CV

When a hero is generated, the system rolls **four life events** — one per life stage — from an authored catalog of 120 paragraphs. The four paragraphs together form the hero's **CV**: a short, first-person life history that reads chronologically and never mentions a single mechanical number.

| Stage | Ages | UI label | Events authored |
|-------|------|----------|-----------------|
| Childhood | 5–10 | "Childhood" | 30 |
| Adolescence | 11–16 | "Adolescence" | 30 |
| Young Adulthood | 17–22 | "Young Adulthood" | 30 |
| Before the Guild | 23–30 | "Before the Guild" | 30 |

The roll happens once, at hire (or when you first look at a hero on a save that pre-dates this system — see [Existing Saves](#existing-saves) below). It does not change. The same hero, on the same save, will always have the same four paragraphs.

### Background weighting

The roll is not uniform. For each event in a stage's pool, the system checks whether any of the event's background tags match the hero's background. If they do, the event gets **3× weight**; if not, it gets baseline weight. So a Noble is roughly three times more likely than baseline to roll noble-tagged events (tutors, refused fish at the family feast, the crown debt that someone else inherited), but cross-background events (`street-orphan-6`, `family-barn-fire-7`) remain eligible at baseline weight. Backgrounds tilt the dice. They do not seal the bag.

The authoring guide caps any single background tag at no more than 25% of a stage's events, which keeps the 3× multiplier from producing degenerate clustering (i.e. every Noble rolling the same four paragraphs).

---

## Mechanical Effects

Every event carries an optional set of `{ stat, multiplier }` pairs. The stats currently affected are:

- `damage` — applied as a multiplicative pass to every hero-source damage roll, on top of the [class damage multiplier](combat.md#hero-damage)
- `hp` — applied to effective max HP after passives, ascendancy, body efficiency, and titles
- `str`, `dex`, `int`, `vit`, `lck` — applied as the final multiplicative pass on effective stats

Modifiers from all four events compound. So do modifiers from any **lifecycle-granted traits** (see below). Contradictions are allowed and intentional — a hero with `sickly` × 0.90 hp and `iron-constitution` × 1.10 hp ends up at ×0.99, both narrative paragraphs intact and the math politely netting out.

The numbers themselves are never shown in the UI. You see the prose. The engine sees the multiplier. The discrepancy between "what they tell you happened" and "what their stats now insist is true" is, in the Guild Clerk's opinion, the most realistic part of the entire system.

### Lifecycle traits

Some events grant a named trait, prefixed `lifecycle:` in the hero's trait list (e.g. `lifecycle:duelist`, `lifecycle:sickly`). These behave like ordinary traits — they're surfaced on the Background tab under "Traits" — but their stat effects are computed by the lifecycle aggregator, not the trait system, which keeps a hero who picks up `Duelist` from a tavern brawl mechanically identical to one who was born to it.

### Body flaws

Some events leave the hero with a **body flaw**: a damaged or destroyed body part. The lifecycle supports six families × left/right = twelve slots:

- Arms, hands, legs, feet, eyes, ears

Brain, jaw, heart, fingers, and faces are explicitly out of scope. The catalog validator hard-rejects events that try to flaw those.

A flaw applies once per slot, even if multiple events touch the same body part — the second narrative paragraph still appears in the CV; the engine just doesn't double-count the damage. Flaws under 100% damage land as **Damaged**; flaws at 100% land as **Destroyed**.

Lifecycle flaws compose cleanly with the [Prosthetic system](crafting.md#prosthetics): fitting a prosthetic at the Infirmary lifts the body-part efficiency back up (basic 50%, standard 80%, enchanted 125%), but the lifecycle's direct stat penalty (e.g. `dex × 0.93` on a cart-foot event) remains. The body-part axis can be over-restored with an enchanted prosthetic; the stat penalty is permanent.

---

## Where Backgrounds Show Up

### At the tavern (recruitment)

Click **Details** on any candidate in the Tavern. The recruit-details modal includes a **"A Life, So Far"** section showing the candidate's four paragraphs in chronological order, each labeled by stage. The CV is the actual rolled narrative — no editorialising, no biased presentation, no "the hero's spin vs the truth." If a candidate is lying to themselves on the page, that's the catalog's voice doing its job, not the UI hiding anything.

The inline quick-hire card does not show the CV — there isn't space. Recruits are screened on the modal.

There is no re-roll. To reject a CV, pass on the candidate.

### On the Background tab (post-hire)

The Hero Details panel now has a **Background tab** (icon 📜) alongside Gems, Social, Career, Chronicle, Paragon, and Trials. It is the canonical home for everything the lifecycle produces. Layout, top to bottom:

1. **Origin** — the hero's background tag and the mechanical effect blurb it carries
2. The four life paragraphs, labeled by stage
3. **Marks of a Life** — friendly-named body flaws ("Missing left eye", "Bad right leg")
4. **Traits** — every `lifecycle:*` trait in the hero's trait list, decoded into display names

The Chronicle tab continues to record world events (missions, ally deaths, milestones). It does **not** weave lifecycle paragraphs in — that was considered and dropped. The CV is the static identity; the Chronicle is the running history. The two surfaces stay separate.

---

## Existing Saves

The system migrates older saves automatically. If a hero record has no lifecycle events, the system rolls four for them on first load, seeded deterministically from the hero's ID — the same hero will always backfill to the same four paragraphs, so the migration is one-time and stable.

There is one accepted consequence: **existing heroes' effective stats will shift slightly on first load** after the upgrade, because the multipliers from their backfilled events take effect immediately. This was a deliberate tradeoff. The alternative was leaving old heroes statless and treated differently from new ones, which the design team judged worse than the small one-time shift.

No migration modal pops up. The Background tab quietly populates the next time you open a hero's details, and the CV is there.

---

## Tips

- **Read the CV before you hire.** Backgrounds tilt the math; lifecycle events stack on top. A hero whose CV reads grim probably has the multipliers to match — for better or worse, depending on which way they net.
- **Match background to role when you can.** Noble Clerics carry the noble tilt into Cleric work; Outlander Rogues bring the outlander tilt into Rogue work. The combinations aren't required, but they're more legible than mismatched pairs.
- **Don't panic about flaws.** A Damaged eye or leg isn't a write-off. The [Prosthetic system](crafting.md#prosthetics) covers every supported slot at three tiers, and enchanted prosthetics over-restore the underlying body-part efficiency.
- **Treat the CV as truth, even when the hero is unreliable.** The first-person narration is sometimes self-serving. That, too, is the design — and the multipliers underneath are honest regardless.

---

## Related Guides

- [Heroes & Classes](heroes.md) — base hero stats and progression
- [Combat System](combat.md#hero-damage) — where the class and lifecycle damage multipliers sit in the damage chain
- [Crafting](crafting.md#prosthetics) — prosthetics for lifecycle-sourced body flaws
- [Interface Overview](interface.md#hero-details) — Hero Details tab layout
