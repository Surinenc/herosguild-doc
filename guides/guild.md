# Guild Management

Your guild is your home base — a collection of buildings, debts, and strong opinions held by people who hit things for a living. Manage facilities, finances, reputation, and your roster of heroes to build something that future historians will either celebrate or use as a cautionary tale.

## Guild Facilities

14 facilities to build and upgrade:

### Core Facilities

| Facility | Function | Max Level |
|----------|----------|-----------|
| **Guild Hall** | Central hub, determines mission slots | 5 |
| **Barracks** | Hero housing, rest, mood | 5 |
| **Tavern** | Recruitment, morale, social | 5 |
| **Training Yard** | Skill training, sparring | 5 |
| **Infirmary** | Injury treatment | 5 |
| **Armory** | Equipment storage | 6 |
| **Warehouse** | Material & gold storage | 6 |
| **Shop** | Sell items to customers | 5 |

### Production Facilities

| Facility | Function | Max Level |
|----------|----------|-----------|
| **Forge** | Metal weapons/armor | 5 |
| **Workshop** | Leather, cloth, wood | 6 |
| **Alchemy Lab** | Potions & elixirs | 5 |
| **Enchanting Table** | Magic enhancement | 5 |

### Support Facilities

| Facility | Function | Max Level |
|----------|----------|-----------|
| **Library** | Research & recipes | 5 |
| **Chapel** | Morale, blessings, funerals | 3 |

---

## Facility Details

### Guild Hall

Your central building. The notice board here has seen more drama than most theaters. Determines mission slots (hero capacity is set by Barracks).

| Level | Name | Mission Slots | Daily Upkeep |
|-------|------|---------------|--------------|
| 1 | Modest Hall | 2 | 5g |
| 2 | Expanded Hall | 4 | 25g |
| 3 | Grand Hall | 6 | 50g |
| 4 | Manor Hall | 8 (+1 contract) | 1,500g |
| 5 | Legendary Hall | 10 (+2 contracts) | 4,000g |

### Barracks

Hero housing affects mood and rest recovery. The beds have witnessed more reconciliations than any chapel.

| Level | Beds | Mood | Rest Speed | Daily Upkeep |
|-------|------|------|------------|--------------|
| 1 | 12 | -10% | 0.9x | 2g |
| 2 | 20 | -5% | 0.95x | 12g |
| 3 | 30 | +0% | 1.0x | 20g |
| 4 | 45 | +5% | 1.05x | 800g |
| 5 | 60 | +10% | 1.1x | 2,000g |

### Tavern

Recruitment hub, morale booster, and the place where most guild drama begins (and occasionally ends, depending on how the gambling goes).

| Level | Name | Recruits/Day | Daily Income | Daily Upkeep |
|-------|------|--------------|--------------|--------------|
| 1 | Rustic Tavern | 1 | 300g | 3g |
| 2 | Cozy Tavern | 1-2 | 1,000g | 15g |
| 3 | Popular Tavern | 1-3 | 3,000g | 30g |
| 4 | Renowned Tavern | 2-4 | 8,000g | 800g |
| 5 | Legendary Tavern | 3-5 | 20,000g | 1,500g |

**Tavern Activities:**

| Activity | Cost | Mood Effect | Cooldown |
|----------|------|-------------|----------|
| Buy Rounds | 50g | +3 mood | 1 day |
| Grand Feast | 200g | +10 mood | 3 days |
| Gambling | Variable | +5 (win) / -3 (loss) | None |
| Bard Night | 100g | +8 mood | 3 days |

#### Nightly Decisions (Tavern Decision Engine)

Each night, the Tavern presents 6-8 situations requiring your attention — heroes in conflict, milestones to celebrate, gossip to manage, or romances to encourage. These appear in the **Tonight** tab (the Tavern screen has two tabs: **Tavern** for recruitment and activities, and **Tonight** for nightly decisions). You spend **Attention Points** to address them. Ignoring certain situations carries penalties, because problems left unsupervised in a room full of alcohol tend to get worse. Note: there is no history log for tavern decisions — once the night passes, the outcomes are final and unrecorded.

**Attention Points per Night:**

| Tavern Level | Points |
|-------------|--------|
| 1-2 | 3 |
| 3-4 | 4 |
| 5+ | 5 |

Each decision costs 1-2 points. You won't have enough to address everything — prioritisation is the point.

**Decision Types:**

