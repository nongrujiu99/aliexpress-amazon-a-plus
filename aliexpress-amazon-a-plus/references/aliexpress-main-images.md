# AliExpress Main-Image Gallery Pack

Use this file when the user requests AliExpress main images, listing images, product gallery images, or a square main-image pack. This is separate from the vertical detail-page system in [aliexpress-detail-size.md](aliexpress-detail-size.md).

## Working Preset

| Parameter | Value | Rule |
| --- | --- | --- |
| Count | `6-8` images | Follow the user's count; otherwise choose from supported visual evidence |
| Canvas | `1024x1024` | Exact square output for every image |
| Aspect ratio | `1:1` | Do not mix portrait or landscape images into the pack |
| Output | Individual image files | Never substitute a contact sheet or stitched board |

Treat this as the skill's user-requested working preset, not a universal official rule for every AliExpress region or category. A current category-specific Seller Center requirement supplied by the user overrides it.

## Count Selection

- Use six images when the supplied product evidence supports only the essential listing sequence.
- Use seven or eight only when each additional image has distinct supported proof, such as another necessary angle, a verified detail, a realistic scale cue, a confirmed variant, or confirmed package contents.
- Never invent specifications, accessories, compatibility, materials, certifications, or package contents to fill the pack.

The task table row count is the generation count. Generate and deliver the planned count exactly unless a failed image cannot satisfy the request.

## Gallery Role Sequence

Use the first six roles by default. Add roles 07 and 08 only when the evidence supports them or the user requests the larger count.

| Image | Role | Required visual job | Copy rule |
| --- | --- | --- | --- |
| 01 | Primary listing image | Show the complete, recognizable product clearly on a clean white or light solid background | No promotional headline, selling labels, price, discount, badge, watermark, contact, URL, or QR code |
| 02 | Alternate view | Reveal a meaningful second angle, structure, opening state, or front/back relationship | Prefer text-free; use only necessary verified labels |
| 03 | Core feature proof | Show one confirmed feature through visible product detail or realistic interaction | One short headline and up to two concise labels when useful |
| 04 | Detail / material evidence | Use a close-up to show a real texture, joint, interface, finish, or construction detail | No unsupported material or performance claim |
| 05 | Scale / fit / use scene | Clarify plausible size, fit, placement, wearing, handling, or real use | Dimensions or compatibility only when confirmed |
| 06 | Purchase confirmation | Confirm visible package contents, verified variants, care, setup, or a concise buying check | Keep information mobile-readable and factual |
| 07 | Secondary scenario or objection | Answer one remaining buyer concern with a different scene or proof method | Optional; do not repeat image 03 or 05 |
| 08 | Variant / package / final check | Reduce choice uncertainty with confirmed color, SKU, package, or fit information | Optional; avoid generic closing slogans |

Reorder roles 02-08 when the product category or strongest buyer concern justifies it. Image 01 always remains the strict primary listing image.

## Composition and Variety

- Keep the same product identity, SKU, silhouette, proportions, color-area relationships, pattern placement, packaging, visible branding, and physical construction throughout the set.
- Aim for at least four composition structures and three subject scales across an eight-image pack; compress proportionally for six or seven images.
- Change the evidence method, camera angle, crop, subject scale, scene, or information structure between adjacent images.
- Do not create a pack that only swaps backgrounds, rotates the product slightly, or changes title placement.
- Keep the product clearly recognizable. For image 01, normally let the complete product occupy roughly `70-85%` of the frame while retaining clean edge clearance.
- Use white or a light solid background for image 01. Supporting images may use restrained scenes or information structures appropriate to the product and confirmed claims.

## Prompt Contract

Every prompt must start with:

```text
1024x1024 AliExpress square product gallery image, 1:1 canvas.
```

Append the common identity and physics locks, then define:

```text
Image [NN] of [TOTAL].
Gallery role: [primary listing image / alternate view / core feature proof / detail evidence / scale or use scene / purchase confirmation / optional role].
Buyer question: [one question].
Supported selling point: [one confirmed selling point or conservative visible fact].
Information confidence: [confirmed / reasonable inference / needs confirmation].
Composition and subject scale: [specific square composition].
Visual proof: [what the image visibly demonstrates].
Required elements: [must appear].
Forbidden elements: [must not appear].
Difference from previous image: [specific visual and informational change].
```

For image 01, also include:

```text
Primary listing image, clean product-only presentation, complete product visible, white or light solid background, no promotional text, no selling labels, no price, no discount badge, no watermark, no contact information, no URL, no QR code, no unrelated props.
```

For images 02-08, use short buyer-facing copy only when it materially explains supported proof. Prefer no more than one headline and two labels.

## Generation and File Naming

Generate each image independently with the smallest set of product references needed for consistency. Do not generate a grid and split it into deliverables.

Use:

```text
<product-name>-aliexpress-main-v1/
├── report.md
├── product-aliexpress-main-01-1024x1024.png
├── product-aliexpress-main-02-1024x1024.png
├── ...
└── product-aliexpress-main-08-1024x1024.png
```

Stop filenames at the planned count. If the generation backend cannot return exact `1024x1024`, disclose the actual dimensions and do not claim compliance. Regenerate within the active generation workflow when the output fails the original exact-size requirement; do not silently stretch a non-square result.

## QA Checklist

- [ ] Final count is between six and eight and matches the task table.
- [ ] Every kept file is exactly `1024x1024` and is a separate image.
- [ ] Image 01 shows the complete correct product on a clean white or light solid background.
- [ ] Image 01 contains no promotional text, labels, badges, price, discount, watermark, contact, URL, QR code, or unrelated props.
- [ ] Images 02-08 each add distinct supported information rather than repeating image 01.
- [ ] Product identity, color, structure, SKU, packaging, and visible branding remain consistent.
- [ ] All specifications, dimensions, materials, variants, compatibility, and package contents shown are confirmed.
- [ ] Text is concise and readable; no image contains dense tiny copy.
- [ ] No fake platform badge, certification, rating, review, test result, sales claim, or exaggerated before/after proof appears.
- [ ] No contact sheet, stitched preview grid, or cropped multi-image board is delivered as the pack.
