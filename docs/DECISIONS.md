# Decisions, alternatives, and evidence

2026-09-22. Distinguish requirements, proposals, and verified environment facts.

## Fixed by the user

- New project: Merge Buddies; remote `https://github.com/SilverUmer21/merge-buddies`.
- Godot; Android first (confirmed in the planning exchange).
- Exactly 4×4 board; cute illustrated game graphics inspired by the supplied reference.
- Children 13 and younger; logical merges; limited competing environmental detail.
- Art/assets first, then minimal game; deliberate animation and UI/UX; step-by-step work.
- Current deliverable is planning and saved design knowledge. The old quoted prompt is background, not an instruction to output unrelated new art examples or prohibit writing planning files.

## Proposed choices and alternatives

| Decision | Benefit | Cost / risk | Alternative and reason deferred |
|---|---|---|---|
| Picnic preparations | Familiar crafting goals, small story, natural reason to prepare/deliver | Less world-building than a farm | Full farm introduces growing/harvesting/economy before the merge is proven |
| Recognizable crafting chains | User favors apple-to-pie transformations; more discovery and distinct forms | Intermediate steps and process cues need care | Quantity-only grouping was too restrictive and has been superseded |
| Two initial families, four stages | Eight item designs establish an achievable first slice | Limited novelty if treated as the entire long-term game | Expandable catalog exists; assess additional V1 families after the first chain and slice |
| Adjacent merges/moves | Makes 16-cell spatial planning matter | Extra taps and possible deadlocks | Free movement is a fallback experiment, not silently adopted |
| Finite authored supply | Reproducible challenge and undo, no unlucky drops | Requires level design and solution checking | Random generators create balancing and fairness work |
| No move/time limits | Children can think and recover | Less competitive pressure | Optional challenge modes can follow an enjoyable core |
| Art proof before full code | Tests the product's main quality bar early | Some art may need adjustment after rules test | A huge greybox game would defer the user's priority too long |
| Quiet buddy animation | Personality without hiding choices | Requires intentional animation limits | Constant bouncing competes with board readability |
| Tap-select/tap-target plus drag | Supports users who struggle with dragging | Two input paths to test | Drag-only is less flexible |
| Offline finite V1 | Small technical scope and predictable sessions | No cross-device progress | Network features do not help prove the core loop |

Quantitative values (timing, logical sizing, content count, session length) are design hypotheses. Research below supports accessible interaction patterns; it does not prove the theme is appealing or the puzzles are balanced.

## Research used

Read on 2026-09-22. Focused primary guidance rather than popularity claims.

1. [Game Accessibility Guidelines: keep accurate interaction targets stationary](https://gameaccessibilityguidelines.com/make-interactive-elements-that-require-accuracy-eg-cursor-touch-controlled-menu-options-stationary/). Supports fixed cell hit regions while sprites animate. It does not prohibit all decorative movement.
2. [Game Accessibility Guidelines: alternatives to simultaneous actions and dragging](https://gameaccessibilityguidelines.com/ensure-that-multiple-simultaneous-actions-eg-click-drag-or-swipe-are-not-required-and-included-only-as-a-supplementary-alternative-input-method/). Supports a tap-select/tap-target path alongside drag.
3. [Game Accessibility Guidelines: basic guidance](https://gameaccessibilityguidelines.com/basic/). Supports generous spaced controls and considering accessibility early. Our 48-unit control target is a proposed project metric, not a claim that this source specifies that exact number.
4. [Android Developers: natural input on all form factors](https://developer.android.com/games/develop/multiplatform/enable-natural-input-on-all-form-factors). Supports avoiding assumptions that touch is the only available input and preserving desktop input for development/review. Android-first still requires testing touch on hardware.

Research route: agent-reach GitHub CLI was available but not authenticated; Exa worked on retry outside the network sandbox. Web search also returned accessibility guidance. Git transport confirmed the remote was empty and cloned it. No claim was made about existing repository code. No market-size, developmental, legal, or model-cost claims were inferred from these sources.

## Environment verified

- Separate local clone created at `Games/merge-buddies`; parent Orbit Shift remote preserved.
- Remote had no refs at inspection; clone reported empty repository.
- Godot MCP returned `4.7.2.stable.official.ed1daf0bf`.
- User reference copied unchanged and hashed in ART_BIBLE.md.
- Android SDK/JDK, export templates, signing, phone connection, device performance: not yet checked.

## Open creative decisions

Confirm picnic premise and exact crafting stages when reviewing the plan. The user supports many logically related merge assets and gave apple-to-pie as an example; the quantity-only interpretation is retired. Review adjacent movement after a small rules experiment. Choose exact font, hero asset construction method, lower-end Android reference device, audio sources, and distribution route at their appropriate gates. These do not block documenting the plan. Do not treat silence as asset approval.
