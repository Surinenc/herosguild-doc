# Skill Gems & Sockets

Hero's Guild uses a Path of Exile-inspired skill gem system, because apparently just "knowing how to fight" wasn't complicated enough. Skills are gems that you socket into equipment, and linking gems together creates powerful combinations — or, if done poorly, expensive disappointments.

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

Gems come in four colors, each aligned with different stats. The Guild Clerk finds the color-coding system needlessly complicated, but admits it does prevent Warriors from accidentally socketing healing spells.

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
| Weapon | 6 | Main skills |
| Body Armor | 6 | Primary skill setup |
| Helmet | 4 | Utility skills |
| Gloves | 4 | Secondary attacks |
| Boots | 4 | Movement, guards |
| Off Hand | 3 | Support skills |
| Amulet | 1 | Single gem |
| Ring | 1 | Single gem |

### Socket Colors

Sockets have colors that determine which gems can be placed:
- Red sockets accept 🔴 red gems
- Green sockets accept 🟢 green gems
- Blue sockets accept 🔵 blue gems
- White sockets accept ⚪ any gem color

**Socket Generation:**

The mathematics of socket generation are, in the Guild Clerk's assessment, the sort of thing that keeps certain heroes awake at night.

- Base socket chance: `30% + item level × 2%` (capped at 90%)
- White socket chance: 3% (rare enough to cause genuine excitement)
- Link chance: `20% + item level × 1%` (capped at 70%)

### Linking Sockets

Sockets can be **linked** together, shown by a bar connecting them. The more links, the more powerful your skill setup — and the more time you'll spend staring at equipment trying to find one with the right colors:

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

Gems gain XP when used in combat. The XP curve is exponential, which means early levels fly by and late levels feel like a personal vendetta from the universe:
- **+10 XP** per skill use
- XP requirement scales exponentially: `100 × 1.08^level`
- Max level: 100

### Level Scaling

As gems level up, they become more powerful but also more expensive to use — a tradeoff the Guild Clerk considers thematically appropriate for the adventuring profession:

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

At level 100, skills cost approximately 3× their base mana. The Guild Clerk has observed that this catches heroes by surprise roughly 100% of the time.

---

## Active Gems

Active gems are the skills your heroes actually use in combat. Each one has a mana cost, a color requirement, and varying degrees of "things exploding."

### Attack Skills (Red)

For heroes who prefer to resolve disagreements through direct physical contact.

| Gem | Type | Description |
|-----|------|-------------|
| **Greater Cleave** | AoE Melee | Swing weapon in arc, hitting all enemies |
| **Ground Slam** | AoE | Slam ground, damaging and stunning nearby |
| **Heavy Strike** | Single | Powerful single-target attack |
| **Flicker Strike** | Single | Teleport to enemy and strike |
| **Viper Strike** | Single | Poison-applying melee attack |

### Ranged Skills (Red/Green)

For heroes who prefer to resolve disagreements from a safer distance.

| Gem | Type | Description |
|-----|------|-------------|
| **Split Arrow** | AoE | Fire arrows that split to hit multiple targets |
| **Barrage** | Multi-hit | Rapid fire multiple arrows at one target |
| **Tornado Shot** | AoE | Arrows spiral outward after impact |

### Spell Skills (Blue)

Fire, lightning, ice, and chaos — the Mage's preferred vocabulary.

| Gem | Type | Description |
|-----|------|-------------|
| **Pyroblast** | Single | Massive fire damage, chance to ignite |
| **Arc** | Chain | Lightning chains between enemies |
| **Freezing Pulse** | AoE | Cold wave that can freeze targets |
| **Essence Drain** | DoT | Chaos damage over time, heals caster |

### Minion Skills (Blue)

The Necromancer's solution to being outnumbered: stop being outnumbered.

| Gem | Type | Description |
|-----|------|-------------|
| **Raise Zombie** | Summon | Raise a zombie from enemy corpse |
| **Summon Skeleton** | Summon | Summon a skeleton warrior |

### Healing Skills (Green)

The skills that make the rest of the party's recklessness survivable.

| Gem | Type | Description |
|-----|------|-------------|
| **Healing Light** | Single | Restore HP to lowest-health ally |
| **Rejuvenation** | HoT | Apply healing over time effect |
| **Divine Shield** | Shield | Grant temporary damage absorption |

### Guard Skills (Green)

Defensive skills, mostly for heroes who've learned what happens without them.

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

For tactical repositioning. Also for leaving approximately as fast as possible.

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

Support gems modify active skills they're linked to. They make everything better — and more expensive. The Guild Clerk has seen heroes socket Multistrike (1.6× mana cost) and then wonder why they're out of mana by turn three. They typically:
- Increase damage at a mana cost multiplier
- Add elemental damage
- Provide utility effects

### Damage Supports

The "more damage, more mana" school of gem design. The Guild Clerk has seen heroes stack three of these and then wonder why they're dry by turn two.

| Gem | Effect | Mana Multiplier |
|-----|--------|-----------------|
| **Increased Damage** | +% damage | 1.15× |
| **Added Fire Damage** | Add fire damage | 1.2× |
| **Added Cold Damage** | Add cold damage | 1.2× |
| **Added Lightning Damage** | Add lightning damage | 1.2× |
| **Increased Critical Strikes** | Higher crit chance | 1.3× |
| **Increased Critical Damage** | Higher crit multiplier | 1.25× |
| **Concentrated Effect** | More damage, smaller area | 1.4× |
| **Multistrike** | Attack multiple times | 1.6× |
| **Spell Echo** | Cast spells twice | 1.4× |
| **Melee Splash** | Melee hits nearby enemies | 1.3× |

### Utility Supports

Practical effects for practical heroes. The Life Leech gem, in particular, has saved more lives than most Clerics will admit.

| Gem | Effect | Mana Multiplier |
|-----|--------|-----------------|
| **Life Leech** | Gain HP from damage dealt | 1.25× |
| **Mana Leech** | Gain mana from damage dealt | 1.2× |
| **Increased Duration** | Buffs/debuffs last longer | 1.1× |
| **Increased Healing** | Stronger healing skills | 1.2× |
| **Minion Damage** | Minions deal more damage (Necromancer) | 1.3× |
| **Minion Life** | Minions have more HP (Necromancer) | 1.15× |

### Defensive Supports

For heroes who've discovered that dying is, on reflection, suboptimal.

| Gem | Effect | Mana Multiplier |
|-----|--------|-----------------|
| **Armor Reinforcement** | Increased armor | 1.1× |
| **Evasion Boost** | Increased evasion | 1.1× |
| **Energy Shield Boost** | Increased energy shield | 1.1× |
| **Damage Reduction** | Reduced damage taken | 1.1× |
| **Thorns** | Reflect damage to attackers | 1.1× |

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

*"A skilled hero is nothing without the gems to prove it — and a less skilled hero is nothing with them, either."*
