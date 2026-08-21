# Character Identity Profile

## Extract identity conservatively

Record visible or user-confirmed traits across these groups:

- species, age impression, body and chibi proportions
- face shape, eyes, brows, nose, mouth, blush
- hair or fur shape, color, highlights, parting, length
- signature accessories and their placement
- default clothing, shoes, and palette
- silhouette-defining features
- companion characters and relative scale

Do not confuse styling with identity. An outfit is normally variable; a signature hair clip may be fixed.

## Separate four states

- **fixed:** identity would feel wrong if changed
- **variable:** safe exploration area
- **current:** selected version for the present asset set
- **forbidden:** rejected or unwanted traits

When the user changes a fixed trait explicitly, update the current version and record the previous state rather than pretending nothing changed.

## Establish acceptance

An output becomes an anchor only when the user accepts it or continues from it without rejecting its identity. A generated draft is not automatically authoritative.

Keep `profile_status: draft` before acceptance. After acceptance, set `profile_status: accepted`, store the accepted anchor path, and preserve the selected style mode for later sessions.

For a new project:

1. copy `assets/character-profile-template.yaml`
2. fill only supported fields
3. add the accepted anchor path
4. increment the version after meaningful identity changes

## Keep companions independent

Keep `companion_ip: false` unless the user explicitly enables it. Do not infer demand from an incidental pet appearance or from the general request to build a personal IP.

When enabled, give each companion its own fixed, variable, current, and forbidden traits. Record the relationship scale and shared style, but do not merge the two identities into one profile.
