# Platform Profiles

Use this file when the user names a marketplace or when cross-border platform fit matters. Keep the whole set horizontal by default unless the user or platform profile specifies a vertical PDP or square product-gallery format.

## Global Default

- Default format: horizontal `2048x1152` (`16:9 / 2K`) modules, unless the platform profile (e.g. Amazon A+) specifies a different size.
- Image prompts must say: `wide 16:9 horizontal ecommerce detail module`, unless the platform profile specifies an exact pixel size.
- When the authorized external API helper supports exact custom dimensions, pass `--size 2048x1152`; otherwise pass `--size 16:9 --resolution 2k`. A user-specified size or platform mapping overrides this default.
- A single image set must keep the same ratio and resolution across every module.
- Do not mix vertical PDP images, square images, and horizontal A+ images unless the user explicitly requests mixed deliverables.
- Use English short copy by default for cross-border output unless the user asks for another language.
- User-specified size, ratio, language, or platform overrides these defaults.

## Ozon / Wildberries Vertical PDP

- Use this profile when the user mentions `Ozon`, `Озон`, `WB`, `Wildberries`, Russian marketplace, Russian copy, or a vertical size such as `900x1200`.
- Final delivery format: vertical `3:4`, commonly `900x1200`, or the exact user-specified pixel size.
- Compatible generation master for `900x1200`: `912x1216`. Generate the complete module at `912x1216`, then downsample proportionally to `900x1200`; do not crop, stretch, or upscale.
- Default language: Russian unless the user asks otherwise.
- Visual direction: polished product photography plus restrained selling information, not a dense parameter poster.
- Text density: low to medium. Use one main headline, two to three selling labels, and at most four necessary parameter items per image.
- For hardware, TV stands, brackets, mounts, electronics, and tools, prefer black product contrast, warm wood tabletop, light grey/cold blue background, realistic metal highlights, and subtle technical accents.
- Make cover, scenario, material, stability, and summary pages feel like real product photography. Reserve diagrams, measurement lines, and denser cards for VESA or installation pages only.
- Ozon/WB is not the same as Temu/AliExpress high-density infographic output. Prioritize clarity, trust, product material quality, and marketplace-ready visual taste.

Avoid:

- cheap blue-white infographic template;
- PPT card stack;
- oversized headline that dominates the canvas;
- repeated three-icon card layout;
- generic shield icons as the main design;
- fake test badge, fake certification, fake review, fake rating, Ozon/WB logo, discount badge;
- complex invented TV backs, ports, tool kits, screw counts, stress-test scenes, or unsupported proof.

Recommended eight-image rhythm:

1. Product-photography cover with 2-3 key labels.
2. Screen-size compatibility.
3. VESA compatibility, with restrained diagram.
4. Material / steel structure close-up.
5. Tabletop placement / no wall drilling.
6. Stability / base contact detail.
7. Home and office scenario.
8. Final purchase checklist.

## Amazon A+

- Most conservative platform profile.
- Use restrained claims, clear functional explanation, material/detail proof, lifestyle scene proof, and A+ module logic.
- Text density: low to medium; short English headlines and concise labels.
- Strong fit for hero banner, feature module, material/detail module, lifestyle scene, comparison, and summary.
- Avoid fake ratings, fake review snippets, fake certification badges, fake Amazon badges, unsupported comparison, strong discount language, and exaggerated performance claims.

### Dual-Size Working Preset

When the user adopts this preset, generate each planned Amazon A+ module in two sizes. A current user-provided Amazon specification overrides the preset:

| Final size | Generation master | Aspect ratio | Use case | Composition guidance |
| --- | --- | --- | --- | --- |
| `1464x600` | `1952x800` | ~2.44:1 (ultra-wide) | Premium A+ full-width module, hero banner, lifestyle scene | Wide horizontal narrative; left-right split layouts; product on one side, copy on the other; panoramic scene depth; multiple visual elements in a row |
| `800x600` | `1024x768` | 4:3 (near-square) | 4:3 working delivery preset, feature module, detail module, comparison | Centered or stacked composition; product as visual hero with copy above/below; compact scene; single focal point; vertical information hierarchy |

**Same content, independent re-composition**: both sizes must carry the same module role, buyer demand, matched selling point, visual proof, headline, and labels. However, each size must be composed from scratch for its aspect ratio. **Never** produce the 800x600 by cropping, scaling, stretching, or letterboxing the 1464x600 (or vice versa). The product identity and physics locks remain identical across both sizes; only the layout, camera distance, crop, scene framing, and text placement change.

**Prompt rule**: write two standalone prompts per module — one starting with `1952x800 generation master for a final 1464x600 Amazon A+ Premium full-width horizontal module` and one starting with `1024x768 generation master for a final 800x600 Amazon A+ 4:3 near-square module`. Both prompts share the same locks, module plan, buyer demand, selling point, and copy, but specify different composition and subject scale appropriate to each aspect ratio.

**File naming**: `product-amazon-module-01-1464x600.png` and `product-amazon-module-01-800x600.png`.

**Generation**: for each module, independently generate `1952x800` and `1024x768`, then downsample them proportionally to final `1464x600` and `800x600`. When the user chooses a compatible external API helper, pass the generation-master size. If exact dimensions are unsupported, disclose the actual output size rather than silently stretching or cropping.

