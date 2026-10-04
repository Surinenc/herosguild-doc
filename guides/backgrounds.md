# Hero Backgrounds & Life Histories

Two heroes, same class, same level, same sword, same gloves, same hat. They will not deal the same damage.

This is not a bug. It is the entire point.

Every hero arrives with a past — a broad-strokes background, and four specific things that happened to them on the way to your tavern door — and the past does not stay in the past. It compounds quietly into the damage chain, into the HP pool, into every number on the sheet. Two heroes who look identical on the equipment screen are, underneath, different people, doing different jobs, with different scars. The CV is not decoration. The CV is the rest of the build.

This guide covers the **Background tag** (the broad-strokes "what they did before") and the **Lifecycle** (the four life events that flesh it out). The two systems compose: the tag biases which events get rolled, and the events make the tag feel like a specific person rather than a template. The Guild Clerk considers this a great improvement on the alternative, in which every Mage would be essentially the same Mage in a different hat.

---

## The Backgrounds

Every recruit carries one background tag, assigned at generation alongside their class and quality. It is independent of both — a Noble Mage and a Noble Warrior share an axis the Cultist Cleric does not, which is why the Cultist Cleric does not get invited to either of their dinner parties. The backgrounds are:

- **Noble** — raised on tutors, expectations, and family debt
- **Criminal** — pragmatic about consequences, rehearsed at improvising
- **Soldier** — knows what an actual fight looks like, often unwilling to talk about it
- **Peasant** — durable, distrustful of paperwork, the cheapest hire and frequently the steadiest
- **Scholar** — reads more than the Guild Clerk would like, occasionally to the point of usefulness
- **Merchant** — values returns; values them especially when they are personal
- **Cultist** — believed something. Some still do. The active-effects row will tell you which.
- **Outlander** — from somewhere the map sketches in dotted lines; arrives with stories nobody else can confirm

