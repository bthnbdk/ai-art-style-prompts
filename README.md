# AI Art Style Prompt Library

**337 art styles · 1011 ready-to-use prompts** for AI image generation — each style ships with a sample image, a **title-driven high-CTR YouTube thumbnail prompt** and a **cinematic video-image prompt**, plus a bare style block you can drop into anything.

**Live gallery → https://ai-art-style-prompts.netlify.app**

---

## What you get per style

| Prompt | What it is | When to use it |
|---|---|---|
| **Test prompt** | The exact prompt used for the sample image on the card (one fixed subject for the whole library) | Comparing styles, sanity-checking a model |
| **YT thumbnail prompt** | One-shot high-CTR thumbnail recipe that takes **one input only: your video title**. The subject, its action, the props, the environment, the camera angle/lens, the lighting and the colour mood are all **derived from the title's meaning**; the title is then **rendered inside the image** (`{TITLE}` slot, 2–3 words), dominant subject at 55–65% of the frame, upper-centre key feature, hard rim light, 2–3 colour zones + one accent, enormous ultra-bold outline+shadow title on the free side, 16:9 | YouTube thumbnails in any niche — paste a title, generate |
| **Video image prompt** | Cinematic still recipe: wide establishing shot, subject on a third with look-space, three depth layers, calm lower third for subtitles, composition that survives a slow push-in and a 10% crop | B-roll, establishing shots, inserts for a video |
| **Style block** | Motifs + palette + mood, model-agnostic | Dropping into your own prompt |

The **thumbnail recipe is title-driven**: nothing in the scene is hard-coded, so the same style block plus a different title gives a different subject, setting and camera. The **video prompt** stays niche-agnostic through a single `{SETTING}` slot. In both cases the style block and the CTR / cinematography scaffolding stay.

## Why the samples are comparable

All sample images were generated with:

- **Model:** `gemini-2.5-flash-image` (Google Vertex AI), 1024×1024
- **Same subject:** *"a lone figure standing in an open landscape"*
- **Same lighting, composition and render instruction** on every card

One documented exception: **Continuous Line Drawing** is generated with *"flat even paper-white light, no cast shadow, no tonal shading"* instead of the shared chiaroscuro line — a single-contour drawing has no tonal shading, so the shared lighting line would contradict the style. Both the sample image and the prompt shown on the card use that override.

The **only variable is the style block**. Generate each style with a different subject and you end up comparing subjects, not styles.

## The base template

```
{your subject}, {style block}
Medium: {suggested medium}. Lighting: {your choice}. Composition: {your choice}. Rendering: sharp, high detail.
--no watermark, text artefacts, muddy colour, extra limbs
```

## The thumbnail recipe (applied in every “YT thumbnail” tab)

**One-shot, title-driven, text included** — you supply **one input: your video title**. The whole image is derived from it, and the title is rendered inside the frame. No empty safe zone, no editing step.

- **the scene comes from the title:** read `{TITLE}` and infer what the video is about, then derive the subject, its action and expression, the props, the environment and time of day, the camera angle / framing / lens / distance, the light direction and the colour mood — nothing in the scene is hard-coded, which is why the same style block with a different title yields a completely different image
- **step-structured prompt:** STEP 1 invent the image from the title → STEP 2 render it in the style block → STEP 3 burn the title in → STEP 4 apply the CTR rules. Models follow this far more reliably than one long paragraph
- **title text baked in:** the prompt asks for the exact `{TITLE}` string, letter-by-letter, in capitals, with no other lettering anywhere
- **keep the title 2–3 words, ALL CAPS (≈16 characters)** — this is the single biggest factor in spelling accuracy; six-word titles get mangled
- typography is forced to clean, upright, ultra-bold condensed sans — explicitly **not** pixelated, dripping, ornate, handwritten, stretched or rotated, so a stylised art style can't destroy legibility
- enormous title (cap height ≈20% of the frame), near-white fill + thick black outline + soft drop shadow so it reads over anything
- title occupies the left or right third — whichever side the derived subject does not — and stays clear of the bottom-right corner (duration badge)
- the derived subject at 55–65% of the frame, key feature on the upper-centre third, clean background behind it, hard rim/back light
- 2–3 colour zones maximum, one complementary accent from the style palette
- must still read at **168×94 px**; each card carries a style-specific readability note (e.g. *"compress the brushwork into a few bold masses"*, *"flat vector masses read perfectly at small sizes"*)
- negative prompt bans misspelled text, garbled/gibberish lettering, duplicated titles and extra or missing characters

Verified renders from this exact template (16:9, title baked in): see [`img/examples/`](img/examples). One Brutalism style block with three different titles gives three different scenes — shattered concrete tower (“WHY IT FAILED”), a vast concrete gateway (“THE LAST CITY”), a blocky concrete mech (“PLAY THIS NOW”) — plus Film Noir “I WAS WRONG” / “FREE MONEY” and Ukiyo-e “SILENT RAIN”. Expect to pick between 2–3 generations for a perfect take.

## The video-image recipe (applied in every “Video image” tab)

- cinematic **16:9 wide establishing shot**; also works for medium shots and detail inserts by swapping that line
- subject on a third with look-space; three depth layers (foreground / midground / background)
- soft key plus one practical accent, consistent light direction
- **palette locked** to the style block — a repeated palette is what turns a style into channel identity
- framed calm enough to survive a slow push-in (Ken Burns) and a 10% crop
- calm, mid-tone lower third for subtitles
- no text, logos, watermark, UI or busy high-frequency detail that breaks at 1080p

