# General Skill — Images

## Hard rule
SingleBrain (and Claude) **NEVER generate images.** You write PROMPTS; Xander generates them in Higgsfield.

## Prompt rules
- One labeled prompt per image slot (`banner.jpg`, `s1.jpg`, `s2.jpg` …).
- Photorealistic, editorial quality. A different look per slot (vary composition/subject).
- **TEXT-SAFE, but NEVER fake-blank.** Avoid *legible* text (AI garbles it) — but a **blank white sheet of paper reads as fake and stupid.** Where paper, labels, or screens must appear, render them **softly out of focus with realistic, non-legible print/marks** (a shipping label with blurred lines + a barcode; a screen with a soft color glow, no UI). Better still: compose so writable objects aren't the focal point.
- **Editorial craft, NOT literal metaphor.** No "network map made of paper slips," no "crew passing glowing blue tools" — that is AI-stock slop. Aim for the register of a real publication (Monocle, Bloomberg Businessweek, WIRED, Fortune): one intelligent idea, real light, real texture, a real human or conceptual truth. Every image must (a) say something the headline doesn't and (b) look like it cost money to shoot.
- No logos, no readable text, no branding in the scene.
- Model of record: **GPT Image 2 — force `quality:"high"`** (it defaults to LOW). (`nano_banana_pro` silently aliases to `nano_banana_2`.)

## Detail + sizes (REQUIRED on every prompt)
- **Detailed, not short.** GPT Image 2 makes mistakes on vague prompts. Write each one like a brief for a real photographer, specifying: the **subject + specifics**, the **setting/environment**, **lighting + time of day**, **composition/framing** (plus any overlay-safe zones — e.g. keep a side darker for text), **mood/emotion**, **photographic style** (camera + lens + film-stock feel), **color palette**, and **explicit negatives** (no text, no logos, no legible signage, no watermarks, no on-screen UI).
- **Always state the SIZE** on every prompt:
  - **Generation size** (GPT Image 2 native): `1024x1024` (square), `1536x1024` (landscape), or `1024x1536` (portrait) — pick the shape closest to the slot.
  - **Display size** in the email in px, so it fits the HTML slot (e.g. hero ~700×430, inline photo ~210×210).

## After generation
Xander returns the images; convert to email-weight JPEGs (~1080px wide, ~90–115 KB) and wire them into the HTML with graceful fallback (`background` + `min-height` on the cell).
