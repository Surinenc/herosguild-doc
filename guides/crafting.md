# Crafting System

Create powerful equipment, potions, and consumables for your heroes. Crafting is a core progression system that lets you gear up without relying on drops.

## Core Concepts

- **Heroes Craft** - Your heroes do the crafting, not NPCs
- **Opportunity Cost** - Crafting heroes can't go on expeditions
- **Skill-Based Quality** - Higher skill = better items
- **Recipe Discovery** - Find or research new recipes

---

## Crafting Stations

### Available Stations

| Station | Function | Skill Used |
|---------|----------|------------|
| **Forge** | Metal weapons & armor | Blacksmithing |
| **Tannery** | Leather goods, prosthetics | Leatherworking |
| **Loom** | Cloth items | Tailoring |
| **Alchemy Lab** | Potions & elixirs | Alchemy |
| **Enchanting Table** | Magic enhancements | Enchanting |
| **Jeweler's Bench** | Rings & amulets | Jewelcrafting |
| **Kitchen** | Food buffs | Cooking |
| **Smelter** | Process ore to ingots | - |
| **Lumber Mill** | Process wood | - |

### Station Levels

| Level | Benefit |
|-------|---------|
| 1 | Basic function |
| 2 | +10% speed, ⭐⭐ recipes |
| 3 | +20% speed, ⭐⭐⭐ recipes |
| 4 | +30% speed, ⭐⭐⭐⭐ recipes |
| 5 | +50% speed, ⭐⭐⭐⭐⭐ recipes, quality bonus |

### Unlocking Stations

Some stations require facility unlock missions (see [Dungeons Guide](dungeons.md)):
- Forge: "The Wandering Smith"
- Alchemy Lab: "Mysterious Ingredients"
- Enchanting Table: "Arcane Secrets"

---

## Hero Crafting Skills

Heroes level up crafting skills by crafting:

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

| Action | XP Gained |
|--------|-----------|
| Craft ⭐ item | 10 |
| Craft ⭐⭐ item | 25 |
| Craft ⭐⭐⭐ item | 50 |
| Craft ⭐⭐⭐⭐ item | 100 |
| Craft ⭐⭐⭐⭐⭐ item | 200 |
| Process materials | 5-15 |
| Exceptional quality | +50% XP |

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
| ⭐⭐⭐⭐⭐ | 7 days |

**Time Modifiers:**
- Station level: -10% per level above 1
- Crafter skill: -1% per 5 skill levels
- Assistant: -20%
- Efficient trait: -20%

### Assistants

Each station can have:
- 1 primary crafter (full XP)
- 1 assistant (+20% speed, 50% XP)

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

Low skill crafters can fail:

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

### Processing Materials

Raw materials must be processed:

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

## Tips for Efficient Crafting

### Early Game

1. **Focus One Crafter** - Level one hero's crafting skill fast
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

*"A well-equipped guild is a successful guild."*
