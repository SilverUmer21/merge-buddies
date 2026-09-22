# Merge Buddies — V1 game design document

Version 0.2 · 2026-09-22 · Revised for the user's apple-to-pie clarification. Design proposal, not an implemented game.

## Product

Help a cheerful cat and chick prepare a picnic by merging matching items through recognizable crafting stages on a small wooden tray. Apples become sliced apples, then filling, then a pie. Each completed request adds one visible detail to the picnic. The delight comes from discovering a satisfying next form and the buddies' reactions.

User requirements: Android first; Godot; exactly 4×4 cells; cute gamified art matching the supplied reference; logical merges; restrained scenery; lively assets and board; art-first production followed by a minimal game. Audience is children 13 or younger. Proposed usability focus is ages 7–12; younger children may need assistance. This age focus needs testing, not assumption of universal suitability.

Proposed V1: portrait, offline, single player, one picnic setting, cat and chick, two item families with four tiers each, 12 short authored puzzles including tutorial, one completion scene, local progress. Target 2–5 minutes per puzzle is a playtest hypothesis.

Exclude from V1: currencies, store, ads, energy, timers, streaks, accounts, chat, cloud saves, procedural levels, multiple worlds, separate multi-ingredient crafting stations, farming simulation, live events, and monetization. Simple recipe-themed merge chains are included. Decide distribution and business model after the slice is enjoyable.

## Merge semantics

One input rule: merge two matching items at the same stage to create the next stage in their family. The meaning is stylized preparation or crafting, not literal physical addition. Intermediate stages must make the transformation understandable. The user's apple-to-pie example supersedes the initial quantity-only proposal.

| Family | Tier 1 | Tier 2 | Tier 3 | Tier 4 | Meaning |
|---|---|---|---|---|---|
| Apple pie | Apple | Sliced apples on a small board | Apple filling in a bowl | Golden apple pie | Slice → Mix → Bake |
| Biscuits (proposed second chain) | Flour bag | Dough ball | Cut biscuit shapes on a tray | Baked flower-shaped biscuits | Mix → Shape → Bake |

Each tier changes silhouette, material, or preparation state. A small live stage badge is optional if the art alone is not clear; it is a stage number, not an ingredient count. The first discovery shows a short verb and the chain preview. A warm oven-shaped cue on Bake can explain the transition without a separate appliance inventory or waiting timer. Shared pantry ingredients and tools are part of the buddy-kitchen fiction: the merge is a shorthand for preparation, not a real recipe or a nutrition lesson.

Apple + flour: invalid under the single-family input rule. Unequal stages: invalid. Final stage + final stage: invalid; deliver the requested finished item instead. Requests may also ask for an intermediate preparation, such as sliced apples, during teaching. Family definitions declare their final stage rather than assuming every future family has four stages.

The standard is plausible connection, not exhaustive realism. A droplet becoming a river changes scale and context without a useful crafted outcome; apples becoming pie have a familiar ingredient-to-food relationship. Avoid arbitrary jumps, but do not burden every transition with extra tools and resources. The chain preview and a short process cue should carry the explanation.

Tradeoff: meaningful transformations give stronger discovery and visual variety, but every stage needs distinct art and clear semantics. Start production with one complete chain, then add families in coherent batches. Two families are a proposed first-release slice, not a permanent content ceiling. See MERGE_CHAINS.md for the expandable catalog and pros/cons.

## Proposed puzzle rules

These rules add spatial planning. Free merging anywhere plus an infinite supply would be closer to an activity toy than a puzzle.

1. Board is a fixed 4×4 array. Each cell holds zero or one item. No gravity, automatic refill, diagonal movement, or automatic cascades.
2. Select an item, then select an orthogonally adjacent destination. Empty destination: move. Equal family/tier: merge into the destination and empty the source. Other occupied destination: reject without changing state.
3. Dragging is an optional equivalent to select-then-tap. Invalid or off-board drops return the item. Selecting the same item again or Back cancels selection. No swapping.
4. Supply sits outside the board in a visible, finite authored queue. Select the next supply, then any empty cell to place it. Show the next three entries and total remaining. Only the first entry can be placed. Full board disables placement, not merging or delivery.
5. Show one request at a time with exact item stage and item count. Select a matching item anywhere on the board, then tap Deliver. Delivery consumes that item and updates the request. No overfilling or accidental consumption.
6. A request may need several matching items. Deliver each separately. A full request advances to the next. Puzzle completes when all authored requests are met; unused supplies may remain.
7. Undo restores the previous complete action: board, queue index, request progress, and completion state. Free unlimited undo within the current puzzle; restart resets its authored state. Neither consumes resources.
8. There is no timer or move cap. A full board alone is not failure. When no move, merge, placement, or delivery is possible, explain the blockage and offer Undo or Restart. Local legal moves do not guarantee solvability; an optional Hint can initially just explain rules, not promise a solution.
9. Commit one valid action atomically before its animation, lock further board actions until it finishes, then allow input. Invalid actions never consume supplies or history. Pause/back during animation must not duplicate items.
10. Save settled state after each action. Resuming reconstructs the board from data, without replaying rewards. Completion is recorded once; leaving a completed puzzle commits it. Undo before leaving can restore pre-completion state.

