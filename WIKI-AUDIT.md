# Wiki Fact Audit

Every checkable claim in `guides/*.md`, with the code reference that settles it.
Phase 1 (this pass) collects the claims. Phase 2 marks each **OK** (code agrees),
**KO** (code disagrees), or **N/A** (unverifiable / pure flavour kept for context).

Game source root: `/home/anarion/proj/herosguild/game/`

| Status | Meaning |
|--------|---------|
| — | not yet checked |
| OK | code confirms the claim as written |
| KO | code contradicts the claim; needs a doc fix |
| ? | could not locate the authority in code |

## Progress

- **717 claims catalogued** across 20 guides, 5 repository documents, 10 cross-document consistency checks and 3 link checks.
- **195 verified so far** — 162 OK, 33 KO.
- Remaining rows are marked `—`. Verification continues guide by guide against `/home/anarion/proj/herosguild/game/`.

---

## events.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| EV-01 | 3 | Six distinct event systems exist | count the systems the other guides document | — | |
| EV-02 | 9 | Tavern **Tonight** tab presents 6-8 situations per night | tavern scene builder (`GameState.buildTavernScene` / TavernTypes) | — | |
| EV-03 | 11 | Attention Points are limited; ignored situations return next night "slightly worse" | tavern decision engine escalation | — | |
| EV-04 | 13 | Morning **Last Night's Notes** panel records resolved decisions | day-summary / Tavern UI component | — | |
| EV-05 | 21 | 22 background events across three types | tavern background event catalog | — | |
| EV-06 | 23 | Background events include Drinking Contest, Bar Fight, Love Triangle, Marriage Proposal | same catalog | — | |
| EV-07 | 31 | Three moral axes: Valor, Wealth, Order | guild axis model | — | |
| EV-08 | 43 | Context-aware events carry deadlines and auto-resolve to a default option when missed | context-aware event engine | — | |
| EV-09 | 51 | Ambient social events named: Good Conversation, Gift Giving, Mentorship Offer / Argument, Betrayal, Rumor Spreading / Saved Life, Left Behind, Brilliant Strategy / Tavern Drinking, Secret Shared | social event catalog | — | |
| EV-10 | 63 | 145+ in-dungeon moral events across seven environments (Forest, Cave, Ruins, Crypt, Swamp, Tower, Volcano), three options each | dungeon moral event data | — | |
| EV-11 | 63 | Some dungeon events gate on a specific hero (trait, mood, bond, chronicle title) and use their name | dungeon moral event requirement fields | — | |
| EV-12 | 73 | Hazards are deterministic, resolved by class composition, with no choice menu | hazard resolution code | — | |
| EV-13 | 91 | 14 crisis types; Cult of the Unseen injects 3 moral events at Moderate+; Heretic Schism 1 per severity escalation; Plague / Cult of the Unseen / Dragon's Tithe fire permadeath moral events at Critical | CrisisState / crisis event injection | OK | 14 crisis types confirmed |

## getting-started.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| GS-01 | 3 | Quillsworth's in-game tutorial explains each screen on first visit | tutorial controller | — | |
| GS-02 | 17 | Daily wages are charged only on heroes at level 2+; level-1 heroes cost nothing | `calculateHeroWages` | OK | wages charged only when hero.level >= 2 |
| GS-03 | 17 | Wages scale exponentially with hero level and hero quality/rarity | `calculateHeroWages` | OK | same formula |
| GS-04 | 29 | Each day: wages tick, contracts expire and refresh, merchants restock, lifecycles age, event windows close | `GameState.advanceDay` | — | |
| GS-05 | 33 | Unhappy heroes fight poorly and eventually leave | mood -> combat modifier + desertion check | — | |
| GS-06 | 39 | "Balance beats power" for the first ~30 hours | advice, not a code claim | N/A | flavour |
| GS-07 | 43 | Guild Hall L1 unlocks 2 mission slots, L2 unlocks 4 | `GuildFacilities.ts` GuildHall levels | OK | missionSlots 2 at L1 and 4 at L2 |
| GS-08 | 43 | Guild Hall L2 costs 5,000g + 50 wood + 30 stone and 3 days | `GuildFacilities.ts` GuildHall level 2 | OK | 5,000g + 50 wood + 30 stone, upgradeTimeDays 3 |
| GS-09 | 43 | Barracks starting capacity is 12 heroes | `GuildFacilities.ts` Barracks level 1 | OK | Barracks L1 maxHeroes 12 |
| GS-10 | 47 | Equipped potions auto-drink below 50% HP; mana flasks at 30%; antidotes when poisoned; thresholds configurable in Settings -> Combat | combat auto-consume logic + settings | — | |
| GS-11 | 51 | Bonds and rivalries directly affect combat performance | combat bond modifiers | — | |
| GS-12 | 57 | Raids are 15-hero fights unlocking at 5,000 reputation and a level-50 hero | raid unlock gate | — | |
| GS-13 | 58 | Abyssal Spire unlocks when a hero reaches level 95; a Tower run advances the game day | `Tower.ts` / unlock gate | OK | unlock level 95 confirmed; tower run advancing the day pending |
| GS-14 | 67 | The Infirmary heals injured heroes but assignment is manual | infirmary / injury healing code | — | |
| GS-15 | 76 | Every hero has an auto-generated Chronicle journal | chronicle model | — | |
| GS-16 | 78 | Every hero has a passive progression tree allocated on level-up | passive tree model | — | |
| GS-17 | 82 | Most craft recipes must be researched at the Workshop before crafting | crafting research gate | — | |
| GS-18 | 88 | There are six hero classes | `HeroClass.ts` | — | |

## backgrounds.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| BG-01 | 7 | Each hero gets 4 lifecycle events drawn from a catalog of "just under two hundred" | `data/lifecycle/catalog.*.ts` totals | KO | the catalog holds 120 events (30 per stage), not "just under two hundred" |
| BG-02 | 15-24 | Eight backgrounds: Noble, Criminal, Soldier, Peasant, Scholar, Merchant, Cultist, Outlander | background enum/data | — | |
| BG-03 | 15 | Background is assigned at generation, independent of class and quality | hero generation | — | |
| BG-04 | 26 | Each background grants a permanent combat modifier shown as a runtime active-effect | background effect data | — | |
| BG-05 | 34-39 | Stage table: Childhood 5-10 / 44 events; Adolescence 11-16 / 49; Young Adulthood 17-22 / 53; Before the Guild 23-30 / 48 | per-stage catalog counts + age ranges | KO | age ranges are right (LIFE_STAGE_AGE_RANGE: 5-10 / 11-16 / 17-22 / 23-30) but every stage has exactly 30 events, not 44 / 49 / 53 / 48 |
| BG-06 | 41 | The lifecycle roll happens once at hire, is deterministic, and cannot be re-rolled | lifecycle roll code | — | |
| BG-07 | 45 | Events are tagged by background; matching tags are weighted up but cross-background events stay eligible | lifecycle weighting | — | |
| BG-08 | 49 | Hard cap: no background tag claims more than a quarter of any stage's events | authoring guide / catalog distribution | OK | no background tag exceeds 25% of any stage; rule is stated in lifecycleAuthoringGuide.md and holds in data |
| BG-09 | 57-59 | Lifecycle modifiers touch damage, hp, str, dex, int, vit, lck; damage sits on top of the class damage multiplier; hp applies at the end of the chain (after passives, ascendancy, body efficiency, titles); stats apply as the final pass | lifecycle aggregator + effective-stat chain | — | |
| BG-10 | 61 | All four events' modifiers compound, as do lifecycle-granted trait modifiers | lifecycle aggregator | — | |
| BG-11 | 67 | Lifecycle traits (Duelist, Sickly, Iron Constitution) are computed by the lifecycle aggregator, not the trait system | trait handling | — | |
| BG-12 | 70 | Body system: 25 parts across four regions (head: brain, eyes, ears, jaw, nose; torso: heart, lungs, liver, kidneys, stomach, spine; arms: shoulders, arms, hands; legs: legs, feet) | body-part data | — | |
| BG-13 | 72 | A flaw applies once per slot; minor flaws land as Damaged, severe as Destroyed | lifecycle flaw application | — | |
| BG-14 | 74 | Prosthetics lift body-part efficiency back up; the event's stat penalty is permanent | prosthetic + lifecycle penalty code | — | |
| BG-15 | 82 | Recruit-details modal shows a section titled "A Life, So Far" | tavern recruit modal | — | |
| BG-16 | 86 | Background tab (icon 📜) sits alongside Gems, Social, Career, Chronicle, Paragon, Trials | HeroDetailTabs | — | |
| BG-17 | 88-91 | Background tab order: Origin, four stage paragraphs, "Marks of a Life", "Traits" (decoded `lifecycle:*` traits) | HeroDetailTabs background panel | — | |
| BG-18 | 93 | The Chronicle tab does not weave in lifecycle paragraphs | chronicle rendering | — | |
| BG-19 | 99 | Pre-system saves backfill four events on first load, seeded from hero ID so it is deterministic | migration code | — | |
| BG-20 | 101 | Backfill shifts existing heroes' effective stats on first load | same migration | — | |

## quest-chains.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| QC-01 | 15 | Seven story chains, each gated on a guild rank, starting at rank F | `StoryChains.ts` | OK | STORY_CHAINS has 7 entries, lowest gate rankMin GuildRank.F |
| QC-02 | 17-19 | Story chains are 3-5 steps, have no time limit, and finale-reward a named legendary + reputation, with two chains also granting a special hero at the highest hero's level, pre-equipped and pre-specced | `StoryChains.ts` | OK | step counts are 4/4/5/4/5/3/3 - all within the stated 3-5 range |
| QC-03 | 23 | The Founding Blade (rank D) and The World Tree Pact (rank D) are both 3-step; Nature's Embrace is a Legendary leather chest for Ranger/Cleric (`NamedItems.ts:331-341`); both finales give named item + recipe + 2 gems | `StoryChains.ts`, `NamedItems.ts` | — | |
| QC-04 | 27-30 | Seven class chains across six classes (Mage has two); unlock needs guild rank E+ AND a hero of that class at level 25+ | `ClassChains.ts` | OK | CLASS_CHAINS has 7 entries across 6 classes; six gate on rankMin E + heroLevelMin 25 |
| QC-05 | 34-36 | Class chains are 3 steps, no time limit, finale = class-restricted named item + crafting recipe + two skill gems | `ClassChains.ts` | OK | every class chain has exactly 3 steps |
| QC-06 | 38 | The Archmage's Thesis needs level 40 and rank C (`ClassChains.ts:148`) and rewards Archmage Robes | `ClassChains.ts:148` | OK | ARCHMAGE_THESIS unlockCondition is rankMin GuildRank.C, heroClassRequired Mage, heroLevelMin 40 |
| QC-07 | 44-49 | Twelve weekly bounty templates, no unlock requirement, 3 steps, 7-day timer, never the same bounty two weeks running, finale = one random Epic+ item scaled to the highest hero's level plus roughly 1,800-4,200g | weekly bounty data | OK | 12 templates, 3 steps each, expiresDay = day + 7 rolling on (day - saveInitialDay) % 7, finaleGold values run 1,800 to 4,200, and rollWeeklyBounty excludes previousBountyId |
| QC-08 | 57 | Chain steps appear on the Mission Board with a 📜 badge and a tooltip naming chain and step | mission board rendering | — | |
| QC-09 | 66-70 | Ignoring a step rolls it to the next board unchanged; failing loses no progress; success shows a narrative screen and unlocks the next step on tomorrow's board | `QuestChain.ts` | — | |
| QC-10 | 74 | A weekly bounty expiring mid-dispatch still completes and resolves; the timer only gates future board rolls | `QuestChain.ts` expiry | — | |
| QC-11 | 80 | Quest Log button uses glyph ❡ and sits in the Top Bar (`TopBar.tsx:134`), visible from day 1 | `TopBar.tsx` | — | |
| QC-12 | 84-86 | Quest Log has Story / Class / Weekly tabs; 7 story chains and 7 class chains across 6 classes in the catalog; Weekly shows a ⏰ countdown plus history | `QuestLog.tsx` + chain catalogs | OK | 7 story + 7 class chains confirmed in the registries |
| QC-13 | 88 | Quest Log does not enumerate locked chains with their requirements (`QuestLog.tsx:113-148`); it renders only chains present in `questChainState.chains` | `QuestLog.tsx` | — | |
| QC-14 | 94-103 | Reward matrix: reputation is story-finale only; named item on story and class finales; recipes on some story and all class; gems on some story and 2x on class; random Epic+ only weekly; special hero on 2 story chains | chain catalogs | — | |
| QC-15 | 111 | Special-hero rewards join at the level of the current highest-level hero, with equipment and a built skill setup | `QuestChain.ts` special hero grant | — | |
| QC-16 | 113-120 | Over-cap arrivals are allowed; a 14-day grace timer runs (`QuestChain.ts:746-766`) with warning colours at elapsed 0-6 (yellow), 7-11 (orange), 12 (modal), 13 (red) | `QuestChain.ts:746-766` | OK | QuestChain.ts:745-765 - elapsed 0-6 yellow, 7-11 orange, 12 day-13 modal, 13 red, removal at >=14 |
| QC-17 | 126 | On day 13 a modal names the lowest-mood hero; on day 14 that hero departs automatically | same | OK | the day-13 modal names lowestMoodHero and auto-removal fires the next tick |
| QC-18 | 136-140 | Unlock timing: first weekly bounty day 1 then every 7 days; story chains at ranks F, E, D, D, D, C, B; class chains rank E + level-25 hero; Thesis rank C + level-40 Mage | chain catalogs | OK | story ranks are F, E, D, C, B, D, D - the same multiset the guide lists, with three at D |
| QC-19 | 149 | The two special-hero chains are "The Undead Plague" and "The Rival's Gambit" | `StoryChains.ts` | OK | specialHero appears only on UNDEAD_PLAGUE (Cleric) and RIVALS_GAMBIT (Rogue) |
| QC-20 | 150 | Each chain has at most one active step on the board at a time; multiple chains can be active at once | `QuestChain.ts` | — | |

## heroic-dungeons.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| HD-01 | 7 | There are exactly 10 heroic modifiers | heroic modifier catalog | OK | HEROIC_MODIFIERS has exactly 10 entries |
| HD-02 | 11-19 | Overwhelming Force 💪, difficulty 2/3: enemies +50% HP, +25% damage; reward +50% gold; red glow | modifier data | OK | difficulty 2, enemyHpMultiplier 1.5, enemyDamageMultiplier 1.25, goldMultiplier 1.5 |
| HD-03 | 21-28 | Relentless Assault ⚔️, 3/3: enemies respawn once at 50% HP; reward +2 guaranteed item drops | modifier data | OK | difficulty 3, respawnOnce true at 50% HP, guaranteedItems 2, no gold multiplier |
| HD-04 | 30-37 | Vampiric Enemies 🩸, 2/3: enemies heal 10% of damage dealt; reward +30% gold | modifier data | OK | difficulty 2, enemyLifeLeech 0.1 applied at Combat.ts:957, gold 1.3 |
| HD-05 | 39-46 | Enrage Timer ⏱️, 3/3: after turn 15 all enemies gain +100% damage; reward +40% gold | modifier data | OK | difficulty 3, enrageAtTurn 15 wired through Combat.applyHeroicModifier and Combat.ts:5315 doubles base damage from that turn; gold 1.4 |
| HD-06 | 48-55 | Elite Swarm 👑, 2/3: all normal enemies upgraded to elite; reward +1 material tier, +40% gold | modifier data | OK | difficulty 2, materialTierBonus 1, gold 1.4 |
| HD-07 | 57-64 | Fragmented Reality 🌀, 2/3: room connections randomise every 3 rooms; reward +30% gold | modifier data | OK | difficulty 2, gold 1.3 |
| HD-08 | 66-73 | Cursed Ground 💀, 2/3: heroes take 2% max HP damage per turn; reward +1 material tier, +40% gold | modifier data | OK | difficulty 2, dotDamagePercent 2 (heroicDotPercent 0.02), materialTierBonus 1, gold 1.4 |
| HD-09 | 75-82 | Arcane Instability ✨, 2/3: random spell effects each room; reward +100% skill gem chance, +30% gold | modifier data | OK | difficulty 2, gemDropBonus 1.0, gold 1.3 |
| HD-10 | 84-90 | Shattered Defenses 🛡️, 2/3: heroes -30% armor and resistances; reward +30% gold, 3x defense gear drop frequency | modifier data | KO | difficulty, -30% armor and gold 1.3 are right, but the "3x defense gear drop frequency" is only a code comment in the rewardBonus block (HeroicModifier.ts:236) - no item-generation code implements it |
| HD-11 | 92-99 | Chaos Incarnate 🌪️, 3/3: two random modifiers at once; reward +75% gold stacking with components | modifier data | OK | difficulty 3, gold 1.75 |
| HD-12 | 117-127 | Gold = Base x Modifier Bonus x Difficulty Bonus, with difficulty 2 = +10% and difficulty 3 = +20%; worked examples 1.65x, 1.2x, 2.1x | heroic reward calc | OK | HeroicModifier.ts:286-292 - gold multiplier then x1.1 at difficulty 2 and x1.2 at difficulty 3; all three worked examples reproduce |
| HD-13 | 133 | Three heroic dungeons per week, rotating Thursday 00:00 UTC, epoch 2026-01-01, 7-day steps (`WeeklyRotation.ts:24`) | `WeeklyRotation.ts` | OK | WeeklyRotation.ts:24-32 - EPOCH 2026-01-01T00:00:00Z (a Thursday) stepping in 7-day blocks; three options generated per week |
| HD-14 | 135-139 | Tiers: Heroic Trial ⭐⭐⭐ at base level (min 80), Heroic Challenge ⭐⭐⭐⭐ at base+5, Heroic Ordeal ⭐⭐⭐⭐⭐ at base+10 | heroic dungeon generation | OK | configs give 3/4/5 stars at baseLevel/+5/+10 with baseLevel = max(80, maxHeroLevel) |
| HD-15 | 141 | Each tier draws a random modifier; Chaos Incarnate is excluded from weekly rotation; no modifier repeats within a week | rotation code | OK | availableModifiers filters out ChaosIncarnate (WeeklyRotation.ts:73) and usedModifiers prevents repeats within the week |
| HD-16 | 143 | Access is Mission Board -> Heroic filter (🔥) with a countdown to the next reset | mission board UI | — | |
| HD-17 | 149 | Each heroic completion rolls 8% Epic and 2% Legendary recipe scrolls independently; duplicates convert to 10,000g / 100,000g | recipe drop code | OK | recipeDrops.ts:18 - heroic_dungeon epic 0.08 / legendary 0.02, duplicates convert to 10,000g / 100,000g |

