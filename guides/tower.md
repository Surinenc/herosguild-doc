# Abyssal Spire (Tower)

The Abyssal Spire is an endless dungeon challenge with scaling enemies — a tower that exists solely to answer the question "how far can your heroes go before the universe objects?"

---

## Unlocking the Spire

**Requirements:**
- At least one hero at level 95+
- Party size: **maximum 4 heroes** (unlike regular dungeons, which allow up to 6)

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

## Tower Unique Items

Only drop from major boss floors (25, 50, 75, 100...). Reaching them is the hard part. The items are the reward for not dying.

| Item | Min Floor | Drop Chance |
|------|-----------|-------------|
| Sigil of the Spire | 25 | 50% |
| Abyssal Shard | 50 | 40% |
| Void Crystal | 75 | 30% |
| Spirebreaker Fragment | 100 | 25% |

Higher tier items are rolled first. The Spirebreaker Fragment at floor 100 has a 25% drop chance, which the Guild Clerk considers "stingy, given what it takes to get there."

---

## Score Calculation

The Spire keeps score, because even existential dread benefits from a competitive element. The Guild Clerk maintains the leaderboard and has observed that the top scores belong exclusively to parties who brought two Clerics.

```
Score = (Floor × 100) + (Enemies Defeated × 10) + (Gold Earned ÷ 100)
```

---

## Related Guides

- [Heroic Dungeons](heroic-dungeons.md)
- [Combat System](combat.md)

---

*"The Spire doesn't end. You do."*
