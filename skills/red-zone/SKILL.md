---
name: red-zone
description: >-
  Red marked area image generation workflow. Use when the user invokes
  "$red-zone", says "红区生成", "红区生成法", "红区生成-v1.0", or asks to
  generate or replace content inside red marked areas of a provided reference
  image, especially H5/game/UI screenshots with red squares, translucent red
  masks, red outlines, or red placeholder blocks. By default produces a
  reference-image replacement result and a matching 1:1 white-background
  standalone icon or asset. When the user explicitly asks for a 主KV, 主 kv,
  H5主视觉, 头图, header KV, or hero visual, use Main KV mode to create a 1:1
  1500 x 1500 replacement-ready KV source image that preserves the KV
  composition/background instead of a white-background asset, then place that
  same source image into the red area for the page effect preview.
---

# 红区生成

Use this skill when the user provides a reference image containing red marked areas and names the content to generate in those red areas, such as cake icon, gift icon, coin icon, diamond icon, pet avatar, reward item, badge, button icon, task reward asset, or an H5 main KV / hero image.

## Mode Selection

- **Default asset mode**: use this when the user asks for an icon, prop, reward item, badge, button icon, small illustration, or does not explicitly say the output is a 主KV / 主 kv / H5主视觉 / 头图 / hero visual. Output a red-area replacement result plus a white-background 1:1 standalone asset.
- **Main KV mode**: use this only when the user explicitly says the generation is a 主KV, 主 kv, H5主视觉, 头图, header KV, hero visual, or asks for a replacement-ready head image. Output a red-area replacement result plus a 1:1 1500 x 1500 KV source image that keeps the full KV background, atmosphere, composition, depth, and visual relationships.

If the wording is ambiguous, prefer default asset mode. Do not use Main KV mode merely because the reference is an H5/game/UI screenshot.

## Default Output

Generate two images unless the user explicitly asks for only one.

### Default asset mode

1. **Red-area replacement result**: preserve the full reference image and replace only the red marked areas with the requested content.
2. **Standalone asset**: generate the same content as a reusable icon/asset on a pure white 1:1 canvas, intended as a 1500 x 1500 image when the tool supports or post-processing can enforce the size. The standalone asset must be visually consistent with the actual generated content in image 1, not merely the same theme.

### Main KV mode

1. **Red-area replacement result**: preserve the full reference image and replace the red KV/header region with the generated KV. Keep all non-red UI, buttons, text, tabs, characters, panels, and overlays unchanged.
2. **KV source image**: generate the same KV as a square 1:1 source image, intended and saved as 1500 x 1500 when possible. This image is for replacing the red header/KV area, so it must keep the complete KV composition, background, atmosphere, depth, and visual hierarchy. It must not be a pure white asset and must not be a vertical H5 long page.

Respect the user's storage preference when known. If the user prefers not to save files locally, do not copy generated outputs into the workspace unless they explicitly ask to save or download them. Temporary or tool-cache files may be unavoidable; avoid extra local copies.

## Input Handling

- Treat the reference image as the edit target.
- Treat every visible red square, translucent red mask, red outline, or red placeholder block as a replacement target.
- Infer the target content from the user's wording. If the target content is missing, ask one concise question.
- If multiple red targets exist, replace all of them with the same content by default.
- Scale the generated content to each target area so small placements remain readable and large placements have enough detail.
- In Main KV mode, analyze the reference page before prompting: identify the red region shape, likely crop/placement, fixed UI overlays, bottom tabs, right-side floating buttons, countdown bars, character overlays, and any zones where important KV content would be covered. Derive a layout-specific safe area instead of assuming a fixed template.

## Image 1: Replacement Result

Prompt the image editor to preserve everything outside the red targets:

- Original page dimensions, composition, crop, and aspect ratio
- Background, characters, products, UI modules, buttons, typography, labels, numbers, and text content
- Existing color relationships, lighting, shadows, material style, clarity, and layer hierarchy

Only the red marked areas should change. Remove the red markers completely and generate the requested content inside those bounds.

For H5/game/UI references, match the visual language of the screenshot:

- Lightweight game UI asset style
- Rounded exaggerated Q-version shape language
- Soft 3D clay/toy-like volume
- High saturation but not harsh
- Bright, clean, polished colors
- Soft highlights and shadows consistent with the reference
- Clear silhouette at small sizes

Avoid these failures:

- Red marker remains visible
- Whole page is redrawn or layout shifts
- Text, numbers, button labels, or characters change
- Generated content covers nearby text or key UI affordances
- Icon escapes the marked region too far
- Style looks flat, dirty, blurry, gray, over-rendered, or unrelated

## Image 2: Standalone Asset

Use this section only in default asset mode.

Generate a separate pure white 1:1 image containing only the requested content. It should match the content inserted in image 1:

- If image 1 has already been generated, inspect the actual red-area replacement result first. Treat the inserted icon/asset shapes in image 1 as the source of truth for image 2.
- The standalone asset must reuse the same icon concepts, silhouettes, dominant colors, decorative accents, material treatment, viewing angle, and relative proportions from image 1.
- For multiple icons/assets, preserve the same order and one-to-one mapping as the red targets in image 1. Do not invent new icon metaphors, swap concepts, or redesign the set in the standalone sheet.
- Same palette, material, texture, shape language, and level of cuteness
- Centered composition with comfortable padding
- Clean white background
- Crisp edge quality and clear silhouette for easy cutout
- More complete, balanced, and structurally refined than the tiny in-layout version

