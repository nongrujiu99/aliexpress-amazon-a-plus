# Failure Retry Rules

Use these rules after each generated image or batch.

## Retry Once Immediately

Retry the failed module once when:

- API returns transient error.
- Image ratio does not match the requested ratio or platform size.
- Product is badly distorted.
- Text is garbled.
- A fake logo, fake certification, rating, review, or unsupported claim appears.
- Model identity changes significantly.

## Shorten Prompt on Retry

Keep:

- Campaign Style Lock
- Model Identity Lock if needed
- Product reference sentence
- Module task
- Headline and labels
- Avoid list

Remove:

- Long descriptive prose
- Too many scene props
- Extra body copy
- Multiple competing visual metaphors

## Safer Regeneration Patterns

- Text failure: use fewer labels; replace paragraphs with icons.
- Product drift: make product larger, front-facing, and explicitly preserve visible structure.
- Model drift: crop below eyes, use side/back view, ghost mannequin, or product-only detail.
- Fake brand prop: specify “generic unbranded props only”.
- Unsupported claim: replace with “visible package claim” or remove the claim.
- Wrong size: regenerate with the documented compatible master. Use `2048x1152` for the default 16:9 set, `912x1216` for final Ozon/WB `900x1200`, Amazon `1952x800` for final `1464x600` or `1024x768` for final `800x600`, and the mapped AliExpress master such as `1216x1824` for final `1200x1800`. Regenerate only the failed variant. Downsample only after the master passes content QA; never crop, stretch, letterbox, or upscale.
