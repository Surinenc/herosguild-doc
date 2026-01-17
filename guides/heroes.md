# Heroes & Classes

Heroes are the core of your guild. Each hero is unique with their own stats, skills, traits, and relationships.

## The Six Classes

Hero's Guild features six distinct hero classes, each with unique roles and playstyles.

### Warrior

**Role:** Tank, Frontline Damage

The Warrior is your shield against danger. With high health and strength, Warriors excel at absorbing damage and keeping enemies focused on them.

| Stat | Value |
|------|-------|
| STR | 14 |
| DEX | 8 |
| INT | 5 |
| VIT | 12 |
| LCK | 6 |

**Key Features:**
- **High Threat** - Generates 1.5x aggro, keeping enemies focused on them
- **Shield Wall** - Can reduce incoming damage by 50%
- **Taunt** - Forces enemies to attack the Warrior
- **Heavy Armor** - Wears plate for maximum protection

**Best For:** New players, protecting squishy allies, dungeons with heavy damage

**Ascendancy Paths:** (See [Ascendancy Guide](ascendancy.md))
- **Champion** - Ultimate tank with enhanced Taunt and Shield Wall
- **Berserker** - Raw damage, life steal, execute mechanics
- **Gladiator** - Dual-wielding, multi-strike, criticals

---

### Mage

**Role:** AoE Damage, Burst Damage

Mages command the elements to devastate groups of enemies. While fragile, their damage output is unmatched.

| Stat | Value |
|------|-------|
| STR | 5 |
| DEX | 7 |
| INT | 15 |
| VIT | 6 |
| LCK | 7 |

**Key Features:**
- **Elemental Spells** - Fire, Ice, and Lightning magic
- **AoE Damage** - Can hit multiple enemies at once
- **Mana-Based** - Uses mana pool for abilities
- **Glass Cannon** - High damage but low survivability

**Best For:** Clearing groups, boss burst phases, players who enjoy spellcasting

**Ascendancy Paths:** (See [Ascendancy Guide](ascendancy.md))
- **Elementalist** - Mastery of fire, cold, and lightning
- **Occultist** - Curses, chaos damage, dark magic

---

### Rogue

**Role:** Single-Target DPS, Utility

Rogues strike from the shadows with devastating critical hits. Their high dexterity makes them excellent at avoiding danger.

| Stat | Value |
|------|-------|
| STR | 8 |
| DEX | 15 |
| INT | 7 |
| VIT | 6 |
| LCK | 9 |

**Key Features:**
- **High Crit Chance** - Built for critical strikes
- **Backstab Bonus** - Extra damage from positioning
- **Evasion** - Can dodge incoming attacks
- **Stealth** - Access to stealth-based abilities

**Best For:** Taking down priority targets, finding treasure, critical-focused builds

**Ascendancy Paths:** (See [Ascendancy Guide](ascendancy.md))
- **Assassin** - First strike, execute, instant kills
- **Trickster** - Poison, debuffs, evasion

---

### Ranger

**Role:** Ranged DPS, Scouting

Rangers keep their distance while delivering consistent damage. Their keen senses help the party avoid traps and ambushes.

| Stat | Value |
|------|-------|
| STR | 9 |
| DEX | 14 |
| INT | 6 |
| VIT | 8 |
| LCK | 8 |

**Key Features:**
- **Ranged Attacks** - Fights safely from a distance
- **Trap Detection** - Bonus to finding hidden dangers
- **Consistent DPS** - Reliable damage output
- **Versatile** - Can adapt to various situations

**Best For:** Safe damage dealing, exploration, trap-heavy dungeons

**Ascendancy Paths:** (See [Ascendancy Guide](ascendancy.md))
- **Deadeye** - Precision, headshots, critical hits
- **Raider** - Speed, evasion, multi-hits
- **Pathfinder** - Potions, buffs, utility

---

### Cleric

**Role:** Healer, Support, Anti-Undead

Clerics are the backbone of any party, keeping allies alive through the toughest fights. They also excel against undead enemies.

| Stat | Value |
|------|-------|
| STR | 7 |
| DEX | 6 |
| INT | 12 |
| VIT | 10 |
| LCK | 8 |

**Key Features:**
- **Healing** - Restores ally HP (see formula below)
- **Low Threat** - Healing generates only 0.5x aggro
- **Anti-Undead** - Bonus damage against undead
- **Death Save Bonus** - Allies have +15% survival chance
- **Divine Favor** - +10% bonus to their own death saves

**Healing Formula:**
```
Heal Amount = Skill Base Heal + (INT × 0.5) + (Level × 6)
```
Modifiers: Mood bonus (±20%), Skill Proficiency, Set bonuses (Crusader 3pc: +25%)

**Best For:** Every party needs one! Essential for longer dungeons

**Ascendancy Paths:** (See [Ascendancy Guide](ascendancy.md))
- **Guardian** - Maximum healing, shields, protection
- **Paladin** - Battle cleric with holy damage

---

### Necromancer

**Role:** Minions, Dark Magic, Debuffs

Necromancers command the forces of death, raising minions to fight for them while weakening enemies.

