# Hero Relationships

Heroes form bonds with each other over time, because apparently you can't put people through repeated near-death experiences without them developing opinions about each other. Strong relationships improve combat performance, while rivalries can cause the sort of problems that no amount of Tavern activities will fix.

## Relationship Levels

| Level | Trust | Description |
|-------|-------|-------------|
| Devoted | +95 to +100 | Unbreakable loyalty |
| Best Friend | +80 to +94 | Deep bond |
| Close Friend | +60 to +79 | Trust each other |
| Friend | +30 to +59 | Comfortable together |
| Friendly | +10 to +29 | Know each other |
| Neutral | -9 to +9 | Just met |
| Annoyed | -10 to -20 | Mild friction |
| Dislike | -21 to -35 | Growing tension |
| Rival | -36 to -55 | Competition |
| Hostile | -56 to -75 | Active antagonism |
| Enemy | -76 to -100 | Hatred |

---

## Building Relationships

### Mission Events (30% Chance per Pair)

Each hero pair has a 30% chance of a relationship event during missions:

| Event Type | Trust Change |
|------------|--------------|
| Fought well together | +3 |
| Covered each other | +5 |
| Worked as a team | +6 |
| Argued over tactics | -3 |
| Blamed for close call | -5 |
| Took credit for kill | -4 |

### Social Events

| Action | Trust Change |
|--------|--------------|
| Intervene save (combat) | +30 saved / +15 saver |
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
| Romantic rejection | -10 |
| Jealousy attack | -25 to -30 |
| Insult | -6 |
| Hogged loot | -4 |

---

## Combat Bonuses

Relationships affect combat performance:

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

---

## Special Bonds

Beyond simple friendship, heroes can form special bonds:

### Lovers / Married

- **How:** High trust + romantic events
- **Bonus:** +15% combat stats together
- **Risk:** Huge penalties if partner dies (Berserk, Broken)
- **Special:** Will always try to intervene

### Mentor / Student

- **How:** Level gap + training together
- **Bonus:** Student learns faster, mentor shares XP
- **Special:** Vengeful state if one dies

### Battle Brothers/Sisters

- **How:** Many combats survived together
- **Bonus:** +15% when adjacent, enhanced intervene
- **Special:** Mutual protection

### Rivals

- **How:** Similar achievements, competitive traits
- **Bonus:** +10% when competing
- **Risk:** May conflict over leadership

### Life Debt

- **How:** After intervene saves life
- **Bonus:** +30% intervene chance
- **Special:** Automatic rescue attempts

### Other Notable Bonds

The game tracks 28 bond types total. Additional important bonds include:

**Positive:**
- **Drinking Buddies** - Bonded over tavern sessions
- **Sparring Partners** - Regular training partners
- **Confidant** - Trusted advisor and emotional support
- **Oath Sworn** - Sworn allegiance to each other
- **Siblings** - Family bond

**Negative:**
- **Nemesis** - Escalated rivalry, deep personal hatred
- **Blood Feud** - Generational or oath-bound enmity
- **Ex / Scorned** - Failed romantic relationship
- **Estranged** - Former bond broken by betrayal

---

## The Intervene Mechanic

When a hero would die, allies may intervene to save them.

### Requirements

- Ally has trust 30+ with target
- Ally is alive
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

1. Intervener takes 50% of killing blow damage
2. Original target survives unharmed
3. Massive trust boost
4. Creates memorable moment

---

## Emotional Reactions in Combat

Relationships trigger emotional states:

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

Each hero has mood that affects performance:

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
| Comfort | Living conditions | Below 80 |

Needs below their critical threshold actively decrease mood.

### Affecting Mood

**Improve:**
- Tavern activities
- Successful missions
- Good relationships
- Comfortable barracks
- Chapel bonus

**Worsen:**
- Failed missions
- Ally deaths
- Relationship conflicts
- Overwork
- Poor living conditions

---

## Mental Breaks

When mood drops critically low, heroes may have what the Guild Clerk's handbook diplomatically refers to as "an episode." The game tracks 8 break types, each with different severity and duration.

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
- **Berserk** heroes attack random allies for full damage
- **Catatonic** heroes freeze and lose their turn completely
- Other break types primarily affect availability outside of combat

### Prevention

- Keep mood above 30 — this is the absolute threshold
- Assign close friends to the same guild activities (each friend reduces break chance by 2%)
- Address low mood quickly — the chance compounds at +3% per day
- Watch for risk factors: recent loss of a loved one adds +15% break chance

---

## Social Traits

Heroes have personality traits affecting relationships. These traits are, regrettably, permanent:

### Positive Traits

| Trait | Effect |
|-------|--------|
| Friendly | +2 trust per interaction |
| Kind | Easier to form positive bonds |
| Brave | Combat bonuses, inspirational |
| Loyal | Won't betray relationships |

### Negative Traits

| Trait | Effect |
|-------|--------|
| Antisocial | -1 trust per interaction |
| Jealous | May sabotage rivals |
| Coward | May flee, lower morale |
| Cruel | Others dislike them |

### Neutral Traits

