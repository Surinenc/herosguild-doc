# World Boss Raids

When a World Boss appears in the realm, the Guild gets an entry on the notice board, the Guild Clerk reaches for a fresh ledger, and somebody — usually the Warrior — says "right, then" in a tone that nobody finds reassuring. A raid is the largest, slowest, most cooperative fight the Guild can put together: up to fifteen heroes, organised into groups, deployed across a tactical board against a single creature that has decided its existence is a problem worth solving in person.

This guide covers how raids are unlocked, how they are fought, and what they pay out for surviving them.

---

## Unlocking a Raid

Raids do not appear on demand. The realm spawns them on its own schedule, and the Guild Clerk has stopped explaining this to people who ask whether it can be hurried up.

**Requirements:**
- **Guild Reputation:** 5000 or higher
- **Heroes:** at least one hero at level 50+
- **Spawn chance:** 5% per day, rising to 10% if it has been 30+ days since the last boss

When a boss spawns, the Guild gets an event notification (*"A World Boss has appeared…"*) and the boss persists for **7 days** before retreating back into whatever it came from. The same boss won't be picked two spawns in a row — the realm draws from a pool of three and avoids the last two picks, which is its way of varying the menu.

You launch the raid from the Guild screen, where the active world boss appears as a card. Pressing it opens the raid setup screen.

---

## What a Raid Looks Like

A raid is a single fight on a tactical grid. The board is **5 rows × 5 columns** plus a dedicated **Boss Arena** zone, and the rows run from F (front, nearest the boss) through M, U, L, to B (back, furthest away). Most ranged abilities pay attention to columns; most movement happens in rows; the boss reaches you when you reach the front.

- **Up to 15 heroes deployed total** — a hard cap, and the sixteenth volunteer is thanked for their enthusiasm and sent to mind the shop
- **Groups are organisational, not capped** — the setup screen lets you build as many or as few groups as you like as long as total deployed heroes stay at or under 15. The realm proposes **five default anchor zones** (F3, M3, U3, L3, B3); you can use them, ignore them, or build your roster a different way
- **5 heroes per zone maximum** — a sixth would have to stand on someone. Boss-melee zones (F1–F5) are where the boss reaches you
- **No rotation, no rest** — everyone you bring fights for the entire raid
- **Orders are issued per group, not per hero**

A group is the unit you actually pilot during the raid. Each group is assigned a home zone, a **role** (Standard or Add DPS), and a composition. Standard groups stay focused on the boss; Add DPS groups break off to handle adds as they spawn. Heroes inside a group take their own actions in initiative order, but you tell them where to be and what to do at the group level.

---

## The Three Bosses

The realm rotates between three bosses, each with its own pattern of pain. The Guild Clerk has prepared a brief on each, mostly out of self-defence.

### Ancient Dragon

A traditional sort of monster. Front-row pressure, sweeping area attacks, and a passive understanding that any hero who hasn't ducked yet is volunteering.

**Phases:**
- **Grounded** (100 → 75% HP) — opening posture
- **Enraged** (75 → 50% HP) — phase transition at 75% HP
- **Flying** (50 → 25% HP) — phase transition at 50% HP
- **Dying Rage** (≤25% HP) — the polite phase ends here

**Signature mechanics:**
- **Dragon Claw** — strikes a hero, with cleave that spills 50% damage onto every other hero in the same zone. The simplest argument against zone-stacking ever made.
- **Dragon Bite** — heavy single-target damage.
- **Fire Bolt** — ranged hit with a burning DoT attached.
- **Fire Breath** (Cone telegraph) — front-row sweep.
- **Tail Sweep** (Row telegraph) — strikes a random occupied row (F/M/U/L).
- **Wing Buffet** (Column telegraph) — strikes a random occupied column (1–5).
- **Inferno Wave** (Spread telegraph) — multiple scattered impacts; spread your groups out.

**Resistances:** fire-resistant, ice-weak. Bring cold.

