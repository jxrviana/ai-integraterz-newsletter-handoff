# Stage 4 — HTML Build Brief (template)

## FILL THESE IN FIRST

*(Operator note, safe to leave in the pasted prompt.)*

| Placeholder | What to put in it | Where to get it |
|---|---|---|
| `{{SOURCE_MARKDOWN}}` | Absolute path to the stage-2 issue file | e.g. `...\Newsletter\PROTOCOL-ISSUE-1.md` |
| `{{TEMPLATE_HTML}}` | Absolute path to a shipped `index.html` to copy the skeleton from | e.g. `...\Newsletter\protocol-issue-1\index.html` |
| `{{ACCENT_COLOUR}}` | Masthead issue-line colour, hex. e.g. `#e8b06a` | Pick one per newsletter and keep it fixed across issues |
| `{{LINK_COLOUR}}` | Every link in the body, hex. e.g. `#1d4ed8` | Same for all newsletters unless told otherwise |
| `{{MASTHEAD_BACKGROUND}}` | Masthead block and section divider bars, hex. e.g. `#1f2430` | Same value is used for both |
| `{{OUTPUT_FILE}}` | e.g. `...\Newsletter\protocol-issue-1\index.html` | The `images\` folder sits beside it |

---

## PASTE FROM HERE

Build the email-safe HTML for one newsletter issue.

**Source of content:** {{SOURCE_MARKDOWN}} — the issue, verbatim. Do not rewrite, re-order, trim, or "improve" any copy. Your job is conversion, not editing. If something in the markdown looks wrong, flag it in your report and build it as written.

**Skeleton to copy:** {{TEMPLATE_HTML}} — an already-shipped issue. Match its structure exactly and change only the content, the three colours below, and the image filenames.

**Write to:** {{OUTPUT_FILE}}. Images are referenced relatively as `images/s0.jpg` … `images/s7.jpg`; that folder sits beside the HTML file.

### Colours

- Masthead block and every section divider bar: `{{MASTHEAD_BACKGROUND}}`
- Masthead issue line: `{{ACCENT_COLOUR}}`
- Every link: `{{LINK_COLOUR}}`
- Page background `#f4f4f5` · card background `#ffffff` · card border `1px solid #e5e7eb` · body text `#333333` · muted text `#666666` and `#8b93a3`

### Email-safe spec — all of it is mandatory

**Document.** XHTML 1.0 Transitional doctype. `<head>` carries `Content-Type` UTF-8, `viewport`, `x-apple-disable-message-reformatting`, `format-detection`, a `<title>`, and the MSO `PixelsPerInch` conditional. Encode every special character as an HTML entity — `&mdash;`, `&rsquo;`, `&ldquo;`, `&ndash;`, `&rarr;`, `&middot;`, and numeric entities for emoji.

**Layout: nested tables only.** No `div` layout, no flexbox, no grid, no float, no positioning. Every layout table carries `role="presentation" cellpadding="0" cellspacing="0" border="0"` and `border-collapse:collapse`. Vertical rhythm is spacer rows — `<tr><td style="font-size:0; line-height:0; height:18px;">&nbsp;</td></tr>` — never margins between blocks.

**All styles inline.** Every style sits in a `style` attribute on the element that needs it, repeated on each element. No external stylesheet, no `<link>`, no web fonts, no JavaScript of any kind, no CSS background images. The only permitted `<head>` CSS is the single link-colour fallback rule the template already carries: `a { color:{{LINK_COLOUR}}; }`.

**Font.** One system stack everywhere, repeated on every text element, including inside `<a>`, `<li>` and `<strong>` contexts:
`-apple-system,'Segoe UI',Roboto,Helvetica,Arial,sans-serif`

**Column.** A full-width outer table on the page background, one centred `td`, and inside it a table at `width:100%; max-width:640px`. Wrap that inner table in the **MSO ghost table** so Outlook holds the width:

```html
<!--[if mso]>
<table role="presentation" width="640" cellpadding="0" cellspacing="0" border="0" align="center"><tr><td>
<![endif]-->
   ... the 640px table ...
<!--[if mso]>
</td></tr></table>
<![endif]-->
```

