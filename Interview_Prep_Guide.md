# INTERVIEW PREPARATION GUIDE

## Dream Games — Product Specialist Position

**Round 2: HR Interview (30 min) + Product Lead Deep-Dive (2 hours)**

*Private preparation document — do not submit. Companion to `Royal_Match_Toon_Blast_GDD` and `Blast_Voyage_Game_Design`.*

---

## Table of Contents

1. Strategy Overview — What Each Interview Is Really Testing
2. The HR Interview (30 Minutes)
3. Know Your Own Submission Cold — Part 1 Cheat Sheet (Royal Match & Toon Blast GDD)
4. Know Your Own Submission Cold — Part 2 Cheat Sheet (Blast Voyage)
5. Dream Games — Company Knowledge
6. Market & Genre Context
7. The Decision-Defense Map — Every Design Choice, the Pushback, and Your Answer
8. Anticipated Question Bank with Model Answers
9. Live Design Exercise Playbook
10. Metrics Glossary — Speak the Language Fluently
11. Your Personal Play Stories — Prepare These From Your Own Experience
12. Questions to Ask Them
13. The Two-Hour Game Plan — Pacing, Materials, Demeanor
14. Final-Week Checklist

---

# 1. Strategy Overview — What Each Interview Is Really Testing

**The HR interview (30 min)** is a screen for: genuine motivation (do you actually want *Dream Games*, or just a job), communication clarity, culture fit (humility + high standards), and logistics (location, availability, expectations). You cannot win the job here, but you can lose it. Goal: warm, structured, concise answers; zero red flags; visible enthusiasm backed by the fact that you play their games daily at level 500+.

**The Product Lead interview (2 hours)** is testing four things, roughly in this order of importance:

1. **Do you own your document?** Every claim, number, and trade-off in your submission must be defensible *by you, live, under friendly pressure*. The fastest way to fail is to seem like the document knows more than you do. The fastest way to impress is to defend a choice, concede a real weakness gracefully, and improve the design on the spot.
2. **Do you think like a product person, not just a fan?** Every design opinion should connect to a player emotion AND a metric. Your signature move for the whole interview: *"Players feel X, which shows up in metric Y, which we'd tune with lever Z."*
3. **Do you actually play?** They will probe for the texture only a real player has: what a specific hard level felt like, what the current live event rotation is, what annoys you. Generic praise is a red flag; specific, affectionate criticism is a green flag.
4. **Can you operate?** Product Specialists at Dream Games live in dashboards, level-funnel data, and A/B tests. Expect at least one analytical scenario ("this level's win rate is 20% and churn is spiking — walk me through what you do").

**Your three campaign themes** — return to these all interview:

- **"Protect the loop; iterate the meaning around it."** Your reading of why Royal Match wins, and the thesis of both your documents. Use the phrase; it's yours now.
- **"Hope is a mechanic."** Your Blast Voyage signature (Breeze Meter / Paper Plane) and your lens on frustration design everywhere.
- **"Trust compounds."** Honest difficulty flags, no forced ads, fail-with-hope tuning — your explanation of Dream Games' moat and your tuning covenant in §6.4 of the Blast Voyage document.

---

# 2. The HR Interview (30 Minutes)

## 2.1 Likely Questions and Strong Answer Frames

**"Tell me about yourself."** (2 minutes, rehearsed but natural)
Frame: present → passion → proof → why here. End on Dream Games. Include the player credentials naturally: *"…and I'm a genuinely heavy casual puzzle player — I'm in the 500s in both Royal Match and Toon Blast, level 550 in Royal Kingdom — which is actually what pulled me toward product work in this genre: I kept noticing why these games' decisions worked on me."*

**"Why Dream Games?"**
Three-layer answer, specific to them:
- *Product:* "Royal Match is the best-executed casual game in the world — not because of one feature, but because of a hundred disciplined decisions: no forced ads, honest difficulty flags, a meta with zero friction. I wrote my case study around that discipline."
- *Company:* "A small team from Istanbul out-executed King and Playrix at their own genre. That ratio of team size to impact tells me the bar inside is extraordinary, and that's where I want to be measured."
- *Personal:* "I already spend my evenings in your products voluntarily. I'd rather spend my analytical energy on games I believe in."

**"Why the Product Specialist role specifically?"**
"It's the role where player empathy and data meet. I love the craft of asking *why* a level, an event, or a price point works — my case study's level-by-level win-rate targets and tuning thresholds are the kind of work I want to do daily."

**"What's your greatest strength / weakness?"**
Strength: pick one and prove it with the case study ("structured product thinking — I can decompose a game into tunable levers; that's literally what my document does"). Weakness: pick something real and non-fatal, with a mitigation ("I can over-polish deliverables past the point of diminishing returns; I now timebox and ship drafts for feedback earlier").

