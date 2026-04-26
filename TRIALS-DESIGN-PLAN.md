# Meet Your Maker → HeroGuild: Adapting the Builder/Raider Loop

Author: design memo for HeroGuild (urummi), 2026-04-23
Audience: solo dev planning Custom Dungeons V2 for Steam Early Access
Length: ~7.6k words

## Part A — What Meet Your Maker actually was

### The core loop, plainly

Meet Your Maker (MYM, Behaviour Interactive, April 2023) was a first-person asymmetric "build-and-raid" game wrapped in a thin post-apocalyptic frame story about feeding a creature called the Chimera. Two modes, one loop:

**Builder mode.** You claimed an "outpost" — a small plot of land with a fixed footprint and a buried "GenMat" capsule at the back. You laid down modular cube blocks (the navigable geometry), then placed traps (spike pits, plasma blasters, holocubes, incinerators) and guards (sword-wielding chargers, bow-wielding watchmen, ranged "killers"). Every block, trap, and guard cost a hard currency — Synthite for builders, with mod points capping how powerful any one thing could get. The HRV (a slow drone) carved a fixed path from entrance to GenMat, and traps were valued by their proximity to that path: a trap one block off the HRV path counted four times its base cost toward the difficulty cap, while a trap three blocks off counted once. That single distance-to-path rule was the entire economy of trap placement, and it shaped every interesting outpost in the game.

**Raider mode.** You picked another player's outpost from a queue (matched roughly by your selected difficulty: Normal/Dangerous/Brutal, later replaced with a 10-skull granular scale). You ran in first-person with a sword, bow, grappling hook, and a small kit of suit mods. Goal: reach the GenMat, grab it, escape. Death sent you back to the entrance with all your gear. Mid-2023 the game added "Dangerous" and "Brutal" tiers and dynamic difficulty rating that updated based on raider kill rates — the outpost's claimed difficulty drifted toward observed reality.

**Progression.** Builders earned Synthite and Prestige Points when raiders died. Hitting a Prestige threshold let you "prestige" the outpost, refilling its GenMat pool and extending active life by ~24 hours per prestige rank, up to 10. After Prestige 10 the outpost moved to a "Social" tab — still playable, but no longer matched into the active raid queue.

**Raiders** earned GenMat by clearing or surviving outposts. GenMat fed five "Advisor" tracks (suits, weapons, traps, guards, blocks) which evolved the Chimera and unlocked new building/raiding pieces. The whole long-tail meta was: kill heroes to earn the right to publish more elaborate murder.

**Social layer.** After every raid, the raider could leave Accolades — small reaction tags ("Brutal", "Ingenious", "Artistic", "Twisted") that pinned to the outpost. The replay system let builders watch every raider attempt at any speed, scrub the timeline, and see exactly which trap got the kill. That replay-plus-accolade pair was MYM's social-recognition engine. It was also (Behaviour explicitly said this in launch interviews) the entire reason the game existed: "no PvP combat — you express your aggression through architecture, and the trace of your victim is the replay."

### What worked

The asymmetry was real and load-bearing. Builders and raiders were playing different games that *needed* each other. A builder who never raided couldn't build well — you had to know what raider movement felt like to know which sightlines mattered. The dual-citizenship model gave the game a depth-of-mastery curve normally reserved for fighting games.

Outposts went viral in a specific way: a clever single-trick outpost ("the entire arena is a single second-wave plasma volley triggered by a holocube") would get stitched into raider TikToks and Reddit clips, the builder's name attached. The replay system made the builder *visibly the author* of any given death. Behaviour leaned into this with featured outposts, weekly Dev Picks, themed "Bunker" events. The implicit creator economy worked when it worked.

### What didn't

MYM bled players hard. Steam peaked at ~3,300 concurrent the first weekend, fell under 1,000 within a month, under 200 by autumn 2023. By March 2024 Behaviour's parent leadership had pulled the team off the game; the official forums shut April 5, 2024; only cosmetic patches followed. Causes, in roughly the order they bit:

1. **Content treadmill on the builder side.** The trap and guard catalog was small (~14 traps, ~6 guards at launch). Within two weeks every outpost felt like permutations of the same three combos. Behaviour added new pieces slowly — one or two per quarterly Chapter — and the catalog never reached the volume the meta demanded.
2. **Unfair-but-not-unbeatable outposts.** Behaviour publicly insisted "no outpost is impossible to defeat." Technically true. Practically, a meaningful slice of brutal outposts required pixel-perfect parkour or memorization, which felt the same as "impossible" to a casual raider.
3. **Monetization missteps.** A premium Bunker pass at launch on top of $30 box price, with cosmetic Dreadshards as a soft currency, signaled "live service" to an audience that read the game as a one-time purchase. The PS Plus Essential drop in summer 2023 dumped a million accounts in, then 94% of them left within weeks.
4. **Audience size.** First-person parkour-FPS plus level-design tools is a Venn intersection that sounds bigger than it is. Mario Maker players don't necessarily play Doom Eternal. The DBD audience didn't crossover.
5. **Anti-grief friction.** Joke outposts (a wall of plasma ten blocks deep) only got filtered after enough raiders rage-quit and reported. Reactive, not preventive.
6. **Builder funnel.** The Mario Maker problem: ~90% of players raid, ~10% build. MYM's incentives (Prestige, Synthite for more building) were too inwardly-pointed. There was no in-game way for a top builder to become a known name to non-followers.

### Design pillars Behaviour explicitly named

- **Asymmetric play loop**: builder and raider are distinct games that share economy.
- **Creator economy / "user-generated forever"**: every level shipped is community-made.
- **Social recognition without live PvP**: replay + accolades replace voice chat and matchmaking salt.
- **No live combat between humans**: "you fight someone's *trace*", not them.
- **Mastery through dual citizenship**: you cannot build well unless you raid, and vice versa.

---

## Part B — HeroGuild's Custom Dungeons today

HeroGuild already has the bones of an MYM-style loop, but rotated 90 degrees. Players use an in-game 2D-grid editor to author dungeons — tiles, enemies, traps, events, room markers, multi-floor stairs — and submit via API. An admin manually approves; approved dungeons appear in a Community Dungeons browser scene where any other player can "raid" them with their own AI hero party (Warrior/Mage/Cleric/Rogue/Ranger/Necromancer mix), resolved via offscreen-resolution and turn-based combat (Part D proposes making the inter-combat navigation interactive while keeping combat itself offscreen). Persistence: SQLite. Identity: Steam ID (036 hardening shipped Steam Web API ticket validation). Limits: 5 publishes per 24h per Steam ID, 6 hazard types, 1MB body cap, audit log, admin queue replacing the older auto-hide-on-3-reports.

