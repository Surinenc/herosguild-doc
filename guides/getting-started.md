# Getting Started with Hero's Guild

Welcome to Hero's Guild! You've just inherited a building, a modest pile of gold, and the vague expectation that you'll fill it with adventurers and somehow make a profit. This guide will help you get started on your journey to build the greatest guild in the realm — or at least one that stays solvent.

## First Launch

When you start Hero's Guild for the first time, you'll be greeted with the main menu. Select **New Game** to begin your adventure.

### Your Starting Roster

You begin with **500 gold** and three pre-recruited heroes already on the books — a Warrior, a Mage, and a Cleric. The Warrior and Mage arrive with starter weapons; the Cleric arrives armed with optimism.

This baseline gives you a tank/DPS/healer triangle from day one. Visit the **Tavern** to expand your roster. When you do, consider whether you need:

- **A second damage dealer** (Rogue or Ranger) — to share the workload, or take risks the Mage shouldn't
- **A Necromancer** — minion-based playstyle for players who like passive damage
- **A second Cleric** — redundancy is rarely a luxury when injuries pile up

Recruiting more heroes is always possible as you earn gold — though you'll quickly discover that "earning gold" and "spending gold on hero wages" exist in a delicate and somewhat adversarial relationship.

## The Guild Screen

The Guild Screen is your home base — the single screen you'll spend most of your career staring at with either satisfaction or mounting concern. From here:

- **View your heroes** - See all recruited heroes, their stats, and current state of health (physical and emotional)
- **Manage facilities** - Build and upgrade guild buildings, each of which costs more than you'd like
- **Access the tavern** - Recruit new heroes, who will immediately start costing you money
- **Check the mission board** - Find dungeons to explore and contracts to accept
- **Open the quest log** - Track story chains, class chains, and weekly bounties (a new bounty rolls every 7 days; the first one appears on **day 1** per `QuestChain.test.ts:794-809`)
- **Open the shop** - Buy and sell items; the prices are not negotiable, but the regret is optional

### The Facilities Screen

The Facilities screen lists **fourteen** buildings in total, organised into four categories. Not all of them will make sense to a new Guild Master on Day One, but you should at least know they exist so you don't panic when the panel opens.

**Core (8):** Guild Hall, Barracks, Tavern, Training Yard, Infirmary, Armory, Warehouse, Shop
**Production (4):** Forge, Workshop, Alchemy Lab, Enchanting Table
**Support (2):** Library, Chapel

The Guild Clerk's recommended early priority is **Barracks first** (more heroes), then **Forge** (better equipment), then **Alchemy Lab** (potions save lives). The rest can wait until you've stopped bleeding gold.

A few consolidations worth flagging, in case older guides confused you:

- The **Kitchen** is not a separate building; food and drink production live under the **Alchemy Lab**.
- The **Tannery**, **Loom**, and **Lumber Mill** all live under the **Workshop** these days.
- The old **Vault** for items is now the **Armory**; the new **Warehouse** stores materials.

The Facilities screen also has buttons that lead into two related sub-systems — **Hero Quarters** (private rooms, decorations, adjacency bonuses) and the **Materials Market** (buy and sell crafting materials with dynamic pricing). They're not part of the upgrade ladder, but you'll spend time in both.

## Missions, Dungeons, Raids and the Tower — the four combat modes

Before your first fight, know which door you're walking through. Hero's Guild has **four separate combat modes**, and new Guild Masters routinely confuse them:

- **Missions** — contracts posted on the **Mission Board**. You assign heroes, they depart at night, they resolve while you continue your day. Simulated combat with a result report. This is the workhorse of guild income.
- **Dungeons** — real-time interactive expeditions accessed from the **Dungeon** screen. You control the party as they move room-to-room, encounter combat, treasure, moral events, and bosses. Slower than missions but you have direct control.
- **Raids** — 15-hero fights against realm-scale bosses. Unlock at **5,000 reputation and at least one level-50 hero**. See the [raid guide](raids.md).
- **Endless Tower** (the **Abyssal Spire**) — a floor-by-floor endurance challenge. Requires **at least one level-95 hero** and — importantly — **a run of the Tower advances the game day by one on completion**. Plan around that; Tower runs are not free-time.

