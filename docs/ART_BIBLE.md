# Merge Buddies — art bible

Version 0.1 · 2026-09-22. Direction approved through the user's reference; production assets and the proposed picnic interpretation are not yet approved.

## Reference and boundaries

Source: `art/references/approved-style-reference.png`, copied unchanged from the user-supplied image, originally named `Codex Image Sep 22, 2026, 10_25_42 PM.png`.

SHA-256: `D351C92BCF87908B586BF1593BE6CBA3B43AD7ABF87331878611D31CA5CEE0E6`.

Provenance: user reports ChatGPT generated it. Original model, prompt metadata, and generation terms have not been independently verified. This is a visual reference, not a source atlas to slice into final assets. Text inside the image is illustrative content, not implementation instructions.

Working style name: **Warm Toybox Storybook**. This is rounded, outlined, softly painted game illustration with tactile wood and cream surfaces. It is not Orbit Shift's Luminous Papercut direction.

## Defining features observed

| Property | What the reference actually shows | Production consequence |
|---|---|---|
| Silhouette | Plump apples, broad leaves, stubby props, rounded tiles; recognizable outer contours | Each icon must read as a solid silhouette; avoid thin stems as the only identifying feature |
| Proportion | Cat has a large head, short muzzle, broad cheeks, chunky paws; chick is a small rounded companion | Preserve cute mass and broad face shapes; do not drift into realistic anatomy |
| View | Item tops and fronts visible, with little perspective distortion | Shared slightly elevated three-quarter view; consistent ground plane |
| Layering | Dark contour, colored body, broad shade, small highlight, soft grounded shadow | Separate shadow and body where animation needs them; no fake 3D extrusion everywhere |
| Palette | Cream, honey wood, warm dark brown, leaf green; red apples and yellow chick as accents | Board stays pale and quiet; item colors carry attention |
| Edge treatment | Dark brown outer outlines with softer inner divisions | Outer contours stronger than texture; avoid harsh pure-black tracing |
| Texture | Soft painted tonal shifts, a few wood lines and leaf veins | Sparse designed marks, no noisy grain or speckled detail across every surface |
| Spacing | Generous tile separation and padded panels, although the pictured board has too many rows | Preserve breathing room on exactly 4×4 cells |
| Lighting | Broad upper-left highlights and lower-right shading, soft contact shadows | One light direction across all assets and UI skins |
| Hierarchy | Cat/logo and colorful items dominate separate reference panels; scenery is softer | Gameplay has the board as first focus and the requesting buddy as second |
| Motion | Static image only; no actual animation demonstrated | All motion specifications below are proposals, not extracted facts |

Keep the cat/chick warmth and tactile board. Do not inherit the pictured five-row board, currency bars, plus buttons, competing scenery, or illegible miniature labels. Recognizable growth and crafting stories can inform merge families; each transition should have an understandable relationship rather than an arbitrary change of object or scale.

## Palette and typography

Starting palette below is a manually chosen interpretation, not measured sampling. Adjust in the first native-scale comparison.

| Role | Color |
|---|---|
| Ink / outline / primary text | `#603C2B` |
| Cream panel | `#FFF0D6` |
| Recessed tile | `#EBCB9D` |
| Honey wood | `#BC7B43` |
| Leaf green | `#75A947` |
| Deeper foliage | `#436A3F` |
| Apple red | `#E95F4D` |
| Chick / reward yellow | `#F5C34F` |
| Quiet sky | `#A8CDD7` |

Do not use every accent in every asset. Three broad values and one focal highlight are a starting constraint. Outline should appear roughly 1.5–2.5 logical pixels at the 56-unit icon size; prove it in render rather than mechanically applying a source stroke width.

Use a rounded, readable licensed font for labels, with open counters and distinct numerals. Font family remains unselected until local font/license review. Target 18 logical units for ordinary labels, 16 for secondary text; test enlargement and narrow screens. Logo lettering may be custom vector art later; essential UI always uses native text. Do not generate text inside raster buttons or bake quantities into sprites.

## Composition and layout

Exactly four columns and four rows. Cream recessed cells on a honey-wood frame, with modest corners and one restrained frame highlight. Keep active items the strongest contrast. The request panel is the second focal region. At most three supporting silhouette groups: distant hills/sky, one side foliage group, small picnic vignette. No extra cottages, rivers, windmills, butterflies, or clouds competing in the main play area.

At a 360-unit viewport, target a 328-unit board and 71-unit cells; most object bodies occupy 52–58 units. Deliver and Undo stay outside the grid. A badge must not collide with the next cell or cover the item's defining silhouette. Tall items must fit without covering other targets.

## Production format