The crucial inversions vs. MYM: the "raider" is never a live human — it's the dungeon-runner's AI hero party. The builder authors once and the dungeon itself never auto-updates in response to specific runs (though once Part D's Watcher Mode ships, the architect's *authoring loop* becomes data-informed — they see every session and iterate accordingly). Difficulty tuning is design-time only. But: HeroGuild has a much richer hero-fiction layer (chronicles, mood, relationships) than MYM ever had, and Steam-authenticated identity means we can attribute creation and clearing to *named people* in a way MYM mostly did with one-line author tags.

---

## Part C — The asymmetric concept, applied

The MYM playbook can't be ported wholesale because there is no live raider, but the *spirit* — "your dungeon is a social object authored by a named person, and other named people leave traces on it" — maps cleanly onto HeroGuild. Below: ten mechanics, ranked by my conviction.

### 1. Architect's Budget (small)

The editor already shows a budget number; make it the spine of scoring. Each tile/enemy/trap has a printed Menace Cost. A dungeon must fit under a published-tier cap (Apprentice <= 200, Journeyman <= 500, Master <= 1,000). Crucially, **clear-rate scoring rewards low-cost-per-difficulty** — a Master-tier dungeon that gets a 30% clear rate on standard parties scores higher than a 30%-clear Apprentice. Builds the "elegance" muscle MYM's distance-to-path rule cultivated.
- **Builds on**: existing budget display, hazard catalog, dungeon ratings.
- **MYM pillar preserved**: constraint-driven creator expression. MYM's distance-to-path math taught builders to think in "threat per Synthite"; this teaches "menace per tile."
- **Asymmetric loop**: builder squeezes maximum lethality from a fixed budget; raider feels the elegance as "this dungeon is *tight*, every room mattered."

### 2. Dungeon Narrator (small)

When publishing, the builder picks ONE hero from their roster as the dungeon's narrator. That hero's name, class, current mood, and last 3 chronicle entries get baked into the dungeon's metadata. Inside the dungeon, flavor strings render: *"Brother Aldric (Cleric, Despondent) shaped these walls during a long depressive episode."* Room descriptions inherit the hero's voice. The narrator is locked from the builder's roster for 3 days — small commitment cost. The real weight comes from the fiction: your hero is *visibly* the soul of a published dungeon that other named players raid; their chronicle accumulates entries about strangers' deaths and triumphs. The 3-day lock is just enough to feel like a real choice without breaking early-game players who only have a 4-hero roster.
- **Builds on**: hero chronicles, mood, relationships, Steam ID.
- **MYM pillar preserved**: "your maker is a person." MYM did this with a one-line author bio; HeroGuild can do it with an actual character, which is *stronger fiction* than MYM ever had.
- **Asymmetric loop**: builder gets fictional embodiment of authorship; raider's party encounters a named, moody nemesis instead of an anonymous level.

### 3. Chronicle Crossings (medium)

When a raider's session ends with **substantial engagement** (cleared OR ≥5 attempts within the session) — one summary entry writes to BOTH chronicles: the builder's Dungeon Narrator (narrator hero, see #2) and the raider's **party leader** (the first hero in the party slot). Peek-and-leave sessions (1–4 attempts and no clear) skip the chronicle write to keep heroes' life stories uncluttered. Re-raids are treated independently — each substantial session writes its own entry, so a player who clears the same dungeon five times gets five distinct chronicle entries, each its own narrative arc. The builder's narrator gains *"Brother Aldric watched a Rogue named Vashti (urummi's party leader) batter herself against his trap forty-seven times before finally cracking it — he felt grudging respect"* and the raider's leader gains *"Vashti led Aldric and Tomas into the Iron Catacombs, authored by Antoni (urummi), and prevailed on her 48th attempt."* The Steam display name of the *other* player anchors the entry. Only the leader receives the entry — non-leader party members get mentioned in-text but not their own chronicle line, keeping each hero's life story uncluttered. This is the highest-leverage social mechanic in this document — every raid session becomes a permanent two-way piece of fiction.
- **Builds on**: chronicles, hero relationships, Steam-authenticated identity, audit log.
- **MYM pillar preserved**: replay + accolades. MYM showed you "a raider you'll never meet died here." HeroGuild writes "a raider you'll never meet died here, and we both have a permanent record of it." Stronger and cheaper than a replay system.
- **Asymmetric loop**: builder gets durable bragging-rights inscriptions in their hero's life story; raider gets a ghost story in *their* hero's chronicle, citable forever.

### 4. Per-Dungeon Leaderboard (small)

**The leaderboard is first-session-only and version-scoped.** Only each Steam ID's *first session against the current dungeon version* counts for leaderboard placement. Subsequent re-raid sessions never appear, no matter how good the time. Previous-version leaderboards archive to an "Old Leaderboards" tab when the architect edits and republishes (see Part D's "Dungeon versioning" subsection). Rationale: a re-raid by a player who already knows the dungeon (even with tree reset) is a fundamentally different challenge than a first-time blind run, and ranking the same player twice — or ranking against an outdated dungeon shape — creates leaderboard dishonesty.

Top 10 first-session clears per dungeon, sorted by tree depth at clear (fewest decisions = most elegant) -> attempts (efficiency) -> turns elapsed -> survival (no hero deaths). Display the Steam name and party composition.

**Dungeon stats panel (separate from the leaderboard)** shows aggregate engagement: total raids, total players who've attempted, average attempts to first clear, average sessions per player, fastest re-raid time as a fun-fact ("cleared in 1:23 on session 5 by RushKing"). Re-raid stats live here, where they're informative without polluting the rankings.

Tree-derived sorts only become meaningful once Part D ships, but the leaderboard schema can be designed up front to accommodate them.
- **Builds on**: Steam ID display, dungeon ratings, run records.
- **MYM pillar preserved**: featured outposts / vault hunter rankings.
- **Asymmetric loop**: builder gets a public roll-of-honor for those who beat them; raider gets durable proof they cleared a notable dungeon.

### 5. Observed Difficulty (small)

Replace the builder's claimed star rating with observed signals: "Author claims: 3 stars" alongside "Observed: 4.2 stars (avg attempts-to-first-clear = 8.6, calculated only from each Steam-ID's first session; avg party power of clearing parties = 1,840)." Once Part D ships, **attempts-to-first-clear** is the headline number — it's the most honest difficulty signal possible, since it's measured against actual raider experience rather than party power. **First-session-only** is critical: a re-raid by a player who already knows the dungeon's general shape (even with a reset tree) doesn't measure difficulty, it measures familiarity. Builders who chronically over-rate or under-rate take a small reputation hit visible on their author page. MYM did exactly this in patch 1.4.
- **Builds on**: existing rating field, run telemetry.
- **MYM pillar preserved**: dynamic difficulty.
- **Asymmetric loop**: builder is held honest; raider gets a trustworthy difficulty signal.

### 6. Architect Seasons / League Rotation (medium)

