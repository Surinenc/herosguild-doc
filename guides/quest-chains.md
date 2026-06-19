# Quest Chains

Some jobs finish when the last goblin falls. Others have a second page. Quest chains are the jobs with a second page — sequences of connected missions that unfold over several in-game days, each step revealing the next, ending with a reward the Guild Clerk files under "makes the paperwork worth it."

A chain is not a single mission. It is a campaign made of missions. You do not accept a chain; it unlocks, puts its first step on the Mission Board with a 📜 badge, and waits patiently for you to notice.

---

## The Three Categories

There are three kinds of chain, each unlocked differently and rewarding differently.

### Story Chains

Seven long-form campaigns that track the shape of your guild's career. Each one unlocks at a specific **guild rank**, starting at rank F and opening up as you climb.

- **3–5 steps** per chain
- **No time limit** — the chain waits as long as it needs to
- **Finale rewards:** a named legendary item, a substantial reputation grant, and in two cases a **special hero** who joins your roster at the level of your highest-level hero, pre-equipped and pre-specced

Story chains are where the game's narrative lives. Each step comes with flavor text; each completion advances a small arc that the world quietly remembers.

The two most recently added are **The Founding Blade** (rank D, retrieves the realm's *first guild sword*) and **The World Tree Pact** (rank D, brokers the realm's accord with the Fae and rewards *Nature's Embrace* — a Legendary leather chest piece for Ranger/Cleric, not a bow per `NamedItems.ts:331-341`). Both ship as full three-step chains with a finale of named item + recipe + two skill gems.

### Class Chains

One chain per class for most of them — **seven chains across six classes**, since the Mage now has two. Unlocking any of them requires two things simultaneously:

- Guild rank **E or higher**, and
- At least **one hero of that class at level 25+**

The Guild Clerk notes that this is the game's way of saying "prove you're committed to this class before it reveals its secrets."

- **3 steps** per chain, thematically tied to the class
- **No time limit**
- **Finale rewards:** a class-restricted named item, a crafting recipe, and two skill gems

The Mage's second chain, **The Archmage's Thesis**, unlocks at level 40 and **rank C** (the standard Class Chain gate is rank E, so the Thesis is two ranks higher, not one — `ClassChains.ts:148`). It rewards the *Archmage Robes* — for Mages who have moved past the "first major item" tier and want something explicitly archmage-flavoured.

You can pursue multiple class chains in parallel — qualifying a Warrior doesn't close the door on the Mage chain, and qualifying the Mage's first chain doesn't close the door on the Thesis.

### Weekly Bounties

Twelve rotating templates. No unlock requirement — every guild sees one from day one.

- **3 steps** per bounty
- **7-day timer** — starts when the bounty rolls; if unfinished by day 7, the chain closes silently and a new one rolls
- The game never rolls the same bounty two weeks running
- **Finale reward:** one random Epic-or-better item scaled to your highest hero's level, plus a meaningful gold bonus (roughly 1,800–4,200g)

Weekly bounties are the game's weekly check-in. They don't have a grand narrative; they have a deadline and a very specific kind of monster to deal with.

---

## How Chains Work on the Mission Board

Each active step appears on the Mission Board as a regular mission with a **📜 badge** and a tooltip that names the chain and the step (e.g., *"The Goblin Menace — Step 1/4"*).

From there, it behaves like any other mission:

1. Select it
2. Form a party
3. Dispatch them
4. Wait for the Guild Clerk's report

**If you ignore the step for a day** — it rolls onto tomorrow's board unchanged. Chain progress doesn't decay.

**If the party fails the step mission** — no chain progress is lost. The same step reappears on the next board roll. You retry until you succeed. (The Guild Clerk considers this generous. The heroes, less so.)

**If the party succeeds** — a narrative completion screen shows the step's flavor text and the rewards earned. The next step unlocks on tomorrow's board.

### The Weekly Bounty Edge Case

If a weekly bounty's 7-day expiry hits while your party is already dispatched on one of its steps, that mission completes normally and the chain resolves before closing. The 7-day timer only affects **future** board rolls — parties already in the air are never recalled.

---

## The Quest Log

The **Quest Log** button (glyph **❡**) sits in the **Top Bar** alongside the other icon buttons (`TopBar.tsx:134`) and is visible from day one. It has three tabs:

| Tab | What it shows |
|-----|---------------|
| **Story** | Active, available, expiring, and completed story chains (7 chains total in the catalog) |
| **Class** | Active, available, expiring, and completed class chains (7 chains across 6 classes — the Mage has two) |
| **Weekly** | The current bounty (with its ⏰ countdown), plus a history of completed bounties |

The Quest Log UI does **not** enumerate locked chains with their unlock conditions (`QuestLog.tsx:113-148`); the panel only renders chains that have entered the player's `questChainState.chains`. When no chain of a type is unlocked yet, the tab shows empty-state flavor copy rather than a list of locked chains. Active chains show your current step, a summary of step-level rewards, and a preview of the finale reward.

---

## Rewards, By Category

| Reward Type | Story | Class | Weekly |
|---|:-:|:-:|:-:|
| Gold (per step + finale) | ✓ | ✓ | ✓ |
| Reputation | Finale only | — | — |
| Materials | ✓ | ✓ | ✓ |
| Named item (finale) | ✓ | ✓ | — |
| Crafting recipe (finale) | Some | ✓ | — |
| Skill gem (finale) | Some | ✓ (×2) | — |
| Random Epic+ item | — | — | ✓ (finale) |
| Special hero (finale) | 2 chains | — | — |

Class chains are the game's main reliable source of class-restricted named gear and targeted skill gems. Weekly bounties are the most predictable source of high-rarity random loot. Story chains are where the singular, named, plot-relevant items live.

---

## Special Hero Rewards & Barracks Overflow

Two story chains grant a **special hero** as part of their finale — a named, pre-built adventurer who joins your guild immediately at the level of your current highest-level hero. They arrive with equipment and a built skill setup.

If your Barracks is already at capacity when this happens, the hero joins anyway. Your roster goes **over cap** (e.g., 13/12), and the Guild Scene header turns red with a warning. A **14-day grace timer** starts:

| Days Remaining | Warning Color |
|----------------|---------------|
| 14 → 8 | Yellow |
| 7 → 4 | Orange |
| 3 → 1 | Red |

Your options during the grace period:

- **Upgrade the Barracks** — raises capacity, removes the warning
- **Dismiss a hero voluntarily** — your choice who leaves
- **Do nothing** — on day 13 the game shows a modal naming the hero with the lowest mood (who will be the one to leave), and on day 14 that hero departs automatically

The Guild Clerk notes that heroes who leave this way are not angry, exactly. They just read the room.

---

## Unlock Timing, At a Glance

| Unlock | When |
|--------|------|
| First Weekly Bounty | Day 1 of any new save (and every 7 days thereafter) |
| Quest Log icon | Visible from day 1 (shows locked chains with requirements) |
| First Story chain | At guild rank F |
| Later Story chains | At ranks E, D, C, B |
| Class chain (per class) | Rank E + one hero of that class at level 25+ |

---

## Tips

- **Check the Quest Log before dispatching parties** — if a chain step is on tomorrow's board, you may want to hold a strong party for it
- **Don't stress weekly bounties you can't finish** — missing one costs nothing except the reward. The next Monday brings a different one
- **Class chains are efficient** — three missions for a named item, a recipe, and two gems is the best reward-per-mission ratio in the game
- **Plan Barracks space before completing "The Undead Plague" or "The Rival's Gambit"** — if you know a special hero is on the finale, having a bed ready avoids the countdown entirely
- **Chain steps don't stack** — each chain has at most one active step on the board at a time, but multiple chains can have steps active simultaneously

---

## Related Guides

- [Interface Overview](interface.md) — Mission Board and Quest Log UI
- [Guild Management](guild.md) — Guild rank progression (gates story chains)
- [Heroes & Classes](heroes.md) — Leveling heroes to 25+ for class chains
