# Getting Started with Hero's Guild

Welcome to Hero's Guild. You've inherited a building, a modest pile of gold, and the vague expectation that you'll fill it with adventurers and somehow make a profit. This guide is short on purpose — it covers the strategic layer. The game itself will walk you through the individual screens as you open them; **Quillsworth's in-game tutorial** will explain each screen the first time you visit. What you're reading here is the pattern you can't learn from a single screen.

## The mental model

You are not a hero. You are the Guild Master — the person who signs contracts, pays wages, and writes the funeral invoices. The heroes fight; your job is administrative. This is a management sim wrapped in fantasy trappings.

The core loop: **recruit → equip → dispatch → manage what comes back → advance the day → repeat.** Every mechanic in the game exists to complicate one of those five verbs.

## The three resources

Three things will make or break your guild. Ignore any one of them and the Guild Clerk will be writing your closure report.

### Gold

Pays for daily upkeep on every unlocked facility and daily wages on every hero at **level 2 or above** (level-1 heroes are freshers and cost nothing until they earn their second level). Wages scale exponentially with hero level and hero quality — a level-100 Legendary hero costs orders of magnitude more per day than a level-10 Common.

It also pays for recruitment fees, contract fees, gear, potions, tavern nights and buildings — which is to say for everything, all of it, continuously.

**Gold leaves faster than it arrives.** This is normal. This is also terrifying.

It is terrifying for a concrete reason: the guild can go **into debt**. An unaffordable night is not written off — it is carried, in red. You get a warning the night you first go negative and a firmer one at **-3,000**, and at **-5,000** the run is over. See [Debt, and the End of It](guild.md#debt-and-the-end-of-it).

### Materials

Spent at the production facilities on equipment, potions and consumables; gathered from mission drops, merchant caravans and the patient business of picking things up. Running out mid-craft is the guild equivalent of running out of flour mid-cake.

### Time (days)

**The invisible one.** The clock is always moving. Every day: wages tick, the Mission Board's contracts expire and new ones appear, merchants restock, hero lifecycles age, events fire whose windows may close. You cannot pause. A day where you do nothing costs you wages and progresses events you'd rather have attended to.

Guilds that fail usually fail because their master treated time as background rather than as currency. It is neither more nor less real than gold.

**Hero mood** is not a shared resource — it's a per-hero attribute — but it interacts with all three. Unhappy heroes fight poorly and eventually leave. Happy heroes merely complain about the food.

## The three (and a half) rules that will save your guild

### 1. Party balance always beats party size

Send tank + damage + healer + one flex. The Guild Clerk has watched hundreds of new masters send four damage dealers into a dungeon with no healer. Every one of them then spent gold they didn't have on a memorial. **Balance beats power** for the first ~30 hours of play.

### 2. Barracks first, then the Guild Hall

Heroes judge their beds long before the beds run out. The Barracks starts to feel crowded at half full, and once three-quarters of the beds are taken every hero sleeping there carries a standing *"These beds are terrible"* — a mood penalty that lasts exactly as long as the crowding does and goes with them into every fight. An upgrade fixes it twice over: more beds, so the same roster has room to breathe, and better ones, worth **+5 comfort** a level, so they mind less. Level 2 costs **2,000 gold plus 30 wood and 20 stone** and two days, which makes it the cheapest happiness in the guild.

Then the **Guild Hall to level 2**: it doubles your mission slots from two to four, and with them your income, for **5,000 gold plus 50 wood and 30 stone** and three days.

The **Forge**, the **Alchemy Lab** and the other crafting buildings start locked. While any of them are, the Mission Board always carries a two-star contract that unlocks the next one — take it whenever you have a spare party.

### 3. Consumables must be equipped to be useful

Potions in the Vault do nothing. Potions equipped in a hero's Consumable slot are drunk automatically when the hero drops below 50% HP (mana flasks at 30%, antidotes when poisoned). Configurable in **Settings → Combat** if the defaults don't suit you.

### 3½. Do not neglect relationships

You'll notice by day 20 that some pairs of heroes always volunteer for the same mission and others quietly try to avoid each other. Bonds and rivalries **directly affect combat performance** — bonded pairs fight better, rivals fight worse. The Tavern's nightly activities exist to shape these. Ignoring them is expensive.

## The four combat modes — know which door you're walking through

- **Missions** — contracts from the Mission Board. Heroes depart at night, combat resolves offscreen. Guild income workhorse.
- **Dungeons** — real-time interactive expeditions. You control the party as they explore. Slower, more control.
- **Raids** — 15-hero endgame fights. Once you have 5,000 reputation and a level-50 hero, a world boss may appear; it arrives when it chooses, which is never convenient.
- **The Abyssal Spire** — endless tower. Unlocks when one hero reaches level 95. A Tower run advances the game day.

New guilds should stay on 1-2 star Missions and shallow Dungeons for the first 5-10 hours. Everything else is post-endgame content that will kill your heroes if you knock on the door early.

## Common early mistakes

The Guild Clerk has seen every one of these. Multiple times. Sometimes in the same week.

1. **Overextending.** The star rating on a mission is a suggestion, not a promise of survival. When in doubt, take an easier one.
2. **No bench for the wounded.** An injured hero cannot be sent anywhere until they have mended, and neither can one who is resting, training or in the middle of a mental break. A guild with exactly one party's worth of heroes finds this out the morning after its first bad night.
3. **No bench depth.** Deaths happen. Injuries happen. Plan on running two rotating parties eventually so one is always ready while the other is healing.
4. **Hoarding gold.** Gold in the vault does not fight dragons. Invest in facility upgrades and better gear.
5. **Neglecting the Tavern.** Not the drinks — the relationships. Bonds and rivalries decide who fights well together.

## Systems you'll meet in your first few hours

Each of these will appear without introduction. Each has its own guide.

- **[Chronicle](heroes.md)** — every hero has an auto-generated journal recording what they've done, refused, been party to, or fled from. Check it before you fire someone.
- **Prosthetics** — heroes who lose limbs, eyes, or (yes) internal organs can have them replaced. See [equipment](equipment.md).
- **[Passive Tree](passive-tree.md)** — every hero has a passive progression tree they allocate as they level.
- **[Ascendancy](ascendancy.md)** — at higher levels, heroes can undertake trials to specialise further.
- **[Skill Gems](skills.md)** — active + support gems socketed into gear grant heroes stronger, mana-costing skills on top of their native class abilities.
- **[Guild Identity + Crises](crisis.md)** — the guild has moral axes that swing based on your choices. Certain positions can trigger realm-wide crises.
- **[Recipe Research](crafting.md)** — most craft recipes must be researched at the Workshop before you can craft them.

## Next steps

Once you're comfortable with the loop:

- [Heroes & Classes](heroes.md) — the six hero classes, backgrounds, and traits
- [Combat System](combat.md) — turn order, threat, status effects, tactical presets
- [Equipment & Items](equipment.md) — gear, gems, rarity, sockets
- [Guild Management](guild.md) — facilities, upkeep, guild rank, reputation

Endgame gates, when you get there:

- [Heroic Dungeons](heroic-dungeons.md) — weekly modifier-laden challenges
- [Abyssal Spire](tower.md) — endless tower, unlocks at hero level 95 (each run advances the game day)
- [World Boss Raids](raids.md) — 15-hero raids; a world boss can appear once you have 5,000 reputation and a level-50 hero

---

*Good luck, Guild Master. The heroes are waiting, the dungeons are full, and the Tavern tab is already running. The rest — how to click through each screen, when to build what, why that hero is in a mood — the game will tell you as it happens. Your job is to remember what you're doing when it does.*
