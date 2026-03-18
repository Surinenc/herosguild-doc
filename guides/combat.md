# Combat System

Hero's Guild features a deep turn-based combat system with threat management, emotional reactions, and dynamic social interactions.

## Turn Structure

### Initiative

At the start of each combat round, turn order is determined by initiative:

```
Initiative = DEX + Random(1-10)
```

Higher initiative means acting earlier. Turn order is recalculated each round.

### Round Flow

1. **Start of Turn** - Mana regenerates (5% of max mana)
2. **Cooldown Tick** - All skill cooldowns decrease by 1
3. **Actions** - Each combatant acts in initiative order
4. **End of Turn** - Buffs/debuffs tick down

### Available Actions

| Action | Description |
|--------|-------------|
| **Attack** | Basic weapon attack against an enemy |
| **Skill** | Use an equipped skill gem or class ability |
| **Defend** | 50% damage reduction until next turn |
| **Flee** | Attempt to escape (30% + DEX + LCK/2 chance) |

**Auto-Potions:** If a hero is below 50% HP at the start of their turn, they automatically drink a health potion (if available).

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

Higher stats provide a multiplicative bonus — for example, 100 stat points = +100% weapon damage.

**Modifiers Applied (multiplicative):**
- Skill damage percentage (e.g., Power Attack = 150%)
- Passive tree bonuses
- Weapon proficiency (0-38% at max level 20)
- Skill proficiency (0-30% at max level 20)
- Monster knowledge (up to +20%)
- Equipment set bonuses
- Ascendancy bonuses
- Relationship modifier (up to ±25%)
- Mood modifier
- Damage variance (±10%)

### Critical Hits

```
Crit Chance = 5% + (DEX / 20) + (LCK / 10) + bonuses
Crit Multiplier = 1.5× (base) + (bonus crit damage% / 100)
```

### Armor and Damage Reduction

```
Armor Reduction = sqrt(Armor × 2) × 100 / (50 + Enemy Level × 0.5)
```

Capped at 95%. Minimum damage dealt is always 1.

**Defense Modifiers:**
- Defending: 50% damage reduction
- Shield Wall: 50% damage reduction

### Evasion

Evasion uses an entropy-based system (similar to Path of Exile 2) to ensure consistent dodge patterns rather than pure randomness.

```
Evasion Rating = DEX + (LCK × 0.5) + flat evasion bonuses
Evasion Chance = sqrt(Evasion Rating × 2) × 100 / (50 + Enemy Level × 0.5)
```

Capped at 95%. The entropy system ensures that if you have 50% evasion, you will always evade every other attack rather than getting unlucky streaks.

### Energy Shield

Mages and Necromancers have an energy shield that absorbs damage before HP:

```
Energy Shield = INT × 5
```

- Absorbs all damage before HP is touched
- Recharges 10% of max ES per round if not hit that round
- Other classes have 0 base energy shield (can gain from gear)

### Life Steal

Life steal has diminishing returns via a square root formula:

```
Heal Amount = floor(sqrt(Damage × Life Steal% / 100 × 100))
```

Examples: 100 damage at 10% steal → 10 HP, 500 damage → ~22 HP, 2500 damage → ~50 HP.

---

## Threat System

Enemies use threat to determine who to attack. Higher threat = more likely to be targeted.

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
- **Best Used:** When squishy allies are being targeted

### Shield Wall

- **Effect:** 50% damage reduction
- **Duration:** 2 turns (+ ascendancy bonuses)
- **Threat Bonus:** +50
- **Cooldown:** 3 turns
- **Best Used:** After Taunt, or when expecting heavy damage

**Pro Tip:** Taunt first, then Shield Wall for maximum party protection.

---

## The Intervene Mechanic

One of the most dramatic combat features: heroes can save each other from death!

### How It Works

When a hero would receive a **killing blow**, allies may intervene:

1. Ally takes 50% of the damage instead
2. Original target survives with no damage
3. Massive relationship boost between them
4. Creates memorable combat moments

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

Combat can trigger powerful emotional reactions based on relationships.

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

When an ally dies, heroes react based on their relationship:

| Relationship | Possible States |
|--------------|-----------------|
| Enemy/Nemesis | Inspired (relief!) |
| Lover/Married | Berserk (40%), Broken (30%), Vengeful (30%) |
| Best Friend | Berserk (30%), Grief (20%), Enraged (50%) |
| Close Friend | Enraged (50%), Grief (50%) |

---

## Skills and Abilities

### Default Class Skills

**Warrior:**
- Strike - 100% damage basic attack
- Power Attack - 150% damage, 2-turn cooldown
- Cleave - 80% damage AoE, 3-turn cooldown
- Taunt - Forces enemies to attack you, 3-turn cooldown
- Shield Wall - 50% damage reduction, 3-turn cooldown

**Cleric:**
- Smite - 90% damage holy attack
- Holy Fire - 110% damage, 2-turn cooldown
- Heal - Single target restoration, 2-turn cooldown
- Prayer of Healing - AoE healing, 4-turn cooldown

**Mage:**
- Staff Strike - 60% damage basic attack
- Fireball - 130% damage with 30% ignite chance, 2-turn cooldown
- Frost Nova - 60% AoE damage with 25% freeze chance, 3-turn cooldown

**Rogue:**
- Stab - 100% damage basic attack
- Backstab - 200% damage single target, 3-turn cooldown
- Fan of Knives - 70% damage AoE, 2-turn cooldown

