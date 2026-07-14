# Game Design Document & Comparative Analysis

## Royal Match · Toon Blast

**Case Study — Product Specialist Position, Dream Games**

**Prepared by:** [Candidate Name]
**Date:** July 2026

---

## Table of Contents

- **0. Analyst's Player Profile & Progress** (required opening analysis)
- **Part I — Game Design Document: Royal Match**
  - 1. Introduction
  - 2. Game Mechanics
  - 3. Level Design
  - 4. Level Difficulty
  - 5. Graphics
  - 6. Animation
  - 7. Particles & Special Effects
  - 8. User Interface
  - 9. System Menus
- **Part II — Game Design Document: Toon Blast**
  - 10. Introduction
  - 11. Game Mechanics
  - 12. Level Design
  - 13. Level Difficulty
  - 14. Graphics
  - 15. Animation
  - 16. Particles & Special Effects
  - 17. User Interface
  - 18. System Menus
- **Part III — Comparative Analysis & Product Takeaways**
  - 19. Head-to-Head: Design Philosophy
  - 20. What Royal Match Does Better, and Why It Matters
  - 21. Observations from Royal Kingdom
  - 22. Closing Notes on Method & Assumptions

---

# 0. Analyst's Player Profile & Progress

Before the document itself, a summary of my first-hand experience with the games analyzed here. Everything in this report is based on my own sustained play on a personal device — not on videos, wikis, or second-hand sources — which is why I can speak to how these games *feel* at specific progression bands, not just how they look.

| Game | Developer | My Current Progress | Play Status |
|---|---|---|---|
| **Royal Kingdom** | Dream Games | **Level 550** | Active, daily |
| **Royal Match** | Dream Games | **Level 500–600 band** | Active, daily |
| **Toon Blast** | Peak Games (Zynga/Take-Two) | **Level 500–600 band** | Active, regular |
| **Match Villains** | — | **Level 400–500 band** | Active, casual |

**What this progression band means for the analysis.** Levels 500–600 sit well past the onboarding and early-retention phase of both Royal Match and Toon Blast. By this point a player has:

- Experienced every board booster and every booster combination hundreds of times, and internalized the "combo economy" (which combinations are worth setting up, and when).
- Met all core obstacle types and most of their layered/compound variants, including the versions that only appear in Hard and Super Hard levels.
- Lived through multiple full cycles of the live-ops calendar — weekly leaderboards, win-streak events, team competitions, and limited-time races — and felt how they interlock with the lives/coins economy.
- Hit real difficulty walls, failed levels repeatedly, and faced genuine spend decisions (extra moves, booster purchases, lives refills). This is where the monetization design actually reveals itself.

In other words, this band is where a player stops evaluating the *tutorial* and starts evaluating the *product*. My analysis below is written from that vantage point.

**Cross-title context.** Playing Royal Kingdom (level 550) alongside Royal Match lets me see Dream Games' design language evolving in real time — what the studio kept, what it re-tuned, and what it added in its second title. Toon Blast, as the defining tap-to-blast game from Peak, is the natural reference point for the "other" dominant casual puzzle input model. Match Villains rounds out my view of how other studios execute (and where their polish gap versus Dream Games is most visible: input latency, effect readability, and event pacing).

A note on figures: numeric values quoted in this document (booster thresholds, continue costs, timer durations) are as observed in my own live builds. Both games A/B test aggressively, so individual readers may see slightly different values; the design logic they express is stable.

---

---

# PART I — GAME DESIGN DOCUMENT: ROYAL MATCH

---

# 1. Introduction

*(Single page. The first paragraph summarizes the entire game and its focus; the following paragraphs fill in the structure of the document; the story summary is included.)*

**Royal Match is a level-based, swap-style match-3 puzzle game in which the player clears thousands of hand-crafted board puzzles to help King Robert restore and decorate his castle, area by area.** The focus of the game is pure, friction-free puzzle gameplay: there are no timers pressuring the player mid-level, no forced ads interrupting play, and no decoration decisions gating progress. Every design choice — from the oversized, instantly readable board pieces to the one-tap booster activation — serves a single goal: let the player get into a level within seconds, understand the board at a glance, and experience a satisfying chain of explosions and rewards. Monetization is built entirely on in-app purchases (extra moves, boosters, coin bundles) driven by carefully tuned level difficulty, and long-term retention is built on a dense, rotating layer of live events, team play, and win-streak systems that sit on top of the core level ladder.

**The core loop** is: open the game → spend a life to enter the next level on the map → clear the level's goals within a limited number of moves → earn coins and event progress → watch King Robert complete the next piece of the current castle area → repeat. Failing a level costs a life (five maximum, regenerating one per 30 minutes), which is the game's primary session pacing valve. Around this loop sits a **meta layer**: castle areas that complete automatically as levels are cleared, a coin economy that funds continues and boosters, teams that share lives and compete together, and a live-ops calendar that ensures there is almost always at least one active event multiplying the value of a winning streak.

**Story summary.** The narrative is deliberately light and purely in service of the gameplay. King Robert, a cheerful and slightly hapless monarch, is restoring his royal castle to its former glory. Each group of levels corresponds to one area of the castle grounds — the Garden, the Throne Room, the Kitchen, the Bedroom, the Library, and so on. As the player clears levels, the area rebuilds itself step by step in short, rewarding vignettes, with the King reacting with delight. There are no branching choices, no dialogue trees, and no story-based failure: the story exists to provide a warm sense of place, a mascot the player grows attached to, and a visible, cumulative monument to the player's progress. Special "save the King" style bonus levels and dark-themed **King's Nightmare** challenge levels extend the King's character into the gameplay itself.

**Who the game is for.** Royal Match targets the broadest possible casual audience: sessions are short, rules are learnable in one level, and reading the board never requires reflexes or twitch skill. At the same time, the difficulty curve and booster economy give mid- and late-game players (the segment I belong to, at levels 500–600) a genuinely demanding puzzle experience with meaningful resource decisions.

