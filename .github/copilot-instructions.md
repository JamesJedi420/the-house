# Copilot Instructions

## Project Summary

Goal: A browser based interactive fiction game with beat driven progression, choices, inventory, and clue logging. The game runs from a single HTML file with embedded CSS and JS.

Core mechanics
1. Beat driven story progression via `const beats = { ... }`.
2. Two choices per beat by default.
3. State tracking: Trust, Normalcy, Unease, Time.
4. Inventory and clues updated through `fx: (s)=>{ ... }`.
5. Save and Load via `localStorage`.

Content rules
1. Keep story text literal.
2. Actor notes are optional and togglable.
3. Do not use meta identifiers in prose such as door IDs.
4. Keep each `text[]` entry to 1–2 sentences.

## Editing Rules (Hard Constraints)

1. Make the smallest valid change that satisfies the request.
2. Only modify files explicitly requested.
3. Do not reformat unrelated sections.
4. Do not change CSS or UI logic unless requested.
5. Validate all beat links: every `choices[].next` must point to an existing beat key or be `null`.
6. Maintain the beat schema: `title`, `loc`, `time`, `text[]`, `notes[]` (optional), `choices[]`, `hint` (optional).
7. Preserve two choices per beat unless the user explicitly wants an end node.

## When Adding or Updating Beats

Required steps
1. Insert new beat objects inside `const beats = { ... }` using keys like `"X.Y"`.
2. Update existing beats by changing only the specific `choices[].next` targets required.
3. Ensure commas and braces are correct:
   - Every beat object ends with `},`
   - Arrays use commas between entries
4. Ensure every `next` target exists before finishing.

Forbidden behavior
1. Do not introduce partial edits that leave dangling `next` references.
2. Do not paste story text into `choices[].t` or other fields.
3. Do not add meta labels in narrative text.

## Project Structure Reference

Single file mode
- `fixing_house_beat1_game.html` contains:
  - CSS for layout
  - `state` object and `localStorage` save/load
  - `beats` object containing story content
  - `render()` / `advance()` functions controlling flow

Optional future split (only if requested)
- `src/beats.js` beat content
- `src/state.js` save/load
- `src/ui.js` rendering

## Definition of Done

1. Page loads and does not hang on "Loading…".
2. Clicking any choice does not throw console errors.
3. New beats are reachable through at least one path.
4. Save and Load work after refresh.
5. No `choices[].next` points to a missing beat.

## Documentation Requirements

If a change adds new workflow rules, update documentation only when requested.
Minimum docs expected:
- `README.md` with run instructions, beat schema, adding beats safely, and troubleshooting.