| Decision | Cost | Trigger | Outcome (Success) | Skip Penalty |
|----------|------|---------|-------------------|-------------|
| Counsel Hero | 2 | Hero mood < 35 or social need < 40 | +6 mood | -3 mood |
| Mediate Conflict | 2 | Two heroes are rivals or worse | +3 mood each, +5 relationship | -3 relationship |
| Break Up Fight | 2 | Rivals with relationship < -50 | +3 relationship | -3 relationship |
| Calm Volatile | 2 | Volatile hero with mood < 40 | +5 mood | -4 mood |
| Comfort Injured | 2 | Hero recovering from injuries | +6 mood, -1 day recovery | -2 mood |
| Mentor Session | 2 | Veteran (50+) and rookie (< 20) present | XP for student, +3 mood for mentor | None |
| Host Feast | 2 | Gold available | +5 mood (all heroes) | None |
| Celebrate Achievement | 1 | Hero reached a milestone | +8 mood (hero), -2 mood (jealous heroes) | None |
| Toast Success | 1 | Recent mission victory | +4 mood, +2 relationship (all) | -2 mood |
| Encourage Romance | 1 | Attracted or dating heroes | +8 relationship | -2 relationship |
| Celebrate Romance | 1 | Lovers/married with recent milestone | +5 mood, +5 relationship | -2 mood |
| Welcome Recruit | 1 | Hero joined < 7 days ago | +5 mood, +2 relationship (all) | -3 mood |
| Drinking Buddy | 1 | Two drinking buddies present | +3 mood, +4 relationship | None |
| Training Partners | 1 | Two heroes both training | +2 mood, +5 training progress | None |
| Address Gossip | 1 | Hero with Gossip trait | Gossip stopped, -1 mood (reprimand) | -3 random relationship |
| Share Loot | 1 | Guild has > 5,000g (costs 500g) | +3 mood (all heroes) | None |
| Tell War Stories | 1 | Always available | +10 XP for low-level heroes | None |
| Eavesdrop | 1 | Always available | Reveals social intel | None |

**Cooldowns:** Each specific hero-situation combination has a 3-night cooldown, so you won't see the same problem with the same heroes every night — just similar problems with different heroes.

#### Tavern Background Events

While you're busy spending Attention Points on the Tonight tab, the rest of the tavern is busy running itself. **Background events** fire automatically whenever heroes are gathered — they don't ask for your approval, spend your points, or warn you in advance. They simply happen, get logged in the social feed, and leave consequences for you to manage in the morning.

**Positive**

| Event | What Happens |
|-------|-------------|
| Impromptu Party | Someone decides the evening calls for celebration. It might not, but no one argues. Mood up for everyone present. |
| Drinking Contest | Heroes compete, because heroes always compete. Winner gets a mood boost; loser gets a hangover and a valuable lesson about pride. |
| Bardic Performance | A bard performs. Heroes who didn't ask for music enjoy it anyway. Mood boost for all. |
| Heart to Heart | Two heroes have an honest conversation, possibly by accident. Relationship improves significantly. |
| Lucky Streak | The dice go the right way for once. Gold gained, mood up, briefly inflated confidence about gambling in general. |
| Toast to the Fallen | Heroes raise a glass to someone no longer with them. Shared grief, and the modest mood boost that comes from not grieving alone. |

**Negative**

| Event | What Happens |
|-------|-------------|
| Bar Fight | At some point, words were insufficient. Injuries possible, relationships damaged, furniture probably not improved. |
| Drunk Confession | A hero says something they've been keeping to themselves. The relationship outcome depends on what it was, which the game knows and is not telling you in advance. |
| Gambling Loss | The dice did not cooperate. Gold lost, mood down, and a renewed conviction that next time will be different. |
| Jealous Outburst | A hero makes their feelings about someone else's success loudly clear. Relationship hit for those involved; dignity hit for the outburst-haver. |
| Vomit Incident | This happened. Mood penalty for the hero; additional penalty for everyone who witnessed it. |
| Broken Heirloom | Something irreplaceable met an avoidable end. Mood penalty plus a grief thought that will linger for days. |
| Drunken Insult | A hero says what they actually think of someone. The damage scales, with uncomfortable accuracy, with how true it was. |
| Cheating Accusation | Someone accuses someone of cheating at cards. The cards are probably not at fault. Trust takes a hit regardless. |
| Stealing Suspicion | A hero is suspected of pocketing more than their share. This may or may not be true, but suspicion does its damage either way. |

