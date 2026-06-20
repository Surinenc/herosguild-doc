# Passive Tree

The Passive Tree is the single largest system in Hero's Guild and, by a comfortable margin, the one most likely to make new players stare at the screen in quiet despair. It contains 354 nodes arranged in a hexagonal web connecting all six classes. Think of it as a map of everything your hero *could* become, drawn by someone with strong opinions about symmetry.

Each hero begins at their class starting node and works outward, spending one passive point per level. By level 100, a hero will have allocated roughly a quarter of the tree — enough to feel powerful, not enough to feel safe.

---

## Node Types

The tree contains five types of nodes, listed here in ascending order of how excited you should be to find one:

| Node Type | Max Level | Size | Description |
|-----------|-----------|------|-------------|
| **Start** | 1 | Largest | Your class entry point. Grants base stats and a damage type bonus. Cannot be removed. |
| **Travel** | 1 | Smallest | Connector nodes. Grant +5 to a stat of your choice (Strength, Dexterity, or Intelligence). |
| **Minor** | 5 | Small | Modest stat bonuses. Can be levelled up to 5 times for compounding returns. |
| **Notable** | 3 | Medium | Significant passives. Named abilities with meaningful impact on your build. |
| **Keystone** | 1 | Large | Powerful transformative effects with mandatory drawbacks. The tree's most interesting decisions. |

---

## Passive Points

Heroes earn **1 passive point per level**, starting at level 1. The first point is spent automatically on the class starting node, which is the tree's way of ensuring everyone begins with at least one correct decision.

| Level | Total Points | Freely Allocatable |
|-------|-------------|-------------------|
| 1 | 1 | 0 (start node) |
| 10 | 10 | 9 |
| 50 | 50 | 49 |
| 100 | 100 | 99 |

---

## Class Regions

The tree is divided into six class regions arranged in a hexagonal layout. Each region contains a starting node and three specialized branches.

### Starting Node Bonuses

Every hero begins on their class node. It cannot be removed, which saves considerable trouble later.

| Class | Starting Stats |
|-------|---------------|
| **Warrior** | +50 STR, +100 Damage, +20% Physical Damage |
| **Mage** | +50 INT, +50 Damage, +20% Spell Damage |
| **Rogue** | +50 DEX, +80 Damage, +20% Physical Damage |
| **Ranger** | +50 DEX, +50 Damage, +20% Projectile Damage |
| **Cleric** | +40 INT, +40 STR, +50 Damage, +20% Spell Damage |
| **Necromancer** | +50 INT, +50 Damage, +20% Chaos Damage |

Warrior and Rogue starting nodes carry extra flat damage — Warrior gets the largest bump because plate-and-stubbornness was the slowest archetype to come online in the early game; Rogue gets a smaller bump because daggers are already pointy.

### Branch Specializations

Each class has three branches, offering distinct playstyles. You won't have the points to fully invest in all three — the tree demands commitment, or at least a convincing impression of it.

**Warrior** — Three opinions on what a Warrior should be doing. They all involve hitting things; they disagree on whether to survive it.
| Branch | Theme | Focus |
|--------|-------|-------|
| Tank | Defensive mastery | Armor, max life, damage reduction |
| Berserker | Aggressive sustain | Physical damage, life leech, crit |
| Warlord | Combat leadership | Melee damage, attack power, strength |

**Mage** — Three schools of destruction, each convinced theirs is the correct element.
| Branch | Theme | Focus |
|--------|-------|-------|
| Fire | Destructive magic | Spell damage, intelligence |
| Frost | Controlled power | Spell damage, survivability trade-offs |
| Arcane | Mana mastery | Spell scaling, mana mechanics |

**Rogue** — Three definitions of 'efficient'. They differ mainly on whether the target sees it coming.
| Branch | Theme | Focus |
|--------|-------|-------|
| Assassin | Precision killing | Critical strike chance and damage |
| Shadow | Dark arts | Chaos damage, life leech |
| Trickster | Agile combat | Damage, dexterity |

**Ranger** — Three applications of the central Ranger philosophy: damage from somewhere safe.
| Branch | Theme | Focus |
|--------|-------|-------|
| Sharpshooter | Ranged dominance | Projectile damage, crit (max-life/armor tradeoff) |
| Beast Master | Companion synergy | Minion damage and life |
| Trapper | Tactical control | Damage, dexterity, spell damage |

