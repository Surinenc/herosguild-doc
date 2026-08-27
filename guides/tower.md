# Abyssal Spire (Tower)

The Abyssal Spire is an endless dungeon challenge with scaling enemies — a tower that exists solely to answer the question "how far can your heroes go before the universe objects?"

---

## Unlocking the Spire

**Requirements:**
- At least one hero at level 95+
- Party size: **maximum 6 heroes** (`selectedIds.size < 6` in `TowerMenu.tsx`)

---

## Floor Types

Every floor is a fight. The only variety is what kind of fight, and whether there's a shop afterwards to contemplate your dwindling resources.

| Event | Floors |
|-------|--------|
| Combat | Every floor |
| Mini-boss | Every 10 floors (10, 20, 30, 40...) |
| Shop | Every 15 floors (15, 30, 45...) |
| Major boss | Every 25 floors (25, 50, 75, 100...) |

Note: Major boss takes precedence over mini-boss (floor 50 is major boss, not mini-boss).

---

## Enemy Scaling

The Guild Clerk has watched the Spire leaderboard with morbid fascination. The numbers below explain why most runs end in the Chapel.

### Enemy Level

Enemies start at level 100 and climb steadily. By floor 50, they're level 137 — comfortably stronger than most heroes who haven't been grinding Paragon points with religious dedication.

```
Enemy Level = 100 + floor(Floor × 0.75)
```

| Floor | Enemy Level |
|-------|-------------|
| 1 | 100 |
| 10 | 107 |
| 50 | 137 |
| 100 | 175 |

### Difficulty Tier

The tier system ensures that even if you've mastered the early floors, the Spire has something unpleasant in reserve.

| Floor Range | Tier |
|-------------|------|
| 1-10 | 2 (Uncommon) |
| 11-25 | 3 (Rare) |
| 26-50 | 4 (Elite) |
| 51+ | 5 (Boss-tier) |

### Enemy Count

The number of enemies per floor increases with depth. The Guild Clerk notes, with concern, that floor 100+ pits your party against up to 7 enemies simultaneously:

| Floor Range | Min | Max | Boss Adds |
|-------------|-----|-----|-----------|
| 1-10 | 2 | 3 | 2 |
| 11-25 | 3 | 4 | 3 |
| 26-50 | 4 | 5 | 4 |
| 51-75 | 4 | 6 | 4 |
| 76-100 | 5 | 6 | 4 |
| 100+ | 5 | 7 | 5 |

---

## Environments

The tower cycles through 5 environments every 20 floors. Heroes universally dread the Shadow Depths (undead AND demons), though the Guild Clerk personally considers the Void Sanctum worse:

| Floors | Environment | Enemy Types |
|--------|-------------|-------------|
| 1-20 | Crystal Halls | Construct, Elemental |
| 21-40 | Shadow Depths | Undead, Demon |
| 41-60 | Infernal Chambers | Demon, Dragon |
| 61-80 | Celestial Heights | Construct, Elemental |
| 81-100 | Void Sanctum | Demon, Undead, Dragon |

Environments cycle after floor 100. The Guild Clerk has noted that parties who survive to the Void Sanctum rarely discuss the experience afterwards. Those who do use words like "never again."

---

## Shop Items

Shops appear after floors 15, 30, 45, etc. The Spire merchant's prices are, in the Guild Clerk's assessment, "optimistic given the circumstances" — but when you're on floor 47 with three wounded heroes, you'll pay anything.

| Item | Price | Effect |
|------|-------|--------|
| Healing Potion | 25g | Restore 50 HP to one hero |
| Greater Healing Potion | 60g | Restore 100 HP to one hero |
| Elixir of Vigor | 40g | Restore 25% HP to all heroes |
| Antidote | 15g | Cure poison, restore 10 HP |

---

## Tower Set Items

Three two-piece sets drop only from Spire major-boss floors. Each set grants a baseline two-piece bonus that applies everywhere, plus a **tower-only bonus** that activates only while you are inside the Abyssal Spire — the realm's way of giving the Spire its own metagame without breaking the wider game's economy.