**Dramatic**

| Event | What Happens |
|-------|-------------|
| Love Triangle | Two heroes discover they are competing for the same third hero. Nobody handles this gracefully. Relationships shift; tension is efficiently generated. |
| Old Flame Appears | A hero's romantic history walks through the door. Mood effects depend entirely on how that particular history ended. |
| The Challenge | Someone issues a formal duel or contest. The outcome — not merely the result, but how each party behaves — shifts mood and reputation. |
| Secret Revealed | Something private becomes public. The consequences span a wide range, depending on what the secret was — and some of them were considerable secrets. |
| Marriage Proposal | A hero proposes to their Lovers-bonded partner. Requires relationship ≥ 80. Creates a Married bond on acceptance; creates a different kind of evening on refusal. |
| Dramatic Exit | A hero decides they've had enough and leaves. Unavailable for a period; the relationship with whoever provoked this is affected. |
| Lovers Getaway | A paired couple slips away for a few days. Both heroes become unavailable for 2 days. Whether they told anyone before leaving is unclear. |

Background events are **weighted** — dramatic events are rarer than positive ones, and positive events are less common than negative ones, because this is a tavern, not a spa. The exact mix depends on which heroes are present, what bonds exist between them, and what relationship scores are in play.

### Training Yard

Where heroes train and spar. The sounds of practice combat are indistinguishable from actual combat, which says something about the quality of training.

| Level | Training Speed | Features |
|-------|----------------|----------|
| 1 | 1.0x | Basic training |
| 2 | 1.25x | Sparring matches |
| 3 | 1.5x | Advanced techniques |
| 4 | 1.75x | Weapon specialization |
| 5 | 2.0x | Master training |

### Infirmary

Treats injured heroes. The smell of antiseptic potions mingles with the sound of "I told you not to fight the dragon."

| Level | Healing Speed | Features |
|-------|---------------|----------|
| 1 | 1.0x | Basic care |
| 2 | 1.25x | Better medicine |
| 3 | 1.5x | Surgery, basic prosthetics |
| 4 | 1.75x | Standard prosthetics |
| 5 | 2.0x | Enchanted prosthetics |

### Armory

A carefully organized collection of pointy things, blunt things, and things that go 'boom' when you least expect it. Determines how many items your guild can store.

| Level | Name | Equipment Slots | Daily Upkeep |
|-------|------|-----------------|--------------|
| 1 | Weapon Rack | 200 | 2g |
| 2 | Small Armory | 400 | 12g |
| 3 | Armory | 800 | 25g |
| 4 | Grand Armory | 1,400 (+ repair) | 45g |
| 5 | Arsenal | 2,000 (+ repair) | 1,500g |
| 6 | Legendary Arsenal | 3,000 (+ repair) | 3,000g |

### Forge

Where raw metal becomes something worth dying over. See [Crafting Guide](crafting.md) for details.

| Level | Craft Speed | Max Tier | Quality Bonus |
|-------|-------------|----------|---------------|
| 1 | 1.0x | ⭐ | - |
| 2 | 1.15x | ⭐⭐ | - |
| 3 | 1.3x | ⭐⭐⭐ | +10% |
| 4 | 1.5x | ⭐⭐⭐⭐ | +20% |
| 5 | 2.0x | ⭐⭐⭐⭐⭐ | +30% |

### Workshop

Covers all leather, cloth, and wood crafting. The Workshop absorbs the legacy Tannery, Loom, and Lumber Mill stations into a single upgradeable facility. The staff take pride in their work, which mostly involves hitting things with other things until they're useful.

See [Crafting Guide](crafting.md) for details.

| Level | Name | Process Speed | Quality Bonus | Daily Upkeep |
|-------|------|---------------|---------------|--------------|
| 1 | Basic Workshop | 1.0× | - | 8g |
| 2 | Crafting Workshop | 1.2× | +5% | 15g |
| 3 | Artisan Workshop | 1.4× | +10% | 25g |
| 4 | Master Workshop | 1.6× | +15% | 40g |
| 5 | Grand Workshop | 2.0× | +20% | 1,500g |
| 6 | Mythic Workshop | 2.5× | +30% | 3,000g |

### Library

Research new recipes and lore. The librarian insists on silence, which is ambitious given the explosions from the Alchemy Lab next door.

