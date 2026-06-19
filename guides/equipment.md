# Equipment & Items

Proper equipment is crucial for hero survival, in the same way that oxygen is crucial for breathing — technically optional, but the alternatives are universally fatal. This guide covers weapons, armor, accessories, and the gem socket system.

## Equipment Slots

Each hero has 10 equipment slots:

| Slot | Types | Notes |
|------|-------|-------|
| **Main Hand** | Weapons | Class-restricted |
| **Off Hand** | Shields, Focus, Secondary | Class-restricted |
| **Armor** | Plate, Mail, Leather, Cloth | Class-restricted |
| **Head** | Helmets, Hoods, Hats | Universal |
| **Boots** | Boots, Greaves, Shoes | Universal |
| **Gloves** | Gauntlets, Gloves, Bracers | Universal |
| **Accessory 1** | Rings, Amulets | Universal |
| **Accessory 2** | Rings, Amulets | Universal |
| **Consumable 1** | Potions, Items | Universal |
| **Consumable 2** | Potions, Items | Universal |

---

## Item Rarity

Items come in seven rarity tiers. The Guild Clerk has witnessed grown heroes weep openly upon receiving a Mythic drop, and throw perfectly serviceable Common items into the nearest ravine. Both reactions are, technically, unprofessional.

| Rarity | Color | Min Sockets | Max Sockets |
|--------|-------|-------------|-------------|
| Common | White | 0 | 1 (5% chance) |
| Uncommon | Green | 0 | 2 |
| Rare | Blue | 1 | 3 |
| Epic | Purple | 1 | 4 |
| Legendary | Orange | 2 | 5 |
| Mythic | Red | 3 | 6 |
| Ancestral | Blood Red | 4 | 7 |

**Bonus Stats by Rarity:** Higher rarity items roll additional random bonus stats:

| Rarity | Bonus Stats | Stat Multiplier |
|--------|-------------|-----------------|
| Common-Uncommon | 0 | 1.0× |
| Rare | 1 | 1.0× |
| Epic | 2 | 1.2× |
| Legendary | 3 | 1.5× |
| Mythic | 4 | 2.0× |
| Ancestral | 5 | 2.5× |

**Drop Requirements:** Higher-rarity items only appear when the content is difficult enough to justify them. The game takes the position that the equipment should be earned:

| Rarity | Min Level | Min Stars | Min Tier |
|--------|-----------|-----------|----------|
| Epic | 40 | 3★ | Any |
| Legendary | 60 | 4★ | Rare (T3+) |
| Mythic | 85 | 5★ | Boss (T5) |

Socket count rolls increase with item level. Base chance: `20% + item level × 1%` (capped at 90%).

---

## Weapons

### Weapon Types by Class

| Class | Available Weapons |
|-------|-------------------|
| Warrior | Swords, Axes, Maces, Spears |
| Mage | Staves, Wands |
| Rogue | Daggers, Swords, Crossbows |
| Cleric | Maces, Staves, Swords |
| Ranger | Bows, Crossbows, Spears |
| Necromancer | Staves, Wands, Daggers |

Heroes without a weapon equipped fight **Unarmed** (1-3 base damage). This is not recommended for anything except proving a point.

### Weapon Stats

Every weapon reduces to five numbers. Heroes who understand these numbers do better than heroes who simply pick up whatever looks most threatening, though both approaches are represented in the guild.

| Stat | Description |
|------|-------------|
| **Damage** | Base attack damage range |
| **Speed** | Attack frequency multiplier |
| **Crit Chance** | % to critically hit |
| **Crit Damage** | Multiplier on critical hits |
| **Special** | Unique effects |

### Example Progression

**Swords (Warrior/Rogue):**
- Iron Sword (Common): 8-12 damage
- Steel Sword (Uncommon): 14-20 damage, +2% crit
- Mithril Blade (Rare): 25-35 damage, +8% crit, +10 STR
- Dragonslayer (Epic): 40-55 damage (the +20% vs Dragons comes from the Dragonslayer 2-piece **set bonus**, not the weapon itself)
- Worldsplitter (Legendary): 70-95 damage, +15% crit, +50% crit damage (the "cleave all enemies" claim has no template-level support; that effect would belong to a linked support gem like Melee Splash)

