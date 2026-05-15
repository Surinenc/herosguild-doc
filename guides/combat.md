# Combat System

Hero's Guild features a turn-based combat system of considerable depth, involving threat management, emotional outbursts, and the sort of dynamic social interactions that make you wonder why you sent these people into a dungeon together in the first place.

## Turn Structure

### Initiative

At the start of each combat round, turn order is determined by initiative:

```
Initiative = DEX + Random(1-10)
```

Higher initiative means acting earlier, which is particularly useful for heroes who subscribe to the "hit them before they hit you" school of combat philosophy. Turn order is recalculated each round, because consistency is for people who aren't being attacked by goblins.

### Round Flow

Every round resolves in the same four phases, in the same order, without exception, regardless of hero preference:

1. **Start of Turn** - Mana regenerates (5% of max mana)
2. **Cooldown Tick** - All skill cooldowns decrease by 1
3. **Actions** - Each combatant acts in initiative order
4. **End of Turn** - Buffs/debuffs tick down

### Available Actions

| Action | Description |
|--------|-------------|
| **Attack** | Basic weapon attack — the fallback when nothing more sophisticated is available, or when the Warrior decides nothing more sophisticated is necessary |
| **Skill** | Use an equipped skill gem or class ability; the reason heroes carry skill gems in the first place |
| **Defend** | 50% damage reduction until next turn; some heroes call this cowardice, others call it still being alive |
| **Flee** | Attempt to escape (30% + DEX + LCK/2 chance); feels lower than it sounds when you're actually trying it |

**Auto-Potions:** If a hero is below 50% HP at the start of their turn, they automatically drink a health potion (if available). This is, admittedly, the only consistently good decision most heroes make without supervision.

---

## Damage Calculation

### Hero Damage

**Base Damage Formula:**

```
Base Damage = (Avg Weapon Damage + Equipment Damage) × (1 + Stat Bonus / 100)
```

**Stat Bonus by Class:**

| Class | Stat Bonus |
|-------|------------|
| Warrior | STR × 0.20 |
| Rogue | DEX × 0.15 |
| Ranger | DEX × 0.15 |
| Cleric | INT × 0.10 + STR × 0.05 |
| Mage | INT × 0.18 |
| Necromancer | INT × 0.18 |
| Paladin (ascendancy) | INT × 0.12 + STR × 0.12 |

Higher stats provide a multiplicative bonus — for example, 100 stat points = +100% weapon damage. This is why experienced guild masters invest in training rather than just handing heroes a bigger sword and hoping for the best.

**Modifiers Applied (multiplicative):**
- **Class damage multiplier** — Mage/Necromancer ×1.25, Rogue/Ranger ×0.80, Warrior/Cleric ×1.00. Applied at every hero-source damage point as a top-level cap on relative class power.
- **Lifecycle damage multiplier** — each hero's [background events](backgrounds.md) compound into a per-hero `damage` multiplier applied on top of everything else. This is the reason two heroes with identical class, level, and equipment will not hit for the same numbers: their pasts disagree about what their hands are capable of.
- Skill damage percentage (e.g., Power Attack = 150%)
- [Passive tree](passive-tree.md) bonuses
- Weapon proficiency (0-38% at max level 20)
- Skill proficiency (0-30% at max level 20)
- Monster knowledge (up to +20%)
- Equipment set bonuses
- Ascendancy bonuses
- Relationship modifier (up to ±25%)
- Mood modifier
- Damage variance (±10%)

The class multiplier exists to keep the spread between best- and worst-case builds within a single weight class — physical Rogue/Ranger top builds were pulling several times the DPS of casters before it was added. Casters get the lift in the same direction. The Guild Clerk considers this fair. The Rogues do not, but the Rogues have never considered anything fair, and this is itself part of the design.

### Critical Hits

When the numbers align, attacks deal significantly more damage. The numbers do not always align:

```
Crit Chance = 5% + (DEX / 20) + (LCK / 10) + bonuses
Crit Multiplier = 1.5× (base) + (bonus crit damage% / 100)
```

### Armor and Damage Reduction