### Lich King

The interrupt fight. Damage from the Lich is manageable. Damage from the Lich *and* its undead retinue *and* the spell you didn't interrupt is not.

**Phases:**
- **Base State** (100 → 75% HP) — opening posture
- **Animator** (75 → 50% HP) — periodic Risen Champion summons every 8 turns
- **Vampiric** (50 → 25% HP) — Heal Steal channel queued every 7 turns
- **Mass Resurrection** (≤25% HP) — raises wraiths in bulk on hero deaths; the fight gets dense

**Signature mechanics:**
- **Frost Lance** — single-target slowing strike.
- **Frost Bolt** (Spread telegraph) — scattered ranged hits.
- **Ice Tomb** (SpotSoak telegraph) — drops a hazard zone; move out.
- **Frost Volley** — heavy column-pattern damage.
- **Death Touch** — single-target SpotSoak telegraph. Step out of it and it touches nobody, which is the best possible outcome for anything with that name.
- **Heal Steal** (CRITICAL — interrupt required) — heals the Lich for **25% of MAX HP** on success (more on Heroic, because of course it is). This is the single biggest reason raids end on enrage instead of victory.
- **Risen Champion** — periodic add wave (every 8 turns in Phase 1+).
- **Wraith adds** — spawn event-driven when a hero dies in the Mass Resurrection phase.

**Heal Steal interrupt:** the interrupt order on the appropriate group rolls **INT + DEX vs DC 14** on Normal, **DC 20** on Heroic. First success cancels the cast; failures stack as "didn't make it." A casting Lich is a problem only if it finishes casting.

**Resistances:** higher magic resist than armor (60 vs 40), plus elemental — resists ice and dark, weak to fire and holy. Pick your damage types accordingly.

### Void Titan

The forced-movement fight. The Titan does not want you where you are, and the Titan has opinions about that.

**Phases:**
- **Gaze** (100 → 75% HP) — opening posture, ranged spread pressure
- **Fractured Mind** (75 → 50% HP) — cluster-amplifying Spread telegraphs; punishes group stacking
- **Spatial Phase** (50 → 40% HP) — **forced movement every 3 turns**, direction rotates S → W → N → E
- **Void Implosion** (≤40% HP) — the closing sequence; the Stack telegraph comes round every 7 turns, like a bus nobody wants to catch

**Signature mechanics:**
- **Void Bolt** — baseline ranged hits.
- **Void Lash** — fires every turn. The fight's metronome.
- **Mind Flay** (SpotSoak telegraph) — single-tile soak; move out.
- **Reality Tear** (Column telegraph) — empties a column.
- **Fractured Mind** (Spread telegraph) — scattered impacts that hit harder the more clustered you are. On Heroic, every shared-zone hit also stacks **Voidmarked** on the affected heroes (see below), turning the cluster from a one-cycle problem into a fight-long one.
- **Void Implosion** (Stack telegraph) — the fight's signature mechanic. The safe zone is **fixed at the M-row centre triplet — M2, M3, M4**, and it never moves, which is the only courtesy the Titan extends. Converge there, *or die.* Every hero caught outside the safe zone takes the damage *and* gains a **Voidmarked** stack. No second draft of this.

This is the fight where standing orders pay for themselves, because manual movement against the forced-relocation cadence wastes order points you don't have.

### Enrage

The Dragon and the Lich share a hard enrage threshold at **turn 250**; the Void Titan's is **turn 300**, its fight being so busy shoving you about the board that it needs the extra fifty turns to fit everything in. From that point on, the boss's base damage scales by **+10% per turn past the threshold, additive, with no cap.** At threshold + 25, base damage is ×3.5; at threshold + 50, it's ×6.0; past that, it's the kind of number the Guild Clerk will not write down for fear of jinxing whatever happens next.

The shape is linear, not compounding — but the practical message is the same: raids are not endurance contests. If you are not winning before the enrage turn, you are losing on the one after.