- Objects and buddies: illustrated RGBA PNGs, 512×512 source canvas for item masters; stable bottom-center contact anchor near normalized (0.5, 0.82). Keep a transparent safety margin and separate shadow layer where useful. Master size is for editing; optimize export after checking native scale.
- Cat/chick: layered body/eyes/mouth or small authored frame sets, with fixed proportions and contact baseline. Prefer controlled part animation over independently generated sequential frames that change identity.
- Board and panels: SVG sources or painted nine-slice skins with corner and stretch zones explicitly marked. Do not stretch wood grain across arbitrary geometry. Native Godot Control nodes handle layout and interaction.
- Simple icons: consistent SVG sources. Raster import is acceptable if checked at final scale. No emoji or mixed stock-icon styles in final UI.
- Background: one quiet 1080×1920 master, with separately movable foreground only if approved. First lab can use a plain cream field; scene detail is not a prerequisite for validating the icon family.
- Fonts and audio: local files with source and redistribution license in the manifest. Do not substitute a font without checking wrapping and outline weight.
- Godot: smooth filtering for painted art, no pixel-art snapping by default. Test import scaling, alpha edges, and atlas padding on Android. Texture compression and mipmaps are measured choices, not assumed defaults.

A 512×512 RGBA image is about 1 MiB uncompressed before mipmaps. Eight item masters alone are about 8 MiB if all are resident at that size. Keep source masters separate from export decisions and profile the full phone build before setting a final budget.

## First asset experiment — do only this next

Create one apple-pie family: apple, sliced apples, filling bowl, finished pie; one tile and board-frame sample; one selected state; one merge animation with a brief process cue. Use the approved reference as a visual input. This experiment tests whether each transformation is understandable, visually rewarding, and legible. See MERGE_CHAINS.md for stage-specific silhouettes. Cat may remain the existing reference thumbnail in private comparison notes, never shipped as a cropped sprite.

Prompt brief for an item draft: “Production 2D game icon, a plump red apple with broad leaf and short stem, slightly elevated three-quarter view, warm brown contour, rounded volume, broad upper-left highlight, soft lower-right shading, sparse surface detail. Match the supplied reference's proportions and soft painted game finish. Isolated object, transparent background, no lettering, labels, mockup frame, scenery, duplicate object, or watermark.” For higher tiers, explicitly state the preparation stage, arrangement, container, identifying material, and the style features locked from the approved seed. A prompt is not proof of conformity.

If generation is used, inspect real alpha; reject baked checkerboards, bright fringes, cropped edges, extra fruit, malformed holders, and perspective drift. Change method to authored paint/vector or controlled edits if repeated drafts fail. Do not compensate for poor art with glows.

## Animation contract

| State | Proposed treatment | Limits |
|---|---|---|
| Idle | Objects remain still; occasional cat blink/chick tilt | No simultaneous loops across the grid |
| Select | Body lifts 2–3 logical units, shadow spreads slightly | Input rectangle stays fixed |
| Move | Short eased slide into adjacent empty cell | Source/destination remain unambiguous |
| Merge | Brief squash, two bodies converge, replacement pops and settles | 220–300 ms; preserve volume; no whole-screen flash |
| Invalid | Settle back plus a clear invalid border cue | No punitive shake or loud alarm |
| Delivery | Item travels to request, buddy reacts | Keep UI readable and reward short |
| Board response | Small local rim/glow response at destination | Grid positions and hit targets never wobble |
| Reduced motion | Immediate stable swap or short fade | No overshoot, particle shower, or decorative loop |

## Approval loop and evidence

1. Primary writes the asset's silhouette, proportion, layering, palette, texture, spacing, and motion checklist before production.
2. Produce a shippable source and record dimensions, anchor, provenance, and status in the manifest.
3. Render at actual 56-unit icon size on the intended 71-unit cell in a live browser lab, plus a 2× detail view. Include an actual 4×4 board filled with all tiers, not only a large isolated beauty render.
4. Compare reference and output. Record concrete mismatches: e.g. leaf too narrow, outline too black, apple too spherical, bowl perspective too steep, highlight too shiny, silhouette unreadable at tier 3.
5. Revise source and rerender. Rejected drafts remain outside production. Do not present an unreviewed draft as an approved result.
6. After primary review passes, show the user the small asset experiment. Record approval explicitly; reference approval does not automatically approve derived sprites.
7. Integrate approved art in an isolated Godot preview, then verify on an Android phone. Review touch occlusion, native resolution, import edges, and animation stability. Production promotion requires the full check.

Acceptance is visual and technical: consistent outline/light/view; recognizable stages in silhouette; clean alpha on light/dark backgrounds; no clipping at peak squash; stable pivot; no generated text; readable labels and request counts; one visual hierarchy. A render must pass both a still and motion check. There are no production-ready assets yet.