```
Armor Reduction = sqrt(Armor × 2) × 100 / (50 + Enemy Level × 0.5)
```

Capped at 95%. Minimum damage dealt is always 1. The square root in the formula ensures diminishing returns, which is the universe's way of telling Warriors that a third piece of plate armor is not, in fact, the answer to everything.

**Defense Modifiers:**
- Defending: 50% damage reduction
- Shield Wall: 50% damage reduction

### Evasion

Evasion uses an entropy-based system (similar to Path of Exile 2) to ensure consistent dodge patterns rather than pure randomness. This means a hero with 50% evasion will reliably dodge every other attack, rather than getting hit seventeen times in a row and writing a strongly-worded complaint to the Guild Clerk's office.

```
Evasion Rating = DEX + (LCK × 0.5) + flat evasion bonuses
Evasion Chance = sqrt(Evasion Rating × 2) × 100 / (50 + Enemy Level × 0.5)
```

Capped at 95%. The entropy system ensures that if you have 50% evasion, you will always evade every other attack rather than getting unlucky streaks.

### Energy Shield

Mages and Necromancers, being too physically fragile to survive combat through conventional means like "having health," instead maintain an energy shield that absorbs damage before HP:

```
Energy Shield = INT × 5
```

- Absorbs all damage before HP is touched
- Recharges 10% of max ES per round if not hit that round
- Other classes have 0 base energy shield (can gain from gear)

### Guardian Shield

