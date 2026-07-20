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
| **Forge** | Metal weapons, armor | Metalsmithing |
| **Armory** | Armor crafting | Metalsmithing |
| **Tannery** | Leather processing and goods | Softcraft |
| **Loom** | Cloth processing and items | Softcraft |
| **Alchemy Lab** | Potions and elixirs | Alchemy |
| **Kitchen** | Food buffs and meals | Alchemy |
| **Enchanting Table** | Magic enhancements | Arcana |
| **Jeweler Bench** | Jewelry and accessories | Arcana |
| **Lumber Mill** | Wood processing, bows, prosthetics | Metalsmithing |
| **Smelter** | Ore processing, ingots | Metalsmithing |

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
| 7 | Aetherforge | 2.8× | +35% |
| 8 | Crucible Sanctum | 3.0× | +40% |
| 9 | Reality Anvil | 3.5× | +50% |
| 10 | Apotheosis Workshop | 4.0× | +60% |

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

Heroes level up crafting skills by crafting. There is no shortcut, no cheat, and no amount of motivational speeches that will substitute for actually making things. Four consolidated disciplines cover all ten stations:

| Skill | Max Level | Governs | Stations |
|-------|-----------|---------|----------|
| Metalsmithing | 100 | Metal weapons, armor, structural work | Forge, Armory, Smelter, Lumber Mill |
| Softcraft | 100 | Leather and cloth goods | Tannery, Loom |
| Alchemy | 100 | Potions, elixirs, food | Alchemy Lab, Kitchen |
| Arcana | 100 | Enchantments, jewelry | Enchanting Table, Jeweler Bench |

### Skill Level Effects

| Skill Level | Recipes Unlocked | Success Rate | Quality Bonus |
|-------------|------------------|--------------|---------------|
| 1-20 | ⭐ | 70% | +0% |
| 21-40 | ⭐⭐ | 80% | +5% |
| 41-60 | ⭐⭐⭐ | 85% | +10% |
| 61-80 | ⭐⭐⭐⭐ | 90% | +15% |
| 81-99 | ⭐⭐⭐⭐⭐ | 95% | +20% |
| 100 | Masterwork | 100% | +30% |

### Passive Combat Buffs

Crafting skills aren't just for the workbench. Each hero's own crafting skill level grants a personal, always-active combat bonus — the game's way of rewarding heroes who've spent time at a station instead of a dungeon:

| Skill | Stat Buffed | L21-40 | L41-60 | L61-80 | L81-99 | L100 |
|-------|-------------|--------|--------|--------|--------|------|
| Metalsmithing | Physical Damage | +5% | +10% | +15% | +20% | +30% |
| Softcraft | Armor | +5% | +10% | +15% | +20% | +30% |
| Alchemy | Max HP | +2% | +5% | +8% | +12% | +20% |
| Alchemy | HP Regen (per turn) | +5% | +10% | +15% | +20% | +30% |
| Arcana | Intelligence | +5% | +10% | +15% | +20% | +30% |

Levels 1–20 grant no combat bonus. Bonuses from multiple levelled skills stack additively — a hero with Metalsmithing 60 and Arcana 40 gets +10% physical damage and +5% intelligence on top of everything else.

### Gaining Crafting XP

XP per level is linear — `100 × level` — so each successive level costs exactly 100 XP more than the last. Cumulative XP from 1 to 100 totals 505,000.

Crafting XP per item is based on tier and level:

```
XP = Base × 100 + Item Level × 20
```

| Material Tier | Base XP |
|---------------|---------|
| Common (T1) | 1 |
| Uncommon (T2) | 2 |
| Rare (T3) | 5 |
| Epic (T4) | 10 |
| Legendary (T5) | 20 |

**Examples:**
- Common item (L5): 1 × 100 + 5 × 20 = 200 XP
- Rare item (L30): 5 × 100 + 30 × 20 = 1,100 XP
- Legendary item (L70): 20 × 100 + 70 × 20 = 3,400 XP

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

**Roll Modifiers (`crafting/system.ts:703`):**
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
| Partial Fail | **No item created.** 75% of materials refunded (25% lost). 50% XP granted to the crafter — a learning experience with an actual, if modest, inventory cost |
| Full Fail | **No item created.** 50% of materials refunded (50% lost) |
| Critical Fail | All materials lost, station damaged |

The wiki previously claimed a Partial Fail produced an item at -1 quality tier; the current code path returns success:false with no item at all. The 50% XP grant on partial fail is the consolation prize, and no longer comes with a full refund — the free-retry loophole was closed.