## tower.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| TW-01 | 10 | The Spire unlocks with at least one hero at level 95+ | tower unlock gate | OK | TOWER_CONFIG.UNLOCK_LEVEL = 95 |
| TW-02 | 11 | Party size is capped at 6 heroes (`selectedIds.size < 6` in `TowerMenu.tsx`) | `TowerMenu.tsx` | — | |
| TW-03 | 19-26 | Floor events: combat every floor, mini-boss every 10, shop every 15, major boss every 25, with major boss taking precedence over mini-boss | `Tower.ts` floor typing | OK | getFloorType checks MAJOR_BOSS_INTERVAL 25 before MINI_BOSS_INTERVAL 10; isShopFloor is every 15 |
| TW-04 | 39-47 | Enemy Level = 100 + floor(Floor x 0.75); table gives 100 / 107 / 137 / 175 at floors 1 / 10 / 50 / 100 | `Tower.ts` | OK | getEnemyLevel = 100 + floor(floor * 0.75); all four table values reproduce |
| TW-05 | 53-58 | Difficulty tier by floor: 1-10 tier 2, 11-25 tier 3, 26-50 tier 4, 51+ tier 5 | `Tower.ts` | OK | getDifficultyTier: <=10 -> 2, <=25 -> 3, <=50 -> 4, else 5 |
| TW-06 | 64-71 | Enemy counts per floor band, min/max/boss-adds: 1-10 (2/3/2), 11-25 (3/4/3), 26-50 (4/5/4), 51-75 (4/6/4), 76-100 (5/6/4), 100+ (5/7/5) | `Tower.ts` | OK | TOWER_CONFIG.ENEMY_COUNTS matches all six bands including bossAdds |
| TW-07 | 77-87 | Five environments on a 20-floor cycle: Crystal Halls (Construct, Elemental), Shadow Depths (Undead, Demon), Infernal Chambers (Demon, Dragon), Celestial Heights (Construct, Elemental), Void Sanctum (Demon, Undead, Dragon); cycles after floor 100 | `Tower.ts` environments | OK | TOWER_ENVIRONMENTS names and enemy categories match; getTowerEnvironment cycles every 20 floors |
| TW-08 | 95-100 | Shop stock and prices: Healing Potion 25g/50HP, Greater 60g/100HP, Elixir of Vigor 40g/25% party, Antidote 15g/cure+10HP | tower shop data | OK | TOWER_SHOP_ITEMS: 25g/50HP, 60g/100HP, 40g/25% party, 15g cure+10HP |
| TW-09 | 108-115 | Six tower set items with slots and drop floors: Spirebreaker Helm (25), Spirebreaker Aegis (50), Voidtouched Cloak (50), Voidtouched Focus (75), Abyssal Boots (75), Abyssal Mask (100) | tower set item data | OK | TOWER_SET_DROP_FLOORS: helm 25, aegis 50, cloak 50, focus 75, boots 75, mask 100. Omission: per-item drop chances (0.50, 0.40, ...) are not documented |
| TW-10 | 119-123 | Set bonuses, always-on and tower-only, for Spirebreaker / Voidtouched / Abyssal as tabulated | set bonus data | OK | TowerSets.ts bonuses match all three sets, always-on and tower-only |
| TW-11 | 125 | Tower-only halves are gated by an `isTowerCombat` flag set at the start of each Spire fight | combat set-bonus gating | — | |
| TW-12 | 127 | Each set needs both pieces; a single piece grants base item stats but no set bonus | set bonus code | — | |
| TW-13 | 133 | Currencies roll per floor cleared, as independent Bernoulli trials, and the Spire is the only source that awards per floor rather than per completion | `TowerRun.tsx` + `currencyDrops.ts` | — | |
| TW-14 | 135-145 | Per-floor rates: Powders 10% / 8%, Salt of Renewal 3%, each Ichor 2%, Salt of Cleansing 0.8%, both Portents 0.8%, Cursed Sigil 0.5% baseline | `currencyDrops.ts` RATES abyssal column | — | edited this session |
| TW-15 | 147 | Depth maps to stars: floors 1-10 = 2 stars, 11-25 = 3, 26-50 = 4, 51+ = 5, so Ichors start at floor 11, Cleansing/Portents at 26, Cursed Sigil at 51 | `towerFloorToStars` + `MIN_DIFFICULTY_STARS` | — | edited this session |
| TW-16 | 151-165 | Sigil soft pity: Rate = min(15%, 0.5% + max(0, floors_since - 50) x 0.05%), with table values 0.5 / 1.75 / 3.0 / 5.5 / 10.5 / 15% | `abyssalSigilRateWithPity` | — | |
| TW-17 | 153 | The pity counter tracks floors since the last Sigil from ANY source; raids, world bosses and heroic dungeons all reset it | `resetAbyssalPityOnSigilDrop` | — | |
| TW-18 | 155 | The counter increments on every floor cleared, including floors the Sigil cannot drop on | `TowerRun.tsx:309-313` | — | edited this session |
| TW-19 | 176 | Score = (Floor x 100) + (Enemies Defeated x 10) + (Gold Earned / 100) | `Tower.ts` calculateScore | OK | calculateScore = floor*100 + enemiesDefeated*10 + floor(gold/100) |

## crisis.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| CR-01 | 3 | Fourteen distinct crisis types exist | `CrisisState.ts` / crisis catalog | OK | CrisisType enum has exactly 14 members |
| CR-02 | 13 | No crisis fires before day 45 | crisis trigger gate | OK | DAY_GATE = 45 (CrisisState.ts:186) |
| CR-03 | 14 | 30-day cooldown after a crisis ends | crisis trigger gate | OK | COOLDOWN_DAYS = 30 |
| CR-04 | 15 | Daily trigger roll is 5% + 2% per day past cooldown, capped at 60% | crisis trigger roll | OK | BASE_PROBABILITY 0.05, PROBABILITY_PER_DAY 0.02, PROBABILITY_CAP 0.60 |
| CR-05 | 17 | Durations run 8-20 days depending on type; start is announced by modal | crisis catalog | OK | all 14 durationRange values fall in 8-20 and match the per-crisis tables |
| CR-06 | 23-28 | Four severity tiers (Mild/Moderate/Severe/Critical); crises start Mild; severity bumps once at the halfway point with no resolution missions; a full run with zero resolutions ends at Critical | crisis escalation code | — | |
| CR-07 | 31 | Completing a resolution mission drops severity one tier | crisis de-escalation | — | |
| CR-08 | 34-37 | End conditions are Engaged (>=1 resolution), Partial (some but insufficient), Ignored (zero) | crisis end evaluation | — | |
| CR-09 | 49-52 | Economic: Creeping Plague 🦠 12-18d (upkeep x1.2-2.0, recruitment frozen at Moderate+, rewards x0.5-0.9, illness contagion x3 under an 0.85 ceiling); Great Famine 🌾 14-20d (upkeep x1.05-2.5, recruitment frozen at Severe+) | crisis catalog + `MAX_CONTAGION_PROBABILITY` | OK | Plague 12-18 upkeep 1.2-2.0, rewards 0.9-0.5, frozen from Moderate; Famine 14-20 upkeep 1.05-2.5, frozen from Severe |
| CR-10 | 56-61 | Military: Guild Wars ⚔️ 10-14d (rewards x0.4-0.8, rival missions); Bandit Raids 🗡️ 8-14d (rewards x0.65-0.85, reputation ±50 to −100); Iron Pact ⚙️ 10-14d (hero physical x1.25, non-physical x0.90); Beast Rampage 🐺 8-12d (beast enemies +25% physical) | crisis catalog | OK | Iron Pact hero physical 1.25 / non-physical 0.90; Beast Rampage enemyCategoryMultipliers Beast physical 1.25; durations and icons match |
| CR-11 | 65-68 | Political: Dragon's Tithe 🐉 8-12d — tribute is a flat -500 gold in production, the 25% vault config exists but is unwired; ignoring damages the highest non-Barracks facility by 2 levels. Royal Levy 👑 8-12d — 15%-of-vault capped at 20,000 in data, production handler not wired | crisis catalog + tribute handler | — | |
| CR-12 | 73-80 | Supernatural: Cult of the Unseen 👁️ 12-16d (3 moral events at Moderate+); Heretic Schism ✝️ 12-18d (1 per escalation); Syzygy 🌕 10-14d (hero fire/cold/lightning x1.30, enemy same x1.15); Planar Interference 🌀 10-16d (hero fire/cold/lightning/holy/chaos x0.70); Blood Moon 🌑 10-14d (both sides chaos x1.50, holy x0.75); Necromancers Stir 💀 10-14d (undead +40% chaos) | crisis catalog | OK | Syzygy hero 1.30 / enemy 1.15 on fire+cold+lightning; Planar 0.70 across five types; Blood Moon chaos 1.50 and holy 0.75 both sides; Necromancers Stir Undead chaos 1.40; all durations and icons match |
| CR-13 | 86-93 | Four chains with cooldown reductions (Ignored/Partial): Plague->Famine 15/8, Guild Wars->Bandit Raids 12/6, Cult->Schism 10/5, Dragon's Tithe->Royal Levy 10/5; an Ignored parent starts the successor at Moderate | crisis chain data | — | |
| CR-14 | 95 | A Partial outcome halves the cooldown reduction | chain code | — | |
| CR-15 | 99 | Engaged outcomes still chain but into a Mild successor and can earn Chain Breaker; the other ten crises do not chain | chain code | — | |
| CR-16 | 109-113 | Permadeath events: Plague/Healer's Sacrifice (highest morale -> most bonds -> highest level, no class filter); Cult/Inquisition's Demand (lowest morale, fewest bonds, lowest level); Dragon's Tithe/Hero Tribute (Legendary hero if any, else most disposable) | permadeath event code | — | |
| CR-17 | 117-121 | Permadeath needs Critical severity, >=1 resolution mission completed, and >=2 living heroes; queued with a deadline of the crisis end day | permadeath gating | — | |
| CR-18 | 124-131 | Accept = hero permadies, crisis force-ends at Engaged, Sacrificial Lamb milestone; Refuse = hero lives, crisis continues at Critical; refusing the Tithe sets `tributeRefused` and earns Defiant Refusal; timeout defaults to Refuse | permadeath resolution | — | |
| CR-19 | 137-143 | Building damage at Ignored/Partial: Plague -> Infirmary -2/-1; Guild Wars -> Training Yard -2/-1; Cult -> Chapel -1/—; Dragon's Tithe -> highest non-Barracks facility -2/—; applied on the crisis end day, recovered only by upgrading | facility damage code | — | |
| CR-20 | 147 | Damaging the Armory triggers an automatic vault-capacity sync | armory damage handling | — | |
| CR-21 | 155 | Six crises modify combat damage and their magnitudes do not scale with severity | crisis combat modifiers | OK | the combat multipliers are identical across all four severity rows in every affected crisis |
| CR-22 | 159-163 | Final Damage = Base x Crisis Type Multiplier x Crisis Enemy-Category Multiplier, applied in sequence | combat damage pipeline | — | |
| CR-23 | 173-183 | Eight milestones with the listed conditions, each one-shot and recorded as a `crisis_milestone` Chronicle entry on every living hero | milestone code | — | |
| CR-24 | 191-197 | UI surface: announcement modal (icon, severity badge, duration, modifier summary), Chronicle entries, log icons 🔗 / 🏚️ / 💫, and no always-on HUD banner | crisis UI | — | |

## custom-dungeons.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| CD-01 | 3-11 | A bottom-nav button labelled "Workshop CD" (🗝) opens the Custom Dungeons app | bottom nav component | OK | BottomNav.tsx:24 - custom-dungeons, glyph 🗝, label "Workshop CD", beta badge |
| CD-02 | 38-42 | Editor rules: rooms may not touch, may not overlap on the minimap, entrance and exit must be reachable, pathfinding must connect them | dungeon validator | — | |
| CD-03 | 43 | The editor offers a starter menu of pre-built themed layouts | editor starters | — | |
| CD-04 | 47 | The validator runs on save and publish and blocks publishing until clean | validator wiring | — | |
| CD-05 | 59-65 | The Test Modal runs the dungeon with a simulated party and reports order, difficulty, and a room-by-room walkthrough | test modal | — | |
| CD-06 | 71 | Publishing is versioned; each publish stamps a version number | publish flow | — | |
| CD-07 | 73-77 | Publishes land as Draft, auto-promote to Public after 10 clears of the current version, forfeits excluded; re-publishing bumps the version, resets the clear count and reverts to Draft unless opted public | publish/promotion code | — | |
| CD-08 | 79 | The optional narrator-hero lock makes that hero unavailable to your own missions for 3 days | narrator lock code | — | |
| CD-09 | 81 | Once published, a dungeon is raid-only for everyone except its author | permissions | — | |
| CD-10 | 95 | Nine named starter dungeons ship as community content (Sunken Cellar, Library That Watches, Goblin Snare-Maze, Patrol Tower of Sighs, Endless Stair of the Lich, Demon's Bargain, Warden's Round, Iron Menagerie, Drowned Cathedral) | starter dungeon data | — | |
| CD-11 | 97 | Gallery cards show name, architect (or Anonymous), elegance score, observed difficulty, and a ⚔ Raid This Dungeon button | gallery UI | — | |
| CD-12 | 101 | Party eligibility is exactly `hero.state === HeroState.Ready` (`raidEligibility.ts:24`), with no level or class restrictions; narrator heroes stay out for 3 days | `raidEligibility.ts` | — | |
| CD-13 | 105 | The raid orchestrator is a 9-state machine | CD raid orchestrator | — | |
| CD-14 | 107 | Rewind tokens default to 2 remaining of 3 max (`cdRaidData.ts:182,220`), do not refill within a run, and carry no scoring penalty | `cdRaidData.ts` | — | |
| CD-15 | 117-123 | Class session abilities: Mage Dispel 2 (magical hazards), Cleric Purify 2 (cursed), Rogue Disable 3 +1 per living Ranger, Necromancer Clear 2 (re-arms after 3 turns) and Send Undead 2 (adjacent room), Ranger Perception passive +1 sight hop, Warrior none | CD ability data | — | |
| CD-16 | 127-131 | Trauma: hazard HP damage permanently reduces effective max HP for the run, heals clamp to the reduced cap, trauma equal to original max HP fells the hero, and it resets only when the run ends | CD trauma code | — | |
| CD-17 | 135-137 | Axis shifts persist on cleared, wiped and forfeited runs; the right-rail HUD shows this run's deltas only, committing at run end | CD axis handling | — | |
| CD-18 | 139 | Custom Dungeons use their own moral event catalogue, placed by the architect | CD moral events | — | |
| CD-19 | 143-149 | Patrols have a default sight range of 1 hop; ambush offers Fight / Hide / Flee; Hide rolls a 5% base plus mood and diminishing per-Ranger bonuses clamped to 5-60%; Flee needs a previous room and patrols still tick | patrol + ambush code | — | |
| CD-20 | 151 | Combat noise redirects patrols within a configurable BFS range toward that room | patrol noise code | — | |
| CD-21 | 155 | First clears pay gold + XP via `computeFirstClearGold` / `computeFirstClearXp` (`cdRaidRewards.ts:64-77`) using `MISSION_GOLD_RANGES` for observed difficulty scaled by average party level; repeat clears pay nothing; the leaderboard ranks each player's best cleared session, top 10, not gated on first clear | `cdRaidRewards.ts` | — | |
| CD-22 | 157 | A banned SteamID is removed from per-dungeon boards, monthly League standings and the Hall of Notorious | `custom-dungeons/routes.js` ban filters | — | verified 2026-08-18 |
| CD-23 | 163 | The elegance score is display-only and affects nothing load-bearing | elegance code | — | |
| CD-24 | 167-175 | The League rotates three metrics monthly — Elegance (decisions), Efficiency (attempts), Speed (turns), all lower-is-better (`cdLeague.ts:128-138`) | `cdLeague.ts` | — | |
| CD-25 | 177-179 | Seasons page shows monthly standings, Hall of Notorious and a legacy archive with no themed rotations; Watcher Journal is a sortable log browser | `CdSeasonsPage.tsx`, `CdWatcherPage.tsx` | — | |
| CD-26 | 185-195 | Architect rewards pay gold + reputation for other players' clears including repeats, claimed on login, never for wipes or your own tests; "fame decay" is dungeon archival after 60 unraided days (`cdObservedDifficulty.ts:103-118`) and rewards are not time-scaled | `cdObservedDifficulty.ts`, architect reward code | — | |
| CD-27 | 197 | The Architect Page shows published dungeons, lifetime rewards, recent clears with raider names, and seasonal standing | architect page UI | — | |

## passive-tree.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| PT-01 | 3 | The tree contains 354 nodes in a hexagonal web connecting all six classes | passive tree data | OK | PassiveTreeDataV3.ts holds exactly 354 node ids and PassiveTreeLayout.ts:141 accounts for 354 slots |
| PT-02 | 5 | Heroes spend one passive point per level and have allocated roughly a quarter of the tree by level 100 | point grant + node count | — | |
| PT-03 | 13-19 | Five node types with max levels: Start 1, Travel 1 (+5 to a chosen stat), Minor 5, Notable 3, Keystone 1 | node type definitions | OK | maxLevel distribution: 218 nodes at 1 (176 travel + 36 keystone + 6 start), 100 notables at 3, 36 minors at 5 |
| PT-04 | 25-32 | 1 point per level from level 1; the first is auto-spent on the class start node; totals 1/10/50/100 with 0/9/49/99 free | point allocation code | — | |
| PT-05 | 44-51 | Start node bonuses: Warrior +50 STR/+100 dmg/+20% phys; Mage +50 INT/+50 dmg/+20% spell; Rogue +50 DEX/+80 dmg/+20% phys; Ranger +50 DEX/+50 dmg/+20% projectile; Cleric +40 INT/+40 STR/+50 dmg/+20% spell; Necromancer +50 INT/+50 dmg/+20% chaos | start node data | OK | all six start blocks match the guide: Warrior 50 STR/100 dmg/20% phys, Mage 50 INT/50/20% spell, Rogue 50 DEX/80/20% phys, Ranger 50 DEX/50/20% projectile, Cleric 40 INT/40 STR/50/20% spell, Necromancer 50 INT/50/20% chaos |
| PT-06 | 60-99 | Eighteen branches, three per class, with the listed names and focuses | branch data | — | |
| PT-07 | 90 | No `holy_damage` stat exists in the passive tree; Cleric branches all scale with `spell_damage` | passive stat ids | — | |
| PT-08 | 109 | Mid-path keystones have bypass paths costing 0-1 extra points; the `_d` suffix appears on 54 detour-helper nodes across the 18 branches | node ids with `_d` | OK | exactly 54 ids match the `_dN` detour pattern, spread across all 18 branch prefixes |
| PT-09 | 115-117 | Keystone penalty patterns by class, with the stated exceptions (Berserker Mastery penalises max life, Frost Mastery crit chance, Trickster Mastery crit) | keystone data | OK | Berserker Mastery penalises maximum_life and Frost Mastery critical_strike_chance, as the guide states |
| PT-10 | 120-127 | Keystone values: Tank +22% armor/+30% life/-20% dmg; Berserker +19% phys/+30% leech/-20% life; Sharpshooter +57% proj/+30% crit/-20% life; Lich +49% chaos/+39% spell/-25% life; Summoner +66% minion dmg/+33% minion life/-25% dmg; Frost +43% spell/+30% mana/-15% crit; Inquisitor +33% spell/+30% crit/-15% dmg | keystone data | OK | all seven keystone stat blocks match the guide value for value |
| PT-11 | 129 | Each class has two keystones per branch, one at the end of each branch path | keystone layout | OK | wording is self-contradictory; check counts; 36 keystones across 18 branches = 2 per branch |
| PT-12 | 135-139 | Travel nodes grant a choice of +5 STR, +5 DEX or +5 INT | travel node data | — | |
| PT-13 | 141 | The tree contains 176 travel nodes | node type counts | OK | 176 nodes of type travel |
| PT-14 | 147-156 | Six cross-class bridges as diamond chains of travel nodes: Warrior-Mage, Mage-Rogue, Rogue-Cleric, Cleric-Ranger, Ranger-Necromancer, Necromancer-Warrior | bridge node data | — | |
| PT-15 | 158 | Bridging into another region unlocks that class's notable and keystone nodes | pathing rules | — | |
| PT-16 | 164 | The Core Hub is a ring of twelve slots equidistant from every class, six of which are mana stat nodes | core hub data | OK | 12 core hub slots with six mana nodes generated in PassiveTreeRemapData.ts:509-530 |
| PT-17 | 170-173 | Hub slots 2, 6, 10 are Mana Wellspring (+mana regen %, 5 levels); slots 4, 8, 12 are Mana Efficiency (-mana cost %, 5 levels), alternating | core hub data | OK | hub indices 1,5,9 are Mana Wellspring (mana_regen 1.5%, maxLevel 5) and 3,7,11 are Mana Efficiency (mana_cost_reduction 1.5%, maxLevel 5) - the guide numbers them 1-based as slots 2/6/10 and 4/8/12, which is consistent |
| PT-18 | 179-182 | Inner tails: Deep Wellspring (regen + flat max mana) behind regen hubs, Practiced Casting (cost reduction) behind cost hubs | hub tail nodes | OK | Deep Wellspring = mana_regen 3% + 15 flat mana; Practiced Casting = mana_cost_reduction 3% |
| PT-19 | 187-190 | Outer tails: Vast Reservoir (regen + larger flat mana) and Arcane Mastery (master-level cost reduction) | hub tail nodes | OK | Vast Reservoir = mana_regen 3% + 24 flat mana; Arcane Mastery = mana_cost_reduction 3% |
| PT-20 | 194 | A full mana lane (hub -> inner tail -> outer tail) is roughly seven points | node levels along the lane | — | |
| PT-21 | 202-206 | Three modifier types: flat (added), percent (additive with other percents), multiplier (multiplicative) | stat aggregation code | — | |
| PT-22 | 212-214 | Full respec is available any time and returns every point except the start node, resetting travel stat choices; partial respec removes one level at a time and must preserve connectivity | respec code | — | |
| PT-23 | 220-225 | Four pathing rules: start from the class node, adjacent-only allocation, no orphans on deallocation, one independent tree per hero | allocation validation | — | |
| PT-24 | 232 | Each cross-class bridge costs 3-4 travel nodes of pure routing | bridge node counts | — | |

