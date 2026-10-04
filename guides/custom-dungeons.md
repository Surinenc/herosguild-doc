# Custom Dungeons

A workshop where Guild Masters design their own dungeons, publish them to the realm, and run other Guild Masters' dungeons in return. The Guild Clerk filed three complaints about the naming — there was already a Workshop, and that Workshop makes belts — and has now, after a career of being told the matter is closed, won one: the bottom-nav button (🗝) reads **Custom Dungeons**.

This guide covers the two halves of the system: designing and publishing dungeons (the **author loop**), and raiding the community's published dungeons (the **raid loop**). They share an interface and a name; otherwise they are quite separate.

---

## Where to Find It

The **Custom Dungeons** button sits at the far right of the bottom navigation, last in a row that runs Tavern, Missions, Dungeon, Craft, Training, Shop, Vault, Facilities, Workshop. It carries a beta badge, which is the interface's way of clearing its throat. Pressing it opens the Custom Dungeons hall, a building with more doors than it strictly needs, each leading to a different thing you might want to do.

The button is **not the crafting Workshop**. That one has hammers. This one has dungeons. Both are essential, and only one of them ends in a wipe.

---

## The Two Loops

The app does two quite different jobs, both from the same home screen, and most Guild Masters discover the second one by accident while avoiding the first:

| Loop | What you do | Where it lives |
|------|-------------|----------------|
| **Author** | Design rooms, validate, test, publish your own dungeon | Editor + Test Modal + Publish Modal |
| **Raid** | Browse community dungeons, deploy a party, run the dungeon | Gallery + Raid screen |

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
- **Key behind its own door** — a locked door whose key sits in a room only that door opens. The validator walks the dungeon the way a raider must, opening a locked door only once the key's room is reachable *without* it, and the same for a hidden door and its trigger. Locking the key inside the vault is a perfectly consistent design and an entirely unplayable one, and the validator will say so
- **A key or trigger pointing at nothing** — delete the room holding a key and the door is quietly told it no longer has one. Dangling references are scrubbed as you edit, so no door gets to claim a key that stopped existing three edits ago

The validator is direct rather than polite. The Guild Clerk approves of this and has asked whether the validator could be redeployed to staff meetings.

### Test Modal

Before publishing, you can test-run your own dungeon in the Test Modal. The test runs the dungeon end-to-end with a simulated party, gives you a difficulty read, and tells you whether the layout actually works in practice — which is sometimes a different question from whether the validator approves of it.

**What testing tells you:**
- Whether the rooms can be cleared in the intended order
- Approximate difficulty based on hazard/encounter density
- A walkthrough of what happens, room by room
- Whether your favourite trap is, in fact, lethal

You can iterate the editor → test loop as many times as you like. Nothing about test runs is recorded publicly.

**A clear is proof of *that* dungeon.** Completing the test run stamps a proof against the dungeon's playable content — its exact fingerprint, as it stood when you beat it. Change that content — rooms, connections, keys, encounters — and the proof is torn up and you test again. Purely cosmetic edits, such as renaming a room or rewriting its description, leave it standing. The realm checks that fingerprint again at publish time against the dungeon you actually submitted, so a proof earned on a beatable draft cannot be carried across to an unbeatable one.

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

A raid opens with a party picker. The only eligibility rule is that the hero is **Ready** — alive, unassigned, uninjured, untraining, uncrafting and unscheduled, which is a longer list of conditions than most heroes meet on a good day. No level cap, no class restrictions. A narrator hero you've locked to one of your own published dungeons stays out of the picker for 3 days regardless.

### The Run

A run proceeds the way all dungeon runs proceed in the ballads: the party enters, traverses rooms, encounters hazards and combat and the dungeon's bespoke moral events, collects loot, and either clears the exit or doesn't. Telegraphs and combat draw on the same systems you know from regular dungeon runs, but the room order, hazards, and events are entirely the architect's doing.

**Rewind.** At any point in a run — and most urgently when the whole party is lying on the floor — you can press **Rewind**, pick any point you've already explored on the saga tree, and roll the run back to it as though the unpleasantness never happened. Rewinds are free and unlimited. They are not, however, *forgotten*: every one is counted and printed on your results screen, a quiet record of how many times history had to be asked nicely. The future you abandoned stays on the tree as a ghost branch, which is either instructive or haunting depending on how it ended.

### Raid Mechanics

Custom Dungeon raids have their own toolkit, distinct from regular dungeon combat. The key pieces:

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

Custom Dungeon raids keep a **trauma** ledger: every point of HP damage a hero takes from a hazard accumulates as a permanent debuff that **reduces that hero's effective max HP for the rest of the run.** A Cleric's heal cannot lift a hero above their trauma-reduced max — the heal clamps to whatever cap the trauma has left them.

A hero whose accumulated trauma reaches their original max HP **falls.** Trauma persists across rooms within a single run, and resets only when the run ends (cleared, wiped, or forfeited).

The practical effect: hazards are not free even if you have a Cleric. The Guild Clerk has observed parties die slowly across six rooms of accumulated paper-cuts where any single hazard would have been trivial.

#### Axis Shifts Are Permanent

Moral-event choices during the run earn or burn the guild's **Valor**, **Wealth**, and **Order** axes. These shifts persist to your guild identity on cleared, wiped, **and** forfeited outcomes — there is no "I quit, I didn't mean it" path. Ending a run now asks you to confirm first, the axes being unforgiving enough without a misplaced click helping them along. The right-rail HUD during the run shows the **deltas this run has earned so far**, not your full axis values; the totals only commit when the run ends.

