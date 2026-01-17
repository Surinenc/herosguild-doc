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

```
Base Damage = Weapon Damage + Stat Scaling
```

**Stat Scaling by Class:**
- **Warrior:** STR × 1.5
- **Mage:** INT × 1.7
- **Rogue:** DEX × 1.5
- **Cleric:** INT × 1.0 + STR × 0.5
- **Ranger:** DEX × 2.0
- **Necromancer:** INT × 3.0

**Modifiers Applied:**
- Passive tree bonuses
- Weapon proficiency (0-38% at max)
- Monster knowledge (up to +20%)
- Equipment set bonuses
- Relationship modifier
- Mood modifier (±20%)
- Damage variance (±10%)

### Critical Hits

```
Crit Chance = 5% + DEX/20 + LCK/10 + bonuses
Crit Multiplier = 1.5x (base) + bonuses
```

### Enemy Damage

```
Raw Damage = Enemy Damage × Ability Multiplier
Defense Reduction = Armor / (Armor + 100)
Final Damage = Raw Damage × (1 - Defense Reduction)
```

**Defense Modifiers:**
- Defending: 50% damage reduction
- Shield Wall: 50% damage reduction
- Minimum damage: 1

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
- **Duration:** 2 turns
- **Threat Bonus:** +200
- **Best Used:** When squishy allies are being targeted

### Shield Wall

- **Effect:** 50% damage reduction
- **Duration:** 2 turns
- **Threat Bonus:** +50
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
- Ally hasn't intervened yet this combat

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
- Taunt - Force enemies to attack
- Shield Wall - 50% damage reduction
- Power Attack - 150% damage

**Cleric:**
- Heal - Single target restoration
- Group Heal - AoE healing
- Smite - Holy damage

**Mage:**
- Fireball - Single target fire
- Ice Storm - AoE cold
- Arcane Missile - Quick attack

**Rogue:**
- Backstab - High single target
- Poison Strike - DoT
- Evasion - Defensive stance

**Ranger:**
- Aimed Shot - High accuracy
- Volley - AoE arrows
- Hunter's Mark - Enemy debuff

**Necromancer:**
- Life Drain - Damage + self heal
- Curse - Enemy debuff
- Shadow Bolt - Dark damage

### Skill Gems

Equip skill gems in your weapon sockets for additional abilities. See [Equipment Guide](equipment.md) for details.

### Skill Proficiency

Using skills improves proficiency:
- +10 XP per use
- Higher proficiency = more damage
- Reduced mana costs
- Lower cooldowns

---

## Status Effects

### Damage Over Time

| Effect | Duration | Damage |
|--------|----------|--------|
| Poison | 3 turns | 5% HP/turn |
| Burn | 3 turns | 5% HP/turn |
| Bleed | 4 turns | 5% HP/turn |

### Control Effects

| Effect | Duration | Impact |
|--------|----------|--------|
| Stun | 1 turn | Skip turn |
| Paralyze | 1 turn | Skip turn |
| Fear | 2 turns | Chance to skip |
| Slow | 2 turns | Lower initiative |
| Blind | 2 turns | Reduced accuracy |

### Debuffs

| Effect | Duration | Impact |
|--------|----------|--------|
| Weaken | 3 turns | Reduced damage |
| Curse | 3 turns | Various penalties |

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

Heroes fight better alongside friends:
- Friends: Small combat bonuses
- Best Friends: Larger bonuses + intervene
- Lovers: Significant bonuses, but HUGE penalties if partner dies

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