| Level | Research Speed | Max Recipe Tier |
|-------|----------------|-----------------|
| 1 | 1.0x | ⭐ |
| 2 | 1.25x | ⭐⭐ |
| 3 | 1.5x | ⭐⭐⭐ |
| 4 | 1.75x | ⭐⭐⭐ (+lore) |
| 5 | 2.0x | ⭐⭐⭐ (+lore) |

### Chapel

Provides mood bonuses and funeral services — two things that, in the adventuring business, are needed with roughly equal frequency.

| Level | Mood Bonus | Features |
|-------|------------|----------|
| 1 | +3 | Basic services |
| 2 | +6 | Blessings |
| 3 | +10 | Holy crafts |

**Special Features:**
- Memorial services for fallen heroes — the Chapel exists for many reasons, but this is the one it gets used for most
- Daily mood bonus for all heroes; the only passive benefit that doesn't require anyone to do anything dangerous
- Blessing buffs before expeditions — optional, but the Guild Clerk has noticed that heroes who skip the blessing tend to become memorial cases

---

## Guild Identity & Moral Events

Your guild develops a moral identity over time, shaped by the decisions you make when events arise. This isn't cosmetic — your guild's moral stance affects hero morale, shop prices, and which heroes approve or disapprove of your leadership.

### Moral Axes

Three axes define your guild's character, each ranging from -100 to +100:

| Axis | Positive (+) | Negative (-) |
|------|-------------|-------------|
| **Valor / Cunning** | Brave, direct, honourable | Pragmatic, deceptive, strategic |
| **Wealth / Glory** | Profit-driven, mercantile | Fame-seeking, generous |
| **Order / Freedom** | Disciplined, structured | Independent, chaotic |

Your position on each axis shifts based on event decisions. There is no right answer — every position has trade-offs.

### Moral Events

Starting from day 10, moral events appear randomly (roughly every 5-7 days). You'll see up to 3 pending events at once. Each presents a situation with multiple options, and each option shifts your moral axes and carries consequences.

**Event Categories:**

| Category | Theme |
|----------|-------|
| Guild Dilemmas | Internal policy decisions |
| Hero Conflicts | Interpersonal disputes requiring judgement |
| Mission Moral | Ethical choices arising from missions |
| Resource Decisions | How to spend or allocate guild resources |
| External Threats | Outside forces demanding a response |

Events have deadlines — ignore them and the default option resolves automatically. Same events won't repeat for 10 days.

**Viewing Events:** Open the Guild Events screen to see two tabs — **Active** (pending events awaiting your decision) and **History** (a log of all past decisions). The history shows the day, your chosen option, which heroes were involved, axis shifts with colour-coded badges, gold changes, and whether the event was auto-resolved because you ignored it.

### Hero Reactions

Heroes react to your moral decisions based on their personality traits:

| Trait | Approves | Disapproves |
|-------|----------|-------------|
| Kind | Valor shifts | Cunning shifts |
| Psychopath | Cunning shifts | Valor shifts |
| Greedy | Wealth shifts | Glory shifts |
| Empathic | Glory shifts | Wealth shifts |
| Loyal | Order shifts | Freedom shifts |
| Volatile | Freedom shifts | Order shifts |

Approving heroes gain mood; disapproving heroes lose it. The mood change scales with the size of the axis shift (roughly 1 mood per 3 axis points).

### Consequences

Event options can trigger a range of effects — sometimes immediately, sometimes several days later when you've forgotten what you decided:

- **Gold changes** — gain or lose gold, depending on whether your choice was the generous one
- **Reputation changes** — guild reputation shifts; the realm notices how you handle difficult situations
- **Hero effects** — promote, heal, or grant items to specific heroes involved in the event
- **Facility boosts** — bonus XP or levels to a facility
- **Recruit heroes** — new heroes join the guild, occasionally as a direct consequence of your having a reputation for being worth joining
- **Chain events** — some decisions trigger follow-up events days later; the game has written the next chapter regardless of whether you were paying attention

### Shop Discounts

A guild strongly aligned with Wealth earns shop discounts:

| Wealth Axis | Price Modifier |
|------------|---------------|
| 60+ | 10% discount |
| 30+ | 5% discount |
| Below 30 | Standard prices |

---

## Context-Aware Guild Events

The guild moral events described above are triggered by your position on the moral axes and arrive on a schedule. Context-aware events are different: they are triggered by your heroes.

