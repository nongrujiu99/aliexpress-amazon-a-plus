# Delivery Format

## No Regeneration In Default Delivery

Default delivery does not include automatic regeneration or suggested regeneration steps. If QA finds issues, report them as notes only. Regenerate only when the user explicitly asks.

## File Naming

Use clear ordered names:

```text
product-platform-module-01.png
product-platform-module-02.png
...
```

For Amazon A+ dual-size output, append the size to every file:

```text
product-amazon-module-01-1464x600.png
product-amazon-module-01-800x600.png
product-amazon-module-02-1464x600.png
product-amazon-module-02-800x600.png
...
```

For AliExpress vertical long-image output, append the final per-module size (width always 1200px, height varies per module, ≤2400px):

```text
product-aliexpress-module-01-1200x1800.png
product-aliexpress-module-02-1200x2200.png
product-aliexpress-module-03-1200x2400.png
...
```

For an AliExpress square main-image gallery, use `main` rather than `module` and append the fixed size:

```text
product-aliexpress-main-01-1024x1024.png
product-aliexpress-main-02-1024x1024.png
...
product-aliexpress-main-08-1024x1024.png
```

Examples:

```text
dress-amazon-module-01-1464x600.png
dress-amazon-module-01-800x600.png
makeup-spray-shopify-module-01.png
storage-box-crossborder-module-01.png
```

## Folder Naming

Prefer:

```text
<product-name>-crossborder-detail-v1
```

If saving to user desktop or project folder, create a dedicated folder and do not mix generated images with source images.

## Size Consistency

- Default output ratio: horizontal `16:9`, with `2048x1152` as the compatible exact-size default when supported, unless the platform profile requires another size.
- Default script settings: `--size 2048x1152` for exact custom-size backends, otherwise `--size 16:9 --resolution 2k`. Use the documented generation master for Amazon A+, AliExpress, and Ozon/WB mappings.
- Every image in one set must use the same ratio and resolution, except for Amazon A+ dual-size output and AliExpress vertical long-image output.
- **AliExpress main-image gallery**: deliver `6-8` separate square images, all exactly `1024x1024`. Image 01 is the clean primary listing image; images 02-08 are supporting gallery roles. Do not mix detail-page long images into this count.
- **Amazon A+ dual-size**: independently generate `1952x800` and `1024x768`, then downsample to final `1464x600` and `800x600`. Both final sizes must be present for every module.
- **AliExpress vertical long-image**: final width is `1200px`; choose a final height from `1200`, `1500`, `1800`, `2000`, `2200`, or `2400`, and use the mapped legal generation master where required.
- **Ozon/WB `900x1200`**: generate `912x1216`, then downsample proportionally to final `900x1200`.
- If a generated image has the wrong ratio, mark it in QA and regenerate only if the user asks.

## Report File (report.md)

All textual analysis, planning, and QA content must be written to a single `report.md` file in the output directory, alongside the generated images. Do not scatter the report across multiple files or only output it in the conversation.

### File Location

```text
<product-name>-crossborder-detail-v1/
├── report.md                          ← 完整文字报告（中文）
├── product-platform-module-01.png
├── product-platform-module-02.png
└── ...
```

### Report Language

- **Report body (all 21 sections)**: Chinese (中文) — for the seller/operator to read.
- **Image text (headlines, labels)**: English — for overseas buyers.
- **Module names / page roles**: Chinese label + English original, e.g. `Impact Cover（冲击封面）`.

### Report Structure (21 sections)

The `report.md` must contain these sections in order:

1. 产品图分析（Product Image Analysis）
2. 信息置信度（Information Confidence）
3. 买家需求图谱（Buyer Demand Map）
4. 需求-卖点匹配（Demand-to-Selling-Point Match）
5. 产品类型策略（Product Type Strategy）
6. 平台画像（Platform Profile）
7. 购买决策类型（Purchase Decision Type）
8. 页面策略（Page Strategy）
9. 首屏最佳方向（Best Hero Direction）
10. 模块规划（Module Plan）
11. 视觉节奏规划（Visual Rhythm Plan）
12. 参考视觉风格锁定（Reference Visual Style Lock）— 仅当提供参考图时
13. 活动风格锁定（Campaign Style Lock）
14. 风格系统锁定（Style System Lock）
15. 设计强度锁定（Design Strength Lock）
16. 产品身份与物理逻辑锁定（Product Identity & Physics Lock）
17. 逐屏任务表（Page Task Table）
18. 场景布局规划（Scene Layout Plan）
19. 生成方式（Generation Method）
20. 已生成文件（Generated Files）
21. QA说明 / 可选审查项（QA Notes / Optional Review Items）

### Report Format Rules

- Use Markdown headers (`##`, `###`) for section structure.
- Use tables for structured data (module plan, page task table, information confidence).
- Use bullet points for lists (buyer demands, selling points, locks).
- Keep each section concise but complete — this is a working document, not a marketing piece.
- Include the exact file names of generated images in section 20.
- Mark any `needs confirmation` items clearly so the seller knows what to verify.

## Response

Return:

1. Generation method and backend actually used; disclose when only prompts were produced.
2. Save directory (the output folder containing `report.md` and all images).
3. `report.md` file path and brief summary of key findings.
4. Numbered image list with purpose (inline in conversation, full details in report.md).
5. QA notes / optional review items (summary in conversation, full details in report.md).
6. Final kept count.

## Required Sections

For completed direct-generation tasks, all of the following sections must be written into `report.md` (Chinese), not just output in the conversation:

1. 产品图分析（Product Image Analysis）
2. 信息置信度（Information Confidence）
3. 买家需求图谱（Buyer Demand Map）
4. 需求-卖点匹配（Demand-to-Selling-Point Match）
5. 产品类型策略（Product Type Strategy）
6. 平台画像（Platform Profile）
7. 购买决策类型（Purchase Decision Type）
8. 页面策略（Page Strategy）
9. 首屏最佳方向（Best Hero Direction）
10. 模块规划（Module Plan）
11. 视觉节奏规划（Visual Rhythm Plan）
12. 参考视觉风格锁定（Reference Visual Style Lock，仅当提供参考图时）
13. 活动风格锁定（Campaign Style Lock）
14. 风格系统锁定（Style System Lock）
15. 设计强度锁定（Design Strength Lock）
16. 产品身份与物理逻辑锁定（Product Identity & Physics Lock）
17. 逐屏任务表（Page Task Table）
18. 场景布局规划（Scene Layout Plan）
19. 生成方式（Generation Method）
20. 已生成文件（Generated Files）
21. QA说明 / 可选审查项（QA Notes / Optional Review Items）

## Local Stitching Ban

Do not create a contact sheet. Contact sheets, preview grids, stitched boards, or any locally assembled image output are disallowed and must never be treated as generated detail-page modules.

Final delivery should list and preview the individual generated module images directly.
