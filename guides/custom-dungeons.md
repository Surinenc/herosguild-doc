# Custom Dungeons

A workshop where Guild Masters design their own dungeons, publish them to the realm, and run other Guild Masters' dungeons in return. The Guild Clerk has filed three complaints about the naming — there is already a Workshop, and that Workshop makes belts — but the bottom-nav button labelled **Workshop CD** (🗝) is firmly in place, and the Clerk has been told the matter is closed.

This guide covers the two halves of the system: designing and publishing dungeons (the **author loop**), and raiding the community's published dungeons (the **raid loop**). They share an interface and a name; otherwise they are quite separate.

---

## Where to Find It

The **Workshop CD** button sits in the bottom navigation alongside Guild, Market, Dungeons, and the rest. Pressing it opens the Custom Dungeons app, which then routes between the various sub-pages depending on what you want to do.

The button is **not the crafting Workshop**. That one has hammers. This one has dungeons. Both are essential, and only one of them ends in a wipe.

---

## The Two Loops

The Custom Dungeons app supports two distinct activities, both reached from the app's home screen:

| Loop | What you do | Where it lives |
|------|-------------|----------------|
| **Author** | Design rooms, validate, test, publish your own dungeon | Editor + Test Modal + Publish Modal |
| **Raid** | Browse community dungeons, deploy a party, run the dungeon | Gallery + Raid runtime |

You can be a full-time architect, a full-time raider, or both. Most Guild Masters end up both, because the architect rewards are paid out when *other* people run your dungeons, and the runners need dungeons to run.

---

## The Author Loop

### The Editor

The editor is a room-graph builder. You place rooms, connect them with corridors, set room types, and arrange the entrance and exit. The canvas pans, zooms, and snaps to a grid — the Guild Clerk insists on the grid, and the editor enforces it without comment.

**Room-graph rules the editor enforces:**

- Each room occupies a footprint on the grid. Rooms may not **touch** each other directly — there must be a corridor between them. Adjacent rooms that share an edge are flagged by the validator and refuse to publish.
- Rooms may not overlap on the minimap. Reposition or resize until the overlap clears.
- The dungeon must have a reachable entrance and a reachable exit.
- Pathfinding must produce a route from one to the other without dead ends that the validator considers actively malicious.

The editor exposes a **starter** menu — pre-built layouts and themed starting points (forest, crypt, infernal, etc.) that you can edit rather than designing from scratch. Most experienced architects start from a starter and then mutilate it beyond recognition.

### The Validator

The validator runs whenever you save or attempt to publish. It surfaces errors as a checklist; you cannot publish until the checklist is empty.

**Common validator complaints:**
- **Touching rooms** — two rooms share an edge. Move one.
- **Minimap overlap** — the minimap representation collides with another room's. Move one.
- **Unreachable entrance/exit** — pathfinding can't connect them. Add corridors.
- **Empty room set** — you have to put rooms in the dungeon.

The validator is direct rather than polite. The Guild Clerk approves of this and has asked whether the validator could be redeployed to staff meetings.

### Test Modal

Before publishing, you can test-run your own dungeon in the Test Modal. The test runs the dungeon end-to-end with a simulated party, gives you a difficulty read, and tells you whether the layout actually works in practice — which is sometimes a different question from whether the validator approves of it.

**What testing tells you:**
- Whether the rooms can be cleared in the intended order
- Approximate difficulty based on hazard/encounter density
- A walkthrough of what happens, room by room
- Whether your favourite trap is, in fact, lethal

You can iterate the editor → test loop as many times as you like. Nothing about test runs is recorded publicly.

### Publish Modal

When you're satisfied, the Publish Modal commits your dungeon to the realm. Publishing is **versioned** — every publish stamps a version number, so you can edit and re-publish without overwriting your live edition mid-raid.

