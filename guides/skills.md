# Skill Gems & Sockets

Hero's Guild uses a Path of Exile-inspired skill gem system. Skills are gems that you socket into equipment, and linking gems together creates powerful combinations.

## Core Concepts

### Skill Gems

Skills in Hero's Guild come as gems that can be:
- **Socketed** into equipment with matching socket colors
- **Leveled up** through combat use (max level 100)
- **Linked** with support gems to enhance their effects

### Gem Types

| Type | Symbol | Description |
|------|--------|-------------|
| **Active** | ● | Skills you use in combat (attacks, spells, buffs) |
| **Support** | ◇ | Modify active skills they're linked to |

### Gem Colors

Gems come in four colors, each aligned with different stats:

| Color | Stat | Typical Skills |
|-------|------|----------------|
| 🔴 **Red** | STR | Melee attacks, heavy strikes, physical damage |
| 🟢 **Green** | DEX | Defensive skills, guards, mobility, healing |
| 🔵 **Blue** | INT | Spells, magic damage, minions |
| ⚪ **White** | Any | Rare gems usable by any class |

---

## Socket System

### Equipment Sockets

Different equipment pieces have different socket configurations:

| Equipment | Max Sockets | Typical Links |
|-----------|-------------|---------------|
| Weapons | 3-6 | Main skills |
| Body Armor | 4-6 | Primary skill setup |
| Helmet | 2-4 | Utility skills |
| Gloves | 2-4 | Secondary attacks |
| Boots | 2-4 | Movement, guards |

### Socket Colors

Sockets have colors that determine which gems can be placed:
- Red sockets accept 🔴 red gems
- Green sockets accept 🟢 green gems
- Blue sockets accept 🔵 blue gems
- White sockets accept ⚪ any gem color

### Linking Sockets

Sockets can be **linked** together, shown by a bar connecting them:

```
[🔴]—[🟢]  ← These two sockets are linked
[🔵]      ← This socket is separate
```

**Why Links Matter:**
- Active gems benefit from support gems in the same link group
- More links = more supports = stronger skills
- A 6-linked item is extremely valuable

---

## Gem Progression

### Gem XP

Gems gain XP when used in combat:
- **+10 XP** per skill use
- XP requirement scales exponentially: `100 × 1.08^level`
- Max level: 100

### Level Scaling

As gems level up:

| Stat | Scaling |
|------|---------|
| Base Damage | Increases per level |
| Mana Cost | +2% per level |
| Status Effects | Stronger/longer duration |
| Area of Effect | May increase |

### Mana Cost Formula

```
Mana Cost = Base Mana × (1 + (Level - 1) × 0.02)
```

At level 100, skills cost approximately 3× their base mana.

---

## Active Gems

### Attack Skills (Red)

| Gem | Type | Description |
|-----|------|-------------|
| **Greater Cleave** | AoE Melee | Swing weapon in arc, hitting all enemies |
| **Ground Slam** | AoE | Slam ground, damaging and stunning nearby |
| **Heavy Strike** | Single | Powerful single-target attack |
| **Flicker Strike** | Single | Teleport to enemy and strike |
| **Viper Strike** | Single | Poison-applying melee attack |

### Ranged Skills (Red/Green)

| Gem | Type | Description |
|-----|------|-------------|
| **Split Arrow** | AoE | Fire arrows that split to hit multiple targets |
| **Barrage** | Multi-hit | Rapid fire multiple arrows at one target |
| **Tornado Shot** | AoE | Arrows spiral outward after impact |

### Spell Skills (Blue)

| Gem | Type | Description |
|-----|------|-------------|
| **Pyroblast** | Single | Massive fire damage, chance to ignite |
| **Arc** | Chain | Lightning chains between enemies |
| **Freezing Pulse** | AoE | Cold wave that can freeze targets |
| **Essence Drain** | DoT | Chaos damage over time, heals caster |

### Minion Skills (Blue)

| Gem | Type | Description |
|-----|------|-------------|
| **Raise Zombie** | Summon | Raise a zombie from enemy corpse |
| **Summon Skeleton** | Summon | Summon a skeleton warrior |

### Healing Skills (Green)

| Gem | Type | Description |
|-----|------|-------------|
| **Healing Light** | Single | Restore HP to lowest-health ally |
| **Rejuvenation** | HoT | Apply healing over time effect |
| **Divine Shield** | Shield | Grant temporary damage absorption |

### Guard Skills (Green)