**Ranger:**
- Arrow Shot - 100% damage basic attack
- Multi-Shot - 70% damage AoE, 2-turn cooldown
- Power Shot - 160% damage single target, 2-turn cooldown

**Necromancer:**
- Dark Touch - 80% damage basic attack
- Soul Drain - 100% damage with 100% lifesteal, 2-turn cooldown
- Curse of Weakness - 60% AoE, 80% chance to weaken for 3 turns, 3-turn cooldown

**Note:** Berserker and Gladiator ascendancies lose Taunt and Shield Wall, keeping only Strike, Power Attack, and Cleave. Paladin ascendancy replaces Heal and Prayer of Healing with Divine Strike (120% damage) and Consecrate.

### Skill Gems

Equip skill gems in your weapon sockets for additional abilities. See [Equipment Guide](equipment.md) for details.

### Skill Proficiency

Using skills improves proficiency, granting stacking bonuses:

| Bonus Type | Rate | Maximum (Level 20) |
|------------|------|---------------------|
| Damage | +1.5% per level | +30% |
| Mana Cost Reduction | -1% per level | -20% |
| Cooldown Reduction | -0.75% per level | -15% |

**Proficiency XP Formula:** `50 × (Level + 1)^1.6` XP to next level. Max level 20.

---

## Monster Knowledge

As heroes fight the same enemy types, they learn their weaknesses.

### Knowledge Levels

| Kills | Level | Damage Bonus | Crit Bonus |
|-------|-------|--------------|------------|
| 5 | Known | +5% | - |
| 20 | Studied | +10% | - |
| 50 | Expert | +15% | - |
| 100 | Slayer | +20% | +5% crit |

Monster knowledge is tracked per hero per enemy type. The Slayer level grants bonus critical hit chance against that enemy.

---

## Status Effects

### Damage Over Time

| Effect | Duration | Damage |
|--------|----------|--------|
| Poison | 4 turns | % of damage dealt per turn |
| Burn | 3 turns | Fire damage per turn (30% ignite chance from Fireball) |
| Bleed | 3 turns | 20% of damage dealt per tick (+ bleed damage bonuses) |

Bleed and poison damage scale from the hit that applied them, not from max HP. Ascendancy bonuses can increase DoT damage significantly.

### Control Effects

| Effect | Duration | Impact |
|--------|----------|--------|
| Stun | 1 turn | Skip turn |
| Freeze | 1 turn | Skip turn (25% chance from Frost Nova) |
| Shock | 2 turns | Target takes +20% damage |
| Weaken | 3 turns | Reduced damage dealt |

### On-Hit Effects

Some ascendancy and gear bonuses apply effects on every hit:
- **Bleed on Hit** - Apply bleed (default 20% of damage per tick, 3 turns)
- **Poison on Hit** - Apply poison (default 15% of damage per tick, 4 turns)
- **Burn Spread** - Burns spread to up to 2 nearby unburned enemies
- **Poison Spread** - Poison spreads to up to 2 nearby unpoisoned enemies
- **Chain Lightning** - Attacks chain to additional enemies at 50% damage

---

## Boss Fights

Boss enemies have multiple phases that activate at HP thresholds.

### Phase Transitions

When a boss drops below a phase threshold:
- Stats may increase (damage, armor)
- New abilities unlock
- Phase entry effect triggers

### Phase Entry Effects

| Effect | Description |
|--------|-------------|
| Heal | Regenerate 10% HP |
| Enrage | +20% damage permanently |
| Summon | Spawn minion reinforcements |
| Shield | +50% armor permanently |
| AoE | Devastating attack on all heroes |

**Strategy:** Plan for phase transitions. Save defensive cooldowns for dangerous phases.

---

## Combat Tips

### General Strategies

1. **Protect Your Healer** - Dead clerics mean dead parties
2. **Control Threat** - Use Warrior Taunt to dictate targeting
3. **Focus Fire** - Kill one enemy fast rather than wounding many
4. **Watch Initiative** - Know who acts when
5. **Save Cooldowns** - Don't blow everything turn 1

### Party Composition

**Balanced Party (Recommended):**
- 1 Warrior (Tank)
- 1 Cleric (Healer)
- 2 DPS (any combination)

**Speed Run Party:**
- 2 Rogues, 2 Mages
- Kill fast before damage matters

**Survival Party:**
- 2 Warriors, 2 Clerics
- Slow but very safe

### Relationship Bonuses

Heroes fight better alongside friends. Relationship combat damage modifiers:

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

**Warning:** Lovers can go Berserk or Broken if their partner dies. Consider the risk.

---

## Ambush Mechanic

Some dungeon encounters start with enemies ambushing your party.

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

All enemies defeated:
- Gain gold drops
- Gain XP (split among alive heroes)
- Loot rolled per enemy
- Relationship changes processed

### Defeat

All heroes knocked out:
- Dungeon failed
- Heroes may have injuries
- Death saves rolled for 0 HP heroes
- Lost items and gold

### Fled

Successful escape:
- No rewards
- Party safely exits
- Better than a wipe!

---

## Related Guides

- [Heroes & Classes](heroes.md) - Class abilities and stats
- [Equipment & Items](equipment.md) - Weapons and skill gems
- [Relationships](relationships.md) - How bonds affect combat

---

*"The difference between victory and defeat often comes down to a single intervene."*