The game continuously scans your roster for specific conditions — a rivalry at boiling point, a hero with dangerously low mood, a veteran who hasn't been acknowledged, a Psychopath with unchecked authority — and when it finds a match, it generates an event tailored to those specific heroes. The event uses their names. The options reflect their history. Ignoring it is a decision with its own consequences.

There are events in five categories. Each event has a deadline (typically 3–5 days). If the deadline passes without a decision, the game picks the default option for you. The default is never the worst option, but it is rarely the best one.

### Categories

**Hero Conflict** — what happens when you put strong personalities in close quarters and give them reasons to compete. Rival feuds, love triangles, veterans using recruits as a means of expressing their opinions about recruits, jealousy over promotions. These events are triggered by bond states, relationship scores, and mission counts — which, when you think about it, are just ways of tracking resentment numerically.

**Guild Dilemma** — structural tensions that require a decision before they make one for you. A hero requesting the promotion they've arguably earned. A problematic personality whose continued presence is becoming expensive. A near-death hero who has decided that mortality is a reason to reconsider. Some options result in a hero permanently leaving the guild. The game will tell you this in advance, which is courtesy of a kind the situation itself rarely offers.

**Mission Moral** — the bill that arrives after the dungeon run. A town you've been carving through sends someone to ask for help. The work you've taken on has a reputation attached to it. The wider world has noticed what kind of guild you're running. Whether this represents opportunity or accountability depends on your recent choices.

**Resource Decision** — the moments when gold and principle have to sit down together and negotiate. A hero with the Kind trait wants to shelter refugees (300g to shelter, 100g for temporary help, 0g to decline). Supply shortages arrive at inopportune times, as they tend to. Money-versus-values is, historically, an undefeated category.

**External Threat** — outside forces making their interest in your guild known. Rival guild alliance offers surface when you have enough Valor to negotiate without looking desperate (≥ 20). Bounties and political pressure arrive when you've attracted the wrong kind of attention. Whether any of this is welcome depends on which direction you've been pushing the axes.

### How Events are Matched

Each event specifies **hero slots** (typically 1–2 heroes) and a set of **preconditions**. The precondition engine checks every hero against those conditions and fills the slots with matching heroes. Precondition types include:

| Precondition | Example |
|---|---|
| Bond exists between heroes | Rival bond, Lovers bond, Attracted |
| Mood below threshold | Mood < 20 for a low-morale event |
| Stat above threshold | 100+ missions for veteran events |
| Days in guild minimum | Minimum tenure for loyalty-related events |
| Trait present | Psychopath, Kind, Volatile |
| Hero count minimum | At least 4 heroes in guild |

If no heroes match the preconditions, the event doesn't fire. Some events are common (rival disputes are a reliable feature of any active guild); others may never appear in a given playthrough if your heroes never develop the required conditions.

### Consequence Chains

Some events specify a **consequence chain** — a follow-up event scheduled 5–30 days later that reflects the choice made. A rival dispute resolved through compromise generates a different follow-up than the same dispute resolved by siding with one party. Consequence chains can themselves trigger further chains. The game has a long memory for these.

### Axis Effects

Context-aware events shift the guild's moral axes (Valor/Wealth/Order) just as standard guild events do, but the scale is typically smaller. Refusing a plea for help doesn't move the needle as far as a formal guild-wide decision — but it still moves it.

---

## Guild Reputation

Reputation unlocks better content and more expedition slots. Depressingly easy to lose, annoyingly hard to gain.

### Reputation Ranks

| Rank | Rep Required | Slots | Benefits |
|------|--------------|-------|----------|
| F | 0 | 1 | Starting rank |
| E | 500 | 2 | Workshop unlock, better missions |
| D | 1,500 | 3 | Good recruits |
| C | 4,000 | 4 | Elite missions |
| B | 10,000 | 5 | Rare recruits, Heroic access |
| A | 25,000 | 6 | Legendary missions |
| S | 60,000 | 8 | Best of everything |

### Earning Reputation

| Action | Reputation |
|--------|------------|
| Complete mission | +5 to +50 |
| Kill boss | +10 to +100 |
| Rescue NPC | +20 |
| Hero reaches Champion | +10 |
| Hero reaches Legend | +25 |

### Losing Reputation

| Action | Reputation |
|--------|------------|
| Fail mission | -10 to -30 |
| Abandon mission | -20 |
| Hero death (public) | -5 |
| Total party wipe | -50 |