**The rest of this document** describes the game bottom-up, in the order a new player experiences it: the mechanics (what the player can do, one verb at a time), the level design that arranges those mechanics into thousands of puzzles, the difficulty system that paces them, and the graphics, animation, effects, and interface that make the whole experience readable and delightful.

---

# 2. Game Mechanics

This section defines what players can do — hence, the game itself. It is structured in the order a first-time player encounters each capability, and each mechanic builds only on mechanics already defined. Nothing is assumed to be obvious: every input, every rule, and every edge case is spelled out so a developer reading this could implement the game without guessing.

## 2.1 The Player's View of the World

Royal Match is presented in **portrait orientation** on a phone or tablet, played one-handed with the thumb. During gameplay the player sees, from top to bottom:

1. **The goal panel** (top of screen): icons of the remaining goal items with countdown numbers (e.g., "12 boxes remaining"), plus the **moves counter** — the single most important number on screen, rendered large and centrally.
2. **The board**: a grid of colored **cubes** (the basic matchable pieces) and obstacles, occupying the majority of the screen. The camera is fixed; the board is always fully visible with no scrolling or zooming during play. Boards are typically around 9 columns wide and 9–10 rows tall, but the *shape* varies per level (holes, notches, and irregular outlines are common).
3. **The in-level booster tray** (bottom of screen): four booster buttons (Hammer, Arrow, Cannon, Jester Hat — defined in §2.7) with owned counts, plus a settings/pause button.

There is no player avatar or surrogate character moving through a world. The player's "character" is effectively **the cursor of their own finger**: the game world is the board, and the player acts on it directly. This is important for the input model — there is no selection step, no pathfinding, and no separate "confirm" action anywhere in core gameplay. Every gameplay verb is a single direct touch on the thing it affects.

## 2.2 Commands (Complete Input List)

All gameplay is driven by exactly four touch inputs:

| # | Command | Input | Effect |
|---|---|---|---|
| 1 | **Swap** | Drag a cube one tile up/down/left/right (a short swipe starting on the cube) | The cube exchanges places with its neighbor. This is the core verb and consumes one move **only if it produces a match or activates a booster** |
| 2 | **Tap a board booster** | Single tap on a Rocket, TNT, Propeller, or Light Ball on the board | Activates that booster immediately. Consumes one move |
| 3 | **Use an item booster** | Tap a tray booster (it arms and highlights), then tap a target tile on the board | Applies the item's effect (e.g., Hammer smashes the tapped tile). **Does not consume a move** |
| 4 | **Pause** | Tap the settings button | Opens the pause overlay (see §9, System Menus) |