Model checks: a merge consumes two matching stage IDs and creates exactly the declared next-stage ID, reducing occupied cells by one. Movement conserves items; placement consumes exactly one queue entry; delivery transfers the exact requested item into fulfilled requests. Optional internal merge weights 1/2/4/8 can verify accounting across this two-to-one chain, but they are abstract progression weights, never claimed physical ingredient quantities. Rule validation must reject missing next stages and cross-family inputs.

## Small concrete tutorial

Coordinates are row, column, starting at 1. Put an apple at (2,2) and (2,3); all other cells empty. Request: sliced apples for the buddy's pie preparation. Supply queue empty.

Prompt: “Merge matching apples.” Select (2,2), then (2,3). A short “Slice!” cue accompanies the result: sliced apples at (2,3), with (2,2) empty. Prompt: “Send them to your buddy.” Select the slices and Deliver. Cat reacts; puzzle completes. Preview the eventual pie to establish what the chain is working toward.

This is a rule example, not a validated shipped level. Later levels introduce moving into empty cells, supply placement, filling and pie, biscuits, then mixed-family planning. Do not introduce all concepts together.

## Content plan

| Puzzles | New concept | Constraints |
|---|---|---|
| 1–2 | Merge and deliver | Apples only; two visible matching singles initially |
| 3–4 | Empty-cell movement and placement | Plenty of free space; explicit supply preview |
| 5–6 | Filling and finished pie | Apple chain only; show Mix and Bake process cues |
| 7–8 | Biscuit family | Introduce separately before mixing |
| 9–10 | Two-family requests | One visible request at a time; queue stays predictable |
| 11–12 | Combine learned rules | Fewer empty cells; free undo remains available |

Every authored level needs a recorded solution trace and a replay check. Exact layouts and difficulty are future work. If adjacency feels fiddly on a phone, compare free movement to empty cells in a disposable rules experiment before producing 12 levels. Keep the 4×4 board fixed in either case.

## UI and presentation

Portrait logical frame: 360×800, scaled responsively rather than treated as fixed physical pixels. Support 360×640 and 412×915 logical layouts plus Android safe areas and text scaling. At 360-wide, use 16-unit side margins, a 328-wide board frame, 10-unit inner padding, 8-unit gutters, and 71-unit square cells: 20 + 4×71 + 3×8 = 328. Sprite visible body approximately 52–58 units; cell remains the full input target.

Top: small buddy portrait, puzzle number, settings. Below: one request with item preview and concise text. Center: 4×4 board, the main focus. Below board: supply queue and contextual Deliver. Bottom: Undo and Restart. Quiet landscape margins and a tiny picnic progress vignette support the board; do not reproduce the reference's title poster beside gameplay.

Screens: compact title/continue, board, settings overlay, completion. Replay completed puzzles from a simple list; no world-map asset set. Settings include music/SFX volume, reduced motion, and text size. Use native text and controls, clear selection/focus state, icon plus label, and comfortable approximately 48-unit minimum control targets as an internal design target. Validate on devices; this is not a physical-size guarantee.

Selected objects lift visually without moving their hit regions. Show legal destinations with a border and symbol, not color alone. Do not animate a hint continuously. No essential sound-only information. Android system Back closes overlays/cancels selection before leaving gameplay; save before backgrounding.

## Feel and audio

Timing proposals, to be tuned in the art lab: press 70–100 ms, lift about 100 ms, merge 220–300 ms with a short squash/pop, invalid return 120–160 ms, delivery 300–450 ms, buddy celebration under 800 ms. Allow at most one focal action effect and a few short sparkles. The board may flex locally at the destination; never shake or translate all cell targets.

Idle: cat blink, occasional chick head tilt; a leaf may sway slowly at an edge. No 16-item synchronized bouncing. Reduced motion removes overshoot, particles, and decorative idle loops while retaining clear immediate state changes.

Plan six quiet feedback sounds (select, move, merge, invalid, deliver, complete), one soft ambient loop, and one short music loop. Source licenses before shipping. Silence is a valid first art-lab state; avoid placeholder sounds that set the wrong tone.

## Technical boundary and validation

Godot 4.7.2 confirmed through MCP. Use a pure board model separate from native Control-based views, data-defined item families/levels, presentation events, and snapshot undo. Use normal Godot animation tools for approved sprite parts. Exact scene/script structure is a later coding task. No server required.

Local save schema records version, puzzle ID, cells, queue index, request progress, completed puzzle IDs, settings, and undo history for the current puzzle. Write atomically; recover a last-good save or safely restart only the current puzzle on corruption. Never log personal information.

Android readiness requires checking SDK/JDK/export templates, signing configuration kept out of Git, and installation on an actual test phone. The presence of MCP is not proof these work. Choose a named lower-end reference phone at the slice stage. Target responsive input and stable 60 fps there; measure before claiming performance.

V1 acceptance: all 12 levels have replayable solutions; invalid inputs conserve state; undo/restart/resume are exact; no duplicate rewards; full-board messaging is correct; all controls remain reachable at target sizes; tap-only play works; reduced motion works; no missing art/licenses; primary and user approve final visual captures. Test on actual Android hardware, including pause/resume and rapid repeated taps.
