# Consistency and Repair QA

## Acceptance order

1. The requested message or edit is correct.
2. Fixed identity traits match the accepted anchor.
3. The target style profile is visible and coherent.
4. Current outfit, hair, accessories, and palette are accurate.
5. Layout, view count, grid count, and aspect ratio are correct.
6. Text and data are exact when required.
7. No unwanted characters, props, labels, logos, or watermarks appear.
8. The workflow did not produce reusable assets before current styling was accepted or enter an unrequested companion branch.

## Common failure signals

- face shape, eye system, or body proportions drift between images
- signature highlights or accessories move, disappear, or change color
- a style-reference character's identity leaks into the user's IP
- an outfit edit unexpectedly changes the face or hair
- a companion changes species, markings, or relative scale
- a turnaround uses different clothing construction across views
- an expression grid contains duplicates, extra subjects, overlaps, or the wrong count
- an article scene is generic and unrelated to the source idea
- an infographic invents, omits, or distorts text or data
- a turnaround or expression sheet is generated for a provisional outfit and then repeated after outfit selection
- a pet or companion workflow is suggested or started without explicit user intent
- the user selects a clear design option and is asked to confirm the same choice again
- a content-only request is blocked on an unrequested turnaround or expression sheet

## Repair by layer

Prefer a narrow repair clause:

- **Identity drift:** restore the accepted face, silhouette, hair, signature accessory, and proportions; preserve the current pose and layout.
- **Style drift:** change only line, shape simplification, palette behavior, texture, and depth; preserve identity and content.
- **Outfit error:** correct the named garment construction or color; preserve face, hair, body, pose, background, and layout.
- **Local facial error:** edit only the eyes, brows, nose, or mouth requested; preserve the original visual language and every other region.
- **Grid error:** restore the exact count, one subject per cell, equal scale, full visibility, and no overlaps.
- **Content error:** replace the generic scene with one concrete action tied to the selected idea.
- **Text or data error:** repair the affected page only; reduce text or split the page when reliable rendering is not possible.

## Version discipline

Do not replace an accepted anchor with a repair draft until the user accepts the identity change. Record meaningful changes in the character profile and keep previous accepted asset paths when available.