**Two-Stage Publishing.** Fresh publishes land as **Draft** by default. A Draft is visible only to you; nobody else sees it in the gallery yet. The dungeon auto-promotes to **Public** once it has been cleared **10 times** on the current version — at which point the gallery starts showing it to the wider realm. You can short-circuit this by ticking the "publish as public" option at publish time, or by promoting manually from your architect tools.

Forfeits do not count toward the 10-clear threshold. Only completed clears do. The Guild Clerk's note in the margin reads: "Audiences who haven't actually made it through your dungeon are not yet your audience."

Re-publishing an existing dungeon bumps its version number, resets the clear count, and (unless you opt back into public) reverts the new version to Draft until it earns its way out again.

**Narrator-Hero Lock.** During publishing, you may optionally lock a specific hero from your own guild as the dungeon's **narrator**. That hero is then temporarily unavailable to your own missions for **3 days** while they tour the realm telling the story of your dungeon. The lock is optional — you can publish anonymously — but a narrator-hero earns the dungeon's audience some flavour and improves the listing.

Published dungeons appear in the community gallery for other Guild Masters to find. **Once published, a dungeon is raid-only for everyone except you** — you can still edit it from your own architect tools, but other Guild Masters cannot open its editor view. They can only run it.

---

## The Raid Loop

### The Gallery

The Gallery is where you find dungeons to run. It lists:

- **Community dungeons** — published by other Guild Masters
- **Templates** — first-party starting layouts available to play as-is
- **Featured / seasonal** — dungeons that the realm has surfaced for the current season

The realm also ships with **nine named starter dungeons** as ongoing community content — *The Sunken Cellar, The Library That Watches, Goblin Snare-Maze, Patrol Tower of Sighs, Endless Stair of the Lich, The Demon's Bargain, The Warden's Round, The Iron Menagerie,* and *The Drowned Cathedral.* They range from short Apprentice-tier layouts to multi-floor Master-tier crawls, and they exist partly as content, partly as worked examples of what an architect can do with the editor.

Each card shows the dungeon's name, the architect's name (or "Anonymous"), the elegance score, observed difficulty from previous raid attempts, and a **⚔ Raid This Dungeon** button. Press it and you commit a party.

### Picking a Party

The raid runtime opens with a party picker. The only eligibility rule is **`hero.state === HeroState.Ready`** (`raidEligibility.ts:24`) — any alive, unassigned, uninjured, untraining, uncrafting, unscheduled hero can be picked. No level cap, no class restrictions. A narrator hero you've locked to one of your own published dungeons stays out of the picker for 3 days regardless.

### The Run

The raid orchestrator is a 9-state machine: the party enters, traverses rooms, encounters hazards and combat and the dungeon's bespoke moral events, collects loot, and either clears the exit or doesn't. Telegraphs and combat draw on the same systems you know from regular dungeon runs, but the room order, hazards, and events are entirely the architect's doing.

**Wipe rewind.** Custom Dungeon raids include a finite-token rewind mechanic (`RewindTokens { remaining, max }`, default starts at 2 remaining out of 3 max — `cdRaidData.ts:182,220`). When the party reaches a wipe condition you may spend a token to roll the run back to a previously-explored node in the saga tree and continue from there. Tokens do not refill within a run; once `remaining` hits 0, the next wipe is final. There is no per-rewind scoring penalty — the cost is the token count itself.

### Raid Runtime Mechanics

The Custom Dungeon raid runtime has its own toolkit, distinct from regular dungeon combat. The key pieces:

#### Per-Class Session Abilities

Each class brings a session-scoped raid ability with limited charges. Charges refresh only at the start of the next run, not between rooms:

| Class | Ability | Charges | Effect |
|-------|---------|---------|--------|
| Mage | **Dispel** | 2 | Permanently disables a **magical hazard** in the current room (e.g. Magic Seal, Icy Flooded Passage). No HP or mood cost |
| Cleric | **Purify** | 2 | Permanently disables a **cursed hazard** (e.g. Toxic Gas Cloud, Cursed Altar) |
| Rogue | **Disable** | 3 | The general-purpose hazard removal — applies to any hazard the Rogue can solve. **+1 charge per living Ranger in the party** |
| Necromancer | **Clear** | 2 | Temporarily clears every hazard in the current room. Each cleared hazard re-arms after 3 turns |
| Necromancer | **Send Undead** | 2 | Sends a minion to a **directly adjacent** target room. If the minion isn't destroyed by a patrol in or adjacent to the target, the target is sighted and all its hazards are permanently cleared. If a patrol is in threat-zone, the minion is destroyed, the room is still sighted, and that patrol redirects toward your party |
| Ranger | **Perception** (passive) | — | Extends the party's sight pool by +1 hop while at least one Ranger is alive. Not a charge — just being a Ranger does it |
| Warrior | — | — | Warriors solve hazards by being warriors at them. The Guild Clerk has stopped trying to write this up |

Hazards that none of your classes can handle become problems you walk through and pay the toll on. Build parties accordingly.

#### Run-Trauma — Hazards Carry Across Rooms

Custom Dungeon raids implement a **trauma** mechanic: every point of HP damage a hero takes from a hazard accumulates as a permanent debuff that **reduces that hero's effective max HP for the rest of the run.** A Cleric's heal cannot lift a hero above their trauma-reduced max — the heal clamps to whatever cap the trauma has left them.

A hero whose accumulated trauma reaches their original max HP **falls.** Trauma persists across rooms within a single run, and resets only when the run ends (cleared, wiped, or forfeited).

The practical effect: hazards are not free even if you have a Cleric. The Guild Clerk has observed parties die slowly across six rooms of accumulated paper-cuts where any single hazard would have been trivial.

#### Axis Shifts Are Permanent

Moral-event choices during the run earn or burn the guild's **Valor**, **Wealth**, and **Order** axes. These shifts persist to your guild identity on cleared, wiped, **and** forfeited outcomes — there is no "I quit, I didn't mean it" path. The right-rail HUD during the run shows the **deltas this run has earned so far**, not your full axis values; the totals only commit when the run ends.

The Custom Dungeon system uses its own moral event catalogue, distinct from the regular [events system](events.md). The events are placed in rooms by the architect and surface as modal choices when your party traverses that room.

#### Patrols, Ambushes, and the Hide / Flee Decision

Architects can place **patrol entities** that walk through dungeon rooms on a set route or wander within a defined zone. Each patrol has a **sight range** (default 1 hop). When the patrol's next position is within sight of your party, they spot you — and you get an ambush overlay with three options:

- **Fight** — engage. Standard combat.
- **Hide** — roll the party's **ambush evasion chance** against the patrol. The chance is built from a 5% base, mood (party-average and leader contribute), a per-Ranger bonus that diminishes after the first, and clamps to a 5–60% range. Succeed and the patrol passes by. Fail and you fight from a disadvantaged position
- **Flee** — retreat to the previous room. Only available when there *is* a previous room to retreat to. Patrols still tick — you can't exploit Flee to dodge cooldowns indefinitely

Combat in a room also broadcasts noise. Patrols within a configurable BFS range of the noise will redirect toward that room on subsequent turns — the dungeon equivalent of "the watchman heard the screams." Architects who place patrols in noise range of likely combat rooms are doing so deliberately.

### Rewards (for the raider)

Custom Dungeon rewards are concentrated in the **first clear**: when you clear a community dungeon for the first time, the realm pays out gold + XP via `computeFirstClearGold` / `computeFirstClearXp` (`cdRaidRewards.ts:64-77`), where the gold range is the regular **`MISSION_GOLD_RANGES`** for the dungeon's observed difficulty stars, scaled by average party level. Subsequent clears of the same dungeon do **not** repeat the first-clear payout — they still record your run for League standings and personal best, but no fresh gold drop.

There is no separate Custom Dungeon loot economy or bespoke loot table — gold reuses the regular mission economy. Leaderboard placement is **not** gated by first-clear status; the leaderboard tracks each player's best cleared session for the dungeon and ranks the top 10.

