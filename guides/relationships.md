# Hero Relationships

Heroes form bonds with each other over time, because apparently you can't put people through repeated near-death experiences without them developing opinions about each other. Strong relationships improve combat performance, while rivalries can cause the sort of problems that no amount of Tavern activities will fix.

## Relationship Levels

| Level | Trust | Description |
|-------|-------|-------------|
| Devoted | +95 to +100 | Would follow into a volcano. Has probably done so. |
| Best Friend | +80 to +94 | The sort of bond that forms under repeated pressure and holds. |
| Close Friend | +60 to +79 | Will fight alongside without needing to be asked twice. |
| Friend | +30 to +59 | Know each other well enough to tell the truth occasionally. |
| Friendly | +10 to +29 | Can name each other. Some progress. |
| Neutral | -9 to +9 | Indifferent. This is the beginning, one way or the other. |
| Annoyed | -10 to -20 | A small quantity of resentment, not yet organized. |
| Dislike | -21 to -35 | Have noticed things about each other that cannot be unnoticed. |
| Rival | -36 to -55 | Actively competing. Neither takes losses gracefully. |
| Hostile | -56 to -75 | Requires active management. Or physical separation. |
| Enemy | -76 to -100 | Puts considerable effort into this. It shows in the combat stats. |

---

## Building Relationships

### Mission Events

Every mission is a social experiment as much as a combat one. Each pair of mission-mates rolls separately on a small set of independent outcomes (`SocialEventGenerator.generateMissionEvents` at `SocialEventGenerator.ts:836-928`):

| Outcome | Chance | Trust Change |
|---------|--------|--------------|
| Mission failure blame (Blame, Cowered, LeftBehind, HoardedLoot) — on a failed mission | 40% (on failure) | varies |
| Personality clash (Argument / Cowered / LeftBehind / HoardedLoot) | 25% | −2 to −6 |
| Combat bonding (FoughtBackToBack / BrilliantStrategy) — requires the mission had combat | 15% | +3 |
| Success bonding (SharedMeal / SharedLoot) — requires success | 10% | +2 |

### Social Events

| Action | Trust Change |
|--------|--------------|
| Intervene save (combat) | +30 saved / +15 saver during combat (`Combat.ts:5260-5261`) PLUS a post-mission **Saved Life** event that adds +20 saved / +15 saver (`SocialEventGenerator.ts:958-959`) — both fire on a successful intervene |
| Shared meal | +2 to +4 |
| Training together (social) | +2 to +4 |
| Gift giving | +4 to +6 |
| Celebration | +5 |
| Sparring partner | +1/day |

### Tavern Activities

| Activity | Relationship Boost |
|----------|-------------------|
| Tactical Retreat Drill | +2 per pair |
| Battle Reenactment | +3 per pair |
| Poetry Slam | +1 all pairs |
| Insurance Planning | +1 all pairs |

### Negative Events

| Event | Trust Lost |
|-------|------------|
| Romantic rejection | −6 (`SocialEventGenerator.ts:673`) |
| Jealousy | −2 (mood penalty −4 is the larger sting; `SocialEventGenerator.ts:546-547`) |
| Insult | −3 to −5 (`SocialEventGenerator.ts:541`) |
| Hogged loot | −2 to −6 (sub-variant of the personality-clash mission event; `SocialEventGenerator.ts:858-887`) |

---

## Combat Bonuses

Relationships affect combat performance in both directions. Heroes who like each other fight better; heroes who don't fight worse; and heroes who actively hate each other make the entire enterprise measurably more dangerous:

### Positive Effects

| Relationship | Damage Modifier |
|--------------|-----------------|
| Friendly | +5% |
| Friend | +10% |
| Close Friend | +15% |
| Best Friend | +20% |
| Devoted | +25% |

### Negative Effects

| Relationship | Damage Modifier |
|--------------|-----------------|
| Annoyed | -3% |
| Dislike | -8% |
| Rival | -12% |
| Hostile | -18% |
| Enemy | -25% |

### Healer Refusal

