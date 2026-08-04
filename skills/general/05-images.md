# General Skill — Images

## Hard rule
SingleBrain (and Claude) **NEVER generate images.** You write PROMPTS; Xander generates them in Higgsfield.

## Prompt rules
- One labeled prompt per image slot (`banner.jpg`, `s1.jpg`, `s2.jpg` …).
- Photorealistic, editorial quality. A different look per slot (vary composition/subject).
- **TEXT-SAFE:** no writable object in the scene (no paper, notebooks, screens, signs) — avoids garbled AI text.
- No logos, no readable text, no branding in the scene.
- Model of record: **GPT Image 2 — force `quality:"high"`** (it defaults to LOW). (`nano_banana_pro` silently aliases to `nano_banana_2`.)

## After generation
Xander returns the images; convert to email-weight JPEGs (~1080px wide, ~90–115 KB) and wire them into the HTML with graceful fallback (`background` + `min-height` on the cell).
