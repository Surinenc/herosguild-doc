# Heroic Dungeons

Heroic Dungeons feature special modifiers that add challenge and reward scaling to endgame content. They are, essentially, regular dungeons that have decided to take things personally.

---

## The Heroic Modifiers

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

> **Currently out of rotation** — and for a more interesting reason than the others. The clock is real; it simply never strikes. Heroic fights are over, one way or another, long before turn 15, so the modifier was promising a threat no party ever stayed long enough to meet. The realm has stopped offering it.

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

> **Currently out of rotation.** The rooms, it turns out, stay stubbornly where they were built, and the realm declines to post a contract promising otherwise.

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

> **Currently out of rotation**, for much the same reason as Fragmented Reality: the random spell effects never actually occur, and a contract describing a hazard that never arrives is, in the Guild Clerk's view, fraud with extra steps.

### Shattered Defenses 🛡️
**Difficulty:** 2/3

Your armor works 30% less well. Warriors find this existentially threatening.

- Heroes have -30% armor and resistances
- Reward: +30% gold, and nothing else — no shower of replacement armour, whatever the name suggests to an optimist. Do not plan a wardrobe around it

### Chaos Incarnate 🌪️
**Difficulty:** 3/3

Two modifiers at once. For heroes who looked at the other options and thought "why not both?"

- 2 random modifiers active simultaneously
- Reward: +75% gold (stacks with component modifiers)
- Visual: Chaos swirl particles

> **Currently out of rotation.** Chaos Incarnate is kept out of the weekly draw; the realm, for once, is showing restraint.

---

## Difficulty Distribution

| Difficulty | Modifiers |
|------------|-----------|
| 2/3 | Overwhelming Force, Vampiric Enemies, Elite Swarm, Cursed Ground, Shattered Defenses (*Fragmented Reality* and *Arcane Instability* are defined at this difficulty but out of rotation) |
| 3/3 | Relentless Assault (*Enrage Timer* and *Chaos Incarnate* are defined at this difficulty but out of rotation) |

---

## Reward Multiplier

A heroic contract's base gold is the **regular contract curve for its stars and monster level, times ten** — see [Monster Level](dungeons.md#monster-level-power) for the curve itself. Three heroics a week will cover the wages of a full five-star roster, which is rather the point of there being exactly three.

On top of that base, the modifier and difficulty bonuses apply. The Guild Clerk considers the result "hazard pay, and barely adequate":

```
Base Gold (contract curve × 10) × Modifier Gold Bonus × Difficulty Bonus
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

Three heroic dungeons are available each week, rotating every **Thursday at 00:00 UTC**, regardless of what day it is in the guild. The Guild Clerk is responsible for posting the rotation on the notice board and, despite years of service, has never once been thanked.

| Tier | Stars | Level |
|------|-------|-------|
| Heroic Trial | ⭐⭐⭐ | Base level (min 80) |
| Heroic Challenge | ⭐⭐⭐⭐ | Base + 5 |
| Heroic Ordeal | ⭐⭐⭐⭐⭐ | Base + 10 |

Each tier gets a randomly assigned modifier, and no modifier repeats within the same week. Four are excluded from the draw: **Chaos Incarnate**, which stacks two others and is kept back; **Fragmented Reality** and **Arcane Instability**, which don't do what they say on the tin; and **Enrage Timer**, whose clock no heroic fight runs long enough to hear — rather than print a promise on the contract card that the fight would then decline to keep, the realm simply doesn't offer them.

The contract names its modifier and quotes what the modifier does, so the card tells you what you are walking into before you agree to walk into it.

Access: Mission Board → Heroic filter (🔥). A countdown timer shows time until the next weekly reset.

Two gates stand in front of all this. You need **10,000 reputation** before heroic contracts appear at all, and you may complete **three per week** — the three that are posted, in other words, and not one of them twice. A dispatched heroic leaves the list, so the board shows what is still open rather than what was once available.

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
