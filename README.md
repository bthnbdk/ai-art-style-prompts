     1|# AI Art Style Prompt Library
     2|
     3|**314 art styles · 942 ready-to-use prompts** for AI image generation — each style ships with a sample image, a **high-CTR YouTube thumbnail prompt** and a **cinematic video-image prompt**, plus a bare style block you can drop into anything.
     4|
     5|**Live gallery → https://ai-art-style-prompts.netlify.app**
     6|
     7|---
     8|
     9|## What you get per style
    10|
    11|| Prompt | What it is | When to use it |
    12||---|---|---|
    13|| **Test prompt** | The exact prompt used for the sample image on the card (one fixed subject for the whole library) | Comparing styles, sanity-checking a model |
    14|| **YT thumbnail prompt** | One-shot high-CTR thumbnail recipe **with the video title rendered inside the image**: `{TITLE}` slot (2–3 words), dominant subject at 55–65% of the frame, upper-centre key feature, hard rim light, 2–3 colour zones + one accent, enormous ultra-bold outline+shadow title on the free side, 16:9 | YouTube thumbnails in any niche |
    15|| **Video image prompt** | Cinematic still recipe: wide establishing shot, subject on a third with look-space, three depth layers, calm lower third for subtitles, composition that survives a slow push-in and a 10% crop | B-roll, establishing shots, inserts for a video |
    16|| **Style block** | Motifs + palette + mood, model-agnostic | Dropping into your own prompt |
    17|
    18|The thumbnail and video prompts are **niche-agnostic** — they contain a `{SUBJECT}` / `{SETTING}` slot. Swap the slot for your topic; the style block and the CTR / cinematography scaffolding stay.
    19|
    20|## Why the samples are comparable
    21|
    22|All sample images were generated with:
    23|
    24|- **Model:** `gemini-2.5-flash-image` (Google Vertex AI), 1024×1024
    25|- **Same subject:** *"a lone figure standing in an open landscape"*
    26|- **Same lighting, composition and render instruction** on every card
    27|
    28|The **only variable is the style block**. Generate each style with a different subject and you end up comparing subjects, not styles.
    29|
    30|## The base template
    31|
    32|```
    33|{your subject}, {style block}
    34|Medium: {suggested medium}. Lighting: {your choice}. Composition: {your choice}. Rendering: sharp, high detail.
    35|--no watermark, text artefacts, muddy colour, extra limbs
    36|```
    37|
## The thumbnail recipe (applied in every “YT thumbnail” tab)

**One-shot, text included** — the video title is rendered inside the image. No empty safe zone, no editing step.

- **title text baked in:** the prompt asks for the exact `{TITLE}` string, letter-by-letter, in capitals, with no other lettering anywhere
- **keep the title 2–3 words, ALL CAPS (≈16 characters)** — this is the single biggest factor in spelling accuracy; six-word titles get mangled
- typography is forced to clean, upright, ultra-bold condensed sans — explicitly **not** pixelated, dripping, ornate, handwritten, stretched or rotated, so a stylised art style can't destroy legibility
- enormous title (cap height ≈20% of the frame), near-white fill + thick black outline + soft drop shadow so it reads over anything
- title occupies the left or right third — whichever side the subject does not — and stays clear of the bottom-right corner (duration badge)
- one dominant subject at 55–65% of the frame, key feature on the upper-centre third, clean background behind it, hard rim/back light
- 2–3 colour zones maximum, one complementary accent from the style palette
- must still read at **168×94 px**; each card carries a style-specific readability note (e.g. *"compress the brushwork into a few bold masses"*, *"flat vector masses read perfectly at small sizes"*)
- negative prompt bans misspelled text, garbled/gibberish lettering, duplicated titles and extra or missing characters