### Crafted Item Sell Value

Successful crafts produce items with a sell value based on material cost and quality — the game's way of ensuring your invested resources translate into at least something if the item isn't worth equipping:

```
Sell Value = floor(Material Cost × 1.3 + Gold Cost × 0.5 + Quality Bonus)
```

Quality bonus is a percentage of total material cost:

| Quality | Bonus |
|---------|-------|
| Poor / Normal | 0% |
| Fine | +10% |
| Superior | +20% |
| Exceptional | +30% |
| Masterwork | +50% |

Material cost is calculated using the sell anchor per tier: Common 100g, Uncommon 1,000g, Rare 10,000g, Epic 100,000g, Legendary 1,000,000g. A Masterwork Legendary item sells for considerably more than its component materials cost — which is, finally, a financial argument for patience.

---

## Recipes

### Recipe Availability

Recipes must be **unlocked** before you can craft them. If a recipe shows up in the UI but the craft button refuses to cooperate, the unlock gate is why — the error message will say as much, with the weary patience of a system that has explained this before.

Every new guild starts with all **Common-tier** recipes unlocked — enough to get the forges warm and the alchemist's eyebrows singed without any research investment. Everything above Common requires either research or a fortunate drop:

| Tier | How to unlock |
|------|---------------|
| Common | Auto-unlocked at guild creation |
| Uncommon | Research at the Workshop |
| Rare | Research at the Workshop |
| Epic | **Drop-only** — heroic dungeons (8%), raids (15%) |
| Legendary | **Drop-only** — heroic dungeons (2%), raids (5%), world bosses (8%) |

A handful of recipes also require a specific **raid boss's first kill** — defeating that boss unlocks every recipe gated behind it (`GameState.ts`). Quest chains can still formally unlock recipes via `QuestChain.unlockRecipe()` (`crafting/system.ts:462`).

### Recipe Drops

Epic and Legendary recipes cannot be researched — they drop from endgame content as recipe scrolls. Each completion rolls two independent Bernoulli trials (one for Epic, one for Legendary), so a single clear can yield zero, one, or — for the improbably lucky — two recipes.

| Source | Epic (per clear) | Legendary (per clear) |
|--------|-------------------|-----------------------|
| Heroic Dungeons | 8% | 2% |
| Raids | 15% | 5% |
| World Bosses | — | 8% |

Drops exclude recipes you've already unlocked and boss-gated recipes whose boss hasn't been beaten yet. If a winning roll draws a recipe you already own, it converts to gold instead — 10,000g for an Epic duplicate, 100,000g for a Legendary. The Guild Clerk considers this "a consolation prize in the loosest possible sense of both words."

### Research

Research is how Uncommon and Rare recipes enter your collection — a process involving gold, materials, and the kind of patience the Guild Clerk considers character-building.

**Slots:** You get one research slot per Workshop level, up to 10 concurrent projects at Workshop L10. Each slot works independently.

**Cost per project:**

| Tier | Gold | Materials | Duration |
|------|------|-----------|----------|
| Uncommon | 5,000g | 50% of recipe's materials (rounded up) | 2 days |
| Rare | 50,000g | 50% of recipe's materials (rounded up) | 5 days |

Common recipes don't need research (already unlocked). Epic and Legendary recipes return "drop-only and cannot be researched" — `getResearchCost` returns `null` for tier 4+ (`formulas.ts:200`).

**Cancellation:** You can cancel a research project at any time. Half the materials come back (rounded down); gold does not. The Guild Clerk notes that this refund policy is "consistent with every other refund policy the guild has ever offered, which is to say: partial, grudging, and non-negotiable."

**XP:** Completed research grants 50% of the equivalent craft XP (floored) to the hero with the highest level in the relevant crafting skill. No hero assignment required — the guild's best crafter for that skill absorbs the knowledge automatically, which is the game's quiet concession that research montages don't need micromanagement.

### Library

The Library facility declares `researchSpeed` and `maxRecipeTier` metadata in its level templates, but neither value is currently consumed by the research system — research slots come from the **Workshop** and research duration is fixed per tier. The Library's actual runtime effects are +5% mission XP per level and unlocking Meditation training at L3.

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
| Peg Leg | ⭐⭐ (Basic) | 3 Hardwood, 2 Leather, 1 Iron Ingot | Softcraft 5 |
| Prosthetic Leg | ⭐⭐⭐ (Standard) | 5 Steel Ingot, 2 Hardened Leather, 1 Mithril Ingot | Metalsmithing 10 |
| Enchanted Leg | ⭐⭐⭐⭐ (Enhanced) | 2 Adamantine Ingot, 1 Dragon Bone, 2 Soul Shard, 1 Arcane Dust | Arcana 15 |

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