Each Monday a new **league** opens — a fresh week-long competition with a posted metric. The metric cycles through a **fixed rotation** of axes so players know what's coming and can plan: Week 1 = lowest tree depth at clear (elegance), Week 2 = lowest attempts to first clear (efficiency), Week 3 = fastest clear time (speed), Week 4 = stealth-clear (no detection / no ambushes triggered). After Week 4, the cycle repeats. Predictable cadence beats randomized metric chaos for player planning, Discord posting, and content-creator pre-announcement. Dungeons authored or re-engaged with during the league count toward its leaderboard.

**League rotation (PoE-style).** When a league ends, its leaderboard rolls to a permanent **Legacy League** archive — browsable forever, sortable by past league, but no longer competing with current standings. Top 3 architects per league earn permanent placement in the **Hall of Notorious Architects** (accumulates across all past leagues — every top-3 finish is preserved) and a top-of-screen ribbon for the *following* league's week.

**What persists across leagues:** dungeons themselves (they don't expire), raider chronicles, Watcher journals, session counts, Architect Pages reputation. **What rotates:** the *competitive frame* — current leaderboard, current league metric, the spotlight ribbon. Architects' permanent reputation accumulates across leagues; their *current standing* is league-local.

Reuses the existing weekly bounty scheduler. This is the single mechanic most likely to make HeroGuild twitter-postable.

**Optional later evolution: league mechanics.** Per-league global modifiers — e.g., "this league all dungeons receive a global stealth penalty," or "this league chooses one featured architect class to spotlight," or "Crimson League: all hazards have +1 severity." MYM did themed Bunker events; PoE leagues are built on this. Could ship in a later weekend if the design appetite is there. Not committed to in the initial roadmap.

- **Builds on**: weekly bounty timing, dungeon ratings, Steam display name, lifetime-aggregate session counts.
- **MYM pillar preserved**: creator economy, social-recognition funnel. MYM's content-creator funnel failed because individual outposts were the unit; weekly themed competition makes *the builder*, not the artifact, the unit of fame. PoE-style league rotation adds a healthy "fresh start" rhythm that prevents stale leaderboards from dominating.
- **Asymmetric loop**: builder gets a weekly named-stage to compete on; raider gets a curated weekly playlist with stakes; both get a permanent legacy archive of past competitions.

### 7. Proof of Clear (medium)

Before publishing, the builder MUST clear their own dungeon. Once Part D ships, that means submitting a complete tree from entry to clear; the tree gets stamped into the dungeon's metadata as *the builder's reference clear*: "Authored and cleared by urummi with Warrior(12)/Cleric(11)/Rogue(10) in 14 decisions, 3 hero deaths, 47 turns." If the builder can't beat it, neither can anyone else; the published tree depth becomes the public lower bound that other raiders' clears get measured against. This is the strong gate against unbeatable-outpost grief — the 036 admin queue catches malicious abuse, but proof-clear scales without admin labor.
- **Builds on**: existing offscreen-resolution combat, audit log, publish flow.
- **MYM pillar preserved**: anti-grief without active moderation. MYM's biggest unsolved problem; this is HeroGuild's single best lever against it.
- **Asymmetric loop**: builder commits to a beatable design and gets to flex their own optimal party; raider knows there exists a clearing party and can study it.

### 8. Fame Decay (small)

A dungeon unplayed for 60 days slides to an **Archive** tab — still searchable, still playable, just not in the front-page rotation. Replays and chronicle entries persist; only catalog placement changes. MYM's "Social tab" was this idea but with the brutal Prestige-10 hard cutoff; soft decay is kinder and doesn't punish the long tail.
- **Builds on**: existing browser sort, run timestamps.
- **MYM pillar preserved**: catalog freshness without catalog destruction.
- **Asymmetric loop**: builder isn't punished for old work but the front page stays alive; raider always sees recent stuff first.

### 9. Two-Stage Publishing (medium)

Publish as **Draft** by default. Drafts are visible only via direct link or Architect Seasons. After 10 successful clears OR an explicit promote action, the dungeon enters the main catalog. Ratings during the draft phase count toward the builder's reputation — meaning a builder can't farm "first impressions" by re-publishing. Combines with #7 (proof-of-clear gates draft -> public, not unpublished -> draft).
- **Builds on**: publish flow, ratings, audit log.
- **MYM pillar preserved**: quality gating without admin gatekeeping.
- **Asymmetric loop**: builder can iterate before a reputation hit; raider's main browse experience is curated by community survival, not RNG.

### 10. Architect Pages (small)

Every Steam-ID with at least one published dungeon gets a public author page: list of dungeons, lifetime clear rate, total chronicle entries written into other players' heroes, accolade tally, current Architect Season ranking. This is the durable fame surface MYM never built — its top builders had no in-game profile worth visiting.
- **Builds on**: Steam ID, ratings, run records.
- **MYM pillar preserved**: creator economy. MYM treated outposts as the durable artifact and builders as evanescent; HeroGuild treats the builder as the durable artifact, which fits a smaller community better.
- **Asymmetric loop**: builder accrues a CV; raider can follow architects whose work they liked.

### What I deliberately did NOT include

- **Live "outpost upgrade after deaths."** No live raider, no point.
- **Replay videos as primary social object.** Turn-based simulation doesn't make a viral 10-second clip. Chronicle entries (mechanic 3) are the equivalent.
- **In-dungeon currency-extracted-from-deaths.** MYM's GenMat-from-corpses loop was a Skinner-box that needed live raid frequency to feel rewarding. HeroGuild's async pacing kills it.
- **Builder-vs-raider matchmaking tiers.** MYM did this because raider skill varied 100x. AI parties have a knowable power level; matchmaking reduces to the menace-vs-power signal in #5.

---

## Part D — Trials: the missing skill layer

**Feature name: Trials.** (Working title was "Interactive Raid" during early design; finalized to "Trials" because it's evocative, single-word, marketing-friendly, and consistent with HeroGuild's existing tone — chronicles, missions, taverns, trials.)

### The gap

Part C's 10 mechanics all sit on the social-recognition layer *above* the raid. None of them give the raider skill expression *during* the raid itself. Today a Custom Dungeon run is "pick party, watch turn log, see outcome." The builder authors with full creative control; the raider is a spectator. Even the best-named-architect dungeon plays out, for the person running it, exactly like a normal one.

This section adds the missing layer: a tactical decision flow inside Custom Dungeon raids that turns the raider into an active player without touching the global combat engine.

### Scope: Custom Dungeons only, desktop only, clean wipe

Trials applies *only* to Custom Dungeons. Mission-board dungeons, story dungeons, and other procedural content keep the existing offscreen-resolution flow — they're not authored asymmetric content and don't benefit from per-decision pauses.

**Existing Custom Dungeons are wiped at Part D rollout.** All previously-published dungeons get deleted; architects must republish in the new format with patrols, LOS, and tree-aware design. This is the cleanest possible migration — no auto-conversion edge cases, no two-class catalog, no compatibility scaffolding. Architects get a final notice + JSON export option before deletion so beloved old designs can be manually re-authored. The wipe is a one-time event; future Part D iterations don't re-wipe.

**Platform scope: desktop only.** Trials does not ship to mobile. The pause-decision UX, tree visualization, hazard-counter pickers, and patrol-aware combat assume mouse/keyboard precision. Mobile users keep access to *browsing* (Architect Pages, Chronicles, Leaderboards, Watcher Mode journal viewing) but cannot raid Custom Dungeons after the wipe — Custom Dungeons becomes a desktop-only feature.

### The mechanic — decision pauses on a per-session exploration tree

A Custom Dungeon raid becomes a sequence of decision pauses at every meaningful node:

- **Crossroads** — which path?
- **Hazard** — which class ability handles it, or eat the consequence? This leans directly on the 035 hazard catalog, where every hazard already has class-specific counters. Class options divide along **two axes**: scope (single-trap vs. multi-trap) and permanence (permanent vs. re-arming):

  - **Rogue — Disable.** Act on a single trap, **permanently disabling** it (no re-arm). Higher resource cost. Surgical, reliable for chokepoints where the party will linger. Best for: known-bad single trap blocking the optimal path.
  - **Mage — Dispel.** Magical neutralization. Single trap, permanent. Similar shape to Rogue but with magical hazard scope (Magic Seals, Cursed Altars, etc. that Rogue's mundane skills can't touch).
  - **Cleric — Purify.** Cleanses cursed/desecrated effects. Single trap, permanent. Like Mage but for the holy/cursed axis of hazards.
  - **Necromancer — Send Undead Ahead.** Summon a temporary undead minion that walks forward and triggers traps in its path. **Multiple traps possible** if they're in the same scope/corridor. Lower resource cost per use. Critical wrinkle: traps have **re-arm times** (see below) — fast-rearming traps may be live again by the time the party reaches them, so this option is *efficient but time-sensitive*. The minion has its own LOS exposure, making it a tactical scout that doubles as trap clearance — but also vulnerable to patrol detection.
  - **Ranger — Perception bonus.** No direct hazard-counter ability, but gives the party a **perception bonus** that extends the vision pool's range (see LOS), boosts trap-detection rolls (sights traps earlier/further), boosts ambush-detection rolls, and gives Rogue a success-rate bonus on Disable. Functions as a force-multiplier for the trap-handling specialists rather than a primary trap-handler. A party with one Ranger sees more, gets ambushed less, and disables more reliably. A party with two Rangers compounds the bonus (with diminishing returns).
  - **Warrior:** no hazard-counter ability and no perception bonus — pure damage absorber. "Eat the trap and tank through" becomes the Warrior's tactical role; in a party without a Rogue/Mage/Cleric/Necromancer, the Warrior is the one who triggers the trap on purpose to clear the path for the rest of the party.

  **Trap re-arm.** Each trap has a re-arm time measured in dungeon turns. When triggered, traps cycle: `armed → triggered → re-arming → armed`. Fast-rearming traps (1–2 turns) stay dangerous after Necromancer clearance; slow-rearming traps (10+ turns) effectively become single-shot. Re-arm time is a design parameter the architect tunes per trap — creating real tactical tension between Rogue's permanent-but-costly disable and Necromancer's broad-but-temporary trigger.

  Class abilities run on **per-attempt cooldowns** that refresh on dungeon-reset (i.e., every party-wipe). Death is genuinely free — every retry starts with full cooldowns.
- **Monster ambush** — the existing global combat engine resolves the encounter as one atomic node. Survivors and losses feed the tree as a single resolved decision; combat code itself is unchanged.
- **Event / chest / altar** — the existing dungeon-event decision UI generalizes here.

Each decision point is a node. Each option you've taken is an edge. Within a single raid session, your decisions accumulate into a navigable tree of *your* knowledge of *this* dungeon.

### Line of sight, awareness, and dynamic ambush

Decisions only become available for things your party can *see*. The party shares a **collective vision pool** — any tile sighted by any party member is sighted for the whole party. The pool's range is set by the highest-perception party member (so a Rogue or Ranger in the lineup extends the party's effective sight). Tiles outside the pool are dark on the green-line overlay. A trap nobody has sighted can't be disarmed in advance — it has to be triggered or avoided blindly. A monster behind a corner has surprise on you until first contact.

