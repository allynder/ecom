# Chinook Seedery — product image naming & folder structure

Source: Figma file `renaming` (7yl9DrcR8E6vo2Lz8jY5NI), page "Page 1".
Target: Shopify product galleries on chinookseedery.com.

## Naming convention

```
[product]_[variant]_[NN]-[slot].png
```

| Part      | Values | Notes |
|-----------|--------|-------|
| product   | `original`, `hatch-chile`, `jalapeno-ranch`, `lemon-pepper`, `hello-hot-honey`, `cinnamon-toast`, `smokehouse-bbq`, `dill-pickle`, `parmesan-pepper`, `variety-pack`, `build-your-own`, `big-bucket` | Matches the Shopify product handles/titles. `parmesan-pepper` (Shopify handle) instead of the Figma row name `parmesan-and-pepper`. |
| variant   | `4oz-case` (Shopify "Full Size"), `1.5oz-case` (Shopify "Single Serve"); for the bucket: `original`, `camo`, `zilla` | Same `[product]_[variant]_` prefix the two bucket heroes already on the site use (`big-bucket_original_hero.png`). |
| NN-slot   | see slot tables below | The two-digit number fixes the gallery order when files are bulk-uploaded to Shopify (the picker sorts by name). |

Example: `lemon-pepper_4oz-case_01-hero.png`

All lowercase. Hyphens inside a part, underscores between parts, so a filename always splits into exactly three pieces.

## Folder structure

Figma turns `/` in a layer name into folders on export, so every exportable layer is renamed to its full path, e.g.
`chinook-seedery/lemon-pepper/4oz-case/lemon-pepper_4oz-case_01-hero`. One "Export all" (File → Export, Cmd/Ctrl+Shift+E) then produces this tree:

```
chinook-seedery/
├── original/
│   ├── 4oz-case/      (8 images)
│   └── 1.5oz-case/    (8 images)
├── hatch-chile/        4oz-case, 1.5oz-case
├── jalapeno-ranch/     4oz-case, 1.5oz-case
├── lemon-pepper/       4oz-case, 1.5oz-case
├── hello-hot-honey/    4oz-case, 1.5oz-case
├── cinnamon-toast/     4oz-case, 1.5oz-case
├── smokehouse-bbq/     4oz-case, 1.5oz-case
├── dill-pickle/        4oz-case, 1.5oz-case
├── parmesan-pepper/    4oz-case, 1.5oz-case
├── variety-pack/
│   ├── 4oz-case/      (6 images)
│   └── 1.5oz-case/    (7 images)
├── build-your-own/
│   ├── 4oz-case/      (6 images)
│   └── 1.5oz-case/    (7 images)
├── big-bucket/
│   ├── original/      (9 images)
│   ├── camo/          (9 images)
│   └── zilla/         (9 images)
└── shared/            social-proof, available-nationwide, sodium-callout
```

One folder per Shopify product, one subfolder per variant. Uploading a product gallery = open the product folder and select both subfolders. Total: 200 images.

## Slots

### Flavor cases (9 flavors × 4oz + 1.5oz = 18 galleries, 8 images each)

| NN-slot               | Figma layer today                | Content |
|-----------------------|----------------------------------|---------|
| `01-hero`             | 01 - Plain Hero Shot             | Case box + bag, "12 PACK" / "36 PACK" |
| `02-whats-included`   | 02 - Whats Included              | "Your Seed Stash, Fully Stocked" |
| `03-flavor`           | 03 - Flavor Description          | Flavor name + tagline, bag with ingredients |
| `04-nutrients`        | 04 - Health Callout - Nutrients  | "Giant Sunflower Seeds Packed With Flavor" (protein / sugar / calories) |
| `05-benefits`         | 05 - Product Benefits            | "Bigger Seeds, Better Quality, Best Flavor" |
| `06-nutrition-facts`  | 09 - Nutrition Facts             | Nutrition label |
| `07-bag-front`        | `*-case-wholesale_02/03`, `single-serve-sampler-pack_05` | Single bag, front, plain background |
| `08-bag-sizes`        | `*-case-wholesale_01`, `Frame 2085663151` | 4oz bag + 1.5oz bag side by side |

