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

Crafting follows six steps in sequence. Missing any of them produces results ranging from nothing happening to an expensive pile of unusable materials:

1. **Select Recipe** - Must have the recipe unlocked; wanting the item is not sufficient
2. **Assign Crafter** - A hero with the appropriate skill who is not currently doing something else
3. **Check Materials** - Everything must be in the guild vault; the station does not improvise
4. **Queue Craft** - Production begins; the crafter is now unavailable for anything more urgent
5. **Wait** - Duration based on item tier ranging from hours to an entire week for Legendary items
6. **Completion** - Quality is rolled, the item is created, and you find out whether the wait was worth it

### Crafting Time

| Item Tier | Base Time |
|-----------|-----------|
| ⭐ | 2 hours |
| ⭐⭐ | 6 hours |
| ⭐⭐⭐ | 1 day |
| ⭐⭐⭐⭐ | 3 days |
| ⭐⭐⭐⭐⭐ | 7 days (10,080 min) |

**Time Modifiers:** Everything that can be done to reduce that 7-day Legendary wait:
- Station level: -10% per level above 1 (see Station Levels table)
- Crafter skill: -1% per 5 skill levels (skill level / 500); a level 100 crafter saves 20% before anything else
- Assistant: -20%; a second hero making themselves useful

### Assistants