**For builders:** LOS becomes a design tool. Place traps with sightlines that depend on party formation. Place watchers down corridors. Build dim/dark zones that punish high-perception-poor parties. Architects who carve open sightlines reward Rogue-heavy teams; architects who twist corridors and cut LOS reward parties willing to walk into the unknown.

**For raiders:** party composition matters mechanically. The Mage's "Light" cantrip becomes a tactical resource. Dark zones are terrifying because the tree shows nothing past them — you're navigating an unmapped frontier even when other parts of the dungeon are mapped. A party without a perception specialist sees less, sights traps later, and gets ambushed more.

**Monster patrols and dynamic ambush.** Monsters aren't static room-bound encounters. They patrol the map on builder-defined routes (or simple wander-in-region defaults), and their LOS works against you symmetrically: if a patrolling monster sees the party — or hears combat noise in an adjacent corridor — it can move to converge. This turns combat into something messier than "fight one room, move on." A fight against three goblins can become a fight against three goblins plus the watchman that heard the screams from two rooms over, plus the wolves that smelled blood. **Ambush probability** is rolled at the moment of detection: a stealthy party (Rogue scouting ahead, Mage casting Silence) reduces the roll; a noisy party (Warrior in plate, casting fireball) increases it. The architect can tune patrol density and aggression as part of the dungeon's menace budget; raiders can use Silence, Smoke, Stealth abilities, or careful pathing to mitigate.

LOS implementation: standard 2D-grid shadowcasting (cheap, well-understood), per-party-member visibility, per-monster visibility, audible-range broadcasting on combat events. Decision options on the pause UI hide hazard-counter abilities for hazards your party can't see. Pause UI fires whenever a new monster enters LOS of any party member ("Watchman sighted at corridor end — engage / hide / flee"), even mid-traversal between decision nodes.

### Death, replay, and the tree

When the party is wiped, the dungeon resets to its entrance and **the full party returns to life** — heroes never permanently die from a Custom Dungeon attempt. Only the dungeon state resets between attempts; the tree survives within the session. On replay you can:

1. Walk the tree manually — every decision again, full control.
2. **Auto-fast-forward to any explored node.** The prefix replays automatically with no per-decision confirmation; you take manual control from that node onward.
3. At any explored node, pick a different edge than last time. Past it is unknown territory; the next pause is a real decision.

The tree is volatile. It exists from the moment you enter the dungeon to the moment you leave — and "leave" is strict. Clear, retreat-to-town, app close, crash, idle timeout: any exit wipes it. A second raid of the same dungeon starts blank.

