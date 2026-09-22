# V1 roadmap

Plan by acceptance gates, not promised dates. Art iteration counts and Android setup cost are unknown. User approves creative outputs; primary reviews them before presentation. User confirmed the order: finish and iterate asset graphics first, then build in Godot, then primary reviews, then user reviews the game. The isolated browser art lab is for visual inspection only.

| Stage | Deliverable | Owner | Exit gate |
|---|---|---|---|
| 0. Foundation — current | GDD, art bible, reference, manifest, tradeoffs, repo | Primary | Documents saved; user can review proposed theme/rules independently of fixed requirements |
| 1. Art proof | One apple family, board sample, select/merge animation in isolated lab | Primary | Reference comparison passes at phone scale; user approves family and board direction |
| 2. Complete graphics kit | Remaining family, cat/chick expressions, UI skins, restrained backdrop, motion studies | Primary art | Required graphics reviewed and approved in art lab; manifest updated; no reference drift |
| 3. Godot integration and minimal loop | Import approved art, make one puzzle with move/merge/supply/delivery/undo; Android build | Luna High bounded implementation; primary review | Confirm toolchain and actual-device visuals, working rules, and no state corruption |
| 4. Game presentation | Wire approved motion, audio, responsive UI, reduced motion | Primary direction; Luna bounded implementation | Presentation matches approved graphics; input and effects remain clear on Android |
| 5. V1 content | 12 authored puzzles, simple progression, local save, settings | Luna High implementation; primary level tuning | Each puzzle has solution trace; difficulty grows gradually; save/resume and recovery pass |
| 6. Release candidate | Android build, full-device playthrough, final art/performance review | Primary acceptance; Luna bug fixes | All V1 acceptance checks pass on named target phone; license/provenance complete; zero blocking defects |

Stage 3 starts after graphics approval and is deliberately tiny. No Godot game implementation during the graphics phase. Art-lab interactions are disposable visual studies, not the game architecture.

## Review points

- After stage 1: is apple-to-pie progression understandable and satisfying, and are all four stages distinguishable at actual size? If not, improve intermediate shapes/process cues before mass production.
- After stage 2: does the whole graphics kit remain cohesive at phone-size layout? After stage 3, verify it on the actual phone and repair import/scale issues before adding content.
- After stage 3: is adjacent movement enjoyable or fussy? Compare a short free-movement variant if necessary; document the decision before level authoring.
- After stage 5: can new players learn without constant adult explanation? Observe representative younger and older players within the target audience, with parent involvement; record task outcomes without collecting identities in the game.

## Proposed playtest criteria

These are decision targets, not claimed research results: first merge within one minute after the tutorial cue; players understand matching items advance their crafting chain and reject cross-family combination; players can find Undo without help; stages and request counts are readable without opening every tooltip; no repeated accidental drop pattern; players notice the result before decorative effects. If several testers struggle in the same place, revise that mechanic or asset before release.

Target session duration is 2–5 minutes per puzzle. A 12-level set should form a small complete experience, not an endless progression promise. If the core loop lacks replay interest, polish the finite experience rather than adding grind.

## Risk and scope cuts

| Risk | Evidence to collect | Response |
|---|---|---|
| Unclear crafting transitions | Native-scale chain and player explanation | Improve intermediate silhouettes and process cues; avoid unnecessary simulation systems |
| Adjacency causes frustration | Invalid-input frequency and player explanations | Test free movement into empty cells, preserving matching-stage merge rules |
| Sixteen cells feel too constrained | Solution traces and time spent stuck | Adjust authored supply/layout/request order; never enlarge board |
| Art drift | Comparison sheet under identical lighting/scale | Reuse approved seed, revise or discard draft |
| Delegate token churn | Number and cause of failed handoffs | Primary fixes ambiguous spec; bound retries and summarize evidence |
| Android setup/performance | Early installed build on named phone | Resolve before full content production |

If schedule must shrink: cut scenery detail, secondary buddy animation, music, then reduce the number of levels with an explicit scope revision. Keep coherent art, the 4×4 board, understandable rules, undo, reliable saves, and phone verification.

## After V1, only with a new decision

Potential directions: explicit growing/care actions; a separate two-ingredient recipe station; another small scene; additional item families. Evaluate each with benefit, cost, merge meaning, UI footprint, and playtest evidence. They are not current backlog commitments. Store release, pricing, analytics, ads, and online features require a separate product decision.