## Niche matrix — same scaffolding, your subject

| Niche | Subject slot example |
|---|---|
| Gaming | `{a stylised game hero mid-action, a boss arena behind them}` |
| Finance | `{a glowing candlestick chart, a city skyline at dusk}` |
| Product | `{a phone floating in studio light, hands mid-unboxing}` |
| History | `{a ruined castle at dusk, an old map with pins}` |
| True crime | `{a rain-soaked alley at night, case files on a table}` |
| Cooking | `{steam rising from a pan, ingredients in a flat-lay}` |
| Travel | `{a cliff road at sunset, a crowded market alley}` |
| Tech / AI | `{a server-room aisle, a glowing neural lattice}` |
| Education | `{a swirling cloud of formulas, books and a desk lamp}` |
| Fitness | `{an athlete mid-sprint, chalk dust in a gym}` |
| Science | `{a microscope slide, a distant nebula}` |
| Motivation | `{a lone climber on a ridge, a rooftop city view}` |

## Data

`data/styles.json` — the whole library (337 styles × 4 prompt fields):

```json
{
  "generator": "Google Vertex AI · gemini-2.5-flash-image",
  "subject": "a lone figure standing in an open landscape",
  "count": 337,
  "prompts_per_style": 3,
  "styles": [
    {
      "id": 1,
      "name": "Art Deco",
      "group": "art-movement",
      "source": "fandom-original",
      "source_label": "Aesthetics Wiki",
      "era": "1910s–1930s",
      "origin": "Paris, France",
      "medium": "lithograph / screenprinted poster, flat ink colour, sharp geometric edges",
      "style_prompt": "Art Deco (1910s–1930s, Paris, France): ...",
      "prompt": "{SUBJECT}, Art Deco ... (test prompt)",
      "thumbnail_prompt": "YouTube thumbnail, 16:9 ... The video title is exactly: \"{TITLE}\" \n STEP 1 — INVENT THE ENTIRE IMAGE FROM THE TITLE ALONE ... STEP 2 — RENDER THAT SCENE IN THIS EXACT ART STYLE: Art Deco ... STEP 3 — BURN THE TITLE IN ... STEP 4 — MAKE IT CLICK ... (title-driven high-CTR recipe)",
      "video_prompt": "{SETTING — your niche scene ...}, Art Deco ... (cinematic recipe)",
      "negative_prompt": "watermark, text artefacts, muddy colour, extra limbs",
      "image": "img/001_art-deco.jpg"
    }
  ]
}
```

## Provenance (labelled on every card)

| Label | Count | Meaning |
|---|---|---|
| **Aesthetics Wiki** | 136 | Style motifs, palettes and mood lines taken from [aesthetics.fandom.com](https://aesthetics.fandom.com) — the original 96 from *Category:Art Movements*, 40 more from article infoboxes (`key_motifs` / `key_colours` / `key_values`). |
| **Authored** | 189 | The style is a documented art/design/film/technique tradition; the prompt text was written for this library from art-history and craft knowledge — includes the whole **Drawing & sketching** group and the whiteboard / explainer-doodle / storyboard / blueprint / wireframe / marker-rendering techniques. |
| **Invented** | 12 | New styles invented for this library (Neural Bloom, Promptcore, Datamosh Rococo, Solastalgia, Zero-Gothic, Halide Dream, Chrome Nouveau, Chthonic Rococo, Terminal Romanticism, Botanica Machina, Ghostlight Noir, Anadolu Retro-Futurism). |

## Groups

`art-movement` (111) · `traditional` (35) · `architecture` (34) · `design` (25) · `cinema` (24) · `internet-aesthetic` (21) · `illustration` (21) · `photography` (17) · `gameart` (15) · `drawing` (12) · `invented` (12) · `street` (10)

The **Drawing & sketching** group covers working-media techniques rather than historical movements: graphite pencil, charcoal, sanguine chalk, silverpoint, coloured pencil, soft pastel, kraft paper, continuous line, cross-hatch pen, ballpoint biro, ink & wash urban sketching and chalkboard chalk. The board-and-explainer side sits next to its relatives — **Whiteboard Animation** and **Doodle Explainer** under illustration, **Dry-Erase Glass Board**, **Technical Blueprint**, **UX Wireframe Sketch**, **Marker Rendering** and **Sticky-Note Doodle Notes** under graphic design, **Storyboard Marker Sketch** and **Rough Animatic Pencil** under cinema, and **Studyblr Notes** / **MS Paint Doodle** under internet aesthetic.

## Files

```
index.html          the gallery (static, no build step, no dependencies)
data/styles.json    all 337 styles × 3 prompts + style blocks (1011 prompts total)
img/                900×900 sample images (1 per style)
img/examples/       16:9 verified thumbnail renders (title-driven recipe, title baked in)
```

## License

- **Prompt text, data and documentation: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)** — commercial use fine, remix fine, just credit this library.
- **Sample images:** AI-generated with Google Vertex AI; see `LICENSE` for notes on the Aesthetics Wiki sourced entries.

## Contributing

Missing a style you love? Open an issue with the name, era, origin, motifs, palette and mood — or a PR against `data/styles.json` plus a sample image.

---

Hosted on Netlify · built and maintained by [@bthnbdk](https://github.com/bthnbdk)
