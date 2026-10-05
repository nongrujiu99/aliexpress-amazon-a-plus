# Generation Backends and Fallbacks

Read this before generating final images. Backend choice must follow the user's request, available tools, privacy expectations, and authorization.

## Priority

1. Use the built-in image-generation capability when it is available and can create or edit the requested images.
2. Use `scripts/generate_image.py` or `scripts/generate_batch.py` only when the user chooses an external OpenAI-compatible image API and provides its endpoint, model, and credentials.
3. If no authorized backend is available, deliver the completed plan and prompt pack, explain what is missing, and do not claim that images were generated.

Product and reference images may contain confidential designs, logos, packaging, or personal data. Do not upload them to a third-party endpoint merely because configuration is present. Confirm that the user's request authorizes that backend or ask before the upload.

## Built-In Generation

- Generate one module per call with the module's full standalone prompt and the smallest set of reference images needed to preserve product identity.
- Request the planned aspect ratio or size supported by the tool. If the backend cannot produce an exact platform pixel size, disclose the generated dimensions and do not silently stretch or crop the result into compliance.
- Prefer dimensions whose width and height are multiples of 16 when the backend supports custom sizes. Use the documented platform generation master when the delivery size is not directly supported.
- A generation master may be downsampled only to its documented same-ratio final size. Record both sizes in `report.md`; never crop, stretch, letterbox, upscale, or reuse one platform variant to manufacture another.
- Save selected outputs in the user-facing output directory and inspect the actual images before delivery.

## Optional External API Helper

The helper supports text-only generation and reference-image editing against compatible endpoints. It reads configuration from environment variables or an explicitly selected `.env` file.

Preferred variables:

```dotenv
IMG_BASE_URL=https://your-provider.example/v1
IMG_MODEL=your-image-model
IMG_API_KEY=your-api-key
IMG_API_MODE=sync
```

Equivalent `OPENAI_IMAGE_GENERATIONS_URL`, `OPENAI_IMAGE_EDITS_URL`, `OPENAI_IMAGE_MODEL`, and `OPENAI_IMAGE_API_KEY` variables are also supported. Keep real credentials outside the skill package and output directory.

### Single module

```powershell
python scripts\generate_image.py `
  --env-file C:\private\image-api.env `
  --prompt-file prompts\module-01.txt `
  --image C:\path\to\product.png `
  --size 2048x1152 `
  --quality high `
  --output-dir generated-images\product-detail-v1
```

Omit `--image` for text-only generation. Repeat it for multiple references. Use `--mode sync` or `--mode async` when provider auto-detection is insufficient.

### Batch generation

```powershell
python scripts\generate_batch.py `
  --env-file C:\private\image-api.env `
  --prompt-dir prompts\product-detail-v1 `
  --image C:\path\to\product.png `
  --size 16:9 `
  --resolution 2k `
  --output-dir generated-images\product-detail-v1
```

Batch generation processes prompt files in lexical order and keeps each module in its own folder. Inspect and rename kept outputs according to [delivery-format.md](delivery-format.md).

## Platform Variants

- For any multi-size platform request, create a separate prompt and generation call for each aspect ratio. Re-compose the module; do not derive one variant by stretching, letterboxing, or mechanically cropping the other.
- Amazon A+ working preset: generate `1952x800` for final `1464x600`, and independently generate `1024x768` for final `800x600`.
- Ozon/Wildberries `900x1200` preset: generate `912x1216`, then downsample proportionally to `900x1200`.
- AliExpress vertical preset: use the generation-master mapping in `aliexpress-detail-size.md`; the maximum final size is `1200x2400`.
- For variable-height vertical modules, keep the planned width and per-module height in both the prompt and the generation arguments when the backend supports exact dimensions.
- Treat sizes documented elsewhere in this skill as working presets. The user's current platform specification takes precedence.

## Failure Handling

- Retry a transient backend failure once. Read [failure-retry.md](failure-retry.md) before changing a prompt or attempting a replacement.
- Stop rather than looping when credentials are missing, authorization is unclear, the provider rejects the requested size, or the same failure repeats.
- Never expose API keys in commands, logs, reports, filenames, or chat. Prefer an environment file outside the deliverable.
- Do not create contact sheets, preview grids, stitched boards, or locally assembled images as substitutes for requested generated modules.
