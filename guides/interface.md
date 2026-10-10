# Interface Overview

A quick guide to the Hero's Guild user interface and controls. Everything you need to know about where things are and what they do — which, in a game with this many menus, is no small undertaking.

## Main Menu

From the main menu you can:
- **New Game** - Start a fresh guild, along with a fresh set of financial anxieties
- **Continue** - Resume your last saved game from where you left off, which may or may not be a comfortable place
- **Load Game** - Browse and load from multiple save slots
- **Settings** - Audio, graphics, and gameplay options; the Guild Clerk recommends reviewing these before your first expedition

---

## Guild Screen

The Guild Screen is your home base — the one screen you'll see more than any other, and the one the Guild Clerk spent considerable effort organizing. It's divided into several areas:

### Top Bar

The top bar answers the three questions you are always asking: how much money you have, what day it is, and how badly you are regarded:
- **Gold** - Your current funds; the number that determines everything
- **Day** - Current game day; the number that determines how long you have been getting into trouble
- **Guild Rank** - Your reputation rank (F through S); the number that determines what trouble is available. Hover the cell, or tab to it, and it lays out the current rank and what it grants — roster space, mission slots, better recruits — then the next rank, the reputation still owed, and what that one grants. It will not tell you which stories open up there, on the grounds that spoiling them would be rude
- **Settings** - Access options

### Hero Panel (Left)

Your roster at a glance. The Guild Clerk designed this panel to answer the question "who is available and who has an excuse" as quickly as possible.
- Portrait and name — the essentials
- Class icon — so you remember what they're supposed to be doing
- Level — so you remember what they're capable of
- Current state (Ready, Injured, Resting, etc.) — the honest answer to whether they can go
- Mood indicator — the honest answer to whether they want to
- **Illness badge** — appears when the hero is sick, coloured by severity (green under 30, amber 30-70, red past 70). The list of afflictions is on their History tab
- **Today's thought** — a small italic strip beneath mood, showing one line of what the hero is currently mulling over. Chosen once a day from their personality traits, so the same hero says roughly the same thing all day and something different tomorrow, much like everyone you have ever worked with
- **Break chips** — a red **Break Risk** chip appears the moment mood falls under 25, and its tooltip names the mood and the line it has crossed rather than leaving you to guess. Should the roll go badly it is replaced by a **Mental Break** chip naming the break and the days left on it, which outranks every other social chip on the card, as these things tend to

Click a hero to see details.

### Facility Panel (Center)

Every facility screen carries a **level badge**: current level, build progress, what the level does for you now, and what the next one would. It appears on the Tavern, Vault, Training, Memorial Hall, Quarters, Mission Board, Shop, Infirmary, Crafting and Workshop screens, and it describes what the building actually does rather than what the builder promised, which in the Guild Clerk's experience is rarer than it should be.

The heart of your guild operations. The Guild Clerk is rather proud of this layout.
- Click facilities to access them
- Upgrade indicators show available upgrades
- Active crafting shows progress
- A row of **quick links** across the top of the facility list jumps straight to **Quarters**, **Market**, and the **Infirmary**. The Infirmary opens on demand whether or not anyone is ill — an empty ward is, per Guild custom, worth looking in on

### Info Panel (Right)

Changes based on what you've selected. The Guild Clerk considers this the most useful part of the interface, which is why nobody looks at it.
- Selected hero details
- Facility information
- Mission details

### Story Moment Scenes

Certain events pause the guild flow with a full-screen **ceremonial scene** — a short vignette between you and the next thing you were going to do. They drain in a fixed priority so the emotionally weighty scenes get their room before the celebratory ones. The current order:

1. **Infirmary** — any hero sick tonight ([Illness system](heroes.md#illness--chronic-traits)). Life-critical, so it renders before anything else.
2. **Guild Rank Up** — the guild reached a new civic milestone. Rare enough to earn the top slot after the medical stuff.
3. **Legendary Item** — a hero discovered or crafted something with a name and a history.
4. **Body Part Loss** — a hero left a piece of themselves in a dungeon. The Guild Clerk marks the incident with an appropriate degree of understatement.
5. **Enemy Made** — a mission created a personal grudge; the Ledger now has another name in it.
6. **Recruit** — a new hero joined. Lowest priority, because it happens often enough that it would otherwise drown out the rare moments above.

Each scene is a **Continue** click away from the next; there is no Skip, but there is no forced reading either — you can Continue immediately if the mood doesn't take you.

### Day Summary

Once the moment queues have drained, the day closes on a **summary** — everything that happened while you weren't watching, filed in order of how badly it wants your attention. Empty sections are simply not drawn, so a quiet day produces a short page and a certain amount of relief:

1. **Heroes Lost**
2. **World Boss**
3. **Scandals**
4. **New Titles Earned**
5. **Auto-resolved Guild Events**
6. **Quest Chain Progress**
7. **Social**
8. **Crafts Completed**
9. **On the Ward** — infections, recoveries, chronic traits granted, and anyone the illness finished off ([Illness system](heroes.md#illness--chronic-traits))
10. **Quarters** — couples who moved in together and pairs the nightly pass moved apart ([Cohabitation](guild.md#cohabitation))
11. **Elsewhere** — what each absent hero claimed to be doing and what it cost them, plus anyone who bought what they were saving for or retired on the strength of it ([Purse & Ambition](heroes.md#purse--ambition))

Fatal news goes at the top and routine record-keeping at the bottom, on the principle that the ward report should not have to compete with a funeral.

---

## Mission Board

Access dungeons and contracts here. The Mission Board opens on a **World Map**, with every contract pinned to the place where it intends to go wrong.

### Mission List

Each mission entry shows what you're getting into — before you commit to getting into it:
- Mission name and type
- Star rating (the dungeon's opinion of its own difficulty)
- Monster level (the dungeon's opinion of yours)
- Reward preview (the reason for all of this)
- Time limit (if any)

### Filters

The Mission Board carries a three-button filter strip, for the days when nine contracts is eight too many to read:

- **All** - Both regular and heroic missions
- **Normal** - Regular missions, the bread and butter of guild operations
- **Heroic** 🔥 - Heroic dungeons, for guilds that have run out of interesting problems

### Chain Step Badge

Missions belonging to a [quest chain](quest-chains.md) carry a **📜 badge** and a tooltip naming the chain and the step (e.g., *"The Goblin Menace — Step 1/4"*). They behave like regular missions on the board — same dispatch flow, same success/failure rules — but completing them advances the chain and unlocks the next step for tomorrow's board.

### Hazard Badge

Missions at 2★ and higher can carry an **environmental hazard** ([Environmental Hazards](dungeons.md#environmental-hazards)) naming the class(es) that resolve it cleanly (e.g., *"Toxic Gas Cloud — Cleric"*). Hazards are listed in the **Contract Details side panel** below the description and requirements — the world-map pins themselves only carry chain (📜) and heroic (🔥) badges, not hazard badges. Bring the named class to handle the hazard cleanly; otherwise the party pushes through and pays for it.

### Starting a Mission

1. Select a mission
2. Form your party (drag heroes onto the slots)
3. Press **Dispatch**

The **success chance** shown beside the party is not an estimate in the loose sense. The realm runs the fight **20 times** through the very same resolution the dispatch will use, and reports how many of those runs came home. It is therefore as honest a number as anyone could ask for, which is not at all the same as a comforting one — a hero who dies in fourteen of twenty rehearsals will not be persuaded otherwise by the fifteenth.

The unsupervised/supervised distinction (and Command Point spending) is set on the dungeon-menu side of expedition launches, not on the Mission Board itself.

---

## Quest Log

The **Quest Log** button (glyph **❡**) sits in the **Top Bar** alongside the other icon buttons — not in a sidebar — and is visible from day one. It tracks every story chain, class chain, and weekly bounty that is currently *active, available, expiring, or completed*.

### Tabs

- **Story** - **Seven** long-form campaigns gated by guild rank (F → B)
- **Class** - **Seven** class chains across the six classes (Mage has two: The Arcane Thesis at rank E + level 25, and The Archmage's Thesis at rank C + level 40)
- **Weekly** - The current weekly bounty with its ⏰ 7-day countdown (the first bounty rolls on **day 1** — the realm wastes no time finding you errands)

The Quest Log UI only enumerates **unlocked** chains — locked chains do not appear with their unlock requirements; if no chain of a type is unlocked, the panel shows a short note to that effect rather than a list of mysteries. Active chains show the current step and finale reward. Completed chains are archived for the record.

→ **Full details:** [Quest Chains](quest-chains.md)

---

## Hero Details

When you select a hero, you get a comprehensive view of everything they are, everything they own, and everything they've done. It is, in the Guild Clerk's opinion, the most informative screen in the game.

Down the right-hand side, beneath Active Effects, the **Mood** panel shows its working: every thought the hero is carrying, sorted by how much it weighs, each with its stack count, its days remaining (or *ongoing*), and its signed value — and a footer doing the sum out loud, `Base 50 · Thoughts ±N · Title ±N = mood`, with *(capped)* appended when the arithmetic ran off either end of the 0–100 scale. A hero with nothing on their mind gets the line *"No active thoughts. The head is, briefly, an empty hall."*

The tabs:

### Gems Tab

Where the real build optimization happens. Heroes have been known to spend more time arranging gems than actually fighting.

- Equipped skill gems and sockets
- Gem levels and XP progress
- Skill proficiency levels
- Socket management (drag gems to sockets)

### Social Tab

The tab that explains why your Rogue refuses to party with your Warrior. Essential reading before forming expedition teams.

- Relationships with other heroes (per-hero trust, bond labels, current modifier)
- Active thoughts (mood-affecting reactions to recent events)

Mood, traits, and needs are surfaced on the main hero panel rather than this tab.

### Career Tab

The Career tab exists because the Guild Clerk wanted receipts.

- **Purse & Ambition** — at the top: what the hero is holding, what they earn a day, and a progress bar toward the thing they are privately saving for, captioned in their own words. A "saved enough" marker appears when the fund fills, and a line beneath it says whether that means *Bought* or *Enough to leave the guild*. Underneath, **Things they saved for** lists everything they have already bought, each chip carrying its permanent effect. See [Purse & Ambition](heroes.md#purse--ambition)
- Mission history and statistics
- Veteran rank and progress
- Monster knowledge levels
- Combat lifetime stats

### Stats Tab

The hero sheet: what this hero is actually worth in a fight, after everything has been counted. Primary stats (**STR / DEX / INT / VIT / LCK**) sit above the derived ones — **ATK**, **CRT%**, **Crit DMG**, **Armor**, **Evasion**, **Energy Shield**, **Life Steal** — and the two out-of-combat modifiers, **Gold Find** and **XP Bonus**.

The crit figures here are worth trusting: combat rolls crit through the same functions this sheet reads, so the percentage shown is the percentage the dice are given. See [Critical Hits](combat.md#critical-hits). Everything on this tab is the *effective* value — gear, passives, ascendancy, paragon, titles, mood, illness and the hero's own life history are already in the numbers, which is why they rarely match the figures on the items.

### Chronicle Tab

The hero's running history. Major fights, lost friends, milestones, titles earned — the entries that decide which titles unlock. The tab carries an unread badge when a new entry has arrived since you last looked.

### Background Tab

The hero's static identity — who this person is, before any of the bonds, achievements, or unfortunate encounters with the dungeon system got involved. The tab holds the four life paragraphs and the modifiers quietly attached to them; the Chronicle handles the running record, the Background handles the origin. See [Hero Backgrounds](backgrounds.md) for the full system.

- **Origin** — the hero's background tag and its mechanical effect
- **Life paragraphs** — childhood, adolescence, young adulthood, before the guild
- **Marks of a Life** — body flaws picked up along the way
- **Traits** — named traits the lifecycle gave them (Duelist, Sickly, and the rest of that family)

**Paragon** and **Trials** tabs sit alongside the above for every hero, qualified or not — the tabs are always there, and the contents will tell you, with varying degrees of tact, whether this particular hero has any business being in them. The Guild Clerk maintains that fitting all of this onto a single screen is a polite fiction and that anyone who reads everything before issuing orders is doing the job properly.

---

## Combat Screen

During supervised expeditions, everything important is visible at once. The Guild Clerk designed this screen on the assumption that things would be happening quickly, and was correct.

### Turn Order (Top)

Shows who acts next, which is the most important question in any combat:
- Current actor highlighted
- Heroes vs enemies — the two factions, with their relative health
- Status effects visible; the icons are small but the effects are not

### Battle Area (Center)

The fight itself, laid out clearly so there are no excuses:
- Your party on left
- Enemies on right
- Health bars above each combatant — watch these
- Status effect icons below health bars

### Combat is AI-driven

Hero's Guild combat has no Attack / Skill / Defend / Flee buttons. Once the fight starts, the heroes choose their own skills, guided by their tactical presets and their own judgement, which is about what you'd expect. Your influence is everything you did *before* the first swing — party composition, equipment, tactics, supervision — and the Guild Clerk notes that this is also how real management works. The bar along the bottom of Hero Details (Passive Tree / Spec / Body / Food / Rest / Dismiss) looks a bit like a combat bar and is nothing of the sort: it manages heroes, not fights.

### Combat Log (Side)

A record of what just happened, in case you weren't watching closely enough:
- Damage numbers
- Skill usage
- Status effects applied
- Hero dialogue, which is occasionally informative and frequently theatrical

### Command Points

Command Points are a dungeon-exploration resource (visible on the Dungeon screen, not the Combat screen) that the Guild Master spends to issue interventions during a supervised expedition. They do not appear on the per-fight combat panel.

---

## Dungeon Exploration

When exploring dungeons:

### Map View

- Fog of war (unexplored = dark)
- Room icons show type
- Current position marked
- Connections visible

### Room Types

| Icon | Type | Notes |
|------|------|-------|
| 🚪 | Entrance | Where optimism is at its peak |
| ⚔️ | Combat | The main attraction, whether you wanted it or not |
| 💎 | Treasure | The reason anyone's here |
| ⚠️ | Trap | The reason anyone's limping |
| 🏕️ | Rest | Popular after the trap |
| ❓ | Event | Something other than combat. Could be better. Could easily be worse. |
| 🏪 | Shop | A merchant who got here somehow and considers this a normal place to work |
| 👹 | Boss | The thing guarding the good loot |
| 🔍 | Secret | Not on the map. Finding it is half the reward. |
| ⬇️ | Stairs | Progress, or the illusion of it |
| 🏁 | Exit | The room everyone is looking for |

---

## Inventory Management

### Guild Vault

Central storage for all items — a carefully catalogued system that heroes will bypass in favor of whatever's shiniest. The vault offers six type filters: **All / Weapons / Armor / Accessory / Consumables / Materials**, plus bulk actions.

### Item Actions

- **Equip** - Assign to hero (can also be done by dragging, which heroes always manage to do accidentally)
- **Sell** - Convert to gold (also available as a bulk-mode toggle). If any living hero carries the **Merchant** background, the highest-level of them handles the transaction and their sell-price bonus applies; the preview, the panel and the toast all name whoever is doing the haggling, so you can see the difference a Merchant makes before you agree to it
- **Salvage** - Get materials (also available as a bulk-mode toggle)

Enchanting is not a per-item vault action — it lives in the Workshop (Enchanting Table facility). Open the workshop and bring the item there.

---

## Crafting Interface

At any crafting station:

### Recipe List

- Available recipes
- Required materials (✓ or ✗)
- Skill requirement
- Expected quality range

### Crafter Assignment

- Assign hero to station
- View skill level
- Estimated time
- Add assistant option

### Queue

- Current craft progress
- Queued items
- Cancel option

---

## Keyboard Shortcuts

The interface is mouse-first, and the keyboard is mostly decorative. **Escape** does not close whatever happens to be open; it dismisses the smaller dialogs — confirmations, the save/load window, the Quarters pickers and their relatives — cancels a group rename in raid setup, and dismisses the credits reel. **Any key at all** skips the intro video, which is the one place the game is entirely relaxed about what you press. Settings, Achievements, and Beta Chat must be closed with their close buttons, like doors in a well-run building.

The **Custom Dungeon editor** is the exception, being a place where people do actual work: **Escape** steps back out of whatever you were doing (patrol placement first, then the active tool, then the selection), and **Delete** or **Backspace** removes the selected room or corridor without asking whether you're sure. Architects learn to be sure.

The raid screen is the other exception: number keys **1–6** select groups and **Escape** cancels the selected group's queued order — see [World Boss Raids](raids.md#the-raid-interface). A few other screens hide right-click shortcuts (Mission Board, Passive Tree, Dungeon Menu), for those who like to poke things and see what happens.

---

## Quick Tips

Small things that make a significant difference, provided for heroes who prefer to learn from documentation rather than experience:

1. **Hover for tooltips** - Most elements have explanations; the game assumes you will use this
2. **Try right-clicking on a few screens** - The Mission Board, Passive Tree, and Dungeon Menu use right-click for niche shortcuts; the rest of the UI is left-click only
3. **Drag and drop** - Equipment, party formation, and gem management all support this
4. **Watch the log** - Combat details and events scroll past quickly; the important ones scroll past quickest
5. **Check notifications** - Red dots indicate something needs attention; they do not go away on their own

---

## Settings

### Audio

- Master Volume (0-100) — controls everything, as the name implies
- Music Volume (0-100) — the guild ambient music is quite pleasant, in the Guild Clerk's opinion
- SFX Volume (0-100) — the sounds of swords, spells, and heroes complaining

### Display

- Resolution dropdown (1280×720 / 1600×900 / 1920×1080 / 2560×1440) — the interface is drawn once, at 1920×1080, and then scaled to fit whatever you pick, so this is a size control rather than a detail control. Nothing extra appears at 2560×1440; the goblins are simply legible from further away. The window cannot be dragged to a new size — a fixed canvas can only be zoomed, and the edges have been nailed down accordingly — so the dropdown is the only handle there is. Desktop version only.
- Fullscreen toggle

### Gameplay

- Skip Intro Video (skip the opening cinematic on New Game — the Guild Clerk takes no position on this, but does note that the intro was expensive to produce)
- Show Advisor Tips (Quillsworth provides tips as you discover game systems — recommend leaving this on unless you enjoy learning things the hard way)
- Online Features (sends leaderboard stats and unlocks community dungeons)

### Leaving

Settings also holds the doors out: **⏏ Return to main menu** and, on the desktop build, **⏻ Quit game**, each behind a confirmation. **📥 Save game** appears only while a game is actually in progress, there being nothing to save from the main menu but your dignity. And **New Game** asks before it writes over your autosave, which is the sort of question one only learns to appreciate after the one time nobody asked it.

### Credits

- 🎬 Roll the credits — opens a cinematic end-credits reel that scrolls the names behind the tunes, the thumps, and the letterforms over the intro backdrop. Hover to pause; Escape or a click on the backdrop dismisses. Purely ornamental, but the people whose work is in the soundtrack deserve their moment.

---

## Related Guides

- [Getting Started](getting-started.md) - First steps
- [Guild Management](guild.md) - Facility details
- [Combat System](combat.md) - Combat mechanics

---

*"A well-organized guild starts with knowing your tools. An exceptionally well-organized guild also reads the documentation — but let's not get ahead of ourselves."*
