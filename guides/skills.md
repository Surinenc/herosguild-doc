# Skill Gems & Sockets

Hero's Guild uses a Path of Exile-inspired skill gem system, because apparently just "knowing how to fight" wasn't complicated enough. Skills are gems that you socket into equipment, and linking gems together creates powerful combinations — or, if done poorly, expensive disappointments.

## Core Concepts

### Skill Gems

Skills in Hero's Guild come as gems that can be:
- **Socketed** into equipment with matching socket colors
- **Leveled up** by gaining gem XP — gems get **10% of the hero's earned XP** every time the hero levels (`Hero.ts:1497-1508`). Gems do not level per skill use; they level as the hero levels. Max gem level 100.
- **Linked** with support gems to enhance their effects

### Gem Types

| Type | Symbol | Description |
|------|--------|-------------|
| **Active** | ● | Skills you use in combat (attacks, spells, buffs) |
| **Support** | ◇ | Modify active skills they're linked to |

### Gem Colors

Gems come in colors that determine which sockets they can be slotted into. Color does **not** strictly map to stat in the way other ARPGs use it — colors gate socket compatibility, while each gem's actual stat requirement (STR / DEX / INT) is on the gem itself.

| Color | Socket gate | Notes |
|-------|-------------|-------|
| 🔴 **Red** | Slots into red sockets | All active attack gems, spell gems, minion gems, holy gems, and ranged-DEX gems are stored under the `RED_ACTIVE_GEMS` catalogue regardless of stat requirement — that's why a Pyroblast spell (needs INT) and a Heavy Strike (needs STR) are both red |
| 🟢 **Green** | Slots into green sockets | The `GREEN_ACTIVE_GEMS` catalogue covers defensive guards, warcries, movement, healing, and several utility spells — stat requirements vary (Healing Light needs INT; Smoke Bomb needs DEX; Enduring Cry needs STR) |
| 🔵 **Blue** | Slots into blue sockets | `BLUE_ACTIVE_GEMS` is currently empty — there are no active blue gems. Blue sockets exist for the **blue variants of support gems** (Increased Damage, Life Leech, etc. come in red/green/blue tri-color variants, with the blue variant requiring INT) |
| ⚪ **White** | Any color | Wild slots that accept any gem; rolled at 3% per socket |

Effectively: a gem's **color** tells you which socket it fits into, and its **requirements field** tells you what stat the hero needs to use it. The two are decoupled.

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

Gems do not gain XP per skill use. Each time the hero earns XP, **every equipped gem receives 10% of that XP** — gems level up alongside their wearer rather than through any particular usage pattern (`Hero.ts:1497-1508`). The XP curve is exponential, which means early levels fly by and late levels feel like a personal vendetta from the universe:
- **10% of hero XP** per hero XP gain, distributed to every equipped gem
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
| **Tornado Shot** | AoE | Primary shot plus one secondary projectile that spirals outward; lower per-hit damage than a single-target equivalent in exchange for the extra hit |

### Spell Skills (Red)

Fire, lightning, ice, and chaos — the Mage's preferred vocabulary. These all live in the red `RED_ACTIVE_GEMS` catalogue even though they require INT — color is socket-gating, not stat-mapping (see the Gem Colors section).

| Gem | Type | Description |
|-----|------|-------------|
| **Pyroblast** | Single | Massive fire damage, chance to ignite |
| **Arc** | Chain | Lightning chains between enemies |
| **Freezing Pulse** | AoE | Cold wave that can freeze targets |
| **Essence Drain** | DoT | Chaos damage over time, heals caster |

Spell gems share the same damage pipeline as attack gems — they scale off the linked weapon's base damage via `base_damage_percent`, plus their own flat damage. Gems that fire secondary projectiles take a per-projectile damage penalty so that "more projectiles" stays a tradeoff rather than a free multiplier.

### Minion Skills (Red)

The Necromancer's solution to being outnumbered: stop being outnumbered. Raise Zombie and Summon Skeleton are red-color gems requiring INT.

| Gem | Type | Description |
|-----|------|-------------|
| **Raise Zombie** | Summon | Raise a zombie from enemy corpse |
| **Summon Skeleton** | Summon | Summon a skeleton warrior |

### Healing Skills (Green)

The skills that make the rest of the party's recklessness survivable.

| Gem | Type | Description |
|-----|------|-------------|
| **Healing Light** | AoE | Restore HP to **all allies** — the gem carries the `aoe` tag, so the AoE pattern is baked in at Cleric level 1; the Guardian ascendancy does not need to convert it |
| **Rejuvenation** | HoT | Apply healing over time effect |
| **Divine Shield** | Shield | Grant temporary damage absorption |
| **Life Tap** | Self HoT (Necromancer) | Sustained percent-life regen for 5 turns. Free to cast — the cost is having to be a Necromancer. |

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
| **Steady Aim** | Self HoT (Ranger) | Grants life regen while active; the Ranger's quiet 4-turn promise that they are about to do something competent |
| **Unholy Vigor** | Self HoT (Necromancer) | Sustained life regen via dark vitality; "darkness is surprisingly nurturing if you ask nicely" |

### Movement Skills (Green)

For tactical repositioning. Also for leaving approximately as fast as possible.

| Gem | Type | Description |
|-----|------|-------------|
| **Evasive Roll** | Self | Dodge and reposition |
| **Smoke Bomb** | Guard / AoE | Swirling cloak of smoke absorbs a percentage of incoming damage; visibility ruined for both parties, only one minds |
| **Shadow Step** | Teleport | Instant teleport behind enemy |

### Holy Skills (Red)

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
| **Multistrike** | Chance for an extra attack (probability-based — `extra_attack_chance`) | 1.6× |
| **Spell Echo** | Chance for an extra cast (probability-based — `extra_cast_chance`) | 1.4× |
| **Melee Splash** | Melee hits nearby enemies | 1.3× |

### Utility Supports

Practical effects for practical heroes. The Life Leech gem, in particular, has saved more lives than most Clerics will admit.

| Gem | Effect | Mana Multiplier |
|-----|--------|-----------------|
| **Life Leech** | Gain HP from damage dealt (2% baseline, scales with gem level) | 1.25× |
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