| Trait | Effect |
|-------|--------|
| Romantic | More likely to form couples |
| Competitive | Forms rivalries easily |
| Independent | Fewer social interactions |

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
| Soulbound | Sentimental only | — | -35 | +8 |

Attachment builds through two paths: **time equipped** and **item rarity**. A Legendary weapon is instantly Prized; an Epic item starts as a Favorite. The highest of the two paths wins.

### Sentimental Items

Some items become Soulbound through events rather than time:

- **Gift** — received from a romantic partner or close friend
- **Memorial** — belonged to a fallen guild member
- **First Kill** — used to slay a significant boss
- **Saved Life** — the hero survived a near-death thanks to this item
- **Family Heirloom** — brought from their background

Soulbound items cannot be removed without severe mood penalties (-35). Heroes will actively resist, and their complaints about it will be memorable.

### Trait Effects

- **Greedy** heroes attach at 2x speed (14 days = Prized instead of Favorite)
- **Ascetic** heroes never form attachments — swap their gear freely

### Removal Mood Effects

Removing a Favorite or higher item causes a lingering mood penalty:

| Lost Level | Mood Penalty | Duration |
|-----------|-------------|---------|
| Favorite | -8 | 3 days |
| Prized | -12 | 5 days |
| Soulbound | -35 (immediate) | — |

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

There are 30+ event types sorted into four groups:

### Positive (Ambient Bonding)

| Event | What It Does |
|-------|-------------|
| Good Conversation | Two heroes talk; relationship and mood both improve modestly |
| Shared Meal | Heroes eat together; small mood boost and relationship improvement |
| Gift Giving | One hero gives another a gift; significant relationship gain for recipient |
| Training Together | Heroes spar or train; relationship improves, small mood boost |
| Saved by Ally | Dungeon callback: a hero acknowledges being saved; large relationship gain |
| Romantic Confession | An Attracted hero confesses feelings; relationship outcome depends on the target |
| Celebration | Hero celebrates something good; mood and relationship boost for those nearby |
| Mentorship Offer | Veteran offers to mentor a junior hero; relationship benefit for both |
| Oath of Friendship | Two high-relationship heroes formalise their bond; may trigger a Best Friends bond |

### Negative (Ambient Conflict)

| Event | What It Does |
|-------|-------------|
| Argument | Heroes disagree; relationship hit, mood hit for both |
| Insult | One hero insults another; relationship damage based on severity |
| Theft | A hero steals from another (Greedy trait relevant); trust hit, relationship down |
| Fight | Physical altercation; relationship damage, possible mood and injury effects |
| Blame | A hero blames another for a failure; relationship damage |
| Jealousy | A hero acts on jealousy over another's success or relationship; relationship hit |
| Romantic Rejection | A confession that doesn't go well; significant relationship hit for the confessor |
| Rumor Spreading | A hero spreads gossip; relationship damage for the subject, possible wider effects |
| Betrayal | A serious breach of trust; large relationship damage, potential bond dissolution |

### Mission-Based (Post-Dungeon Reactions)

These fire after dungeon runs based on what happened in the field:

| Event | Trigger |
|-------|---------|
| Saved Life | A hero saved another's life during the mission |
| Fought Back to Back | Heroes fought alongside each other throughout |
| Cowered | A hero failed to engage when allies needed help |
| Left Behind | A hero was left in a difficult position by another |
| Shared Loot | Heroes split loot fairly |
| Hoarded Loot | A hero kept more than their share |
| Blamed for Trap | A hero is blamed for walking into a trap |
| Brilliant Strategy | A hero's tactic turned the fight |

Mission-based events are among the most powerful relationship movers in the game. Getting saved tends to create lasting gratitude. Getting left behind tends to create lasting resentment.

### Tavern (Social Context)

| Event | What It Does |
|-------|-------------|
| Tavern Drinking | Heroes drink together; relationship improvement, drunk level rises |
| Tavern Gambling | Heroes gamble together; outcome-dependent relationship and mood effects |
| Tavern Feast | Heroes share a meal at the tavern; mood and relationship boost for participants |
| Secret Shared | One hero confides something private in another; significant relationship gain |

Social events are logged with the hero's name and a description. The logs don't go away — if you want to understand why two heroes have the relationship they have, the social feed is the record.

---

## Managing Relationships

### Tips

1. **Party together** - Bonds form in combat
2. **Watch for conflicts** - Separate enemies
3. **Use the Tavern** - Shared activities build trust
4. **Check compatibility** - Trait conflicts hurt
5. **Leverage bonds** - Best friends excel together

### Warning Signs

- Multiple heroes dislike someone
- Trust declining rapidly
- Mood consistently poor
- Conflicts in combat

### Building Dream Teams

1. Start with compatible traits
2. Run missions together consistently
3. Use Tavern activities
4. Let relationships form naturally
5. Don't force incompatible pairs

---

## Related Guides

- [Combat System](combat.md) - Emotional states and intervene
- [Guild Management](guild.md) - Mood and facilities
- [Heroes & Classes](heroes.md) - Traits and states

---

*"The bonds between heroes matter more than their individual strength — which is fortunate, because their individual judgment is often questionable."*