### Variety Pack and Build Your Own (4oz + 1.5oz)

Same slots 01–06. The 1.5oz galleries also have `07-bags-fan` (the nine 1.5oz bags fanned out). No bag-front / bag-sizes shots exist for these.

### Big Bucket (original / camo / zilla, 9 images each)

| NN-slot               | Figma layer today               | Content |
|-----------------------|---------------------------------|---------|
| `01-hero`             | big-bucket_*_hero               | Bucket with bags |
| `02-whats-included`   | big-bucket_*_benefits-1         | "Stock Up For The Season", 72 × 1.5oz + bucket |
| `03-built-to-last`    | big-bucket_*_benefits-2         | "Built To Last", rope handle / lid callouts |
| `04-benefits`         | big-bucket_*_benefits-3         | "Bigger Seeds, Better Quality, Best Flavor" |
| `05-bucket-angle`     | (AI prompt as layer name)       | Bucket, slight angle, plain background |
| `06-bucket-front`     | Bucket 1 2 / (prompt)           | Bucket straight on |
| `07-rope-detail`      | Bucket 1 1 / (prompt)           | Rope handle close-up |
| `08-lid-top`          | (prompt)                        | Lid, top-down |
| `09-bucket-with-lid`  | (prompt) / Frame 2085663238 1   | Bucket with lid leaning on it |

### Shared

`shared/social-proof.png`, `shared/available-nationwide.png`, `shared/sodium-callout.png` — not tied to one product.

## Export settings

Every one of the 200 layers gets a single export setting: **PNG @1x = 2048 × 2048 px** (Shopify's recommended square size, and the size the two bucket heroes already on the site were uploaded at). Today the layers are a mix of JPG @2x (4096 px), PNG @1x and no setting at all; 17 inner layers (logos, bag cut-outs) also carry stray export settings and would pollute "Export all", so those get cleared.

## Things fixed along the way

- Row `original-case-1.5oz` exists twice; the second one (node 1:13509) is actually Hatch Chile → renamed `hatch-chile-case-1.5oz`.
- `cinnamon-toast-case-4oz` has its 8 images nested one level deeper (inside "Frame 2085663292") than every other row; the script addresses them by node id, so no manual re-nesting is needed.
- The 04/05 numbering follows the layer names (04 = nutrients, 05 = benefits), which is also the on-canvas order in the Variety Pack / Build Your Own rows. The flavor rows have them swapped on canvas; the numbering wins.
- The gap 06–08 in the old numbering (nutrition facts was "09") is closed; slots are now contiguous.

## Status

**Applied to the Figma file on 2026-09-29.** All 200 layers renamed, PNG @1x export settings set, 17 stray export settings cleared, row 1:13509 renamed to `hatch-chile-case-1.5oz`. Verified afterwards: exactly 200 layers carry export settings, all names unique, all under `chinook-seedery/`.

### To export

1. Open the file in Figma, File → Export (Cmd/Ctrl+Shift+E).
2. The dialog lists the 200 layers. Click "Export".
3. Figma downloads a zip whose folders match the tree above.

## Decisions taken (confirmed before running)

1. Slot names and the 04 (nutrients) / 05 (benefits) order.
2. Folder nesting `product/variant/` (vs. flat `product-variant/`).
3. `1.5oz-case` keeps the dot. Shopify accepts it; `1-5oz-case` is the alternative if you prefer no dots in URLs.
4. PNG @1x 2048 px (vs. JPG, which is roughly 5–10× smaller per file).
5. Zilla bucket is not a variant on the live site yet; it is included in the export regardless.

All five went through as proposed.

## Files

- `figma-image-map.csv` — all 200 images: folder, file, product, variant, slot, Figma node id, old layer name, new layer name.
- `figma-rename-script.js` — the Plugin API script that applies the renames and export settings (run through the Figma MCP `use_figma` tool). Idempotent; re-running it is safe.
