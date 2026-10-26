---
name: garment-tryon-studio
display_name: 商品服装换装图策划与质检
display_name_en: Garment Try-On Planning and QA
description: Plan and review faithful ecommerce garment try-on images from product references.
description_zh: 根据服装素材制定换装图方案、生成提示词，并按产品结构和颜色验收成片。
description_en: Plan garment styling, prepare image prompts, and review try-on results for ecommerce use.
examples_zh:
  - 帮我根据这件外套的照片做一张电商换装图方案，先别生成。
  - 检查这张换装图有没有改掉衣服结构或颜色。
  - 给这件针织衫整理搭配和生图提示词。
examples_en:
  - Plan an ecommerce try-on image from this jacket photo, but do not generate it yet.
  - Check whether this try-on image changed the garment's shape or color.
  - Suggest styling and prepare an image prompt for this knit top.
version: 0.1.1
author: giorgioqin
---

# 商品服装换装图策划与质检

Use this skill when planning, prompting, generating, or reviewing ecommerce fashion try-on images. Treat the garment reference as the source of truth.

Load the relevant supporting instructions for each stage: `@references/workflow.md`, `@references/prompt-template.md`, and `@references/quality-checklist.md`. Read the workflow at intake, the prompt template before writing a generation prompt, and the quality checklist when reviewing an image.

## Workflow

1. Identify the requested stage: intake, styling plan, prompt only, image generation, image review, local repair, or delivery. Do not silently move to a later stage.
2. Review the supplied garment images. Record only visible facts about color, cut, collar, placket, pockets, seams, sleeves, hem, material, texture, and pattern. If an important feature is blocked, cropped, blurry, or obscured by color cast, ask only for the missing information needed for this shot. Never fill gaps by guessing.
3. Select up to three visual selling points. Each point must have a specific visible location in the image. Keep factual claims such as fiber content, warmth, or care instructions out of the image unless the user supplies evidence and asks for copy.
4. Suggest an inner layer, bottom, accessories, model reference, pose, lighting, and framing that make the garment easy to judge. Keep the relevant neckline, placket, hem, cuffs, and other defining construction details visible. Do not let styling hide a selling point.
5. Prepare the prompt using the seven-part structure in `references/prompt-template.md`. Preserve the supplied garment's construction, color, proportions, closures, and pattern. If a model reference is supplied, preserve that person's identity and the requested pose and scene unless the user asks to change them.
6. Before using an image-generation capability, state the image count, available tool, and cost estimate when known. Generate only when the user explicitly asks for generation or confirms the proposed generation. Default to one image per garment and model combination. Reuse an accepted result when available. Do not reroll, retry, add variants, or incur a second charge automatically.
7. Review generated images with `references/quality-checklist.md`. Describe each visible issue and its location. Prefer a local, targeted repair when the available tools support it. Ask before any additional generation or paid operation.
8. If image generation or image editing is unavailable, say so plainly and return the plan, prompt, or repair brief that can be used elsewhere. Never claim an image was created when it was not.

## Privacy and rights

- Use customer images only for the requested task. Do not add customer images, private prompts, personal data, model-library files, or client examples to this Skill, public repositories, or public demonstrations.
- Do not send, publish, or share an image or customer material unless the user explicitly asks for that specific action.
- Keep original images unchanged. Treat third-party reference images and assets as subject to their original permissions; public availability alone does not grant resale rights.
- Do not invent product specifications, permissions, costs, or successful test results.

## Response shape

Keep the first response concise and practical. For a plan, return:

- Confirmed garment facts and any blocking unknowns.
- Up to three visual selling points with their image locations.
- Styling and framing plan.
- A ready-to-use prompt, if requested.
- Whether image generation is available and what it would cost, if known.

For image review, return a pass/fix list tied to visible details. Separate confirmed defects from uncertain observations.