| Stat | Value |
|------|-------|
| STR | 5 |
| DEX | 6 |
| INT | 14 |
| VIT | 7 |
| LCK | 8 |

**Key Features:**
- **Summon Undead** - Creates zombie and skeleton minions
- **Life Drain** - Heals by damaging enemies
- **Debuffs** - Weakens enemy capabilities
- **Dark Magic** - Unique spell school

**Best For:** Players who like pet classes, attrition strategies, unique playstyles

**Ascendancy Paths:** (See [Ascendancy Guide](ascendancy.md))
- **Puppeteer** - Minion armies, summon mastery
- **Lich** - Personal power, life drain, undeath

---

## Hero Stats

### Primary Stats

| Stat | Abbreviation | Description |
|------|--------------|-------------|
| **Strength** | STR | Physical damage, carry capacity |
| **Dexterity** | DEX | Speed, crit chance, dodge, initiative |
| **Intelligence** | INT | Magic damage, skill power, mana |
| **Vitality** | VIT | Defense, HP, injury resistance |
| **Luck** | LCK | Loot find, death saves, crit chance |

### Derived Stats

These are calculated from primary stats:

| Derived Stat | Formula |
|--------------|---------|
| Max HP | 50 + (VIT × 5) + (Level × 10) |
| Max Mana | 30 + (INT × 5) |
| Initiative | DEX + 1d10 (random roll at combat start) |
| Crit Chance | 5% + (DEX / 20) + (LCK / 10) + bonuses |

---

## Hero Quality

Heroes come in five quality tiers that affect their base stats and trait count:

| Quality | Stars | Stat Multiplier | Trait Count |
|---------|-------|-----------------|-------------|
| Common | ⭐ | 1.0x | 1 |
| Uncommon | ⭐⭐ | 1.08x | 1-2 |
| Rare | ⭐⭐⭐ | 1.18x | 2 |
| Epic | ⭐⭐⭐⭐ | 1.32x | 2-3 |
| Legendary | ⭐⭐⭐⭐⭐ | 1.50x | 3 |

**Recruit Rarity (varies by Tavern level):**

| Tavern | Common | Uncommon | Rare | Epic | Legendary |
|--------|--------|----------|------|------|-----------|
| Level 1 | 100% | - | - | - | - |
| Level 2 | 70% | 30% | - | - | - |
| Level 3 | 50% | 35% | 15% | - | - |
| Level 4 | 30% | 40% | 25% | 5% | - |
| Level 5 | 15% | 35% | 37% | 10% | 3% |

Higher quality heroes are significantly stronger due to the stat multiplier applying to ALL stats after all bonuses.

---

## Hero States

Heroes can be in various states that affect what they can do:

| State | Description | Can Go on Mission? | Can Craft? |
|-------|-------------|-------------------|------------|
| Ready | Available for assignment | ✓ | ✓ |
| Scheduled | Assigned to upcoming mission | ✗ | ✗ |
| On Mission | Currently in dungeon | ✗ | ✗ |
| Injured | Recovering from wounds | ✗ | ✗ |
| Resting | Recovering energy | ✗ | ✗ |
| Crafting | Assigned to crafting | ✗ | - |
| Training | At training yard | ✗ | ✗ |
| Dead | Permanently deceased | ✗ | ✗ |

---

## Body & Injury System

Heroes have a detailed body system with 25 body parts that can be damaged, destroyed, or replaced.

### Body Part Categories

| Region | Parts |
|--------|-------|
| **Head** | Brain, Left Eye, Right Eye, Left Ear, Right Ear, Jaw, Nose |
| **Torso** | Heart, Left Lung, Right Lung, Liver, Left Kidney, Right Kidney, Stomach, Spine |
| **Arms** | Left Shoulder, Right Shoulder, Left Arm, Right Arm, Left Hand, Right Hand |
| **Legs** | Left Leg, Right Leg, Left Foot, Right Foot |

### Injury Triggers

Injuries occur during combat:
- **Big Hit** (>50% max HP in one attack): 15% chance
- **Knocked Out** (HP = 0): 30% chance

### Injury Severity & Recovery

When an injury occurs, a roll determines severity:

| Roll | Severity | Recovery Time |
|------|----------|---------------|
| 1-30 | Crippling | 14 days |
| 31-50 | Severe | 7 days |
| 51-70 | Moderate | 5 days |
| 71-85 | Light | 3 days |
| 86-95 | Scratches | 1 day |
| 96-100 | None | 0 days |

**Roll Modifiers:**
- VIT stat: +1 per point
- Cleric in party: +10 per cleric
- Infirmary level: +5 per level
- Supervised mission: +20
- Hardy trait: +10
- HP below 25%: -20
- Cursed trait: -10

### Body Part States

| State | Efficiency | Description |
|-------|------------|-------------|
| Healthy | 100% | No damage |
| Damaged | 50-99% | Partial damage |
| Destroyed | 0% | Missing/non-functional |
| Prosthetic | 50-80% | Replaced with artificial part |
| Enchanted | 125% | Magically enhanced replacement |

### Fatal Injuries

Certain injuries cause instant death:
- Heart destroyed
- Liver destroyed
- Both Lungs destroyed
- Both Kidneys destroyed