Verified renders from this exact template (16:9, title baked in): see [`img/examples/`](img/examples) — Film Noir “WHY IT FAILED”, 8-Bit NES “PLAY THIS NOW”, Brutalism “THE LAST CITY”. Expect to pick between 2–3 generations for a perfect take.
    50|
    51|## The video-image recipe (applied in every “Video image” tab)
    52|
    53|- cinematic **16:9 wide establishing shot**; also works for medium shots and detail inserts by swapping that line
    54|- subject on a third with look-space; three depth layers (foreground / midground / background)
    55|- soft key plus one practical accent, consistent light direction
    56|- **palette locked** to the style block — a repeated palette is what turns a style into channel identity
    57|- framed calm enough to survive a slow push-in (Ken Burns) and a 10% crop
    58|- calm, mid-tone lower third for subtitles
    59|- no text, logos, watermark, UI or busy high-frequency detail that breaks at 1080p
    60|
    61|## Niche matrix — same scaffolding, your subject
    62|
    63|| Niche | Subject slot example |
    64||---|---|
    65|| Gaming | `{a stylised game hero mid-action, a boss arena behind them}` |
    66|| Finance | `{a glowing candlestick chart, a city skyline at dusk}` |
    67|| Product | `{a phone floating in studio light, hands mid-unboxing}` |
    68|| History | `{a ruined castle at dusk, an old map with pins}` |
    69|| True crime | `{a rain-soaked alley at night, case files on a table}` |
    70|| Cooking | `{steam rising from a pan, ingredients in a flat-lay}` |
    71|| Travel | `{a cliff road at sunset, a crowded market alley}` |
    72|| Tech / AI | `{a server-room aisle, a glowing neural lattice}` |
    73|| Education | `{a swirling cloud of formulas, books and a desk lamp}` |
    74|| Fitness | `{an athlete mid-sprint, chalk dust in a gym}` |
    75|| Science | `{a microscope slide, a distant nebula}` |
    76|| Motivation | `{a lone climber on a ridge, a rooftop city view}` |
    77|
    78|## Data
    79|
    80|`data/styles.json` — the whole library (314 styles × 4 prompt fields):
    81|
    82|```json
    83|{
    84|  "generator": "Google Vertex AI · gemini-2.5-flash-image",
    85|  "subject": "a lone figure standing in an open landscape",
    86|  "count": 314,
    87|  "prompts_per_style": 3,
    88|  "styles": [
    89|    {
    90|      "id": 1,
    91|      "name": "Art Deco",
    92|      "group": "art-movement",
    93|      "source": "fandom-original",
    94|      "source_label": "Aesthetics Wiki",
    95|      "era": "1910s–1930s",
    96|      "origin": "Paris, France",
    97|      "medium": "lithograph / screenprinted poster, flat ink colour, sharp geometric edges",
    98|      "style_prompt": "Art Deco (1910s–1930s, Paris, France): ...",
    99|      "prompt": "{SUBJECT}, Art Deco ... (test prompt)",
   100|      "thumbnail_prompt": "{SUBJECT — your niche subject ...}, Art Deco ... (high-CTR recipe)",
   101|      "video_prompt": "{SETTING — your niche scene ...}, Art Deco ... (cinematic recipe)",
   102|      "negative_prompt": "watermark, text artefacts, muddy colour, extra limbs",
   103|      "image": "img/001_art-deco.jpg"
   104|    }
   105|  ]
   106|}
   107|```
   108|
   109|## Provenance (labelled on every card)
   110|
   111|| Label | Count | Meaning |
   112||---|---|---|
   113|| **Aesthetics Wiki** | 136 | Style motifs, palettes and mood lines taken from [aesthetics.fandom.com](https://aesthetics.fandom.com) — the original 96 from *Category:Art Movements*, 40 more from article infoboxes (`key_motifs` / `key_colours` / `key_values`). |
   114|| **Authored** | 166 | The style is a documented art/design/film tradition; the prompt text was written for this library from art-history knowledge. |
   115|| **Invented** | 12 | New styles invented for this library (Neural Bloom, Promptcore, Datamosh Rococo, Solastalgia, Zero-Gothic, Halide Dream, Chrome Nouveau, Chthonic Rococo, Terminal Romanticism, Botanica Machina, Ghostlight Noir, Anadolu Retro-Futurism). |
   116|
   117|## Groups
   118|
   119|`art-movement` (111) · `traditional` (35) · `architecture` (34) · `cinema` (22) · `design` (20) · `internet-aesthetic` (19) · `illustration` (19) · `photography` (17) · `gameart` (15) · `street` (10) · `invented` (12)
   120|
   121|## Files
   122|
   123|```
   124|index.html          the gallery (static, no build step, no dependencies)
   125|data/styles.json    all 314 styles × 3 prompts + style blocks (942 prompts total)
   126|img/                900×900 sample images (1 per style)
   127|```
   128|
   129|## License
   130|
   131|- **Prompt text, data and documentation: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)** — commercial use fine, remix fine, just credit this library.
   132|- **Sample images:** AI-generated with Google Vertex AI; see `LICENSE` for notes on the Aesthetics Wiki sourced entries.
   133|
   134|## Contributing
   135|
   136|Missing a style you love? Open an issue with the name, era, origin, motifs, palette and mood — or a PR against `data/styles.json` plus a sample image.
   137|
   138|---
   139|
   140|Hosted on Netlify · built and maintained by [@bthnbdk](https://github.com/bthnbdk)
   141|