Default rhythm:

1. Hero banner.
2. Core fit / function.
3. Material or structure detail.
4. Lifestyle use.
5. Objection handling or comparison.
6. Practical feature / use process.
7. Scenario grid or information confirmation.
8. Summary / choice reducer.

## Shopify / Independent Site

- More brand-driven and emotional than Amazon.
- Use stronger atmosphere, product story, lifestyle identity, collection logic, and brand-like visual system.
- Text density: medium; copy may have a stronger brand tone while staying concise.
- Strong fit for hero story, lifestyle scene, material desirability, usage imagination, bundle/collection, and closing summary.
- Avoid overloading a single image with all details, fake brand heritage, fake endorsements, and copied competitor brand language.

## Temu / AliExpress

- More direct benefit language and clearer information density.
- Emphasize concrete use value, SKU clarity, size/fit cues, package contents, quick feature proof, and scenario fit.
- Text density: medium-high but still mobile-readable.
- Use stronger visual hierarchy and obvious selling labels.
- Avoid premium-only editorial layouts that hide concrete benefits, unsupported parameter claims, fake discount badges, and excessive tiny text.

### AliExpress Main-Image Gallery Working Preset

Use this preset when the user requests AliExpress main images, listing images, product gallery images, or a `6-8` image square pack. Read [aliexpress-main-images.md](aliexpress-main-images.md) before planning or prompting.

- Deliver `6-8` individual images at exactly `1024x1024`; follow an explicit user count within that range.
- If no count is given, choose six for products with limited confirmed evidence and up to eight only when distinct supported angles, details, scenarios, variants, package contents, or buying checks justify them.
- Image 01 is the primary listing image: complete recognizable product, clean white or light solid background, no promotional copy, badges, watermarks, contacts, QR codes, or unrelated props.
- Images 02-08 are supporting gallery images, not duplicates of image 01. Use alternate views, confirmed detail proof, scale or fit cues, realistic use scenes, verified variants, or confirmed package contents.
- Keep the product identity, SKU, colors, structure, proportions, packaging, and visible branding consistent across the set.
- Treat `1024x1024` as this skill's user-requested working preset. A current category-specific Seller Center requirement supplied by the user overrides it.

**Prompt rule**: every prompt starts with `1024x1024 AliExpress square product gallery image, 1:1 canvas.` Image 01 must also state `primary listing image, clean product-only presentation, no promotional text`.

**File naming**: `product-aliexpress-main-01-1024x1024.png` through `product-aliexpress-main-08-1024x1024.png`, stopping at the planned kept count.

**Generation**: make one generation call per image. Do not create the pack as a contact sheet, crop multiple deliverables from one board, or reuse one composition with only background changes.

### AliExpress Vertical Working Preset

When the user adopts this preset, use the following vertical long-image system. A current user-provided AliExpress specification overrides it:

| Parameter | Value | Notes |
| --- | --- | --- |
| Width | `1200px` (fixed) | All modules share the same 1200px width |
| Final height per screen | `≤ 2400px` | Each delivered image height must not exceed 2400px under this preset |
| Final aspect ratio range | `1:1` to `1:2` | Height varies by module content, from 1200px up to 2400px |
| Orientation | Vertical long image | Not horizontal 16:9; this is a mobile-first vertical PDP format |

**Height selection rule**: choose the final module size from `1200x1200`, `1200x1500`, `1200x1800`, `1200x2000`, `1200x2200`, or `1200x2400`. Use the compatible generation-master mapping in [aliexpress-detail-size.md](aliexpress-detail-size.md). Never exceed `2400px` final height under this preset.

**Prompt rule**: every AliExpress prompt must state both the compatible generation master and final delivery size, e.g. `1216x1824 generation master for a final 1200x1800 AliExpress vertical long detail image`. Do not use `wide 16:9 horizontal` for AliExpress.

**File naming**: `product-aliexpress-module-01-1200x1800.png`, `product-aliexpress-module-02-1200x2200.png`, etc. The height suffix reflects each module's actual generated height.

**Generation**: call the image generator once per module with its mapped generation-master size. Downsample only when the mapping requires it; direct sizes remain unchanged. Do not force all modules to the same height.

**Temu note**: Temu shares the same direct-value visual profile but does not inherit this 1200px-wide vertical preset. When the user says "Temu" only, use the general horizontal working preset unless the user specifies a size. For AliExpress, use the vertical preset when no newer user-supplied specification is available.

## TikTok Shop

- Fast visual hook, lifestyle scene, social sharing feeling, and immediate benefit recognition.
- Text density: low; punchy benefit labels.
- Strong fit for UGC-like use moment, hands-on scene, before/after problem framing, fast summary, and emotional ownership.
- Avoid complex comparison tables, dense specs, slow brand-story layouts, and fake influencer/review claims.

## Platform Selection Rule

If the user provides a platform, adapt page rhythm, density, text tone, image orientation, and compliance to that platform. If no platform is specified, use a general cross-border PDP/A+ profile: moderately compliant, visually polished, concise English copy, and mixed proof/scene/detail modules.
