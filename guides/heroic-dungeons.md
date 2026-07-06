# Heroic Dungeons

Heroic Dungeons feature special modifiers that add challenge and reward scaling to endgame content. They are, essentially, regular dungeons that have decided to take things personally.

---

## The 10 Heroic Modifiers

Each heroic dungeon has one modifier that changes gameplay. Think of them as the dungeon's way of saying "you thought this would be straightforward?"

### Overwhelming Force 💪
**Difficulty:** 2/3

The straightforward approach to making things harder: make them bigger and angrier.

- Enemies have +50% HP
- Enemies deal +25% damage
- Reward: +50% gold
- Visual: Red enemy glow

### Relentless Assault ⚔️
**Difficulty:** 3/3

Kill them once, kill them again. The Guild Clerk considers this modifier personally offensive.

- Enemies respawn once at 50% HP when killed
- Reward: +2 guaranteed item drops
- Visual: Dark mist particles

### Vampiric Enemies 🩸
**Difficulty:** 2/3

Self-healing enemies. The Guild Clerk finds this deeply unfair and has filed a formal complaint with the dungeon.

- Enemies heal 10% of damage dealt
- Reward: +30% gold
- Visual: Dark red enemy glow, life drain particles

### Enrage Timer ⏱️
**Difficulty:** 3/3

A clock that punishes dawdling. The Guild Clerk has strong feelings about heroes who stop to loot mid-combat.

- After turn 15, all enemies gain +100% damage (×2.0)
- Reward: +40% gold
- Visual: Red screen tint, timer UI

### Elite Swarm 👑
**Difficulty:** 2/3

Every enemy gets a promotion. Nobody asked for this.

- All normal enemies upgraded to elite tier
- Reward: +1 material tier, +40% gold
- Visual: Gold enemy glow

### Fragmented Reality 🌀
**Difficulty:** 2/3

The dungeon rearranges itself while you're inside it. The map you made three rooms ago is now decorative fiction.

- Room connections randomize every 3 rooms
- Reward: +30% gold
- Visual: Reality glitch particles, warped floor overlay

### Cursed Ground 💀
**Difficulty:** 2/3

The floor is, quite literally, trying to kill you. Clerics earn their wages here.

- All heroes take 2% max HP damage per turn
- Reward: +1 material tier, +40% gold
- Visual: Cursed floor overlay, dark aura, purple tint

### Arcane Instability ✨
**Difficulty:** 2/3

Random magical chaos. Sometimes it helps you. Usually it doesn't.

- Random spell effects each room
- Reward: +100% skill gem chance, +30% gold
- Visual: Arcane sparks, arcane runes floor overlay

### Shattered Defenses 🛡️
**Difficulty:** 2/3

Your armor works 30% less well. Warriors find this existentially threatening.

- Heroes have -30% armor and resistances
- Reward: +30% gold, 3× defense gear drop frequency

### Chaos Incarnate 🌪️
**Difficulty:** 3/3

Two modifiers at once. For heroes who looked at the other nine options and thought "why not both?"

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

Gold rewards are calculated as follows. The Guild Clerk considers the bonus "hazard pay, and barely adequate":

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

Three heroic dungeons are available each week, rotating every **Thursday at 00:00 UTC** (the rotation epoch is 2026-01-01, a Thursday, and the window steps forward in 7-day increments — `WeeklyRotation.ts:24`). The Guild Clerk is responsible for posting the rotation on the notice board and, despite years of service, has never once been thanked.

| Tier | Stars | Level |
|------|-------|-------|
| Heroic Trial | ⭐⭐⭐ | Base level (min 80) |
| Heroic Challenge | ⭐⭐⭐⭐ | Base + 5 |
| Heroic Ordeal | ⭐⭐⭐⭐⭐ | Base + 10 |

Each tier gets a randomly assigned modifier. Chaos Incarnate is excluded from the weekly rotation entirely. No modifier repeats within the same week.

Access: Mission Board → Heroic filter (🔥). A countdown timer shows time until the next weekly reset.

---

## Recipe Drops

Each heroic dungeon completion rolls for recipe scrolls — 8% for an Epic recipe and 2% for a Legendary, independently. Duplicates convert to gold (10,000g / 100,000g). See [Crafting Guide — Recipe Drops](crafting.md#recipe-drops).

---

## Related Guides

- [Combat System](combat.md)
- [Abyssal Spire](tower.md)
- [World Boss Raids](raids.md)

---

*"Heroic modifiers exist because someone, somewhere, decided that regular dungeons weren't unfair enough."*