## skills.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| SK-01 | 11, 98-101 | Equipped gems receive 10% of the hero's earned XP on each hero XP gain (`Hero.ts:1497-1508`), never per use; gem XP requirement is 100 x 1.08^level; max gem level 100 | `Hero.ts` gem XP | — | |
| SK-02 | 16-19 | Two gem types: Active (●) and Support (◇) | gem type enum | — | |
| SK-03 | 25-32 | Colour gates sockets, not stats: `RED_ACTIVE_GEMS` holds attack, spell, minion, holy and ranged-DEX gems; `GREEN_ACTIVE_GEMS` holds guards, warcries, movement, healing, utility; `BLUE_ACTIVE_GEMS` is empty; white sockets accept any gem and roll at 3% | gem catalogues | — | |
| SK-04 | 42-51 | Max sockets by slot: weapon 6, body armor 6, helmet 4, gloves 4, boots 4, off-hand 3, amulet 1, ring 1 | socket generation code | KO | getMaxSockets (GemSocket.ts:268) has these values but only gates the uncalled generateRandom; live socket count is capped by RARITY (Item.ts), not by slot |
| SK-05 | 65-67 | Socket chance 30% + itemLevel x 2% capped at 90%; white socket 3%; link chance 20% + itemLevel x 1% capped at 70% | socket generation code | KO | live socket roll is 20% + level x 1% cap 90% (Item.ts:1041); the 30%+2% figure is from uncalled GemSocket.generateRandom. White 3% is correct (ItemForge.ts:24). Link chance roll never runs - ItemForge.ts:61 links every socket into one group |
| SK-06 | 85-90 | Placement rules (`ItemForge.ts:canSocketGemIntoGroup`): actives need an empty group, supports must pass the active's `canBeSupported` tag check, removing an active cascades every support back to the hero's gem inventory, duplicate supports stack additively | `ItemForge.ts` | — | |
| SK-07 | 110, 117-120 | Mana cost = Base Mana x (1 + (Level - 1) x 0.02), i.e. +2% per level, roughly 3x base at level 100 | gem mana cost code | — | |
| SK-08 | 132-138 | Attack gems: Greater Cleave, Ground Slam, Heavy Strike, Flicker Strike, Viper Strike, with the stated types | gem catalogue | — | |
| SK-09 | 146-150 | Ranged gems: Split Arrow, Barrage, Tornado Shot (primary + one secondary projectile, lower per-hit damage) | gem catalogue | — | |
| SK-10 | 158-163 | Spell gems Pyroblast, Arc, Freezing Pulse, Essence Drain live in the red catalogue despite requiring INT | gem catalogue | — | |
| SK-11 | 165 | Spell gems scale off the linked weapon's base damage via `base_damage_percent` plus their own flat damage; multi-projectile gems take a per-projectile damage penalty | skill damage pipeline | — | |
| SK-12 | 171-174 | Minion gems Raise Zombie and Summon Skeleton are red and require INT | gem catalogue | — | |
| SK-13 | 182-187 | Healing gems: Healing Light carries the `aoe` tag and hits all allies without the Guardian ascendancy; Rejuvenation (HoT); Divine Shield; Life Tap (Necromancer, 5-turn percent-life regen, free to cast) | gem catalogue | — | |
| SK-14 | 195-200 | Guard gems: Molten Shell, Frost Shield, Bone Armor, Arcane Barrier | gem catalogue | — | |
| SK-15 | 206-211 | Warcries: Enduring Cry; Rallying Cry buffs party damage additively with Courage blessing and OathSworn bond and removes only its own contribution on expiry; Steady Aim (Ranger, 4 turns); Unholy Vigor (Necromancer) | gem catalogue + buff expiry code | — | |
| SK-16 | 219-223 | Movement gems: Evasive Roll, Smoke Bomb (percentage damage absorb), Shadow Step | gem catalogue | — | |
| SK-17 | 229-233 | Holy gems: Holy Bolt (bonus vs undead), Divine Wrath, Righteous Fury | gem catalogue | — | |
| SK-18 | 245-256 | Damage support mana multipliers: Increased Damage 1.15x, Added Fire/Cold/Lightning 1.2x, Increased Critical Strikes 1.3x, Increased Critical Damage 1.25x, Concentrated Effect 1.4x, Multistrike 1.6x (`extra_attack_chance`), Spell Echo 1.4x (`extra_cast_chance`), Melee Splash 1.3x | support gem data | — | |
| SK-19 | 262-269 | Utility supports: Life Leech 1.25x (2% baseline scaling with level), Mana Leech 1.2x, Increased Duration 1.1x, Increased Healing 1.2x, Minion Damage 1.3x, Minion Life 1.15x | support gem data | — | |
| SK-20 | 275-281 | Defensive supports all 1.1x: Armor Reinforcement, Evasion Boost, Energy Shield Boost, Damage Reduction, Thorns | support gem data | — | |
| SK-21 | 299 | `Concentrated Effect` replaced the removed `Increased Area` template and no `Stun` support template exists | support gem catalogue | — | |
| SK-22 | 313 | Gem socketing has no class restriction; STR/DEX/INT requirements are the only gate | socketing validation | — | |
| SK-23 | 322-328 | Gem sources: dungeon drops Common-Rare, boss drops Uncommon-Epic, quest rewards specific gems, Guild Shop basic gems, world bosses Legendary | drop tables | — | |
| SK-24 | 332-336 | Heroes hold a personal gem inventory; gems can be stored, traded between heroes, and sold | gem inventory code | — | |

## raids.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| RD-01 | 14-16 | Raids need 5000 guild reputation and a level-50+ hero; spawn chance is 5% per day rising to 10% after 30+ days without a boss | world boss spawn code | — | |
| RD-02 | 18 | A spawned boss persists 7 days; the realm draws from a pool of three and avoids the last two picks | spawn selection | — | |
| RD-03 | 26 | The board is 5 rows x 5 columns plus a Boss Arena zone, rows F / M / U / L / B front to back | `RaidBoard.ts` | — | |
| RD-04 | 28 | `MAX_HEROES_TOTAL = 15` in `RaidSetup.tsx` | `RaidSetup.tsx` | OK | MAX_HEROES_TOTAL = 15 at RaidSetup.tsx:9 |
| RD-05 | 29 | Group count is unconstrained; five default anchor zones are proposed (F3, M3, U3, L3, B3) | raid setup defaults | — | |
| RD-06 | 30 | `ZONE_HERO_CAPACITY = 5` in `RaidBoard.ts`; F1-F5 are the boss-melee zones | `RaidBoard.ts` | OK | ZONE_HERO_CAPACITY = 5 and BOSS_MELEE_ZONES = F1-F5 at RaidBoard.ts:19,28 |
| RD-07 | 34 | Group roles are `'standard' \| 'add_dps'` | raid types | — | |
| RD-08 | 46-50 | Ancient Dragon phase thresholds at 75 / 50 / 25% HP (`AncientDragon.ts:107,114,121`) | `AncientDragon.ts` | — | |
| RD-09 | 53-59 | Dragon abilities: Dragon Claw cleaves 50% onto others in the zone; Dragon Bite; Fire Bolt DoT; Fire Breath (cone); Tail Sweep (row); Wing Buffet (column); Inferno Wave (spread) | `AncientDragon.ts` | — | |
| RD-10 | 61 | The Dragon is fire-resistant and ice-weak | boss resistance data | — | |
| RD-11 | 67-71 | Lich phases at 75 / 50 / 25% (`SkeletalLich.ts:77,84,91`); Risen Champion summons every 8 turns; Heal Steal queued every 7 turns; Mass Resurrection raises wraiths on hero deaths | `SkeletalLich.ts` | — | |
| RD-12 | 79 | Heal Steal heals the Lich for 25% of MAX HP on success (`bossTuning.ts:328`), higher on Heroic | `bossTuning.ts` | KO | healFraction 0.25 is right for Normal, but Heroic LOWERS it to 0.08 (bossTuning.ts:635) - the guide says Heroic "raises this further". Heroic does raise the interrupt DC to 20 |
| RD-13 | 83 | Interrupt rolls INT + DEX vs DC 14 on Normal and DC 20 on Heroic; first success cancels the cast | interrupt code | OK | Normal interruptDC 14, Heroic 20 |
| RD-14 | 85 | The Lich has magic resist 60 vs armor 40, resists ice and dark, is weak to fire and holy | boss stat data | — | |
| RD-15 | 91-95 | Void Titan phases (`VoidTitan.ts:99,105,116`): Gaze 100-75, Fractured Mind 75-50, Spatial Phase 50-40 with forced movement every 3 turns rotating S->W->N->E, Void Implosion <=40% (`bossTuning.ts:551`, cd 7 in phase 3) | `VoidTitan.ts`, `bossTuning.ts` | — | |
| RD-16 | 103 | The Void Implosion safe zone is fixed at M2, M3, M4 (`VoidTitan.ts:239-241`) | `VoidTitan.ts` | OK | VoidTitan.ts:355 - ["M2","M3","M4"] mid row centre, no rotation. Citation drift: the guide cites lines 239-241 |
| RD-17 | 109 | Enrage at turn 250 for Dragon and Lich (`bossTuning.ts:92,257`) and turn 300 for the Void Titan (`bossTuning.ts:443`); +10% base damage per turn past threshold, additive, uncapped; x3.5 at +25 and x6.0 at +50 | `bossTuning.ts` | KO | thresholds are right (Dragon 250, Lich 250, Void Titan 300) and the +10%/turn additive shape is right, but the worked multipliers are off by one stack: stacks = turn - threshold + 1, so threshold+25 is x3.6 and threshold+50 is x6.1, not x3.5 and x6.0 |
| RD-18 | 115-123 | Wounded stacks from Cone / Row / Column cleaves only (not SpotSoak or Spread); each adds +20% to subsequent telegraph damage (x(1 + 0.2N)) and +30% to all damage taken; permanent within an attempt, reset between attempts; avoidance is positional and deterministic | Wounded implementation | — | |
| RD-19 | 127-134 | Voidmarked: +15% damage taken per stack (`VoidmarkedStacks.ts:27`), no ceiling, no decay, cleared by `clearAllVoidmarked` (`VoidmarkedStacks.ts:90`); on Heroic, Fractured Mind shared-zone hits also apply it (`RaidOrchestrator.ts:1949-1958, 2033-2037`; `bossTuning.ts:497,676`) | `VoidmarkedStacks.ts` | OK | DAMAGE_TAKEN_PER_STACK = 15 with STACK_CEILING removed (spec 186) and clearAllVoidmarked present |
| RD-20 | 140-148 | Heroic loot (`lootTables.ts:380-456`): `HEROIC_TOKEN_MULTIPLIER = 2`, `HEROIC_MATERIAL_MULTIPLIER = 2` (scales 2-4 -> 4-8, 2-4 -> 4-8, 1-3 -> 2-6), a second dedup'd item-roll pass taking an 8% named drop to ~15% effective, gold unchanged; net ~1.65x named and ~1.28x total item yield | `lootTables.ts` | — | |
| RD-21 | 154-162 | Default anchors Group 1-5 at F3 / M3 / U3 / L3 / B3; `BOSS_MELEE_ZONES` is F1-F5 | raid setup + `RaidBoard.ts` | OK | same source for BOSS_MELEE_ZONES |
| RD-22 | 168-180 | 5 order points per turn; costs: Move 0, Hold 0, Engage 1, Taunt 1 (Warrior-only, range 1 chebyshev), Interrupt 1, Disengage 1, Burst 1 (Mage/Necromancer), Standing Order 1 to set, Call Retreat 0 | order cost table | — | |
| RD-23 | 183-185 | One order per group per turn with the latest winning; movement consumes the hero's action | order resolution | — | |
| RD-24 | 191 | Raids run in real time on a 6-second base tick (`BASE_TICK_MS = 6000` in `RaidStateProvider.tsx`), with a 1/2x-1x-2x-4x speed selector and a Pause control (`RaidPhaseHeader.tsx:285`, `data-test-id="raid-pause-toggle"`) also bound to Space; End Turn was removed in spec 130 | `RaidStateProvider.tsx`, `RaidPhaseHeader.tsx` | — | |
| RD-25 | 206 | Turn 0 is setup-only and returns before combat, telegraphs, spawns or status ticks (`RaidOrchestrator.ts:690-694`) | `RaidOrchestrator.ts` | — | |
| RD-26 | 208 | Telegraphs are announced one turn before they resolve | telegraph scheduling | — | |
| RD-27 | 212 | Add waves default to a 3-turn cadence; `BOSS_ADD_CONFIG` (`RaidOrchestrator.ts:2019-2024`) gives Dragon 3 Fire Whelps, Lich 2 Skeletons, Void Titan 2 Wraiths, with a bare Goblin fallback | `RaidOrchestrator.ts` | — | |
| RD-28 | 214-218 | Ground effects persist and stack on a tile; unspent order points do not carry over; Call Retreat is outside the budget (`data-test-id="call-retreat-btn"` in `RaidTurnControl.tsx`) | orchestrator + `RaidTurnControl.tsx` | — | |
| RD-29 | 228-238 | Victory / Wipe / Retreat are the three outcomes; fallen heroes end at 0 HP in Ready state with no injury, infirmary time or permadeath risk, and keep their equipment; retries are unlimited until the 7-day timer, each building a fresh orchestrator | raid end handling | — | |
| RD-30 | 246-250 | Victory rewards: Dragon 8,000-12,000g / 5-10 tokens / Ancient Dragon Scale; Lich 10,000-15,000g / 6-12 / Phylactery Shard; Void Titan 12,000-18,000g / 8-14 / Reality Fragment | `lootTables.ts` | — | |
| RD-31 | 252 | Ancestral tier-set pieces roll at 20% each; first kill unlocks all recipes gated behind that boss; later kills roll 15% Epic and 5% Legendary recipe scrolls; world bosses roll 8% Legendary only; duplicates convert to 10,000g / 100,000g | recipe drop code | OK | same table confirms 15% Epic / 5% Legendary on raids and 8% Legendary only on world bosses |
| RD-32 | 254 | Raid currency rates: each Ichor 6%, Salt of Cleansing and each Portent 4%, Cursed Sigil 3%, ungated by difficulty; world bosses 5% Sigil only | `currencyDrops.ts` | — | edited this session |
| RD-33 | 260-269 | The Raid Tokens tab appears after the first token and stocks 26 items in six sections at the listed token prices, all tier-set pieces Ancestral | vendor data | — | |
| RD-34 | 271 | Set bonuses trigger at 2, 4 and 5 pieces; Dragon funds Wyrmscale, Lich funds Litany of Bones, Void Titan funds Cosmic Discord, Titanslayer draws from all three (weapon+helm Dragon, armor+accessory Lich, sigil Void Titan) | `EquipmentSets.ts` + token drop mapping | — | |
| RD-35 | 275-281 | Exact set bonus values for Wyrmscale, Litany of Bones, Cosmic Discord and Titanslayer at 2/4/5 pieces (`EquipmentSets.ts`) | `EquipmentSets.ts` | — | |
| RD-36 | 287-291 | Three stages (Setup, Board, Results) and the described board layout | raid UI | — | |
| RD-37 | 293-296 | Hotkeys M / H / B / T / I / E for orders, 1 / 2 / 3 to select group, Space pause, Esc cancel (`RaidOrderBar.tsx:279`) | `RaidOrderBar.tsx` | — | |
| RD-38 | 298 | Phase-header view tabs switch between Live, Telegraphs and Storyboards | raid phase header | — | |
| RD-39 | 304 | Aggro-switch banner: dark-red, ⚠, "Aggro -> {hero}", auto-dismiss after 3s with timer restart, detected client-side from the combat log (`RaidStateProvider.tsx:457`), stdout `[AggroSwitch]` line, no banner on first lock-on | `RaidStateProvider.tsx` | — | |
| RD-40 | 310 | The Raid tab sits in the Leaderboard screen with six boards (3 bosses x Normal/Heroic), top 25 by fewest turns, tiebreak lower wallclock then earlier occurrence, columns `# / Player / Turns / Time / Survivors / Version`, own row gold "(you)", plus per-boss tabs, sortable columns and an Attempts column (spec 167) | `Leaderboard.tsx` | — | |
| RD-41 | 312 | Steam / Mobile / Web chips; the screen opens on Steam for Steam builds and Web otherwise; the Raid view offers only Steam and Web; the server files submissions by verified Steam ticket first, then declared mobile, else web | `Leaderboard.tsx`, `route-helpers.js` | — | verified 2026-08-18 |
| RD-42 | 314 | Opening the Leaderboard registers a cloud token if absent, submits stats and awaits that before reading the board; Steam builds wait for the persona first | `CloudService.ts`, `Leaderboard.tsx` | — | verified 2026-08-18 |
| RD-43 | 316-318 | Bans key on SteamID, device or IP; all three block submission; SteamID hides rows everywhere including custom-dungeon leagues, device hides rows on the main player board, IP hides nothing; reads and cloud saves unaffected; shadow and hard flavours; lifting clears without deleting | `leaderboard-bans.js` | — | verified 2026-08-18 |
| RD-44 | 320 | `handleRaidEnd('victory')` submits `{boss, difficulty, turns, wallClockSec, survivors, partySize, appVersion, gitCommitSha, occurredAtUtc}` plus attempts; wipes and retreats are not submitted; the server keeps one row per (player, boss, difficulty) replaced only on strictly fewer turns; the same IP rate limiter applies | `Raid.tsx`, server raid routes | — | |
| RD-45 | 322 | Each launch increments `raidAttempts[bossDifficulty]` on GameState (`GameState.ts:1122`), persisted in saves, counting forfeits and wipes | `GameState.ts` | — | |
| RD-46 | 324 | The boards have no time filter; they are perpetual per-player bests | leaderboard UI | — | |

