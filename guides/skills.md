# Skill Gems & Sockets

Hero's Guild uses a Path of Exile-inspired skill gem system, because apparently just "knowing how to fight" wasn't complicated enough. Skills are gems that you socket into equipment, and linking gems together creates powerful combinations — or, if done poorly, expensive disappointments.

## Core Concepts

### Skill Gems

Skills in Hero's Guild come as gems that can be:
- **Socketed** into equipment with matching socket colors
- **Leveled up** by gaining gem XP — gems get **10% of the hero's earned XP** every time the hero earns any. Gems do not level per skill use; they level as the hero does, like a dog that grows to resemble its owner. Max gem level 100.
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
| 🔴 **Red** | Slots into red sockets | All active attack gems, spell gems, minion gems, holy gems, and ranged-DEX gems are red regardless of stat requirement — that's why a Pyroblast spell (needs INT) and a Heavy Strike (needs STR) are both red |
| 🟢 **Green** | Slots into green sockets | Green covers defensive guards, warcries, movement, healing, and several utility spells — stat requirements vary (Healing Light needs INT; Smoke Bomb needs DEX; Enduring Cry needs STR) |
| 🔵 **Blue** | Slots into blue sockets | There are no active blue gems at all. Blue sockets exist for the **blue variants of support gems** (Increased Damage, Life Leech, etc. come in red/green/blue tri-color variants, with the blue variant requiring INT) |
| ⚪ **White** | Any color | Wild slots that accept any gem; rolled at 3% per socket |

Effectively: a gem's **color** tells you which socket it fits into, and its **stat requirement** tells you what the hero needs to use it. The two are decoupled.

---

## Socket System

### Equipment Sockets

Any equipped item can carry sockets — weapon, off hand, armour, helmet, gloves, boots, and both accessory slots — and how many it gets depends on its **rarity**, not on where you wear it. The realm distributes them with the generosity of a landlord:

| Rarity | Guaranteed | Maximum |
|--------|------------|---------|
| Common | 0 | 1 (5% chance) |
| Uncommon | 0 | 2 |
| Rare | 1 | 3 |
| Epic | 1 | 4 |
| Legendary | 2 | 5 |
| Mythic | 3 | 6 |
| Ancestral | 4 | 7 |

A Mythic ring has as many sockets as a Mythic breastplate. The ring finds this flattering; the breastplate has stopped mentioning it.

### Socket Colors

Sockets come in colours, and a socket is entirely inflexible about what it will accept:
- Red sockets accept 🔴 red gems
- Green sockets accept 🟢 green gems
- Blue sockets accept 🔵 blue gems
- White sockets accept ⚪ any gem color

**Socket Generation:**

The mathematics of socket generation are, in the Guild Clerk's assessment, the sort of thing that keeps certain heroes awake at night.

- Above the guaranteed sockets, each extra one rolls at `20% + item level × 1%` (capped at 90%), and the rolling **stops at the first failure** — so a long run of sockets is a long run of luck
- White socket chance: 3% per socket (rare enough to cause genuine excitement)
- The other colours lean by item: **weapons** mostly red, then green, then blue; **armour** mostly red, then blue, then green; **everything else** mostly blue, with green and red sharing the rest

Colours are rolled **once**, when the item's sockets first appear, and belong to the item from then on. Unequip it, vault it, hand it to another hero — the colours go with it. There is no re-rolling a bad set of sockets by taking the boots off and putting them on again, though heroes have been seen trying.

### Linking Sockets

Every socket on an item is **linked to every other socket on it**. There are no loose sockets and no link rolls: an item is one link group, however many sockets it has.

```
[🔴]—[🟢]—[🔵]—[🔴]  ← a four-socket item: one active skill, up to three supports
```

