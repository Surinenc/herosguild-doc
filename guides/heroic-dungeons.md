# Heroic Dungeons

Heroic Dungeons feature special modifiers that add challenge and reward scaling to endgame content. They are, essentially, regular dungeons that have decided to take things personally.

---

## The 10 Heroic Modifiers

Each heroic dungeon has one modifier that changes gameplay. Think of them as the dungeon's way of saying "you thought this would be straightforward?"

### Overwhelming Force 💪
**Difficulty:** 2/3

- Enemies have +50% HP
- Enemies deal +25% damage
- Reward: +50% gold
- Visual: Red enemy glow

### Relentless Assault ⚔️
**Difficulty:** 3/3

- Enemies respawn once at 50% HP when killed
- Reward: +2 guaranteed item drops
- Visual: Dark mist particles

### Vampiric Enemies 🩸
**Difficulty:** 2/3

- Enemies heal 10% of damage dealt
- Reward: +30% gold
- Visual: Dark red enemy glow, life drain particles

### Enrage Timer ⏱️
**Difficulty:** 3/3

- After turn 15, all enemies gain +100% damage (×2.0)
- Warning message at turn 12
- Reward: +40% gold, +50% bonus if average combat finishes before turn 12
- Visual: Red screen tint, timer UI

### Elite Swarm 👑
**Difficulty:** 2/3

- All normal enemies upgraded to elite tier
- Reward: +1 material tier, +40% gold
- Visual: Gold enemy glow

### Fragmented Reality 🌀
**Difficulty:** 2/3

- Room connections randomize
- Reward: +30% gold
- Visual: Reality glitch particles, warped floor overlay

### Cursed Ground 💀
**Difficulty:** 2/3

- All heroes take 2% max HP damage per turn
- Reward: +1 material tier, +40% gold
- Visual: Cursed floor overlay, dark aura, purple tint

### Arcane Instability ✨
**Difficulty:** 2/3

- Random spell effects each room
- Reward: +100% skill gem chance, +30% gold
- Visual: Arcane sparks, arcane runes floor overlay

### Shattered Defenses 🛡️
**Difficulty:** 2/3

- Heroes have -30% armor and resistances
- Reward: +30% gold, 3× defense gear drop frequency

### Chaos Incarnate 🌪️
**Difficulty:** 3/3

- 2 random modifiers active simultaneously
- Reward: +75% gold (stacks with component modifiers)
- Visual: Chaos swirl particles

---

## Difficulty Distribution

| Difficulty | Modifiers |
|------------|-----------|
| 2/3 | Overwhelming Force, Vampiric Enemies, Elite Swarm, Fragmented Reality, Cursed Ground, Arcane Instability, Shattered Defenses |
| 3/3 | Relentless Assault, Enrage Timer, Chaos Incarnate |

---

## Reward Multiplier

Gold rewards are calculated as:

```
Base Gold × Modifier Gold Bonus × Difficulty Bonus
```

Difficulty bonuses:
- Difficulty 2: +10%
- Difficulty 3: +20%

**Example multipliers:**
- Overwhelming Force: 1.5 × 1.1 = 1.65x
- Relentless Assault: 1.0 × 1.2 = 1.2x
- Chaos Incarnate: 1.75 × 1.2 = 2.1x

---

## Weekly Rotation

Three heroic dungeons are available each week, rotating every Sunday at 00:00 UTC:

| Tier | Stars | Level |
|------|-------|-------|
| Heroic Trial | ⭐⭐⭐ | Base level (min 80) |
| Heroic Challenge | ⭐⭐⭐⭐ | Base + 5 |
| Heroic Ordeal | ⭐⭐⭐⭐⭐ | Base + 10 |

Each tier gets a randomly assigned modifier (Chaos Incarnate is excluded from weekly rotation — it only appears as a standalone modifier). No modifier repeats within the same week.

Access: Mission Board → Heroic filter (🔥). A countdown timer shows time until the next weekly reset.

---

## Related Guides

- [Combat System](combat.md)
- [Abyssal Spire](tower.md)

---

*"Heroic modifiers exist because someone, somewhere, decided that regular dungeons weren't unfair enough."*