### Wounded — The Cleave Tax

Every time a hero is in the affected zone of a dodgeable cleave (Cone, Row Sweep, or Column Sweep) when it resolves, they take the damage *and* gain a **Wounded** stack. Wounded does two unpleasant things:

- **+20% damage on every subsequent telegraph hit** to that hero (the multiplier compounds: at N stacks, the next telegraph deals `× (1 + 0.2 × N)`)
- **+30% to all damage taken** by that hero, permanently for the fight

Both effects stack with additional Wounded marks. Both are permanent within an attempt — no decay, no time-out, no priest can cleanse them — and both are cleared the moment the attempt **ends**, on victory, wipe or retreat alike, rather than lingering on the roster until the next raid happens to start. A save loaded with stale marks on it has them stripped too, a raid being incapable of being in progress across a load.

The avoidance check is **deterministic and positional.** A hero who moved out of the telegraphed zone before resolution takes no damage and gains no Wounded stack. A hero who didn't gets both. There is no dodge roll. The Guild Clerk approves of this — it makes the heroes' movement orders *matter* in a way that random saving throws never quite did.

SpotSoak and Spread telegraphs do not apply Wounded. The risk is specifically in the column- and row-shaped cleaves.

### Voidmarked — The Void Titan Tax

A parallel debuff system to Wounded, exclusive to the Void Titan. Heroes caught outside the Void Implosion safe zone gain a **Voidmarked** stack along with the damage. On Heroic, heroes sharing a zone when Fractured Mind resolves also pick up a stack — because the shared-zone amplification is the punishment vector, and marking the same heroes lets it cascade into the next Implosion.

Each stack does one unpleasant thing, but does it relentlessly:

- **+15% damage taken** per stack on every subsequent hit (additive — ten stacks is +150%, which is a number, and also a eulogy)
- **No stack ceiling** — stacks accumulate without bound, the Void having never been introduced to the concept of *enough*
- **Permanent within the attempt** — no decay, no time-out
- **Cleared on attempt reset** — a wipe and retry resets the slate

The avoidance check, like Wounded, is positional and deterministic. A hero who reached the M-row centre triplet before Void Implosion resolved takes no damage and gains no stack. A hero who did not gets both, and the next Implosion will hit them 15% harder, and the one after that 30%, and so on, until the Void Titan stops being a fight and starts being a budget.

On Normal, only Void Implosion applies Voidmarked; the Fractured Mind shared-zone trigger requires the amplification to exceed 1.0×, which it does only on Heroic. The Guild Clerk has filed this under "things that get worse when you select Heroic," a category she now keeps a dedicated drawer for.

### Normal vs Heroic

