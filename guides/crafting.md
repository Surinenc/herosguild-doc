# Crafting System

Create powerful equipment, potions, and consumables for your heroes — assuming you can spare a hero from dungeon duty long enough to actually craft something. Crafting is a core progression system that lets you gear up without relying on the generous loot drops of monsters (who are, it must be said, not known for their generosity).

## Core Concepts

- **Heroes Craft** - Your heroes do the crafting, not NPCs. Yes, the same heroes who think "charge the dragon" is a valid strategy.
- **Opportunity Cost** - Crafting heroes can't go on expeditions. Choose wisely.
- **Skill-Based Quality** - Higher skill = better items. Lower skill = interesting explosions.
- **Recipe Discovery** - Find or research new recipes

---

## Crafting Stations

### Production Facilities

Ten crafting station types, each requiring a hero who could otherwise be doing something more immediately dangerous:

| Station | Crafts | Skills Used |
|---------|--------|-------------|
| **Forge** | Metal weapons, armor | Blacksmithing |
| **Armory** | Armor crafting and repair | Armorsmithing |
| **Tannery** | Leather processing and goods | Leatherworking |
| **Loom** | Cloth processing and items | Tailoring |
| **Alchemy Lab** | Potions and elixirs | Alchemy |
| **Kitchen** | Food buffs and meals | Cooking |
| **Enchanting Table** | Magic enhancements | Enchanting |
| **Jeweler Bench** | Jewelry and accessories | Jewelcrafting |
| **Lumber Mill** | Wood processing, bows, prosthetics | Leatherworking |
| **Smelter** | Ore processing, ingots | Blacksmithing |

### Station Levels (Base)

Each crafting station has an internal level that reduces crafting time by 10% per level and unlocks material tiers. At level 5, you also get a quality bonus, which is the game's way of rewarding patience — a virtue that, in the Guild Clerk's experience, is in desperately short supply.

| Level | Time Modifier | Tier Unlocked | Quality Bonus |
|-------|---------------|---------------|---------------|
| 1 | 1.0× (base) | ⭐ Common | - |
| 2 | 0.9× (-10%) | ⭐⭐ Uncommon | - |
| 3 | 0.8× (-20%) | ⭐⭐⭐ Rare | - |
| 4 | 0.7× (-30%) | ⭐⭐⭐⭐ Epic | - |
| 5 | 0.6× (-40%) | ⭐⭐⭐⭐⭐ Legendary | +5 to quality roll |

This applies uniformly to all 10 station types.

### Facility Upgrades (Stacking Bonuses)

Guild facility upgrades provide **additional** speed and quality bonuses on top of station-level modifiers. These are separate systems that stack.

**Forge Facility** (metals, weapons, armor):

| Level | Name | Speed | Quality Bonus |
|-------|------|-------|---------------|
| 1 | Simple Forge | 1.0× | - |
| 2 | Blacksmith Forge | 1.15× | - |
| 3 | Master Forge | 1.3× | +10% |
| 4 | Dwarven Forge | 1.5× | +20% |
| 5 | Legendary Forge | 2.0× | +30% |

**Workshop Facility** (leather, cloth, wood — covers Tannery, Loom, Lumber Mill stations):

| Level | Name | Speed | Quality Bonus |
|-------|------|-------|---------------|
| 1 | Basic Workshop | 1.0× | - |
| 2 | Crafting Workshop | 1.2× | +5% |
| 3 | Artisan Workshop | 1.4× | +10% |
| 4 | Master Workshop | 1.6× | +15% |
| 5 | Grand Workshop | 2.0× | +20% |
| 6 | Mythic Workshop | 2.5× | +30% |

**Alchemy Lab Facility** (potions, elixirs):

| Level | Name | Speed | Potency Bonus |
|-------|------|-------|---------------|
| 1 | Brewing Station | 1.0× | - |
| 2 | Alchemy Corner | 1.2× | - |
| 3 | Alchemy Lab | 1.4× | +10% |
| 4 | Grand Laboratory | 1.6× | +20% |
| 5 | Arcane Laboratory | 2.0× | +30% |