**Cards.** Every content block is its own table row whose `td` carries: `background-color:#ffffff; border:1px solid #e5e7eb; border-radius:6px; padding:22px;` plus the font stack. The house blurb is the one deliberate variant (`background-color:#fafafa`, centred italic) — it is not a story card.

**Preheader.** Exactly one hidden element in the entire email, immediately after `<body>`, using exactly this and nothing else:

```html
<div style="display:none;max-height:0px;overflow:hidden;mso-hide:all;">PREVIEW TEXT HERE</div>
```

**No `font-size` on it. No `color` on it.** A near-zero font size here triggers SpamAssassin's `__FONT_INVIS` — 2.499 points on mail-tester, and it arms six sibling rules worth 2.5-3.5 each. Colour-matching-the-background is a *different and near-worthless* rule (`HTML_FONT_LOW_CONTRAST`, 0.001) — do not confuse the two and do not "fix" this by adding a colour. And keep it to one hidden element: `display:none` feeds `__STY_INVIS`, which is harmless once and risky repeated.

**Images.**
- Banner: `width="600"`, `style="width:100%; max-width:640px; height:auto; display:block; border:0; background-color:#e9ecf1;"`
- Story and utility: `width="594"`, same style plus `border-radius:4px`, wrapped in `<div style="margin-top:16px; font-size:0; line-height:0;">`
- **Never declare a width larger than the source file.** Sources are 600px wide; declaring more makes the client upscale it.
- **Real, literal alt text on every image** — the story headline in plain words, or a short factual description of the banner. Never empty, never generic, never a filename.
- **Never put a merge token inside an `alt` attribute.** Any `alt` value containing `{{` is a build error. If a token lands there, the ESP renders raw braces into the reader's inbox on every blocked-image open.

**Links.** Every `<a>` carries the full font stack, an explicit `font-size`, `color:{{LINK_COLOUR}}`, and `text-decoration:underline`. Story headlines are links *and* so is `Read more &rarr;` — both point at the same URL. Footer links use the muted colour, not the link colour.

**Tokens that must survive into the output:** `{{UNSUBSCRIBE_LINK}}` (top bar and footer) and `{{VIEW_ONLINE_LINK}}` (top bar and the footer preferences line). Do not resolve them, do not delete them, do not rename them. The ESP maps them at build time.

### The card-3 parity check — do this programmatically

Card 3 is the house announcement. The entire mechanic depends on it being visually indistinguishable from the news cards around it. **The human eye will not catch a 2px padding difference, and that difference is exactly what tells a reader "this one is an ad."**

After the file is written, run a script that:

1. Extracts the tag skeleton of all six story cards.
2. Extracts **every `style` attribute** from all six story cards, in document order.
3. Diffs cards 2, 3, 4, 5 and 6 against card 1.
4. Prints the diff.

Cards 2-6 must come back **byte-identical to card 1** on every structural style attribute — card `td`, category label, headline anchor, image wrapper, image, body paragraphs, list, list items, and the `Read more` anchor. The only legitimate differences are the text content, the `href`, the image `src`, and the `alt`.

Report the actual diff output. "I checked and they match" is not a result.

### Verification report — required, in your final message

1. **The card-3 parity diff**, pasted, with the command you ran.
2. **Every outbound URL in the file**, listed, with the count of how many times each appears. Confirm each one is a real destination and not a placeholder someone forgot.
3. **Every double-brace token remaining in the file, with its occurrence count.** Expect only `{{UNSUBSCRIBE_LINK}}` and `{{VIEW_ONLINE_LINK}}`. Anything else is a blocking item — name it.
4. **Explicit confirmation that no double-brace token appears inside any `alt` attribute.** Grep for `alt="{{` and show the zero-hit result.
5. Confirmation there is exactly one hidden element, and that the preheader div carries no `font-size` and no `color`.
6. Confirmation that no image declares a width larger than 600.
7. The rendered file's byte size.

### Done means

{{OUTPUT_FILE}} exists, opens in a browser looking like the markdown, contains no external CSS or JS, carries both ESP tokens and no others, has literal alt text on all eight images with no token in any of them, and its six story cards diff clean against card 1.
