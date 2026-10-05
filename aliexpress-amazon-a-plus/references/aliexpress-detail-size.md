# AliExpress Detail Size Specification

Use this file when the user requests the skill's AliExpress vertical-detail preset. It defines a working canvas system, per-module height selection, composition guidance, prompt structure, and QA checks. A current user-provided AliExpress specification overrides this preset.

## Vertical Working Preset

Under this preset, use this format for every planned module:

| Parameter | Value | Rule |
| --- | --- | --- |
| Width | `1200px` | Fixed for every module in the set |
| Final height per screen | `≤ 2400px` | Each delivered image must not exceed 2400px under this preset |
| Final height range | `1200px` – `2400px` | Choose per module based on content density |
| Orientation | Vertical long image | Not horizontal 16:9 |
| Final aspect ratio range | `1:1` to `1:2` | Varies by module |

**Preset rules**:
- Keep width at `1200px` unless the user supplies another current platform specification.
- Keep each final image at or below `2400px` under this preset. Split denser content into two modules instead of exceeding the preset height.
- Use a vertical rather than horizontal `16:9` composition under this preset.
- Each module may have a different height. The set does not require uniform height — only uniform width (1200px).

## Height Selection By Content Density

Choose each module's final height based on its page role and visual mechanism:

| Module type | Recommended size | Rationale |
| --- | --- | --- |
| Impact cover / hero poster | `1200x1500` or `1200x1800` | Single strong focal point, moderate copy |
| Core demand / single selling point | `1200x1500` or `1200x1800` | One demand + one proof, compact |
| Scene proof / lifestyle | `1200x1800` or `1200x2000` | Immersive scene needs vertical depth |
| Detail evidence / material macro | `1200x1500` or `1200x1800` | Close-up crop, focused |
| Objection handling / comparison | `1200x2000` or `1200x2200` | Before/after or side-by-side needs space |
| Use process / step flow | `1200x2000` or `1200x2400` | Multiple steps stack vertically |
| Info confirmation / SKU / specs / package | `1200x2200` or `1200x2400` | Dense information, multiple SKUs or parameters |
| Closing summary | `1200x1500` or `1200x1800` | Concise recap, clean finish |

**Selection principle**: more visual elements, more steps, more SKUs, or denser information → taller image (up to 2400px). Single focal point, compact hero, or concise summary → shorter image (1200–1800px). When in doubt, use `1200x1800` as the default middle ground.

## Compatible Generation Masters

Use these exact mappings when the backend supports custom dimensions:

| Final delivery size | Generation master | Handling |
| --- | --- | --- |
| `1200x1200` | `1200x1200` | Direct output |
| `1200x1500` | `1216x1520` | Equal-ratio downsample |
| `1200x1800` | `1216x1824` | Equal-ratio downsample |
| `1200x2000` | `1200x2000` | Direct output |
| `1200x2200` | `1248x2288` | Equal-ratio downsample |
| `1200x2400` | `1200x2400` | Direct output |

The generation master and final size share the exact same aspect ratio. Do not crop, stretch, letterbox, or upscale. Record both dimensions in `report.md`.

## Vertical Long-Image Composition Guide

AliExpress vertical long-images are mobile-first. Composition must work in a narrow 1200px-wide vertical canvas.

### Recommended layouts

- **Top headline + middle product hero + bottom labels**: classic vertical hierarchy, works for cover and core demand pages.
- **Stacked sections**: divide the vertical canvas into 2–3 horizontal bands (e.g. top scene, middle detail, bottom info card). Good for process and comparison pages.
- **Full-bleed scene with overlay copy**: immersive lifestyle or scene proof. Product and scene fill the canvas; headline and labels sit in readable zones.
- **Centered product with surrounding annotations**: detail or macro pages. Product in center, callout lines and labels around it.
- **Vertical step flow**: numbered steps stacked top to bottom, each with its own visual and short label. Good for use process.
- **SKU grid / parameter table**: compact grid of color options, sizes, or package contents. Good for info confirmation.

### Composition rules

- Keep the product visible and recognizable. In a vertical canvas, the product should occupy 40–65% of the canvas height for hero and scene pages.
- Place headline in the top 15–25% of the canvas. Keep it short (3–8 English words).
- Place selling labels in the bottom 15–25% or in side margins. Do not let labels overlap the product's key features.
- Use vertical depth: foreground / midground / background layers work well in tall canvases.
- For dense pages (process, SKU, comparison), use clear visual separation between sections — dividers, color bands, or card boundaries.
- Do not cram too many elements into a single screen. If content exceeds comfortable spacing, split into two modules or increase final height up to 2400px.

### What to avoid

- Horizontal left-right split layouts that waste vertical space.
- Tiny text that is unreadable on mobile.
- Product floating in a large empty vertical canvas.
- Reusing the same centered-product + top-title + bottom-label layout on every page.
- Exceeding 2400px final height on a single image.

## Prompt Structure

Every AliExpress prompt must start with its exact generation-master and final-delivery declaration:

```text
[generation-master-width]x[generation-master-height] generation master for a final 1200x<height> AliExpress vertical long detail image, final width fixed 1200px, final single-screen height ≤2400px.
```