New guilds should start with 1-2 star **Missions** or shallow **Dungeons**. Everything else is post-endgame.

## Your First Dungeon

Ready for adventure? (The heroes certainly think they are.) Head to the **Mission Board** and select a low-difficulty dungeon (1-2 stars). If a mission is marked with a **📜 badge**, it's the first step of a [quest chain](quest-chains.md) — completing it unlocks the next step on tomorrow's board.

### Selecting Your Party

The Guild Clerk has onboarded hundreds of Guild Masters. Every single one has, at some point, sent a party of four damage dealers into a dungeon with no healer. Don't be that Guild Master.

- Choose 3-4 heroes for your expedition
- Balance your team with tank, damage, and support roles
- Check that heroes are healthy (not injured or exhausted)

### Dungeon Exploration

Dungeons consist of multiple rooms connected by corridors. What's behind each door is a surprise — and not always a pleasant one:

- **Enemies** - Combat encounters (the main attraction, whether you want it or not)
- **Treasure** - Loot chests with items and gold (the reason you're here)
- **Events** - Random encounters that may help or hinder (the universe rolling dice)
- **Shops** - Merchants selling supplies (at dungeon markup prices)
- **Boss** - Powerful enemies with better rewards (the thing standing between you and going home)

### Combat Basics

Combat is turn-based with these key mechanics:

1. **Initiative** — determines turn order (higher is faster)
2. **Attack** — use basic attacks or skills to damage enemies
3. **Defend** — reduce incoming damage
4. **Skills** — powerful abilities with various effects

Target weaker enemies first, use your tank to draw aggro (threat), and keep your healer ready. If this sounds simple, the Guild Clerk assures you it will feel considerably less simple when three goblins are hitting your Mage.

A few things happen in combat that new Guild Masters often don't recognise on their first fight:

- **Skill gems** socketed into gear grant heroes their active and support skills. A hero with an empty weapon socket-group is missing a skill they could otherwise be using; see the **Vault** to socket one.
- **Health potions** in a hero's Consumable slots are drunk automatically when the hero drops below 50% HP. Mana Flasks trigger below 30%. **Antidotes** trigger when a hero is poisoned. Equip these before missions or the hero cannot use them.
- **Threat** is a hidden number. Tanks generate more of it; enemies attack the highest-threat visible target. If your Mage is being hit, either the tank isn't Defending or the Mage's Fireball made enemies angry enough to override the tank's threat.
- **Status effects** — poison, bleed, burn, stun, freeze — tick every turn. Some can be prevented with resistances on gear. Poison can be cleared mid-fight with an Antidote in a Consumable slot.

You don't need to master any of this on Day One. You do need to know these systems exist, because they will kill your heroes long before you notice them.

## After the Dungeon

Upon returning to the guild (assuming they return — the Guild Clerk finds optimism useful but not guaranteed):

1. **Collect rewards** - Gold, items, and experience
2. **Heal injuries** - Injured heroes need rest or medical attention
3. **Manage mood** - Exhausted heroes may need a break
4. **Equip new gear** - Upgrade your heroes with found equipment
5. **Sell extras** - Vendor unwanted items for gold

## Progression Tips

### Early Game (Levels 1-20)

The Guild Clerk has coached hundreds of new Guild Masters through this phase. The ones who listen tend to keep their guilds.

- Focus on one strong party rather than many weak heroes. Four competent heroes outperform eight mediocre ones, and cost half the wages.
- Complete easy dungeons repeatedly to build resources
- Upgrade your Forge for better gear
- Save gold for emergency situations (wages, healing, that moment when three heroes need prosthetics simultaneously)

### Building Your Guild

The transition from "small band of adventurers" to "functioning institution" is where most guilds either flourish or discover what bankruptcy looks like.

- Hire diverse hero classes for flexibility — you'll need every class eventually
- Build relationships between heroes (they fight better together, and the Tavern bills are worth it)
- Invest in crafting facilities for better equipment
- Keep backup heroes in case of injuries — and there will be injuries

### Managing Resources

Three things will make or break your guild. Ignore any one of them and the Guild Clerk will be writing your closure report.

- **Gold** — pay daily upkeep on facilities and daily wages on **any hero at level 10 or above** (per `calculateHeroWages`; level 1-9 heroes are free until they earn their tenth level). Also pays for recruitment, contracts, items, and buildings. Gold leaves faster than it arrives. This is normal. This is also terrifying.
- **Time (days)** — the clock is always moving. Each day advances hero lifecycles, rotates the Mission Board, ages relationships, and re-rolls what merchants are selling. There is no pause. A day where you do nothing costs you wages and progresses events you might have preferred to attend to. **Time is the resource you can't buy more of.**
- **Materials** — craft equipment and consumables. Running out of materials mid-craft is the guild equivalent of running out of flour mid-cake.

**Hero Mood** is not a shared resource — it's a per-hero attribute — but it interacts with the three above. Unhappy heroes fight poorly, pick fights with each other, and occasionally leave. Happy heroes merely complain about the food.

## Common Mistakes to Avoid

The Guild Clerk has seen every one of these mistakes. Multiple times. Sometimes in the same week.

1. **Overextending** - Don't tackle dungeons beyond your level. The dungeon doesn't care about your ambition.
2. **Ignoring injuries** - Injured heroes perform poorly and may die. The Infirmary exists for a reason.
3. **No reserves** - Always have backup heroes ready. Injuries happen. Deaths happen. Planning prevents panic.
4. **Hoarding gold** - Invest in facilities and equipment. Gold in the vault doesn't fight dragons.
5. **Neglecting relationships** - Heroes with bonds fight better together. Heroes who hate each other fight worse — and occasionally fight each other.

## Systems You'll Encounter That This Guide Doesn't Cover Yet

The Quick Start above is enough to get you moving, but the game has several systems that will appear in your first few hours without introduction. Here's a two-line preview of each so nothing takes you by surprise:

- **Chronicle** — every hero has an auto-generated per-hero journal recording everything they've done, refused, been party to, or fled from. Check it before you fire someone.
- **Prosthetics** — heroes who lose limbs, eyes, or (yes) internal organs can have them replaced. Options range from "carved wooden leg" to "Octiron Cogitator." See [equipment](equipment.md).
- **Passive Tree** — every hero has a 354-node passive progression tree they allocate as they level. See [passive tree](passive-tree.md).
- **Ascendancy** — at higher levels, heroes can undertake trials to specialise further. Fourteen ascendancy paths total, 2-3 per class. See [ascendancy](ascendancy.md).
- **Skill Gems** — active + support gems socketed into gear grant heroes their combat abilities. See [skills](skills.md).
- **Guild Identity + Crises** — the guild has three moral axes that swing based on your choices. Certain axis positions can trigger realm-wide crises. See [crisis](crisis.md).
- **Recipe Research** — most craft recipes must be researched at the Workshop before you can craft them. See [crafting](crafting.md).

## Next Steps

Once you're comfortable with the basics:

- [Heroes & Classes](heroes.md) — learn about the 6 hero classes
- [Combat System](combat.md) — master tactical combat
- [Equipment & Items](equipment.md) — understand gear and gems
- [Guild Management](guild.md) — optimise your guild operations

Endgame, when you get there:

- [Heroic Dungeons](heroic-dungeons.md) — weekly modifier-laden challenges
- [Abyssal Spire](tower.md) — the endless tower, for parties with at least one level-95 hero (note: each Tower run advances the game day)
- [World Boss Raids](raids.md) — 15-hero raid fights, unlocked at 5,000 guild reputation and a level-50 hero

---

*Good luck, Guild Master. The heroes are waiting, the dungeons are full, and the Tavern tab is already running. Your adventure — and your accounting — awaits.*