Certain ascendancy and passive tree effects grant the **Heal Grants Shield** bonus — when a hero heals an ally, a percentage of the heal amount is applied as a temporary shield (bonus HP that absorbs damage before the hero's actual health is touched).

- Stacks with multiple heals
- Absorbed damage is reduced before reaching HP or Energy Shield
- The `shieldAbsorbBonus` stat makes shields absorb more efficiently (shields take less damage per point absorbed)
- Separate from Energy Shield — Guardian Shield comes from healing, Energy Shield comes from INT

This is primarily a Cleric mechanic (Prophet and Paladin ascendancy paths), and the reason well-supported parties survive significantly longer than ones that consider healing optional.

### Life Steal

Life steal has diminishing returns via a square root formula, because the universe is fundamentally opposed to anyone becoming truly immortal through violence alone:

```
Heal Amount = floor(sqrt(Damage × Life Steal% / 100 × 100))
```

Examples: 100 damage at 10% steal → 31 HP, 500 damage → ~70 HP, 2500 damage → ~158 HP.

---

## Threat System

Enemies use threat to determine who to attack. Higher threat means more attention from things that want to kill you, which is either the entire point (Warriors) or a catastrophic failure of planning (everyone else).

### Starting Threat

| Class | Starting Threat |
|-------|-----------------|
| Warrior | 50 |
| All Others | 10 |

### Generating Threat

| Action | Threat Generated |
|--------|------------------|
| Dealing Damage | Amount × 1.0 (Warriors: × 1.5) |
| Healing | Amount × 0.5 |
| Taunt | +200 |
| Shield Wall | +50 |

### Enemy Targeting Logic

1. **Taunted?** - Must attack the taunter
2. **50% Chance** - Target highest threat hero
3. **25% Chance** - Target wounded hero (<50% HP)
4. **Otherwise** - Random weighted by threat

---

## Warrior Skills: Taunt & Shield Wall

### Taunt

- **Effect:** Forces ALL enemies to attack the Warrior
- **Duration:** 2 turns (+ ascendancy bonuses)
- **Threat Bonus:** +200
- **Cooldown:** 3 turns
- **Best Used:** When squishy allies are being targeted, which is to say, constantly

### Shield Wall

- **Effect:** 50% damage reduction
- **Duration:** 2 turns (+ ascendancy bonuses)
- **Threat Bonus:** +50
- **Cooldown:** 3 turns
- **Best Used:** After Taunt, or when expecting heavy damage (also constantly)

**Pro Tip:** Taunt first, then Shield Wall. The traditional "stand there and get hit" approach, but done professionally.

---

## The Intervene Mechanic

One of the most dramatic combat features — and the one responsible for approximately 80% of all post-mission tavern stories. When things go horribly wrong, heroes can save each other from death.

### How It Works

When a hero would receive a **killing blow**, allies may intervene:

1. Ally takes 50% of the damage instead
2. Original target survives with no damage
3. Massive relationship boost between them
4. Creates the kind of moment that bards write songs about (and that the Guild Clerk writes incident reports about)

### Requirements

- Ally has positive relationship (30+) with target
- Ally is alive
- Ally hasn't intervened yet this combat (unless they have the Double Intervene ascendancy bonus)

### Intervene Chance

| Relationship | Base Chance |
|--------------|-------------|
| Friend (30-49) | 20% |
| Close Friend (50-79) | 40% |
| Best Friend (80+) | 60% |

**Modifiers:**
- Warrior class: +20%
- Lovers/Married: +25%
- Life Debt bond: +30%
- Maximum: 90%

### Relationship Impact

- Saved hero: +30 trust toward savior
- Savior: +15 protective instinct toward saved
- May trigger "Inspired" emotional state

---

## Emotional States

Combat can trigger powerful emotional reactions based on relationships. This is what happens when you send people who care about each other into mortal danger — they develop feelings about it.

| State | Effect | Duration | Trigger |
|-------|--------|----------|---------|
| **Normal** | None | - | Default |
| **Inspired** | +15% all stats | 3 turns | Saved by ally |
| **Panicked** | 40% skip turn | 2 turns | Coward trait + ally death |
| **Grief** | -20% all stats | 2-3 turns | Friend dies |
| **Enraged** | +30% damage, focuses target | 2-3 turns | Close friend dies |
| **Vengeful** | +20% vs specific enemy | 4-6 turns | Mentor/student dies |
| **Berserk** | +50% damage, -30% defense, random target | 4-5 turns | Lover dies |
| **Broken** | Cannot act | 4 turns | Extreme trauma |

### Death Reactions

When an ally dies, heroes react based on their relationship. These reactions are not optional, not controllable, and not particularly convenient:

| Relationship | Possible States |
|--------------|-----------------|
| Enemy/Nemesis | Inspired (relief!) |
| Lover/Married | Berserk (40%), Broken (30%), Vengeful (30%) |
| Best Friend | Berserk (30%), Grief (20%), Enraged (50%) |
| Close Friend | Enraged (50%), Grief (50%) |

---

## Skills and Abilities

### Default Class Skills

Every hero starts with a set of class skills before any gem customization. These represent each class's foundational combat identity — which is a polite way of saying "what they do when no one has given them anything more interesting."

**Warrior:** *Stand there and get hit, professionally.*
- Strike - 100% damage basic attack
- Power Attack - 150% damage, 2-turn cooldown
- Cleave - 80% damage AoE, 3-turn cooldown
- Taunt - Forces enemies to attack you, 3-turn cooldown
- Shield Wall - 50% damage reduction, 3-turn cooldown

**Cleric:** *Split their effort between hurting enemies and repairing heroes, with variable success.*
- Smite - 90% damage holy attack
- Holy Fire - 110% damage, 2-turn cooldown
- Heal - Single target restoration, 2-turn cooldown
- Prayer of Healing - AoE healing, 4-turn cooldown

**Mage:** *Prefers not to be touched while working.*
- Staff Strike - 60% damage basic attack
- Fireball - 130% damage with 30% ignite chance, 2-turn cooldown
- Frost Nova - 60% AoE damage with 25% freeze chance, 3-turn cooldown

**Rogue:** *Every attack is described as a precision strike. Some of them are.*
- Stab - 100% damage basic attack
- Backstab - 200% damage single target, 3-turn cooldown
- Fan of Knives - 70% damage AoE, 2-turn cooldown

**Ranger:** *Attacks from a distance, where things cannot hit back. A sensible policy.*
- Arrow Shot - 100% damage basic attack
- Multi-Shot - 70% damage AoE, 2-turn cooldown
- Power Shot - 160% damage single target, 2-turn cooldown

**Necromancer:** *Makes death work for them rather than against them, which is the principal advantage their colleagues lack.*
- Dark Touch - 80% damage basic attack
- Soul Drain - 100% damage with 100% lifesteal, 2-turn cooldown
- Curse of Weakness - 60% AoE, 80% chance to weaken for 3 turns, 3-turn cooldown

**Note:** Berserker and Gladiator ascendancies lose Taunt and Shield Wall, keeping only Strike, Power Attack, and Cleave. Paladin ascendancy replaces Heal and Prayer of Healing with Divine Strike (120% damage) and Consecrate.

### Skill Gems

Equip skill gems in your weapon sockets for additional abilities. See [Equipment Guide](equipment.md) for details.

### Skill Proficiency

Using skills improves proficiency, which is the game's way of rewarding you for doing the same thing over and over (also known as "combat"):

| Bonus Type | Rate | Maximum (Level 20) |
|------------|------|---------------------|
| Damage | +1.5% per level | +30% |
| Mana Cost Reduction | -1% per level | -20% |
| Cooldown Reduction | -0.75% per level | -15% |

**Proficiency XP Formula:** `50 × (Level + 1)^1.6` XP to next level. Max level 20.

---

## Monster Knowledge

As heroes fight the same enemy types, they gradually learn their weaknesses — a process best described as "educational violence."

### Knowledge Levels

| Kills | Level | Damage Bonus | Crit Bonus |
|-------|-------|--------------|------------|
| 5 | Known | +5% | - |
| 20 | Studied | +10% | - |
| 50 | Expert | +15% | - |
| 100 | Slayer | +20% | +5% crit |

Monster knowledge is tracked per hero per enemy type. The Slayer level grants bonus critical hit chance against that enemy, which seems fair after you've killed a hundred of them.

---

## Status Effects

### Damage Over Time

| Effect | Duration | Damage |
|--------|----------|--------|
| Poison | 4 turns | % of damage dealt per turn |
| Burn | 3 turns | Fire damage per turn (30% ignite chance from Fireball) |
| Bleed | 3 turns | 20% of damage dealt per tick (+ bleed damage bonuses) |

Bleed and poison damage scale from the hit that applied them, not from max HP. Ascendancy bonuses can increase DoT damage significantly — the Berserker's bleed build, in particular, has been described by surviving enemies as "deeply unfair."

### Control Effects

| Effect | Duration | Impact |
|--------|----------|--------|
| Stun | 1 turn | Skip turn |
| Freeze | 1 turn | Skip turn (25% chance from Frost Nova) |
| Shock | 2 turns | Target takes +20% damage |
| Weaken | 3 turns | Reduced damage dealt |

### Elemental Procs

Skills with elemental damage types have a chance to trigger corresponding status effects. The proc chance comes from gear, passive tree, and ascendancy bonuses:

| Damage Type | Proc Effect | What It Does |
|------------|-------------|-------------|
| **Fire** | Ignite | Applies Burn (10 fire damage/turn for 3 turns) |
| **Cold** | Freeze | Applies Stun for 1 turn |
| **Lightning** | Shock | Target takes +20% increased damage for 2 turns |

A fire skill with 30% ignite chance will proc Burn roughly every third hit. Freeze chance stacks from gear and ascendancy sources. These procs are separate from on-hit effects — a fire skill can both ignite and trigger on-hit bleed if you have both stats.

### On-Hit Effects

Some ascendancy and gear bonuses apply effects on every hit, because merely hitting someone once wasn't considered thorough enough:
- **Bleed on Hit** - Apply bleed (default 20% of damage per tick, 3 turns)
- **Poison on Hit** - Apply poison (default 15% of damage per tick, 4 turns)
- **Burn Spread** - Burns spread to up to 2 nearby unburned enemies
- **Poison Spread** - Poison spreads to up to 2 nearby unpoisoned enemies
- **Chain Lightning** - Attacks chain to additional enemies at 50% damage

---

## Boss Fights

Boss enemies have multiple phases that activate at HP thresholds. This is their way of informing you that the fight is not, in fact, nearly over.

### Phase Transitions

When a boss drops below a phase threshold:
- Stats may increase (damage, armor)
- New abilities unlock
- Phase entry effect triggers

### Phase Entry Effects

| Effect | Description |
|--------|-------------|
| Heal | Recovers 10% HP. The boss is, in other words, not finished. |
| Enrage | +20% damage, permanently. It does not calm down. |
| Summon | Reinforcements arrive — the dungeon's way of noting the fight has not concluded |
| Shield | +50% armor, permanently. The approach that was working needs adjusting. |
| AoE | All heroes take significant damage simultaneously. This is the warning. |

**Strategy:** Plan for phase transitions. Save defensive cooldowns for dangerous phases. If the boss starts glowing, that's generally a sign that things are about to become worse.

---

## Combat Tips

### General Strategies

1. **Protect Your Healer** - Dead clerics mean dead parties. This is not a suggestion.
2. **Control Threat** - Use Warrior Taunt to dictate targeting. The Warrior's job is to be hit. They are, one assumes, fine with this.
3. **Focus Fire** - Kill one enemy fast rather than wounding many. A half-dead goblin is just as dangerous as a fully healthy one, but significantly angrier.
4. **Watch Initiative** - Know who acts when
5. **Save Cooldowns** - Don't blow everything turn 1. Overconfidence is the leading cause of party wipes, closely followed by underleveled equipment.

### Party Composition

**Balanced Party (Recommended, 4-6 heroes):**
- 1-2 Warriors (Tank)
- 1-2 Clerics (Healer)
- 2-3 DPS (any combination)

**Speed Run Party:**
- 2-3 Rogues, 2-3 Mages
- Kill fast before damage matters. Also known as "the optimist's formation."

**Survival Party:**
- 2 Warriors, 2 Clerics, 2 DPS
- Slow but very safe. Recommended for guild masters who've grown attached to their heroes.

### Relationship Bonuses

Heroes fight better alongside friends and worse alongside enemies, because professionalism in the adventuring industry is, at best, aspirational:

| Relationship | Damage Modifier |
|--------------|-----------------|
| Devoted (95+) | +25% |
| Best Friend (80-94) | +20% |
| Close Friend (60-79) | +15% |
| Friend (30-59) | +10% |
| Friendly (10-29) | +5% |
| Neutral (-9 to 9) | 0% |
| Annoyed (-10 to -20) | -3% |
| Dislike (-21 to -35) | -8% |
| Rival (-36 to -55) | -12% |
| Hostile (-56 to -75) | -18% |
| Enemy (-76 to -100) | -25% |

**Warning:** Lovers can go Berserk or Broken if their partner dies. Consider the risk. Love is a battlefield, and in this case, that's literally true.

---

## Ambush Mechanic

Some dungeon encounters start with enemies ambushing your party, which is deeply inconsiderate of them.

### What Happens

- Enemies gain massive initiative bonus (+10,000)
- Enemies always act first on turn 0
- No time to prepare or buff

### Counter-Strategies

- Keep tank HP high (absorb first strikes)
- Use Guardian Shield passives
- Ranger "First Strike" can counter
- Stay healthy between encounters

### Ambush Indicators

- "AMBUSH!" message at combat start
- Higher chance in Swamp and Crypt dungeons

---

## Combat Results

### Victory

All enemies defeated. The part everyone came for:
- Gain gold drops
- Gain XP (split among alive heroes)
- Loot rolled per enemy
- Relationship changes processed

### Defeat

All heroes knocked out. The dungeon has, in the technical sense, won:
- Dungeon failed
- Heroes may have injuries
- Death saves rolled for 0 HP heroes
- Lost items and gold

### Fled

Successful escape — the tactical decision the Guild Clerk officially discourages and quietly recommends:
- No rewards
- Party safely exits
- Better than a wipe

---

## Related Guides

- [Heroes & Classes](heroes.md) - Class abilities and stats
- [Equipment & Items](equipment.md) - Weapons and skill gems
- [Relationships](relationships.md) - How bonds affect combat

---

*"The difference between victory and defeat often comes down to a single intervene — and whether anyone likes each other enough to bother."*