## interface.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| IF-01 | 7-11 | Main menu offers New Game, Continue, Load Game, Settings | `MainMenu.tsx` | — | |
| IF-02 | 21-25 | Top bar shows Gold, Day, Guild Rank (F through S) and Settings | `TopBar.tsx` | — | |
| IF-03 | 30-36 | Hero panel rows show portrait, name, class icon, level, state, mood, an illness badge coloured green <30 / amber 30-70 / red >70, and a per-day stable "today's thought" seeded from personality traits | `HeroRow` component | — | |
| IF-04 | 46 | Facility panel has quick links to Quarters, Market and Infirmary, and the Infirmary opens even with nobody ill | facilities quick links | — | |
| IF-05 | 57-66 | Ceremonial scene priority: Infirmary, Guild Rank Up, Legendary Item, Body Part Loss, Enemy Made, Recruit; each advances with Continue and there is no Skip | scene queue code | — | |
| IF-06 | 70-84 | Day summary section order: Heroes Lost, World Boss, Scandals, New Titles, Auto-resolved Guild Events, Quest Chain Progress, Social, Crafts Completed, On the Ward, Quarters, Elsewhere; empty sections are omitted | day summary component | — | |
| IF-07 | 90 | The Mission Board defaults to the World Map (V2) view; the legacy list is gated by `useMissionBoardV2` in `GameSettings` (default true, read at `GuildLedgerApp.tsx:607`) with no in-game toggle | `GuildLedgerApp.tsx` | — | |
| IF-08 | 103-107 | The Mission Board filter strip has three buttons — All / Normal / Heroic 🔥 (`MissionBoard.tsx:390-392`) | `MissionBoard.tsx` | — | |
| IF-09 | 111 | Quest chain missions carry a 📜 badge with a chain/step tooltip | mission board rendering | — | |
| IF-10 | 115 | Hazards appear on 2★+ missions, name the resolving class, and render in the Contract Details side panel (`MissionBoard.tsx:826-840`); map pins carry only 📜 and 🔥 | `MissionBoard.tsx` | — | |
| IF-11 | 123 | The supervised/unsupervised choice and Command Point spending live on the dungeon menu, not the Mission Board | dungeon menu | — | |
| IF-12 | 127-135 | Quest Log glyph ❡ in the Top Bar (`TopBar.tsx:134`); 7 story chains (ranks F->B), 7 class chains (Mage has Arcane Thesis rank E + lvl 25 and Archmage's Thesis rank C + lvl 40), weekly bounty with a 7-day countdown first rolling on day 1 (`QuestChain.test.ts:794-809`) | `TopBar.tsx`, chain catalogs | OK | 7 story and 7 class chains; Arcane Thesis at rank E/level 25 and Archmage Thesis at rank C/level 40 |
| IF-13 | 137 | The Quest Log enumerates only unlocked chains, falling back to empty-state copy (`QuestLog.tsx:113-148`) | `QuestLog.tsx` | — | |
| IF-14 | 147-152 | Gems tab shows equipped gems and sockets, gem levels and XP, skill proficiency, and drag-to-socket management | hero details gems tab | — | |
| IF-15 | 158-164 | Social tab shows per-hero trust, bond labels, current modifier and active thoughts; mood, traits and needs live on the main hero panel instead | hero details social tab | — | |
| IF-16 | 168-175 | Career tab leads with Purse & Ambition (holdings, daily earnings, savings progress bar with a "saved enough" marker and Bought / Enough to leave line, plus a "Things they saved for" list), then mission history, veteran rank, monster knowledge and lifetime combat stats | hero details career tab | — | |
| IF-17 | 179 | Chronicle tab carries an unread badge when a new entry has arrived | chronicle tab | — | |
| IF-18 | 183-190 | Background tab holds Origin, four life paragraphs, Marks of a Life, and lifecycle Traits | background tab | — | |
| IF-19 | 192 | Paragon and Trials tabs render unconditionally for every hero (`HeroDetails.tsx:741-756`) with no level-100 or ascendancy gate at the tab strip | `HeroDetails.tsx` / `HeroDetailTabs.tsx` | — | tabs were extracted to HeroDetailTabs.tsx in spec 355 |
| IF-20 | 198-210 | Combat screen shows turn order with the current actor highlighted, both factions with health, and status effects | combat UI | — | |
| IF-21 | 214 | Combat is AI-driven: no per-hero Attack/Skill/Defend/Flee buttons; `Combat.selectBestSkill` picks skills from tactical presets, and the `CombatActionType` enum is consumed by AI, not clicks | `Combat.ts` | — | |
| IF-22 | 222-228 | Command Points are a dungeon-exploration resource shown on the Dungeon screen, not the combat panel | dungeon UI | — | |
| IF-23 | 236-262 | Dungeon map shows fog of war, room type icons, current position and connections; room types are Entrance, Combat, Treasure, Trap, Rest, Event, Shop, Boss, Secret, Stairs, Exit | dungeon room types | — | |
| IF-24 | 268 | The Vault offers six filters — All / Weapons / Armor / Accessory / Consumables / Materials (`Vault.tsx:75-82`) — plus bulk actions | `Vault.tsx` | — | |
| IF-25 | 272-278 | Item actions are Equip, Sell, Salvage (the latter two with bulk-mode toggles); enchanting is not a vault action and lives at the Enchanting Table | vault actions | — | |
| IF-26 | 306 | There is no global Escape handler in ui-next; Escape is scoped to the Raid Test Sandbox, the RaidSetupV2 rename input and the Custom Dungeon editor | ui-next key handlers | — | |
| IF-27 | 308 | Right-click handlers exist in Mission Board, Passive Tree and Dungeon Menu only | those scenes | — | |
| IF-28 | 330-346 | Settings: Audio master/music/SFX 0-100; Display resolution dropdown (1280x720 / 1600x900 / 1920x1080 / 2560x1440, Electron only) and fullscreen toggle; Gameplay Skip Intro Video, Show Advisor Tips, Online Features | settings component | — | |
| IF-29 | 350 | A Credits entry rolls a cinematic end-credits reel over the intro backdrop, pausing on hover and dismissed by Escape or backdrop click | credits component | — | |

## ascendancy.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| AS-01 | 3 | Each class has 2-3 ascendancy paths; 14 paths in total across six classes | ascendancy data | — | |
| AS-02 | 9-14 | Trials fire at hero levels 25, 50, 75 and 100, granting one point each | trial gating | — | |
| AS-03 | 16 | Trial targets are solo tower floors 10, 15, 20 and 25 respectively | trial config | — | |
| AS-04 | 20-24 | Each ascendancy has 10 nodes — 1 mandatory start plus three branches (A/B/C) of 3 — and heroes earn 4 points total | ascendancy tree data | — | |
| AS-05 | 38-48 | Champion: start "Defender's Stance" +100 armor and +1000% threat; A Fortify +5% max HP -> 1% HP regen/turn -> +10% damage reduction; B Riposte +1 taunt duration -> 100% counter-attack on every hit taken -> +1 intervene; C Shield +1 Shield Wall duration -> +50 armor -> Shield Wall heals 10% HP; retains Taunt and Shield Wall | ascendancy data | — | |
| AS-06 | 60-68 | Berserker removes Taunt and Shield Wall; start +86% physical, +15% damage, +10% crit, +20% rage damage per 5% HP missing; branches as tabulated (bleed, leech, execute with 5% instant kill) | ascendancy data | — | |
| AS-07 | 80-88 | Gladiator removes Taunt and Shield Wall; start +69% physical, +29% damage; branches Multi-Strike (15% -> 35% double, 10% triple), Dual Wield (+20% dmg, +50% crit dmg, offhand 100%), Counter (50% -> 100% chance, +300% crit damage on counters) | ascendancy data | — | |
| AS-08 | 104-112 | Assassin: start +20% crit, +50% physical, +15% DEX; branch A crit nodes each add +10% damage taken; B first-hit nodes; C execute with 10% instant kill | ascendancy data | — | |
| AS-09 | 124-133 | Trickster: start +10% crit damage, +45% physical, +10% damage, +15% DEX; A venom; B party damage +5/+10/+12% enemy damage taken at +10% self damage taken each; C weaken | ascendancy data | — | |
| AS-10 | 145-152 | Deadeye branches: crit chance +10/+15/+25%; crit damage +15/+25/+40%; headshot 10% -> 25% total at 2x -> 2.5x damage | ascendancy data | — | |
| AS-11 | 162-170 | Raider: start "Professionally Nosy" +35% damage and +14% physical; A materials +25/+50/+100%; B item drops +10/+20/+30%; C magic find +10/+15/+20 | ascendancy data | — | |
| AS-12 | 180-190 | Pathfinder: start allies +30% crit damage; A initiative (always act first via +10M initiative, first hit 1.5x, Hunter's Mark +10% ally crit damage); B debuffs; C party buffs; start + Hunter's Mark total +40% ally crit damage | ascendancy data | — | |
| AS-13 | 202-210 | Elementalist: start +10% crit, +150% damage; branches fire / lightning / ice as tabulated | ascendancy data | — | |
| AS-14 | 218-226 | Occultist: start +180% damage and skills apply weaken; branches weaken / chaos / drain as tabulated | ascendancy data | — | |
| AS-15 | 238-246 | Guardian: start +20% healing effectiveness; A heal power with Chain of Grace bounce; B party damage reduction -10/-15/-25%; C shields | ascendancy data | — | |
| AS-16 | 256-272 | Paladin replaces Heal and Prayer of Healing with Divine Strike (120% damage) and Consecrate; start +60% damage; branches absorption / holy DPS / party as tabulated | ascendancy data | — | |
| AS-17 | 286-294 | Puppeteer: start +1 max minion, +30% minion damage, +120% damage; branches minion damage / durability / count (+1, +1, +2) | ascendancy data | — | |
| AS-18 | 304-312 | Lich: start +6% chaos, +10% life steal, +6% crit, +42% damage; branches chaos / drain / crit as tabulated | ascendancy data | — | |
| AS-19 | 320-336 | The 14 class-to-ascendancy pairings listed in the recommendation table match the code's class assignments | ascendancy data | — | |

## equipment.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| EQ-01 | 7-20 | Ten equipment slots: Main Hand, Off Hand, Armor, Head, Boots, Gloves, Accessory 1-2, Consumable 1-2, with the listed class restrictions | `EquipmentSlot` enum | — | |
| EQ-02 | 28-36 | Seven rarities with min/max sockets: Common 0/1 (5% chance), Uncommon 0/2, Rare 1/3, Epic 1/4, Legendary 2/5, Mythic 3/6, Ancestral 4/7 | rarity + socket data | OK | min/max socket tables at Item.ts:1043-1063 match exactly, incl. Common 5% |
| EQ-03 | 40-47 | Bonus stats and stat multiplier by rarity: Common-Uncommon 0/1.0x, Rare 1/1.0x, Epic 2/1.2x, Legendary 3/1.5x, Mythic 4/2.0x, Ancestral 5/2.5x | item generation | — | |
| EQ-04 | 51-55 | Drop requirements: Epic needs level 40 / 3★; Legendary level 60 / 4★ / tier Rare+; Mythic level 85 / 5★ / Boss tier | drop gating | — | |
| EQ-05 | 57 | Socket count chance is 20% + item level x 1%, capped at 90% | socket roll | OK | conflicts with skills.md SK-05 (30% + ilvl x 2%) — reconcile; Item.ts:1041 `Math.min(0.9, 0.2 + level * 0.01)` |
| EQ-06 | 65-72 | Weapon types by class as tabulated (Warrior swords/axes/maces/spears, Mage staves/wands, Rogue daggers/swords/crossbows, Cleric maces/staves/swords, Ranger bows/crossbows/spears, Necromancer staves/wands/daggers) | weapon restriction data | — | |
| EQ-07 | 74 | Unarmed heroes fight with 1-3 base damage | unarmed fallback | — | |
| EQ-08 | 91-100 | Weapon progression examples: Iron Sword 8-12, Steel Sword 14-20 +2% crit, Mithril Blade 25-35 +8% crit +10 STR, Dragonslayer 40-55, Worldsplitter 70-95 +15% crit +50% crit damage; Wooden Staff 5-8 +10 mana, Arcane Staff 18-28 +50 mana, Staff of Eternity 55-80 +150 mana | weapon templates | — | |
| EQ-09 | 108-113 | Armor types by class: Plate Warrior, Mail Cleric/Ranger, Leather Rogue/Ranger, Cloth Mage/Necromancer | armor templates | — | |
| EQ-10 | 129-132 | Armor examples: Iron Plate 15/+20HP, Steel Plate 30/+40HP, Dragonplate 80/+120HP, Immortal Bastion (Mythic L68 Warrior/Cleric) 120 armor, +200 HP, +28 STR, +28 VIT, +20% to five resists (`ArmorTemplates.ts:260-274`) with no HP regen | `ArmorTemplates.ts` | — | |
| EQ-11 | 142-146 | Ring examples: Iron Band +3 STR or DEX; Silver Ring +6 stat +5% resist; Gold Ring +12 INT +20 mana; Ring of Power (Legendary L60) +25 to STR/DEX/INT/VIT | accessory templates | — | |
| EQ-12 | 154-157 | Amulets: Bone Charm +10 HP; Crystal Pendant +25 HP and +15 mana; Heart of the World (Legendary L70) +150 HP, +100 mana, +10% life steal with no auto-resurrect | accessory templates | — | |
| EQ-13 | 163-169 | Unique accessories: Ring of Shadows +15 DEX +8% crit (Rogue L30 Rare, Shadow Assassin set); Amulet of the Phoenix +80 HP +30 fire resist (L50 Epic); Band of Haste +15 DEX (L50 Epic); Charm of Fortune +35 LCK +30% gold find +20% magic find (L50 Legendary); Signet of Command +15 to all five stats (L60 Legendary) | accessory templates | — | |
| EQ-14 | 175-180 | `manaRegen` rolls on Accessory 1-2; `manaCostReduction` rolls on accessories and weapons, additive with proficiency/passives/sets/ascendancy and capped at 75% total; both scale continuously with level and rarity | affix data + mana cost cap | — | |
| EQ-15 | 190-196 | Health potions: Minor 50 HP stack 10, Health 150 HP stack 10, Greater 400 HP stack 5; auto-use default threshold 50%, adjustable in Settings -> Combat | consumable templates | — | |
| EQ-16 | 200-206 | Mana potions: Minor 30 stack 10, Mana Potion 80 stack 10; no "Greater/Superior Mana Potion" templates exist | consumable templates | — | |
| EQ-17 | 212-218 | Mana flasks: Lesser (Uncommon, 120, L20, stack 5), Mana Flask (Rare, 250, L40, stack 5), Greater (Epic, 500, L60, stack 5); auto-used below a default 30% mana threshold | consumable templates + auto-use | — | |
| EQ-18 | 224-228 | Antidote (Common, stack 10) auto-uses at the start of a poisoned hero's turn, slot 1 before slot 2, clearing poison instantly | antidote handling | — | |
| EQ-19 | 232-236 | Phylactery Elixir (Legendary, L80, stack 1) revives to full HP and mana on lethal damage, checked inside `Hero.takeDamage` before death finalises, covering attacks, DoTs and AoE | `Hero.takeDamage` | — | |
| EQ-20 | 240-248 | Elixirs are equipped passive buffs in four tiers with the listed stacks and level ranges; Legendary elixirs carry `hpRegenPct` wired into the combat regen loop rather than one-shot heals | elixir templates | — | |
| EQ-21 | 252-256 | Buff potions: Strength Tonic +10% STR, Defense Potion +15% armor, Haste Potion +8% crit chance, each lasting one combat | buff potion templates | — | |
| EQ-22 | 266-272 | Socket colours: red holds attack/spell/minion/holy/ranged actives, green holds guards/warcries/healing/movement, blue has no actives and takes blue support variants requiring INT, white is wild at ~3% | gem catalogues | — | duplicate of SK-03 |
| EQ-23 | 292-298 | Link tiers: 1-link skill only, 2-link +1 support, 3-link +2, 4-6 link +3-5 supports, 6-links only on weapon and body armor | socket link generation | KO | ItemForge.ts:61 puts every socket in ONE fully-linked group, so an N-socket item is always an N-link; there are no partial links and no slot-based 6-link restriction |
| EQ-24 | 310-316 | Dragonslayer set (Epic): 2pc +20% damage vs Dragons, 3pc +50% fire resist, 4pc Dragon's Fury 10% attacks breathe fire; pieces Dragonslayer Blade, Dragonplate Armor, Dragonscale Shield, Dragon Fang Amulet | `EquipmentSets.ts` | — | |
| EQ-25 | 320-326 | Shadow Assassin set (Epic): 2pc +15% crit damage, 3pc +20% crit chance, 4pc `assassin_ambush` first attack always crits; four listed pieces | `EquipmentSets.ts` | — | |
| EQ-26 | 330-336 | Archmage's Regalia (Legendary): 2pc +50 mana, 3pc -20% cooldowns, 4pc spells echo at 50% power; four listed pieces | `EquipmentSets.ts` | — | |
| EQ-27 | 340-346 | Crusader's Armament (Epic): 2pc +30% holy damage, 3pc +25% healing, 4pc +100% damage vs undead/demons; four listed pieces | `EquipmentSets.ts` | — | |
| EQ-28 | 354-361 | Six quality tiers with modifiers: Poor -20%, Normal +0%, Fine +10%, Superior +20%, Exceptional +30%, Masterwork +50% | quality data | OK | QUALITY_STAT_MODIFIERS -20/0/+10/+20/+30/+50 |
| EQ-29 | 369 | Enchant slots are per-template `maxEnchantSlots` (typically 1-3); the Enchanting Table scales Rune Desk -> Enchanting Altar -> Arcane Workshop -> Mystic Chamber -> Ley Nexus with `enchantPower` 1.0x-2.0x and `maxTier` 1-5 (`GuildFacilities.ts:309-313`) | `GuildFacilities.ts` | OK | values correct; citation drift - the Enchanting Table block is GuildFacilities.ts:291-295, not 309-313 |
| EQ-30 | 371 | `Item.enchantments` is a `string[]` with no named effect catalogue in code | `Item.ts` | — | |
| EQ-31 | 383-391 | Seven forges with the listed specialties | forge data | — | |
| EQ-32 | 398 | Heroes track forge usage: after roughly ten missions with a forge's kit there is about a one-in-three chance of forming a favourite; sentimental gifts can lock it in; rival-forge gear causes a daily mood drip; three critical crafting failures at a forge can trigger a boycott | forge preference code | — | |

## crafting.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| CF-01 | 18-31 | Ten crafting stations mapped to four skills as tabulated (Forge/Armory/Smelter/Lumber Mill -> Metalsmithing, Tannery/Loom -> Softcraft, Alchemy Lab/Kitchen -> Alchemy, Enchanting Table/Jeweler Bench -> Arcana) | station data | — | |
| CF-02 | 37-45 | Station levels 1-5 give time modifiers 1.0/0.9/0.8/0.7/0.6, unlock tiers Common->Legendary, and add +5 to the quality roll at level 5, uniformly across all ten stations | station level data | — | |
| CF-03 | 53-59 | Forge facility levels: Simple 1.0x, Blacksmith 1.15x, Master 1.3x +10%, Dwarven 1.5x +20%, Legendary 2.0x +30% | `GuildFacilities.ts` | OK | same as GD-31 |
| CF-04 | 63-74 | Workshop facility runs to level 10 with speeds 1.0x-4.0x and quality +5% to +60% as tabulated | `GuildFacilities.ts` | OK | same as GD-32 |
| CF-05 | 78-84 | Alchemy Lab levels 1-5: speeds 1.0/1.2/1.4/1.6/2.0 with potency +10/+20/+30% at 3/4/5 | `GuildFacilities.ts` | OK | GuildFacilities.ts:274-278 craftSpeed and potency |
| CF-06 | 88-94 | Enchanting Table levels: Rune Desk 1.0x, Enchanting Altar 1.2x, Arcane Workshop 1.4x, Mystic Chamber 1.7x, Ley Nexus 2.0x | `GuildFacilities.ts` | OK | GuildFacilities.ts:291-295 enchantPower 1.0/1.2/1.4/1.7/2.0 |
| CF-07 | 98-101 | Station unlock missions: Forge "The Wandering Smith", Alchemy Lab "Mysterious Ingredients", Enchanting Table "Arcane Secrets" | facility unlock missions | — | |
| CF-08 | 109-114 | Four crafting skills, each max level 100, governing the listed stations | crafting skill data | — | |
| CF-09 | 118-125 | Skill bands unlock recipe tiers with success rates 70/80/85/90/95/100% and quality bonuses +0/+5/+10/+15/+20/+30% | crafting formulas | OK | SKILL_LEVEL_EFFECTS matches tier access, success rates 70/80/85/90/95/100 and quality bonuses 0/5/10/15/20/30 |
| CF-10 | 131-139 | Passive combat buffs by skill band: Metalsmithing physical damage, Softcraft armor, Alchemy max HP and HP regen, Arcana intelligence, at the tabulated percentages; nothing below level 21; multiple skills stack additively | crafting passive buff code | — | |
| CF-11 | 143 | Crafting XP per level is `100 x level`, totalling 505,000 from 1 to 100 | crafting XP curve | OK | getCraftingXpForLevel = 100 x level; sum 1..100 = 505,000 |
| CF-12 | 148-163 | Craft XP = Base x 100 + Item Level x 20 with tier bases 1/2/5/10/20; Exceptional quality gives +50% XP | crafting XP code | OK | CRAFTING_XP_BASE 1/2/5/10/20 and base*100 + level*20; all three worked examples reproduce. Omission: Masterwork also gets the +50% XP, not just Exceptional |
| CF-13 | 185-191 | Base craft times by tier: 2 hours, 6 hours, 1 day, 3 days, 7 days (10,080 min) | recipe duration data | OK | BASE_CRAFTING_TIME 120/360/1440/4320/10080 minutes |
| CF-14 | 193-196 | Time modifiers: station level -10% per level above 1, crafter skill -1% per 5 levels (skill/500), assistant -20% | craft duration formula | — | |
| CF-15 | 200-204 | Each station takes 1 primary crafter (full XP) and 1 assistant (+20% speed, no XP) | assistant handling | — | |
| CF-16 | 210-217 | Quality roll bands: 1-10 Poor -20%, 11-30 Normal +0%, 31-60 Fine +10%, 61-85 Superior +20%, 86-95 Exceptional +30%, 96-100 Masterwork +50% | quality roll code | OK | QUALITY_THRESHOLDS and QUALITY_STAT_MODIFIERS match exactly |
| CF-17 | 219-224 | Roll modifiers (`crafting/system.ts:703`): skill level adds directly, station quality bonus adds, skill 100 guarantees 50+, `extraQualityBonus` is fed only by the Master Artisan title (+10), no assistant quality bonus | `crafting/system.ts` | OK | system.ts:875-882 - qualityBonus = skill band bonus + skill level + station bonus + extraQualityBonus, and level 100 clamps the roll to >= 50 |
| CF-18 | 230-237 | Failure outcomes: Partial Fail returns no item, refunds 75% of materials and grants 50% XP; Full Fail returns no item and refunds 50%; Critical Fail loses everything and damages the station | craft failure code | KO | partial refunds ceil(qty x 0.75) and full refunds floor(qty/2), but CRITICAL also refunds floor(qty/2) and nothing damages a station - the "all materials lost, station damaged" line is only a flavour string (system.ts:968). Also, the 50% XP grant applies to every failure type, not just partial |
| CF-19 | 245-259 | Sell Value = floor(Material Cost x 1.3 + Gold Cost x 0.5 + Quality Bonus) with quality bonuses 0/0/+10/+20/+30/+50% and tier sell anchors 100 / 1,000 / 10,000 / 100,000 / 1,000,000g | sell value formula | OK | calculateCraftedSellValue and MATERIAL_SELL_ANCHOR match the guide exactly |
| CF-20 | 269-275 | All Common recipes are unlocked at guild creation; Uncommon and Rare are researched; Epic and Legendary are drop-only at the listed rates | recipe unlock code | — | |
| CF-21 | 277 | Some recipes unlock on a raid boss's first kill; `QuestChain.unlockRecipe()` also exists (`crafting/system.ts:462`) | `GameState.ts`, `crafting/system.ts` | — | |
| CF-22 | 283-289 | Recipe scroll rates per clear: heroic dungeons 8% Epic / 2% Legendary, raids 15% / 5%, world bosses 8% Legendary only; already-known and boss-locked recipes are excluded; duplicates convert to 10,000g / 100,000g | recipe drop code | OK | RECIPE_DROP_RATES: heroic 8%/2%, raid 15%/5%, world boss 0%/8%; duplicate gold 10k/100k |
| CF-23 | 295-303 | Research: one slot per Workshop level up to 10; Uncommon costs 5,000g + 50% of recipe materials over 2 days; Rare costs 50,000g + 50% materials over 5 days; `getResearchCost` returns null for tier 4+ (`formulas.ts:200`) | `formulas.ts` | OK | getResearchSlotCount = min(10, max(1, level)) at formulas.ts:184; getResearchCost: Uncommon 5,000g/2 days, Rare 50,000g/5 days, 50% materials rounded up, null for tier >= Epic |
| CF-24 | 305 | Cancelling research refunds half the materials (rounded down) and no gold | research cancel code | — | |
| CF-25 | 307 | Completed research grants 50% of equivalent craft XP (floored) to the highest-skilled hero in that skill, with no assignment needed | research completion code | — | |
| CF-26 | 312 | The Library's `researchSpeed` and `maxRecipeTier` metadata are unused; its real effects are +5% mission XP per level and Meditation training at L3; research slots come from the Workshop | `GuildFacilities.ts` + research code | — | |
| CF-27 | 320-339 | Five material tiers with the listed example materials and source gates (T3 level 30+, T4 level 50+ and boss drops, T5 world bosses level 70+) | material data | — | |
| CF-28 | 345-362 | Processing chains: 2 ore -> 1 ingot; 2 iron + 1 coal -> 1 steel; 3 scraps -> 1 leather; 2 leather + 1 oil -> 1 hardened; 3 cloth -> 1 fine cloth | processing recipes | — | |
| CF-29 | 369-402 | Example recipe materials and skill requirements for weapons, armor, potions and prosthetics as tabulated | recipe data | — | |
| CF-30 | 408 | The Item Workshop reroll UI does not gate by rarity or named status; `handleReroll` has no `isNamed` check | workshop reroll UI | OK | Workshop.tsx handleRerollAll guards only on isCursed and gold - no rarity or isNamed check. NOTE: cursed items are refused, which no guide mentions |
| CF-31 | 412-416 | Reroll cost = 1,000 x Rarity Tier x 2^(previous rerolls), with accept/reject preview | reroll cost code | OK | getRerollCost = 1000 x rarity x 2^rerollCount (Balance.ts:770). Omission: the Workshop discount is then applied on top |
| CF-32 | 418 | The Workshop (⚙) is a bottom-nav peer of Guild and Market, not a Guild Hall sub-screen | bottom nav | OK | BottomNav.tsx:23 - workshop, glyph ⚙ |
| CF-33 | 423 | There are ten crafting currencies | `CurrencyTemplates.ts` | — | |
| CF-34 | 429-458 | Currency effects as listed for both Powders, both Salts, the three Ichors, both Portents and the Cursed Sigil (25% each of buff / add slot / seal / destroy, all marking the item Cursed) | currency effect code | — | |
| CF-35 | 462 | Powders cost 500g each and Salt of Renewal 5,000g at the Materials Market, restocked daily and exempt from market events | market stock code | — | |
| CF-36 | 468-478 | Per-source currency rates and the difficulty gate / tower depth mapping as tabulated | `currencyDrops.ts` | — | edited this session |
| CF-37 | 480 | Abyssal Cursed Sigil soft pity: +0.05% per floor beyond 50, capped at 15% | `abyssalSigilRateWithPity` | — | |
| CF-38 | 484 | Workshop levels 2-10 cut currency gold costs by (level - 1) x 10%, capped at 90% | currency cost code | KO | formula is right ((level-1) x 10% capped 90%, formulas.ts:174) but it discounts the Workshop REROLL-ALL gold cost, not "the gold fee charged when you use a currency" - applying a currency costs no gold |
| CF-39 | 508 | Enchanted prosthetics reach 125% efficiency, exceeding the original body part | prosthetic tier data | — | |

## dungeons.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| DG-01 | 7 | The Mission Board refreshes daily | mission generation | — | |
| DG-02 | 11-17 | Five mission types (Combat, Boss Hunt, Escort, Retrieval, Exploration) with the listed reward focus | mission type data | — | |
| DG-03 | 23-32 | Six facility unlock missions (Wandering Smith/Forge, Craftsman's Legacy/Workshop, Mysterious Ingredients/Alchemy Lab, Lost Tomes/Library, Arcane Secrets/Enchanting Table, A Priest's Prayer/Chapel); they never expire and are always 2★ | facility mission data | — | |
| DG-04 | 36 | Hazards appear on 2★+ contracts with an orange ⚠️ badge naming hazard and resolving class | mission board + hazard code | — | |
| DG-05 | 48-54 | Star structure: 1★ 4 rooms/1 floor/1 day/no boss; 2★ 7/1/2/no; 3★ 12/2/3/boss; 4★ 16/3/4/boss; 5★ 20/4/5/boss | `Dungeon.ts` | — | |
| DG-06 | 58-61 | Monster level scales with the guild's highest hero level and is independent of star rating | mission generation | — | |
| DG-07 | 69-75 | Reward scaling by stars: gold 1.0/1.5/2.0/3.0/5.0x, XP 1.0/1.3/1.6/2.0/3.0x, elite chance 0/10/20/35/50% | reward scaling code | — | |
| DG-08 | 81-131 | Seven environments (Forest, Cave, Ruins, Crypt, Swamp, Tower, Volcano) with the listed enemy categories and loot focus | environment data | — | |
| DG-09 | 139-145 | Supervised expeditions: one per night, +25% XP, +20% loot quality, +20 to injury rolls, retreat option, Command Points | supervised expedition code | — | |
| DG-10 | 149-159 | Command Point actions and costs: Battle Cry 1 (+25% damage 3 turns), Shield Wall 1 (-30% taken 3 turns), Quick Heal 1 (30% max HP), Rallying Cry 2 (cleanse + heal all), Heroic Strike 2 (all crit next turn), Treasure Hunt 3 (+1 item), Tactical Retreat 3 (exit keeping loot/XP) | command point data | — | |
| DG-11 | 161 | Command Points start at 3 per floor with a maximum of 3 | command point code | — | |
| DG-12 | 169-177 | Five tactical presets (Reckless, Aggressive, Balanced, Cautious, Survival) with the described behaviour | tactical preset code | — | |
| DG-13 | 183-186 | Party size: minimum 1, maximum `Math.min(3 + stars, 8)` (`Mission.ts:354`), +5 party rating per hero beyond the third | `Mission.ts` | — | |
| DG-14 | 199-203 | Relationship effects in party: friends add damage/combat bonuses, enemies subtract and may refuse to help, lovers give large bonuses with a death penalty | combat relationship modifiers | — | |
| DG-15 | 219-233 | Eleven room types with icons as listed | room type enum | — | |
| DG-16 | 237-241 | Fog of war reveals the entrance and all rooms directly connected to it at start (`Dungeon.ts:1000-1008`); everything beyond stays dark until reached | `Dungeon.ts` | — | |
| DG-17 | 249-259 | Trap damage table: Pit 15, Poison Dart 10 + poison, Spike 20, Fire 25 + burn, Tripwire 0 (alerts), Crushing Ceiling 40, Arcane Glyph 30 + mana drain; Rogues with Detect Traps can spot them | trap data | — | |
| DG-18 | 269-275 | Hazards appear only on 2★+ missions, are listed on the contract card before commitment, and can sit in combat rooms; a 2★ dungeon carries roughly one; boss rooms, rest stops, shops and event rooms never host them | hazard placement code | — | |
| DG-19 | 279-292 | Eight hazard types with their resolving classes (`HazardCatalog.ts`), not environment-themed | `HazardCatalog.ts` | — | |
| DG-20 | 296-302 | Clean resolution uses the first matching hero in party order, costs that hero -3 to -8 mood and no HP, keeps rewards full, and prints a green narrative line | hazard resolution code | — | |
| DG-21 | 304-309 | Pushing through costs every party member 5-15% of max HP (clamped to 1 HP minimum), reduces rewards 5-20%, and still completes as Success | hazard resolution code | — | |
| DG-22 | 313-319 | Hazards are deterministic with no skill check; only party composition mitigates; items, skills, equipment, traits and Detect Traps do not bypass them | hazard code | — | |
| DG-23 | 323-327 | Clean resolution nudges +Order; pushing through nudges +Freedom | hazard axis code | — | |
| DG-24 | 331 | Resolved hazards stay resolved across save/reload because they are tied to the dungeon instance | hazard persistence | — | |
| DG-25 | 339-347 | Moral events span all seven environments, each with three options (benevolent, neutral, aggressive), gated by environment, difficulty and hero conditions | dungeon event data | — | |
| DG-26 | 351-363 | Consequence types include heal/damage, spawn enemies, grant loot (common-epic), buff for N rooms, reveal map, mood change, chronicle entry, axis shift, and consequence chains scheduled 2-30 dungeons later | dungeon event consequences | — | |
| DG-27 | 367-375 | Hero-specific triggers: trait-gated, mood-gated (thresholds typically 25-50), bond-gated, chronicle-title-gated | dungeon event gating | — | |
| DG-28 | 379-383 | Sacrifice events appear only in higher-difficulty dungeons, kill a hero permanently, and require two deliberate confirmations | sacrifice event code | — | |
| DG-29 | 387-397 | The seven listed example events exist with the described option sets | dungeon event data | — | |
| DG-30 | 405 | Axis pairs are Valor <-> Cunning, Wealth <-> Glory, Order <-> Freedom | guild axis model | — | |
| DG-31 | 415-421 | Material tiers by stars as tabulated, with Rare unlocking at L30+, Epic at L50+, Legendary at L70+ | `generateMaterialDrops` | — | |
| DG-32 | 425-433 | Loot quality factors: star rating, monster level, supervised +20% quality, LCK, secret rooms +1 tier | loot code | — | |
| DG-33 | 439-445 | Low-level drop boost: party avg 1-9 gets +1 flat roll, x1.5 drop count and an item level floor; 10-20 gets a 25% chance of +1 per base roll; 21+ baseline; stacks additively with the Criminal background bonus | `Inventory.ts` loot code | — | |
| DG-34 | 449 | Dungeon currency rates and star gates as stated | `currencyDrops.ts` | — | edited this session |
| DG-35 | 457-469 | Death save: base 50% clamped 5-95%, +15% Cleric in party, +10% supervised, +10% if the hero is a Cleric, +5% Lucky, +1% per 5 VIT (max +5%), +1% per 5 LCK (max +5%), -10% Cursed | death save code | KO | omits `hasSurvivalGear` +5%, which is in getDeathSaveChance |
| DG-36 | 473-481 | Injury severity bands: 1-30 Crippling 14d, 31-50 Severe 7d, 51-70 Moderate 5d, 71-85 Light 3d, 86-95 Scratches 1d, 96-100 None | injury roll code | OK | same source |
| DG-37 | 489-494 | Mission result multipliers: Critical Success 150/150/150, Success 100/100/100, Partial 50/70/50, Failure 0/30/-30 | mission result code | — | |
| DG-38 | 510-518 | Mission slots = Guild Hall level (2/4/6/8/10) + rank bonus (F,E +0; D,C +1; B,A +2; S +3); only one supervised expedition per night | slot calculation | OK | Guild Hall missionSlots 2/4/6/8/10 plus GUILD_RANK_SLOT_BONUS 0/0/1/1/2/2/3 |
| DG-39 | 524-536 | Prestige missions unlock at level 50 and 2,000 reputation, only the highest qualifying tier is offered, and the five tiers carry the tabulated level/reputation gates, multipliers and durations | prestige mission data | — | |
| DG-40 | 546 | Each prestige mission also rewards 5 guaranteed materials with tier scaling by hero level | prestige reward code | — | |
| DG-41 | 566-576 | Weekly heroic rotation: three tiers at 3★/4★/5★ with level offsets +0/+5/+10, random modifier and environment, base level minimum 80, reset Thursday 00:00 UTC | `WeeklyRotation.ts` | OK | duplicate of HD-13/HD-14; same source as HD-13/HD-14 |

## combat.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| CB-01 | 12 | Initiative = DEX + Random(1-10), recalculated each round | `Combat.ts` initiative | — | |
| CB-02 | 19-24 | Round phases in order: mana regen at start of turn, cooldown tick, actions in initiative order, buff/debuff tick at end | `Combat.ts` round loop | — | |
| CB-03 | 28-33 | Actions are Attack, Skill, Defend (50% reduction until next turn), Flee (30% + DEX + LCK/2) | `Combat.ts` action handling | — | |
| CB-04 | 35 | Auto-potion thresholds default 50% HP and 30% mana, both adjustable in Settings -> Combat; antidote auto-use checks slot 1 then slot 2 | auto-consume code | — | |
| CB-05 | 46 | Base Damage = (Avg Weapon Damage + Equipment Damage) x (1 + Stat Bonus / 100) | damage formula | — | |
| CB-06 | 51-59 | Stat bonus per class: Warrior STR x0.20, Rogue/Ranger DEX x0.15, Cleric INT x0.10 + STR x0.05, Mage/Necromancer INT x0.18, Paladin INT x0.12 + STR x0.12 | damage formula | — | |
| CB-07 | 64 | Class damage multipliers: Mage/Necromancer x1.25, Cleric/Warrior x1.00, Rogue x0.85, Ranger x0.80, applied at every hero-source damage point | class multiplier code | — | |
| CB-08 | 65-75 | Additional multiplicative modifiers: lifecycle damage multiplier, skill damage percent, passive tree, weapon proficiency (0-38% at level 20), skill proficiency (0-30% at level 20), monster knowledge (up to +20%), set bonuses, ascendancy, relationship (±25%), mood, damage variance ±10% | damage pipeline | OK | rollDamageVariance = 0.9 + random*0.2 |
| CB-09 | 84-85 | Crit Chance = 5% + DEX/20 + LCK/10 + bonuses; Crit Multiplier = 1.5x + bonus crit damage%/100 | crit formula | OK | Balance.ts:624 + BASE_CRIT_MULTIPLIER 1.5 |
| CB-10 | 88 | Socketed gems contribute `critical_strike_multiplier` on top of weapon and stat bonuses | gem crit handling | — | |
| CB-11 | 92 | Damage-type weaknesses multiply damage by 1.5x before armor | weakness code | — | |
| CB-12 | 96-107 | The enemy-family weakness table matches enemy templates | `Enemy.ts` templates | — | |
| CB-13 | 110 | The Fire Whelp is flagged raid-only with base damage 100 (12.5x a Goblin) and no longer rolls into mission, dungeon or Tower encounters | `Enemy.ts` | — | edited this session |
| CB-14 | 112 | Weaknesses and resistances display at Studied knowledge (20 kills); Known is 5 kills and grants a damage bonus but no resistance display | monster knowledge code | — | |
| CB-15 | 117-123 | Armor Reduction = sqrt(Armor x 2) x 100 / (50 + Enemy Level x 0.5), capped 95%, minimum damage 1; Defending and Shield Wall each give 50% reduction | armor formula | OK | Combat.calculateArmorReduction (Combat.ts:751) is sqrt(armor*2)*100/(50+enemyLevel*0.5) capped 0.95. NOTE: Balance.applyArmorReduction is a different armor/(armor+100) helper not used in the hero damage path |
| CB-16 | 127-145 | Hero resistances use Effective% = Raw/(Raw+100) x 100 over Fire, Cold/Ice, Lightning, Holy, Dark/Chaos, summed from equipment and buffs, with the tabulated values; physical has no resistance stat | resistance code | — | |
| CB-17 | 149 | Enemies use a flat 50% reduction per matching resistance tag | enemy resistance code | — | |
| CB-18 | 155-160 | Evasion Rating = DEX + LCK x 0.5 + flat bonuses; Evasion Chance = sqrt(Rating x 2) x 100 / (50 + Enemy Level x 0.5), capped 95%, using an entropy system for consistent dodge spacing | evasion code | OK | calculateEvasionRating and calculateEvasionChance match; the entropy system is real (Combat.ts:838-866) and does produce the every-other-attack behaviour the guide describes. Omission: passive-tree evasion and defensive support gems also feed the rating |
| CB-19 | 166-172 | Energy Shield = INT x 5, absorbs before HP, recharges 10% of max per round when not hit; other classes have 0 base | energy shield code | — | |
| CB-20 | 176-183 | Guardian Shield: heals grant a percentage as temporary shield, stacking across heals, absorbed before HP and ES, with `shieldAbsorbBonus` improving absorption | guardian shield code | — | |
| CB-21 | 189-195 | Heal Amount = floor(sqrt(Damage x LifeSteal% / 100 x 100)); examples 100 dmg at 10% -> 31 HP, 500 -> ~70, 2500 -> ~158; Life Leech gem grants `life_leech_percent` at 2% baseline scaling ~3% over 100 levels | life steal code | — | |
| CB-22 | 205-211 | Mana Regen = 20 flat + floor(Max Mana x Total Regen% / 100 x Class Coefficient) + equipment flat regen, where Total Regen% = 3% baseline + passive `mana_regen` + ascendancy `mana_regen` | mana regen code | — | |
| CB-23 | 217-222 | Class regen coefficients: Ranger 1.1x, Mage/Necromancer/Cleric 1.0x, Rogue 0.95x, Warrior 0.7x | mana regen code | — | |
| CB-24 | 226 | `mana_cost_reduction` stacks from equipment, passives, sets, ascendancy and skill proficiency additively, capped at 75% | mana cost code | — | |
| CB-25 | 232-238 | Five sustain levers as described, including `mana_regen` rolling on accessories only and flasks restoring 120 / 250 / 500 | affix + flask data | — | |
| CB-26 | 246-250 | Starting threat: Warrior 50, all others 10 | threat code | — | |
| CB-27 | 254-259 | Threat generation: damage x1.0 (Warriors x1.5), healing x0.5, Taunt +100,000 (`TAUNT_THREAT_BOOST`), Shield Wall +50 | threat code | — | |
| CB-28 | 263-266 | Enemy targeting: taunted enemies must attack the taunter; otherwise 50% highest threat, 25% wounded hero under 50% HP, else random weighted by threat | targeting code | — | |
| CB-29 | 274-286 | Taunt: forces all enemies onto the Warrior, 2 turns, +100,000 threat, 3-turn cooldown. Shield Wall: 50% reduction, 2 turns, +50 threat, 3-turn cooldown | skill data | — | |
| CB-30 | 300-310 | Intervene: ally takes 50% of the damage, target survives untouched, relationship boost; requires relationship 30+, a living ally, and one intervene per combat unless the Double Intervene ascendancy bonus applies | intervene code | OK | Combat.ts:5540-5560. Omission: the intervener also mitigates with VIT-based armor (vit*2 / (armor+100)), and an ally who would die from the 50% share is skipped entirely (Combat.ts:5989) |
| CB-31 | 314-326 | Intervene chances: Friend 20%, Close Friend 40%, Best Friend 60%; +20% Warrior, +25% lovers/married, +30% Life Debt; capped at 90% | intervene code | OK | tryIntervene (Combat.ts:5941-5984): 20/40/60 by relationship, Warrior +20, LifeDebt +30, Attracted/Lovers/Married +25, Mentor/BattleBrothers +15, Shield Sibling title +15, cap 90 |
| CB-32 | 330-333 | Intervene aftermath: +30 trust for the saved hero, +15 protective instinct for the savior, may trigger Inspired | intervene code | OK | Combat.ts:5572-5573 - +30 saved, +15 savior |
| CB-33 | 343-352 | Emotional states and their live effects: Inspired flag only, Panicked 40% skip (`Combat.ts:7411`), Grief flag only (`Combat.ts:7451`), Enraged and Vengeful force aggressive AI and lock target (`Combat.ts:7442-7450`), Berserk forces aggressive AI with random targeting (`Combat.ts:7438, 6859-6941`), Broken cannot act (`Combat.ts:7398`); the enum-doc damage modifiers are not applied | `Combat.ts` | OK | Combat.ts:7468-7530 confirms: Broken refuses, Panicked 40% skip, Berserk/Vengeful/Enraged set forceAggressive + target lock, Grief/Inspired only carry "handled in damage modifiers" comments and no modifier reads emotionalState anywhere else |
| CB-34 | 358-364 | Death reactions by relationship: Enemy/Nemesis -> Inspired; Lover/Married -> Berserk 40 / Broken 30 / Vengeful 30; Best Friend -> Berserk 30 / Grief 20 / Enraged 50; Close Friend -> Enraged 50 / Grief 50 | death reaction code | OK | Combat.ts:6076-6160 sets Inspired on enemy death, Berserk/Vengeful on lover death, Berserk/Grief/Enraged on best-friend death, Enraged/Grief on friend death, Vengeful on mentor death |
| CB-35 | 372-404 | Default class skills and their percentages/cooldowns for all six classes as listed | class skill data | — | |
| CB-36 | 406 | Berserker and Gladiator lose Taunt and Shield Wall; Paladin replaces Heal and Prayer of Healing with Divine Strike (120%) and Consecrate | ascendancy skill overrides | — | |
| CB-37 | 414-422 | Skill proficiency: +1.5% damage per level (max +30%), -1% mana cost per level (max -20%), -0.75% cooldown per level (max -15%); XP to next level = 50 x (Level + 1)^1.6; max level 20 | proficiency code | — | |
| CB-38 | 430-437 | Monster knowledge tiers: 5 kills Known +5%, 20 Studied +10%, 50 Expert +15%, 100 Slayer +20% and +5% crit; tracked per hero per enemy type | monster knowledge code | — | |
| CB-39 | 443-449 | DoT effects: Poison 4 turns, Burn 3 turns (30% ignite from Fireball), Bleed 3 turns at 20% of the applying hit; DoTs scale from the hit, not max HP | status effect code | — | |
| CB-40 | 453-460 | Control effects: Stun 1 turn, Freeze 1 turn (25% from Frost Nova), Shock 2 turns +20% damage taken, Vulnerable 3 turns +10% damage from all sources (applied and refreshed by Ranger Spectral Wolf bites), Weaken 3 turns | status effect code | — | |
| CB-41 | 464-470 | Elemental procs: Fire ignites for 15% of the hit per turn, Cold freezes (stun 1 turn), Lightning shocks (+20% damage taken for 2 turns) | proc code | — | |
| CB-42 | 476-482 | On-hit effects: bleed 20%/tick for 3 turns, poison 15%/tick for 4 turns, burn and poison spread to up to 2 nearby enemies, chain lightning at 50% damage | on-hit code | — | |
| CB-43 | 494-504 | Boss phase entry effects: Heal 10% HP, Enrage +20% damage permanently, Summon, Shield +50% armor permanently, AoE | boss phase code | — | |
| CB-44 | 542-556 | Relationship damage modifiers by band from Devoted +25% down to Enemy -25%, with the listed score ranges | relationship modifier code | KO | the VALUES match RELATIONSHIP_COMBAT_MODIFIERS, but Combat.ts imports getRelationshipTier from Balance.ts, which has only 9 tiers and different negative boundaries (Dislike >=-29, Rival >=-59, Enemy below). In combat, -3% Annoyed and -18% Hostile never fire: a hero at -15 takes -8% and one at -70 takes -25% |
| CB-45 | 566-570 | Ambush: enemies gain +10,000 initiative and always act first on turn 0 | ambush code | — | |
| CB-46 | 578-580 | Ambush chance is higher in Swamp and Crypt dungeons | ambush code | — | |
| CB-47 | 588-606 | Victory splits XP among living heroes and rolls loot per enemy; defeat rolls death saves for 0 HP heroes and can lose items and gold; fleeing gives no rewards | combat result code | — | |

## heroes.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| HR-01 | 7 | Six hero classes exist | `HeroClass.ts` | OK | HeroClass enum has exactly six classes |
| HR-02 | 15-21, 44-50, 73-79, 101-107, 128-134, 168-174 | Base stat blocks: Warrior 14/8/5/12/6, Mage 5/7/15/6/7, Rogue 8/15/7/6/9, Ranger 9/14/6/8/8, Cleric 7/6/12/10/8, Necromancer 5/6/14/7/8 (STR/DEX/INT/VIT/LCK) | class base stats | OK | CLASS_BASE_STATS at Hero.ts:1256-1263 match all six classes exactly |
| HR-03 | 24 | Warriors generate 1.5x threat | threat code | — | duplicate of CB-27 |
| HR-04 | 31-34, 61-63, 89-91, 116-119, 145-147, 176-178 | Ascendancy paths per class: Warrior 3, Mage 2, Rogue 2, Ranger 3, Cleric 2, Necromancer 2 | ascendancy data | — | |
| HR-05 | 56, 165 | Mage and Necromancer energy shield = INT x 5 | energy shield code | — | duplicate of CB-19 |
| HR-06 | 85 | Rogues, or heroes with KeenEyes / NimbleFingers, handle traps and locks (`Expedition.ts:221, 224`) | `Expedition.ts` | — | |
| HR-07 | 140-142 | Healing generates 0.5x threat; Cleric in party gives allies +15% death save; Divine Favor gives the Cleric +10% on their own | threat + death save code | — | |
| HR-08 | 145-148 | Base Heal = Skill Base Heal + INT + (Level + sqrt(Level)) + Max HP x 0.015, then mood ±20%, skill proficiency, Cleric magic bonus at half rate (x1 + magicDamage%/200), gem heal effectiveness, ascendancy healing nodes, and set bonuses Crusader 3pc x1.25 and Paladin 3pc x1.30 | healing formula | — | |
| HR-09 | 196-202 | Five primary stats and what each governs | stat model | — | |
| HR-10 | 208-214 | Derived stats: Max HP = 50 + VIT x 10 + Level x 10; Max Mana = 30 + INT x 5; Initiative = DEX + 1d10; UI crit chance = 5% + DEX/20 + LCK/20 (`Hero.ts:2778`); combat crit chance = 5% + DEX/20 + LCK/10 (`Balance.ts:625`) | `Hero.ts`, `Balance.ts` | OK | two different crit formulas — confirm both still exist; both formulas live: Hero.ts:3312 uses LCK/20 for the display path, Balance.ts:624 calculateCritChance uses LCK/10 and is what Combat.ts calls. Citation drift: the guide says Hero.ts:2778, actual line is 3312 |
| HR-11 | 222-228 | Quality tiers with stat multipliers and trait counts: Common 1.0x/1, Uncommon 1.08x/1-2, Rare 1.18x/2, Epic 1.32x/2-3, Legendary 1.50x/3 | hero quality data | — | |
| HR-12 | 232-238 | Recruit rarity distribution by Tavern level as tabulated | tavern recruit code | — | |
| HR-13 | 244 | Eight background tags and a four-paragraph life history rolled from a catalog of 120 events | lifecycle catalogs | OK | says 120 here; backgrounds.md says "just under two hundred" — reconcile; 120 events confirmed; 8 backgrounds in HeroBackground |
| HR-14 | 254-263 | Eight hero states with the tabulated mission/craft eligibility | `HeroState` enum | — | |
| HR-15 | 269-277 | 25 body parts across four regions as listed | body part data | — | duplicate of BG-12 |
| HR-16 | 281-283 | Injury triggers: big hit (>50% max HP in one attack) 15% chance; knocked out (0 HP) 30% chance | injury code | OK | Combat.ts:5594-5596 - big hit is >50% max HP with a 0.15 roll |
| HR-17 | 287-306 | Injury severity bands and roll modifiers: VIT +1/point, Cleric +10 each, Infirmary +5/level, supervised +20, Hardy +10, HP below 25% -20, Cursed -10 | injury roll code | OK | INJURY_THRESHOLDS and rollInjury modifiers (Balance.ts:201-245) match exactly |
| HR-18 | 310-317 | Body part states and efficiencies: Healthy 100%, Damaged 50-99%, Destroyed 0%, Basic prosthetic 50%, Standard 80%, Enchanted 125% | body part code | — | |
| HR-19 | 321-327 | Fatal injuries: brain, heart or liver destroyed, or both lungs, or both kidneys | fatal injury code | — | |
| HR-20 | 331 | Prosthetics cover the original limb/sense set plus 10 additional body-part families for 47 prosthetic types | prosthetic data | — | |
| HR-21 | 333 | Prosthetics install from the Body Status modal, only when the Infirmary tier supports the tier, with no gold surgical fee | prosthetic install code | — | |
| HR-22 | 335-341 | Prosthetic tiers: Basic 50% (Infirmary 3, Softcraft 5), Standard 80% (Infirmary 4, Metalsmithing 10), Enchanted 125% (Infirmary 5, Arcana 15+) | prosthetic data | — | |
| HR-23 | 343 | Vital organs can only receive prosthetics while Damaged, never after destruction; non-vital parts are Destroyed-only | prosthetic install rules | — | |
| HR-24 | 355-357 | Illness outcome rules: immunity 100 = recovery with possible chronic trait; lethal threshold kills only untreated strains; the six lethal illnesses named | `IllnessEngine.ts` | — | edited this session |
| HR-25 | 359 | Contagion multipliers: married x3.5, lovers/dating x3.0, best friends x2.0, shared room x2.0, same party x1.5, Plague crisis x3, Enemy/Nemesis x0.7 | `IllnessEngine.ts` contagion | — | |
| HR-26 | 361 | The contagion product is capped at 0.85 | `MAX_CONTAGION_PROBABILITY` | — | EA value; demo is 1.0 |
| HR-27 | 365 | Illness stat penalties floor at -60% across illnesses and -30% for chronic traits, applied multiplicatively; positive percentages are uncapped | effective stat code | — | |
| HR-28 | 369 | Mood modifiers are absolute, range -3 to -15, re-applied each morning with one day of life; The Glimmers gives +2 | illness catalog | — | |
| HR-29 | 375-382 | Six illness categories with the listed examples, including occupational illnesses that only fire on the matching class | illness catalog | — | |
| HR-30 | 384 | Background infection rate is roughly 4.5% per day per hero, compounded from a small per-strain roll across 23 self-seeding illnesses | `AUTONOMOUS_SEED_BASE_RATE` + catalog | — | edited this session |
| HR-31 | 386 | Environment and age multipliers: Marsh Sweats x4 in swamps, crypt/ruins/tower biases, age multipliers x1.3 / x1.8 / x2.5 past 40 / 55 / 70 for the listed illnesses; crisis multipliers as listed | illness trigger multipliers | — | |
| HR-32 | 390-398 | Named illness specifics: Glimmers +8% INT / -10% DEX; Thaumic Flu ±8% daily deterministic swings on STR/DEX/INT; The Sighs -12 mood; Watchman's Foot -5% DEX non-contagious; Backfire Fever Mage-only, lethal, leaves Wandering Mind | illness catalog | — | |
| HR-33 | 404-410 | Treatment capacity 4/6/10/16/24 by Infirmary level | `GuildFacilities.ts` | — | edited this session |
| HR-34 | 412-416 | A bed treats every illness on the hero, cutting growth 80%; tiers shave 5% per level; lethal strains grow 2.5-6/day untreated vs 0.8-2 immunity; treated growth about 1/day at level 1 | `IllnessEngine.ts` | — | edited this session |
| HR-35 | 418 | Cleric at the guild adds +25% immunity to treated heroes; VIT above 10 adds up to +50% constitution bonus | `computeTickDeltas` | — | |
| HR-36 | 420 | Skip Infirmary fills beds by illness, worst strain first, across the whole guild | `resolveAutonomousInfirmary` | — | edited this session |
| HR-37 | 422 | The Until Cured toggle pre-ticks flagged heroes up to bed count worst-first, is unticked freely, and is never cleared automatically | `Infirmary.tsx`, `Hero.keepInWard` | — | edited this session |
| HR-38 | 428-430 | Chronic traits: Long Cough -> The Wheeze, Grey Weep -> Hollow Blood, Vampire Anaemia -> Slow Blood, Chimney Ash Lung -> Ash Lung; listed on the History tab | illness catalog + UI | — | |
| HR-39 | 440-460 | Death save base 50% clamped 5-95% with modifiers: Cleric +15%, supervised +10%, Divine Favor +10%, survival gear +5%, Lucky +5%, LCK +1%/5 (max 5), VIT +1%/5 (max 5), Cursed -10% | death save code | OK | duplicate of DG-35, plus survival gear; Balance.ts:289-302 matches all eight modifiers and the 5-95 clamp |
| HR-40 | 472 | Heroes are credited their base daily wage each morning into a purse; new recruits arrive with three days' wage or 25 gold, whichever is larger | purse code | — | |
| HR-41 | 478-483 | Spend bands: Modest 5-40g, Comfortable 50-300g, Fine 400-1,500g, Extravagant 2,000-10,000g; heroes keep about a day's wage in reserve | spend band data | — | |
| HR-42 | 495 | 35% of each day's surplus goes to the dream fund, capped at 35% of daily wage, and nothing on a day spent to the reserve | dream fund code | — | |
| HR-43 | 499-505 | Dream scales and costs: Trifle 3,000-12,000g, Modest 30,000-90,000g, Substantial 200,000-600,000g, Grand 1,500,000-5,000,000g, Fable 20,000,000-60,000,000g | dream data | — | |
| HR-44 | 513-518 | Fund completion is authored per dream: most heroes buy and stay (flat mood bonus, sometimes a stat modifier, logged under Things they saved for) and then pick a new dream; a little over one in five leave | dream outcome data | — | |
| HR-45 | 522-528 | Retiring heroes are filed in the Departed archive as `Retired` and still trigger the same grief among friends as a death | retirement code | — | |
| HR-46 | 538-542 | On death the realm generates a three-paragraph obituary, preserves titles (memorial shows two chips plus +N), marks the hero Dead and buries their equipment beyond Vault reach | death handling | — | |
| HR-47 | 550-554 | The Departed archive covers banished, deserted, quest-sent, capacity-released and retired heroes, keeps titles and chronicle entries, and lives behind a Departed tab on the Chapel screen with the listed labels | departed archive code | — | |
| HR-48 | 564 | Heroes gain 3 attribute points per level; total = (Level - 1) x 3 | levelling code | — | |
| HR-49 | 570-577 | Veteran ranks by mission count with morale, reputation, damage and survival bonuses as tabulated | veteran rank data | OK | getVeteranBonuses (Hero.ts:972-986) matches morale, reputation, damage and survival columns exactly |
| HR-50 | 585-600 | Fourteen chronicle titles with the listed triggers and bonuses; titles stack | title data | — | |
| HR-51 | 610-620 | Level milestones: 1 start node, 25 first trial, 30 advanced skills, 50 second point + elite access, 75 third point, 80 heroic access, 95 Spire access, 100 fourth point + Paragon | progression gates | — | |
| HR-52 | 624 | XP required per level = ceil(2.5 x level^2.5) | XP curve | OK | getXpForLevel = ceil(100 * level^2.5 * 0.25 / 10) = ceil(2.5 * level^2.5) |
| HR-53 | 630-638 | XP retention penalties at levels 95-99: 90 / 85 / 80 / 75 / 70% | XP penalty code | OK | getXpPenalty 0.90/0.85/0.80/0.75/0.70 at 95-99 |
| HR-54 | 640-647 | XP bonuses: supervised +25%, mentor +50%, Quick Learner +25%, Library +5%/level, Guild XP Banner +10%, Paragon up to +100%, rest bonus | XP modifier code | OK | calculateFinalXp confirms supervised +25%, mentor +50%, Quick Learner +25%, Library +5%/level, paragon and rest. The Guild XP Banner +10% is not in this function - it must come from elsewhere or not at all |
| HR-55 | 653-670 | Paragon: 192,109 XP per point, 8 categories capped at 50 each with the listed per-point bonuses, 400 points to max everything | paragon data | OK | Balance.ts:24-65 - PARAGON_XP_PER_POINT 192,109, all eight caps 50, bonuses 2/2/2/4/0.5/1/5/2 |

## relationships.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| RL-01 | 7-19 | Eleven relationship tiers with the listed trust ranges | relationship tier data | OK | RelationshipTier enum (social/relationships.ts:17-33) has all 11 tiers with exactly these ranges |
| RL-02 | 27-34 | Mission social rolls (`SocialEventGenerator.ts:836-928`): failure blame 40% on failure, personality clash 25% at -2 to -6, combat bonding 15% at +3, success bonding 10% at +2 | `SocialEventGenerator.ts` | — | |
| RL-03 | 38-45 | Social event trust values: intervene +30/+15 in combat (`Combat.ts:5260-5261`) plus a Saved Life event +20/+15 (`SocialEventGenerator.ts:958-959`); shared meal +2-4; training +2-4; gift +4-6; celebration +5; sparring +1/day | `SocialEventGenerator.ts` | OK | +30/+15 in-combat trust confirmed at Combat.ts:5572 |
| RL-04 | 49-54 | Tavern activity boosts: Tactical Retreat Drill +2/pair, Battle Reenactment +3/pair, Poetry Slam +1 all pairs, Insurance Planning +1 all pairs | tavern activity data | — | |
| RL-05 | 58-63 | Negative event values: romantic rejection -6 (`:673`), jealousy -2 with -4 mood (`:546-547`), insult -3 to -5 (`:541`), hogged loot -2 to -6 (`:858-887`) | `SocialEventGenerator.ts` | — | |
| RL-06 | 73-89 | Relationship damage modifiers +5% to +25% and -3% to -25% by tier | relationship modifier code | KO | duplicate of CB-44; same as CB-44 |
| RL-07 | 93-97 | Healers skip wounded allies at relationship <= -25; single-target heals retarget or refuse; AoE heals exclude hated allies; Guardian and Champion self-heals are exempt | healer refusal code | — | |
| RL-08 | 109-115 | Lovers/Married: +15% combat stats together, death penalties, +25% intervene (`Combat.ts:5656-5660`) capped at 90% overall, cohabitation move-in worth up to +12 morale on one room's upkeep, contagion up to x7 | bond data + `Combat.ts` | — | |
| RL-09 | 117-121 | Mentor/Student: student learns faster, mentor shares XP, Vengeful state on death | bond data | — | |
| RL-10 | 123-127 | Battle Brothers/Sisters: +15% combat damage while active, enhanced intervene | bond data | — | |
| RL-11 | 129-133 | Rivals: -15% combat damage when partied together and a refusal to party once the bond locks in | bond data | — | |
| RL-12 | 135-139 | Life Debt: +30% intervene chance and automatic rescue attempts | bond data | — | |
| RL-13 | 145-152 | Oath Sworn grants +5% party damage once per mission regardless of how many pairs are deployed | oath sworn code | — | |
| RL-14 | 154-160 | Blood Feud heroes refuse to deploy together with no override | blood feud code | — | |
| RL-15 | 162 | Divorced / Ex / Ex-Partner / Scorned / Estranged / Cheated with no surviving romance separates a cohabiting pair on the next day-advance | cohabitation code | — | |
| RL-16 | 170-176 | Four arc archetypes checked in priority Romance -> Mentorship -> Rivalry -> Honor Debt, one arc in flight per hero | `arcDefinitions.ts` | — | |
| RL-17 | 181-187 | Arc common rules: both heroes level 5+, 200-day per-pair cooldown, one arc per hero, spark then modal with a 3-day deadline, per-archetype expiry defaults (`arcDefinitions.ts:58,82,107,131`), deferred a day while a crisis is active | `arcDefinitions.ts` | — | |
| RL-18 | 193-201 | Romance arc triggers (Attracted bond, tier >= Friendly, shared combat within 10 days) and its three outcomes including auto-upgrade to Married and Scorned with a 30-day mood penalty | `arcDefinitions.ts` | — | |
| RL-19 | 205-213 | Mentorship arc triggers (same class, veteran 30+, rookie under 10, 2+ shared missions) and outcomes (Student/Mentor bonds, 60-day mood bonus, dismiss) | `arcDefinitions.ts` | — | |
| RL-20 | 217-225 | Rivalry arc triggers (tier <= Dislike, contested kill, combat within 5 days) and outcomes (Tavern +15, Duel +10 with -2 STR for 30 days on the lower-level hero, Fester -> Blood Feud) | `arcDefinitions.ts` | — | |
| RL-21 | 229-237 | Honor Debt arc triggers (intervene save within 5 days) and outcomes (Oath Sworn, asymmetric Life Debt, Refuse -15) | `arcDefinitions.ts` | — | |
| RL-22 | 243-249 | Arc lifecycle: silent spark with Chronicle entries, modal 3-7 days later, immediate resolution, then the 200-day cooldown | arc code | — | |
| RL-23 | 251 | If a hero dies before resolution the arc is swept with a `relationship_arc_resolved` Chronicle entry flagged as permadeath, and the cooldown still applies | arc code | — | |
| RL-24 | 265-272 | Intervene requirements and chances (duplicate of combat.md) plus Mentor/Battle Brother +15% | intervene code | OK | mentor/battle-brother modifier not listed in combat.md; same source; relationships.md is the more complete of the two lists |
| RL-25 | 285-301 | Emotional state effects: Inspired +15% all stats, Enraged +30% damage, Vengeful +20%, Berserk +50%/-30% defense, Grief -20% all stats, Broken refuses to act, Panicked may flee | `Combat.ts` emotional states | KO | **conflicts with combat.md CB-33**, which says these modifiers are not applied in code; no damage/stat modifier consumes emotional state; the +15%/+30%/+20%/+50%/-30%/-20% figures are not applied in code |
| RL-26 | 313-320 | Mood states: Broken 0-9 -30%, Miserable 10-29 -20%, Unhappy 30-49 -10%, Content 50-69 0, Happy 70-89 +10%, Elated 90-100 +20% | mood code | OK | MOOD_STAT_MODIFIERS + getMoodState at social/mood.ts:62-107 match exactly |
| RL-27 | 326-333 | Four hero needs (Energy, Social, Recreation, Comfort) with critical thresholds below 20 that actively decrease mood | needs code | — | |
| RL-28 | 358-368 | Mental breaks only below mood 30, base 5%, +3% per day at low mood, +10% below 20, +20% below 10, +15% recent loss, -2% per close friend, capped at 80% | mental break code | KO | HeroMentalBreak.ts:52-78: trigger is mood < 25 (not 30); base 15% (not 5%); +5%/day (not +3%); -5% per close friend (not -2%); +20% recent loss (not +15%); cap 90% (not 80%); the "+10% below 20 / +20% below 10" tiers do not exist |
| RL-29 | 372-383 | Eight break types with durations and weights as tabulated (Desertion 15%, Berserk 10%, Catatonic 15%, Binge 15%, Insulting 15%, Hiding 10%, Wandering 10%, Confession 10%) | mental break data | OK | MENTAL_BREAK_WEIGHTS at social/mood.ts:83-92 match exactly (15/10/15/15/15/10/10/10) |
| RL-30 | 387-391 | Berserk break heroes attack a random target drawn from allies and enemies (`Combat.ts:6859-6941`) with damage passing the full defensive pipeline; Catatonic heroes lose their turn | `Combat.ts` | OK | Berserk sets forceAggressive/forbidDefensive with random targeting (Combat.ts:7512, 7842) |
| RL-31 | 401-405 | Breaks clear on schedule and the hero returns to their prior state; desertion is permanent | mental break recovery | — | |
| RL-32 | 413-437 | Social traits and effects: Friendly +2 trust/interaction, Antisocial -1, plus Kind, Brave, Loyal, Jealous, Coward, Cruel, Romantic, Competitive, Independent | trait data | — | |
| RL-33 | 447-455 | Attachment levels with time thresholds, rarity shortcuts, removal mood and worn mood: None/Comfortable(3d, Rare+, -5)/Favorite(14d, Epic+, -10, +3)/Prized(30d, Legendary, -20, +5)/Soulbound(+8) | `equipment.ts` attachment | — | |
| RL-34 | 461-469 | Five sentimental sources (Gift, Memorial, First Kill, Saved Life, Family Heirloom); Soulbound items cannot be removed at all; Prized and Soulbound are skipped by auto-equip | attachment code | — | |
| RL-35 | 471-473 | Greedy heroes attach at 2x speed (`equipment.ts:204`) reaching Prized at 15 actual days (`ATTACHMENT_THRESHOLDS[Prized] = 30`); Ascetic heroes never attach | `equipment.ts` | — | |
| RL-36 | 479-486 | Removal mood penalties: Favorite -8 for 3 days, Prized -12 for 5 days; aesthetically displeasing gear -5 while worn | attachment code | — | |
| RL-37 | 496-504 | Drunk levels 0-100 in five bands with social and accuracy modifiers; Hammered and Blackout block missions | alcohol code | — | |
| RL-38 | 508 | The accuracy column applies as a miss chance on basic attacks only; hangover and withdrawal penalties stack into the same roll | combat miss code | — | |
| RL-39 | 512-522 | Seven drinks with intoxication, addiction risk and price as tabulated | drink data | — | |
| RL-40 | 526-533 | Four tolerance levels with the described effects | tolerance code | — | |
| RL-41 | 539-546 | Four hangover levels with mood, accuracy, energy drain and vomit risk as tabulated | hangover data | — | |
| RL-42 | 552-560 | Four addiction levels with mood penalty, shakes, recovery days and mission refusal chance as tabulated | addiction data | — | |
| RL-43 | 564 | Blackout heroes can experience random unremembered events revealed next morning | blackout event code | — | |
| RL-44 | 574-587 | Ten unavailability reasons; overriding costs mood; Mourning and Mental Health cannot be overridden | unavailability code | — | |
| RL-45 | 593-597 | Absences are priced per claimed line (not per reason), paid from the hero's purse, billed the same night and shown under Elsewhere; heroes who cannot afford anything take a free day that the ledger notes | absence pricing code | — | |
| RL-46 | 601-607 | Veracity levels Sincere / Unverifiable / Thin with the listed reason mappings, recorded but never adjudicated | absence veracity data | — | |
| RL-47 | 615-628 | Ten mission refusal reasons with soft/hard severities as tabulated | refusal code | — | |
| RL-48 | 632 | Location trauma severity runs 1-10, drains one point every ten days, and clears at zero | trauma code | — | |
| RL-49 | 638-650 | Eight insistence reasons; removing an insistent hero costs mood | insistence code | — | |
| RL-50 | 656-700 | Ambient social event catalogue in four groups with the listed events | social event catalog | — | |
| RL-51 | 728-734 | Keepsake sources: Gift (bonded pair, 100-day per-pair cooldown), Heirloom (10% at recruitment from background pool), Memorial (on death, to closest surviving bonded hero) | `HeroSocial.ts` | — | |
| RL-52 | 736 | Gift names come from per-class pools, heirloom names from background, memorial keepsakes named "Memento of {hero}" with a mood-floor bonus | keepsake data | — | |
| RL-53 | 742-748 | Keepsakes carry exactly one bonus of kind `mood_floor`, `combat` or `resist` (`KeepsakeBonus` in `HeroSocial.ts`) | `HeroSocial.ts` | — | |
| RL-54 | 750 | `applyKeepsakeBonus` (`GameState.ts:118`) applies combat and resist bonuses as `BuffSource.Keepsake` entries; mood-floor bonuses become long-lived mood modifiers | `GameState.ts` | — | |
| RL-55 | 754 | There is no cap on keepsakes per hero | keepsake code | — | |

## guild.md

| ID | Line | Claim | Where to verify | Status | Notes |
|----|------|-------|-----------------|--------|-------|
| GD-01 | 7-38 | 14 facilities with the listed max levels (most 5, Armory and Warehouse 6, Workshop 10, Quarters and Materials Market unlevelled) | `GuildFacilities.ts` | OK | 14 FacilityTypes with maxLevel 5 except Armory 6, Warehouse 6, Workshop 10 |
| GD-02 | 44-51 | Facility upgrades are timed construction projects driven by `upgradeTimeDays` (2-20 days); the old level stays active, only one build guild-wide at a time, no cancellation, and completion emits a `facility_upgrade_complete` day-summary event | `GuildFacilities.ts` + upgrade code | KO | mechanics are right, but the stated range is wrong: upgradeTimeDays runs 1 to 180 days, not "2 days to 20 days" |
| GD-03 | 57-69 | Build-day distribution across all facility levels as tabulated (7 at 2 days, 10 at 3, 3 at 4, 5 at 5, 6 at 6, 4 at 7, 3 at 8, 7 at 10, 1 at 14, 1 at 15, 3 at 20) | `GuildFacilities.ts` | KO | distribution is wrong on three counts: it says "14 facilities x 5 levels" (there are 77 level entries, not 70); 14-day count is 2 not 1 and 15-day count is 3 not 1; and it omits the 1, 12, 16, 18, 25, 30, 35, 60, 90, 120 and 180-day buckets. Guild Hall L5 is 30 days, not 20 |
| GD-04 | 75-77 | UI cues: 🏗 Nd badge with progress bar on the tile, construction card replacing Upgrade in the detail panel, and a build-time line on the next-level block | facilities UI | — | |
| GD-05 | 87-93 | Guild Hall levels: Modest 2 slots 5g, Expanded 4 slots 25g, Grand 6 slots 50g, Manor 8 (+1 contract) 1,500g, Legendary 10 (+2) 4,000g | `GuildFacilities.ts` | OK | GuildFacilities.ts:138-142 matches names, slots, contracts and upkeep |
| GD-06 | 99-105 | Barracks levels: beds 12/20/30/45/60, mood -10/-5/0/+5/+10%, rest 0.9-1.1x, upkeep 2/12/20/800/2,000g | `GuildFacilities.ts` | OK | GuildFacilities.ts:154-158 matches beds, mood, restRate and upkeep |
| GD-07 | 115-120 | Barracks morale penalty by hero level: none below 50, -5 at 50-79, -10 at 80-99, -15 at 100+ | quarters code | OK | Quarters.ts:512-515 - -15 at 100+, -10 at 80+, -5 at 50+, none below |
| GD-08 | 124-133 | Six quarters floors of 12 rooms each, built in order, costing 50,000 / 150,000 / 400,000 / 800,000 / 1,500,000 / 3,000,000g | quarters code | OK | FLOORS costs 50k/150k/400k/800k/1.5M/3M and FLOOR_LAYOUT.roomPositions holds 12 rooms |
| GD-09 | 135 | 72 private rooms total, sleeping up to 144 heroes at two per room | quarters code | OK | 6 floors x 12 rooms = 72; rooms hold two heroes |
| GD-10 | 141-147 | Room tiers 1-5 with upgrade cost, upkeep, deco slots and morale as tabulated | quarters room data | OK | ROOM_TIERS matches upgrade cost, upkeep, decoration slots and morale exactly |
| GD-11 | 149 | Only occupied rooms are charged upkeep, billed per room rather than per hero | upkeep code | OK | calculateQuartersUpkeep bills distinct occupied room keys (spec 265) |
| GD-12 | 155-161 | Decoration best-items with costs and effects (Royal Bed 100,000g +25% HP recovery, Magic Orb 80,000g +12 morale, Legendary Banner 150,000g +3% damage, Hot Spring 120,000g +8 morale +15% HP recovery, Gold Statue 200,000g +2% all stats); cheaper options 1,000-60,000g; sell refund 50% | decoration data | OK | DECORATION_DEFINITIONS: Royal Bed 100k/+25% recovery, Magic Orb 80k/+12, Legendary Banner 150k/+3% dmg, Hot Spring 120k/+8/+15%, Gold Statue 200k/+2% all stats; cheaper tiers run 1,000-60,000 |
| GD-13 | 165 | Class decoration preferences grant +3 morale, with the listed class-category pairs | decoration preference code | OK | CLASS_DECORATION_PREFERENCES matches all six classes; +3 morale on a category match |
| GD-14 | 171-181 | Adjacency morale: Best Friend +10, Friend +5, Neutral 0, Rival -5, Enemy -10; each room has 1-2 neighbours around a central hallway | adjacency code | OK | getRelationshipMoraleModifier returns +10/+5/0/-5/-10; adjacencyPairs give each room 1-2 neighbours |
| GD-15 | 185-193 | Private rooms hold two heroes; shared-room romance morale Married +12, Lovers/Partner +9, Dating +6, else 0; non-romantic roommates take no penalty | cohabitation code | OK | getCohabitationMoraleBonus: Married +12, Lovers/Partner +9, Dating +6, others 0 |
| GD-16 | 195-201 | The nightly pass runs before upkeep, separates split bonds first, moves a hero's strongest current partner in (Married > Lovers > Partner > Dating), keeps the better-tiered room, skips full rooms, and leaves Barracks couples alone | cohabitation code | OK | reconcileCohabitation runs separations first (Quarters.ts:341-344) and leaves Barracks couples alone |
| GD-17 | 205 | Roommates multiply illness transmission x2.0 on top of bond multipliers; Barracks heroes are not roommates for contagion | `IllnessEngine.ts` contagion | — | |
| GD-18 | 211-217 | Quarters morale thresholds: above 20 gives +3% damage / +5% XP, above 10 gives +1% / +2%, 0-10 nothing, -5 to 0 gives -2% XP, below -5 gives -3% damage / -5% XP | quarters morale code | — | |
| GD-19 | 223-229 | Tavern levels with recruit quality ranges, daily income 150/500/1,500/4,000/10,000g and upkeep 3/15/30/800/1,500g (`GuildFacilities.ts:190-194`) | `GuildFacilities.ts` | OK | GuildFacilities.ts:170-174 matches quality ranges, income and upkeep |
| GD-20 | 231 | The tavern quality column is `recruitQualityMin`/`recruitQualityMax`, not a recruit count | `GuildFacilities.ts` | OK | effects are recruitQualityMin/Max as stated |
| GD-21 | 239-244 | Tavern activity costs, baseline mood effects and cooldowns: Buy Rounds 10g x levels +3, Grand Feast 100g + 20g x levels +10 (1 day), Gambling 50-500g +5, Bard Night 15g x levels +8 (3 days); per-hero variance from traits | tavern activity code | — | |
| GD-22 | 246 | Each activity carries roughly a 15% chance of pushing a secondary event onto the nightly scouting scene | tavern activity code | — | |
| GD-23 | 250-252 | The nightly scouting scene rolls 3-6 weighted autonomous events; intervention spends Attention Points from the same budget as the Tonight tab; Skip passes unresolved events to the autonomous resolver | tavern scene code | — | |
| GD-24 | 256-264 | The Tonight tab presents 6-8 situations per night; Attention Points by Tavern level are 3 (L1-2), 4 (L3-4), 5 (L5+); each decision costs 1-2 | tavern decision engine | — | |
| GD-25 | 268-290 | Eighteen decision types with cost, trigger, success outcome and skip penalty as tabulated | decision data | — | |
| GD-26 | 292 | Each hero-situation combination has a 3-night cooldown | decision cooldown code | — | |
| GD-27 | 298-330 | Background event catalogue in three groups (6 positive, 9 negative, 7 dramatic) with the listed effects, including Marriage Proposal requiring relationship >= 80 and Lovers Getaway making both heroes unavailable for 2 days | background event data | — | |
| GD-28 | 338-344 | Training Yard levels give training speed 1.0/1.25/1.5/1.75/2.0x with the listed features | `GuildFacilities.ts` | OK | GuildFacilities.ts:186-190 trainingSpeed 1.0/1.25/1.5/1.75/2.0 |
| GD-29 | 349-355 | Infirmary levels: healing speed 1.0-2.0x, treatment slots 4/6/10/16/24, features as listed | `GuildFacilities.ts` | OK | edited this session; GuildFacilities.ts:202-206 |
| GD-30 | 361-368 | Armory levels: 200/400/800/1,400/2,000/3,000 equipment slots with upkeep 2/12/25/45/1,500/3,000g and repair from L4 | `GuildFacilities.ts` | OK | GuildFacilities.ts:218-223 slots, upkeep and repair flag from L4 |
| GD-31 | 374-380 | Forge levels: craft speed 1.0/1.15/1.3/1.5/2.0x, max tier 1-5, quality +10/+20/+30% at L3-5 | `GuildFacilities.ts` | OK | GuildFacilities.ts:257-261 |
| GD-32 | 388-399 | Workshop levels 1-10 with process speed, quality bonus and upkeep as tabulated | `GuildFacilities.ts` | OK | GuildFacilities.ts:308-322 speeds, quality bonuses and upkeep through L10 |
| GD-33 | 401 | Workshop levels 7-10 unlock the crafting currency discount of 10% per level above 1 up to 90% | currency discount code | KO | claim says levels 7-10 but crafting.md says levels 2-10 — reconcile; the discount starts at Workshop level 2, not level 7 |
| GD-34 | 407-413 | Library levels: research speed 1.0-2.0x, max recipe tier 1/2/3/3+lore/3+lore | `GuildFacilities.ts` | OK | GuildFacilities.ts:338-342 researchSpeed and maxRecipeTier (3 from L3 with loreBonus at L4/L5) |
| GD-35 | 419-425 | Chapel levels: mood +3/+6/+10/+15/+22 with blessings from L2 and Sacred Crafts from L3 | `GuildFacilities.ts` | OK | GuildFacilities.ts:355-362 moodBonus 3/6/10/15/22, blessings from L2, holyCrafts from L3 |
| GD-36 | 428-432 | Chapel special features: memorial services, daily mood bonus, blessings from L2, sacred crafting at the Forge from L3 requiring a Cleric | chapel code | OK | blessings flag from L2, holyCrafts from L3 with requiresClassOnRoster Cleric |
| GD-37 | 436-444 | One blessing charge per day at Chapel L2+, no roll-over, spent from the Mission Board contract panel on an undispatched contract, lasting until the mission resolves; magnitude scales with Chapel level per the table | blessing code | OK | getBlessingCharges returns 1 at L2+ regardless of level; BLESSING_EFFECTS table matches the guide row for row |
| GD-38 | 448-452 | Courage raises the critical-success chance rather than the win rate; Fortune always adds at least +1 item with a rare chance of a guaranteed top-tier drop for the mission's tier; Vigilance reduces post-death-save injury chance only for heroes who went down | blessing effect code | OK | Blessing.ts comments confirm successBoost is Success->CriticalSuccess only, Fortune adds a guaranteed +1 item on top of lootMult with tier-bounded rare roll, and injuryMult applies to the death-save-survivor branch |
| GD-39 | 458-466 | Sacred Crafts: 6 recipes unlocking 2 per Chapel level from L3, all using blessed_stone / world_tree_branch / god_tear, Ancestral rarity, Cleric-locked, and vanishing if no Cleric remains | sacred craft data | KO | six recipes, 2 per Chapel level from L3, Cleric-locked and Ancestral (NamedItems.ts:730) are all correct - but the materials claim is wrong: the L3 pair uses mithril_ingot + blessed_stone only, the L4 pair blessed_stone + world_tree_branch, and only the L5 pair uses god_tear. Not "all six use" all three |
| GD-40 | 468 | Every sacred craft carries a hidden `Consecrated` tag worth +30 flat HP while equipped, stacking to +180 across six pieces | consecrated code | OK | CONSECRATED_HP_PER_PIECE = 30 (Inventory.ts:25), applied per equipped consecrated item, 6 pieces = +180 |
| GD-41 | 478-484 | Three moral axes ranging -100 to +100 with the listed poles | guild identity code | — | |
| GD-42 | 488-500 | Moral events start on day 10, up to 3 pending at once, five categories, deadlines with default auto-resolution, and a 10-day no-repeat window | guild identity code | — | |
| GD-43 | 502 | The Guild Events screen has Active and History tabs, the latter showing day, chosen option, heroes involved, axis shifts, gold changes and auto-resolution | guild events UI | — | |
| GD-44 | 508-518 | Hero trait reactions to axis shifts as tabulated, with mood change scaling roughly 1 mood per 3 axis points | reaction code | — | |
| GD-45 | 534-538 | Wealth axis shop discounts: 10% at 60+, 5% at 30+, none below 30 | shop pricing code | — | |
| GD-46 | 548-560 | Context-aware events in five categories with deadlines of typically 3-5 days and a default option on expiry | context event code | — | |
| GD-47 | 566-575 | Context events fill 1-2 hero slots via preconditions (bond, mood threshold, stat threshold, tenure, trait, hero count) and do not fire when nothing matches | precondition engine | — | |
| GD-48 | 579 | Consequence chains schedule follow-ups 5-30 days later and can chain further | consequence chain code | — | |
| GD-49 | 595-605 | Reputation ranks and thresholds F 0, E 500, D 1,500, C 4,000, B 10,000, A 25,000, S 60,000 (`GuildFacilities.ts:579-586`) with bonus slots +0/+0/+1/+1/+2/+2/+3 (`GuildFacilities.ts:607-615`) | `GuildFacilities.ts` | OK | REPUTATION thresholds and GUILD_RANK_SLOT_BONUS match exactly. Omission: GUILD_RANK_HERO_BONUS also adds +0/+2/+4/+6/+8/+12/+18 to hero capacity by rank, which no guide mentions |
| GD-50 | 607 | The Workshop is gated by `unlockRequirements: { questUnlock: true }` (`GuildFacilities.ts:333`), not by reputation rank | `GuildFacilities.ts` | — | |
| GD-51 | 613-620 | Reputation is granted only by mission completion (`GameState.ts:4707`), quest chain rewards (`QuestChain.ts:465`), moral event consequences (`GuildIdentity.ts:243`, `MoralEventResolver.ts:72`) and custom dungeon architect rewards (`architectRewards.ts:56`) | those files | — | |
| GD-52 | 624-628 | There is no reputation-loss path; failure pays zero reputation (`GameState.ts:4702-4708`) and no abandon, death or wipe penalty exists | `GameState.ts` | — | |
| GD-53 | 638-644 | Income sources: dungeon loot, tavern income 150-10,000g/day, item sales | income code | — | |
| GD-54 | 648-657 | Expense list including quarters upkeep 30-1,000g per occupied room and recruitment 50g-100,000g+ | expense code | — | |
| GD-55 | 663-679 | Daily Wage = floor((Level - 1)^1.5 x 3) x Quality Multiplier with multipliers 1.0/1.2/1.5/2.0/3.0 and the worked examples 24 / 248 / 1,029 / 2,955 / 8,865g | `calculateHeroWages` | OK | GameState.calculateHeroWages: floor(pow(level-1,1.5)*3) x [1,1,1.2,1.5,2,3][quality]; all five worked examples reproduce exactly |
| GD-56 | 681 | Level 1 heroes are free; sixty Legendary level-100 heroes cost 531,900g/day | wage code | OK | 8,865 x 60 = 531,900 |
| GD-57 | 683 | Heroes are credited their base wage, unaffected by the crisis multiplier the guild pays | wage + purse code | — | |
| GD-58 | 699-708 | Eight hero states with mission/craft eligibility | `HeroState` enum | — | duplicate of HR-14 |
| GD-59 | 714-721 | Mood bands and stat modifiers | mood code | OK | duplicate of RL-26; same source as RL-26 |
| GD-60 | 745 | Mental breaks are prevented by keeping mood above 50 | mental break code | KO | conflicts with relationships.md RL-28, which puts the break threshold at mood 30; breaks trigger below mood 25, not 50; the guidance overstates the threshold by 25 points |
| GD-61 | 755-765 | Relationship tiers with combat bonuses; Best Friend row notes Intervene | relationship code | OK | the positive tiers agree in both implementations |
| GD-62 | 781-787 | Shop levels: display slots 8/16/24/32/48, customers per day 4-7 / 6-10 / 10-15 / 14-20 / 20-30, upkeep 5/10/20/600/1,500g | shop data | OK | GuildFacilities.ts:375-379 display slots and upkeep; the customer ranges match the description strings |
| GD-63 | 789 | Eight customer types with distinct budgets, item preferences and rarity ceilings; higher shop levels tilt the mix toward wealthier types | customer data | — | |
| GD-64 | 791 | Theft chances: Peasants ~8%, Rival Guilds ~5%, Knights/Nobles/Collectors never; anti-theft investment raises catch rate and a caught thief leaves a ⚑ mark for a couple of days | theft code | — | |
| GD-65 | 795 | Market events: Festivals +30% accessory demand, Wars +25% weapon/armor, Disease Outbreaks +50% consumables | shop market events | — | |
| GD-66 | 807-819 | Materials Market pricing: Effective Price = Base x Player Multiplier x Event Modifiers, with base prices 100 / 1,000 / 10,000 / 100,000g and Legendary materials and monster parts excluded | market code | — | |
| GD-67 | 821 | The market stocks Powder of First Enchantment 500g, Powder of Erasure 500g and Salt of Renewal 5,000g daily, exempt from multiplier and events | market code | — | |
| GD-68 | 823 | Player multiplier starts at 1.0x, ±0.05 per unit traded, clamped 0.5x-10.0x, with a -0.01 per unit spillover onto cheaper metals in the same category | market code | — | |
| GD-69 | 829-839 | Restock quotas and max stock by tier (Common 5/100, Food 20/400, Uncommon 4/80, Rare 1/20, Epic 1 weekly/20); stock above quota is kept; Buy/Sell limited to 1 or 10 per click with no daily cap | market code | — | |
| GD-70 | 845-869 | Market events fire at 5% daily, up to 3 concurrent, lasting 3-10 days, with the twelve listed spikes and drops; modifiers stack on the player multiplier and are not clamped | market event data | — | |
| GD-71 | 875-883 | The Item Workshop rerolls Rare+ items, excludes named items, and costs 1,000 x Rarity x 2^(reroll count) | workshop reroll code | KO | conflicts with crafting.md CF-30, which says there is no rarity or named gate; no Rare+ gate and no named-item gate exist; the only refusal is for cursed items |
| GD-72 | 885 | The Item Workshop is reached from the Guild Screen -> Item Workshop button | navigation | KO | conflicts with crafting.md CF-32, which says it is a bottom-nav peer; the Workshop is a bottom-nav entry, not a Guild Screen button |
| GD-73 | 891-897 | Merchant caravans first arrive on day 5, visit every 3-7 days, and stay 2-5 days | caravan code | — | |
| GD-74 | 899 | Eight merchant types; Master Crafter needs 5,000+ reputation and Exotic Goods 2,000+ | caravan data | — | |
| GD-75 | 907-915 | The rival-guild manager has been removed from the game; only the Rival Guild War crisis type and Rival Guilds as shop customers survive | code search for rival guild manager | — | |
| GD-76 | 921-931 | The Guild Chronicle has Combat and Social tabs with the listed top-3 categories and sortable columns | chronicle UI | — | |
| GD-77 | 935-945 | Guild hero ranks require both days served and missions completed: Recruit 0/0, Member 50/25, Senior 150/75, Officer 300/200, Leader 500/400 | rank code | — | |
| GD-78 | 949-955 | Chronicle entry categories and the 50-entry Legend title | chronicle code | — | |
| GD-79 | 963-969 | The five day phases are Dawn, Morning, Midday, Afternoon, Night (`GameState.ts:337-343`) with the described contents | `GameState.ts` | — | |
| GD-80 | 973-977 | Daily wages and upkeep are charged daily; the mission board refreshes on a variable cadence; a new weekly bounty rolls every 7 days | day tick code | — | |

## Repository docs (non-guide)

| ID | File:Line | Claim | Where to verify | Status | Notes |
|----|-----------|-------|-----------------|--------|-------|
| RM-01 | README.md:12-17 | Index claims 6 hero classes, 8 backgrounds with a 4-stage life history, and a 354-node passive tree | game data | OK | same claims as HR-01, BG-02, PT-01; 6 classes, 8 backgrounds and the 4-stage lifecycle confirmed; 354-node tree pending PT-01 |
| RM-02 | README.md:26 | "The 14 realm-wide crises" | crisis catalog | OK | same as CR-01; 14 crises confirmed |
| RM-03 | README.md:34 | Raids are 15-hero | `RaidSetup.tsx` | — | same as RD-04 |
| RM-04 | README.md:51-57 | Key features: 6 classes named, 14 ascendancy paths, 10 production facilities, 7 dungeon environments | game data | — | crafting.md lists 10 stations but guild.md lists 4 production facilities — check which "10" is meant |
| RM-05 | README.md:63 | Steam store link is `https://store.steampowered.com/app/herosguild` | `getSteamStoreUrl()` in `utils/demo.ts` | — | code uses app/4268730/Heros_Guild |
| RM-06 | README.md:64-65 | Discord invite `discord.gg/herosguild` and bug reports at `github.com/Surinenc/herosguild-doc/issues` | external; repo remote | — | remote confirmed as Surinenc/herosguild-doc |
| RM-07 | README.md:69 | The game is in Early Access | build/release config | — | |
| CM-01 | CLAUDE.md:13 | Canonical game repo root is `/Users/20018578/proj/surinenc_k8s/heroworld-speckit-test/` | filesystem | — | path does not exist on this machine; real repo is /home/anarion/proj/herosguild |
| CM-02 | CLAUDE.md:14 | `heroworld/` symlink in this repo points at the canonical root and game source is at `heroworld/game/src/` | filesystem | — | symlink is dangling |
| CM-03 | CLAUDE.md:7 | Documentation-only repo with no package.json, test suite or build step | repo contents | — | |
| CM-04 | CLAUDE.md:39 | The guides list enumerates every file in `guides/` | `ls guides/` | — | |
| CM-05 | CLAUDE.md:44 | `TRIALS-DESIGN-PLAN.md` is a long-form design doc not part of the shipped wiki | file contents | — | |
| CN-01 | constitution.md:4,120 | Constitution version 1.1.0, ratified and last amended 2026-03-17 | git history of the file | — | |
| CN-02 | constitution.md:30,94 | Game source root is the macOS path `/Users/20018578/proj/surinenc_k8s/heroworld-speckit-test/game/src/` | filesystem | — | same dead path as CM-01 |
| CN-03 | constitution.md:87-98 | The Source Code References table maps subsystems to files that exist in the game repo | game repo paths | — | |
| SK-W-01 | SKILL.md:4-6 | The skill points at the same macOS path and reaches it via the `heroworld/` symlink | filesystem | — | same dead path as CM-01 |
| SK-W-02 | SKILL.md:104-108 | The survey command `cd heroworld && git log <sha>..HEAD -- game/src/models/ game/src/scenes/ game/src/data/` works as written | shell | — | fails through the dangling symlink |
| SK-W-03 | SKILL.md:135-140 | The marker file `.specify/memory/last-wiki-sync.txt` holds one short SHA of the game repo HEAD | file contents | — | |
| TR-01 | TRIALS:52 | Part B "Custom Dungeons today" (2026-04-23): admin manual approval, 5 publishes per 24h per Steam ID, 6 hazard types, 1MB body cap, audit log, admin queue | custom dungeon server routes + `HazardCatalog.ts` | — | dated snapshot; dungeons.md now documents 8 hazard types |
| TR-02 | TRIALS:64 | Proposed tier caps Apprentice <= 200, Journeyman <= 500, Master <= 1,000 menace | custom dungeon budget code | — | design proposal; check whether it shipped |
| TR-03 | TRIALS:71 | Proposed narrator-hero lock of 3 days | narrator lock code | — | shipped per custom-dungeons.md CD-08 |
| TR-04 | TRIALS:85 | Proposed leaderboard: first-session-only, version-scoped, top 10 sorted by tree depth then attempts then turns then survival | leaderboard code | — | custom-dungeons.md CD-21 says best cleared session, not first-session-only |
| TR-05 | TRIALS:103-113 | Proposed weekly leagues opening each Monday with a four-metric rotation including stealth-clear, plus Legacy League archive and Hall of Notorious top-3 | `cdLeague.ts` | — | shipped monthly with three metrics per CD-24 |
| TR-06 | TRIALS:119 | Proposed mandatory proof-of-clear before publishing | publish flow | — | check whether it shipped |
| TR-07 | TRIALS:126 | Proposed fame decay: unplayed 60 days slides to an Archive tab | `cdObservedDifficulty.ts:103-118` | — | shipped per CD-26 |
| TR-08 | TRIALS:133 | Proposed two-stage publishing: Draft by default, promoted after 10 successful clears or explicit promote | publish/promotion code | — | shipped per CD-07 |
| TR-09 | TRIALS:140 | Proposed Architect Pages with lifetime clear rate, chronicle entries written, accolade tally, season ranking | architect page UI | — | partially shipped per CD-27 |

---

## Cross-document consistency checks

| ID | Claim A | Claim B | Status | Notes |
|----|---------|---------|--------|-------|
| XR-01 | skills.md:65 socket chance `30% + ilvl x 2%` capped 90% | equipment.md:57 socket chance `20% + ilvl x 1%` capped 90% | OK | both cannot be right; both formulas exist: Item.ts generateSocketCount is 20%+1% (live loot path); GemSocket.generateRandom 30%+2% has NO production callers |
| XR-02 | combat.md CB-33: emotional-state damage modifiers are NOT applied in code | relationships.md RL-25: Inspired +15% all stats, Enraged +30% damage, etc. | KO | direct contradiction; combat.md is right, relationships.md is wrong |
| XR-03 | relationships.md RL-28: mental breaks trigger below mood 30 | guild.md GD-60: "Prevent breaks by keeping mood above the Unhappy threshold (50+)" | KO | thresholds disagree; neither guide is right: code threshold is mood < 25 (HeroMentalBreak.ts:52) |
| XR-04 | crafting.md CF-30: Item Workshop has no rarity or named-item gate | guild.md GD-71: rerolls Rare+ only, named items excluded | KO | direct contradiction; crafting.md is right, guild.md is wrong |
| XR-05 | crafting.md CF-32: Workshop is a bottom-nav peer (⚙) | guild.md GD-72: reached from Guild Screen -> Item Workshop button | KO | may be two different screens; confirm; crafting.md is right, guild.md is wrong |
| XR-06 | crafting.md CF-38: currency discount at Workshop levels 2-10 | guild.md GD-33: "Levels 7-10 also unlock a crafting currency discount" | KO | disagree on which levels; crafting.md has the right levels, guild.md is wrong; both describe what it discounts incorrectly |
| XR-07 | backgrounds.md BG-01: lifecycle catalog is "just under two hundred" events | heroes.md HR-13: "a catalog of a hundred and twenty events" | KO | counts disagree; spec 374 authored obituary clauses for "all 120 lifecycle events"; heroes.md (120) is right; backgrounds.md is wrong on both the total and the per-stage counts |
| XR-08 | heroes.md HR-10: UI crit chance uses LCK/20 | combat.md CB-09: crit chance uses LCK/10 | OK | heroes.md says both exist in different paths; verify; not a contradiction - two live paths, and heroes.md already explains both |
| XR-09 | combat.md CB-31 intervene modifiers omit Mentor/Battle Brother | relationships.md RL-24 lists Mentor/Battle Brother +15% | KO | one list is incomplete; combat.md omits the Mentor/Battle Brother +15% modifier that exists in code; both guides omit Attracted bonds and the Shield Sibling title bonus |
| XR-10 | dungeons.md DG-35 death save omits survival gear | heroes.md HR-39 includes survival gear +5% | KO | one list is incomplete; heroes.md is complete; dungeons.md is missing the survival-gear row |

---

## Link integrity

| ID | Check | Status | Notes |
|----|-------|--------|-------|
| LK-01 | Every intra-wiki markdown link resolves to an existing file | OK | all file targets resolve except getting-started.md:76 |
| LK-02 | Every anchor link (`file.md#anchor`) matches a heading in the target file | KO | equipment.md:287 -> skills.md#socket-links; the heading is "Linking Sockets" |
| LK-03 | `getting-started.md:76` links to `guides/heroes.md` from inside `guides/` | KO | confirmed: resolves to guides/guides/heroes.md |