| Item | Slot | Set | Drop Floor |
|------|------|-----|------------|
| Spirebreaker Helm | Head | Spirebreaker | 25 |
| Spirebreaker Aegis | Armor | Spirebreaker | 50 |
| Voidtouched Cloak | Armor (Mage/Necromancer) | Voidtouched | 50 |
| Voidtouched Focus | Accessory (Mage/Necromancer) | Voidtouched | 75 |
| Abyssal Boots | Boots | Abyssal | 75 |
| Abyssal Mask | Head | Abyssal | 100 |

**Set bonuses:**

| Set | Two-Piece (Always) | Two-Piece (Tower Only) |
|-----|--------------------|------------------------|
| Spirebreaker | +50 armor, +20 VIT, +200 HP | +75 armor, +400 HP |
| Voidtouched | +35 INT, +150 mana, +20 crit damage | +25 INT, +20% mana cost reduction, +150 mana |
| Abyssal | +6 crit chance, +20 DEX, +12 LCK | +10 crit chance, +35 crit damage, +15 DEX |

The tower-only halves are gated by an `isTowerCombat` flag the Spire run sets at the start of each fight. The Guild Clerk notes that the gating exists "so that an Abyssal Mask doesn't trivialise the rest of the game," which it would.

Each set takes both pieces to activate. Single-piece set items grant the base item stats but no set bonus — which is why most Spire-bound Guild Masters either run a full Spirebreaker tank or commit to none of it.

---

## Currency Drops

Each floor cleared rolls for [crafting currencies](crafting.md#crafting-currencies) — independent Bernoulli trials per currency, so a single floor can drop several. The Spire is the only content source that awards currencies on *every* floor rather than per-completion, which makes deep runs a meaningful farming path for the rarer items.

| Currency | Drop Rate (per floor) |
|----------|-----------------------|
| Powder of First Enchantment | 10% |
| Powder of Erasure | 8% |
| Salt of Renewal | 3% |
| Ichor of Reshaping / Empowerment / Sealing | 2% each |
| Salt of Cleansing | 0.8% |
| Portent of the Weighing | 0.8% |
| Portent of Kinship | 0.8% |
| Cursed Sigil | 0.5% baseline (soft pity) |

Those rates only apply once you are deep enough to earn them. The Spire has no star rating of its own, so it uses depth as one: floors **1–10** count as ⭐⭐, **11–25** as ⭐⭐⭐, **26–50** as ⭐⭐⭐⭐, and **51 and beyond** as ⭐⭐⭐⭐⭐. Since each reagent has a minimum rating (see [Crafting Guide — Currencies](crafting.md#crafting-currencies)), the shallow floors pay in Powders and Salt of Renewal, Ichors begin at floor 11, Salt of Cleansing and the Portents at floor 26, and the Cursed Sigil not until floor 51. Floor 1 is a great many things, but it is not endgame content, and it has stopped raining Portents accordingly.

### Cursed Sigil Soft Pity

The Cursed Sigil's 0.5% base rate on Abyssal floors ramps up if you go long enough without seeing one. The counter tracks floors cleared since the last Sigil dropped from *any* source — raids, world bosses, and heroic dungeons all reset it.

The counter climbs on **every** floor you clear, including the shallow ones the Sigil can't drop on at all. Grinding floors 1–50 therefore builds pity you cannot spend until you're past floor 50 — a saved-up debt the Spire honours the moment you're deep enough to collect, which is either good planning or a long walk, depending on temperament.

```
Rate = min(15%, 0.5% + max(0, floors_since_last − 50) × 0.05%)
```

| Floors Since Last Sigil | Drop Rate |
|-------------------------|-----------|
| 1–50 | 0.5% (flat) |
| 75 | 1.75% |
| 100 | 3.0% |
| 150 | 5.5% |
| 250 | 10.5% |
| 340+ | 15% (cap) |

The pity ramp is the Spire's quiet concession that running 340 floors without a Legendary drop would test even the Guild Clerk's commitment to accurate recordkeeping.

---

## Score Calculation

The Spire keeps score, because even existential dread benefits from a competitive element. The Guild Clerk maintains the leaderboard and has observed that the top scores belong exclusively to parties who brought two Clerics.

```
Score = (Floor × 100) + (Enemies Defeated × 10) + (Gold Earned ÷ 100)
```

---

## Related Guides

- [Heroic Dungeons](heroic-dungeons.md)
- [World Boss Raids](raids.md)
- [Combat System](combat.md)

---

*"The Spire doesn't end. You do."*
