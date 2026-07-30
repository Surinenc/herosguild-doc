# Heroes & Classes

Heroes are the core of your guild — a collection of unique individuals with their own stats, skills, traits, and opinions about absolutely everything. Managing them is rather like herding cats, if the cats could wield swords and occasionally set things on fire.

## The Six Classes

Hero's Guild features six distinct hero classes, each with unique roles and varying degrees of self-preservation instinct.

### Warrior

**Role:** Tank, Frontline Damage

The Warrior is your shield against danger, primarily because someone has to stand in front of the dragon and Warriors are the ones too stubborn to move. With high health and strength, they excel at absorbing damage and keeping enemies focused on them — a job description that, when you think about it, is deeply alarming.

| Stat | Value |
|------|-------|
| STR | 14 |
| DEX | 8 |
| INT | 5 |
| VIT | 12 |
| LCK | 6 |

**Key Features:**
- **High Threat** - Generates 1.5x aggro, keeping enemies focused on them
- **Shield Wall** - Reduces incoming damage by 50%, which is still quite a lot of incoming damage
- **Taunt** - Forces all enemies to redirect their attention to the Warrior, who volunteered for this
- **Heavy Armor** - Wears plate, which absorbs damage the way Warriors absorb criticism: completely

**Best For:** New players, protecting squishy allies, dungeons with heavy damage

**Ascendancy Paths:** (See [Ascendancy Guide](ascendancy.md))
- **Champion** - Ultimate tank with enhanced Taunt and Shield Wall
- **Berserker** - Raw damage, life steal, execute mechanics
- **Gladiator** - Dual-wielding, multi-strike, criticals

---

### Mage

**Role:** AoE Damage, Burst Damage

Mages command the elements to devastate groups of enemies. While possessing all the physical durability of a damp biscuit, their damage output is unmatched — a tradeoff they consider entirely reasonable.

| Stat | Value |
|------|-------|
| STR | 5 |
| DEX | 7 |
| INT | 15 |
| VIT | 6 |
| LCK | 7 |

**Key Features:**
- **Elemental Spells** - Fire, Ice, and Lightning magic; the Mage considers these three arguments for staying out of reach
- **AoE Damage** - Can hit multiple enemies simultaneously, which is the most efficient use of a single spell and the most dangerous thing to do with friendly fire disabled
- **Mana-Based** - Uses a mana pool for abilities; runs out at the worst possible moment
- **Energy Shield** - INT × 5 energy shield absorbs damage before HP; the Mage's substitute for having health
- **Glass Cannon** - High damage, low survivability; a tradeoff the Mage finds entirely acceptable from behind someone else

**Best For:** Clearing groups, boss burst phases, players who enjoy spellcasting

**Ascendancy Paths:** (See [Ascendancy Guide](ascendancy.md))
- **Elementalist** - Mastery of fire, cold, and lightning
- **Occultist** - Curses, chaos damage, dark magic

---

### Rogue

**Role:** Single-Target DPS, Utility

Rogues strike from the shadows with devastating critical hits. Their high dexterity makes them excellent at avoiding danger, which they consider a far more sensible approach to combat than the Warrior's "stand there and take it" methodology.

| Stat | Value |
|------|-------|
| STR | 8 |
| DEX | 15 |
| INT | 7 |
| VIT | 6 |
| LCK | 9 |

**Key Features:**
- **High Crit Chance** - Designed around making the first strike count, ideally before anyone knows there's a fight
- **Backstab Bonus** - Extra damage from positioning, which they treat as evidence that approach matters
- **Evasion** - Can dodge incoming attacks, which they consider far preferable to receiving them
- **Trap Detection & Lockpicking** - Rogues (or heroes with the KeenEyes / NimbleFingers traits) handle traps and locks the rest of the party would fail at — `Expedition.ts:221, 224`

**Best For:** Taking down priority targets, finding treasure, critical-focused builds

**Ascendancy Paths:** (See [Ascendancy Guide](ascendancy.md))
- **Assassin** - First strike, execute, instant kills
- **Trickster** - Poison, debuffs, evasion

---

### Ranger

**Role:** Ranged DPS, Scouting

Rangers keep their distance while delivering consistent damage. Their keen senses help the party avoid traps and ambushes — services that are deeply underappreciated right up until the moment someone steps on a spike trap.

| Stat | Value |
|------|-------|
| STR | 9 |
| DEX | 14 |
| INT | 6 |
| VIT | 8 |
| LCK | 8 |

