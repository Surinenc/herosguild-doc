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

When mood drops critically low, heroes may have what the Guild Clerk's handbook diplomatically refers to as "an episode":

| Break | Effect | Recovery |
|-------|--------|----------|
| Tantrum | May damage property | 1 day |
| Hiding | Won't work | 2 days |
| Berserk | May fight allies | Until calmed |
| Catatonic | Cannot function | 3+ days |
| Breakdown | Leaves guild | Permanent |

**Prevention:** Keep mood above "Poor"!

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