Each background grants a permanent combat modifier (listed among the hero's active effects) and a tilt in which lifecycle events the hero is likely to have rolled. The mechanical effect is described on the **Background tab** of Hero Details — same information from two angles, intentionally duplicated, because *who's modifying combat right now* and *who this person is* turn out to be two questions with the same answer and different audiences.

---

## The Lifecycle: Four Stages, One CV

Every hero, at the moment of generation, gets four things that happened to them. One from childhood. One from adolescence. One from young adulthood. One from the years just before the contract got signed. The four paragraphs together form the hero's **CV** — a short, first-person life history that reads chronologically and never mentions a single mechanical number, which is the polite way of saying that the heroes don't know their own multipliers and would probably be insulted to learn they had any.

| Stage | Ages | Shown as |
|-------|------|----------|
| Childhood | 5–10 | "Childhood" |
| Adolescence | 11–16 | "Adolescence" |
| Young Adulthood | 17–22 | "Young Adulthood" |
| Before the Guild | 23–30 | "Before the Guild" |

The roll happens once, at hire. It does not change. The same hero, on the same save, will always have the same four paragraphs. There is no re-roll. The Guild Clerk has fielded the question many times and the answer has not improved with practice.

### Background weighting

The roll is not uniform. Each event in the pool is tagged with zero or more backgrounds — and an event whose tag matches the hero's background is weighted more heavily in the draw. So a Noble is meaningfully more likely than baseline to roll noble-flavoured events (tutors, the family feast where someone refused the fish, the crown debt that someone else inherited), but cross-background events remain eligible. The street-orphan paragraph can still happen to a Noble, and frequently does, with the kind of consequences you'd expect.

Backgrounds tilt the dice. They do not seal the bag.

No single background can claim more than a quarter of any stage's events, either. This keeps the weighting from collapsing into "every Noble has the same four paragraphs," which would defeat the purpose of everyone having had a different life.

---

## Mechanical Effects

This is where the "no two heroes the same" claim earns its keep. Every event carries an optional handful of modifiers, each one a multiplier on a specific stat. The stats the lifecycle can touch are:

- **Damage** — a multiplier on every damage roll the hero makes, applied on top of the [class damage multiplier](combat.md#hero-damage). This is the big one: two heroes with the same kit and the same class can hit for different numbers because their pasts say they should.
- **HP** — a multiplier on effective max HP, applied at the end of the chain (after passives, ascendancy, body efficiency, and titles)
- **STR**, **DEX**, **INT**, **VIT**, **LCK** — multipliers on the primary stats, applied as the final pass on effective stats

All four events' modifiers compound. So do the modifiers from any **lifecycle-granted traits** (see below). Contradictions are not just allowed but expected — a hero with one event that left them sickly and another that hardened them carries both, the math nets out somewhere honest in the middle, and both narrative paragraphs stay on the CV. People are like that. So are heroes.

The numbers themselves are never shown. You see the prose; the dice see the multipliers; and you are left with the resulting damage roll and your own conclusions. The discrepancy between *what they tell you happened* and *what their stats now insist is true* is, in the Guild Clerk's opinion, the most realistic part of the entire system.

### Lifecycle traits

Some events grant a named trait — *Duelist*, *Sickly*, *Iron Constitution*, and others in that register. They sit on the Background tab under **Traits**, and they work the same however they were come by: a hero who picked up Duelist from a teenage tavern brawl is mechanically identical to a hero who was born to it. The route to the trait does not matter. The trait matters.

### Body flaws

Some events leave the hero with a **body flaw**: a damaged or destroyed body part. The full body system covers four regions — head (brain, eyes, ears, jaw, nose), torso (heart, lungs, liver, kidneys, stomach, spine), arms (shoulders, arms, hands), and legs (legs, feet). See [Heroes Guide — Body & Injury](heroes.md#body--injury-system) for the complete list, including the vital-organ prosthetic window.

A flaw applies once per slot, even if multiple events touch the same body part. The second narrative paragraph still shows up in the CV; the body simply declines to be ruined twice in the same place, which is the polite version of the heroes' own habit of editing the worse details out of their second telling. Minor flaws land as **Damaged**; severe ones land as **Destroyed**, which is the realm's tactful term for *gone*.

Lifecycle flaws compose cleanly with the [Prosthetic system](crafting.md#prosthetics): fitting a prosthetic at the Infirmary lifts body-part efficiency back up, with the higher tiers covering more of the gap. The accompanying stat penalty from the event itself, however, is permanent. The body part can be mended. The wider story it came from is part of who the hero is now, and no amount of mithril and gears will undo it.

---

## Where Backgrounds Show Up

### At the tavern (recruitment)

Click **Details** on any candidate in the Tavern. The recruit-details modal opens with a section titled **"A Life, So Far"** — the four paragraphs in chronological order, stage by stage. The CV is the actual rolled narrative. There is no editorial filter and no biased presentation, and if a candidate is lying to themselves on the page, that is the candidate's own voice, not the Tavern being coy.

The inline quick-hire card does not show the CV — there isn't space, and the Guild Clerk considers a hire made without reading the CV to be a hire made at one's own risk. To reject a CV, pass on the candidate. There is no re-roll, partly because re-rolls would defeat the point of unique heroes, and partly because the Guild Clerk has already explained this once.

### On the Background tab (post-hire)

The Hero Details panel has a **Background tab** (icon 📜) alongside Gems, Social, Career, Chronicle, Paragon, and Trials. It is the canonical home for everything the lifecycle produces. Layout, top to bottom:

1. **Origin** — the hero's background tag and the mechanical effect blurb it carries
2. The four life paragraphs, labeled by stage
3. **Marks of a Life** — friendly-named body flaws ("Missing left eye", "Bad right leg")
4. **Traits** — every trait their life handed them, in plain words

The Chronicle tab continues to record world events (missions, ally deaths, milestones). It does **not** weave the life paragraphs in. The CV is the static identity; the Chronicle is the running history. The two surfaces stay separate.

---

## Tips

- **Read the CV before you hire.** Backgrounds tilt the math; lifecycle events stack on top. A hero whose CV reads grim probably has the multipliers to match — for better, for worse, or for the more common outcome, which is *some of each, in slightly different places*.
- **Don't expect two heroes to be interchangeable, ever.** The CV is the answer to "why didn't this Mage hit for the same as the other Mage." Equip them the same and they still aren't the same.
- **Match background to role when you can.** Noble Clerics carry the noble tilt into Cleric work; Outlander Rogues bring the outlander tilt into Rogue work. The pairings aren't required, but they're more legible than mismatched ones, and legibility is the difference between a roster and a list of names.
- **Don't panic about flaws.** A Damaged eye or leg isn't a write-off — the [Prosthetic system](crafting.md#prosthetics) handles every supported slot, and the higher tiers go a long way. The accompanying stat penalty stays, but heroes are not actuarial tables; they are what's left after they survived something.
- **Treat the CV as truth, even when the hero is unreliable.** The first-person narration is sometimes self-serving. That, too, is the point — and the multipliers underneath are honest regardless, which is a sentence the Guild Clerk has had cause to say more than once.

---

## Related Guides

- [Heroes & Classes](heroes.md) — base hero stats and progression
- [Combat System](combat.md#hero-damage) — where the class and lifecycle damage multipliers sit in the damage chain
- [Crafting](crafting.md#prosthetics) — prosthetics for lifecycle-sourced body flaws
- [Interface Overview](interface.md#hero-details) — Hero Details tab layout