**Cleric** — Three interpretations of divine power: protective, supportive, and the one that hits unexpectedly hard.
| Branch | Theme | Focus |
|--------|-------|-------|
| Paladin | Holy warrior | Spell damage, armor (no `holy_damage` stat exists in the passive tree — Cleric branches all scale with `spell_damage`) |
| Prophet | Divine channeller | Mana regen, maximum mana |
| Inquisitor | Righteous fury | Spell damage, critical strikes |

**Necromancer** — Three professional arrangements with death, ranked by how personally the hero gets involved.
| Branch | Theme | Focus |
|--------|-------|-------|
| Lich | Death magic | Chaos & spell damage (reduced max life) |
| Summoner | Minion master | Minion damage & life (keystones penalize damage and armor) |
| Death Knight | Dark warrior | Chaos damage, life leech, armor |

---

## Keystone Nodes

Keystones are the tree's most dramatic nodes. Every keystone grants a powerful bonus alongside at least one significant penalty. Allocating one is less of a decision and more of a personality test.

### Bypass Paths

Mid-path keystones have **bypass paths** — adjacent non-keystone nodes connect to create parallel routes around them. A keystone's tradeoff is genuinely optional: you can skip it for 0–1 extra points. The tree does not force you to accept a drawback just to reach the nodes behind it. (The exact number of bypass-equipped keystones isn't a code constant; the `_d` suffix appears on 54 detour-helper nodes spread across the 18 branches.)

### Penalty Patterns

Keystone penalties tend to track each class's defensive profile, with **notable exceptions** — the pattern is a tendency, not a guarantee:

- **Warrior / Cleric** keystones usually penalize damage or crit (armor is their primary defense). Exception: Berserker Mastery penalizes max life
- **Mage / Necromancer** keystones usually penalize armor or max life (they rely on flat HP and energy shield rather than plate). Exception: Frost Mastery penalizes crit chance
- **Rogue / Ranger** keystones usually penalize armor or max life (evasion is the survival layer). Exception: Trickster Mastery penalizes crit chance / crit multiplier instead

### Example Keystones

| Keystone | Bonuses | Penalty |
|----------|---------|---------|
| Tank Mastery (Warrior) | +22% Armor, +30% Max Life | -20% Damage |
| Berserker Mastery (Warrior) | +19% Physical Damage, +30% Life Leech | -20% Max Life |
| Sharpshooter Mastery (Ranger) | +57% Projectile Damage, +30% Crit Chance | -20% Max Life |
| Lich Mastery (Necromancer) | +49% Chaos Damage, +39% Spell Damage | -25% Max Life |
| Summoner Mastery (Necromancer) | +66% Minion Damage, +33% Minion Life | -25% Damage |
| Frost Mastery (Mage) | +43% Spell Damage, +30% Max Mana | -15% Crit Chance |
| Inquisitor Mastery (Cleric) | +33% Spell Damage, +30% Crit Chance | -15% Damage |

Each class has two keystones per branch — one at the end of each branch path. Penalties vary by class: STR-based classes trade damage or crit, while DEX and INT classes trade armor or max life. The Spire leaderboard reflects this design philosophy: the top entries are all glass cannons, and the second page is full of cautionary tales.

---

## Travel Nodes & Stat Choices

Travel nodes are the connective tissue of the tree. When you allocate a travel node, you choose which stat it grants — a small decision made dozens of times, with cumulative consequences:

- **Strength** (+5 flat) — the choice for physical fighters and anyone playing a Warrior who hasn't read the other options
- **Dexterity** (+5 flat) — useful for speed, dodge, and critical chance; Rogues and Rangers pick this by reflex
- **Intelligence** (+5 flat) — spell damage and mana scaling; Mages consider any other choice a waste of a perfectly good node

With 176 travel nodes in the tree, these choices add up. A Warrior routing through 40 travel nodes and picking Strength each time gains +200 STR before even counting minor and notable nodes.

---

## Cross-Class Bridges

The six class regions are connected by diamond-shaped bridge paths — chains of travel nodes linking adjacent classes:

| Bridge | Connects |
|--------|----------|
| Warrior ↔ Mage | A fighter who casts, or a caster who can absorb a hit — either direction is unusual, both are effective |
| Mage ↔ Rogue | Arcane precision and close-range application; philosophical differences, shared disinterest in being seen |
| Rogue ↔ Cleric | Shadow and holy — theologically awkward, mechanically effective |
| Cleric ↔ Ranger | Divine support from a distance, which the Cleric finds professionally humbling |
| Ranger ↔ Necromancer | Arrows and minions — more complementary than they appear, less explicable than they should be |
| Necromancer ↔ Warrior | For heroes who want to destroy things and then make professional use of the remains |