**"Where do you see yourself in 3–5 years?"**
Growth *inside* the craft: "Owning a product area — difficulty, economy, or live-ops — and being the person the team trusts on why players behave the way they do."

**Logistics questions** (salary expectation, notice period, office/relocation to Istanbul, work authorization): decide your answers *before* the call; deliver them in one calm sentence each; give a salary range only if pressed, anchored on research, with "flexible for the right role."

## 2.2 HR Red-Flag Avoidance

- Never criticize a previous employer or interviewer.
- Don't over-talk: 60–90 seconds per answer, then stop. HR interviews die from monologues.
- Don't mention competing offers as leverage in this round.
- Have one question ready for HR: "What does the rest of the process look like after the Product Lead interview?" and one culture question: "What do people who thrive at Dream Games have in common?"

---

# 3. Know Your Own Submission Cold — Part 1 Cheat Sheet

*(Everything the Product Lead may quiz you on from your Royal Match / Toon Blast GDD. Re-verify each fact in the live games during your final week — both games A/B test values, and "as of this week in my build…" is the most credible phrase you can use.)*

## 3.1 Royal Match — Core Facts as Stated in Your Document

- **Core:** level-based **swap** match-3; drag one tile to an adjacent position; a swap that makes no match bounces back and **costs no move**.
- **Board boosters and creation rules:** **Rocket** = match 4 in a line (clears a row/column per its printed orientation); **Propeller** = match 4 in a 2×2 square (flies to a target biased toward level goals); **TNT** = 5 in an L/T shape (~2-tile radius blast); **Light Ball** = 5 in a straight line (clears all of one color). Activation = **tap**; combination = **swap two adjacent boosters**.
- **Combos:** Rocket+Rocket = cross; Rocket+TNT = 3-wide cross; TNT+TNT = bigger blast; Propeller+Propeller = 3 propellers; Propeller+X = carries X to target; LightBall+Rocket/TNT = converts a color to that booster; LightBall+LightBall = full-board clear.
- **In-level items (no move cost):** Hammer (1 tile), Arrow (row), Cannon (column), Jester Hat (shuffle). **Pre-level loadout:** Rocket, TNT, Light Ball.
- **Economy:** one currency (coins); **lives 5 / 30-min regen**; continue ≈ +5 moves for coins (~900 in your build); leftover moves at a win convert to boosters that detonate for bonus coins.
- **Meta:** castle areas restore **automatically** — no decoration choices, no star gates (the deliberate contrast with Playrix); King Robert vignettes; **no per-level star rating**.
- **Difficulty:** announced tiers — Hard (red flag), Super Hard (dark purple); difficulty is the monetization engine; **no forced ads, IAP-only**.
- **Live-ops named in your doc:** Butler's Gift (win-streak pre-boosters), Propeller Madness, Lightning Rush, Sky Race, King's Cup, Royal League (weekly divisions), Team Battle, Book of Treasure, Magic Cauldron; Teams (lives sharing, chat); King's Nightmare (dark ultra-hard themed levels).

## 3.2 Toon Blast — Core Facts as Stated in Your Document

- **Core:** **tap-to-blast** — tap 2+ adjacent same-colored cubes; no swapping; lone-cube tap costs nothing; falling cubes do **not** auto-pop (manual cascade harvesting).
- **Booster thresholds:** **5–6 → Rocket** (orientation shown on piece), **7–8 → Bomb**, **9+ → Disco Ball** (clears the color of the group that made it). Groups big enough to mint a booster show a **pre-tap badge**.
- **Combos (adjacency + tap):** Rocket+Rocket = cross; Rocket+Bomb = 3-wide cross; Bomb+Bomb = mega; Disco+Rocket/Bomb = color converts to that booster; Disco+Disco = full board.
- **Items:** Hammer, Boxing Glove (row), Anvil (column), Dice (shuffle).
- **Structure:** **50-level episodes, weekly release**; trio of mascots (Cooper Cat, Wally Wolf, Bruno Bear); episode intro gags; no restoration meta.
- **Stars:** **1–3 stars per level** feeding Star Chest and the weekly Star Tournament — the systemic contrast with Royal Match (performance currency vs. pure completion).
- **Other systems:** Crown Rush (win-streak → start boosters), teams at level 20, lives 5 / ~30 min, coins + continue, Hard/Super Hard flags, no forced ads.
- **Heritage:** Peak Games, global launch 2017; Peak acquired by Zynga (2020, ~$1.8B); Zynga acquired by Take-Two (2022).

## 3.3 The Comparative Claims You Made (be ready to argue each)