---

## Guild Finances

The eternal struggle between "we need more heroes" and "we need to pay the heroes we have." A guild master's life is, at its core, an accounting problem with swords.

### Income Sources

| Source | Amount | Notes |
|--------|--------|-------|
| Dungeon loot | Variable | Main income |
| Tavern income | 300-20,000g/day | Based on level |
| Item sales | Variable | Sell to merchants |

### Expenses

| Expense | Amount | When |
|---------|--------|------|
| Hero wages | Per hero/week | Weekly |
| Facility upkeep | Per facility/day | Daily |
| Crafting materials | Variable | On craft |
| Recruitment | 50-500g | Per hire |
| Infirmary costs | Variable | Per treatment |

### Daily Wages

Heroes expect to be paid based on their level, because apparently risking their lives for the guild's reputation isn't reward enough:

```
Daily Wage = (Level - 1) × 3 × Quality Multiplier
```

| Hero Quality | Multiplier |
|--------------|------------|
| Common | 1.0x |
| Uncommon | 1.2x |
| Rare | 1.5x |
| Epic | 2.0x |
| Legendary | 3.0x |

**Examples:**
- Level 10 Common: (10-1) × 3 × 1.0 = 27g/day
- Level 20 Rare: (20-1) × 3 × 1.5 = 86g/day
- Level 50 Legendary: (50-1) × 3 × 3.0 = 441g/day

Level 1 heroes are free (no wages).

### Managing Finances

1. **Watch your burn rate** - Know weekly expenses
2. **Don't over-hire** - More heroes = more wages. This seems obvious, yet guilds go bankrupt every day.
3. **Sell excess items** - Keep vault clean
4. **Upgrade Tavern** - Passive income helps
5. **Build reserves** - Keep 2+ weeks of wages saved. The dungeon will still be there tomorrow.

---

## Hero Management

### Hero States

| State | Can Mission? | Can Craft? | Notes |
|-------|--------------|------------|-------|
| Ready | ✓ | ✓ | Available |
| Scheduled | ✗ | ✗ | Assigned to mission |
| On Mission | ✗ | ✗ | In dungeon |
| Injured | ✗ | ✗ | Recovering |
| Resting | ✗ | ✗ | Fatigue recovery |
| Crafting | ✗ | - | At station |
| Training | ✗ | ✗ | At Training Yard |
| Dead | ✗ | ✗ | Permanent |

### Hero Mood

Mood affects combat performance. Happy heroes hit harder; miserable heroes hit the tavern:

| Mood | Effect |
|------|--------|
| Excellent | +10% all stats |
| Good | +5% all stats |
| Neutral | No modifier |
| Poor | -5% all stats |
| Terrible | -15% all stats |

**Improving Mood:** The things worth investing in.
- Tavern activities (Buy Rounds, Feast) — the Guild Clerk considers these mandatory expenses
- Comfortable Barracks — the baseline everyone notices when it falls below acceptable
- Chapel bonus — passive, daily, and the easiest improvement in the game to arrange
- Successful missions — nothing lifts morale like coming back
- Good relationships — heroes who like each other perform better, which in turn keeps morale higher

**Decreasing Mood:** The things that happen anyway.
- Failed missions — the performance penalty and mood penalty compound together
- Ally deaths — difficult to prevent, impossible to ignore
- Poor Barracks — the complaint that never stops
- Overwork — unchecked, it turns capable heroes into liabilities
- Relationship conflicts — stress is contagious in small, armed groups

### Mental Breaks

When mood drops too low, heroes may have mental breaks. These are, without exception, inconvenient:

| Break | Effect | Duration |
|-------|--------|----------|
| Tantrum | May damage property | 1 day |
| Hiding | Won't work | 2 days |
| Berserk | May fight allies | Until calmed |
| Catatonic | Cannot function | 3+ days |
| Breakdown | Leaves guild | Permanent |

Prevent breaks by maintaining hero mood above "Poor".

---

## Hero Relationships

Heroes form bonds with each other, for better and frequently for worse. See [Relationships Guide](relationships.md) for full details.

### Relationship Levels

| Level | Trust | Combat Bonus |
|-------|-------|--------------|
| Neutral | -9 to +9 | None |
| Friendly | +10 to +29 | +5% |
| Friend | +30 to +59 | +10% |
| Close Friend | +60 to +79 | +15% |
| Best Friend | +80 to +94 | +20%, Intervene |
| Devoted | +95 to +100 | +25% |