This is deliberate. It prevents tree-sharing as spoiler currency, keeps each revisit fresh, and matches HeroGuild's "leaderboards yes, route sharing no" stance. What persists past the session is a *summary*: deepest node reached, attempts spent, time elapsed, final outcome — written to the leaderboard and as one chronicle entry per session into the raider's party leader and the builder's Dungeon Narrator (see #3 Chronicle Crossings for entry shape).

### Visualization

A green-line path overlay through the dungeon, numbered at each decision node, toggleable on/off so the dungeon view stays clean during manual play. Click any edge to fast-forward up to it. Frontier (un-explored) nodes are dimmed; LOS-occluded tiles are hidden entirely until sighted. No graph-view UI needed — the dungeon map *is* the tree, drawn on top of it.

### Non-determinism — the tree records paths, not outcomes

Auto-fast-forward through known nodes does NOT replay outcomes — it replays *decisions*. Outcomes always re-roll. Sources of RNG include hero skill checks (Rogue's perception roll for hidden traps, Cleric's hazard-identification, ambush awareness), trap-triggering order when multiple are placed in proximity, hazard severity rolls, monster patrol positions at moment-of-encounter, ambush-detection rolls, and combat resolution itself (already RNG-based via the existing engine).

The tree records "I chose to disarm" — not "the disarm succeeded." On replay, auto-fast-forward pauses when the situation has materially diverged from the recorded run.

**Divergence threshold rules (default):**

1. **Always pause on outcome-class change.** Categorical events that change *what kind* of result happened: hero died vs. survived, ambush triggered vs. didn't, trap triggered vs. avoided, combat won vs. lost, patrol detected the party vs. walked past.
2. **Always pause on critical HP state.** If, after a re-rolled outcome, any party member is now below 30% HP OR the party's total HP is below 50%, fast-forward stops — even if no categorical change occurred. The state going forward is now risky enough to warrant a manual decision.
3. **Ignore raw damage variance.** If the previous run took 5 damage and this run took 25 damage but everyone is still above the HP threshold and no categorical event differed, fast-forward continues. Avoids noise from routine RNG fluctuation.

**Player-tunable sensitivity slider** in the pause UI: Low / Medium (default) / High. Low pauses only on outcome-class changes (categorical only — speedrunners). High pauses on any meaningful divergence including damage variance >25% (cautious players who want to micromanage). Medium is the (1)+(2) combination above. The setting persists per-player, not per-session.

This prevents the dungeon from becoming a memorization game. A "known" path through the tree is statistically likely to succeed but never guaranteed. Skill-based RNG also rewards higher-leveled heroes — better perception sees more, better lore identifies more, better stealth is detected less. Hero progression has direct mechanical leverage on Custom Dungeon performance.

**Mood is a roll modifier.** HeroGuild heroes have mood states (Despondent, Reverent, Confident, etc.) that already shape narrative outcomes. In Trials, mood now also multiplies skill-check rolls — a Despondent Rogue sees fewer traps and disarms less reliably; a Reverent Cleric purifies with a bonus; a Confident party leader gives a small ambush-awareness boost to the whole party. The catalog of mood-to-modifier mappings is /specify-time work, but the principle is locked: mood is a real mechanical input, not just narrative flavor. This wires HeroGuild's existing fiction layer directly into the new tactical layer — your roster's emotional state has stakes during raids, which means it has stakes during the rest of the game too.

### Watcher Mode — the persistent journal

The session tree itself is volatile. The session *journal* is not. Every decision and every outcome — from "entered dungeon" to "cleared / abandoned / retreated" — gets serialized as a replayable log and saved to the player's Watcher Mode tab.

This is the async equivalent of MYM's replay system. **Sharing rules:**

1. The **architect** of the dungeon *always* sees every session against their own dungeon — auto-shared, no opt-in needed. They need this telemetry to learn where their design is failing and which trap or hazard is doing the work.
2. **Public sharing** (other players, content creators, friends) is **opt-in per session** by the raider. Default state on session end is private-but-architect-visible. The raider can mark a memorable run public, leave it private, or delete the journal entirely.
3. The raider always sees their own past sessions in their personal Watcher tab.

**Architect Watcher tab — filtering and sorting.** Critical UX, because a popular dungeon accumulates hundreds of journals fast and an unfiltered list is useless. The tab supports:

- **Sort by:** attempt count (surface the easy clears AND the brutal grinds), tree depth at clear (find the most elegant solutions), session length (longest engagements), outcome (cleared / abandoned / retreated), date.
- **Filter by:** dungeon version (see versioning below), raider party composition, raider Steam name, time period, outcome.
- **Aggregate views:** heatmap of which decision nodes get visited most, which traps generate the most kills, which paths lead to clears, average attempts per session, percentage of sessions abandoned at each node.

The goal is to let the architect actually *use* the data — spotting the unintended easy path through their dungeon, the trap that's too punishing, the corridor nobody takes — not just drown in raw replay logs.

What Watcher Mode is NOT: a way to copy the tree. The journal shows what *one specific raider* did in *one specific session* with *one specific RNG seed*. A new raider watching it learns the dungeon's general shape but still has to play their own session against fresh rolls (perception checks, patrol positions, ambush dice). This preserves the no-spoilers stance while restoring MYM's "replay culture" social object.

Storage: compact action log per session (~10–50 KB typical). Serializable, sharable via Steam display name + dungeon ID. Persistence: indefinite for the session's own player and the dungeon's architect; auto-archived after 90 days for other viewers (public-marked sessions).

### Dungeon versioning and edit handling

When an architect edits a published dungeon, the changes don't apply retroactively to in-progress sessions or already-recorded data. Each publish-after-edit creates a **new versioned dungeon record**:

- **Version-locked leaderboard.** The previous version's leaderboard archives to an "Old Leaderboards" tab on the dungeon page (browsable forever). The new version starts with an empty leaderboard. This prevents the dishonesty of a 1:23 clear time still ranking against a dungeon that has since had a corridor added.
- **Version-locked journals.** Watcher Mode journals stay attached to the version they were recorded against. Reading "session journal v3 of Iron Catacombs" tells you exactly which dungeon shape it represents. Cross-version journals don't exist.
- **Version-locked chronicle entries.** A chronicle entry written from a v3 session names the version in its prose ("Vashti raided the Iron Catacombs v3, authored by Antoni"). When v4 ships, the v3 entry remains historically accurate.
- **Aggregated stats.** Architect Pages aggregate lifetime stats across all versions (total clears, total players, total sessions). Per-version stats are also viewable for granularity.
- **In-progress sessions.** A session that started before an edit completes against the version it started on; the version freeze happens at session-start, not edit-time. This prevents mid-session geometry shifts that would invalidate the player's tree.