1. **The Propeller is the genre's best frustration valve** — solves "I can see the last goal but can't reach it"; Toon Blast has no equivalent; protects mood *and* continue intent.
2. **Royal Match's event density adds meaning, never complexity** — every event consumes the same action (win the next level).
3. **Swap supports a deeper deliberate-planning skill ceiling; tap is faster but shallower** — you experience this personally at the 500–600 band.
4. **Toon Blast's counterweights are the star system and weekly episode ritual** — real strengths Royal Match consciously traded away for frictionlessness.
5. **Shared DNA is deliberate:** Dream's founders came from Peak; Royal Match kept the proven skeleton (lives, honest flags, no ads, teams) and innovated in the layers around it.

**If they correct a detail from your document** (e.g., an exact coin price, a booster radius, an event's current name): do not defend the pixel — defend the layer. *"You're right — that value has likely changed in a test since I wrote it; the design point it illustrates is X, and that's stable."* Graceful, non-defensive factual correction handling is itself being evaluated.

---

# 4. Know Your Own Submission Cold — Part 2 Cheat Sheet (Blast Voyage)

You must be able to reproduce every number below from memory, on a whiteboard, without the document.

## 4.1 The One-Paragraph Recall

*Blast Voyage: tap-to-blast; pop 2+ adjacent same-colored balloons; Coco the red panda pilot restores beloved landmarks on a world tour (Paris levels 1–25, Tokyo 26–50); IAP-only, no ads; one currency; lives 5/30 min; honest Hard/Super Hard flags; "protect the loop" meta where every system feeds on winning the next level.*

## 4.2 The Numbers Table

| System | Value |
|---|---|
| Power-up thresholds | **5–6 → Firework, 7–8 → Confetti Bomb, 9+ → Globe** |
| Novel rule 1 | **Firework orientation = shape of the popped group's bounding box** (wider→horizontal, taller→vertical, tie→toward more goals), previewed on the pre-tap badge; power-up spawns **on the tapped tile** |
| Novel rule 2 | **Breeze Meter**: +1 per balloon popped; fills at **25** (baseline; dial range ~15 generous to ~35 walls); spawns a **Paper Plane** on the filling tile; Plane flies to nearest goal; in combos it **carries** the partner's full effect |
| Combos | Same monotonic table as genre standard + Plane-as-delivery; Plane+Plane = 3 planes; Globe+Globe = board clear |
| Items (no move cost) | **Pin** (1 tile), **Boomerang** (row), **Anchor** (column), **Whirlwind** (shuffle) |
| Item grant levels | Pin 9, Boomerang 19, Anchor 24, Whirlwind 31; pre-level loadout unlocks **21** |
| Power-up intro levels | Firework **4**, Bomb **7**, Globe **14**, combo tutorial **17**, Breeze/Plane **20** |
| Obstacle intro levels | Crates **10** (2-layer at 12), Bubbles **26**, Souvenirs **32**, Mailboxes/postcards **38**, Fog **46** |
| Difficulty flags | Hard: **25, 34, 40, 47**; Super Hard: **50**; colors 3→4 (lv 3), 5 (lv 18), 6 (lv 45) |
| Win-rate targets | Normal 65–90% (position-dependent), **Hard 25–35%**, **Super Hard 10–15%**; attempts-to-pass ≤2 / 3–6 / 7–12 |
| Meta unlocks | Jet Stream streak **13**, loadout **21**, Voyage League **30**, Travel Crews **35** |
| Live-ops | Voyage League (weekly divisions), Balloon Regatta (3-day race), Tailwind Rush (streak pre-charges Breeze Meter), Festival Days (real global festivals), Passport Album (seasonal collection) |
| Obstacle backlog (post-50) | Customs Gates (color locks), Ticket Booths (reverse-spawner), Lanterns (same-turn pairs), Cuckoo Clocks (countdown) |

## 4.3 The Design Logic You Must Narrate Fluently

- **Teaching cadence:** introduce → isolate → combine; *no level in 1–50 teaches two things at once*.
- **Walls only after arming:** Hard #1 (25) lands after streak (13) and loadout (21) — difficulty always meets a resource decision.
- **Breathers flank walls** (24→25→26; 49→50); meta unlocks land on breathers so good news stacks on relief.
- **Meta payoff syncs with difficulty payoff:** chapter finales (25, 50) = flagged walls = landmark completions — the hardest fight and biggest reward are one memory.
- **Fail-with-hope rule:** losing boards must end visibly close; measured via *loss proximity* (avg % of goals complete at failure).
- **Red-flag process:** any level with elevated quit-without-retry or cohort D1-churn spike gets re-tuned within the weekly cycle *regardless of revenue*.

---

# 5. Dream Games — Company Knowledge

*(Verify anything time-sensitive the week of the interview; state dates confidently but be ready to say "as reported publicly.")*

- **Founded 2019, Istanbul**, by five veterans of **Peak Games**: **Soner Aydemir (CEO)**, İkbal Namlı, Hakan Sağlam, Eren Şengül, Serdar Yılmaz. Peak pedigree matters: they built/shipped Toon Blast and Toy Blast, sold Peak to Zynga in 2020 for ~$1.8B, and left to build something even more disciplined.
- **Funding trajectory (publicly reported):** rapid rounds culminating in a **$255M raise in early 2022 at a ~$2.75B valuation** (Index Ventures among lead investors; earlier rounds included Balderton and Makers Fund; a **2025 investment by CVC Capital Partners reportedly valued the company around $5B**). One of the most valuable startups ever from Türkiye.
- **Royal Match:** soft launch 2020, **global launch early 2021**. Rose to the top of the worldwide top-grossing charts — at times **the #1 top-grossing mobile game globally**, out-earning Candy Crush in its own genre. Multi-billion-dollar lifetime revenue. Famous for **no forced ads**, extreme polish, and relentless live-ops cadence.
- **Royal Kingdom:** the second title, **global launch late 2024** — same match-3 engine DNA with a more ambitious meta (kingdom-scale building, an antagonist — the Dark King — adding narrative stakes). *You are level 550 — you know its systems from play better than any briefing; spend an evening writing down its mechanical differences from Royal Match in your own words (new pieces, event formats, meta structure), because "compare Royal Match and Royal Kingdom" is a near-certain question and your first-hand answer is gold.*
- **Culture signals to echo (not flatter):** small teams with an extreme quality bar; craft + data together; "fewer, better things"; hiring slowly and deliberately. Genuine implication for you: they want people who *finish* and *polish*, and who treat tuning as craft.
- **The ads story (know it, handle it maturely):** Royal Match became famous partly through "save the King" style ad creatives that dramatized peril beyond real gameplay; the company later added actual King-rescue-flavored content (e.g., King's Nightmare) that closed the gap. If asked, be balanced: performance-marketing creative and in-game truth converged over time, and the *in-game* product has always been honest with its players where it matters — difficulty flags, pricing, no bait mechanics.

---

# 6. Market & Genre Context

- **The casual puzzle market** is one of mobile gaming's largest and most durable revenue pools (match/blast puzzle alone is a multi-billion-dollar annual category). Key players: **King** (Candy Crush Saga — the legacy giant), **Playrix** (Gardenscapes/Homescapes — decoration meta pioneers), **Peak/Zynga/Take-Two** (Toon Blast, Toy Blast), **Dream Games** (Royal Match — the current benchmark), plus fast followers copying Royal Match's formula.
- **The strategic story you should be able to tell in 90 seconds:** King proved the genre; Playrix proved meta narrative sells; Peak proved tap-blast simplicity and honest difficulty; **Royal Match synthesized all of it and subtracted the friction** — no decoration decisions, no star gates, no ads — betting everything on loop purity plus live-ops density. The result out-executed every incumbent. Royal Kingdom is the test of whether the formula extends to richer metas without losing the discipline.
- **Current genre trends to name-drop credibly:** live-ops as the primary growth lever on mature titles; win-streak systems as standard retention architecture; sticker/album seasonal metas; team-based competitive events; rising UA costs pushing everyone toward LTV depth (events, battle-pass-like tracks) rather than pure install volume; heavy A/B infrastructure on economy values.
- **Why IAP-only (no rewarded ads) is a defensible strategy:** protects session immersion and premium brand feel, keeps the difficulty→spend loop clean (rewarded ads leak monetization pressure), and simplifies the economy. Trade-off: foregoes ad revenue from never-payers — acceptable when LTV depth among payers is world-class. Be able to argue both sides, then land on: for a category leader with Royal Match's polish, trust and immersion compound better than ad ARPDAU.

---

# 7. The Decision-Defense Map — Every Design Choice, the Pushback, and Your Answer

This is the heart of the two-hour interview. Format: **Decision → Why → Expected challenge → Your response** (including what you'd concede).

**1. Travel/world-tour theme.**
Why: borderless global appeal; infinite chapter roadmap; every real festival becomes authentic live-ops; localization becomes marketing.
Challenge: *"Travel is generic. Where's the emotional hook of a King Robert?"*
Response: the hook is Coco + *place attachment* — "your city in the game" is personal in a way castles aren't. Concede: theme differentiation lives or dies on character execution; I'd invest in Coco's acting the way Royal Match invests in the King's.

**2. Balloons as match elements.**
Why: the theme explains the verb (popping IS the fantasy); connects board to meta (balloon travel).
Challenge: *"Balloons are visually soft — will boards read as crisply as cubes?"*
Response: readability is carried by hue separation + per-color symbols + silhouette discipline (documented in §4.1); art direction problem, solvable; and the tactile "poppability" upside is worth it. Concede: would prototype-test board readability first thing.

**3. Shape-determined Firework orientation (novel rule 1).**
Why: converts a random outcome into a visible skill; previewed pre-tap so casuals lose nothing; deepens the one verb without adding verbs.
Challenge: *"Cognitive overload for casual players / tutorializing this is hard."*
Response: it's *invisible-by-default* — a casual who never notices still gets a rocket; the badge preview means discovery is ambient, not gated. Teach it once (level 6's tall board) and let mastery be optional. Concede: the tie-breaking rule (point toward goals) must be playtested for perceived randomness; if players can't predict it, simplify to alternating.

**4. The Breeze Meter + Paper Plane (novel rule 2).**
Why: guaranteed frustration valve; charges from the thing you're already doing; placement and timing add quiet skill; per-level fill cost is a first-class difficulty dial; expresses "hope is a mechanic."
Challenge A: *"Free help every ~25 pops will cannibalize continue/booster revenue."*
Response: it's a *dial*, not a gift — walls run it at 35 where a Plane must be earned; and near-miss frequency (the real driver of continue take-rate) goes *up* when boards stay hopeful. Royal Match's Propeller proves reliable help and top-grossing monetization coexist. I'd A/B fill costs against continue take-rate and D7 jointly — I win either way, because that test is exactly the job.
Challenge B: *"It's just the Propeller with a meter."*
Response: the Propeller inspired the *role* (goal-seeking valve); the creation economy (charge-per-pop), spawn placement (filling tile), pacing control (per-level dial), and delivery-combo behavior are original — per the brief's Note 4, the innovation space was exactly there. Concede the lineage proudly; owning your references reads as senior, not derivative.

**5. Manual cascades (falling balloons never auto-pop).**
Why: blast genre convention; preserves 100% player agency; luck-cascades belong to swap games where the input is slower.
Challenge: *"You're giving up free delight moments."*
Response: the delight budget is spent instead on chain-detonating win celebrations and combo spectacles — *authored* delight, which is tunable. Concede: worth one prototype A/B, but agency is the genre's core feel and I'd protect it.

**6. No per-level star rating.**
Why: chose the Royal Match model — completion purity, zero performance anxiety, no gates; stars add a second currency of meaning that complicates every reward surface.
Challenge: *"Toon Blast's stars power its chest/tournament economy — you left retention value on the table."*
Response: true, and it's a conscious trade documented in my Part 1 analysis; my performance-reward substitute is the leftover-moves detonation bonus (efficiency → coins) plus streak systems. If data showed a mid-game engagement gap, a star-like layer is *addable* later without touching the loop — the reverse migration (removing stars) is nearly impossible. Ship without, keep the option.

**7. First Hard level at 25 (earlier than Royal Match's first wall).**
Why: chapter finale synchronization (meta payoff + difficulty payoff = one memory); player is armed by 13 (streak) and 21 (loadout).
Challenge: *"Too early — you'll spike churn in the FTUE tail."*
Response: the 25–35% win-rate target with a 30% first-attempt expectation is gentle for a flagged wall, and the breather-flank pattern (24, 26) cushions it; but this is precisely a soft-launch calibration question — I'd watch attempt-distribution and quit-without-retry on 25 like a hawk and move the wall if cohorts say so. (Saying "the data may overrule my document" is a *strength* here.)

**8. Six colors by level 45.**
Why: calibrating players early for endgame color counts; introduced on a big board so it reads as variety.
Challenge: *"Six colors at 45 is aggressive vs. genre norms."*
Response: it's unflagged-but-spicy by design with a 72% target; if telemetry disagrees, the color dial is the cheapest thing in the game to re-tune.

**9. IAP-only, no rewarded ads.**
Why: §6 above — trust, immersion, clean difficulty economy; the Dream Games model.
Challenge: *"You're a new IP without Royal Match's brand — can you afford to skip ad revenue?"*
Response: honest answer — for a smaller studio, rewarded video on never-payers is defensible; but as a *Dream Games* concept the strategic answer is loop purity, and the LTV depth from trust-driven long retention is the bet. Show you understand it's a bet, not a religion.

**10. Win-rate targets themselves.**
Challenge: *"Where do 25–35% Hard / 10–15% Super Hard come from?"*
Response: genre-standard bands consistent with my own felt experience at level 500+ in both reference games (walls take ~3–6 / ~7–12 attempts), bounded below by the fail-with-hope covenant. They're *starting priors for soft launch*, not commandments — the per-level instrumentation (attempts distribution, loss proximity, quit-without-retry) is what actually sets them.

---

# 8. Anticipated Question Bank with Model Answers

*(Practice saying these aloud. Model answers are 30–90 seconds spoken; bullets = your beats.)*

## 8.1 About the Analysis (Part 1)

**Q: "Summarize why Royal Match beat Candy Crush in one minute."**
A: Subtraction + operations. It removed every friction the genre had accumulated — ads, decoration decisions, star gates, timers — leaving a pure loop; then it operated that loop harder than anyone: honest difficulty flags that convert frustration into consent, the Propeller as a built-in frustration valve, streak systems that make every next level worth one more life, and an event calendar where everything feeds on the same action. Add category-best polish and input feel, and the moat is *trust* — which compounds daily and can't be copied quickly.

**Q: "You claim swap is 'deeper' than tap. Defend it."**
A: In swap games, booster manufacture requires *formation planning* — you're constructing shapes several moves ahead; in tap games, it's *threshold patience* — grow groups, manage adjacency. Both are real skill, but the swap planning horizon is longer, which is why my Royal Match sessions at 550 feel more deliberate than my Toon Blast sessions at the same band. Tap's compensation is pace and accessibility — which is exactly why the case brief asks for a tap game, and why Blast Voyage adds *depth back* through shape-aiming and meter timing without touching the verb.

**Q: "What's the smartest single design decision in Toon Blast?"**
A: The pre-tap booster badge. It turns every board into a visible market — pop now or grow the group — which is the entire skill economy of the genre rendered as one UI element. I stole the principle for Blast Voyage and extended it to preview orientation, not just type.

**Q: "What would you change about Royal Match?"** (They *will* ask some form of this.)
A: Pick 1–2 affectionate, specific, defensible items and phrase as hypotheses to test, e.g.: (1) mid-game event-popup stacking after wins can get heavy — I'd A/B a batched "rewards summary" against the sequential popups on session-length and event participation; (2) at deep levels the between-walls stretches can feel flat — I'd test micro-variety injections (modifier levels like pre-charged boards) on D30 cohorts. Never: "add ads," "add gacha," or anything that violates their loop-purity identity.

## 8.2 About Blast Voyage (Part 2)

**Q: "Pitch Blast Voyage in 60 seconds."** — Memorize §4.1's paragraph + one pillar sentence: "One verb, zero friction; skill you can see; hope as a mechanic; a world worth restoring."

**Q: "Which of your two novel mechanics would you cut if forced, and why?"**
A: Shape-aiming — reluctantly. The Breeze Meter is load-bearing (it's the frustration valve, a difficulty dial, and an event hook — Tailwind Rush — simultaneously); shape-aiming is depth-enrichment. Cutting the load-bearing one would change the game's promise; cutting the enrichment only lowers the ceiling. This answer shows you know your own design's dependency graph.

**Q: "Design levels 51–75 right now."**
A: Framework aloud: new chapter (Istanbul), one new obstacle class introduced at ~53 (Customs Gates from my backlog — color locks that finally make *color choice* strategic, a natural post-fog escalation), isolate then combine through the 60s, colors mostly 5 with 6 on spice levels, Hard at ~58, 65, 72, Super Hard finale at 75 synced to the tea-garden restoration, breathers flanking every wall, and one "confidence builder" with a 15-cost Breeze Meter before the finale. You just demonstrated the strategy generalizes.

**Q: "Your Breeze Meter — walk me through the exact A/B test."**
A: Hypothesis: fill cost affects churn and monetization in opposite directions; find the trust-preserving optimum. Cohorts on fill cost 20/25/30 (new installs only, levels 20–120). Primary metrics: D7/D14 retention, continue take-rate on flagged walls, attempts-to-pass on walls, quit-without-retry. Guardrail: loss-proximity (fail-with-hope) must not degrade. Decision rule pre-registered: if 30 lifts revenue but D7 drops beyond threshold, trust wins — we take 25. That last sentence is your tuning covenant, said like an operator.

**Q: "How does Blast Voyage make money in month 12 for a level-800 player?"**
A: Same engine, deeper meaning stack: walls tuned against a richer owned-booster economy; streak protection (Jet Stream at stage 3 is worth real coins, making continues rational); league/crew standing as social stakes; seasonal Passport nearing completion as sunk-cost momentum; and festival events as recurring spend peaks. The month-12 payer isn't buying moves — they're buying *momentum preservation*.

## 8.3 Analytical / Operator Scenarios

**Q: "Level 214's win rate dropped from 28% to 15% overnight. Go."**
A: (1) *Verify before acting:* real drop or instrumentation/version artifact? Segment by app version, platform, cohort. (2) *Diff the causes:* was a change shipped — level tweak, economy value, booster price, an event ending that had been supplying free boosters? (The most common real answer: an event that pre-armed players rotated out.) (3) *Check player state:* are players arriving at 214 with fewer boosters/lower streaks than before — upstream change, downstream symptom. (4) *Act proportionally:* if authored difficulty is the cause, re-tune moves/meter; if upstream, fix upstream; communicate in the weekly tuning cycle. Never tune the level first and ask questions later.

**Q: "D1 retention is fine, D7 is sagging. Where do you look?"**
A: The days-2–6 experience: wall placement in levels ~30–120 (attempt distributions, quit-without-retry), lives economy friction (are players bouncing off empty lives with no crew yet — note my design unlocks crews at 35 partly for this), meta unlock pacing (is there a 'nothing new' desert), and notification/return-trigger performance. Cohort by acquisition source too — a UA-mix shift can masquerade as a product problem.

**Q: "How would you decide the price of the continue?"**
A: Anchored A/B against take-rate × downstream retention, segmented by payer status; the continue is priced not to maximize per-event revenue but to keep the *near-miss → continue → triumph* loop feeling fair — overpriced continues teach players that near-misses are extraction, which erodes the trust that funds everything else.

## 8.4 Behavioral (Product Lead version)

- *"Tell me about a time you changed your mind because of data."* Prepare one real story; if your document offers one, use the honest framing: "writing my case, I started believing X, then realized Y" (e.g., you initially wanted auto-cascades for spectacle, then chose agency).
- *"Tell me about receiving harsh feedback on work you were proud of."* Show upgrade-not-defend behavior — it's the exact behavior they'll test live when they challenge your document.
- *"A designer and your data disagree. What do you do?"* Reframe: data says *what*, the designer often knows *why*; my job is designing the test that lets reality arbitrate — and pre-agreeing what result changes whose mind.

---

# 9. Live Design Exercise Playbook

If handed a marker and a prompt, use a visible framework — they're grading the *shape* of your thinking.

**Universal skeleton (say the steps aloud):**
1. **Player & moment:** who is this for and where in their lifecycle?
2. **Emotion target:** what should the player *feel*? (hope, momentum, prestige, relief)
3. **Loop fit:** does it consume the core action (winning levels) or compete with it? Never compete.
4. **Mechanics sketch:** simplest version that delivers the emotion.
5. **Economy touchpoints:** sources, sinks, and where spend pressure arises *fairly*.
6. **Metrics & test plan:** primary, guardrail, decision rule.
7. **Risks & cut-line:** what you'd drop for v1.

**Prompt: "Design a new event for Royal Match."** Example run: lapsed-player re-entry event → emotion: "the game missed me" → mechanic: 48-hour comeback track where first N wins pay escalating streak-restoration gifts (rebuilds the Butler's Gift state they lost by lapsing) → consumes core loop, zero new verbs → metrics: lapsed-cohort return rate, week-2 re-retention; guardrail: no cannibalization of active-player event participation.

**Prompt: "Add a social feature to Blast Voyage."** Crew Postcards: each personal win contributes a stamped postcard to a shared crew mailbox; filling it opens a crew chest. One-verb rule preserved; visible individual contribution (the retention magic of team systems); lightweight.

**Prompt: "This obstacle tests badly — fix it."** Ask what "badly" means (win rate? comprehension? fun-score?), because the fix differs: comprehension → isolate its tutorial level and its visual state-telegraphing; win rate → depth/count/moves dials; fun → usually the obstacle acts on the player without counterplay — add a counterplay verb-interaction.

---

# 10. Metrics Glossary — Speak the Language Fluently

| Metric | Definition | The sentence that shows fluency |
|---|---|---|
| **D1/D7/D30** | % of installs returning on day N | "Wall placement problems show up in D7 before they show in revenue." |
| **ARPDAU** | Avg revenue per daily active user | "Events lift ARPDAU; trust protects the DAU it multiplies." |
| **Conversion** | % of players who ever pay | "The continue at a near-miss is the genre's #1 first-purchase trigger." |
| **LTV / CPI / ROAS** | Lifetime value / cost per install / return on ad spend | "Rising CPIs are why LTV depth via live-ops beats install volume." |
| **Attempts-to-pass** | Distribution of tries per level | "I read the distribution, not the mean — a long tail is churn hiding." |
| **Quit-without-retry** | Fail → app close, no retry | "My single favorite red-flag metric; it's frustration in its purest form." |
| **Continue take-rate** | % of fails converting to a continue purchase | "Take-rate is a fairness thermometer as much as a revenue line." |
| **Loss proximity** | Avg % of goals complete at failure | "My fail-with-hope covenant, made measurable." |
| **Sink/source balance** | Currency inflow vs. outflow | "Single-currency design lives or dies on this ledger." |
| **Cohort analysis** | Grouping users by install date/source for comparison | "Never evaluate a tuning change on mixed cohorts." |

---

# 11. Your Personal Play Stories — Prepare These From Your Own Experience

Nothing in the two hours will land harder than specific first-person moments. Before the interview, write down (from your actual play — these must be yours, not mine):

1. **A Royal Match level that took you many attempts** — its number, what made it evil (geometry? colors? spawner?), what finally worked, and how you felt. This single story proves more than ten slides.
2. **Your favorite combo moment** (e.g., a Propeller carrying a Light Ball into a corner safe) and *why* it felt so good — connect it to the delivery-combo mechanic you designed into the Paper Plane.
3. **A moment a game felt unfair** — and whether you kept playing. This powers every trust/tuning answer you'll give.
4. **Your team/crew experience** — a time lives-gifting or a team event changed your session behavior.
5. **Royal Kingdom vs. Royal Match differences you've *felt*** at level 550 — meta weight, event formats, difficulty texture, anything the Dark King framing changes emotionally. (Near-certain question; your first-hand comparison is your unique asset — I can't write this for you as authentically as your own play can.)
6. **The current week's live state of both games** — active events, current offers, what's new. Refresh this the morning of the interview. "As of this morning, the rotation is…" is a devastating credibility move.
7. **A Match Villains observation** — one thing a smaller competitor does worse (input latency, effect readability, event pacing) — proves your comparative eye extends beyond the giants.

---

# 12. Questions to Ask Them

Pick 3–4; they signal what you care about:

1. "How does the level-tuning loop actually run here — what does a level's journey from designer to global look like, and where does a Product Specialist sit in it?"
2. "What's a decision where player-trust and short-term revenue conflicted, and how was it resolved?" (Shows you understood their moat.)
3. "What did Royal Kingdom teach the company that Royal Match couldn't?"
4. "What separates a good Product Specialist here from a great one, a year in?"
5. "What's the most contrarian design belief the team holds that the industry disagrees with?"
6. (If time feels right) "Was there anything in my case study you disagreed with? I'd genuinely rather hear it now." — Bold, memorable, and invites the exact conversation you're best prepared for.

---

# 13. The Two-Hour Game Plan — Pacing, Materials, Demeanor

- **Bring:** printed copies of both documents (one for them, one annotated for you), a one-page numbers cheat sheet (memorized anyway), and a notebook. If remote: both documents open, wireframes ready to screen-share.
- **Open strong (first 5 minutes):** they'll likely ask you to walk through the case. Do NOT read the document. Deliver: 90-second Part 1 thesis ("subtraction + operations; protect the loop"), 90-second Blast Voyage pitch, then: "I'm happy to go section by section, or dive wherever you want to push." Handing them the steering wheel signals confidence.
- **Answer shape:** claim → reason → evidence (game example or metric) → concession if real. 60–90 seconds, then stop talking. Silence after a good answer is your friend, not a gap to fill.
- **When challenged:** never defend the pixel, defend the layer; concede genuinely when they're right ("that's fair — here's how I'd revise it") — *they are testing coachability as much as correctness*.
- **When you don't know:** "I don't know the number, but here's how I'd find out" + the actual query/test design. Operators love this; bluffers die here.
- **Whiteboard reflex:** any question with more than two moving parts — stand up and draw. The §9 skeleton, the difficulty pulse curve, the funnel. Physical structure = perceived seniority.
- **Energy management:** two hours is long. Water. Brief recaps at section transitions ("so far we've covered X — want to move to the meta design?") make *you* feel like the meeting's co-owner rather than its subject.
- **The lasting-impression close:** if given a final word, use the three themes: "Everything I believe about this genre is in those three ideas — protect the loop, hope is a mechanic, trust compounds. That's the product person you'd be hiring."

---

# 14. Final-Week Checklist

- [ ] Play Royal Match, Toon Blast, and Royal Kingdom **daily**; screenshot current events, offers, and your progress the morning of the interview.
- [ ] Re-verify every §3 fact against your live builds; note anything that changed since the document (mentioning a change *yourself* is a credibility weapon: "since I wrote this, the event rotation added X").
- [ ] Rehearse aloud: 90-second Part 1 thesis, 60-second Blast Voyage pitch, the §4.2 numbers table from memory, and the three campaign themes.
- [ ] Write your five personal play stories (§11) in your own words.
- [ ] Do one full mock: have a friend fire 15 questions from §8 in random order; practice stopping at 90 seconds.
- [ ] Prepare §12 questions; print documents; test tech if remote; sleep.
- [ ] Morning of: 20 minutes in the games, one read of the cheat sheets (§3–4), then trust your preparation.

*You wrote a document good enough to get you into the room. The interview is the same skill performed live: love the games specifically, defend decisions structurally, concede gracefully, and connect every feeling to a lever. Go get it.*