Replace the placeholders with the mapped pair, for example `1216x1824 generation master for a final 1200x1800 AliExpress vertical long detail image` or direct `1200x2000 generation master and final output`.

The full prompt structure:

```text
[generation master] for a final 1200x<height> AliExpress vertical long detail image, final width fixed 1200px, final single-screen height ≤2400px.

[Campaign Style Lock: use Temu / AliExpress Direct Value]
[Reference Visual Style Lock, when references are provided]
[Style System Lock]
[Design Strength Lock]
[Visual Quality Lock]
[Product Identity & Physics Lock]
[Optional Model Identity Lock]

Use the uploaded product image only as a product-identity reference, not as a composition reference.
Preserve the visible product appearance, color, packaging, structure, material look, SKU, logo/nameplate placement, pattern placement, proportions, and key details.
Do not replicate a white-background reference as a white-background single-product image. Change the composition, angle, crop, scene or detail-page layout, and include the required ecommerce headline, selling labels, and visual proof.

Create module [NN] of [TOTAL] for an AliExpress vertical long detail page.
Platform profile: AliExpress (速卖通) direct-value vertical long-image.
Purchase decision type: [impulse-driven / efficacy-driven / trust-driven / aesthetic-driven / parameter-driven / gift-driven].
Page strategy: [main purchase resistance and conversion angle].
Page role: [impact cover / core demand / scene proof / detail evidence / objection handling / use process / info confirmation / closing summary].
Module plan: [module title direction, buyer question, core information, visual suggestion, copy suggestion, required proof, risk reminder].
Buyer demand: [one buyer question or concern this image answers].
Matched selling point: [one selling point that answers the demand].
Information confidence: [confirmed / reasonable inference / needs confirmation].
Product type strategy: [standard-functional / aesthetic-design / consumable / gift-emotional-value / mixed].

Headline text: "[short natural English headline]"
Support labels: "[label 1]" / "[label 2]" / "[label 3]"
Composition and subject scale: [vertical hierarchy / stacked sections / full-bleed scene / centered product with annotations / vertical step flow / SKU grid], product or key material detail uses a clear scale appropriate for this module and the 1200px-wide vertical canvas.
Visual proof: [what the image should show, not just say].
Scene/information structure: [top headline / middle hero / bottom labels, or stacked vertical sections, or vertical step flow].
Difference from previous module: [change layout structure, subject scale, title position, product angle, visual device, or information density].
Required elements: [must appear].
Forbidden elements: [must not appear].

Avoid: fake logo, watermark, fake certification, fake reviews, fake ratings, fake platform badge, unsupported claims, dense tiny text, distorted product, copied competitor layout, horizontal 16:9 format, final width other than 1200px, final height exceeding 2400px, small floating product on a large empty vertical canvas, gold badge circles, beige icon rows, fake luxury frames.
```

## File Naming And Directory

File naming includes the per-module size:

```text
product-aliexpress-module-01-1200x1800.png
product-aliexpress-module-02-1200x2200.png
product-aliexpress-module-03-1200x2400.png
...
```

Directory:

```text
<product-name>-aliexpress-detail-v1/
  module-01-1200x1800.png
  module-02-1200x2200.png
  ...
```

## Generation Workflow

1. Plan the module set and assign each module a final size based on its content density.
2. Select the corresponding generation master from the mapping table.
3. Write one standalone prompt per module, stating both its generation master and final delivery size.
4. Read [fallback-generation.md](fallback-generation.md) and use an available, authorized backend. When the chosen helper supports exact custom sizes, pass the mapped generation-master size.
5. For mapped masters, downsample proportionally to the final size. Do not crop, stretch, letterbox, or upscale.
6. If the selected backend cannot return the master dimensions, disclose the actual size rather than claiming compliant output.
7. Verify each final image: width exactly 1200px, height is one of the planned final heights and ≤2400px, vertical orientation, content matches the module plan.
8. If a module fails size or content QA during the active generation workflow, regenerate only that module.

## QA Checklist For AliExpress

- [ ] Every image width is exactly `1200px`.
- [ ] Every final height is one of `1200`, `1500`, `1800`, `2000`, `2200`, or `2400px` and does not exceed `2400px`.
- [ ] Every non-direct final records its correct generation master: `1216x1520`, `1216x1824`, or `1248x2288`.
- [ ] Every image is vertical (height > width), not horizontal 16:9.
- [ ] Each module's height matches its planned content density (dense pages taller, compact pages shorter).
- [ ] Product is recognizable and consistent with the reference image.
- [ ] Headline and labels are readable on mobile (not too small, not overlapping key product features).
- [ ] At least 5 different layout structures across the set (not all centered-product + top-title + bottom-label).
- [ ] No fake logo, certification, ratings, reviews, platform badges, or unsupported claims.
- [ ] No image was produced by cropping or stretching a horizontal image.
- [ ] File names include the per-module size suffix (e.g. `-1200x1800`).

## Temu vs AliExpress Clarification

- **Temu**: shares the same direct-value visual profile but does **not** mandate the 1200px vertical long-image format. When the user says "Temu" only, use the default horizontal 16:9 unless the user specifies a size.
- **AliExpress / 速卖通**: use the 1200px-wide vertical working preset (final height ≤2400px) when the user does not provide a newer platform specification or another requested size.