Architects who want to iterate aggressively use **Two-Stage Publishing (#9)** to keep changes in Draft mode (no leaderboard, no journals counted) until they're ready to publish a stable version. Once public, every edit creates a new version and the previous one archives.

### Death cost and the win-win economy (active-time-based)

The raider pays no in-game cost for deaths within a session — only time. There is no hard attempt cap; raiders can keep grinding indefinitely if they want. Their own end-of-session rewards (chronicle entry, leaderboard credit, clear bonus) are *guaranteed* on substantial sessions regardless of attempt count.

**Architect earnings are based on active time spent in the dungeon, not attempt count.** This is the cleaner economic model:

- **Per-second tick.** Architect earns a small gold/reputation tick per second of active raider engagement (decisions taken, combat resolved, navigation events, fast-forward replay running, etc.).
- **Idle detection.** The session pauses earnings when the raider is idle — no input for ~60 seconds, browser tab unfocused, pause menu open without interaction. Leaving the laptop for lunch with the dungeon open earns the architect zero. This is critical anti-exploit infrastructure.
- **Substantial-session gate.** A session must accumulate at least ~3 active minutes before the architect earns *anything*. Shorter than that = peek-and-leave, no payout. (The 3-minute threshold is /specify-time tunable.)
- **Soft cap per session.** Earnings have diminishing returns over very long sessions — the 30th active minute earns less than the 5th. Prevents one obsessive raider from inflating payouts without bounding genuine play.
- **Re-raids reset.** Each new session restarts the curve — a devoted fan returning daily earns the architect full payouts each day. This is fine: scales naturally with sustained engagement.

Why this design beats attempt-count-based earnings:
1. **A 47-attempt grinding session represents real engagement** — and pays the architect proportionately because the time was real.
2. **A 2-attempt skill-clear by an expert** earns the architect modest time-based gold rather than zero — the architect still made a dungeon worth playing.
3. **Idle/AFK exploits are blocked at the source** — earnings track activity, not session-existence.
4. **Open-and-close session farming is impossible** — the substantial-session gate kills it.

Architects whose dungeons get casually cleared in 2 minutes earn pennies. Architects whose dungeons hold raiders' attention for 20–40 active minutes earn the most. Architects whose dungeons get abandoned in disgust at minute 4 earn less. The active-time curve naturally pays for "challenging and engaging" dungeon designs.

### Re-raids and metric scope

After clearing (or abandoning) a dungeon, a raider can return for additional sessions. Each session is fully atomic:

- **Tree resets to blank.** Fresh exploration every time, no carry-over knowledge between sessions. Even your fifth session against the same dungeon starts with no map, no node history, no remembered branches.
- **Journal is new.** Each session writes its own Watcher Mode log; the architect sees them all stacked.
- **Chronicle entry** writes only on substantial sessions (cleared OR ≥5 attempts). Peek-and-leave sessions skip the chronicle to keep each hero's life story uncluttered.
- **Architect earnings** restart with the full diminishing-returns curve every session, with no lifetime cap. A devoted fan re-raiding 50 times earns the architect 50 sessions of peak-curve gold — which is fine: it scales naturally with engagement.

**Two metric tiers** flow from this distinction. Several Part C mechanics need to specify which tier they read from:

- **Session-level metrics** (within one session): attempts, tree depth at clear, turns elapsed, stealth status, hero deaths, ambushes triggered, outcome.
- **Lifetime-aggregate metrics** (per Steam-ID + dungeon, across all sessions): total sessions, sessions cleared, best session by each axis, first-session metrics.

Mechanic-by-mechanic clarifications:

- **Per-Dungeon Leaderboard (#4)** — best session per Steam ID (one entry per player, not all sessions), with **session count displayed alongside** so observers can read the context: "PB 1:23 — best of 12 sessions" reads differently than "PB 1:31 — first try."
- **Observed Difficulty (#5)** — first-session-only on attempts-to-first-clear. Second-session-onward signals are polluted by prior knowledge of the dungeon's general shape (even though the tree itself reset, the player remembers it's *clearable*).
- **Chronicle Crossings (#3)** — one entry per substantial session (cleared OR ≥5 attempts), so a player who clears the same dungeon five times gets five chronicle entries — each a distinct narrative arc.
- **Architect Seasons (#6)** — all in-league sessions count for the architect's metric. Re-raids inflate engagement signals, which is exactly what seasonal rankings should reward.

### Why HeroGuild specifically

1. **Combat engine untouched, but invoked from new contexts.** All new code is decision-tree state machine plus pause UI; the combat engine itself stays the single source of truth. However, the *invocation surface* changes: combat can now be triggered mid-traversal by a noise-attracted patrol arriving as reinforcement, or by an LOS-driven ambush detection. The existing combat caller will need a small extension to pass "ongoing-fight + arriving-reinforcements" context — a thin shim, not a rewrite.
2. **035 hazards are already class-coded.** Toxic Gas wants a Mage, Magic Seal wants a Cleric. Today the dungeon resolution applies these effects as automatic checks; Trials is the surface that lets the player *choose* to deploy class counters, turning hazards from stat checks into tactical decisions.
3. **Existing dungeon-event UI generalizes.** The decision-with-options pattern shipped with chronicles has the visual vocabulary. Scaling it to every dungeon node is increment, not invention.
4. **Async-friendly.** No live opponent. A session can sit paused indefinitely.

### Synergies with Part C

Trials makes every Part C mechanic land harder:

- **Chronicle Crossings (#3)** entries cite the *specific* arc: *"Vashti raided the Iron Catacombs across 47 attempts, dying again and again to the chasm she refused to leap, until the 48th run when she finally jumped."* A tree turns "she died here" into "she died here trying X, finally won by trying Y."
- **Proof of Clear (#7)** is more than party-comp metadata. The builder must clear their own dungeon, producing a tree of their own; clearing-tree depth becomes the published lower bound.
- **Per-Dungeon Leaderboard (#4)** ranks on multiple honest axes from one mechanic: tree depth at clear (elegance), attempt count (efficiency), time, and — once LOS and patrols are live — **stealth-clear** (no detection / no ambushes triggered) and **blind-clear** (no auto-fast-forward used).
- **Architect Seasons (#6)** unlocks new metric axes: lowest attempts to first clear, lowest tree depth at clear, fewest dead-end edges, blind-clear, stealth-clear, no-Mage-clear (forced class-omit challenges).
- **Architect's Budget (#1)** gains teeth — a dungeon with 80 decision nodes but a 12-step optimal solution rewards builders who design for tree *shape*, not just trap density. With patrols and LOS as menace-cost-bearing elements (a patrol covering three corridors costs more than three static encounters), the budget shapes architectural style as well as content density.
- **Observed Difficulty (#5)** uses average-attempts-to-first-clear: far more honest than a star rating. With non-determinism, "average" means something — it filters out lucky one-shots.
- **Architect Pages (#10)** become a Watcher Mode showcase: the architect's most-watched journals, hardest-to-clear dungeons, and "best ambush moments" become exhibit pieces, building durable creator fame in a way MYM never did.

### Honest cuts from the broader Tower Defense GDD draft

A separate GDD sketch ("Tower Defense Asimétrico con Auto-Battler") proposed a much larger system. For HeroGuild scope, the following are cut or deferred:

- **Dual builder/raider currency (Steel/Tech).** HeroGuild already runs on gold + reputation + chronicles. A parallel currency split is exactly the Synthite-shaped treadmill MYM walked back from.
- **Explicit Scout vs. Assault run modes.** The session tree *is* the scout layer — every first run is exploratory by nature. Gating that behind an opt-in "scout phase" doubles the UI surface for no behavioral change.
- **Manual mid-combat ability activation.** Violates the "global combat engine untouched" constraint. Pre-combat class abilities at hazards do the same job at much lower cost.
- **Blind Race / synchronous multiplayer modes.** Off-genre and off-roadmap. HeroGuild's strength is async fiction, not real-time competition.
- **If-then conditional automation rules.** Auto-fast-forward through explored nodes already does the real work. Per-condition logic adds a programming layer most players won't touch and is anyway irrelevant — trees don't persist between sessions.
- **Energy / gold cost on retries.** No-cost retries with architect-side reward scaling is a cleaner asymmetric incentive.

### Testing strategy

Every Part D sub-feature ships with tests. The surface breaks down as follows:

| Feature | Test approach | Difficulty |
|---------|---------------|------------|
| Tree state machine | Standard unit tests on decision recording, edge addition, fast-forward, session reset | Easy |
| LOS / shadowcasting | Property tests on visibility math, symmetry, occlusion fixtures | Easy |
| Monster patrols | Scripted scenarios on fixed maps with stubbed RNG; tests for LOS-react, noise-react, mid-combat reinforcement arrival | **Medium-hard** — biggest state space |
| Non-determinism / divergence detection | Compare-current-vs-prior-outcome logic; stub RNG at test boundary for distribution checks | Medium |
| Editor rework | Patrol authoring CRUD, waypoint validation, save/load round-trip | Medium |
| Diminishing-returns economy | Pure math, easy unit tests on the curve and per-session resets | Easy |
| Watcher Mode | Log serialization round-trip + log-driven render correctness | Easy |
| Re-raids / metric tiers | Data-layer tests with multi-session fixtures (first-session filter, best-per-Steam-ID, lifetime aggregates) | Easy |
| League rotation | Clock-mocked weekly cycle tests; archive snapshot, Hall accumulation across leagues | Medium |

**Critical test-design note: Watcher Mode is replay-by-log, not replay-by-execution.** The session journal stores `{decision chosen, outcome observed, state snapshot}` per event; the replay player walks the log and renders each frame. No RNG re-roll, no seed needed for replay. The recorded outcome IS the outcome. This means: (a) Watcher Mode tests are simple round-trip checks, (b) the global combat engine does not need to expose a seed parameter as a production concern, (c) tests can stub/seed RNG at the test boundary using standard patterns without production-side coupling. Future implementers should not re-introduce a "replay re-executes with same seed" coupling — the log-driven design is intentional and simpler.

**Patrol AI is the heaviest test surface.** Scripted-scenario fixtures cover the deterministic core, but emergent cases (patrol arrives during ongoing combat from a noise broadcast, two patrols converging, ambush during reinforcement arrival) need careful test design. Budget ~0.25 weekend dedicated to test infrastructure on the patrol-runtime weekend.

### Effort

**6.5–8.5 weekends of solo-dev work**, broken down:

- *Core tree mechanic* (1 weekend): tree state machine, decision-pause UI, fast-forward replay, toggleable green-line visualization, single-session in-memory persistence, summary writes to chronicles + leaderboard at session end.
- *LOS runtime* (1 weekend): 2D-grid shadowcasting with party-collective visibility pool, audible-range broadcasting on combat events, dim-tile rendering, decision-availability gating on sighted-or-not.
- *Monster patrols + dynamic ambush runtime* (1.25 weekends — runtime + dedicated test infrastructure): patrol pathing, monster-side LOS checks, noise-attraction logic, ambush-detection rolls, mid-traversal pause UI ("monster sighted, engage / hide / flee"). The +0.25 buffer is for scripted-scenario fixture design — emergent multi-patrol cases need careful test setup.
- *Editor rework for patrols* (1–2 weekends): the current dungeon editor has static encounter rooms only. Patrol authoring requires waypoint paths, region-wander zones, aggression triggers (LOS-react / noise-react), and per-dungeon patrol density caps. This is significant editor work and is a hard prerequisite for monster patrols at runtime — could even be extracted as its own spec.
- *Non-determinism layer* (0.5 weekend): RNG hooks at hazard severity, perception checks, patrol position, ambush detection. Mostly plumbing — divergence-detection on auto-fast-forward (when a previously-survived outcome now differs meaningfully) is the trickiest part.
- *Active-time-based economy* (0.5 weekend): per-second activity ticker, idle detection (input timestamp + tab-focus + pause-state), substantial-session gate, soft-cap diminishing curve over long sessions, gold/reputation writes per active second, end-of-session settlement. Idle detection is the critical anti-exploit piece.
- *Watcher Mode journal* (1 weekend, can defer): action-log serialization, replay player UI, scrubbable timeline, sharing flow with auto-architect-visibility + opt-in-public.

Reuses: existing combat engine, 035 hazard catalog, dungeon-event UI, Steam-auth identity from 036, weekly bounty scheduler.

This is by far the largest feature in this document. It is also the only one that gives the raider a play experience as expressive as the builder's. Without it, Custom Dungeons remains a half-loop. If scope must be cut, defer Watcher Mode (ships independently without blocking anything else) and consider extracting the editor rework as its own spec.

---

## Shipping Order (10 weekends)

**Weekend 1 — Spec 037 — the spine.** #2 Dungeon Narrator + #3 Chronicle Crossings + #10 Architect Pages. Together they convert Custom Dungeons from "user level browser" to "named-author social game." Chronicle Crossings is the load-bearing one — its initial form writes generic outcome lines; later specs retroactively upgrade those entries with tree depth, decision specifics, ambush narrative, and stealth/no-detection facts as each runtime piece comes online. Ships entirely on already-shipped systems (036 Steam-auth + chronicles); cheapest opener.

**Weekends 2–3 — Spec 038 — Editor patrol rework.** The current dungeon editor has static encounter rooms only. Patrol authoring needs waypoint paths, region-wander zones, aggression triggers (LOS-react / noise-react), per-dungeon patrol density caps, and the Necromancer's summon-units placement. Shipped as its own spec because (a) the editor is a distinct subsystem, (b) it can be tested independently with editor-only fixtures, (c) it gates Trials runtime — getting it wrong costs all subsequent weekends. The Custom Dungeon wipe migration also lands here (delete existing dungeons + JSON-export tool for affected architects).

**Weekends 4–6 — Spec 039 — Trials runtime (Part D).** Spans three weekends: W4 core tree mechanic + visualization + Watcher Mode journal capture (serialization only, no playback UI), W5 LOS runtime + party-collective vision + non-determinism plumbing + monster patrol runtime + dynamic ambush + combat-invocation shim + mood-as-roll-modifier, W6 diminishing-returns economy + re-raid metric tier wiring + tutorial scaffolding for first-time raiders. This is the largest feature in the doc and the one that gives raiders skill expression. Every later spec assumes it.

**Weekend 7 — Spec 040 — the honesty layer.** #7 Proof of Clear + #5 Observed Difficulty. With Trials live, Proof of Clear means "the builder cleared their own dungeon and we have their tree as the published lower bound." Observed Difficulty uses average-attempts-to-first-clear (first-session-only filter), an honest signal the moment any clears exist. Together they prevent the unbeatable-outpost rot that killed MYM's casual funnel.

**Weekend 8 — Spec 041 — the competition layer.** #6 Architect Seasons / League Rotation + #4 Per-Dungeon Leaderboard. Fixed-rotation weekly metric (depth → attempts → speed → stealth, repeat), Legacy League archive, Hall of Notorious Architects accumulation, best-session-per-Steam-ID leaderboard with session count displayed. Most likely mechanic to drive Steam reviews and Discord engagement.

**Weekend 9 — Spec 042 — the polish layer.** #1 Architect's Budget + #8 Fame Decay + #9 Two-Stage Publishing. Sand the corners. Budget scoring with tree-shape feedback gets builders thinking like designers; Fame Decay and Two-Stage Publishing keep the catalog healthy at scale.

**Weekend 10 — Spec 043 — Watcher Mode playback.** Replayable journal UI for sessions captured starting Spec 039 / W4. Async equivalent of MYM's replay system. Builds on data already being recorded; this weekend adds the player UI, scrubbable timeline, and the auto-architect-visibility + opt-in-public sharing flow.

## What I would cut (MYM-specific cuts)

(Part D's "Honest cuts from the broader Tower Defense GDD draft" subsection covers cuts from the separate tactical-raid GDD draft. The bullets below are the original MYM-specific cuts.)

- **Spectator mode video replay** — originally cut from this design, brought back as Watcher Mode (Part D) because the tree mechanic gave us replay infrastructure for free. The original cut still applies to *video* replay specifically: turn-based async doesn't yield a watchable 30-second clip, so don't try. Watcher Mode ships compact action logs the player walks through interactively — a different format, succeeding where video would have flopped.
- **Ratings/likes as primary social currency.** In a community of low hundreds, a raw five-star rating creates ranking noise more than signal. Use clear-rate, observed difficulty, and Architect Seasons rankings instead. Consider one or two accolade-style tags ("Cruel", "Elegant") only after Weekend 3 reveals what players want to compliment.
- **In-game currency for builders.** MYM's Synthite was a treadmill; HeroGuild doesn't need one. Reputation, chronicle entries, and Architect Season placement are richer signals.
- **Crossover unlocks (clear N dungeons -> unlock builder pieces).** The dual-citizenship unlock pattern worked in MYM because raid/build were the same game. In HeroGuild they're already unified through the hero roster; gating editor pieces behind raid hours just makes the editor feel grumpy.

## Does the asymmetric model fit a single-player-async indie game?

Honest answer: yes, with a caveat — and Part D narrows the caveat. MYM's loop *needed* a high-frequency live-raider population to feel alive: when concurrent raiders dropped below ~500, builders watched their replays with hours of lag and the social-recognition piece broke. HeroGuild's async loop has the inverse property: it scales *down* gracefully because nothing requires concurrency. A chronicle entry written when one of forty active players runs your dungeon at 3am Tuesday lands the same as one written during peak hours. The proof-clear gate, the Architect Seasons cadence, and the fame-decay model all work at 100 active players or 10,000.

The original concern was that an async loop would be *less spectacularly addictive* than a live-raider variant — there's no "someone is dying in my outpost RIGHT NOW" dopamine. Without Part D, that's true; HeroGuild trades thrill for durability. With Part D, the dopamine returns in a different shape: the raider's 47-attempt grinding session ending in a finally-earned clear is the same dramatic arc as MYM's live-raid death, just compressed into the raider's own afternoon — and replayed in their hero's chronicle for years afterward. The architect doesn't *witness* the deaths in real time, but the per-attempt rewards mean they *feel* every attempt as gold and reputation ticking up. The model fits, and Part D is the piece that makes it fit *well*. Ship it.

---

## Sources

- [Meet Your Maker: Designing Destruction (Xbox Wire)](https://news.xbox.com/en-us/2022/08/03/meet-your-maker-preview/)
- [Meet Your Maker — Wikipedia](https://en.wikipedia.org/wiki/Meet_Your_Maker)
- [Meet Your Maker Review — TheGamer](https://www.thegamer.com/meet-your-maker-review/)
- ["No Outpost Is Impossible To Defeat" — TheGamer](https://www.thegamer.com/meet-your-maker-no-outpost-is-impossible-to-defeat/)
- [Meet Your Maker Review — Niche Gamer](https://nichegamer.com/reviews/meet-your-maker-review/)
- [Architectural Sadism review — ScreenRant](https://screenrant.com/meet-your-maker-review-architectural-sadism/)
- [Outpost Prestige — MYM Wiki](https://meetyourmaker.fandom.com/wiki/Outpost_Prestige)
- [Trap Mechanics + Stats (Steam Guide)](https://steamcommunity.com/sharedfiles/filedetails/?id=2960440775)
- [How is your map's Difficulty Decided? — Steam Discussions](https://steamcommunity.com/app/1194810/discussions/0/3829789648152445061/)
- [Patch Notes 31/10/23](https://support.meetyourmakergame.com/hc/en-us/articles/20502343907220-Meet-Your-Maker-Patch-Notes-31-10-23)
- [So Yea, Meet Your Maker Is Just Dead Now — BHVR Forums](https://forums.bhvr.com/dead-by-daylight/discussion/411272/so-yea-meet-your-maker-is-just-dead-now)
- [MYM forums retiring April 5, 2024 — X/Twitter](https://x.com/MeetYourMaker/status/1768385399171203361)
- [Meet Your Maker Steam Charts — SteamDB](https://steamdb.info/app/1194810/charts/)
- [PS Plus 94% drop discussion — Steam](https://steamcommunity.com/app/1194810/discussions/0/3842179871517893608/)
- [Meet Your Maker — DualShockers reveal coverage](https://www.dualshockers.com/meet-your-maker-new-asymmetrical-fps-revealed-by-dead-by-daylight-devs/)
