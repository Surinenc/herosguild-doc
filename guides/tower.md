# Abyssal Spire (Tower)

The Abyssal Spire is an endless dungeon challenge with scaling enemies.

---

## Unlocking the Spire

**Requirement:** At least one hero at level 95+

---

## Floor Types

| Event | Floors |
|-------|--------|
| Combat | Every floor |
| Mini-boss | Every 10 floors (10, 20, 30, 40...) |
| Shop | Every 15 floors (15, 30, 45...) |
| Major boss | Every 25 floors (25, 50, 75, 100...) |

Note: Major boss takes precedence over mini-boss (floor 50 is major boss, not mini-boss).

---

## Enemy Scaling

### Enemy Level

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

| Floor Range | Tier |
|-------------|------|
| 1-10 | 2 (Uncommon) |
| 11-25 | 3 (Rare) |
| 26-50 | 4 (Elite) |
| 51+ | 5 (Boss-tier) |

### Enemy Count

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

The tower cycles through 5 environments every 20 floors:

| Floors | Environment | Enemy Types |
|--------|-------------|-------------|
| 1-20 | Crystal Halls | Construct, Elemental |
| 21-40 | Shadow Depths | Undead, Demon |
| 41-60 | Infernal Chambers | Demon, Dragon |
| 61-80 | Celestial Heights | Construct, Elemental |
| 81-100 | Void Sanctum | Demon, Undead, Dragon |

Environments cycle after floor 100.

---

## Shop Items

Shops appear after floors 15, 30, 45, etc.

| Item | Price | Effect |
|------|-------|--------|
| Healing Potion | 25g | Restore 50 HP to one hero |
| Greater Healing Potion | 60g | Restore 100 HP to one hero |
| Elixir of Vigor | 40g | Restore 25% HP to all heroes |
| Antidote | 15g | Cure poison, restore 10 HP |

---

## Tower Unique Items

Only drop from major boss floors (25, 50, 75, 100...).

| Item | Min Floor | Drop Chance |
|------|-----------|-------------|
| Sigil of the Spire | 25 | 50% |
| Abyssal Shard | 50 | 40% |
| Void Crystal | 75 | 30% |
| Spirebreaker Fragment | 100 | 25% |

Higher tier items are rolled first.

---

## Score Calculation

```
Score = (Floor × 100) + (Enemies Defeated × 10) + (Gold Earned ÷ 100)
```

---

## Related Guides

- [Heroic Dungeons](heroic-dungeons.md)
- [Combat System](combat.md)