### Special Bonds

| Bond | Effect |
|------|--------|
| Lovers | The most powerful bond in the game. Also the most expensive to lose. |
| Rivals | Both fight harder when the other is watching. Neither admits this. |
| Mentor/Student | The veteran improves the rookie. The rookie reminds the veteran how annoying they used to be. |
| Enemies | Active mutual resentment with measurable stat consequences. |

---

## Guild Shop

The guild shop lets you sell items to visiting customers for gold — turning your dungeon loot into someone else's problem.

| Level | Name | Display Slots | Customers/Day | Daily Upkeep |
|-------|------|---------------|---------------|--------------|
| 1 | Market Stall | 8 | 4-7 | 5g |
| 2 | Small Shop | 16 | 6-10 | 10g |
| 3 | Merchant Store | 24 | 10-15 | 20g |
| 4 | Trading Post | 32 | 14-20 | 600g |
| 5 | Emporium | 48 | 20-30 | 1,500g |

**Customer Types:** Peasants, Adventurers, Merchants, Knights, Nobles, Collectors, Rival Guilds, and Mages — each with different budgets and item preferences.

**Pricing:** Set prices on displayed items. Customers react based on how your price compares to fair value — price too high and they leave, price too low and you lose profit. Finding the sweet spot is an art form that most guild masters discover through expensive trial and error.

**Market Events:** Random events like Festivals (+30% accessory demand), Wars (+25% weapon/armor demand), or Disease Outbreaks (+50% consumable demand) temporarily shift prices.

---

## Item Workshop

The Item Workshop lets you reroll bonus stats on Rare or higher rarity items for gold. Named items cannot be rerolled, because some things are sacred (or at least expensive enough to discourage tampering).

**Reroll Cost Formula:**
```
Cost = 1,000 × Rarity × 2^(Reroll Count)
```

Costs double with each successive reroll. You can preview the new stats before accepting or rejecting.

Navigate to the Item Workshop from the Guild Screen → Item Workshop button.

---

## Merchant Caravans

Traveling merchants visit your guild periodically, offering items and services. Their arrival is always welcome; their prices, less so.

- **First Arrival:** Day 5
- **Visit Interval:** Every 3-7 days
- **Stay Duration:** 2-5 days

**Merchant Types:** Armorer, Alchemist, Jeweler, Exotic Goods, Black Market, Collector, Wanderer, and Master Crafter. Higher guild reputation attracts rarer merchants (Master Crafter at 5,000+ rep, Exotic Goods at 2,000+).

**Services:** Repair equipment, sharpen weapons, identify items, custom brewing, gem socketing, item upgrading, and more — costs vary by merchant type.

---

## Rival Guilds

> **Currently Disabled** — The Rival Guild system exists in the game code but is currently disabled. The information below describes the intended design, which is to say, a design that exists in the philosophical sense.

Rival guilds are AI-controlled competing guilds with different personalities (Aggressive, Scheming, Honorable, Desperate, Mercantile). They can interact with your guild through events like hero poaching, reputation attacks, sabotage, trade offers, and challenges.

---

## Guild Chronicle

The Guild Chronicle (Guild Screen → Guild Stats) tracks lifetime statistics for all heroes across two tabs. It is, essentially, a permanent record of every decision you've ever made — good and bad.

**Combat Tab:**
- Top 3 heroes by: Damage Dealt, Damage Taken, Healing Done, and Kills
- Sortable table with columns: Hero, Class, Stars, Level, Ascendancy, Power, Damage Out, Damage In, Healing Out, Healing In, Kills, Bosses, DPS, Missions

**Social Tab:**
- Top 3 heroes by: Most Drinks, Most Days Off, Best Mood, and Most Friends
- Sortable table with columns: Hero, Mood, Friends, Rivals, Drinks, Days Off, Addiction, Background

Click any column header to sort. Hover on Friends/Rivals columns to see relationship names.

### Guild Hero Ranks

Each hero holds a guild rank that advances automatically based on time served and missions completed:

| Rank | Days in Guild | Missions Completed |
|------|--------------|-------------------|
| Recruit | 0 | 0 |
| Member | 50 | 25 |
| Senior | 150 | 75 |
| Officer | 300 | 200 |
| Leader | 500 | 400 |