**Enchanting Table Facility** (enchantments, jewelry):

| Level | Name | Enchant Power |
|-------|------|---------------|
| 1 | Rune Desk | 1.0× |
| 2 | Enchanting Altar | 1.2× |
| 3 | Arcane Workshop | 1.4× |
| 4 | Mystic Chamber | 1.7× |
| 5 | Ley Nexus | 2.0× |

### Unlocking Stations

Some stations require facility unlock missions (see [Dungeons Guide](dungeons.md)):
- Forge: "The Wandering Smith"
- Alchemy Lab: "Mysterious Ingredients"
- Enchanting Table: "Arcane Secrets"

---

## Hero Crafting Skills

Heroes level up crafting skills by crafting. There is no shortcut, no cheat, and no amount of motivational speeches that will substitute for actually making things:

| Skill | Max Level | Governs |
|-------|-----------|---------|
| Blacksmithing | 100 | Metal weapons/armor |
| Armorsmithing | 100 | All armor types |
| Leatherworking | 100 | Leather goods |
| Tailoring | 100 | Cloth items |
| Alchemy | 100 | Potions |
| Enchanting | 100 | Magic enhancements |
| Jewelcrafting | 100 | Accessories |
| Cooking | 100 | Food buffs |

### Skill Level Effects

| Skill Level | Recipes Unlocked | Success Rate | Quality Bonus |
|-------------|------------------|--------------|---------------|
| 1-20 | ⭐ | 70% | -10% |
| 21-40 | ⭐⭐ | 80% | +0% |
| 41-60 | ⭐⭐⭐ | 85% | +5% |
| 61-80 | ⭐⭐⭐⭐ | 90% | +10% |
| 81-99 | ⭐⭐⭐⭐⭐ | 95% | +15% |
| 100 | Masterwork | 100% | +25% |

### Gaining Crafting XP

Crafting XP is based on item tier and level:

```
XP = Base × Item Level × 15
```

| Material Tier | Base XP |
|---------------|---------|
| Common (T1) | 10 |
| Uncommon (T2) | 25 |
| Rare (T3) | 50 |
| Epic (T4) | 100 |
| Legendary (T5) | 200 |

**Examples:**
- Common item (L5): 10 × 5 × 15 = 750 XP
- Rare item (L30): 50 × 30 × 15 = 22,500 XP

Exceptional quality crafts give +50% XP.

---

## The Crafting Process

### Step by Step

1. **Select Recipe** - Must have recipe unlocked
2. **Assign Crafter** - Hero with appropriate skill
3. **Check Materials** - Must be in guild vault
4. **Queue Craft** - Production begins
5. **Wait** - Time based on item tier
6. **Completion** - Quality rolled, item created

### Crafting Time

| Item Tier | Base Time |
|-----------|-----------|
| ⭐ | 2 hours |
| ⭐⭐ | 6 hours |
| ⭐⭐⭐ | 1 day |
| ⭐⭐⭐⭐ | 3 days |
| ⭐⭐⭐⭐⭐ | 7 days (10,080 min) |

**Time Modifiers:**
- Station level: -10% per level above 1 (see Station Levels table)
- Crafter skill: -1% per 5 skill levels (skill level / 500)
- Assistant: -20%

### Assistants