| Gem | Type | Description |
|-----|------|-------------|
| **Molten Shell** | Self | Absorb damage, explode when hit |
| **Frost Shield** | Self | Cold-based damage absorption |
| **Bone Armor** | Self | Necromancer's defensive shell |
| **Arcane Barrier** | Self | Mana-based shield |

### Warcry Skills (Green)

| Gem | Type | Description |
|-----|------|-------------|
| **Enduring Cry** | Self | Restore HP, generate endurance charges |
| **Rallying Cry** | Party | Buff nearby allies' damage |

### Movement Skills (Green)

| Gem | Type | Description |
|-----|------|-------------|
| **Evasive Roll** | Self | Dodge and reposition |
| **Smoke Bomb** | AoE | Create concealment, chance to evade |
| **Shadow Step** | Teleport | Instant teleport behind enemy |

### Holy Skills (Red/Green)

| Gem | Type | Description |
|-----|------|-------------|
| **Holy Bolt** | Single | Holy damage, bonus vs undead |
| **Divine Wrath** | AoE | Holy explosion centered on caster |
| **Righteous Fury** | Buff | Holy damage aura around caster |

---

## Support Gems

Support gems modify active skills they're linked to. They typically:
- Increase damage at a mana cost multiplier
- Add elemental damage
- Provide utility effects

### Damage Supports

| Gem | Effect | Mana Multiplier |
|-----|--------|-----------------|
| **Increased Damage** | +30-50% damage | 1.2× |
| **Added Fire Damage** | Add fire damage | 1.3× |
| **Added Cold Damage** | Add cold damage | 1.3× |
| **Added Lightning Damage** | Add lightning damage | 1.3× |
| **Added Chaos Damage** | Add chaos damage | 1.4× |

### Utility Supports

| Gem | Effect | Mana Multiplier |
|-----|--------|-----------------|
| **Faster Attacks** | Increased attack speed | 1.15× |
| **Greater Multiple Projectiles** | More projectiles, less damage each | 1.4× |
| **Life Leech** | Gain HP from damage dealt | 1.2× |
| **Mana Leech** | Gain mana from damage dealt | 1.15× |
| **Stun** | Increased stun chance | 1.1× |
| **Increased Duration** | Buffs/debuffs last longer | 1.1× |
| **Increased Area** | Larger AoE | 1.2× |

### Status Supports

| Gem | Effect | Mana Multiplier |
|-----|--------|-----------------|
| **Chance to Ignite** | Fire skills ignite more often | 1.15× |
| **Chance to Freeze** | Cold skills freeze more often | 1.15× |
| **Chance to Shock** | Lightning skills shock more often | 1.15× |
| **Poison** | Attacks apply poison | 1.2× |
| **Bleed** | Attacks cause bleeding | 1.2× |

---

## Building Skill Setups

### Example Setups

**Warrior Main Attack (4-link):**
```
[Heavy Strike]—[Increased Damage]—[Added Fire]—[Life Leech]
```
Result: Heavy single-target attack with fire damage and sustain.

**Mage AoE (5-link):**
```
[Arc]—[Added Lightning]—[Increased Area]—[Stun]—[Mana Leech]
```
Result: Chaining lightning with wider area, stuns, and mana sustain.

**Cleric Healing (3-link):**
```
[Healing Light]—[Increased Duration]—[Increased Area]
```
Result: AoE healing with extended duration (if Guardian ascendancy).

### Tips

1. **Match gem colors to sockets** - Plan your equipment around desired skill colors
2. **Balance mana costs** - Support gems multiply mana costs; don't overstack
3. **Consider your class** - Some gems work better with certain classes
4. **Level your main skills** - Focus XP on your primary damage/healing gems
5. **Link count matters** - A 4-link with good supports beats a 6-link with bad ones

---

## Gem Sources

### Finding Gems

| Source | Gem Quality |
|--------|-------------|
| Dungeon drops | Common to Rare |
| Boss drops | Uncommon to Epic |
| Quest rewards | Specific useful gems |
| Guild Shop | Basic gems for purchase |
| World bosses | Legendary gems |

### Gem Inventory

Heroes have a personal gem inventory separate from equipment sockets. Unneeded gems can be:
- Stored for later use
- Traded between heroes
- Sold for gold

---

## Related Guides

- [Equipment & Items](equipment.md) - Socket system on gear
- [Combat System](combat.md) - How skills work in combat
- [Heroes & Classes](heroes.md) - Class-specific skill considerations

---

*"A skilled hero is nothing without the gems to prove it."*
