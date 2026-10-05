# Amazon A+ Dual-Size Recomposition

Use this file when the user requests the skill's Amazon A+ dual-size preset. It governs independent re-composition for the two requested canvases. A current user-provided Amazon specification overrides this preset.

## Dual-Size Working Preset

Under this preset, independently generate each planned module on two compatible masters, then downsample to the two final delivery sizes:

| Final delivery size | Generation master | Aspect ratio | Amazon A+ module type |
| --- | --- | --- | --- |
| `1464x600` | `1952x800` | ~2.44:1 (ultra-wide) | Premium A+ full-width module, hero banner, lifestyle scene, brand story |
| `800x600` | `1024x768` | 4:3 (near-square) | 4:3 working delivery preset, feature module, detail module, comparison, info card |

Unless the user selects different Amazon modules or sizes, apply both sizes to every planned module. A set of 8 modules therefore produces 16 images.

## Same Content, Independent Re-Composition

Both images of one module must carry identical:

- module role and page number;
- buyer demand and matched selling point;
- information confidence level;
- headline text and support labels;
- product identity and physics locks;
- campaign style lock, style system lock, design strength lock, and visual quality lock.

But each image must be composed from scratch for its own aspect ratio. The following must differ between the two sizes:

- layout structure (left-right split vs. centered/stacked);
- camera distance and crop (wide panoramic vs. compact medium);
- subject scale and placement;
- scene framing and depth;
- text placement (side column vs. top/bottom band);
- number and arrangement of visual elements;
- negative space distribution.

### Forbidden: Simple Crop / Scale / Stretch

Never produce one size from the other by:

- cropping the 1464x600 to 800x600 (or vice versa);
- scaling or resizing one image to the other dimension;
- stretching or squashing the aspect ratio;
- letterboxing or pillarboxing with empty bars;
- reusing the same prompt with only the size field changed.

Each size requires its own standalone prompt with composition instructions tailored to that aspect ratio.

Permitted master conversion: downsample `1952x800` to `1464x600`, and independently downsample `1024x768` to `800x600`. Each mapping preserves its exact aspect ratio. This does not authorize converting either final variant into the other.

## 1464x600 Composition Guide (Ultra-Wide)

The 1464x600 canvas is ~2.44:1, significantly wider than 16:9. Use the horizontal space deliberately.

Recommended layout patterns:

- **Left-right split**: product on one third, headline + labels on the other two thirds, with a visual divider or scene transition.
- **Panoramic scene**: product placed in a wide lifestyle environment with foreground / midground / background depth; copy in a clean side column.
- **Horizontal narrative**: three visual zones in a row (problem → product → benefit), with the product as the central anchor.
- **Full-width hero**: product dominating center with generous side whitespace, headline as a horizontal band above or below.
- **Comparison strip**: before/after or feature comparison laid out horizontally.

Avoid:

- centered product with empty left and right space;
- a single small subject floating in the wide canvas;
- vertical text stacks that leave the horizontal space unused;
- dense text blocks that read poorly across the ultra-wide width.

## 800x600 Composition Guide (4:3 Near-Square)

The 800x600 canvas is 4:3, close to square. Use compact, focused compositions.

Recommended layout patterns:

- **Centered hero**: product as the dominant visual center, headline above, labels below in a clean band.
- **Top-bottom stack**: visual proof in the upper 60%, information card or labels in the lower 40%.
- **Compact scene**: product in a tight lifestyle close-up with shallow depth, copy in a corner or side margin.
- **Detail macro**: material or structure close-up filling the canvas, with minimal overlay labels.
- **Single focal point**: one clear visual mechanism per image (product hero, material macro, installation step, VESA card, stability detail, or checklist).

Avoid:

- trying to fit a wide panoramic scene into the near-square canvas;
- left-right splits that feel cramped;
- multiple competing visual elements;
- text that dominates the product area.

## Dual-Size Prompt Structure

For each Amazon A+ module, write TWO standalone prompts. Both share the same lock block and module plan, but differ in the canvas declaration and composition section.

### Shared block (identical in both prompts)