**Key Features:**
- **Ranged Attacks** - Fights from a distance, where the enemies are not
- **Consistent DPS** - Reliable output from positions that arrows can reach and enemies cannot
- **Versatile** - Adapts to most situations, primarily by remaining in the back of them

**Best For:** Safe damage dealing, exploration, trap-heavy dungeons

**Ascendancy Paths:** (See [Ascendancy Guide](ascendancy.md))
- **Deadeye** - Precision, headshots, critical hits
- **Raider** - Loot specialist, increased material and item drops
- **Pathfinder** - Tactical support, initiative control, party buffs

---

### Cleric

**Role:** Healer, Support, Anti-Undead

Clerics are the backbone of any party, keeping allies alive through the toughest fights while maintaining the quiet, resigned expression of someone who knows they'll be blamed if anyone dies. They also excel against undead enemies, which is convenient given how often parties create them.

| Stat | Value |
|------|-------|
| STR | 7 |
| DEX | 6 |
| INT | 12 |
| VIT | 10 |
| LCK | 8 |

**Key Features:**
- **Healing** - Restores ally HP; the reason they get blamed when someone dies
- **Low Threat** - Healing generates only 0.5x aggro, which is small comfort when the Warrior is down
- **Anti-Undead** - Bonus damage against undead enemies, who tend to take it personally
- **Death Save Bonus** - Allies have +15% survival chance when a Cleric is present, which is why you always bring one
- **Divine Favor** - +10% bonus to their own death saves; the guild makes no comment on whether this is fair

**Healing Formula:** For those who find it reassuring to know exactly how much someone else's suffering is worth in numbers:
```
Base Heal = Skill Base Heal + INT + (Level + sqrt(Level)) + Max HP × 0.015
```
Then the realm applies, in order: mood modifier (±20%), skill proficiency, the **Cleric magical damage bonus** at half-rate (`× 1 + magicDamage% / 200`), heal-effectiveness from gem supports, ascendancy healing-% nodes, and set bonuses — Crusader 3-piece (×1.25) and Paladin 3-piece (×1.30). A fully-supported endgame Cleric heals for several times what the base formula suggests, which is the difference between the party surviving and the Guild Clerk filing more paperwork than usual.

**Best For:** Every party needs one! Essential for longer dungeons. Arguably the most important class, a fact they will remind you of at every opportunity.

**Ascendancy Paths:** (See [Ascendancy Guide](ascendancy.md))
- **Guardian** - Maximum healing, shields, protection
- **Paladin** - Battle cleric with holy damage

---

### Necromancer

**Role:** Minions, Dark Magic, Debuffs

Necromancers command the forces of death, raising minions to fight for them while weakening enemies. Other heroes find them unsettling, which Necromancers consider a professional compliment.

| Stat | Value |
|------|-------|
| STR | 5 |
| DEX | 6 |
| INT | 14 |
| VIT | 7 |
| LCK | 8 |

**Key Features:**
- **Summon Undead** - Raises the fallen to fight again, which solves the enemy problem and the body problem simultaneously
- **Life Drain** - Heals by dealing damage; the Necromancer considers this efficient
- **Debuffs** - Arrives to encounters having already done some of the work
- **Energy Shield** - INT × 5 energy shield absorbs damage before HP; the Necromancer's substitute for having a body that cares about being hit
- **Dark Magic** - A spell school other heroes avoid discussing over dinner

**Best For:** Players who like pet classes, attrition strategies, unique playstyles

**Ascendancy Paths:** (See [Ascendancy Guide](ascendancy.md))
- **Puppeteer** - Minion armies, summon mastery
- **Lich** - Personal power, life drain, undeath

---

## Hero Stats

### Primary Stats

Five stats govern everything a hero can do. Heroes have opinions about which one matters most. Those opinions correlate suspiciously with their class.

| Stat | Abbr | What It Affects | Notable Opinions |
|------|------|-----------------|-----------------|
| **Strength** | STR | Physical damage, carry capacity | Warriors consider this the only stat. They are wrong, but not entirely. |
| **Dexterity** | DEX | Speed, crit chance, dodge, initiative | Rogues treat their DEX score as a personal achievement. |
| **Intelligence** | INT | Magic damage, skill power, mana | Mages regard low INT in others as a character failing. |
| **Vitality** | VIT | Defense, HP, injury resistance | The stat nobody invests in until they need it urgently. |
| **Luck** | LCK | Loot find, death saves, crit chance | The Guild Clerk takes no official position on whether this works. |

