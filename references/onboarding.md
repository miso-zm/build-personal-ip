# First-Use Onboarding

## Goal

Help a first-time user understand what to upload and choose a style path before building the character. Do not force the user to learn the Skill's internal vocabulary.

## Detect the current state

Use this decision table:

| Existing accepted profile | Identity image | Style reference | Action | Stored style mode |
|---|---|---|---|---|
| no | no | no | explain both paths and request an identity image | unset until chosen |
| no | yes | no | announce and use the default cute style, then create the combined character-and-styling checkpoint | `default-cute` |
| no | yes | yes | confirm input roles, extract custom style DNA, then create the combined character-and-styling checkpoint | `custom-reference` |
| no | no | yes | retain the style reference and request an identity image | `custom-reference` after identity arrives |
| yes | any | any | reuse the accepted profile and anchor without repeating onboarding; treat new references only in roles the user explicitly assigns | keep existing mode unless explicitly changed |

An explicit user instruction overrides automatic detection. If a user supplies a style image but explicitly asks for the default style, keep `default-cute` and treat the extra image only in the role the user assigns.

### No accepted character and no identity image

Explain the two paths, then ask the user to upload at least one identity image.

Use this concise Chinese message when the conversation is in Chinese:

```text
可以。请先上传至少一张清晰的本人照片，你有两种建立方式：

1. 默认可爱Q版：只上传真人照片，我会使用这套Skill自带的可爱插画风格。
2. 自定义画风：上传真人照片，再补充1–3张你喜欢的插画参考，我会保留你的身份特征，只参考它们的线条、比例、颜色和质感。

最好包含一张清晰正脸；如果方便，再补充一张全身照。上传后我会先让人物形象和服装一起定稿，再用定稿版本一次生成三视图与表情包，避免反复重做。
```

Translate or adapt the message to the user's language while preserving the two choices.

### Identity photo only

Select the default cute style without asking a redundant style question. Briefly state the selected path:

```text
我会把这张照片作为人物身份参考，并使用Skill自带的可爱Q版风格。先把人物特征与服装造型一起整理成正面设计方案；确认后再一次生成三视图和表情包。
```

Ask a question only when a decisive identity feature is obscured or contradictory.

Set `style_profile.mode` to `default-cute` and keep `style_profile.reference_paths` empty.

### Identity photo plus illustration references

Select the custom reference path. Confirm the roles before generation:

```text
我会把真人照片作为人物身份参考，把插画图片仅作为画风参考。参考图人物的脸、发型、服装和配饰不会自动复制到你的角色上。
```

If the user also supplied outfit or accessory references, identify those separately.

Set `style_profile.mode` to `custom-reference` and record only the accepted style-reference paths in `style_profile.reference_paths`.

### Style reference only

Do not turn the style-reference character into the user's IP. Ask for at least one identity image:

```text
这张图可以作为画风参考。还需要你上传至少一张本人、宠物或已有角色的清晰图片，才能建立属于你的IP身份。
```

### Existing accepted profile or anchor

Use the accepted identity immediately. Ask whether to keep the current style only when the new request introduces conflicting style references.

Do not overwrite the stored style mode or anchor merely because new images appear in the conversation. Change them only when the user assigns those images a new role or accepts a revised anchor.

## Resolve styling at the first checkpoint

- If the user explicitly specifies an outfit, hairstyle, or accessory—or asks to keep the photographed styling—create one integrated front-facing design draft.
- If styling is visibly incidental, unspecified, or the user wants choices, create two to four full-body options immediately. Keep identity, pose, and style constant; vary only the unresolved design layer.
- Present this as one character-design decision, not as a later outfit workflow.
- A clear option selection counts as acceptance unless the user also requests changes. Do not ask a redundant follow-up such as “是否正式确认”.
- After a requested revision, repair only the chosen design until accepted. Do not create provisional turnarounds or expression sheets before this point.

Do not force variant exploration when the user already knows what they want.

## Keep companion IP opt-in

Set `companion_ip` to `false` by default. Do not add a pet question to ordinary onboarding.

Enable the companion branch only when the user explicitly asks for a pet/companion IP or explicitly assigns an uploaded pet image that role. A pet visible incidentally in a personal photo does not enable the branch.

## Recommended upload quality

- Minimum: one unobstructed face or character image.
- Better for a full-body anchor: one clear face image plus one full-body image.
- Better for signature styling: one additional image showing normal hairstyle, outfit, or accessories.
- Custom style: one to three coherent illustration references. Avoid mixing unrelated styles unless the user wants deliberate exploration.

Do not demand all recommended images before starting. Explain how missing views may reduce certainty and proceed conservatively when possible.

## Conversation sequence

Use a two-decision budget for a normal reusable-IP build:

1. select or accept the integrated character design
2. confirm the turnaround and expression sheet together

Do not turn automatic routing into user questions. Do not separately ask the user to confirm style mode, face, clothing, turnaround, and expressions when the inputs or prior selection already resolve them. Ask at most one short clarification at a time, and only when the answer would materially change the result.

Use concise prompts adapted to the user's language:

- Design checkpoint: `请选择一个方案，回复编号即可；需要修改时直接指出具体位置。`
- Core-pack checkpoint: `三视图和九宫格表情是否可以一起定稿？如有问题，请指出具体视角或表情。`

1. Explain the two style paths when inputs are missing.
2. Receive and classify uploaded images.
3. State the chosen style path and image roles.
4. Summarize a compact identity-and-styling profile.
5. Generate one integrated front-facing draft, or two to four same-pose options when styling is unresolved.
6. Ask the user to select, accept, or narrowly revise the design. A clear selection is the acceptance event.
7. On acceptance, set `profile_status` to `accepted`, store the selected anchor, and lock the current styling.
8. For a reusable-IP build, generate the turnaround and compact expression sheet together as one core asset stage, unless the user requested only one of them.
9. Ask for one combined confirmation, then move directly to the user's requested article illustrations, social visuals, knowledge cards, or infographics.

For a content-only request, stop the setup sequence after step 7 and produce the requested content directly. Do not require the core asset pack first.

Avoid collecting a long questionnaire before the first design checkpoint. Use the first output as a concrete object for discussion. Do not automatically append companion creation or unrelated variant exploration to the main path.