Each station can have:
- 1 primary crafter (full XP, does the actual work)
- 1 assistant (+20% speed, **no XP**, does whatever the primary crafter doesn't want to do)

The assistant accelerates the craft but does not currently earn skill XP for the work — only the primary crafter levels up. An in-code comment notes that per-skill assistant XP tracking would need to be added before this changes; until then, the assistant role is purely a speed lever, not a training rotation. The Guild Clerk still considers it an excellent way to keep idle heroes out of the Tavern.

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

**Roll Modifiers (Combat.ts:2528):**
- Skill level adds directly to the roll
- Station quality bonus adds to the roll
- Masterwork skill (100) guarantees a 50+ roll
- `extraQualityBonus` slot: the **Master Artisan title** adds +10 to this slot; it is the only consumer in current code
- *(No assistant quality bonus is currently applied.)*

### Crafting Failures

Low skill crafters can fail, with consequences ranging from "mildly disappointing" to "where did the Forge go?":

| Result | Effect |
|--------|--------|
| Success | Item created at rolled quality |
| Partial Fail | **No item created.** 100% of materials refunded. 50% XP granted to the crafter — a learning experience with no inventory cost |
| Full Fail | **No item created.** 50% of materials refunded (50% lost) |
| Critical Fail | All materials lost, station damaged |

The wiki previously claimed a Partial Fail produced an item at -1 quality tier; the current code path returns success:false with no item at all. The 50% XP grant on partial fail is the only consolation prize.

---

## Recipes

### Recipe Sources

Recipes enter your inventory through two confirmed code paths: the **starter set** that ships with a new guild, and **quest chain rewards** via `QuestChain.unlockRecipe()`. Other sources may exist as content in specific encounters, but no general recipe-acquisition table is wired in code.

| Source | Status |
|--------|--------|
| Starting set | Confirmed — shipped with a new guild |
| Quest chain rewards | Confirmed — `QuestChain.unlockRecipe()` is the production hook |
| Merchant purchase | <!-- TODO: verify - no merchant recipe table found in code --> |
| Mission rewards | <!-- TODO: verify - no general mission recipe drop table found --> |
| Boss drops | <!-- TODO: verify - no per-boss-tier recipe drop table found --> |

### Library Research

<!-- TODO: verify - the Library research workflow (researcher hero assignment, research materials, research timer) is not implemented in production code. The Library facility carries `maxRecipeTier` and `researchSpeed` metadata, but the research workflow itself has no startResearch / researcher / timer logic in current code. Treat this section as documented intent rather than a currently-usable system. -->

The Library facility tracks a `maxRecipeTier` cap (3 at maximum facility level) and a `researchSpeed` modifier, but the workflow for *using* the Library to research a recipe — assigning a hero, consuming materials, waiting for a timer — has no implementation in production code. The system appears to have been planned but not wired up.

If you need recipes beyond the starter set, the production path is **quest chains** and **content unlocks**, not Library research.

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
Cloth → [Loom] → Fine Cloth
  3 cloth = 1 fine
```

---

## Example Recipes

### Weapons

| Recipe | Tier | Materials | Skill Req |
|--------|------|-----------|-----------|
| Iron Sword | ⭐ | 3 Iron Ingot, 1 Wood | 1 |
| Steel Sword | ⭐⭐ | 4 Steel Ingot, 2 Hardwood | 25 |
| Mithril Blade | ⭐⭐⭐ | 5 Mithril Ingot, 2 Ironwood | 50 |
| Adamantine Edge | ⭐⭐⭐⭐ | 4 Adamantine Ingot, 2 Dragon Fang | 75 |
| Dragonslayer Axe | ⭐⭐⭐⭐⭐ | 3 Dragonscale, 2 Adamantine Ingot, 1 Dragon Heart | 100 |

### Armor

| Recipe | Tier | Materials | Skill Req |
|--------|------|-----------|-----------|
| Iron Plate | ⭐ | 5 Iron Ingot | 1 |
| Steel Plate | ⭐⭐ | 6 Steel Ingot, 3 Leather | 25 |
| Mithril Mail | ⭐⭐⭐ | 5 Mithril Ingot, 3 Quality Leather | 50 |
| Dragonplate | ⭐⭐⭐⭐ | 4 Adamantine Ingot, 4 Dragonscale | 75 |

### Potions

| Recipe | Tier | Materials | Skill Req |
|--------|------|-----------|-----------|
| Minor Health Potion | ⭐ | 2 Herbs, 1 Water | 1 |
| Health Potion | ⭐⭐ | 2 Herb Extract, 1 Blood | 25 |
| Greater Health Potion | ⭐⭐⭐ | 2 Herb Concentrate, 1 Rare Herbs | 50 |

### Prosthetics

| Recipe | Tier | Materials | Skill Req |
|--------|------|-----------|-----------|
| Peg Leg | ⭐⭐ (Basic) | 3 Hardwood, 2 Leather, 1 Iron Ingot | Leatherworking 5 |
| Prosthetic Leg | ⭐⭐⭐ (Standard) | 5 Steel Ingot, 2 Hardened Leather, 1 Mithril Ingot | Blacksmithing 10 |
| Enchanted Leg | ⭐⭐⭐⭐ (Enhanced) | 2 Adamantine Ingot, 1 Dragon Bone, 2 Soul Shard, 1 Arcane Dust | Enchanting 15 |

---

## Item Workshop

The Item Workshop lets you reroll the bonus stats on equipment without crafting a new item. This is useful for items that have good base stats but poor bonus rolls — a situation that occurs with frustrating regularity.

**Requirements:** the Workshop UI itself does not currently gate rerolls by rarity or by named status — the rarity filter offers a "common-uncommon (C/U)" option, and `handleReroll` has no `isNamed` check. In practice you can reroll any item the Workshop will display, including named ones.

**Reroll Cost:**
```
Cost = 1,000 × Rarity Tier × 2^(Previous Rerolls)
```

Costs double each time you reroll the same item. You can preview the new stats and choose to Accept or Reject before committing.

**Navigate to:** the **Workshop** (⚙) button in the bottom navigation — it is a peer of Guild and Market, not a sub-screen of the Guild Hall.

---

## Tips for Efficient Crafting

### Early Game

1. **Focus One Crafter** - Level one hero's crafting skill fast; a generalist who's mediocre at everything produces consistently mediocre items
2. **Process Materials** - Keep raw materials processed and ready; unprocessed ore can't be crafted into anything useful, regardless of how much you have
3. **Unlock Stations Early** - Facility missions are worth prioritizing; you cannot craft what you don't have a station for
4. **Research Basic Recipes** - Library investment pays off quickly with access to Tier 2 recipes before you'd find them in the field

### Mid Game

1. **Specialize Heroes** - Different heroes for different skills; a Blacksmithing 80 and an Alchemy 80 outperform two heroes who are both at 40 in both
2. **Use Assistants** - The speed bonus compounds with other modifiers; a full crafting team is meaningfully faster
3. **Hunt for Recipes** - Boss dungeons drop blueprint tiers you cannot research; plan expeditions with this in mind
4. **Quality Matters** - A Superior-quality item from a skilled crafter beats a Normal-quality item from the same recipe; wait for the crafter, not just the materials

### Late Game

1. **Masterwork Crafters** - Skill level 100 guarantees quality rolls of 50+, which eliminates Poor and Normal outcomes entirely
2. **Farm World Bosses** - The only reliable source of ⭐⭐⭐⭐⭐ recipes; no Library level substitutes for this
3. **Enchant Everything** - Bare high-tier gear is leaving performance on the table
4. **Prosthetics** - Enchanted prosthetics at 125% efficiency outperform the original body part; this is, technically, a reason to be optimistic

---

## Crafting Station Recommendations

The honest answer to "which stations should I build" is "all of them eventually." These are the starting priorities while "eventually" is still a long way off:

### Per Hero Count

| Heroes | Priority Stations |
|--------|-------------------|
| 3-5 | Forge, Alchemy Lab — equipment and potions cover the basics |
| 6-10 | + Tannery, Kitchen — more heroes means more healing needed and more leather |
| 10+ | + Enchanting, Jeweler — at this point, accessories and enhancement become the limiting factor |

### Per Guild Focus

| Focus | Priority |
|-------|----------|
| Combat | Forge, Alchemy Lab — weapons, armor, and something to drink when it goes wrong |
| Exploration | Kitchen, Alchemy Lab — sustained dungeons require sustained consumables |
| Crafting Empire | All stations maxed — the goal is self-sufficiency, and it requires everything |

---

## Related Guides

- [Equipment & Items](equipment.md) - What you can craft
- [Heroes & Classes](heroes.md) - Hero states and assignment
- [Guild Management](guild.md) - Facility upgrades

---

*"A well-equipped guild is a successful guild. A well-equipped guild that also remembers to pay its crafters is an exceptional one."*