### Derived Stats

These are calculated from primary stats, because apparently nothing in this guild can be simple:

| Derived Stat | Formula |
|--------------|---------|
| Max HP | 50 + (VIT × 10) + (Level × 10) |
| Max Mana | 30 + (INT × 5) |
| Initiative | DEX + 1d10 (random roll at combat start) |
| Crit Chance | 5% + (DEX / 20) + (LCK / 20) + bonuses (UI / stat display path, `Hero.ts:2778`) |
| Crit Chance (combat) | 5% + (DEX / 20) + (LCK / 10) + bonuses (in-fight roll, `Balance.ts:625`) |

---

## Hero Quality

Heroes come in five quality tiers that affect their base stats and trait count. The difference between a Common hero and a Legendary one is roughly the difference between a butter knife and a siege weapon:

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

### Background & Life History

Class and quality only get you so far. Every hero also arrives carrying a **background tag** — one of eight: Noble, Criminal, Soldier, Peasant, Scholar, Merchant, Cultist, Outlander — and a **four-paragraph life history** rolled from a catalog of a hundred and twenty events. Both feed multiplicative modifiers into the damage chain and the effective-stats pass, and that is why two heroes with identical kit and identical class will not, in practice, hit for the same numbers. The Guild Clerk considers this a feature, on the grounds that previously the heroes were starting to look interchangeable.

The CV shows up on the Details modal at the Tavern (before you hire) and on the Background tab in Hero Details (after you do). See [Hero Backgrounds](backgrounds.md) for the full system.

---

## Hero States

Heroes can be in various states that affect what they can do. Think of it as a very complicated scheduling problem:

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

Heroes have a detailed body system with 25 body parts that can be damaged, destroyed, or — in a triumph of guild engineering — replaced with something mechanical. The human body, it turns out, is surprisingly modular.

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

When an injury occurs, a roll determines severity. Higher rolls are better, and a Cleric's presence has never been more appreciated:

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
| Prosthetic (Basic) | 50% | Wooden/glass replacements |
| Prosthetic (Standard) | 80% | Metal mechanical replacements |
| Prosthetic (Enchanted) | 125% | Magically enhanced, better than original |

### Fatal Injuries

Certain injuries cause instant death — which is why the vital-organ prosthetic window exists. Install the replacement *before* the organ is Destroyed, because afterwards there is nobody to install it on:
- Brain destroyed
- Heart destroyed
- Liver destroyed
- Both Lungs destroyed
- Both Kidneys destroyed

### Prosthetics

Destroyed parts can be replaced with prosthetics. The original limb-and-sense set (arms, legs, hands, feet, eyes, ears) is joined by full-body prosthetics covering 10 additional body part families — Brain, Jaw, Nose, Heart, Lung, Liver, Kidney, Stomach, Spine, and Shoulder — for a total of 47 prosthetic types. The Guild Clerk considers this a testament to both engineering ambition and the frequency of workplace injuries.

**Installing one:** Open a hero's Body Status modal (the ✚ panel on the right of the character screen). Every non-healthy part with an in-stock, tier-compatible prosthetic gets an install button showing the prosthetic name, efficiency, and current stock — click to fit it. The button only appears when the current Infirmary tier supports that prosthetic. Fees are paid at craft time via material costs (see [Crafting Guide](crafting.md)); the surgical procedure itself is currently free — the Guild Clerk assumes the anaesthetic budget will resolve itself.

| Tier | Efficiency | Infirmary Level | Crafting Skill |
|------|------------|-----------------|----------------|
| Basic | 50% | Level 3 | Softcraft 5 |
| Standard | 80% | Level 4 | Metalsmithing 10 |
| Enchanted | 125% | Level 5 | Arcana 15+ |

**Vital-organ rescue window:** Vital body parts (Brain, Heart, Lungs, Liver, Kidneys, Stomach, Spine) follow a different install rule — they can *only* receive a prosthetic while **Damaged**, not after destruction. Once a vital organ is Destroyed, the hero is already dead (or, for paired organs like lungs and kidneys, dies only when both are gone). The window between "damaged" and "destroyed" is when the prosthetic must go in — the guild surgeon's version of a last-chance clearance sale. Non-vital parts (limbs, eyes, ears, jaw, nose, shoulders) work as before: Destroyed-only installation.