Selected at setup. Heroic raises HP and damage substantially across the board, raises interrupt DCs (notably the Lich's Heal Steal from DC 14 to DC 20), and is intended for parties who've already cleared the Normal version and want to know what it's like when the boss is taking it seriously.

**Heroic loot bonuses:**

- **2× raid tokens** — the base token roll is doubled.
- **2× guaranteed materials** — material quantities are doubled. Dragon scales go from 2–4 to 4–8, Phylactery shards 2–4 → 4–8, Reality fragments 1–3 → 2–6.
- **Bonus item-roll pass** — after the normal chance-roll pass, Heroic runs a second independent roll against every item in the boss's loot table. Items already awarded from the first pass are skipped, so a single clear cannot mint two of the same named item. An 8% named drop lands at roughly 15% effective on Heroic — exciting, not guaranteed.
- **Gold unchanged** — the extra reward is in tokens, materials, and drops.

The net effect: roughly 1.65× named-item yield and 1.28× total-item yield per clear, plus the doubled materials and tokens. The Guild Clerk considers this adequate compensation for the substantially increased risk of everyone dying.

---

## Groups and the Board

Each group occupies a home zone and operates from it. By default, the realm proposes anchor zones:

| Group | Default Anchor | Role |
|-------|----------------|------|
| Group 1 | F3 (front centre) | Tank line |
| Group 2 | M3 (middle centre) | Mid-line |
| Group 3 | U3 (upper centre) | Mid-line |
| Group 4 | L3 (lower centre) | Mid-line |
| Group 5 | B3 (back centre) | Rear / specialist |

You can override the anchor at setup, along with each group's role (Standard / Add DPS) and composition. Standard groups stay focused on the boss; Add DPS groups break off to engage adds as they appear. The boss treats anything in the F-row (F1–F5) as **melee distance**, which is useful information for both the heroes you want there and the ones you don't.

---

## Orders and the Five-Budget

You command groups by issuing orders. Each turn you have **5 order points** to spend across all your groups, and most orders cost 1 point.

| Order | Cost | Effect |
|-------|------|--------|
| Move Group | 0 | Reposition a group to an adjacent zone. Free, but the hero moving spends their action on the move. |
| Hold | 0 | The group stays put and defends. |
| Engage | 1 | Press the attack on the nearest valid target. |
| Taunt | 1 | Warrior-only. Forces nearby enemies onto the Warrior. Range: 1 zone (chebyshev). Fizzles out of range. |
| Interrupt | 1 | The group rolls to interrupt a casting enemy. First success cancels. Roll: INT + DEX vs DC. |
| Disengage | 1 | Pull back from melee. |
| Burst | 1 | Mage/Necromancer only. Channel a high-cost spell now. |
| Standing Order | 1 (to set) | Set a default behaviour that persists across turns until changed. Setting it costs 1; it costs nothing to keep. |
| Call Retreat | 0 | End the raid immediately. The Guild Clerk records this without comment, but expressively. |

**Per-group rules:**
- One order per group per turn.
- If you issue two orders to the same group, the **latest wins**.
- Movement consumes that hero's action — moving groups don't also attack the same turn.

Standing orders are the lever for boss patterns you've seen before: the second time you fight the Void Titan, "Standing Order: Converge on the Stack telegraph" is two points well spent.

---

## The Turn Loop

**Raids run in real time.** There is no End Turn button; the boss does not wait for you to finish thinking. Turns auto-resolve on a **6-second base tick**, and you control the pace through a **speed selector** at the top of the raid UI offering ½×, 1×, 2×, and 4× speeds. A **Pause** button sits in the raid phase header — useful when you need to read a queued telegraph or queue a complex set of orders without the tick eating the window.

The loop, in practice:

1. The current turn starts. You see the board state, the queued telegraphs, the threat list, and your group order panel.
2. You queue orders during the tick window — up to 5 points worth, per the budget above.
3. When the tick timer hits zero (or sooner if you've already queued all the orders you intend), the turn resolves itself — moves, attacks, telegraphs that came due, and the boss's own actions.
4. The next turn begins, and you do it again.

A few things worth knowing about the cadence:

- **Turn 0 is setup-only.** Nothing fights, nothing spawns, nothing telegraphs, and nothing ticks — the boss is, for one brief turn, merely looking at you. Use it to position groups before the boss starts swinging.
- **Telegraphs are announced one turn before they resolve.** A telegraph that appears this turn fires *next* turn — that's your window to move out of it or interrupt the cast.
- **Add waves run on a 3-turn cadence, but the guest list varies by boss.** The Ancient Dragon brings 3 Fire Whelps per wave, the Lich King 2 Skeletons, and the Void Titan 2 Wraiths — each boss, in its own way, believing in family. Boss-scripted waves (e.g. the Lich's add-summon abilities) layer on top of this cadence.
- **Ground effects linger.** Burning patches, frost zones, and the Ice Tomb hazard remain on the board after they land and stack with anything else dropped on the same tile.
- **Unspent order points do not carry over.** Each turn refreshes the 5-point budget.
- **Heroes recover between rounds**, as they do anywhere else: mana regenerates, skill cooldowns tick down, and per-turn HP regeneration — food buffs, Alchemy regen, equipped-item regen, the Champion's own Regeneration node — applies. Sustain you have stacked for the rest of the game does not politely stand down because the enemy is enormous.
- **Call Retreat** has its own button outside the order budget; pressing it ends the raid immediately, and with slightly more dignity than the alternative.

The speed selector is the lever for actually surviving the harder fights — speeding up trivial turns and slowing down to read telegraphs and queue intricate group orders during the dangerous ones.

---

## Outcomes

A raid ends in one of three ways.

**Victory** — the boss reaches 0 HP. Loot, gold, raid tokens, and (if it's the first kill of that boss) a recipe unlock land in the Guild vault. The boss slot clears and the realm rolls for the next spawn on its usual schedule.

**Wipe** — every deployed hero reaches 0 HP. The raid ends; the boss does not.

**Retreat** — you press Call Retreat. The raid ends; the boss does not.

### What Happens to Fallen Heroes

Nothing, in the way the Guild Clerk finds most surprising. Unlike regular dungeon defeats — which trigger death-saves, injury rolls, and Infirmary stays — a raid has nothing waiting at the bottom of the fall, and this is **deliberate rather than an oversight**: a raid never kills a hero, full stop. Heroes who fall come out of the fight at **0 HP, in Ready state, with no injury, no infirmary time, and no permadeath risk.** Rest them at the Guild and they recover normally.

Equipment is not lost. The raid is, in this one specific sense, oddly forgiving.

### Retries

A wipe or retreat **does not clear the boss.** The boss persists until its 7-day timer expires, and you can re-launch the raid from the Guild screen as many times as you like in that window. Each attempt rolls its add waves and telegraphs afresh, so the second attempt is not the first attempt replayed.

The Guild Clerk considers this the sporting thing to do. The Warrior considers it the sensible thing to do. They are, for once, in agreement.

### Rewards (on victory)

| Boss | Gold | Raid Tokens | Guaranteed Material |
|------|------|-------------|---------------------|
| Ancient Dragon | 800,000 – 1,200,000 | 5 – 10 | Ancient Dragon Scale |
| Lich King | 1,000,000 – 1,500,000 | 6 – 12 | Phylactery Shard |
| Void Titan | 1,200,000 – 1,800,000 | 8 – 14 | Reality Fragment |

These are the largest purses in the realm, and deliberately so: the hardest fight in the game should not pay like an errand. Heroic difficulty leaves the gold alone and doubles tokens, materials and item rolls instead, on the reasoning that a guild at this point has plenty of money and a shortage of things it can only get here.

Each boss also drops a set of guaranteed items, plus chance-rolled named items from its loot table (Ancestral-rarity tier-set pieces at 20% per roll, alongside other named drops at varying chances). The first kill of each boss unlocks every recipe gated behind it — the kind of recipe the alchemist won't shut up about. Subsequent kills roll for recipe scrolls instead: 15% for an Epic recipe, 5% for a Legendary (independent rolls). World bosses skip Epic and roll 8% for Legendary only. Duplicates convert to gold (10,000g / 100,000g). See [Crafting Guide — Recipe Drops](crafting.md#recipe-drops).

**Crafting currency drops:** Raid victories roll each Ichor at 6%, Salt of Cleansing and each Portent at 4%, and the Cursed Sigil at 3% — the best rates in the game for all three tiers, and unlike dungeons they carry no difficulty gate, a raid boss being considered self-evidently endgame. World Boss kills have a 5% chance to drop a Cursed Sigil specifically and nothing else at all. See [Crafting Guide — Currencies](crafting.md#crafting-currencies).

---

## The Raid Token Vendor

Raid tokens are spent at the **Market → Raid Tokens** tab, which appears after your first raid token lands in the vault. The vendor stocks six sections — all tier-set pieces are **Ancestral** rarity (the highest gear tier, matching Heroic Dungeon drops but with set bonuses on top):

| Section | Items | Token Price |
|---------|-------|-------------|
| **Wyrmscale Regalia** (Ranger DEX set) | 5 | 8 tokens each |
| **Litany of Bones** (Rogue/Necromancer INT-DEX set) | 5 | 10 tokens each |
| **Cosmic Discord** (Mage INT set) | 5 | 12 tokens each |
| **Titanslayer Regalia** (Warrior STR set) | 5 | 8 / 8 / 10 / 10 / 12 tokens |
| **OffHand Mythics** | 3 | 10 / 12 / 14 tokens |
| **Raid Materials** | 3 | 3 / 4 / 5 tokens |

Each tier-set covers a coordinated set of slots and grants set bonuses at 2, 4, and 5 pieces. The bosses that drop the matching tokens are the bosses whose tier-set you'd most expect — the Dragon funds Wyrmscale, the Lich funds Litany of Bones, and the Void Titan funds Cosmic Discord. Titanslayer draws pieces from all three bosses (weapon and helm from Dragon, armor and accessory from Lich, sigil from Void Titan), which the Guild Clerk considers a reasonable incentive to kill everything at least once.

**Set Bonuses:**

| Set | 2-piece | 4-piece | 5-piece |
|-----|---------|---------|---------|
| Wyrmscale | +40 DEX, +30 Fire Resist | +40 Fire Damage, +8% Crit Chance | +100 Fire Resist, +200 HP, +30 DEX |
| Litany of Bones | +40 INT, +30 Dark Resist | +50 Magic Damage, +200 Mana | +25 Life Steal, +100 Dark Resist, +30 INT |
| Cosmic Discord | +40 INT, +30 Dark Resist | +50 Crit Damage, +25 Mana Regen | +40 Magic Damage, +8% Crit Chance, +75 Crit Damage |
| Titanslayer | +40 STR, +200 HP | +100 Armor, +40 Crit Damage | +60 STR, +400 HP, +10% Crit Chance, +80 Crit Damage |

---

## The Raid Interface

The raid plays out in three stages:

1. **Setup** — pick your groups, their anchor zones, their roles, and the difficulty.
2. **Board** — the tactical screen where the raid is actually fought.
3. **Results** — the aftermath, with the loot panel and a summary of who survived.

The board layout, from top to bottom: a status bar at the top, the groups roster on the left, the tactical board in the centre, the threat queue and combat log on the right, and the group chips, order panel, and keyboard legend along the bottom.

**Keyboard.** A legend along the bottom of the board lists hotkeys — **M / H / B / T / I / E** for orders, **1 / 2 / 3** for groups, **Space** to pause, **Esc** to cancel. It is a handsome legend, and a legend is all it is: the keys do nothing. Every order, group and pause is issued with the mouse. The Guild Clerk has seen signposts like this before, usually pointing at a bridge that isn't there.

A trio of view tabs in the phase header switches the central panel between **Live** (the fight as it stands), **Telegraphs** (a reference card for what the queued symbols mean), and **Storyboards** (a tactical preview of the boss's known patterns). The Telegraphs tab is worth opening every time you face a new boss; the Storyboards tab is worth opening every time you face a familiar one.

The board stage also swaps the music. You'll notice.

### The Aggro-Switch Warning

When the boss flips its target from one hero to another mid-fight, a transient banner slides in at the top of the board area — dark-red panel, ⚠ glyph, uppercase text reading **"Aggro → {hero name}"**. The banner auto-dismisses after 3 seconds, restarting the timer if another switch fires inside the window. The first time the boss locks on does not fire the banner — there is no *switch* in choosing your first victim, merely an introduction.

---

## Raid Leaderboard

Cleared raids submit to a global cloud leaderboard. The Raid tab lives inside the **Leaderboard** screen (not inside the raid view itself) — six boards stacked in a fixed order, **Dragon / Lich / Void Titan × Normal / Heroic**, each ranking the top 25 players by fewest turns (tiebreakers: lower wallclock seconds, earlier occurrence). Columns: **# · Player · Turns · Time · Survivors · Version**. Your own row is highlighted gold and tagged "(you)", so you can find yourself quickly and then wish you hadn't. Each board has **per-boss tabs and sortable columns**, and an **Attempts** column showing how many times you've launched against each boss/difficulty combo.

**Three boards, not one.** Above the table sits a row of chips — **Steam / Mobile / Web** — and the screen opens on the board *you* submit to — Steam if you're playing on Steam, Web otherwise — so you are not greeted by a stranger's list and left to wonder whether you exist. The Raid view offers only **Steam and Web**, on the sensible grounds that nobody raids from a phone and an empty Mobile raid board would be a monument to that fact rather than a ranking. Which board *you* land on is not a choice you get to make: your submission goes under Steam if Steam vouches for you, under Mobile if it doesn't and your copy of the game says it's mobile, and under Web otherwise. Verification outranks declaration — a verified player whose game insists it's mobile is still filed under Steam. Browser and beta builds are ranked among themselves, which is a different board rather than a lesser one, whatever the Guild Clerk's expression may suggest.

**Opening the screen is what puts you on it.** No cloud save is required: opening the Leaderboard signs you up if you haven't been signed up, sends in your stats, and *waits* for them to arrive before reading the board back — so your own row is there on first open rather than one refresh later. Steam builds still wait for the Steam persona to resolve before submitting anything, on the grounds that a row filed under a randomly generated name is worse than no row at all.

**Your name on the board.** A leaderboard name belongs to whoever registered it, and the rules differ by board, which is less arbitrary than it sounds. On **Steam** and **mobile** a name is taken for good and a device answers to exactly one name — try to register a claimed name and you are told, flatly, that it is claimed. The **web** board is where the beta testers live and is correspondingly forgiving: a web-only name can be registered again, so a tester whose login quietly expired gets their name back rather than losing it to themselves, and a browser that changes name takes its device along with it. A name a Steam player owns, or one with a Steam or mobile row behind it, stays locked on every board. The Guild Clerk approves of a filing system that can admit a clerical error.

**Bans.** The realm keeps a short list of players whose results it no longer believes. A banned player cannot submit, and some bans also quietly withdraw the rows already on the board — the [custom dungeon](custom-dungeons.md) leagues included. No ban stops you *reading*, so you may browse at leisure the standings you are no longer in, and no ban ever touches your cloud saves: a leaderboard problem stays a leaderboard problem. A ban that announces itself comes with an appeal address, on the reasoning that a false positive deserves somewhere to go. Lifting a ban clears it without erasing the record, because the ledger remembers everything; it is the one guild employee that never retires.

**Only victories count.** Wipes and retreats are not submitted, which is the leaderboard's one act of tact. The board keeps **one row per player, boss and difficulty**, and replaces it only when a new clear is strictly faster in turns — slower clears are quietly kept off, the leaderboard having no interest in your second-best afternoon.

**Attempts.** Every launch counts, and the tally lives in your save. This is what the Attempts column displays. Forfeits and wipes still count toward the attempts total — the column is "how many times have you stepped up to this fight," not "how many times you've cleared it."

The boards have **no time filter** (no this-week / all-time toggle); they are perpetual per-player bests.

**Plausibility.** A submission is checked for internal sense before it is believed: survivors cannot exceed the party size, a party cannot exceed **15**, and no raid can be finished faster than its own turns can physically tick. A run reporting 999,999 survivors in a single turn is therefore filed under *no* rather than under *first place*.

---

## Related Guides

- [Combat System](combat.md)
- [Heroic Dungeons](heroic-dungeons.md)
- [Abyssal Spire](tower.md)
- [Equipment & Items](equipment.md) — for the tier sets the vendor stocks
- [Custom Dungeons](custom-dungeons.md) — a different "raid" system that runs player-built dungeons

---

*"You don't beat a raid. You convince it to leave."*