The Custom Dungeon system uses its own moral event catalogue, distinct from the regular [events system](events.md). The events are placed in rooms by the architect and surface as modal choices when your party traverses that room.

#### Patrols, Ambushes, and the Hide / Flee Decision

Architects can place **patrol entities** that walk through dungeon rooms on a set route or wander within a defined zone. Each patrol has a **sight range** (default 1 hop). When the patrol's next position is within sight of your party, they spot you — and you get an ambush overlay with three options:

- **Fight** — engage. Standard combat.
- **Hide** — roll the party's **ambush evasion chance** against the patrol. The chance is built from a 5% base, mood (party-average and leader contribute), a per-Ranger bonus that diminishes after the first, and clamps to a 5–60% range. Succeed and the patrol passes by. Fail and you fight from a disadvantaged position
- **Flee** — retreat to the previous room. Only available when there *is* a previous room to retreat to. Patrols still tick — you can't exploit Flee to dodge cooldowns indefinitely

Combat in a room also broadcasts noise. Patrols within earshot — a set number of rooms, chosen by the architect — will redirect toward that room on subsequent turns — the dungeon equivalent of "the watchman heard the screams." Architects who place patrols in noise range of likely combat rooms are doing so deliberately.

### Rewards (for the raider)

Custom Dungeon rewards are concentrated in the **first clear**: when you clear a community dungeon for the first time, the realm pays out gold + XP, with the gold drawn from the regular mission gold range for the dungeon's observed difficulty stars and scaled by average party level. Subsequent clears of the same dungeon do **not** repeat the first-clear payout — they still record your run for League standings and personal best, but no fresh gold drop.

There is no separate Custom Dungeon loot economy or bespoke loot table — gold reuses the regular mission economy. Leaderboard placement is **not** gated by first-clear status; the leaderboard tracks each player's best cleared session for the dungeon and ranks the top 10.

Custom Dungeon standings answer to the same bans as everything else that keeps score: a banned Steam player vanishes from the per-dungeon boards, the monthly League standings, and the Hall of Notorious alike, retroactively and without ceremony. See [Raid Leaderboard](raids.md#raid-leaderboard) for what a ban does and, more importantly, what it doesn't.

---

## Scoring & Seasons

### Elegance Score

Every published dungeon carries an **elegance score** computed from its layout — rewarding clean routing, sensible room arrangements, and varied encounter types over arbitrary cruelty. The elegance score is **display-only**: it does not affect rewards, leaderboard placement, or anything load-bearing. It is, in the Guild Clerk's words, "a small medal pinned to the architect's lapel by the realm itself."

### The League

The League rotates through three competitive metrics on a **monthly cadence**, a new month bringing a new definition of *good*. The metric scoring is unrelated to the per-dungeon elegance display:

| Metric | What it scores | Better when |
|--------|----------------|-------------|
| **Elegance** | **Decisions taken** on a cleared run | Fewer is better — the contest is about clearing a dungeon with the fewest choice-prompts handled |
| **Efficiency** | **Attempts** until first clear | Fewer is better — rewards getting it right early |
| **Speed** | **Turns** on a cleared run | Fewer is better — straight speedrun |

The League panel shows the current month's metric, your standing, and the top performers. (Note: this is distinct from the per-dungeon **elegance score** described above, which is a layout-quality display number — the League's Elegance metric measures *decision frugality*, not layout cleanliness.)

### Seasons & The Watcher

The **Seasons** page shows the rolling monthly league standings, the Hall of Notorious, and an archive of leagues past. It holds no themed rotations or special events — the season is a calendar, not a festival.

The **Watcher Journal** is a log browser: your raids plus raids of your published dungeons, sortable by date / attempts / outcome / depth, with a scrubbable timeline. It is closer to a chronological log viewer than an achievements page.

---

## Architect Rewards

This is the half of the system that makes publishing worth the trouble.

When other Guild Masters across the realm clear *your* published dungeon, the realm pays you, the architect, in **gold and Guild Reputation**. The rewards pile up in the realm's ledger whether or not you're watching, and are **claimed on login** — every time you start a session, any pending architect rewards are deposited into your vault and noted in the Chronicle. The Guild Clerk has stopped pretending not to look at this notification first.

**What earns architect rewards:**
- A successful clear of your dungeon by another Guild Master
- Repeat clears — your dungeon doesn't stop paying you because it's been run before
- The rewards scale with the observed difficulty of your dungeon and the cleared status

**What does not:**
- Wipes by raiders — your dungeon paying you for killing other people's parties would create perverse incentives
- Your own test-runs of your own dungeon

**Fame Decay (Dungeon Archival).** Fame decays here in the old-fashioned way: by being forgotten. A published dungeon that goes **60 days** without being raided is archived out of the main browse list, like a play nobody has bought a ticket to since spring. Pending architect rewards do not shrink while they wait — you collect every coin and every point of reputation in full, however late you turn up. To keep a dungeon visible and earning, it has to keep being run.

The **Architect Page** shows your published dungeons, lifetime architect rewards earned, recent clears with raider names and outcomes, and your seasonal standing. Most architects discover that one specific dungeon outearns all their others combined, and respond by quietly trying to figure out which feature of that dungeon is doing the work.

---

## Related Guides

- [Dungeons](dungeons.md) - Regular dungeons (the realm's, not yours)
- [Guild Management](guild.md) - The Workshop facility — the one with hammers
- [World Boss Raids](raids.md) - A different "raid" system entirely
- [Combat System](combat.md) - The combat the custom dungeons inherit

---

*"A dungeon worth publishing is one you wouldn't survive yourself. Publish it anyway."*