```text
[Campaign Style Lock: Amazon A+ Clean Proof]
[Style System Lock]
[Design Strength Lock]
[Visual Quality Lock]
[Product Identity & Physics Lock]
[Reference Visual Style Lock, when references are provided]

Use the uploaded product image only as a product-identity reference, not as a composition reference.
Preserve the visible product appearance, color, packaging, structure, material look, SKU, logo/nameplate placement, pattern placement, proportions, and key details.
Do not replicate a white-background reference as a white-background single-product image.

Module [NN] of [TOTAL] for Amazon A+.
Page role: [impact cover / core demand / scene proof / detail evidence / objection handling / use process / info confirmation / closing summary].
Purchase decision type: [type].
Page strategy: [main purchase resistance and conversion angle].
Buyer demand: [one buyer question].
Matched selling point: [one selling point].
Information confidence: [confirmed / reasonable inference / needs confirmation].

Headline text: "[short English headline]"
Support labels: "[label 1]" / "[label 2]" / "[label 3]"
Required elements: [must appear].
Forbidden elements: [must not appear].
```

### 1464x600-specific opening and composition

```text
1952x800 generation master for a final 1464x600 Amazon A+ Premium full-width ultra-wide horizontal module.

Composition: ultra-wide 2.44:1 canvas; [left-right split / panoramic scene / horizontal narrative / full-width hero / comparison strip]; product placed in [zone]; headline and labels in [side column / horizontal band]; [foreground/midground/background depth description]; purposeful use of horizontal space, no centered floating product.
Subject scale: [full product / partial crop / human-object scale / deep scene].
Visual proof: [what the wide image shows].
Difference from 800x600 version: this version uses the ultra-wide canvas for [horizontal narrative / panoramic depth / side-by-side layout], while the 800x600 version uses a compact centered composition.
```

### 800x600-specific opening and composition

```text
1024x768 generation master for a final 800x600 Amazon A+ 4:3 near-square composition.

Composition: compact 4:3 canvas; [centered hero / top-bottom stack / compact scene / detail macro / single focal point]; product as dominant visual center; headline above and labels below in clean bands, or copy in corner margin; single clear visual mechanism; no cramped left-right split.
Subject scale: [full product / partial crop / local macro / information card].
Visual proof: [what the compact image shows].
Difference from 1464x600 version: this version uses the near-square canvas for [focused hero / tight detail / stacked info], while the 1464x600 version uses an ultra-wide horizontal composition.
```

### Shared negative constraints (append to both prompts)

```text
Avoid: fake logo, watermark, fake certification, fake reviews, fake ratings, fake Amazon badge, unsupported claims, dense tiny text, distorted product, copied competitor layout, small floating product on empty background, gold badge circles, cheap blue-white infographic template, PPT card stack.
Do not crop, scale, stretch, or letterbox the other size to produce this image. Compose independently for this aspect ratio.
```

## File Naming and Directory

```text
<product-name>-amazon-a-plus-v1/
├── module-01-1464x600.png
├── module-01-800x600.png
├── module-02-1464x600.png
├── module-02-800x600.png
├── ...
└── module-08-800x600.png
```

Prompt files follow the same pattern:

```text
prompts/
├── module-01-1464x600.txt
├── module-01-800x600.txt
├── module-02-1464x600.txt
├── module-02-800x600.txt
└── ...
```

## Generation Workflow

For each module:

1. Write the shared lock block and module plan once.
2. Write the `1952x800` master prompt for final `1464x600`, with ultra-wide composition instructions.
3. Write the `1024x768` master prompt for final `800x600`, with 4:3 composition instructions.
4. Read [fallback-generation.md](fallback-generation.md) and generate the ultra-wide variant at `1952x800` with an available, authorized backend.
5. Generate the 4:3 variant separately at `1024x768` with its independently composed prompt.
6. Downsample proportionally to final `1464x600` and `800x600`; do not crop, stretch, letterbox, or upscale.
7. If the backend cannot return the mapped master dimensions, disclose the actual size and do not claim compliant final delivery.
8. Save both final images with final-size-suffixed filenames and record master-to-final mappings in `report.md`.

## QA Check for Dual-Size Output

After generation, verify for every module:

- Both `1464x600` and `800x600` images exist and are non-empty.
- The `1464x600` final came only from its `1952x800` master, and the `800x600` final came only from its independently generated `1024x768` master.
- Both images carry the same headline, labels, module role, and selling point.
- The 1464x600 image uses the ultra-wide canvas intentionally (not a centered product with empty sides).
- The 800x600 image uses a compact composition (not a cropped or squashed version of the 1464x600).
- Product identity is consistent across both sizes (same color, structure, logo placement, material).
- Neither image contains fake Amazon badges, certifications, ratings, or reviews.
- Text is readable and not overlapping the product in either size.
- No image was produced by cropping or scaling the other.

If either size fails the check, regenerate only that size with a revised prompt — do not regenerate both unless both fail.