Crossing into another class's region costs travel points (you're spending nodes on connectors rather than stats), but unlocks access to their notable and keystone nodes. A Warrior who bridges into Mage territory can pick up spell damage nodes — unorthodox, effective, and precisely the sort of thing that makes build theorycrafting worth the time.

---

## Core Hub Mana Cluster

At the very centre of the tree sits the Core Hub — a ring of twelve slots equidistant from every class. Six of those slots are now mana stat nodes; each has an outward "tail" notable behind it, and beyond those a second outer tier of stronger notables. Sustain has gone from "what your INT happens to give you" to "what you pathed to."

### Hub Ring (six minor stats, alternating)

Walking through the ring grants one of two flavours, depending on which slot you reach first:

| Slot | Node | Stat |
|------|------|------|
| 2, 6, 10 of 12 | **Mana Wellspring** | +mana regen % (5 levels) |
| 4, 8, 12 of 12 | **Mana Efficiency** | -mana cost % (5 levels) |

The flavours alternate around the ring, so any class can reach either kind without doubling back.

### Inner Tails (six notables, one per hub)

Each repurposed hub slot has a single notable connected outward — a stronger version of its parent's flavour:

| Parent Hub | Tail Notable | Effect |
|------------|--------------|--------|
| Regen hubs | **Deep Wellspring** | Greater mana regen + flat max mana |
| Cost hubs | **Practiced Casting** | Greater mana cost reduction |

### Outer Tails (six notables, deeper investment)

A second outward ring of notables sits beyond the inner tails — for builds willing to commit a longer travel:

| Parent | Outer Notable | Effect |
|--------|---------------|--------|
| Regen line | **Vast Reservoir** | Significant mana regen + larger flat max mana |
| Cost line | **Arcane Mastery** | Master-level cost reduction |

### Why This Matters

The hub gives every class a deliberate sustain path that competes with damage branches for the same points. Allocating a full mana lane (hub → inner tail → outer tail) is roughly seven points; spent on a damage branch those same points buy a notable cluster instead. The choice is the point. Pathfinders, Occultists, and anyone running a high-cost 6-link skill will find the detour pays for itself; pure burst builds may decide the damage path is worth the thirst.

---

## Stat Modifier Stacking

Passive tree bonuses don't all stack the same way. Three modifier types govern how bonuses combine — a distinction that matters considerably more than it initially looks:

| Type | Behaviour | Example |
|------|-----------|---------|
| **Flat** | Added directly | +50 Strength, +50 Damage |
| **Percent** | Additive with other percent bonuses | Two +5% Armor nodes = +10% Armor |
| **Multiplier** | Multiplicative scaling | Compounds with other multiplier sources |

---

## Respec

Heroes can fully respec their passive tree at any time. A full respec deallocates every node except the starting node and returns all points to your pool. Travel node stat choices are also reset.

**Partial respec** is also available — you can deallocate individual nodes one level at a time, provided removing the node doesn't break your tree's connectivity. The tree enforces that all allocated nodes must remain connected to the starting node through other allocated nodes. No orphaned branches allowed.

---

## Pathing Rules

Four rules govern what you can and can't do. They are not complex. They become important the moment you try to violate them:

1. **Start from your class node** — every allocation must connect back to it; the tree is radial, not open
2. **Adjacent nodes only** — you can only allocate nodes connected to at least one already-allocated node; there is no teleportation
3. **No orphans** — deallocating a node that would disconnect other nodes from the start is blocked; the tree enforces its own topology
4. **One tree per hero** — each hero has their own independent passive tree; what your Warrior puts into Defence does not affect your Mage's Frost build

---

## Strategy Tips

- **Specialise early** — pick one branch and invest deeply before spreading out. Scattered points produce scattered results.
- **Travel nodes matter** — 40 travel nodes × +5 STR = +200 STR. Choose your travel stat deliberately.
- **Keystones define builds** — decide which keystone you're pathing toward before you start allocating. Working backward from the destination is more efficient than wandering forward.
- **Cross-class bridges are expensive** — each bridge costs 3-4 travel nodes of pure routing. Only cross if the destination nodes are worth the detour.
- **Respec is free** — experiment without fear. The worst outcome is learning something about your build preferences.