**Install fees:** The gold-cost surgical fee described in previous versions is not currently charged — the only cost is the material investment at craft time. If per-part surgical fees are added later, this section will list them.

---

## Illness & Chronic Traits

Heroes catch things. It is an entirely separate problem to injury, wounds, or the aftermath of a Grand Feast — one that spreads, worsens over days, and occasionally kills. The Guild Clerk has, per Guild custom, expanded the medical filing cabinet.

### How Illness Works

Every day, each active illness gains **severity** and each afflicted hero builds **immunity**. Whichever wins first decides the outcome:

- Immunity fills first → **recovered**. If the peak severity during the illness crossed that illness's chronic-recovery threshold, a **chronic trait** is granted — a permanent scar the Clerk will now file under the hero's name for the rest of their career.
- Severity reaches the illness's **lethal threshold** first → **dead**. Most illnesses cap out non-lethal, but a handful — Wound Rot, The Long Cough, The Grey Weep, The Blackblood, Backfire Fever, The Marsh Sweats — will finish the job.

Illnesses spread, and they spread along the lines of affection. Contagion ticks daily against every uninfected hero in reach — the whole roster if you're at the guild, your party-mates if you're out on a mission — and the multipliers stack: **married ×3.5**, **lovers, partners and the merely dating ×3.0**, **best friends ×2.0**, **sharing a room ×2.0 on top of whichever of those applies** (see [Cohabitation](guild.md#cohabitation)), **same mission party ×1.5**, and a Plague crisis **×3** across everything transmissible. **Enemy** and **Nemesis** bonds *dampen* transmission to **×0.7** — heroes who loathe each other keep their distance, which turns out to be medically fortunate.

The whole product is then capped at **0.85**, because a married couple in a shared bed during a plague was otherwise reaching certainty, and certainty makes for poor drama. Even at the ceiling there is roughly a one-in-seven chance of not catching it, which the Guild Clerk files, per Guild custom, under *hope*.

### Symptom Penalties

Active illnesses apply **percentage-based** stat penalties. Across all active illnesses on a hero, negative percents on any single stat are floored at **−60%**. Chronic traits stack a separate **−30% per stat** floor. The two apply multiplicatively, so a hero riding every cap sits at their base stat × 0.28 — barely functional, but still able to hold a sword the wrong way round.

Positive percentages are uncapped. This matters chiefly because **The Glimmers** grants +8% INT (the affected hero temporarily perceives the eighth colour, which is helpful for mages and unnerving for everybody else) at the cost of −10% DEX.

Mood modifiers stay absolute — mood is a 0-to-100 scale, so a −15 mood hit means −15, no scaling required. Every illness carries one, ranging from a −3 sulk to a −15 collapse, re-applied each morning with a single day's life so it lapses of its own accord the moment the hero recovers and nobody has to remember to file the paperwork. The Glimmers is the only affliction in the cabinet that *improves* a hero's mood, by +2, on the grounds that the eighth colour is at least interesting.

### Illness Categories

Illnesses come in six broad flavours, each with its own risk profile and its own reasons for happening.

| Category | Character | Examples |
|----------|-----------|----------|
| Mundane / Ambient | Low-lethality, common | The Sniffles, The Grippe, Wet Boots Fever, Slap-Belly, Rat-Cough |
| Urban / Guttergate-adjacent | Air-quality respiratory | Chimney Ash Lung |
| Occupational / Class-linked | Fire **only** on the matching class | Warrior's Elbow, Mage's Fugue, Whisper Throat (Cleric), Necromancer's Shadow Cough, Ranger's Sun-Fever |
| Magical residue | Tower & high-magic zones | Ambient Aetheric Rash, Thaumic Flu, The Glimmers, Backfire Fever |
| Beast / creature-linked | Injury-seeded from beast wounds | Werewolf Fever, Vampire Anaemia |
| Metaphysical | Slow, mood-crushing, non-lethal | The Sighs, The Doldrums, The Small Hours |

Where a hero contracts an illness depends heavily on **environment** — Swamps push respiratory fevers (Marsh Sweats ×4), Crypts stir The Long Cough and Necromancer's Shadow Cough, Ruins amplify The Small Hours, Towers grow the magical bestiary — and on **age**. Age-linked illnesses (Grippe, Marsh Sweats, Long Cough, River Sickness, Rat-Cough, Watchman's Foot, Chimney Ash Lung) compound at roughly **×1.3 / ×1.8 / ×2.5** for heroes past **40 / 55 / 70**. Crises pile on further multipliers where the pairing makes sense: **The Blood Moon** triples Werewolf Fever, **The Syzygy** triples Thaumic Flu, **The Cult of the Unseen** doubles The Small Hours and The Sighs, **The Great Famine** doubles The Doldrums.

Class also matters. Warriors are more prone to Wound Rot; Necromancers court The Long Cough and The Grey Weep; Rangers shrug off Marsh Sweats and Wet Boots Fever thanks to herbal knowledge and, apparently, waterproof boots. The occupational category is stricter than a nudge — those illnesses **only** fire on the matching class in the first place.

A few specimens worth naming individually, because you will meet them and remember them:

- **The Glimmers** — the eyes, having seen the eighth colour, decline to stop. Mechanically, +8% INT and −10% DEX, so a mage who catches it becomes briefly cleverer at the cost of walking into furniture. The only illness in the catalog with a *positive* stat mod, and the only one anybody has ever been vaguely pleased to develop.
- **Thaumic Flu** — magical inflammation. Every day, deterministic ±8% swings on STR / DEX / INT, seeded per hero per day, so you can't plan around it and it isn't the same swing tomorrow. The Syzygy triples the odds of catching it in the first place.
- **The Sighs** — pure existential malaise. No stat penalty, no death, just a −12 mood tick that goes on for as long as it goes on. Cult Uprisings double it, which nobody finds coincidental.
- **The Watchman's Foot** — flat-foot ache from too many years walking a beat. Non-contagious, non-lethal, mostly a −5% DEX with an age curve. Rangers get a pass; Warriors, per medical record, get a limp.
- **Backfire Fever** — Mage-only. A spell went wrong; the mage is now the spell. Lethal if untreated, chronic-recovery leaves **Wandering Mind**, and The Syzygy doubles the odds.

### Treatment

Whenever any hero is sick, the next morning opens on the **Infirmary scouting scene** — rendered before the Tavern and above the ceremonial moment queues, on the reasonable principle that dying tomorrow is more urgent than most other things. Each sick hero gets a card: illness name, severity bar, immunity bar, Pratchett-flavoured symptom notes, and a **Treat** toggle. Treatment slots are limited by Infirmary tier:

| Infirmary Level | Treatment Capacity |
|-----------------|--------------------|
| 1 | 2 heroes |
| 2 | 3 heroes |
| 3 | 5 heroes |
| 4 | 8 heroes |
| 5 | 12 heroes |

Treating a hero cuts that illness's daily severity growth by roughly **60%**. Higher Infirmary tiers shave an additional **5% per level** off severity growth even without a direct treatment slot, on the theory that a well-appointed ward is medically useful just by existing.

A **Cleric present at the guild** — not dead, not on mission, no assignment necessary — adds an immunity bonus of **+25%** to each treated hero. Heroes with high VIT (above the class baseline of 10) also add a **constitution bonus** of up to +50% immunity gain of their own; VIT is genuinely load-bearing here in a way it isn't in ordinary combat.

**Confirm** applies your chosen treatments. **Skip Infirmary Tonight** dismisses the scene and resolves the untreated heroes autonomously, worst-case, which is a polite way of saying the highest-severity ones may not survive the week. Sick heroes are flagged on their **HeroRow** with an illness badge coloured by severity — green under 30, amber 30 to 70, red past 70 — so you can tell at a glance who's on borrowed time.

### Chronic Traits

If a hero's peak severity crossed the illness's chronic-recovery threshold before immunity finished the race, they recover with a **chronic trait** — a permanent scar with modest but permanent stat and mood costs. A survivor of The Long Cough carries **The Wheeze** for life; a Grey Weep survivor picks up **Hollow Blood**; Vampire Anaemia leaves **Slow Blood**; Chimney Ash Lung leaves **Ash Lung**. The Guild Clerk enters these into the record with the polite understatement of someone who has, per custom, seen a great deal — "the lungs, per medical record, remember the fight. They will not, per record, forget it."

The full list of a hero's chronic traits appears on the **History tab** of the Hero Details modal, each one a short bureaucratic obituary of a fight the hero came back from.

---

## Death Saves

When a hero is reduced to 0 HP, they must make a death save to determine whether they survive with an injury or join the memorial wall permanently. It is, without exaggeration, the most stressful dice roll in the guild.

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

## Purse & Ambition

Heroes are paid. This was, for a long time, a polite fiction — the guild was debited every morning and the money simply ceased to exist, which the Guild Clerk describes as "the tidiest payroll in the realm" and everybody else describes as theft. It now goes into the hero's **purse**, and what they do with it is entirely their own business.

### The Purse

Every living hero is credited their daily wage each morning — the base figure, not the crisis-inflated one, so a crisis costs *you* rather than enriching the staff. A new recruit arrives holding **three days' wage**, or **25 gold**, whichever is larger, so nobody starts destitute on their first afternoon off.

What a hero can afford is expressed in absolute gold rather than as a share of their income, which is the whole point: a recruit on 24 gold a day genuinely cannot reach what a veteran takes for granted.

| Band | Cost |
|------|------|
| Modest | 5–40g |
| Comfortable | 50–300g |
| Fine | 400–1,500g |
| Extravagant | 2,000–10,000g |

Heroes never spend down to nothing — they keep roughly a day's wage in reserve, on the grounds that a hero who blew every coin on one evening and could then do nothing at all until payday reads as a bug rather than a personality.

Purse and daily wage are both shown on the **Career tab** of the Hero Details modal.

### Days Off Cost Money

The reasons a hero is unavailable — the Personal Day, the Hangover, the family business that may or may not exist — are now **priced**, and the hero pays. See [Unavailability](relationships.md#unavailability) for the reasons themselves and what the ledger records.

The short version: the gold comes out of their purse, which is gold not going into the fund below. A hero who keeps going to the coast never finishes saving for anything. That tension is deliberate.

### The Dream

Every hero is privately saving toward one specific thing. **35%** of each day's surplus goes into the fund, capped at 35% of their daily wage so the sum stays linear rather than compounding, and paying nothing at all on a day they've spent down to the reserve.

The price belongs to the **dream**, not the dreamer. A headstone is cheap and a ship is not, regardless of who wants one:

| Scale | Cost | What it buys |
|-------|------|--------------|
| Trifle | 3,000–12,000g | A coat. A headstone. A debt settled with a neighbour |
| Modest | 30,000–90,000g | A stall, a room, a small and unreliable boat |
| Substantial | 200,000–600,000g | The bakery. The farm. The shop with their name over it |
| Grand | 1,500,000–5,000,000g | Only the very well paid, and only if they live frugally |
| Fable | 20,000,000–60,000,000g | Nobody finishes these. They were never really about the money |

Which scale a hero reaches for is weighted by what they earn, but with a genuine tail upward — a fair number of heroes want something they will never afford, and will carry the ambition their entire career and die still short of it. The Guild Clerk considers this the most realistic feature in the game.

The **Career tab** shows the dream as a progress bar with the hero's own words underneath, the amount saved against the target, and a "saved enough" marker when the fund fills.

### What Happens When the Fund Fills

Authored per dream, not derived from its price — nobody hands in their notice over a pair of boots:

- **They keep it.** They buy the thing, carry on working, and are permanently a little better for having it — a small flat mood bonus, sometimes a percentage stat modifier, always a line on the Career tab under *Things they saved for*. Then they start saving for something else, drawn from what they haven't already bought. Most dreams work this way
- **They leave.** Some dreams *were* the change of life. The hero retires from the guild, alive, on their own terms, owing nothing

A little over one dream in five is the second kind. You will not know which until the bar fills.

### Retirement

A retiring hero walks out through the front gate in daylight and is filed in the **Departed archive** under `Retired`, which is the only cheerful entry that archive has ever held.

It is still a loss. The guild runs exactly the same grief through their friendships that a death does — their friends do not care that it was a happy ending, and neither, in the small hours, do you. You are obliged to be pleased about it. The Quartermaster has noted that the roster is one shorter and one happier, and has been asked to stop saying this.

There is an inversion worth planning around: paying your best hero well buys them out sooner. The guild's interests and the hero's are not, it turns out, entirely aligned.

---

## Memorial and Departed

A hero can leave the guild in two distinctly different ways, and the realm keeps separate records for each.

### The Chapel Memorial — for heroes who died

Heroes killed in combat get a memorial in the Chapel. When a hero dies, the realm:

- Generates an **obituary** — a short, Chronicle-flavoured three-paragraph piece drawn from the hero's background, career, relationships, and the manner of their death. The Guild Clerk has standing instructions not to read these aloud at staff meetings, having tried it once
- Preserves any **earned titles** the hero held; the memorial card shows the first two as title chips with a `+N` overflow indicator
- Marks the hero as `Dead` and removes them from the active roster permanently — their equipment goes with them. Gear cannot be pulled from a corpse during the burial grace period; the loadout is buried alongside the hero. The Vault will not let you select a dead hero's items, however briefly they're still in the system

Memorial cards are visible from the Chapel screen. The cards persist indefinitely; the realm does not forget. The Guild Clerk, asked whether the memorial should ever be cleared, has replied only "no" on each of the seven occasions the question has come up.

### The Departed Archive — for heroes who left alive

Not every hero who leaves the guild dies. Some are banished after disgracing themselves. Some desert after a particularly bad mission. Some are sent off on a permanent quest. Some are released because the guild has overrun its barracks capacity and the realm has decided which name to draw out of the metaphorical hat. And some — see [Retirement](#retirement) — simply saved up enough to stop.

These heroes go to the **Departed archive**, a separate record from the Chapel memorial. They are not dead — they are simply no longer with the guild — and they retain their titles and chronicle entries in the archive. The realm keeps the record so that, should any of them ever return, the guild has a paper trail to consult. The archive lives behind the **Departed** tab on the Chapel screen, alongside the Memorial Hall, each card labelled with the manner of going: Retired, Deserted, Guild event, Lost to a dungeon, Called away, or the admirably noncommittal Left the guild.

The distinction matters: a hero killed in combat is mourned in the Chapel. A hero who walks out alive is filed in the archive. The Guild Clerk insists that mixing these two categories would be "professionally embarrassing."

---

## Leveling & Progression

### Stat Points

Heroes gain **3 attribute points per level** to distribute among primary stats. Total points = (Level - 1) × 3.

### Veteran Status

Heroes earn veteran ranks based on completed missions. The progression from Rookie to Legend is primarily a measure of how many times someone has voluntarily walked into a dungeon:

| Rank | Missions | Morale Bonus | Rep Multiplier | Damage Multiplier | Survival Bonus |
|------|----------|-------------|----------------|-------------------|----------------|
| Rookie | 0-9 | +0 | 1.0× | 1.0× | 0% |
| Seasoned | 10-24 | +5 | 1.05× | 1.0× | +2% |
| Veteran | 25-49 | +10 | 1.1× | 1.02× | +5% |
| Elite | 50-99 | +15 | 1.2× | 1.04× | +8% |
| Champion | 100-199 | +25 | 1.3× | 1.06× | +12% |
| Legend | 200+ | +40 | 1.5× | 1.08× | +15% |

### Chronicle Titles

Heroes earn titles by achieving specific milestones tracked in their Chronicle. Unlike veteran ranks, titles are permanent achievements with concrete gameplay bonuses — the game's way of rewarding heroes who have survived long enough to have a story worth telling.

| Title | Trigger | Bonus |
|-------|---------|-------|
| **Dragonslayer** | Kill a dragon-type boss | +10% damage vs Dragons |
| **Heartbroken** | Lose a partner to death | +8% all damage |
| **Veteran** | Complete 100 missions | +5% XP to lower-level allies |
| **Ironhide** | Survive 5 near-death experiences | +10% max HP |
| **Oathbound** | Form an OathSworn bond | +8% damage with oath partner |
| **Master Artisan** | Craft 3 Masterwork items | +10 crafting quality |
| **Shield Brother** | Save 10 allies via Intervene | +15% Intervene chance |
| **Nemesis Hunter** | End a Blood Feud | +10% damage vs Humanoids |
| **Survivor** | Recover from a mental break | -20% negative mood impact |
| **Legend** | Accumulate 50+ chronicle entries | +8% to all stats |
| **Trial-Master** | Complete all 4 ascendancy trials | +5% to all stats |
| **Old Guard** | Serve 500 days in the Guild | +5% XP aura to nearby allies |
| **Whisperer** | Maintain bonds with 5 different heroes | +5% damage when partied with a bonded ally |
| **Phoenix** | Recover from 3 mental breaks | -25% negative mood impact |

Titles stack — a hero can hold multiple titles simultaneously. The Legend title (+8% all stats) is particularly valuable as a long-term goal, and Heartbroken (+8% all damage) is the sort of bonus that makes you feel guilty for appreciating it. Trial-Master is the only title that requires the [Ascendancy](ascendancy.md) trial path; Old Guard rewards heroes who simply refuse to retire.

When a hero dies, their earned titles are preserved on their **Chapel memorial card** — the Guild Clerk considers this the minimum decency the realm can offer.

### Experience

Heroes gain XP from the following, in descending order of excitement:
- Completing dungeons — the main source, and the main reason dungeons exist
- Defeating enemies — each one contributes a small amount to the total
- Mission completion bonuses — for finishing, not just surviving
- Training Yard (passive, slower) — for heroes who prefer to learn without anyone actively trying to kill them

### Level Milestones

Most levels are just numbers. These ones come with something attached:

| Level | Unlock |
|-------|--------|
| 1 | Starting abilities, first passive tree point on the class start node (see [Passive Tree](passive-tree.md)) |
| 25 | Ascendancy Trial unlocked |
| 30 | Advanced skills |
| 50 | Second Ascendancy point, Elite content access |
| 75 | Third Ascendancy point |
| 80 | Heroic dungeon access |
| 95 | Abyssal Spire access |
| 100 | Fourth Ascendancy point, Paragon system unlocks |

### XP Curve

XP required uses a single power-law formula: `ceil(2.5 × level^2.5)`. Reaching level 100 is meant to feel like an achievement, not a commute, and `level^2.5` makes sure of it — early levels go quickly, the mid-game stretches, and the last ten levels are the kind of climb that makes you read the patch notes.

### XP Penalties (Levels 95-99)

High-level heroes gain reduced XP from content, slowing the final push. The universe's way of saying "are you sure about this?"

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
- Paragon XP allocation: Up to +100% (50 points × +2%)
- Rest bonus: Accumulated while resting

### Paragon System (Level 100+)

After reaching level 100, heroes stop levelling and start earning Paragon points instead. This is the endgame progression system — slower, deliberate, and the difference between a hero who can survive the Abyssal Spire and one who decorates its floors.

Each Paragon point costs **192,109 XP**. Points are allocated into 8 categories, each capped at 50 investments:

| Category | Bonus Per Point | Cap | Max Bonus |
|----------|-----------------|-----|-----------|
| Strength | +2 STR | 50 | +100 STR |
| Dexterity | +2 DEX | 50 | +100 DEX |
| Intellect | +2 INT | 50 | +100 INT |
| Vitality | +4 VIT | 50 | +200 VIT |
| Crit Chance | +0.5% | 50 | +25% |
| Crit Damage | +1% | 50 | +50% |
| Armor | +5 Armor | 50 | +250 Armor |
| XP Gain | +2% | 50 | +100% |

**Total Paragon Points:** 400 points to fully max all 8 categories.

**Strategy Notes:**
- **XP Gain first** — investing early in XP Gain (up to +100%) dramatically accelerates all future Paragon point acquisition. The maths is compelling.
- **Primary stat second** — dump into your class's primary stat (STR for Warriors, DEX for Rogues/Rangers, INT for Mages/Clerics/Necromancers) for immediate combat impact.
- **Vitality for Spire pushers** — +200 VIT at max is the difference between surviving floor 100+ and not. The Spire scales enemies to level 175 at floor 100; your heroes need the health pool.
- **Crit for damage dealers** — +25% crit chance and +50% crit damage together create multiplicative scaling that outperforms flat stat investment at high gear levels.
- **Armor is situational** — +250 armor matters most for frontline heroes absorbing hits; backline heroes benefit more from offensive stats.

---

## Tips for Building Your Roster

1. **Class Diversity** - Have at least one of each class for flexibility. You never know when you'll need a Necromancer until you really, really need a Necromancer.
2. **Quality Matters** - A Legendary hero can outperform several Common heroes. It's not fair, but then neither is combat.
3. **Backup Heroes** - Keep reserves for when main heroes are injured. They will be injured.
4. **Relationship Synergy** - Heroes with bonds fight better together
5. **Match to Content** - Some dungeons favor certain classes

---

## Related Guides

- [Combat System](combat.md) - How heroes fight
- [Equipment & Items](equipment.md) - Gearing your heroes
- [Ascendancy](ascendancy.md) - Specialization paths
- [Relationships](relationships.md) - Social bonds
- [Crises](crisis.md) - Three named crises can kill a hero outright via Critical-severity moral events

---

*"A guild is only as strong as its weakest hero — which is why the Guild Clerk keeps a very detailed spreadsheet."*