**Explicitly defined edge cases** (never leave these to the implementer's assumptions):

- **Invalid swap:** if a swap would produce no match, the two pieces slide toward each other, bump, and slide back with a short "wobble" animation and a soft denial sound. **No move is consumed.** The player can never waste a move by accident.
- **Tapping a plain cube** (not a booster) does nothing — no move loss, no error popup; the cube gives a tiny squash "acknowledge" wiggle. Matching requires a swap, never a tap. (This is the single biggest input difference from Toon Blast, covered in Part II.)
- **Board with no possible moves:** the game detects a dead board automatically and **reshuffles it for free**, with a brief "Shuffling!" notice. The player is never softlocked and never penalized for board state they didn't create.
- **Input during resolution:** while cascades are resolving, new swaps are queued/locked briefly rather than dropped, so fast players never feel the game "ate" an input.

## 2.3 The "Movement Model" — Speed and Feel

Royal Match has no character locomotion, so its equivalent of a movement model is **input cadence and resolution speed**, and it is tuned to be *quick and tight rather than slow and precise*:

- **Swaps resolve instantly.** The swap animation is roughly a quarter of a second; there is no perceptible input latency. The game never makes the player wait to act except during cascade resolution.
- **Cascades are fast but readable.** When matched pieces clear, pieces above fall under snappy, slightly-eased gravity and new pieces spawn from the top of each column. Chain reactions resolve quickly enough to feel exciting, slowly enough that the player can track *why* each match happened.
- **The pace is entirely player-driven.** There is no timer in standard levels. The player can stare at the board for ten minutes or blitz through on instinct; pressure comes only from the finite move count. This "slow to think, fast to execute" model is the tuning heart of the game: deliberate strategy, instant gratification.
- **Consistency:** speed never changes across the game. Level 5 and level 5,000 resolve at identical speed; mastery changes the *player*, not the simulation.

## 2.4 The First Verb: Matching Cubes

The most basic thing a player can do — and the first thing every new player does in level 1 — is **swap two adjacent cubes to line up three or more same-colored cubes in a row or column**. Matched cubes pop and disappear; everything above falls down; new cubes drop in from the top. If falling pieces happen to form new lines of three or more, they match automatically as a **cascade**, at no move cost — cascades are the game's free jackpot moments and a key source of delight.

Cubes come in a small set of highly distinct colors (red, green, blue, yellow, purple, orange). Levels use a subset — fewer colors makes matches easier, more colors makes them scarcer — which is one of the primary difficulty dials (§4).

**Matching is also the universal "attack."** Nearly every obstacle in the game (§2.8) is damaged by making a match adjacent to it or on top of it. The player only ever needs the one verb they learned in level 1; everything else in the game is a force multiplier on it.

## 2.5 The Second Layer: Creating Board Boosters

Within the first handful of levels the game teaches that **matching more than three cubes creates a booster on the board** — a special piece occupying one tile, which stays there until activated by a tap or a swap. Boosters are introduced one at a time, each with its own tutorial level, in this order:

| Booster | How It Is Created | Effect When Activated |
|---|---|---|
| **Rocket** | Match **4 in a straight line** | Fires along its printed direction, clearing an entire **row or column**. The rocket's orientation is visible on the piece, so the player always knows which line it will clear |
| **Propeller** | Match **4 in a 2×2 square** | Launches off the board, flies to a tile elsewhere on the board — with targeting biased toward remaining **level goals** — and destroys what it lands on. The player's "smart missile" for out-of-reach objectives |
| **TNT** | Match **5 in an L or T shape** | Explodes, destroying everything in a roughly two-tile radius around itself |
| **Light Ball** | Match **5 in a straight line** | The rarest and strongest single booster. Swap it into any colored cube to destroy **every cube of that color on the board**; tapped alone, it targets the most common color |

Design intent worth spelling out: booster creation is **deterministic and previewable**. The player can see exactly which formation they are about to make, so booster creation is a skill, not a slot machine. High-level play (my 500–600 band) is essentially the craft of *manufacturing* the right booster in the right place.

## 2.6 The Third Layer: Booster Combinations

Once two boosters exist on the board, **swapping them into each other combines them** — the game's deepest and most satisfying mechanic, and the one most Hard levels are secretly about. Every pairing is defined:

| Combination | Result |
|---|---|
| Rocket + Rocket | Cross blast: clears one full row **and** one full column |
| Rocket + TNT | Giant cross: clears a **three-wide** row and three-wide column |
| TNT + TNT | Mega explosion with roughly double the normal radius |
| Propeller + Propeller | **Three** propellers launch simultaneously at separate targets |
| Propeller + (Rocket / TNT / Light Ball) | The propeller **carries** the paired booster and detonates its full effect at the destination tile — precision delivery of heavy ordnance |
| Light Ball + Rocket | Every cube of one color turns into a Rocket; all fire at once |
| Light Ball + TNT | Every cube of one color turns into a TNT; all explode |
| Light Ball + Light Ball | **Clears the entire board.** The game's ultimate moment, reserved by scarcity for rare, memorable turns |

The combination table is intentionally *monotonic*: any combination is at least as strong as its parts, so experimenting is always safe and always rewarded. Players discover combos on their own, but the game also nudges discovery via tutorials on early levels.

## 2.7 The Fourth Layer: Item Boosters (the Player's Inventory)

Distinct from board boosters (earned by play *inside* a level), **item boosters are owned consumables** — the game's inventory — used deliberately by the player:

**Pre-level boosters** — selected on the level-start popup before entering a level. Up to three can be armed; they appear on the board already charged at move one:

- **Rocket**, **TNT**, **Light Ball** (same effects as their board-made counterparts).

**In-level boosters** — the tray at the bottom of the gameplay screen, usable at any moment **without consuming a move**:

- **Hammer** — destroy any single tile (the surgical tool: last box, buried key item).
- **Arrow** — clears an entire row of the player's choice.
- **Cannon** — clears an entire column of the player's choice.
- **Jester Hat** — reshuffles all cubes on the board (obstacles stay put).

Item boosters are earned from events, win streaks (Butler's Gift, §3.5), area completions, and team rewards, and can be bought with coins. The inventory "window" is not a separate screen: owned counts are displayed directly on the level-start popup (pre-level items) and on the in-level tray (in-level items) — inventory is always shown *at the moment of use*, never one navigation step away.

## 2.8 Obstacles and Goal Items

Levels are defined by their **goals** — counts of specific items to clear — and items follow a small grammar of behaviors that combine into dozens of variants. Representative archetypes a player meets across the first few hundred levels:

- **Adjacent-clear, single layer** (e.g., **Grass** tiles): destroyed by any match or explosion adjacent to or on them. The gentlest goal type; teaches "matches have splash relevance."
- **Adjacent-clear, multi-layer** (e.g., **Boxes**, **Plates**): require two or three separate hits, with visible damage states between hits so remaining health is always readable at a glance.
- **Spawners/carriers** (e.g., **Mailboxes producing Mail envelopes**): hitting the carrier releases collectible items; the goal counts the collectibles, forcing repeated attention to one board region.
- **Gravity collectibles** (e.g., **Diamonds**): fall like cubes; the player must clear a path so they reach the bottom/collector row. Introduces vertical planning and column control.
- **Shielded/locked pieces** (e.g., cubes under **ice or chains**): the covering must be broken before the cube beneath can be matched or moved. These constrain board mobility rather than being goals themselves.
- **Heavy vault-type objects** (e.g., **Coin Safes**, **Cupboards**): multi-hit, large or immovable, often payout-flavored — cracking them feels like a heist.

Two universal rules keep this whole taxonomy learnable: **(1)** everything is damaged by the same causes — adjacent matches and booster effects — so no obstacle ever needs a unique verb; **(2)** every obstacle's remaining state is visually explicit (cracks, layers, counters), so the player never has to memorize hidden health.

## 2.9 Turn Structure, Winning, Losing, and Continuing

Spelled out end to end:

1. The player enters a level by tapping its node on the map, reviewing goals on the level-start popup, optionally arming pre-level boosters, and pressing **Play**. Entering costs **one life**.
2. Each valid swap or board-booster tap consumes **one move**. Item boosters and cascades are free.
3. **Win condition:** all goal counters reach zero. The moment they do, the level ends immediately — even mid-cascade — and any **unused moves convert into random board boosters that all detonate in a celebratory chain**, each paying bonus coins. Finishing efficiently is thus directly rewarded, and every win ends in fireworks.
4. **Lose condition:** moves reach zero with goals remaining. The game first offers a **Continue**: for coins (starting around 900), the player buys +5 extra moves and keeps all board progress. Declining ends the level: the life is spent, and all progress on that attempt is lost.
5. **Out-of-lives state:** with zero lives the player may wait (30 minutes per life), ask teammates for lives, or purchase a refill. Timed **unlimited-lives** rewards from events suspend life costs entirely and are the game's strongest "binge play" lever.

## 2.10 Gameplay GUI

*(Layout of the play screen plus the game's equivalents of conversation and inventory windows. Non-gameplay screens — map, shop, settings — are covered in §8 User Interface and §9 System Menus.)*

- **Goal panel (top):** goal icons with live countdown numbers; each goal item cleared flies visibly from the board up into its counter, tying cause to effect. The **moves counter** sits beside the goals in the largest type on screen. When moves run low (≤5), the counter pulses red — the only "pressure" signaling in the game.
- **Board (center):** occupies maximum screen area; tile size is deliberately large so pieces remain unambiguous at phone scale and are comfortable, forgiving touch targets.
- **Booster tray (bottom):** the in-level inventory (Hammer, Arrow, Cannon, Jester Hat) with owned counts; a booster with count zero shows a coin price instead, making the purchase path one tap long. A settings button sits in the corner for pause/quit.
- **Conversation window:** Royal Match has no dialogue system in the classic sense. Its "conversation UI" is (a) **tutorial callouts** — a hand cursor plus a short instruction bubble that dims the board except the relevant tiles, and (b) **King Robert vignettes** between levels, where the King reacts with animation and a short text line as areas complete. Both are one-tap-to-dismiss and never interrupt an active board.
- **Overlays:** the Continue offer, the win screen (coins tally + event progress bars), and the lose screen all appear as modal cards over a dimmed board, so the player never loses spatial context of the level they were just playing.

---

# 3. Level Design

## 3.1 Structure: One Ladder, Thousands of Rungs

The game is a single linear sequence of numbered, **hand-crafted** levels (10,000+ live, extended weekly). There is no level select in the classic sense — the map always focuses on the next level, so the "what do I do now?" question never exists. Levels are grouped into **castle areas** (roughly a few dozen levels each); completing an area triggers its decoration payoff and rolls into the next.

## 3.2 Anatomy of a Level

Every level is defined by: **board shape** (grid outline, holes, notches), **cube color count** (fewer colors = easier), **goal set** (which items, what counts), **obstacle layout**, **spawn rules** (what falls from which columns), and **move limit**. Because all levels share one verb set, these six dials are the entire design space — and the game gets remarkable variety out of them.

## 3.3 Teaching Through Levels

New mechanics are introduced on a strict pattern that I'd summarize as **introduce → isolate → combine**:

1. A new obstacle debuts in a deliberately easy level whose board makes the new element the only thing to think about, with a one-line tutorial.
2. The next several levels feature it in growing quantities but friendly layouts.
3. Only then is it combined with previously learned obstacles — and those combinations are where real puzzles begin.

The cadence of new content is tuned so that at any point in progression a player is typically within ~20 levels of *something* new, which is a major reason the level 500–600 band still feels fresh.

## 3.4 Spatial Design Patterns

Recurring layout archetypes, each creating a distinct puzzle "feel":

- **Open field:** big rectangular board, goals spread evenly — a booster-economy playground; the relaxing baseline.
- **Chokepoint boards:** two board regions connected by a narrow channel; controlling what falls through the channel is the puzzle.
- **Excavation boards:** goals buried under layered obstacles at the bottom; the level is a top-down dig, and Propellers/vertical Rockets become premium.
- **Perimeter boards:** goals ringed around the outside edge where matches are geometrically harder to form; TNT splash and Propellers shine.
- **Escort/gravity boards:** Diamonds must be routed down specific columns; the player manages lanes rather than areas.

Hard levels combine two or more archetypes; Super Hard levels combine them *and* tighten the move budget.

## 3.5 The Layer Around Levels: Events and Teams

Level design in Royal Match cannot be evaluated without the live-ops layer that multiplies its value:

- **Butler's Gift:** consecutive wins escalate a streak meter granting free pre-level boosters — making streaks themselves a resource the player protects (and a reason to spend on a continue rather than break the streak).
- **Propeller Madness / Lightning Rush / Sky Race** and rotating equivalents: timed events converting wins into event currency, board head-starts (e.g., propellers pre-placed at level start), or race positions against other players.
- **Royal League:** weekly division-based leaderboard of levels completed — the competitive spine for progression-focused players.
- **King's Cup:** short solo tournaments with milestone chests.
- **Teams:** up to 50 players; life requests/donations, chat, and team competitions. Teams convert the single-player ladder into a lightweight social obligation loop ("my team needs my wins today").
- **Book of Treasure / collection events:** completing levels advances a themed collection track with a large terminal reward.

The critical design property: **all events consume the same action — winning levels.** Nothing asks the player to play differently; events simply stack extra reward meaning onto the next level, which keeps the core loop singular and clean.

---

# 4. Level Difficulty

## 4.1 The Three Announced Tiers

Every level carries a public difficulty label, and the honesty of this labeling is a signature Dream Games choice:

| Tier | Signaling | Design Intent |
|---|---|---|
| **Normal** | Standard map node and level-start popup | Rhythm and reward; win rate kept high |
| **Hard** | Red-flagged node, warning styling on the level-start popup | A genuine wall; expected to take multiple attempts; where pre-level boosters and streak rewards become *strategically* relevant |
| **Super Hard** | Dark purple flagging, heavier warning treatment | Rare, memorable spikes; expected multi-session effort; the game's primary monetization moments and its biggest victory highs |

Announcing difficulty up front does three jobs at once: it lets players *budget* (save boosters and streak gifts for the flagged level), it converts frustration into anticipation (the player consented to the challenge), and it makes overcoming the level feel like an event.

## 4.2 The Difficulty Dials

Difficulty is composed from independent, tunable inputs — the same six dials from §3.2, plus randomness bounds:

1. **Move budget** relative to goal counts (the master dial).
2. **Color count** (six colors on a Super Hard level makes raw matches scarce, starving booster production).
3. **Obstacle depth** (layers, shields, spawner counts).
4. **Geometry hostility** (chokepoints, corners, isolated pockets that boosters struggle to reach).
5. **Goal dispersion** (spread goals dilute booster value; clustered goals reward one big combo).
6. **Spawn mix** (what falls in — including whether helpful pieces flow to where they're needed).

Because each dial is independent, the designers can produce "hard but fair"-feeling levels: even the cruelest boards visibly obey the same rules, and the player can always articulate *why* they lost.

## 4.3 The Curve Across Progression

From my own progression: the first ~30–40 levels are near-unloseable onboarding; Hard levels then begin appearing every handful of levels, with Super Hard entering later at a slower cadence. In the 500–600 band, the effective rhythm is a pulse — a few comfortable levels, then a flagged wall — which maps directly onto the emotional loop of *cruise, tension, spike, triumph*. Crucially, walls arrive **after** the player has an inventory of earned boosters and an active streak worth defending, so difficulty always intersects with a resource decision rather than a dead end.

## 4.4 Difficulty as the Monetization Engine

Royal Match runs **no advertising**; revenue is IAP only, and difficulty is the engine. The spend moments are all difficulty-shaped: the **continue** offer at a near-win ("2 boxes left" is the most persuasive salesman in mobile gaming), booster purchases before a flagged level, and lives refills mid-binge. The tuning discipline is what impresses me most as a player: near-misses on hard levels consistently feel *earned by the level design* rather than manufactured, which preserves trust — and trust is what lets a player at level 550 still feel the game is fair.

---

# 5. Graphics

## 5.1 Art Direction

Royal Match's visual identity is **bright, rounded, premium casual**: saturated colors on a regal blue-and-gold palette, soft 3D-rendered forms with gentle gradients and highlights, and zero visual grit. The look reads instantly as friendly and high-budget — deliberately closer to a modern animated feature than to a flat mobile puzzle. King Robert anchors the brand: a compact, expressive design (big head, big mustache, big emotions) that survives any scale from app icon to fullscreen celebration.

## 5.2 Readability as the First Law

Every graphical decision defers to board readability:

- **Cube colors are maximally separated** in hue and additionally distinguished by shape/marking, so no two piece types can be confused at speed or by colorblind players.
- **Boosters look categorically different from cubes** — mechanical and detailed against soft cube forms — so "actionable specials" pop out of any board state instantly.
- **Obstacle damage states are drawn, not implied**: a two-hit box visibly cracks after the first hit. Remaining work is always legible without UI.
- **The board sits on a low-contrast, softly-lit backdrop** themed to the current castle area; the background is beautiful but tonally suppressed so full attention stays on the play field.

## 5.3 Environment and Meta Graphics

The map and castle areas carry the visual richness the board intentionally suppresses: layered parallax scenery, warm lighting, and dense decorative detail that transforms as areas complete. The before/after contrast of a restored area is the graphical payoff of the whole meta loop. Menu and event screens share one design system — rounded gold-trimmed panels, ribbon headers, consistent iconography — so nothing anywhere in the product feels imported from a different game.

## 5.4 Technical Quality

Performance is part of the art direction: stable frame rate through even maximal cascades on mid-range hardware, crisp assets across device resolutions, and fast level load (map-tap to first move in a few seconds). For a game whose feel depends on instant response (§2.3), this engineering polish *is* a graphics feature.

---

# 6. Animation

Animation in Royal Match is the delivery mechanism for game feel. The principles at work:

- **Squash and stretch everywhere.** Cubes compress on landing, bulge on popping, wobble on invalid swaps. Every piece behaves like soft candy, making the board feel alive and touchable.
- **Anticipation on power.** Big effects wind up before paying off: TNT's fuse sparks, the Light Ball charges and crackles, propellers rev before takeoff. A few frames of anticipation multiply perceived impact.
- **Cause-and-effect trails.** Collected goal items physically fly from the board into their counters; coins arc into the coin balance. The player's eye is never left wondering what just happened or why a number changed.
- **The win choreography** is a fixed, escalating sequence — goals complete, leftover moves convert to boosters, boosters chain-detonate, coins fountain, King Robert celebrates — long enough to feel like a reward, short enough (and skippable enough) to never tax a player on a streak.
- **Character animation.** King Robert's between-level vignettes use full cartoon acting (posture, takes, eyebrow work) and area completions play as short transformation scenes. The character layer earns emotional attachment the board alone can't.
- **Interruptibility.** Nearly all celebration is tap-through. Respecting a fast player's time is treated as an animation feature, and at level 550 I can confirm it is felt daily.

---

# 7. Particles & Special Effects

Effects are the reward currency of a match-3, and Royal Match's effect design follows a clear grammar:

- **A strict hierarchy of scale.** A 3-match emits a modest color-matched burst; Rockets leave screen-long trails with debris; TNT produces a shockwave, flying fragments, and a camera shake; the Light Ball fires a beam to every piece of the chosen color; Light Ball + Light Ball whites out the entire screen. Effect magnitude precisely tracks mechanical magnitude, so spectacle is *information*.
- **Screen shake used sparingly** — reserved for TNT-and-above so that the biggest plays keep a physical signature that smaller plays never dilute.
- **Effects never obscure play.** Particles are brief, and goal counters/moves remain readable through every explosion. The board state is never hidden behind its own celebration.
- **Cascade escalation:** consecutive chain reactions raise effect intensity and sound pitch step by step, turning lucky cascades into audible, visible jackpot sequences.
- **UI effects:** buttons glimmer on important CTAs, chests burst with light on opening, streak meters flare as they fill. The same effect language sells reward moments outside the board.
- **Audio as effect:** pops, whooshes, fanfares, and coin sounds are layered with the particle work; the rising cascade pitch is arguably the game's single most satisfying feedback device.

---

# 8. User Interface

*(Gameplay-adjacent UI. Pure system screens are in §9.)*

## 8.1 The Map — the Home Screen

The map is the hub, and its design thesis is **one giant obvious next action**: the current level node with a pulsing **Play** button, centered. Around this anchor:

- **Top bar:** lives (with regen timer), coin balance (+ button → shop), and area/star progress.
- **Side rails:** live event entry points — compact animated widgets for Royal League, King's Cup, active streak meters, and timed offers. Dense but strictly perimeter; the center path is never blocked.
- **Bottom bar:** navigation to Teams, Events, and the area/decoration view.

A new player sees one button; a veteran sees a dashboard. The same screen serves both because everything except **Play** is visually subordinate.

## 8.2 Interaction Standards

- **Everything is one tap.** No long-presses, no gestures beyond the board swap, no hidden menus.
- **Modal discipline:** popups stack in a fixed order after wins (event progress → streak update → offers), each dismissible with one tap in a consistent position. Even the marketing surfaces are rhythm-predictable.
- **Numbers before prose:** timers, counters, and progress bars carry meaning; text is minimal and localized-length-safe.
- **State is always visible:** lives, coins, streaks, and event timers are permanently on the hub — the player never navigates to discover whether they can afford to play.

## 8.3 Purchase & Offer UI

The shop is a paged grid of coin bundles and booster kits with clear price anchoring; contextual offers (e.g., after a failed Hard level) are visually distinct cards so the player always recognizes a commercial surface as commercial. Continue and refill prompts show price and content with zero ambiguity — one more piece of the trust economy discussed in §4.4.

# 9. System Menus

*(Non-gameplay GUIs, kept apart from Game Mechanics as specified.)*

- **Settings:** sound/music toggles, haptics, language, notifications, and support/FAQ access — one flat screen, no nesting.
- **Account & save:** progress syncs via platform account linkage; a returning or device-switching player restores by signing in — no manual save/load anywhere (session state of an abandoned level is simply discarded; the life was the cost).
- **Pause overlay (in-level):** resume, toggle sound, or **quit** (with an explicit warning that quitting spends the life). Nothing else — the level itself is never configurable.
- **Team management:** browse/search teams, join rules (open/invite), member list with weekly contribution, and chat. Deliberately shallow: social features are lightweight by design.
- **No load-game, difficulty, or graphics menus exist** — every removed system screen is friction that a casual player never has to think about, which is itself a design statement.

---

---

# PART II — GAME DESIGN DOCUMENT: TOON BLAST

---

# 10. Introduction

**Toon Blast is a level-based, tap-to-blast puzzle game in which the player pops groups of two or more adjacent same-colored cubes to clear cartoon-themed board goals across thousands of levels, progressing through weekly 50-level episodes alongside a trio of toon mascots.** The focus of the game is *speed and simplicity of input*: where classic match-3 asks the player to plan swaps, Toon Blast asks only for a tap on an existing group — the lowest-friction core verb in the puzzle genre. Everything else in the design (instant booster creation from big groups, one-tap booster combos, snappy cascade resolution) is built to preserve that immediacy. Like Royal Match, it is monetized through IAP driven by level difficulty, with no forced advertising, and retained through episodic content drops, star-collection meters, and team play.

**The core loop:** spend a life → enter the next level → clear the goal items within a move limit by tapping cube groups → earn stars and coins → advance toward the episode's end → repeat. Five lives regenerate one per 30 minutes; teams (unlocked at level 20) share lives and compete together.

**Story summary.** Toon Blast's narrative is a premise rather than a plot: **Cooper Cat, Wally Wolf, and Bruno Bear** are the stars of a Saturday-morning-style cartoon world, and the player travels with them through themed episodes — each episode a self-contained cartoon "set" (jungles, ski slopes, pirate seas) introduced with a short slapstick vignette. There is no restoration meta, no decisions, and no continuing storyline; the characters exist as comedic mascots whose gags frame the level ladder and give each weekly episode a fresh coat of theme. The charm of the trio, rather than any narrative stake, is the emotional hook.

**Who it's for:** the same broad casual audience as Royal Match, tilted slightly toward players who value pace over planning — sessions are even faster because every action is a single tap on something already visible.

**Document structure** mirrors Part I: mechanics in first-experience order, then level design, difficulty, and the presentation layers.

---

# 11. Game Mechanics

## 11.1 The Player's View

Portrait orientation; a fixed, fully visible board of colored cubes filling most of the screen; goal icons and the moves counter at the top; the in-level booster tray (Hammer, Boxing Glove, Anvil, Dice) at the bottom; character art framing the board on episode-themed backdrops. As in Royal Match there is no avatar and no camera movement: the player acts directly on the board with single touches.

## 11.2 Commands (Complete Input List)

| # | Command | Input | Effect |
|---|---|---|---|
| 1 | **Blast** | Tap any group of **2+ adjacent same-colored cubes** | The whole group pops instantly. Consumes one move |
| 2 | **Activate booster** | Tap a Rocket, Bomb, or Disco Ball on the board | Fires it. Consumes one move. If another booster is adjacent, they **combine** automatically |
| 3 | **Use an item booster** | Tap a tray item, then tap a target tile | Applies the effect. **No move consumed** |
| 4 | **Pause** | Tap the settings button | Opens the pause overlay |

Edge cases, spelled out:

- **Tapping a lone cube** (no same-colored neighbor) produces a wiggle and a soft sound; **no move is consumed**. Mistaps are free.
- **There is no swapping whatsoever.** Cubes cannot be moved by the player — only removed. Board manipulation happens exclusively through what you choose to pop and what falls as a result.
- **Dead board** (no group of 2+ anywhere): automatic free shuffle.
- **Group highlighting:** groups large enough to create a booster display a badge of the booster they would create, directly on the cubes. The player always sees the reward before spending the tap.

## 11.3 Movement Model — Feel

Toon Blast is the *quickest and tightest* input model in the genre: no drag distance, no direction, no source-and-destination — one tap equals one resolved action. Pops resolve near-instantly; gravity is snappy with cartoon overshoot; and because groups (not lines) are the match unit, the board reads as clusters of color that the eye parses even faster than match-3 rows. There are no timers; pace is fully player-driven; resolution speed is constant across all 10,000+ levels. The result is a play rhythm measurably faster than swap games — several taps per Royal Match swap — which is the game's defining sensation.

## 11.4 First Verb: Popping Groups

Level 1 teaches the entire input model: tap two or more connected cubes of one color to pop them; everything above falls; new cubes rain in from the top; incidental new groups do **not** auto-pop (unlike Royal Match's cascading matches, falling cubes simply form new *tappable* groups — the player harvests cascades manually, keeping every point of agency in their finger). Fewer colors in a level means bigger groups; more colors means fragmentation. As in Royal Match, adjacency of a pop is the universal way to damage obstacles.

## 11.5 Second Layer: Boosters from Big Groups

Booster creation is threshold-based on **group size at the moment of the tap**:

| Group Size | Creates | Effect When Tapped |
|---|---|---|
| **5–6 cubes** | **Rocket** (horizontal or vertical, shown on the piece) | Clears its full row or column |
| **7–8 cubes** | **Bomb** | Explodes a roughly two-tile radius |
| **9+ cubes** | **Disco Ball** | Clears **every cube of the color of the group that made it** |

Because the pending booster is badged on the group *before* the tap (§11.2), booster manufacturing is a visible economic decision: pop a 4-group now, or spend taps elsewhere to grow it to 5 and mint a Rocket? This "grow the group" tension is Toon Blast's core skill expression, and at levels 500+, it is nearly all I think about while playing.

## 11.6 Third Layer: Booster Combinations

Tapping a booster **adjacent to another booster** merges them automatically:

| Combination | Result |
|---|---|
| Rocket + Rocket | Cross: full row + full column |
| Rocket + Bomb | Giant cross: three rows + three columns |
| Bomb + Bomb | Double-radius mega blast |
| Disco + Rocket | All cubes of the Disco's color become Rockets and fire |
| Disco + Bomb | All cubes of that color become Bombs and detonate |
| Disco + Disco | **Clears the entire board** |

Note the design difference from Royal Match: combos require **adjacency + a single tap**, not a swap — consistent with the game's one-verb philosophy. Setting up adjacency (minting two boosters next to each other) is therefore itself the high-skill play.

## 11.7 Fourth Layer: Item Boosters (Inventory)

- **In-level tray:** **Hammer** (destroy one tile), **Boxing Glove** (clear a row), **Anvil** (clear a column), **Dice** (reshuffle). None consume a move; counts and coin-purchase fallbacks display in place, exactly at the moment of need.
- **Level-start boosters** (Rocket/Bomb/Disco pre-placed on the board at move one) come chiefly from the **Crown Rush** win-streak system and chest rewards rather than from a free-choice loadout — Toon Blast leans more on *earned momentum* and less on *player-armed loadouts* than Royal Match.

## 11.8 Obstacles and Goal Items

Same behavioral grammar as §2.8, dressed in cartoon props. Representative archetypes: single-hit adjacent-clear items (**balloons**), multi-layer adjacent-clear items (**crates** with visible damage states), embedded/rooted items (**carrots** popped by adjacent blasts), containers that hold cubes until freed (**bubbles**), and gravity collectibles (**ducks** that must be walked down to the bottom of the board by clearing beneath them). All obey the two universal rules: damaged only by adjacent pops and booster effects; remaining health always drawn on the object.

## 11.9 Winning, Losing, Stars, and Continuing

- **Win:** all goals reach zero; remaining moves convert into board boosters that chain-detonate for bonus score; a **1–3 star rating** is awarded based on performance. Stars are a real currency: they fill the **Star Chest** and weekly **Star Tournament**, so playing *well* (not just winning) has systemic value — a meaningful contrast with Royal Match, which has no per-level rating.
- **Lose:** moves hit zero → Continue offer (+5 moves for coins, keeping board progress) → decline ends the attempt and the life.
- **Lives economy:** 5 lives / 30-minute regen / team requests / unlimited-lives event rewards — structurally identical to Royal Match.

## 11.10 Gameplay GUI

Top: goal icons with counters and the prominent moves number. Center: board, maximally sized, tap targets generous. Bottom: item tray + settings. **Conversation UI:** episode-intro vignettes (a comic-panel gag with the trio, one tap to dismiss) and hand-cursor tutorial callouts; no dialogue system. **Inventory UI:** in place at point of use, as in Royal Match. Modal overlays (continue/win/lose) appear over the dimmed board.

---

# 12. Level Design

- **Episodic structure:** levels ship in **50-level episodes with a new episode weekly**, each with a unifying theme and intro gag. Episodes give progression a visible chapter rhythm — "finishing the episode" is a natural session/weekly goal that Royal Match's continuous castle-area flow expresses differently.
- **The blast verb changes the puzzle geometry.** Because groups are the unit, level design manipulates *color connectivity*: walls and holes that sever regions, obstacle screens that block group growth, and layouts that make big groups possible only after specific excavations. Where Royal Match designs around swap lines, Toon Blast designs around cluster topology.
- **Teach-isolate-combine** pacing for new obstacles mirrors Royal Match's, with new content cadence sustained deep into the level ladder (still true in my 500–600 band).
- **Meters around the levels:** Star Chest (stars → reward chest), Toon/level chests, team chests, Crown Rush streaks, and weekly Star and team tournaments — all feeding on the same act of playing levels, keeping the loop singular. Teams unlock at level 20 with lives-sharing and chat.

# 13. Level Difficulty

- **Announced tiers:** Normal, **Hard** (red-flagged), **Super Hard** (dark purple) — the same trust-building, budget-enabling transparency as Royal Match, which Peak pioneered for the blast genre.
- **Dials:** move budget, color count (the strongest lever — extra colors shatter group connectivity), obstacle depth, board fragmentation, goal dispersion, and spawn mix. Blast mechanics add a distinctive dial: **group-size starvation**, layouts that make 5+ groups rare, throttling booster minting.
- **Curve shape:** generous onboarding, then pulsed walls at increasing frequency; in the 500–600 band, hard levels arrive in clusters between comfortable stretches. Randomness of spawns means repeat attempts vary meaningfully, keeping retries hopeful rather than rote.
- **Monetization coupling:** identical structure to Royal Match — continues at near-miss, boosters before walls, lives refills mid-streak — with the star system adding a soft prestige incentive on top.

# 14. Graphics

Toon Blast's identity is **flat, bold, 2D cartoon**: thick outlines, poster-saturated colors, exaggerated character silhouettes, and episode backdrops staged like animation cels. Where Royal Match reads "premium rendered," Toon Blast reads "classic cartoon" — a deliberately louder, funnier register. Readability rules are the same and equally strict: maximally separated cube colors, categorically distinct booster art, drawn damage states on every obstacle, and backgrounds tonally suppressed behind the play field. The trio of mascots carries the brand across icon, store, and UI. Performance is flawless on modest hardware — flat 2D art keeps even massive chain reactions cheap to render.

# 15. Animation

The animation language is *slapstick cartoon physics*: heavy squash-and-stretch on every pop and landing, overshoot and bounce on falling cubes, and character animations built on classic gag timing (double takes, pratfalls) in episode intros and win screens. Boosters get anticipation frames (bomb fuse, disco spin-up); collected goal items fly to their counters; win choreography converts leftover moves into a chain of detonating boosters with escalating energy. Everything celebratory is tap-skippable. Compared with Royal Match's softer, more "premium animated film" motion, Toon Blast's animation is broader and more comedic — a register choice, executed with equal discipline.

# 16. Particles & Special Effects

The same effect grammar as §7, tuned louder: strict scale hierarchy (group pop → rocket trail → bomb shockwave with shake → disco ball color-sweep beams → disco+disco full-screen wipe), confetti-flavored 2D particles matching the cartoon art, escalating pitch on consecutive pops, and celebratory UI effects on chests, stars, and crowns. Spectacle exactly tracks mechanical power, effects never obscure counters, and screen shake stays reserved for the top of the hierarchy. Star awards on the win screen slam in one by one with stamp effects — a small touch that makes the 3-star chase physically felt.

# 17. User Interface

The hub map centers the next level node with one dominant Play button; the top bar holds lives, coins, and stars; perimeter widgets expose Crown Rush, Star Chest, tournaments, and team entry. Episode boundaries render as gates on the map, giving the weekly cadence a visible geography. All interactions are single taps; popup order after wins is fixed and predictable; and every meter that matters (streaks, chests, tournament rank) is visible on the hub without navigation. The shop and contextual offers follow the same clearly-commercial-surface discipline described in §8.3.

# 18. System Menus

Settings (sound, notifications, language, support), account sync via platform sign-in with no manual save/load, an in-level pause overlay (resume / sound / quit-with-warning), and team management (search, join, member list, chat). As with Royal Match, the near-absence of system screens is the point: nothing configurable stands between the player and the next level.

---

---

# PART III — COMPARATIVE ANALYSIS & PRODUCT TAKEAWAYS

---

# 19. Head-to-Head: Design Philosophy

| Dimension | Royal Match | Toon Blast |
|---|---|---|
| **Core verb** | Swap (drag) to match lines | Tap to pop groups |
| **Skill center** | Manufacturing boosters via formation planning | Growing groups to thresholds; engineering booster adjacency |
| **Cascades** | Automatic (free luck moments) | Manual (player harvests them — more agency, less luck) |
| **Booster set** | Rocket, Propeller, TNT, Light Ball (+ swap combos) | Rocket, Bomb, Disco Ball (+ adjacency combos) |
| **Per-level rating** | None — win/lose only | 1–3 stars feeding chests & tournaments |
| **Content structure** | Continuous ladder + castle areas + story vignettes | Weekly 50-level themed episodes |
| **Meta payoff** | Castle restoration with King Robert | Episode completion + mascot gags |
| **Art register** | Premium rendered, regal, warm | Flat 2D cartoon, loud, comedic |
| **Loadout model** | Player-armed pre-level boosters | Streak-earned automatic head starts |
| **Shared DNA** | Lives (5 / 30 min), coins, continues, teams, announced Hard/Super Hard tiers, no forced ads, IAP-only, win-streak events, weekly leaderboards | Same |

The shared DNA is no accident — Royal Match visibly studied the Peak playbook (transparent difficulty tiers, no-ads premium feel, team lives economy) and then made two decisive bets of its own: **the Propeller** (a goal-seeking booster that keeps hopeless-looking boards winnable, smoothing frustration on exactly the levels that monetize) and **removing all meta friction** (no decoration choices, no star gates — nothing between the player and the next level).

# 20. What Royal Match Does Better, and Why It Matters

1. **The Propeller is the genre's best frustration valve.** Blast and match games die on "I can see the last goal but can't reach it." A booster that *aims itself at goals* converts those dead boards into hopeful ones, which protects both session mood and continue-purchase intent. Toon Blast has no equivalent.
2. **Higher event density with zero added complexity.** Royal Match's live-ops calendar keeps multiple win-multiplying meters running at nearly all times, yet every one of them consumes the same action — winning the next level. The player's decision space never grows; only the meaning of a win does.
3. **The swap verb produces deeper deliberate play.** Tap-blast is faster, but swap-based booster manufacturing supports a longer skill ceiling — my level 500–600 experience in Royal Match involves noticeably more planning per move than the same band in Toon Blast, which supports long-horizon retention for invested players.
4. **Toon Blast's counterpunch is the star system and episode cadence** — a per-level performance currency and a weekly "new chapter" ritual that Royal Match deliberately traded away for frictionlessness. The trade is coherent on both sides; Royal Match's revenue trajectory suggests frictionlessness won.

# 21. Observations from Royal Kingdom

Playing Dream Games' second title to level 550 alongside Royal Match shows the studio iterating on its own formula rather than resting on it: the core swap-match engine, booster grammar, and honest difficulty flagging carry over intact, while the meta layer grows more ambitious — a kingdom-scale progression with an antagonist framing (the Dark King) that adds narrative stakes Royal Match never needed, plus new board mechanics and event formats layered onto the same one-verb loop. The important product lesson is the *discipline of the carryover*: everything that made Royal Match frictionless survives untouched, and innovation is confined to the layers around the core. That is exactly how I would expect a Product Specialist at Dream Games to think about change: protect the loop, iterate the meaning around it.

# 22. Closing Notes on Method & Assumptions

- All analysis derives from sustained first-hand play at the progression bands stated in §0, on live production builds.
- Numeric values (booster thresholds, life timers, continue pricing) reflect my builds; both games A/B test economy and event parameters continuously, so exact figures may vary across cohorts. The design logic described is stable across such variation.
- Obstacle lists are representative archetypes rather than exhaustive catalogs; both games hold dozens of variants that all reduce to the behavioral grammar defined in §2.8 / §11.8.
- Where the brief's template assumes an avatar-based game (pathfinding, character movement), I have translated those requirements faithfully to the puzzle genre: input model, resolution speed, and action cadence are the puzzle game's movement model, and are documented as such in §2.3 and §11.3.

*Thank you for reviewing this study. I would welcome the chance to discuss any section — particularly the difficulty-monetization coupling in §4.4 and the live-ops architecture in §3.5 — in person.*
