# Asset review log

## Apple 01 v1

- Source: built-in image generation; original output `exec-fe362c4c-680d-4bce-8bec-c91b28c70a52.png`.
- Preserved master: `masters/apple-01-v1.png`; 1254×1254 RGBA. Original generated metadata retained by copying the file unchanged.
- User explicitly approved its appearance: “hell yeah this is good.” It is now the style anchor for derived chain assets.
- Defining features: rounded asymmetrical red body; broad green leaf; short chunky stem; dark warm-brown silhouette; soft upper-left highlight; burgundy lower-right shading; minimal internal detail.
- Compared with the initial reference: larger stem and leaf, somewhat stronger highlights. User approval establishes these as accepted seed characteristics, not reasons to redesign the asset.
- Real alpha channel confirmed. Native-scale edge, animation, browser, and eventual Android checks are separate from visual approval.
- Browser review: inspected on 71-pixel cells in a fixed 4×4 board. Silhouette, leaf, and highlight remain distinct; no visible rectangular background. Majority of painted pixels have alpha 252–253 rather than full 255; slight residual low-alpha pixels exist in the outer canvas. This is a source master, not a normalized export. Keep it unchanged; validate/normalize export edges before Godot production integration.
- Status: visual seed approved; still-image browser check passed; Android and final animation checks pending; not integrated into a game.

Generation mode: built-in image tool. Prompt: create a single centered transparent red-apple game sprite matching the original reference's rounded silhouette, broad leaf, warm brown contour, top-left highlights, soft shading, and 56-pixel readability; no face, text, scene, or exterior shadow.

## Work order confirmed by user

Finish asset graphics and their iterations first. Then make the Godot game, perform primary review, and present it for user review. Current browser files are an isolated art inspection lab, not game implementation. Do not build the Android gameplay slice ahead of art approval.

## Derived apple stages v1

- Slices: `lab/apple-02-v1.png`, generated using approved apple reference. Three wedges dominate a slim wooden board. Brown outline, red peel, and cream flesh preserve family identity. The board has more surface detail than requested, but the detail is subordinate at native size.
- Filling: `lab/apple-03-v1.png`, generated using approved apple reference. Chunky red-edged apples in a cream bowl with golden filling. It reads as a prepared fruit stage; no utensils or competing props. The draft has four prominent chunks rather than the prompt's proposed five or six; quantity is not a gameplay requirement and fewer chunks improve readability.
- Pie: `lab/apple-04-v1.png`, generated using approved apple reference. Broad golden lattice and scalloped edge create a distinct final shape. Slightly steeper top view than the bowl; assess together at native size. Pastry has a few more lattice subdivisions than requested; retain only if still readable.
- All are 1254×1254 RGBA with real transparent pixels. `lab/alpha-report.json` records dimensions and significant-alpha bounds. Original generated files copied unchanged, preserving metadata.
- User explicitly approved pie v1: “This looks hell great,” attached to the pie. Preserved unchanged in `masters/apple-04-v1.png`. Slices and filling still await explicit user approval.
- Whole-chain browser still review passed on 71-pixel cells with object sizes normalized visually to approximately 56 pixels. Four distinct silhouettes remain readable: upright apple, fanned wedges, round bowl, lattice pie. The pie's steeper view does not break family cohesion at target size; broad lattice reads clearly. Bowl highlights and board grain do not overpower the forms. This is a still-image pass, not a completed animation or Android pass.
- Drafts stay in the lab pending user approval. Do not promote them merely because the apple seed was approved.

Prompt records (built-in tool):

1. Slices: three chunky cream wedges with red peel on a small honey-brown board; match approved apple's outline/light/view; minimal detail; no knife; transparent centered sprite readable at 56 pixels.
2. Filling: cream bowl with large red-edged apple pieces in golden filling; same warm outline and painted finish; no spoon/garnish; transparent 56-pixel-readable silhouette. First call failed with a connection error; successful retry used the same brief and approved apple reference.
3. Pie: whole round pie, thick golden scalloped crust, broad lattice over red-gold filling, slim cream dish; match approved apple; no steam/decoration/text; transparent centered sprite readable at 56 pixels.