### Prosthetics

Destroyed parts can be replaced with prosthetics:

| Tier | Efficiency | Infirmary Level | Crafting Skill |
|------|------------|-----------------|----------------|
| Basic | 50% | Level 3 | Leatherworking 5 |
| Standard | 80% | Level 4 | Blacksmithing 10 |
| Enchanted | 125% | Level 5 | Enchanting 15+ |

---

## Death Saves

When a hero is reduced to 0 HP, they must make a death save to survive. This determines whether they live with an injury or die permanently.

### Base Survival Chance

```
Survival Chance = 50% (base)
```

**Always clamped between 5% and 95%** — there's always a chance to live or die.

### Death Save Modifiers

| Modifier | Bonus |
|----------|-------|
| Cleric in party | +15% |
| Supervised mission | +10% |
| Is a Cleric (Divine Favor) | +10% |
| Survival gear equipped | +5% |
| Lucky trait | +5% |
| LCK stat | +1% per 5 LCK (max +5%) |
| VIT stat | +1% per 5 VIT (max +5%) |
| Cursed trait | -10% |

### Example Calculations

**Level 50 Warrior with 30 VIT, 15 LCK, Cleric in party:**
```
50% (base) + 15% (cleric) + 5% (VIT) + 3% (LCK) = 73% survival
```

**Same hero on a supervised mission:**
```
50% + 15% + 10% + 5% + 3% = 83% survival
```

**Level 30 Cleric with Lucky trait and party cleric:**
```
50% + 15% (party cleric) + 10% (Divine Favor) + 5% (Lucky) = 80% survival
```

---

## Leveling & Progression

### Experience

Heroes gain XP from:
- Completing dungeons
- Defeating enemies
- Mission completion bonuses
- Training Yard (passive, slower)

### Level Milestones

| Level | Unlock |
|-------|--------|
| 1 | Starting abilities |
| 5 | First passive tree point |
| 25 | Ascendancy Trial unlocked |
| 30 | Advanced skills |
| 50 | Second Ascendancy point, Elite content access |
| 75 | Third Ascendancy point |
| 80 | Heroic dungeon access |
| 95 | Abyssal Spire access |
| 100 | Fourth Ascendancy point, Paragon system unlocks |

### XP Curves

XP required increases differently at each stage:

| Level Range | Formula | Curve Type |
|-------------|---------|------------|
| 1-30 | `15 × level^1.8` | Flatter (faster early game) |
| 31-60 | Moderate scaling | Level^2.0 transition |
| 61-90 | `level^2.2` scaling | Steeper grind |
| 91-100 | Level 90 × multiplier | Brutal endgame |

**Level 91-100 Multipliers:**

| Level | Multiplier |
|-------|------------|
| 91 | 1.5× |
| 92 | 2.0× |
| 93 | 2.5× |
| 94 | 3.0× |
| 95 | 3.5× |
| 96 | 4.0× |
| 97 | 4.5× |
| 98 | 5.0× |
| 99 | 5.5× |
| 100 | 6.0× |

### XP Penalties (Levels 95-99)

High-level heroes gain reduced XP from content, slowing the final push:

| Level | XP Retained |
|-------|-------------|
| 95 | 90% |
| 96 | 85% |
| 97 | 80% |
| 98 | 75% |
| 99 | 70% |

**XP Bonuses:**
- Supervised mission: +25%
- Mentor in party: +50%
- Quick Learner trait: +25%
- Library (per level): +5%
- Guild XP Banner: +10%
- Paragon XP allocation: Up to +40%
- Rest bonus: Accumulated while resting

### Paragon System (Level 100+)

After reaching level 100, heroes gain Paragon points to further specialize.

**XP Required:** 400,000 XP per Paragon point (roughly equal to level 99→100)

| Category | Bonus Per Point | Cap | Max Bonus |
|----------|-----------------|-----|-----------|
| Strength | +2 STR | 50 | +100 STR |
| Crit Chance | +0.5% | 30 | +15% |
| Crit Damage | +2% | 30 | +60% |
| Vitality | +2 VIT | 50 | +100 VIT |
| Bonus HP | +10 HP | 50 | +500 HP |
| Armor | +5 Armor | 50 | +250 Armor |
| Dexterity | +2 DEX | 50 | +100 DEX |
| Speed | +1% | 30 | +30% |
| XP Gain | +2% | 20 | +40% |

**Total Paragon Points:** 360 points to fully max all categories

---

## Tips for Building Your Roster

1. **Class Diversity** - Have at least one of each class for flexibility
2. **Quality Matters** - A Legendary hero can outperform several Common heroes
3. **Backup Heroes** - Keep reserves for when main heroes are injured
4. **Relationship Synergy** - Heroes with bonds fight better together
5. **Match to Content** - Some dungeons favor certain classes

---

## Related Guides

- [Combat System](combat.md) - How heroes fight
- [Equipment & Items](equipment.md) - Gearing your heroes
- [Ascendancy](ascendancy.md) - Specialization paths
- [Relationships](relationships.md) - Social bonds

---

*"A guild is only as strong as its weakest hero."*