A Cleric or Paladin will not heal an ally they actively despise. Any wounded hero at **relationship value ≤ -25** (Dislike, Rival, Hostile, Enemy — mutual grievance is not required, the healer's ledger is the one that counts) is skipped:

- **Single-target heals** pick the next-most-wounded ally they *don't* hate. If every wounded ally is hated, the caster spends the turn refusing loudly (mercifully, at no cooldown cost).
- **AoE heals** exclude hated allies from the target set — the shield of holy light politely goes around them.
- **Guardian and Champion self-heal** paths are exempt, on the theory that even a bitter healer will patch themselves up rather than bleed on principle.

The reliable fix is to stop your Cleric hating people. The unreliable one is to stock a great many Bandages and hope they land on the right hero.

---

## Special Bonds

Beyond simple friendship, heroes can form special bonds — deeper entanglements with their own mechanics, bonuses, and, in some cases, spectacular failure modes:

### Lovers / Married

- **How:** High trust + romantic events
- **Bonus:** +15% combat stats together
- **Risk:** Huge penalties if partner dies (Berserk, Broken); the guild does not recommend falling in love as a combat strategy
- **Special:** +25% intervene chance modifier (`Combat.ts:5656-5660`). Not an always-trigger — the overall intervene chance still caps at 90%

### Mentor / Student

- **How:** Level gap + training together
- **Bonus:** Student learns faster; mentor shares XP — the most reliable form of productivity in the guild
- **Special:** Vengeful state if one dies

### Battle Brothers/Sisters

- **How:** Many combats survived together
- **Bonus:** +15% combat damage while the bond is active, enhanced intervene
- **Special:** Mutual protection — the kind forged by people who have seen each other at their worst and kept showing up

### Rivals

- **How:** Similar achievements, competitive traits
- **Penalty:** -15% combat damage when both are in the same party — the bond is corrosive in practice. Rivals also refuse to party together once the bond locks in.
- **Risk:** May conflict over leadership

### Life Debt

- **How:** After intervene saves life
- **Bonus:** +30% intervene chance
- **Special:** Automatic rescue attempts; the saved hero takes the concept seriously in a way that occasionally causes logistical problems

### Other Notable Bonds

Additional bonds include:

**Positive:**
- **Drinking Buddies** - Bonded over tavern sessions
- **Sparring Partners** - Regular training partners
- **Confidant** - Trusted advisor and emotional support
- **Oath Sworn** - Sworn allegiance to each other. A pair of Oath Sworn heroes assigned to the same mission grants **+5% party damage** for that mission. The bonus applies once regardless of how many Oath Sworn pairs are in the party — the realm rewards the dramatic gesture, not the inventory
- **Siblings** - Family bond

**Negative:**
- **Nemesis** - Escalated rivalry, deep personal hatred
- **Blood Feud** - Sworn enemies. Heroes in a Blood Feud bond **refuse to deploy on the same mission together** — a hard refusal that cannot be overridden, even at a mood cost. You will have to send one of them, or neither
- **Ex / Scorned** - Failed romantic relationship
- **Estranged** - Former bond broken by betrayal

---

## Story Arcs

Some relationships develop their own plotlines. When two heroes have spent enough time around each other under the right conditions, the realm proposes a **Story Arc** — a queued moral event with three branches, each of which permanently changes the bond between them.

The Guild Clerk has filed arcs as a separate category from bonds because arcs *create* bonds (or destroy them), rather than being bonds themselves. There are four arc archetypes, and only one arc can be in flight per hero at a time. The realm checks them in a fixed priority: **Romance → Mentorship → Rivalry → Honor Debt.**

### Common Rules

All arcs share:
- Both heroes must be at least **level 5**
- A per-pair **cooldown of 200 days** after any arc resolves — the realm does not allow the same two heroes to keep restarting
- Only **one arc in flight per hero** at any time
- The arc opens with a Chronicle **spark** entry, then a delayed **modal event** in Guild Events with a **3-day deadline**. The default-on-expiry varies by archetype (`arcDefinitions.ts:58,82,107,131`): Romance defaults to *Play it cool* (no change), Mentorship to *Casual* (small mood bonus), Rivalry to *Tavern* (positive resolution), and Honor Debt to *Even debt* (asymmetric LifeDebt). None of the four archetypes default to the openly negative branch on expiry
- The crisis system has the right of way: if a [crisis](crisis.md) is active, the arc step is deferred by a day

### The Four Arc Archetypes

#### Romance

**Triggers:** the pair has an Attracted bond, relationship tier ≥ Friendly, and shared combat within the last 10 days.

**Choices at the modal:**
- **Encourage** — both heroes gain the **Lovers** bond. If either was already in a Lovers or Dating relationship, it auto-upgrades to **Married**.
- **Play it cool** — nothing happens. The realm files it away. Reroll is possible after the cooldown.
- **Break it off** — both heroes gain the **Scorned** bond and take a 30-day mood penalty. The Guild Clerk recommends only doing this if you have a very good reason and a very strong sense of theatre.

#### Mentorship

**Triggers:** the two heroes share a class, the veteran is level 30+, the rookie is below level 10, and they've completed at least 2 missions together.

**Choices at the modal:**
- **Formalize** — the rookie gains the **Student** bond, the veteran gains **Mentor.** A small valor boost for both.
- **Casual** — a small mood bonus for 60 days; no bond change.
- **Dismiss** — nothing happens.

The Guild Clerk approves of Mentorship arcs more than the others, because they tend to resolve quietly and rarely involve anyone getting Scorned.

#### Rivalry

**Triggers:** the pair's relationship tier is at or below Dislike, they have at least one contested kill on record, and they've shared combat within the last 5 days.

**Choices at the modal:**
- **Tavern** — relationship value improves by 15. A drink does what years of strained professionalism could not.
- **Duel** — relationship value improves by 10, but the lower-level hero takes a **−2 STR debuff for 30 days.** The Guild Clerk regards organised duelling as "structured violence with better paperwork."
- **Fester** — both heroes gain the **Blood Feud** bond. They will refuse to deploy on the same mission until something dramatic resolves it.

#### Honor Debt

**Triggers:** one hero performed an intervene save on the other within the last 5 days — specifically, a save that would otherwise have been a kill.

**Choices at the modal:**
- **Oath** — both heroes gain the **Oath Sworn** bond (and its +5% party damage when deployed together).
- **Even debt** — the saved hero gains the **Life Debt** bond toward the saviour. Asymmetric: only the saved hero carries it.
- **Refuse** — relationship value drops by 15. The realm files this under "ingratitude."

### How You Encounter an Arc

The lifecycle plays out like this:

1. The arc **sparks** silently in the background when the conditions are met. Both heroes get a Chronicle entry; you can read about it but cannot yet act on it.
2. A few days later (3 to 7 days depending on archetype), the **modal event** appears in Guild Events. You pick one of three options.
3. The outcome resolves immediately: bonds are granted or removed, mood and stat effects apply, and a Chronicle entry is written for both heroes.
4. The per-pair 200-day cooldown begins.

If one of the heroes dies before the modal resolves, the arc is swept clean with a `relationship_arc_resolved` Chronicle entry on the survivor flagged as a permadeath resolution. The cooldown still applies.

### Where Arcs Are Tracked

Arcs surface in three places:

- **Guild Events** — the modal for the active step
- **The Chronicle** — every hero's Chronicle shows arc sparks and resolutions tagged as Social entries, with metadata fields for which archetype, which branch, and whether the arc ended in permadeath
- **Pending Consequences** — the queue of upcoming arc modals lives on the relationship arc state, and the deadline for each is visible on the event card

The Guild Clerk has, on three separate occasions, suggested adding an "Active Arcs" panel to the Social tab. The suggestion is being considered, in the way that ledger items are considered when nobody has decided who owns them.

---

## The Intervene Mechanic

When a hero would die, allies may intervene to save them — a mechanic responsible for the most dramatic moments in the guild and the most dramatic entries in the Guild Clerk's incident reports.

### Requirements

An intervene attempt requires all of the following, because goodwill alone is not enough:
- Ally has trust 30+ with target
- Ally is alive (this requirement eliminates more candidates than expected)
- Ally hasn't intervened this combat

### Intervene Chance

| Relationship | Base Chance |
|--------------|-------------|
| Friend (30-49) | 20% |
| Close Friend (50-79) | 40% |
| Best Friend (80+) | 60% |

### Modifiers

| Condition | Modifier |
|-----------|----------|
| Warrior class | +20% |
| Life Debt bond | +30% |
| Lovers/Married | +25% |
| Mentor/Battle Brother | +15% |
| Maximum | 90% |

### What Happens

1. Intervener takes 50% of the killing blow damage, further reduced by their own armor
2. Original target survives unharmed
3. Massive trust boost — the sort that tends to outlast everything else
4. Creates the kind of moment that ends up in the Combat Log and, eventually, the Tavern stories

---

## Emotional Reactions in Combat

Relationships trigger emotional states during combat — uncontrollable, unscheduled, and occasionally devastating. When someone important dies, the remaining heroes do not simply continue their turn:

### On Ally Death

| Relationship | Possible States |
|--------------|-----------------|
| Enemy | Inspired (relief) |
| Lover | Berserk, Broken, Vengeful |
| Best Friend | Berserk, Grief, Enraged |
| Close Friend | Enraged, Grief |

### Emotional States

| State | Effect | Duration |
|-------|--------|----------|
| Inspired | +15% all stats | 3 turns |
| Enraged | +30% damage, focuses on target | 2-3 turns |
| Vengeful | +20% damage vs specific enemy | 4-6 turns |
| Berserk | +50% damage, -30% defense, attacks randomly | 4-5 turns |
| Grief | -20% all stats, may refuse to heal | 2-3 turns |
| Broken | Refuses to act, cowers in fear | 4 turns |
| Panicked | May flee or cower | 2 turns |

Note: "Broken" appears as both a combat emotional state (triggered by trauma during combat) and a mood state (mood 0-9). They are separate systems.

---

## Mood System

Each hero has a mood value (0-100) that quietly applies a multiplier to everything they do. Happy heroes fight better, earn more, and complain less. Miserable heroes do the reverse — and occasionally leave:

### Mood States

Mood is a 0-100 value mapped to 6 states:

| Mood | Range | Stat Modifier |
|------|-------|---------------|
| Broken | 0-9 | -30% all stats |
| Miserable | 10-29 | -20% all stats |
| Unhappy | 30-49 | -10% all stats |
| Content | 50-69 | No modifier |
| Happy | 70-89 | +10% all stats |
| Elated | 90-100 | +20% all stats |

### Hero Needs

Heroes have four needs that affect mood:

| Need | Description | Critical Threshold |
|------|-------------|-------------------|
| Energy | Physical stamina | Below 20 |
| Social | Desire for companionship | Below 20 |
| Recreation | Need for fun/downtime | Below 20 |
| Comfort | Living conditions | Below 20 |

Needs below their critical threshold actively decrease mood.

### Affecting Mood

**Improve:** Things that remind heroes why they're here.
- Tavern activities — the Guild Clerk considers these an investment, not an expense
- Successful missions — nothing improves morale like surviving
- Good relationships — heroes who like each other perform better, and feel better about performing
- Comfortable barracks — adequate conditions are underrated until they're absent
- Chapel bonus — spiritual morale boost; the Chapel does not provide guidance on why the mission went badly

**Worsen:** Things that are harder to avoid than you'd think.
- Failed missions — the consequences compound
- Ally deaths — particularly if anyone liked the deceased
- Relationship conflicts — stress leaks into performance
- Overwork — heroes sent on back-to-back missions with no rest will eventually stop asking nicely
- Poor living conditions — the barracks complaint is the one they never stop making

---

## Mental Breaks

When mood drops critically low, heroes may have what the Guild Clerk's handbook diplomatically refers to as "an episode." Each break type has different severity and duration.

### Trigger Conditions

Mental breaks can only occur when mood drops below **30** (critical zone). The chance increases with:

| Factor | Effect on Break Chance |
|--------|----------------------|
| Base chance | 5% |
| Per day at low mood | +3% per day |
| Mood below 20 | +10% |
| Mood below 10 | +20% |
| Recently lost loved one | +15% |
| Per close friend | -2% (protective) |

Break chance is capped at 80%. Keep mood above 30 to prevent breaks entirely.

### Break Types

| Break | Duration | Weight | Effect |
|-------|----------|--------|--------|
| Desertion | Permanent | 15% | Hero leaves the guild |
| Berserk | 1 day | 10% | Attacks random allies in combat |
| Catatonic | 3-7 days | 15% | Cannot function, loses turns in combat |
| Binge | 2-4 days | 15% | Goes on a drinking spree |
| Insulting | 1-2 days | 15% | Insults other heroes, damages relationships |
| Hiding | 2-5 days | 10% | Refuses to leave quarters |
| Wandering | 1-3 days | 10% | Wanders off, unavailable |
| Confession | Instant | 10% | Blurts out a secret, one-time relationship impact |

### Combat Impact

Mental breaks affect heroes mid-combat:
- **Berserk** heroes attack a random target from a pool that includes both allies *and* enemies (`Combat.ts:6859-6941`). The damage passes through the full defensive pipeline (evasion, armor, ascendancy reduction, elemental resists, energy shield) — not "full damage" in the unmitigated sense
- **Catatonic** heroes freeze and lose their turn completely
- Other break types primarily affect availability outside of combat

### Prevention

- Keep mood above 30 — this is the absolute threshold
- Assign close friends to the same guild activities (each friend reduces break chance by 2%)
- Address low mood quickly — the chance compounds at +3% per day
- Watch for risk factors: recent loss of a loved one adds +15% break chance

---

## Social Traits

Heroes have personality traits that affect relationships. These traits are, regrettably, permanent — the guild does not offer a service for replacing personality:

### Positive Traits

| Trait | Effect |
|-------|--------|
| Friendly | +2 trust per interaction; most heroes consider this overachievement |
| Kind | Easier to form positive bonds; not everyone finds this useful |
| Brave | Combat bonuses, inspirational; the trait the Warrior has already explained to you |
| Loyal | Won't betray relationships; a lower bar than it sounds |

### Negative Traits

| Trait | Effect |
|-------|--------|
| Antisocial | -1 trust per interaction; they are not trying, and it shows |
| Jealous | May sabotage rivals; productive only from a very specific angle |
| Coward | May flee, lower morale; consistent at least |
| Cruel | Others dislike them; they consider this neutral information |

### Neutral Traits

| Trait | Effect |
|-------|--------|
| Romantic | More likely to form couples; this goes well until it doesn't |
| Competitive | Forms rivalries easily; also the source of the +10% rival bonus, which is cold comfort |
| Independent | Fewer social interactions; harder to build bonds, easier to avoid drama |

---

## Equipment Attachment

Heroes develop emotional bonds with their equipment over time. The longer they wear something, the less enthusiastic they'll be about giving it up. This is, from a management perspective, inconvenient.

### Attachment Levels

| Level | Time Required | Rarity Shortcut | Mood on Removal | Mood While Worn |
|-------|--------------|----------------|----------------|----------------|
| None | < 3 days | — | 0 | 0 |
| Comfortable | 3+ days | Rare+ | -5 | 0 |
| Favorite | 14+ days | Epic+ | -10 | +3 |
| Prized | 30+ days | Legendary | -20 | +5 |
| Soulbound | Sentimental only | — | *N/A* | +8 |

Attachment builds through two paths: **time equipped** and **item rarity**. A Legendary weapon is instantly Prized; an Epic item starts as a Favorite. The highest of the two paths wins.

### Sentimental Items

Some items become Soulbound through events rather than time:

- **Gift** — received from a romantic partner or close friend
- **Memorial** — belonged to a fallen guild member
- **First Kill** — used to slay a significant boss
- **Saved Life** — the hero survived a near-death thanks to this item
- **Family Heirloom** — brought from their background

Soulbound items cannot be removed at all — the Vault's confirmation dialog offers a Close button where the Unequip button used to be, and the hero declines to elaborate. The bond only ends when the item is destroyed or the hero is. This is not a mood penalty you can pay through; it is simply not on the menu.

Prized and Soulbound items are also skipped by the auto-equip pass, so a shinier drop won't quietly displace either from a hero who's grown fond of what they've got.

### Trait Effects

- **Greedy** heroes attach at 2× speed (`equipment.ts:204`). Effective days are doubled, so an item reaches **Prized at 15 actual days** (effectiveDays ≥ 30 per `ATTACHMENT_THRESHOLDS[Prized] = 30`). 14 actual days still lands at Favorite (effectiveDays 28, below the 30 threshold)
- **Ascetic** heroes never form attachments — swap their gear freely

### Removal Mood Effects

Removing a Favorite or higher item causes a lingering mood penalty:

| Lost Level | Mood Penalty | Duration |
|-----------|-------------|---------|
| Favorite | -8 | 3 days |
| Prized | -12 | 5 days |
| Soulbound | *cannot be removed* | — |

Heroes also complain about equipment they find aesthetically displeasing (-5 mood while worn).

---

## Alcohol & Addiction

The Tavern serves drinks. Heroes drink them. Sometimes, they drink too many of them. The game tracks intoxication, tolerance, addiction, and hangovers with the kind of detail that suggests the developers have Opinions about pub culture.

### Drunk Levels

Intoxication is tracked on a 0-100 scale:

| Level | Range | Can Mission? | Social | Accuracy | Description |
|-------|-------|-------------|--------|----------|-------------|
| Sober | 0-20 | Yes | +0 | +0 | Clear-headed |
| Tipsy | 21-40 | Yes | +10 | -5 | Pleasantly relaxed |
| Drunk | 41-60 | Yes | +15 | -15 | Confident, poor judgement |
| Hammered | 61-80 | **No** | +5 | -40 | Trouble with basic motor functions |
| Blackout | 81-100 | **No** | -20 | -80 | Will remember nothing tomorrow |

Heroes who are Hammered or Blacked Out cannot be sent on missions. A Tipsy hero has better social interactions but slightly worse aim — a trade-off the game considers fair.

The Accuracy column is not decorative. It applies as a **miss chance on basic attacks** — a Drunk hero's swings fail 15% of the time, a Hammered one 40%. Skills, spells, and gem-driven attacks land as normal, because muscle memory is apparently more waterproof than motor control. Hangover accuracy penalties and withdrawal shakes stack into the same roll, which is how a hero with a bad night behind them and worse plans ahead of them can miss a stationary goblin.

### Drinks

| Drink | Intoxication | Addiction Risk | Price | Notes |
|-------|-------------|---------------|-------|-------|
| Tavern Ale | +10 | 2 | 2g | Reliable, affordable |
| Honey Mead | +12 | 2 | 4g | Sweet enough to trick you |
| House Wine | +15 | 3 | 5g | Supposedly from grapes |
| Dwarven Stout | +25 | 5 | 8g | Could dissolve a spoon |
| The Mystery Special | +35 | 8 | 10g | Contents unknown |
| Lord's Brandy | +30 | 6 | 15g | Drunk and pretentious |
| Goblin's Regret | +50 | 12 | 20g | Named for the inventor's last words |

### Tolerance

Tolerance builds with drinking — higher tolerance means it takes more to get drunk, but also produces worse hangovers:

| Level | Effect |
|-------|--------|
| Lightweight | Gets drunk easily, clears fast |
| Normal | Standard processing |
| Seasoned | Takes more to get drunk, longer hangovers |
| Ironclad | Legendary tolerance, massive hangovers |

### Hangovers

The morning after. Hangovers affect mood, accuracy, energy, and — at higher levels — may cause vomiting in combat.

| Level | Mood | Accuracy | Energy Drain | Vomit Risk |
|-------|------|----------|-------------|-----------|
| Mild | -3 | -5 | -10 | 0% |
| Moderate | -8 | -15 | -25 | 5% |
| Severe | -15 | -25 | -40 | 20% |
| Death's Embrace | -25 | -40 | -60 | 50% |

### Addiction

Repeated drinking builds addiction (0-100 scale). Without alcohol, addicted heroes suffer withdrawal:

| Level | Mood Penalty | Shakes (Accuracy) | Days to Recover | Mission Refusal Chance |
|-------|-------------|-------------------|----------------|----------------------|
| Dabbler | -2 | 0 | 3 | 0% |
| Regular | -5 | -5 | 7 | 5% |
| Heavy | -12 | -15 | 14 | 15% |
| Addicted | -25 | -30 | 30 | 40% |

Recovery requires going without drinks for the listed number of days. An Addicted hero needs a full month of sobriety — during which they'll be miserable, shaking, and may refuse to work 40% of the time.

### Blackout Events

Heroes who reach Blackout may experience random events they won't remember: losing gold, gaining or losing items, forming unexpected bonds, or doing things they'll later be embarrassed about. The details are revealed the next morning.

---

## Unavailability & Refusal

Heroes are not, despite what the roster screen implies, available at all times. They have personal lives, grudges, hangovers, and occasional existential crises. The game tracks three systems: **unavailability** (can't go), **refusal** (won't go), and **insistence** (determined to go whether you like it or not).

### Unavailability

A hero may be temporarily unavailable for social or personal reasons. Some can be overridden by the Guild Master — at a mood cost.

| Reason | Description |
|--------|-------------|
| Personal Day | Needs a day off. For reasons. |
| Romantic Escape | Gone off with their partner |
| Sulking | After a rejection, breakup, or insult |
| Hangover | Drank too much last night |
| Bender | Extended drinking episode (addiction-related) |
| Pilgrimage | Religious observance |
| Mourning | Lost someone close |
| Family Business | Vague "family matters" |
| Runaway | Temporarily left the guild |
| Mental Health | Recovering from trauma |

Forcing an unavailable hero onto a mission (when overridable) incurs a mood penalty. Some reasons — like Mourning or Mental Health — cannot be overridden at all.

### Mission Refusal

Even available heroes may refuse specific missions:

| Reason | Trigger | Severity |
|--------|---------|----------|
| Rival Conflict | Rival is on the team | Soft |
| Ex Conflict | Ex-partner is on the team | Soft |
| Enemy Conflict | Someone they hate is assigned | Hard |
| Too Exhausted | Energy critically low | Soft |
| Too Drunk | Currently intoxicated | Hard |
| Location Trauma | Bad memories of this dungeon type | Hard |
| Coward + Danger | Coward trait facing high-difficulty mission | Soft |
| Mourning | Still grieving | Hard |
| Low Mood | Mood too low to function | Soft |
| Equipment Missing | Favourite or required gear unavailable | Soft |

**Soft** refusals can be overridden with a mood penalty. **Hard** refusals cannot — the hero simply will not go.

### Location Trauma

Heroes who experience traumatic events in specific dungeon types (a party wipe in Crypts, a near-death in Caves) develop location trauma. They will refuse missions to those dungeon types until the trauma fades. Trauma has a severity scale of 1-10, with higher severity meaning longer recovery.

### Insistence

The opposite of refusal — sometimes heroes *insist* on joining a mission, and removing them costs mood:

| Reason | Trigger |
|--------|---------|
| Vendetta | Enemy killed their friend |
| Protective | Partner or best friend is assigned |
| Best Friend in Danger | Best friend is going |
| Prove Themselves | Recent humiliation, wants glory |
| Revenge | Personal grudge against enemy type |
| Rival Showing | Rival is going — must outshine them |
| Favourite Activity | Mission type they enjoy |
| Treasure Hunter | High-loot mission + Greedy trait |

An insistent hero removed from the party suffers a mood penalty. Sometimes it's easier to just let them come.

---

## Hero Social Events

Beyond the Tonight tab and the tavern's background chaos, heroes generate a third layer of social activity: **ambient social events** that fire automatically between themselves, without any interface, any tab, or any prompting on your part.

These events appear in the social feed. They cost you nothing. They cannot be prevented. The relationship scores you built — or didn't build — are the only variable.

Events are sorted into four groups:

### Positive (Ambient Bonding)

| Event | What It Does |
|-------|-------------|
| Good Conversation | Two heroes talk and discover compatibility, which is rarer than it sounds. Relationship and mood both improve. |
| Shared Meal | Heroes eat together. It's difficult to genuinely dislike someone who shares your bread. This does not always stop them. Modest mood and relationship improvement. |
| Gift Giving | One hero gives another a gift. The recipient is touched regardless of the giver's motives, which the game charitably does not investigate. Significant relationship gain. |
| Training Together | Heroes compete without actively trying to harm each other, which turns out to be good for the relationship. Small mood boost, meaningful relationship gain. |
| Saved by Ally | A hero reflects on being pulled out of a bad situation by someone who didn't have to. The resulting relationship gain is large and tends to stick. |
| Romantic Confession | An Attracted hero says what they've been thinking. The outcome depends entirely on what the target has been thinking, which is not information the game provides in advance. |
| Celebration | A hero has something worth celebrating and shares it with whoever's nearby. Mood and relationship boost for participants. |
| Mentorship Offer | A veteran offers to help a junior hero improve — voluntarily, without being asked. Relationship benefit for both; the junior feels seen, the veteran feels useful. |
| Oath of Friendship | Two heroes who have spent enough time together make it formal. May trigger a Best Friends bond. |

### Negative (Ambient Conflict)

| Event | What It Does |
|-------|-------------|
| Argument | Heroes disagree and neither backs down. Relationship hit and mood hit for both — the twin costs of being right and winning nothing. |
| Insult | One hero says something about another that they may or may not have meant. The target treats it as intentional either way. Relationship damage varies with severity. |
| Theft | A hero takes something that wasn't offered. Greedy trait makes this more likely. Trust takes the damage, and trust is slow to rebuild. |
| Fight | Words escalated past their natural limit. Relationship damage, potential mood effects, possible injury. |
| Blame | A hero nominates someone else to be responsible for a failure. The nominee notices. Relationship damage follows. |
| Jealousy | A hero finds another's success or relationships difficult to tolerate and makes this apparent. Relationship hit for everyone involved. |
| Romantic Rejection | A confession the target wasn't ready to hear. The relationship takes a significant hit — this outcome is, statistically, more common than it should be. |
| Rumor Spreading | A hero shares information about another hero that wasn't theirs to share. The subject suffers for it; the wider social fabric suffers more quietly. |
| Betrayal | A hero does something to another that cannot be explained as an accident or misunderstanding. Large relationship damage. Bonds do not survive this easily. |

### Mission-Based (Post-Dungeon Reactions)

These fire after dungeon runs based on what happened in the field. The dungeon ends; the accounting begins.

| Event | What It Does |
|-------|---------|
| Saved Life | A hero pulled another back from the edge. The relationship gain is large — the kind that tends to persist through subsequent arguments. |
| Fought Back to Back | Heroes who relied on each other throughout come out of it closer. Sustained mutual dependence is good for trust. |
| Cowered | A hero failed to act when action was needed. The heroes who noticed this do not forget. Relationship drops with those who witnessed it. |
| Left Behind | A hero was put in a dangerous position by another's choice. The resulting resentment is proportional to how bad it got. |
| Shared Loot | Heroes divided rewards fairly. Small positive relationship signal — the baseline decent behavior that tends to be taken for granted until it stops happening. |
| Hoarded Loot | A hero kept more than their share. The others notice. Relationship damage with the rest of the party. |
| Blamed for Trap | A hero is held responsible for a trap that caught someone. Fair or not, the accused takes a relationship hit with whoever was caught. |
| Brilliant Strategy | A hero's thinking turned the fight. The rest of the party is prepared to acknowledge this. Mood and relationship boost. |

Mission-based events are among the most powerful relationship movers in the game. Getting saved tends to create lasting gratitude. Getting left behind tends to create lasting resentment.

### Tavern (Social Context)

| Event | What It Does |
|-------|-------------|
| Tavern Drinking | Heroes drink together. Conversation gets easier as the evening progresses. Relationship improves; drunk levels rise as a natural consequence. |
| Tavern Gambling | Heroes gamble together. The relationship effects depend on the outcome — shared loss is more bonding than it has any right to be, but winning at someone's expense is not. |
| Tavern Feast | Heroes share a proper meal together rather than eating alone. Mood and relationship improve for participants. |
| Secret Shared | One hero tells another something they've told no one else. Whether this was wisdom or alcohol is not recorded. The relationship gain is significant either way. |

Social events are logged with the hero's name and a description. The logs don't go away — if you want to understand why two heroes have the relationship they have, the social feed is the record.

---

## Keepsakes

Heroes accumulate sentimental mementos — non-item tokens stored on their social data (`HeroSocial.ts`). A keepsake is not equipment; it cannot be traded, sold, or dropped. It sits in the hero's record and applies a small permanent bonus, which is the game's way of saying that sentiment has mechanical weight.

### How Keepsakes Are Acquired

| Source | Trigger | Cooldown |
|--------|---------|----------|
| **Gift** | A Gift Giving social event fires between two bonded heroes | 100 days per giver–receiver pair |
| **Heirloom** | 10% chance at recruit time, drawn from the hero's background pool | Once (at recruitment) |
| **Memorial** | A hero dies; their closest surviving guild-mate receives a memento | On death of any hero with bonds |

Gift names are drawn from per-class pools — Warriors give battle-worn hilts and campaign coins; Mages give rune-etched pebbles and crystallised mana shards; Rogues give trick coins and marked playing cards. Heirloom names depend on background. Memorial keepsakes are named "Memento of {fallen hero}" and carry a mood-floor bonus.

### Keepsake Bonuses

Each keepsake carries exactly one bonus from a discriminated union (`KeepsakeBonus` in `HeroSocial.ts`):

| Kind | Effect | Example |
|------|--------|---------|
| `mood_floor` | Permanent mood modifier (adds to mood baseline) | +3 mood floor |
| `combat` | Percent bonus to crit chance, dodge, or life steal | +3% crit chance |
| `resist` | Percent resistance to a damage type (fire, cold, lightning, or general) | +5% fire resist |

Bonuses are applied as buffs via `applyKeepsakeBonus` (`GameState.ts:118`) — combat and resist bonuses become `BuffSource.Keepsake` entries visible in the hero's Active Effects panel; mood-floor bonuses are applied as long-lived mood modifiers on the social system.

### Limits

There is no cap on the number of keepsakes a hero can hold. A hero who lives long enough and maintains strong bonds will accumulate several — each one small, but collectively meaningful. The Guild Clerk finds this thematically appropriate: sentiment accrues.

---

## Managing Relationships

### Tips

1. **Party together** - Bonds form in combat; put people through the same danger and they'll form opinions about each other, which eventually become opinions about each other
2. **Watch for conflicts** - Separate enemies before the situation resolves itself through violence
3. **Use the Tavern** - Shared activities build trust; it's cheaper than the alternative
4. **Check compatibility** - Trait conflicts erode trust passively, even when nothing specific goes wrong
5. **Leverage bonds** - Best friends fighting together apply their relationship bonus simultaneously; plan accordingly

### Warning Signs

- Multiple heroes dislike the same person — at some point this becomes a consensus
- Trust declining rapidly without obvious cause — check the social log
- Mood consistently poor — the performance penalty compounds
- Conflicts triggering in combat — the worst possible time to discover someone has enemies

### Building Dream Teams

The goal is a roster where people fight better together than they do alone — which requires treating the social feed as seriously as the stat sheet:

1. Start with compatible traits — Antisocial and Jealous heroes require more management than they're worth in most party compositions
2. Run missions together consistently — bonds form through sustained shared experience, not single events
3. Use Tavern activities — the nightly routines quietly accumulate trust at no cost except the time
4. Let relationships form naturally — manufactured bonds are weaker than earned ones
5. Don't force incompatible pairs — some heroes simply will not get along, and a party's performance suffers if two of its members are at -50 trust

---

## Related Guides

- [Combat System](combat.md) - Emotional states and intervene
- [Guild Management](guild.md) - Mood and facilities
- [Heroes & Classes](heroes.md) - Traits and states

---

*"The bonds between heroes matter more than their individual strength — which is fortunate, because their individual judgment is often questionable."*