For icon-like targets, optimize the structure:

- Clear hierarchy between main body, decorative details, and base
- No broken geometry, awkward perspective, impossible overlaps, sticky unclear details, or material discontinuities
- No text, watermark, complex background, dirty gradients, or low-resolution softness

If the tool output is not exactly 1500 x 1500 and a local file is being saved, resize the standalone image to 1500 x 1500. Do not do this extra local save step when the user has asked for preview/download-only behavior.

## Main KV Mode Details

When the user asks for a 主KV / H5主视觉 / 头图, the second image is not a white-background icon. It is the replacement-ready KV source.

### Required workflow

1. Inspect the reference image and red area. Note the page dimensions, red region bounds, overlaying UI, and likely visible/cropped portion of a square source image.
2. Generate the **1:1 KV source image first** when practical, with the requested title/theme and the safe-area constraints derived from the reference.
3. Create the red-area replacement result using the same KV source image and the same placement/crop logic. This keeps image 1 and image 2 compositionally consistent.
4. If local files are being saved, resize or export the KV source image to exactly 1500 x 1500.
5. Visually verify the page effect: no red marker remains, no important title/character/focal prop is hidden by UI overlays, and the KV focus feels correct after placement.

### KV source image rules

- Canvas: 1:1 square, intended 1500 x 1500. Never output a vertical H5 long image for the pure-view/source image.
- Background: keep the full KV atmosphere and composition. Do not use a pure white background.
- Consistency: image 2 must preserve the composition, visual relationships, mood, depth, and focal hierarchy used in image 1. It may be more polished, but it should not become a different poster.
- Safety: reserve layout-specific safe zones for page overlays. For top H5 header/KV references, this often means keeping the main title/focal group in the upper or upper-middle safe area, leaving lower overlay zones cleaner, and avoiding important content under right-side floating buttons. Adjust these rules based on the actual reference, not a fixed number.
- Style: soft lightweight 3D, Q-version rounded exaggerated forms, high saturation but not harsh, bright cheerful palette, polished toy/clay/plastic material, clean hierarchy, strong focal point, depth of field, and impactful composition.
- Avoid: white studio background, vertical page mockup, extra UI buttons, extra text, watermark, cluttered lower overlay zones, distorted title characters, or source images that cannot be placed back into the red area cleanly.

## Prompt Template

### Default asset mode

Use this compact template and fill in `{target}`:

```text
Execute $red-zone for the provided reference image.

Image 1: preserve the original screenshot exactly outside all red marked areas. Identify every red square, translucent red mask, red outline, or red placeholder block. Remove those red markers and replace only those areas with {target}. Match the original H5/game/UI visual style: lightweight, rounded exaggerated Q-version design, soft 3D clay/toy texture, bright clean high-saturation colors that are not harsh, soft highlights and shadows, crisp small-size readability. Do not alter text, numbers, buttons, characters, background, layout, crop, or aspect ratio. Do not leave red markers visible.
```

For image 2:

```text
Generate the standalone asset from $red-zone using the actual red-area replacement result from image 1 as the visual source of truth. Recreate the same inserted icon/asset content from image 1 on a pure white 1:1 canvas, intended 1500 x 1500. Preserve the same icon concepts, silhouettes, dominant colors, decorative accents, material treatment, viewing angle, relative proportions, and order. Refine only edge quality, centering, padding, and resolution. Do not invent new icon metaphors, swap concepts, or redesign the set. Rounded Q-version shape, soft 3D toy/clay material, bright clean palette, crisp edges, no text, no watermark, no complex background, no broken geometry.
```

### Main KV mode

For the 1:1 KV source image, fill in `{title}`, `{theme}`, and the reference-specific safe-area notes:

```text
Execute $red-zone Main KV mode.

Generate the replacement-ready KV source image first: a square 1:1 H5 header/main KV source, intended 1500 x 1500. Main title text exactly: {title}. Theme: {theme}. Keep the full KV composition, background, atmosphere, depth, and visual relationships; do not use a white background and do not make a vertical H5 long page.

Use the reference-specific placement constraints: {safe-area notes from inspecting the red area and overlaying UI}. Keep important title strokes, character faces, and focal props out of covered overlay zones. Preserve clear visual hierarchy and a strong focal point after the image is placed into the H5 page.

Style: soft lightweight 3D, Q-version rounded exaggerated forms, high saturation but not harsh, bright cheerful palette, polished toy/clay/plastic material, soft glossy highlights, gentle shadows, crisp silhouettes, cinematic depth of field, impactful but clean composition. No extra text, no watermark, no UI buttons, no screenshot frame, no broken geometry, no distorted title characters.
```

For the page replacement result:

```text
Create the red-area replacement result using the same KV source image and the same placement/crop logic. Preserve the original screenshot exactly outside all red marked areas. Remove the red markers and replace only those red areas with the KV. Do not alter text, numbers, buttons, characters, panels, tabs, background outside the red area, crop, or aspect ratio. Do not leave red markers visible.
```

## Delivery

Return both images clearly labeled:

- `图 1：红区替换效果图`
- Default asset mode: `图 2：白底 icon/资产纯享图`
- Main KV mode: `图 2：方形 KV 头图源图（1500 x 1500）`

If the user prefers download-only delivery, show the generated previews or links without making extra workspace copies. If local files are intentionally saved, report their paths and final dimensions.