---

## Scoring & Seasons

### Elegance Score

Every published dungeon carries an **elegance score** computed from its layout — rewarding clean routing, sensible room arrangements, and varied encounter types over arbitrary cruelty. The elegance score is **display-only**: it does not affect rewards, leaderboard placement, or anything load-bearing. It is, in the Guild Clerk's words, "a small medal pinned to the architect's lapel by the realm itself."

### The League

The League rotates through three competitive metrics on a **monthly cadence** (the server indexes by `leagueMonth`; the client `leagueMetricForWeek` helper is the offline-only approximation). The metric scoring is unrelated to the per-dungeon elegance display:

| Metric | What it scores | Better when |
|--------|----------------|-------------|
| **Elegance** | **Decisions taken** on a cleared run (`r.decisions`) | Fewer is better — the contest is about clearing a dungeon with the fewest choice-prompts handled |
| **Efficiency** | **Attempts** until first clear (`r.attempts`) | Fewer is better — rewards getting it right early |
| **Speed** | **Turns** on a cleared run (`r.turns`) | Fewer is better — straight speedrun |

Source: `cdLeague.ts:128-138`. The League panel shows the current month's metric, your standing, and the top performers. (Note: this is distinct from the per-dungeon **elegance score** described above, which is a layout-quality display number — the League's Elegance metric measures *decision frugality*, not layout cleanliness.)

### Seasons & The Watcher

The **Seasons** page (`CdSeasonsPage.tsx`) shows the rolling monthly league standings, the Hall of Notorious, and a legacy-league archive. It does not currently expose themed dungeon rotations or special events — those are aspirational labels.

The **Watcher Journal** (`CdWatcherPage.tsx`) is a log browser: your raids plus raids of your published dungeons, sortable by date / attempts / outcome / depth, with a scrubbable timeline. It is closer to a chronological log viewer than an achievements page.

---

## Architect Rewards

This is the half of the system that makes publishing worth the trouble.

When other Guild Masters across the realm clear *your* published dungeon, the realm pays you, the architect, in **gold and Guild Reputation**. The rewards accumulate on the server while you're playing, and are **claimed on login** — every time you start a session, any pending architect rewards are deposited into your vault and noted in the Chronicle. The Guild Clerk has stopped pretending not to look at this notification first.

**What earns architect rewards:**
- A successful clear of your dungeon by another Guild Master
- Repeat clears — your dungeon doesn't stop paying you because it's been run before
- The rewards scale with the observed difficulty of your dungeon and the cleared status

**What does not:**
- Wipes by raiders — your dungeon paying you for killing other people's parties would create perverse incentives
- Your own test-runs of your own dungeon

**Fame Decay (Dungeon Archival).** "Fame Decay" in this system is a **dungeon-archival** mechanic in `cdObservedDifficulty.ts`, not a rewards-shrinking one: a published dungeon that goes 60 days without being raided is archived out of the main browse list (`cdObservedDifficulty.ts:103-118`). Pending architect rewards themselves are not time-scaled by the client — the server returns the full accumulated `claimedGold` and `claimedReputation` at the time of claim. To keep a dungeon visible and earning, it has to keep being run.

The **Architect Page** shows your published dungeons, lifetime architect rewards earned, recent clears with raider names and outcomes, and your seasonal standing. Most architects discover that one specific dungeon outearns all their others combined, and respond by quietly trying to figure out which feature of that dungeon is doing the work.

---

## Related Guides

- [Dungeons](dungeons.md) - Regular dungeons (the realm's, not yours)
- [Guild Management](guild.md) - The Workshop facility — the one with hammers
- [World Boss Raids](raids.md) - A different "raid" system entirely
- [Combat System](combat.md) - The combat the custom dungeons inherit

---

*"A dungeon worth publishing is one you wouldn't survive yourself. Publish it anyway."*
