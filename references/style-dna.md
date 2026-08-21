# Style DNA Analysis

## Select one of two modes

### Default cute style

Use `default-cute-style.md` when the user provides a real-person or pet identity photo but no style reference. Do not derive a random visual style from the photo.

### Custom reference style

When the user uploads an illustration reference, analyze it using the dimensions below. Treat it as a style source only unless the user explicitly assigns it another role.

## Describe observable properties

Analyze a target style through:

1. **line:** color, thickness, continuity, wobble, taper, closure
2. **shape:** geometric, bean-like, angular, rounded, asymmetrical
3. **proportion:** head-to-body ratio, limb length, hand and foot scale
4. **face:** eye system, mouth scale, nose treatment, blush, expression range
5. **color:** saturation, value range, palette size, accent behavior
6. **texture:** flat, pencil, paper grain, wax, watercolor, or none
7. **depth:** flat fill, minimal shading, modeled volume, lighting behavior
8. **composition:** subject scale, spacing, background, cropping, layout rhythm
9. **motion language:** action lines, emotion marks, exaggeration, pose looseness
10. **text:** handwriting, labels, typography, or text-free

Produce a compact style profile with positive rules and an avoid list. Describe the visual result rather than naming or copying the character shown in the reference.

## Keep identity separate

A style reference controls how to draw, not whom to draw. Explicitly exclude its:

- face and hairstyle
- glasses and accessories
- clothing and shoes
- props and companion characters
- written text and logos

## Preserve identity under restyling

Restyling may simplify forms, but it must preserve the character's signature silhouette and fixed traits. If a target style cannot show a small detail reliably, convert it into a simpler equivalent rather than deleting it silently.

## Avoid vague style prompts

Replace “make it cuter” or “match this style” with observable instructions. For example:

```text
Use thin warm-brown contours, flat low-detail fills, a 2.5-head chibi proportion,
dot eyes, a tiny coral mouth, restrained blush, a warm off-white background,
and sparse hand-drawn motion marks. Remove glossy shading and dense hair strands.
```
