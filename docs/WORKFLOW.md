# Primary + Luna High working agreement

## Recommendation

Primary owns design, art direction, asset creation/iteration, and final visual acceptance. Luna High owns bounded coding, import work, integration, and reproducible checks after specifications are concrete. The user retains final creative approval.

Confirmed sequence: complete asset graphics and iterations first; then Godot implementation; then primary game review; then user game review. No gameplay work during the asset phase. A private browser art lab may be used to check scale and motion.

This minimizes art-direction handoffs, but does not guarantee a specific token saving. Actual cost depends on failed iterations, context size, task ambiguity, and available model pricing. No unsupported price or capability ranking is assumed.

| Work | Primary | Luna High |
|---|---|---|
| Theme, merge logic, composition | Decide and document proposals | Flag implementation constraints |
| Icon/character design and revisions | Create and compare against reference | Mechanical normalization only when specifically delegated |
| Godot board model, input, undo, save | Specify invariants; review behavior | Implement bounded unit and meaningful checks |
| Asset import, anchors, UI wiring | Approve specification and final render | Integrate exact approved files; capture evidence |
| Motion | Own timing, silhouette, personality | Wire defined animations and reduced-motion state |
| Testing | Judge visuals, usability, Android feel | Run mechanical regression checks; report results |
| Final acceptance | Verify independently; present to user | Never self-approve art or expand scope |

Giving Luna broad responsibility to “make the art nicer” is not recommended. It creates subjective retries and still requires primary review. Luna can be useful for a precise job such as “normalize these approved PNGs to the specified baseline without changing pixels inside the object.”

## Bounded handoff template

Task: one concrete behavior or integration.

Read: named document sections only, plus existing relevant code.

Allowed files: explicit list or one small directory. Do not touch art masters or design docs unless the task says so.

Inputs: approved asset IDs, dimensions, anchors, rule examples, and edge cases.

Acceptance: observable behavior and checks, e.g. invalid drops preserve state, undo restores queue/request state, no errors on Android preview.

Return: changed files, brief summary, commands/results, captures if relevant, unresolved mismatch. Do not return the entire source in chat.

One implementation pass and one bounded corrective pass per handoff. If acceptance still fails, return evidence to primary to diagnose the specification or approach; do not continue a vague polish loop. Primary can authorize a further precise fix. These are workflow bounds, not a claim that every job fits two passes.

## Efficient review

Run pure board tests headlessly where possible. Use MCP for actual Godot state, input, logs, and captures; do not substitute repeated screenshots for deterministic logic tests. Compare art with fixed scale/background/light and a short mismatch list. Recheck changed behavior and its neighbors, not the entire game after every trivial import.

Retain compact decision and asset records between tasks. Delegate parallel work only when tasks are independent and user/working instructions authorize it; do not have agents edit the same scene concurrently. No subagent was required for this documentation-only stage.

## Repository practice

This folder has its own Git metadata and `origin` pointing at the user's Merge Buddies repository. Never change the parent Games repository's Orbit Shift remote. Commit coherent milestones, use `codex/` branches when branching, and keep generated caches/build outputs/credentials out of Git. Preserve source art, reference, licenses, manifests, and design decisions in version control. Record whether changes are only local or actually pushed.