**Staves (Mage/Cleric/Necromancer):**
- Wooden Staff (Common): 5-8 damage, +10 Mana
- Arcane Staff (Rare): 18-28 damage, +50 Mana
- Staff of Eternity (Legendary): 55-80 damage, +150 Mana, +int (the "-20% cooldowns" claim is the **Archmage's Regalia 3-piece set bonus**, not a weapon stat)

<!-- TODO: verify - 'Oak Staff' and 'Staff of Elements' templates were not found in code. -->
<!-- TODO: verify - 'Mithril Mail' template was not found in ArmorTemplates.ts. -->

---

## Armor

### Armor Types by Class

| Type | Defense | Classes | Guild Clerk's Notes |
|------|---------|---------|---------------------|
| **Plate** | Highest | Warrior | Warriors consider anything less to be "pajamas" |
| **Mail** | High | Cleric, Ranger | A sensible compromise |
| **Leather** | Medium | Rogue, Ranger | Rogues insist this is "tactical" |
| **Cloth** | Low | Mage, Necromancer | Mages consider anything heavier "excessive" |

### Armor Stats

Armor trades mobility for survival. Warriors consider this an excellent trade. Mages consider it a personal affront.

| Stat | Description |
|------|-------------|
| **Armor** | Reduces incoming damage |
| **HP Bonus** | Increases max health |
| **Resistance** | Elemental damage reduction |
| **Speed** | Movement modifier (plate is slower) |

### Example Progression

**Heavy Armor (Warrior):**
- Iron Plate: 15 armor, +20 HP
- Steel Plate: 30 armor, +40 HP
- Dragonplate: 80 armor, +120 HP, 50% Fire Resist (the Fire Resist actually comes from the Dragonslayer 3-piece set bonus)
- **Immortal Bastion** (Mythic, L68, Warrior/Cleric): 120 armor, +200 HP, +28 STR, +28 VIT, +20% to each of fire/ice/lightning/holy/dark resists (`ArmorTemplates.ts:260-274`). No HP regen mechanic — the wiki previously claimed 150 armor + 5% regen/turn, both invented.

---

## Accessories

### Rings

Two ring slots per hero, both treated as a personality statement. The Guild Clerk views them as stat bonuses.

| Example | Rarity | Effect |
|---------|--------|--------|
| Iron Band | Common | +3 to STR or DEX |
| Silver Ring | Uncommon | +6 to stat, +5% resist |
| Gold Ring | Rare | +12 INT, +20 Mana |
| **Ring of Power** | Legendary, L60 | +25 to **all four** primary stats (STR/DEX/INT/VIT). No single "legendary effect" beyond the across-the-board stat boost |

<!-- TODO: verify - 'Enchanted Band' template was not found in AccessoryTemplates.ts. -->

### Amulets

Amulets focus on HP, Mana, and powerful unique effects — the equipment category that tends to matter most when the fight stops going to plan.

| Example | Rarity | Effect |
|---------|--------|--------|
| Bone Charm | Common | +10 HP |
| Crystal Pendant | Uncommon | +25 HP **and** +15 Mana |
| **Heart of the World** | Legendary, L70 | +150 HP, +100 Mana, **+10% Life Steal** (the wiki previously claimed auto-resurrect — that mechanic does not exist on this template) |

<!-- TODO: verify - 'Enchanted Amulet' and 'Medallion of Power' templates were not found in AccessoryTemplates.ts. -->
| Heart of the World | Legendary | +150 HP, +100 Mana, auto-resurrect |

### Notable Unique Accessories

| Name | Effect |
|------|--------|
| Ring of Shadows | +15 DEX, +8% crit chance (Rogue, L30 Rare, part of the Shadow Assassin Set) |
| Amulet of the Phoenix | +80 HP, +30 Fire Resist (L50 Epic, part of the Phoenix set) |
| Band of Haste | +15 DEX (L50 Epic — the "haste" is flavor; the stat is DEX) |
| Charm of Fortune | +35 LCK, +30% Gold Find, +20% Magic Find (L50 Legendary) |
| Signet of Command | +15 to STR/DEX/INT/VIT/LCK (L60 Legendary — a flat +15 across all five primary stats) |

### Mana Sustain Affixes

Two random-roll affixes feed the [mana economy](combat.md#mana-economy):

| Affix | Rolls On | Effect |
|-------|----------|--------|
| `manaRegen` | Accessory 1, Accessory 2 | Flat mana regen per turn; stacks with passive tree and class baseline |
| `manaCostReduction` | Accessory 1, Accessory 2, weapons | Percent reduction to skill mana costs; additive with proficiency, passives, set bonuses, and ascendancy, capped at 75% total |

Both use continuous scaling — a rare ring at L50 will roll something modest, the same affix on a mythic at L100 considerably less so. They can coexist on the same accessory, which is the combination experienced builders look for first.

---

## Consumables

Items heroes use mid-combat when the situation has become urgent — which, in the Guild Clerk's experience, it always does. Pack them. Heroes who forget consumables tend to generate paperwork.

### Health Potions

| Name | Rarity | Healing | Stack |
|------|--------|---------|-------|
| Minor Health Potion | Common | 50 HP | 10 |
| Health Potion | Uncommon | 150 HP | 10 |
| Greater Health Potion | Rare | 400 HP | 5 |

**Auto-Use:** Heroes automatically drink health potions when below 50% HP.

<!-- TODO: verify - 'Superior Health Potion' and 'Elixir of Life' templates were not found in ConsumableTemplates.ts. -->

### Mana Potions

| Name | Rarity | Mana | Stack |
|------|--------|------|-------|
| Minor Mana Potion | Common | 30 | 10 |
| Mana Potion | Uncommon | 80 | 10 |

(For Rare and Epic tier mana consumables, see **Mana Flasks** below — the wiki previously listed "Greater Mana Potion" (Rare, 200 mana) and "Superior Mana Potion" (Epic, 500 mana) as separate items, but those exact named templates don't exist; the live Rare/Epic mana consumables are Mana Flask (Rare, 250 mana) and Greater Mana Flask (Epic, 500 mana).)

### Mana Flasks

A higher-tier line of mana consumables for heroes who've gone past the "occasionally run dry" stage and into the "regularly spend a 6-link's mana in one turn" tier. Combat tactical logic auto-uses these when mana drops below threshold and a flask is in either Consumable slot.

| Name | Rarity | Mana | Min Level | Stack |
|------|--------|------|-----------|-------|
| Lesser Mana Flask | Uncommon | 120 | 20 | 5 |
| Mana Flask | Rare | 250 | 40 | 5 |
| Greater Mana Flask | Epic | 500 | 60 | 5 |

Craftable at the alchemy bench. The recipes are short. The alchemist's commentary on them, less so.

### Buff Potions

| Name | Effect | Duration |
|------|--------|----------|
| Strength Tonic | +15 STR | 1 combat |
| Defense Potion | +25 Armor | 1 combat |
| Haste Potion | +50% Speed | 1 combat |

<!-- TODO: verify - 'Ironflesh Elixir', "Giant's Strength", 'Berserker Brew', and 'Invulnerability' templates were not found in ConsumableTemplates.ts. The Defense Potion (Rare, +25 Armor) is the closest real item to the wiki's removed Ironflesh entry. -->

---

## Gem Sockets

Equipment can have gem sockets based on rarity and slot type (see [Skill Gems Guide](skills.md) for full socket details). Socketed gems grant additional skills or bonuses. The Guild Clerk finds the entire gem-linking system needlessly complicated, but acknowledges that heroes who master it are considerably harder to kill.

### Socket Colors

Socket colors gate **gem compatibility** — they do not map cleanly to a damage/magic/utility split. See the full color discussion in the [Skills guide](skills.md#gem-colors); briefly:

| Color | Accepts | Where it shows up |
|-------|---------|-------------------|
| **Red** | Red gems | All active attack, spell, minion, holy, and many ranged gems are red regardless of their stat requirement |
| **Green** | Green gems | Defensive guards, warcries, healing, movement and some utility actives |
| **Blue** | Blue gems | Currently no active blue gems exist; blue sockets accept the **blue variants of support gems**, which require INT |
| **White** | Any color | Wild slot, rolled at ~3% per socket |

### Skill Gems

Skill gems add new abilities to your hero when socketed:

| Gem | Type | Effect |
|-----|------|--------|
| Pyroblast | Spell | Single-target fire spell |
| Freezing Pulse | Spell | Cold spell with freeze chance |
| Heavy Strike | Attack | High single-target physical hit |
| Greater Cleave | Attack | AoE melee swing |
| Split Arrow | Ranged | Bow attack hitting multiple targets |
| Healing Light | Support | Heals an ally in combat |

### Socket Links

Linked sockets allow support gems to enhance skill gems. Each additional link makes the skill considerably more dangerous, which is the point. Weapon and body-armor slots can support up to 6-link chains; smaller slots cap lower (see [Skill Gems](skills.md#socket-links)).

| Link | Effect |
|------|--------|
| **1-Link** | Skill gem only |
| **2-Link** | Skill + 1 support |
| **3-Link** | Skill + 2 supports |
| **4–6-Link** | Skill + 3–5 supports (weapon / body armor only) |

**Support Gem Examples:**
- **Added Fire Damage** - Adds fire damage to linked skill
- **Multistrike** - Skill repeats additional times
- **Spell Echo** - Spell casts twice
- **Life Leech** - Heal a percentage of damage dealt
- **Concentrated Effect** - More damage at the cost of AoE radius

---

## Equipment Sets

Wearing multiple pieces from the same set grants powerful bonuses. The Guild Clerk has filed multiple incident reports about heroes refusing to equip statistically superior items because they'd "break the set." This is, apparently, a matter of principle.

### Dragonslayer Set (Epic)

| Pieces | Bonus |
|--------|-------|
| 2 | +20% damage vs Dragons |
| 3 | +50% Fire Resistance |
| 4 | Dragon's Fury: 10% attacks breathe fire |

**Pieces:** Dragonslayer Blade, Dragonplate Armor, Dragonscale Shield, Dragon Fang Amulet

### Shadow Assassin Set (Epic)

| Pieces | Bonus |
|--------|-------|
| 2 | +15% Crit Damage |
| 3 | +20% Crit Chance |
| 4 | First attack in combat always crits (`assassin_ambush`) |

**Pieces:** Shadowblade, Nightstalker Armor, Hood of Shadows, Ring of Shadows

### Archmage's Regalia (Legendary)

| Pieces | Bonus |
|--------|-------|
| 2 | +50 Mana |
| 3 | -20% Cooldowns |
| 4 | Spells echo (cast twice at 50% power) |

**Pieces:** Staff of Eternity, Vestment of Eternity, Crown of Stars, Amulet of the Arcane

### Crusader's Armament (Epic)

| Pieces | Bonus |
|--------|-------|
| 2 | +30% Holy Damage |
| 3 | +25% Healing |
| 4 | +100% damage vs Undead/Demons |

**Pieces:** Blessed Blade, Crusader's Plate, Shield of Faith, Holy Symbol

---

## Item Quality

Beyond rarity, items have quality ratings that affect their stats. A Masterwork Rare can outperform a Normal Epic — a fact that crafters mention at every possible opportunity:

| Quality | Stat Modifier | Visual |
|---------|---------------|--------|
| Poor | -20% | Dull, worn |
| Normal | +0% | Standard |
| Fine | +10% | Polished |
| Superior | +20% | Gleaming |
| Exceptional | +30% | Ornate |
| Masterwork | +50% | Legendary appearance |

Quality is determined by crafting skill or random drop luck.

---

## Enchanting

Items can hold enchantments in their **`maxEnchantSlots`** (a per-template field, typically 1–3 depending on slot and rarity), filled at the Enchanting Table facility.

<!-- TODO: verify - The named-enchantment registry the wiki previously listed (Sharpness +10% Damage, Flaming +Fire DoT, Frost +Ice Damage Slow, Lightning Chain to 2 enemies, Vampiric 5% Life Steal, Vorpal +15% Crit +50% Crit Damage, Holy +100% vs Undead/Demons; armor enchants Fortified/Resilient/Resistant/Thorns/Regeneration/Warding; accessory enchants Luck/Swiftness/Wisdom/Wealth/Survival) has no corresponding code data structure — Item.enchantments is currently typed as string[] with no canonical effect-by-name table found in the templates or models. The Enchanting Table facility exists; the named enchant catalogue described in earlier wiki versions appears to be aspirational or pre-implementation. Section pruned pending re-verification against an enchantment registry once one ships. -->


---

## Forges & Manufacturers

Every piece of equipment has a maker, and heroes have opinions about them. Strong opinions. Surprisingly passionate opinions, given that they're talking about a sword.

### Major Forges

| Forge | Specialty | Known For |
|-------|-----------|-----------|
| **Valdris Arms** | Premium | Expensive but perfect |
| **Kothric Steel** | Dwarven | Traditional, unbreakable |
| **Grimforge** | Mass-produced | Cheap but inconsistent |
| **Thornwood Armory** | Elven | Elegant, lightweight |
| **Ironheart Works** | Generic | Reliable, boring |
| **Blackmoor Blades** | Dark | Intimidating, edgy |
| **Sunfire Smithy** | Holy | Blessed, anti-undead |

Heroes may comment on equipment based on their personality:
- Vain heroes prefer prestigious forges
- Frugal heroes complain about expensive gear
- Traditional heroes like dwarven craftsmanship

---

## Managing Equipment

### Guild Vault

All items go to the central Guild Vault. From there you can:
- **Equip** items to heroes
- **Sell** items for gold
- **Salvage** items for crafting materials
- **Enchant** items with magical properties

### Tips

1. **Match to Role** - Equipment built for a class performs better in that class's hands. This seems obvious until you see how heroes shop unattended.
2. **Complete Sets** - Set bonuses are very powerful
3. **Socket Skills** - Skill gems dramatically increase power
4. **Upgrade Often** - Sentimentality about old gear is the leading cause of preventable injuries
5. **Check Quality** - A Superior Rare may beat a Normal Epic

---

## Related Guides

- [Heroes & Classes](heroes.md) - Class weapon restrictions
- [Crafting](crafting.md) - Creating equipment
- [Skills & Abilities](skills.md) - Skill gem details
- [Combat System](combat.md) - How equipment affects combat
- [World Boss Raids](raids.md) - Tier sets and offhand mythics available at the Raid Token vendor

---

*"The difference between a dead hero and a legend is often just better equipment — and the wisdom to check it's not cursed before putting it on."*
