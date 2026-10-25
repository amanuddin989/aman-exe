# AMAN.EXE

A playable 8-bit introduction for Aman, Visual Communication Designer at GreyB.
React + TypeScript + CSS, built with Vite into one self-contained HTML file.

## Run
    npm install
    npm run dev      # local preview
    npm run build    # writes dist/index.html (single file, sprites inlined)

## Edit
- src/config.ts    contact for the final button (email or Teams link), palette
- src/content.ts   every line of dialogue and on-screen text
- src/scenes/*.tsx one file per scene: the view and its script (await d.walk(), d.say() ...)

## Sprites
src/assets/sprites/ holds one transparent PNG per pose, expression and prop, cut from the
character sheet by tools/extract.py (crop, remove the paper background, halve to the sheet's
real pixel size, snap to one shared 64-colour palette). Re-run with `npm run sprites`.

The sheet has one frame per pose, so animations combine poses:
walk = side + stride, wave = wave + idle, idle = front + front idle.
For smoother motion, ask an artist for 4-6 frame cycles at the same 80px height and
drop them into src/assets/sprites, then list them in src/components/Character.tsx.

## Publish on GitHub Pages
The built site is docs/index.html (one file, nothing else needed).
Repo Settings > Pages > Source: Deploy from a branch > Branch: main, folder: /docs.
After a change: `npm run build && cp dist/index.html docs/index.html`, then commit.