## Crafting Currencies

Ten consumable items that modify equipment bonus stats — the Workshop rerolls them wholesale, but currencies let you sculpt them one at a time, seal what you want to keep, or burn the lot down and start again. Think of them as the difference between "re-deal the whole hand" and "draw one card." The Cursed Sigil, at the far end, is the difference between "draw one card" and "flip a table."

### Currency Types

**Powders** (Common — purchasable at the Materials Market):

| Currency | Effect |
|----------|--------|
| Powder of First Enchantment | Add one random bonus stat to an item that has none |
| Powder of Erasure | Remove one random bonus stat (skips sealed stats) |

**Salts** (Uncommon / Epic):

| Currency | Effect |
|----------|--------|
| Salt of Renewal (Uncommon) | Reroll the *values* of existing bonus stats without changing which stats are present (skips sealed) |
| Salt of Cleansing (Epic) | Strip *all* bonus stats and seals — a clean slate, for when the sculptor's approach has failed and the quarry's approach seems appropriate |

**Ichors** (Rare — drop-only):

| Currency | Effect |
|----------|--------|
| Ichor of Reshaping | Replace one random bonus stat with a different one (skips sealed) |
| Ichor of Empowerment | Add one bonus stat, up to the item's maximum bonus slots |
| Ichor of Sealing | Lock one bonus stat permanently — sealed stats cannot be removed, rerolled, or replaced by any currency |

**Portents** (Epic — drop-only):

| Currency | Effect |
|----------|--------|
| Portent of the Weighing | One-shot modifier: the *next* currency you apply targets the lowest-value stat |
| Portent of Kinship | One-shot modifier: the *next* currency is restricted to the item's most common stat family |

**Cursed Sigil** (Legendary — drop-only):

Equal 25% chance of four outcomes: buff a stat, add a bonus slot, seal a stat, or **destroy the item**. All outcomes mark the item as Cursed. The Sigil is, in the Guild Clerk's opinion, an object that rewards courage and punishes optimism in equal measure.

### Obtaining Currencies

Common and Uncommon currencies (the two Powders and Salt of Renewal) are stocked daily at the Materials Market — 500g for either Powder, 5,000g for the Salt. Prices are fixed and exempt from market events.

Everything Rare and above is drop-only, awarded from content completion:

| Source | Drops |
|--------|-------|
| Regular Dungeons | Common Powders (10–15%), Ichors (0.5–1.5%), Salt of Cleansing (1%), Portents (1–1.5%) |
| Heroic Dungeons | Full range including Cursed Sigil (~1%) |
| Abyssal Spire | Full range, Cursed Sigil (0.5% + soft pity) |
| Raids | Rare currencies, Portents, Cursed Sigil (3%) |
| World Bosses | Cursed Sigil only (5%) |

Regular dungeons drop Rare+ currencies at roughly half the heroic rate — early- and mid-game players see Ichors and Portents without needing endgame content. Only the Cursed Sigil remains gated to heroic dungeons, the Abyssal Spire, raids, and world bosses.

Each currency is an independent Bernoulli roll per clear — you can receive multiple currencies from a single run. The Cursed Sigil has a soft-pity ramp on Abyssal floors: after 50 floors without one, the drop chance increases by +0.05% per floor, capping at 15%.

### Workshop Currency Discount

Workshop levels 2–10 reduce the gold cost of currency operations by 10% per level above 1 — `(level − 1) × 10%`, capped at 90% at level 10. This applies to the gold fee charged when you use a currency on an item, not to market purchase prices.

---

## Tips for Efficient Crafting

### Early Game

1. **Focus One Crafter** - Level one hero's crafting skill fast; a generalist who's mediocre at everything produces consistently mediocre items
2. **Process Materials** - Keep raw materials processed and ready; unprocessed ore can't be crafted into anything useful, regardless of how much you have
3. **Unlock Stations Early** - Facility missions are worth prioritizing; you cannot craft what you don't have a station for
4. **Research Basic Recipes** - Library investment pays off quickly with access to Tier 2 recipes before you'd find them in the field

### Mid Game

1. **Specialize Heroes** - Different heroes for different skills; a Metalsmithing 80 and an Alchemy 80 outperform two heroes who are both at 40 in both
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