Each station can have:
- 1 primary crafter (full XP, does the actual work)
- 1 assistant (+20% speed, 50% XP, does whatever the primary crafter doesn't want to do)

The assistant system is, in the Guild Clerk's opinion, an excellent way to keep idle heroes out of the Tavern.

---

## Quality System

When crafting completes, quality is rolled:

| Roll | Quality | Stat Modifier |
|------|---------|---------------|
| 1-10 | Poor | -20% |
| 11-30 | Normal | +0% |
| 31-60 | Fine | +10% |
| 61-85 | Superior | +20% |
| 86-95 | Exceptional | +30% |
| 96-100 | Masterwork | +50% |

**Roll Modifiers:**
- Higher skill level adds to roll
- Better station adds to roll
- Masterwork skill (100) guarantees 50+ roll
- Assistant adds +5

### Crafting Failures

Low skill crafters can fail, with consequences ranging from "mildly disappointing" to "where did the Forge go?":

| Result | Effect |
|--------|--------|
| Success | Item created |
| Partial Fail | Item at -1 quality tier |
| Full Fail | 50% materials lost |
| Critical Fail | All materials lost, station damaged |

---

## Recipes

### Recipe Sources

| Source | Recipe Tiers | How to Get |
|--------|--------------|------------|
| Starting | ⭐ basic | Begin with these |
| Library Research | ⭐ to ⭐⭐⭐ | Research time + materials |
| Merchant Purchase | ⭐ to ⭐⭐⭐ | Buy from traders |
| Mission Rewards | ⭐⭐ to ⭐⭐⭐⭐ | Quest completion |
| Boss Drops | ⭐⭐⭐ to ⭐⭐⭐⭐ | Kill bosses |
| World Boss Drops | ⭐⭐⭐⭐⭐ | Kill world bosses |

**Important:** ⭐⭐⭐⭐ and ⭐⭐⭐⭐⭐ recipes CANNOT be researched - they must be found!

### Library Research

Research new recipes at the Library:

**Requirements:**
- Library facility (level determines max tier)
- Hero assigned as researcher
- Research materials
- Time

| Library Level | Max Research Tier | Speed Bonus |
|---------------|-------------------|-------------|
| 1 | ⭐ | +0% |
| 2 | ⭐⭐ | +10% |
| 3 | ⭐⭐⭐ | +20% |

### Boss Recipe Drops

| Boss Type | Recipe Tier | Drop Chance |
|-----------|-------------|-------------|
| Dungeon Boss | ⭐⭐⭐ | 30% |
| Elite Boss | ⭐⭐⭐ to ⭐⭐⭐⭐ | 50% |
| Raid Boss | ⭐⭐⭐⭐ | 75% |
| World Boss | ⭐⭐⭐⭐⭐ | 100% unique |

---

## Materials

### Material Tiers

**Tier 1 - Common (⭐)**
- Wood, Iron Ore, Leather Scraps, Cloth, Herbs, Stone
- Source: Any dungeon, shops

**Tier 2 - Uncommon (⭐⭐)**
- Hardwood, Steel Ingot, Quality Leather, Silk, Rare Herbs
- Source: ⭐⭐+ dungeons

**Tier 3 - Rare (⭐⭐⭐)**
- Ironwood, Mithril Ore, Dragonhide, Mooncloth
- Source: ⭐⭐⭐+ dungeons, Level 30+

**Tier 4 - Epic (⭐⭐⭐⭐)**
- World Tree Branch, Adamantine, Phoenix Feather, Void Crystal
- Source: ⭐⭐⭐⭐+ dungeons, Level 50+, boss drops

**Tier 5 - Legendary (⭐⭐⭐⭐⭐)**
- Primordial Essence, God Tear, Eternity Shard
- Source: World bosses, Level 70+
- The sort of materials that make the Forge glow ominously when you bring them inside

### Processing Materials

Raw materials must be processed before use. The Guild Clerk has lost count of the number of heroes who've tried to craft a sword from unprocessed ore. It doesn't work. It has never worked.

**Metal Chain:**
```
Iron Ore → [Smelter] → Iron Ingot → [Forge] → Steel Ingot
  2 ore = 1 ingot          2 iron + 1 coal = 1 steel
```

**Leather Chain:**
```
Leather Scraps → [Tannery] → Leather → [Tannery] → Hardened Leather
  3 scraps = 1 leather         2 leather + 1 oil = 1 hardened
```

**Cloth Chain:**
```
Cloth → [Loom] → Fine Cloth → [Loom] → Enchanted Cloth
  3 cloth = 1 fine         2 fine + 1 essence = 1 enchanted
```

---

## Example Recipes

### Weapons

| Recipe | Tier | Materials | Skill Req |
|--------|------|-----------|-----------|
| Iron Sword | ⭐ | 3 Iron Ingot, 1 Wood | 1 |
| Steel Sword | ⭐⭐ | 4 Steel, 2 Hardwood | 25 |
| Mithril Blade | ⭐⭐⭐ | 5 Mithril, 2 Quality Wood | 50 |
| Dragonslayer | ⭐⭐⭐⭐ | Dragon Heart, 8 Adamantine | 75 |

### Armor

| Recipe | Tier | Materials | Skill Req |
|--------|------|-----------|-----------|
| Iron Plate | ⭐ | 5 Iron Ingot | 1 |
| Steel Plate | ⭐⭐ | 6 Steel Ingot | 25 |
| Mithril Mail | ⭐⭐⭐ | 8 Mithril, 4 Leather | 50 |
| Dragonplate | ⭐⭐⭐⭐ | 3 Dragonhide, 6 Adamantine | 75 |

### Potions

| Recipe | Tier | Materials | Skill Req |
|--------|------|-----------|-----------|
| Minor Health Potion | ⭐ | 2 Herbs, 1 Water | 1 |
| Health Potion | ⭐⭐ | 3 Rare Herbs, 1 Vial | 25 |
| Greater Health Potion | ⭐⭐⭐ | 5 Alchemical Essence | 50 |
| Superior Health Potion | ⭐⭐⭐⭐ | 3 Void Crystal, Phoenix Feather | 75 |

### Prosthetics

| Recipe | Tier | Materials | Skill Req |
|--------|------|-----------|-----------|
| Peg Leg | ⭐ (Basic) | 3 Hardwood, 2 Leather, 1 Iron | Leatherworking 5 |
| Prosthetic Leg | ⭐⭐ (Standard) | 5 Steel, 2 Hardened Leather | Blacksmithing 10 |
| Enchanted Leg | ⭐⭐⭐ (Enhanced) | 2 Adamantine, Dragon Bone, 2 Soul Shard | Enchanting 15 |

---

## Item Workshop

The Item Workshop lets you reroll the bonus stats on equipment without crafting a new item. This is useful for improving Rare+ items that have good base stats but poor bonus rolls — a situation that occurs with frustrating regularity.

**Requirements:**
- Item must be Rare rarity or higher
- Named items cannot be rerolled

**Reroll Cost:**
```
Cost = 1,000 × Rarity Tier × 2^(Previous Rerolls)
```

Costs double each time you reroll the same item. You can preview the new stats and choose to Accept or Reject before committing.

Navigate to: Guild Screen → Item Workshop

---

## Tips for Efficient Crafting

### Early Game

1. **Focus One Crafter** - Level one hero's crafting skill fast. A jack-of-all-trades crafter is a master of none, and a producer of Poor-quality swords.
2. **Process Materials** - Keep raw materials processed
3. **Unlock Stations Early** - Do facility missions ASAP
4. **Research Basic Recipes** - Library is worth the investment

### Mid Game

1. **Specialize Heroes** - Different heroes for different skills
2. **Use Assistants** - Speed bonus adds up
3. **Hunt for Recipes** - Boss dungeons for better blueprints
4. **Quality Matters** - Wait for high-skill crafters

### Late Game

1. **Masterwork Crafters** - Level 100 for guaranteed quality
2. **Farm World Bosses** - Legendary recipe sources
3. **Enchant Everything** - Max out your gear
4. **Prosthetics** - Replace destroyed body parts

---

## Crafting Station Recommendations

### Per Hero Count

| Heroes | Priority Stations |
|--------|-------------------|
| 3-5 | Forge, Alchemy Lab |
| 6-10 | + Tannery, Kitchen |
| 10+ | + Enchanting, Jeweler |

### Per Guild Focus

| Focus | Priority |
|-------|----------|
| Combat | Forge, Alchemy Lab |
| Exploration | Kitchen, Alchemy Lab |
| Crafting Empire | All stations maxed |

---

## Related Guides

- [Equipment & Items](equipment.md) - What you can craft
- [Heroes & Classes](heroes.md) - Hero states and assignment
- [Guild Management](guild.md) - Facility upgrades

---

*"A well-equipped guild is a successful guild. A well-equipped guild that also remembers to pay its crafters is an exceptional one."*