**Why Links Matter:**
- Each item holds **one active skill**, and every other gem on it supports that skill — eight equipment slots, at most eight active skills
- More sockets = more supports = stronger skills, but also a dearer and slower one (see [Cooldowns](#cooldowns) and [Mana Cost](#mana-cost-formula))
- A seven-socket Ancestral item is a six-support skill in one piece, and is treated by its owner accordingly

### Socket Placement Rules

Placement follows a strict hierarchy, enforced without sympathy:

- **The active goes in first.** A support on its own does nothing, so the game won't let you socket one into an item that has no active skill yet.
- **Active gems require an empty item.** You cannot place an active skill into an item that already holds any gem — clear it first.
- **Supports must be tag-compatible.** Once an item has an active gem, any new support must share a tag with it — a fire support has nothing to say to a healing spell. Incompatible supports are greyed out in the UI.
- **Cascade unsocket.** Removing an active gem also unsockets every support on that item, since supports with no active are inert. All ejected gems return to the hero's gem inventory.
- **Unequipping returns the gems.** Take an item off — by hand, by auto-equip, by selling it — and every gem in it goes back to its hero's gem inventory first. A sword in the vault casts nothing.
- **Duplicate supports stack.** You can socket two copies of the same support gem into one item — they stack in full rather than being deduplicated, and the Guild Clerk has been told, firmly, that this is how some people like their builds.

### Cooldowns

A gem skill's cooldown is the size of its link: **1 for the active, plus 1 for every compatible support linked to it** (duplicates each count), reduced by the hero's skill proficiency and the Archmage's Regalia set, rounded to the nearest round, and never below 1.

| Linked gems | Base cooldown |
|-------------|---------------|
| Active alone | 1 |
| Active + 2 supports | 3 |
| Active + 5 supports | 6 |

A skill with cooldown N sits out the next N rounds after it is cast. This applies to every kind of gem skill — damage, heals, guards, warcries and minions. Bigger links hit harder and come round less often, which is the trade at the heart of the whole system. In a raid, cooldowns carry from round to round, a raid being one very long fight.

The Gems tab, the gem tooltip and the item forge all show the **real** mana per cast and cooldown of each link, worked out the same way combat works it out.

### How Heroes Choose

Heroes pick their own skills in combat, and they pick the **strongest** one ready to fire — judged on the damage it would actually do with its linked supports included, every turn, against the enemies actually in front of them. Mana is not part of the judgement; a hero who can afford a skill will use the best one, and worry about the bill later.

---

## Gem Progression

### Gem XP

Gems do not gain XP per skill use. Each time the hero earns XP, **every equipped gem receives 10% of that XP** — gems level up alongside their wearer rather than through any particular usage pattern. The XP curve is exponential, which means early levels fly by and late levels feel like a personal vendetta from the universe:
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
          × each support's mana multiplier
          × (1 + 0.15 × number of supports)
          × (1 − the hero's mana cost reduction)        (minimum 1)
```

The third line is the link tax: every support adds 15% on top of its own multiplier, so a five-support link costs ×1.75 before its supports have even opened their invoices. At level 100, a bare skill costs approximately 3× its base mana. The Guild Clerk has observed that this catches heroes by surprise roughly 100% of the time.

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

Fire, lightning, ice, and chaos — the Mage's preferred vocabulary. These are all red even though they require INT — color is socket-gating, not stat-mapping (see the Gem Colors section).

| Gem | Type | Description |
|-----|------|-------------|
| **Pyroblast** | Single | Massive fire damage, chance to ignite |
| **Arc** | Chain | Lightning chains between enemies |
| **Freezing Pulse** | AoE | Cold wave that can freeze targets |
| **Essence Drain** | DoT | Chaos damage over time, heals caster |

Spell gems share the same damage pipeline as attack gems — they scale off a percentage of the weapon's base damage, plus their own flat damage — even a Mage's fireball owes something to the stick it came out of. Gems that fire secondary projectiles take a per-projectile damage penalty so that "more projectiles" stays a tradeoff rather than a free multiplier.

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
| **Healing Light** | AoE | Restore HP to **all allies** — the gem is area-of-effect by nature, from Cleric level 1; the Guardian ascendancy does not need to convert it |
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
| **Rallying Cry** | Party | Buffs the party's damage modifier for its duration; stacks *additively* with pre-combat additions (Courage blessing, Oath Sworn bond). When the warcry expires, only its own contribution is removed — pre-combat bonuses survive intact |
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
| **Multistrike** | Chance for an extra attack — a chance, not a promise | 1.6× |
| **Spell Echo** | Chance for an extra cast — likewise | 1.4× |
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
[Arc]—[Added Lightning]—[Concentrated Effect]—[Increased Critical Strikes]—[Mana Leech]
```
Result: Chaining lightning that hits harder per target, with raised crit chance and mana sustain.

**Cleric Healing (3-link):**
```
[Healing Light]—[Increased Healing]—[Increased Duration]
```
Result: AoE healing (Healing Light is already AoE at the gem level — see the gem note in the Spell Skills section) made stronger by Increased Healing and held longer by Increased Duration.

### Tips

1. **Match gem colors to sockets** - Plan your equipment around desired skill colors
2. **Balance mana costs** - Support gems multiply mana costs; don't overstack
3. **Any hero, any gem** - There are no class restrictions on gems; stat requirements (STR/DEX/INT) are the only gate, and a Warrior with enough INT may cast what they like
4. **Level your main skills** - Focus XP on your primary damage/healing gems
5. **Link count matters** - A 4-link with good supports beats a 6-link with bad ones

---

## Gem Sources

### Finding Gems

Gems turn up where the fighting is worst, and nowhere they can be bought:

| Source | Chance |
|--------|--------|
| Mission with a boss fight that doesn't fail | 10% at ⭐⭐⭐, 15% at ⭐⭐⭐⭐, 20% at ⭐⭐⭐⭐⭐ |
| Dungeon boss room | 10% / 15% / 20% at ⭐⭐⭐ / ⭐⭐⭐⭐ / ⭐⭐⭐⭐⭐ — **doubled** in Heroic dungeons |
| Heroic dungeon treasure room | 10% |
| Quest chain rewards | Named in the chain's rewards |

A drop is any gem at all, active or support, with no regard for who is in the party — so roughly two in three are supports, and the Necromancer's gem may very well go to the Warrior. Gems have no rarity; a gem's worth is its level and what you link to it.

### Gem Inventory

Every hero keeps a personal gem inventory, separate from their sockets, and **a gem belongs to the hero who found it**. It cannot be handed to another hero or sold — the one possession in the guild that is genuinely, permanently personal. A mission drop goes to a random survivor of the party, a dungeon find to the first hero still standing. If the wrong hero picked up the right gem, the only remedy is to make the wrong hero into the right one. Identical gems — same name, level and colour — are shown as one entry with a count, so a hero hoarding five Life Leeches is at least hoarding them tidily.

**Recycling.** You can *ask* a hero to recycle a gem they don't want. It is destroyed outright — nothing comes back but shelf space — and the hero has a say:

| | Chance to agree |
|---|---|
| Base | 70% |
| Ascetic | +25% |
| Kind | +15% |
| Empathic, Loyal | +10% each |
| Paranoid | −10% |
| Competitive | −15% |
| Jealous | −20% |
| Greedy | −40% |
| Limits | 5% to 95% |

Agreeing leaves a small **+2** thought for three days (*"Let a gem go. Lighter for it."*); refusing, a **−3** one (*"As if it were theirs to ask."*), and you may not ask about that gem again for **seven days**. A Greedy, Jealous hero is very unlikely ever to part with anything, which surprises nobody who has met one.

---

## Related Guides

- [Equipment & Items](equipment.md) - Socket system on gear
- [Combat System](combat.md) - How skills work in combat
- [Heroes & Classes](heroes.md) - Hero stats and progression

---

*"A skilled hero is nothing without the gems to prove it — and a less skilled hero is nothing with them, either."*
