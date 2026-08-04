# Stage 3 — Image Brief (template)

## FILL THESE IN FIRST

*(Operator note, safe to leave in the pasted prompt.)*

| Placeholder | What to put in it | Where to get it |
|---|---|---|
| `{{NEWSLETTER_NAME}}` | e.g. `The Protocol` | `CLAUDE.md` |
| `{{IMAGE_DIRECTIONS}}` | All **8** slot directions, s0-s7, one line each, pasted as a list. Read them together before pasting: no two slots may share a subject. | The "Staging notes → Image slots" table in the stage-2 markdown |
| `{{OUTPUT_FOLDER}}` | e.g. `...\Newsletter\protocol-issue-1\images` | Convention: `<name>-issue-N\images` beside the `index.html` |

**Before you paste:** check the eight directions for a repeated subject. Two van scenes in one issue and two empty-studio-with-chairs scenes in another each cost a re-shoot. This is the cheapest check available and it happens here, not after generation.

---

## PASTE FROM HERE

Generate the eight images for one issue of **{{NEWSLETTER_NAME}}**. Save them to **{{OUTPUT_FOLDER}}**.

The first two image sets on this project were rejected by the client as *"templated, cheap, AI slop."* The cause was a locked style block — one palette, one look, one model across every slot. Real newsletters look like curated news precisely because every image came from somewhere different. The rules below are what fixed it.

### The eight slots

{{IMAGE_DIRECTIONS}}

Slot `s0` is the banner. `s1`-`s6` are the six story cards. `s7` is the utility segment. **`s3` is the house announcement image** — see the exception below.

### The brief

- **Photorealistic editorial and press photography only.** Never illustration, never vector, never 3D render, never infographic, never chart.
- **A different model for every slot.** This is the single biggest variety lever. **No model used more than twice in one issue.** Write your model-to-slot plan out before you generate anything.
- **Vary lighting, colour temperature, composition, focal length and mood between slots.** Warm practical light in one, cold overhead in the next; overhead flat-lay here, shallow-depth eye-level there; morning, midday, night.
- **Art-direct each slot independently.** Never write a reusable style block and apply it across slots. That is exactly what produced the rejected sets.
- **The test:** *if any two images in the issue look like they came from the same shoot, you failed.* Apply it before you deliver, not after.
- **No identifiable real people.** No recognisable faces, no public figures, no named brands, no logos or brand marks. Empty rooms, hands, and out-of-focus figures at distance are the safe register.
- **The exception to the variety rule:** `s3`, the house-announcement image, **must not be the visual outlier.** It has to sit naturally among s1-s6 at the same width, aspect ratio and register. Any visual signal that it is a promo flags the block as an ad and defeats the entire native-announcement mechanic. Vary it like the others — just never past the point where it stands out.

### The text problem — the biggest tell

Garbled AI lettering is what makes an image read as fake. **A "no text" clause in the prompt is not sufficient.** It fails often enough to be useless on its own. The real rule:

> **Choose concepts where no surface in frame could plausibly carry lettering.**

Some concepts are *structurally* text-generating and no prompt discipline saves them.

**High-risk subjects — avoid or reframe:** windshield or dashboard POV (car interior warning labels and gauges *plus* street signage in one frame — this failed twice), whiteboards, equipment with badges or nameplates, vehicles with grilles or livery, product packaging, book spines, screens and monitors, notebooks and paperwork, building facades, storefronts, jerseys, keyboards, machine control panels.

**Safe subjects:** lawns, sky, bare ground, asphalt, fabric, foliage, coiled cable, empty rooms, unbranded tools, water, food, hands, plain furniture, single light sources.

The strongest images across every set produced so far were the emptiest ones — an attic, a hearing room, a marble cafe table. When a direction is ambiguous, take it emptier.

Still include a no-text, no-lettering, no-logo instruction in every prompt. It is a second line of defence, not the first.

### Known model quirks — verified across five production runs

| Model | Behaviour you must handle |
|---|---|
| `gpt_image_2` | **Defaults to `quality:"low"`.** Always set `quality:"high"` and the `2k` tier explicitly. This default is the likeliest root cause of the original "cheap" complaint. |
| `nano_banana_pro` | **Silently aliased server-side to `nano_banana_2`.** You cannot get the Pro tier. Plan your rotation as if only `nano_banana_2` exists. |
| `cinematic_studio_2_5` | Reliable, 4k. **Ignores time-of-day unless it is the FIRST thing in the prompt, in caps** — `NIGHT HAS FALLEN.` Cost two daylight misses before this was found. |
| `soul_2` | Best film grain of the set, but **ignored explicit negative instructions three times running.** Use it for texture, never for a scene that depends on something being excluded. |
| `flux_2` (pro) | Best constraint-following. Defaults to 1k — force the tier. |
| `seedream_v4_5` / `seedream_v5_pro`, `kling_omni_image`, `nano_banana_2` | Solid all-rounders. Good rotation filler. |

### Verification — do this yourself, before delivering

1. **Look at the images.** Use `Read` on each `.jpg`. Do not trust your own self-report and do not describe an image you have not opened.
2. **Inspect the master at full size, then zoom the text-capable surfaces specifically.** A label you missed at thumbnail size is the one a reader will see.
3. **Check the delivery file, not the master.** Defects invisible at 600px do not matter and masters may keep them.
4. If a small label survives and everything else about the frame works, it can be patched by cloning adjacent texture — but that is a **hand edit and must be disclosed** in your report, never passed off as a generation.
5. Re-run the same-shoot test across the final eight.

### Delivery specs

- Save the full-resolution generations as **`.png` masters** in {{OUTPUT_FOLDER}}, named `s0.png` … `s7.png`. Keep them for future re-use.
- Deliver **`s0.jpg` … `s7.jpg`, resized to 600px wide, JPEG quality 62.**
- Expected total payload for the eight JPEGs: roughly **140-215 KB**. Materially over that, re-check the compression.
- 600px is deliberate: the HTML declares `width="600"` on the banner and `width="594"` on story images, and **never declares larger than the source** or the email client upscales it into mush.

### Report back with

- The model used for each slot, proving no model was used more than twice.
- Confirmation you opened every delivered `.jpg` and what you saw in each.
- Any surviving text, any hand edit, and any slot you would re-shoot given more credits.
- The file sizes of the eight JPEGs.

### Done means

Eight photorealistic images, no two from the same apparent shoot, s3 sitting invisibly among s1-s6, zero legible lettering anywhere, masters kept, and eight 600px JPEGs in {{OUTPUT_FOLDER}}.