Both thresholds must be met for promotion. A hero who has completed 400 missions but only served 200 days remains an Officer until day 500.

### Chronicle Entries

The chronicle tracks events across three categories:

- **Combat:** First kill, boss kill, biggest crit, near-death, intervene save, worst injury
- **Social:** Bond formed, bond lost, romantic milestone, mental break
- **Guild:** Mission milestone, crafting masterwork, facility contribution, rank promotion, ascendancy trial

Accumulating 50+ entries earns the **Legend** title (+3 to all stats). See [Chronicle Titles](heroes.md#chronicle-titles) for all title bonuses.

---

## Daily Operations

### Daily Cycle

The day proceeds in five phases, with or without your attention — though your attention is recommended:

1. **Dawn** - Expeditions return and process results; this is when you find out how last night went
2. **Morning** - Check injuries, assign treatment; the infirmary does not operate on optimism alone
3. **Day** - Craft, train, prepare missions; the most productive part of the cycle, which is also the easiest to skip
4. **Evening** - Launch supervised expedition; typically the one you've been planning since morning
5. **Night** - Unsupervised expeditions run; you've made your choices and can no longer help

### Weekly Cycle

- **Day 1** - Wages paid; the number that reminds you what "burn rate" means
- **Daily** - Facility upkeep charged; small individually, significant collectively
- **Variable** - Mission board refreshes; new opportunities, some of which are genuinely dangerous

### Recommended Daily Routine

Not strictly required. Heroes are capable of functioning without micromanagement — they simply function worse. The Guild Clerk recommends this order:

1. Check expedition results — find out what happened while you were unavailable
2. Heal injured heroes — the Infirmary addresses problems that sympathy cannot
3. Manage mood (Tavern activities) — preemptive morale investment, cheaper than recovery
4. Assign crafters — idle crafting stations are missed resources
5. Review mission board — evaluate options before committing to them
6. Form expedition parties — check compatibility, not just stats
7. Launch nightly missions — the guild's primary source of income, experience, and incident reports

---

## Upgrade Priority

The Guild Clerk's recommendations, based on extensive observation of which guilds survive their first year and which don't:

### Early Game

1. **Guild Hall 2** - More mission slots means more income; this is the foundational upgrade
2. **Barracks 2** - A mood penalty from overcrowding compounds daily; fix it early
3. **Tavern 2** - Better recruits start arriving, which is the entire point of having a Tavern
4. **Infirmary 2** - Faster healing means heroes are back on roster sooner; you will need this immediately

### Mid Game

1. **Forge 3** - Better equipment tier unlocked; the quality jump at level 3 is significant
2. **Training Yard 3** - Faster leveling for heroes who aren't the ones dying; invest in the ones who survive
3. **Library 3** - Research unlocks recipes that cannot be obtained any other way
4. **Warehouse 3** - More storage means less forced selling of materials you'll want later

### Late Game

1. **All facilities to max** - Every bonus counts at high levels; there are no unimportant upgrades at this point
2. **Chapel 3** - Mood management becomes critical as the roster grows and the drama multiplies
3. **Arsenal** - Equipment maintenance becomes a real consideration when heroes are carrying Legendary gear

---

## Tips for Guild Masters

The Guild Clerk has watched enough guilds fail to identify the patterns. These are the lessons that tend to arrive too late when learned by experience:

1. **Balance your roster** - Diversity in classes and levels prevents the specific kind of catastrophe where you really need a Cleric and don't have one
2. **Maintain reserves** - Backup heroes exist to replace heroes who are injured, which they will be; the backup heroes will also get injured eventually
3. **Watch finances** - Bankrupt guilds close, and closed guilds do not make comebacks; know your weekly burn rate before it exceeds your weekly income
4. **Manage relationships** - Happy heroes fight better, and heroes who like each other fight better still; the social tab is not optional reading
5. **Upgrade steadily** - No facility is unimportant; the one you neglect will be the one you needed
6. **Use the Tavern** - Morale activities are the cheapest productivity investment in the guild; the comparison is to replacing heroes who leave due to low morale

---

## Related Guides

- [Heroes & Classes](heroes.md) - Your roster
- [Crafting](crafting.md) - Production facilities
- [Dungeons](dungeons.md) - Expedition management
- [Relationships](relationships.md) - Social system

---

*"Running a guild is easy. It's the heroes, finances, facilities, reputation, morale, injuries, deaths, and interpersonal drama that make it complicated."*
