---
name: aliexpress-amazon-a-plus
description: "Plan and generate truthful, platform-fit cross-border ecommerce image sets from product photos and confirmed selling points. Use for AliExpress 6-8 image main-gallery packs and vertical detail images, Amazon A+/Premium A+, Shopify PDP modules, Temu, TikTok Shop, Ozon, or Wildberries; do not use for ordinary product copy with no visual deliverable."
---

# Cross-Border A+ Detail Images

Create finished ecommerce detail-page modules, not merely strategy or prompts, unless the user asks for planning or prompts only. Treat product images as identity evidence, not as a composition template.

## Document Routing

Always resolve relative links from this `SKILL.md` directory. Read only the references required by the active request, but do not skip a routed reference that governs the requested platform or output type.

- Shared planning: `buyer-demand-strategy.md`, `page-planning-strategy.md`, and `page-task-table.md`.
- Platform selection and default sizes: `platform-profiles.md`.
- AliExpress square main-image pack: `aliexpress-main-images.md`.
- AliExpress vertical detail modules: `aliexpress-detail-size.md`.
- Amazon A+/Premium A+ dual-size output: `amazon-a-plus-dual-size.md`.
- Prompt construction: `prompt-contract.md`; use `prompt-templates.md` only when an example is needed.
- Generation backend and compatible dimensions: `fallback-generation.md`.
- Output inspection and failure handling: `qa-checklist.md` and, only after a generation failure, `failure-retry.md`.
- Final filenames, folders, and report: `delivery-format.md`.

## Operating Priorities

Apply these priorities in order:

1. Follow the user's platform, dimensions, language, module count, style, brand colors, and delivery requirements.
2. Preserve product truth and platform compliance. Never invent specifications, materials, certifications, tests, reviews, ratings, sales claims, medical effects, compatibility, or brand identity.
3. Give every module one buyer question, one supported selling point, and visible proof.
4. Keep the set visually coherent while varying composition, subject scale, evidence method, and density.
5. Adapt reference style without copying exact layout, wording, logos, ratings, badges, or distinctive brand assets.

If required facts are missing, continue with visible facts and conservative inferences, label unknowns in the report, and keep them off the generated image.

## Workflow

1. Inspect the supplied product and reference images. Record visible identity anchors, physical relationships, confirmed facts, reasonable inferences, and unknowns.
2. Read [buyer-demand-strategy.md](references/buyer-demand-strategy.md), [page-planning-strategy.md](references/page-planning-strategy.md), and [page-task-table.md](references/page-task-table.md). Build a buyer-demand map, module plan, visual rhythm, and per-module task table before prompting.
3. Read [platform-profiles.md](references/platform-profiles.md) for the named platform. Treat documented sizes as working presets; a current user-provided platform specification overrides them.
4. When relevant, load only the matching conditional references:
   - Amazon A+/Premium A+: [amazon-a-plus-dual-size.md](references/amazon-a-plus-dual-size.md).
   - AliExpress main-image or product-gallery set: [aliexpress-main-images.md](references/aliexpress-main-images.md).
   - AliExpress vertical detail images: [aliexpress-detail-size.md](references/aliexpress-detail-size.md).
   - Category-specific strategy: [category-playbooks.md](references/category-playbooks.md) and, when a stronger visual direction is needed, [design-archetypes.md](references/design-archetypes.md).
   - User-supplied competitor or style references: [reference-page-analysis.md](references/reference-page-analysis.md).
5. Establish the visual and physical locks. Read [scene-layout-standard.md](references/scene-layout-standard.md), [style-system-standard.md](references/style-system-standard.md), [design-strength-system.md](references/design-strength-system.md), [visual-quality-rules.md](references/visual-quality-rules.md), and [product-consistency-physics.md](references/product-consistency-physics.md). Use [style-locks.md](references/style-locks.md) only when reusable lock wording helps.
6. Run the plan through [anti-template-check.md](references/anti-template-check.md). Revise repeated structures or weak visual proof before generation.
7. Build standalone prompts with [prompt-contract.md](references/prompt-contract.md). Read [prompt-templates.md](references/prompt-templates.md) only when an example is useful; adapt it rather than copying it mechanically.
8. Generate one image per planned module. Read [fallback-generation.md](references/fallback-generation.md) to select an authorized backend. Do not upload product images to a third-party API without the user's authorization.
9. Inspect the actual outputs using [qa-checklist.md](references/qa-checklist.md). On a generation failure, read [failure-retry.md](references/failure-retry.md); retry only within the user's requested scope and the backend's safe stopping rule.
10. Deliver the kept images and report using [delivery-format.md](references/delivery-format.md).

## Planning Defaults

- If the user gives a module count, follow it exactly. Otherwise plan eight modules and expand only when distinct, supported buyer questions justify it.
- For an AliExpress main-image or product-gallery request, plan `6-8` square images at exactly `1024x1024`. Choose the count from the available distinct, supported visual evidence; do not invent filler claims merely to reach eight.
- If no platform or dimensions are specified, use a coherent horizontal PDP set and state the chosen size. Do not present a working preset as an official platform requirement.
- For each module define: buyer question, supported selling point, confidence, page role, composition, subject scale, visual proof, short headline, up to three labels, required elements, forbidden elements, and difference from the preceding module.
- Across a normal eight-module set, aim for at least five composition structures and three subject scales. Avoid using any one structure more than twice.
- Use short, mobile-readable on-image copy in the market language requested by the user.

## Product and Claim Integrity

- Preserve silhouette, proportions, color-area relationships, material appearance, structure, packaging, SKU, visible branding, pattern placement, and plausible scale/contact/shadow/perspective.
- Keep `confirmed`, `reasonable inference`, and `needs confirmation` distinct. Only confirmed facts may become hard claims.
- A reasonable inference may describe a conservative usage fit; it must not become a specification, performance guarantee, or certification.
- Reference images may guide palette, lighting, density, hierarchy, rhythm, composition devices, card/label treatment, and atmosphere. They do not authorize copying protected or identifying elements.
- For people or wearables, define a model identity and fit lock when consistency across modules matters.

## Generation Boundaries

- Prefer the built-in image-generation capability when available. Use the bundled API scripts only when the user chooses that external backend and supplies credentials/configuration.
- Generate each delivered module as a complete image-generation result. Do not substitute a stitched contact sheet, preview grid, or locally assembled multi-screen board for individual modules.
- Local file saving, renaming, copying, and dimension checks are allowed. Do not use local compositing to fabricate a supposedly generated final module unless the user explicitly requests a separate compositing workflow.
- Equal-ratio downsampling is allowed only for a documented platform master-to-delivery mapping. The source must be an independently generated complete module with the same aspect ratio; disclose the master and final dimensions. Never crop, stretch, letterbox, upscale, or derive one platform variant from another.
- Do not overwrite existing outputs without explicit permission.
- Default QA is inspection, selection, and disclosure. Regenerate only when the user asks for a fix/replacement or when generation is still in progress and the failed result cannot satisfy the original request.

## Delivery

Keep one `report.md` beside the images. Write the operator-facing report in Chinese unless the user asks otherwise; use the requested market language for image copy. Include exact filenames, generation method, dimensions, module purposes, unsupported/unknown claims excluded, QA findings, and final kept count.

Use concise chat delivery with links to the output directory, `report.md`, and individual images when useful. The report is the detailed record.
