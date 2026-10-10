# AI Art Style Prompt Library

**314 art styles · 942 ready-to-use prompts** for AI image generation — each style ships with a sample image, a **high-CTR YouTube thumbnail prompt** and a **cinematic video-image prompt**, plus a bare style block you can drop into anything.

**Live gallery → https://ai-art-style-prompts.netlify.app**

---

## What you get per style

| Prompt | What it is | When to use it |
|---|---|---|
| **Test prompt** | The exact prompt used for the sample image on the card (one fixed subject for the whole library) | Comparing styles, sanity-checking a model |
| **YT thumbnail prompt** | High-CTR thumbnail recipe: dominant subject at 60–70% of the frame, key feature on the upper-centre third, hard rim light, 2–3 colour zones + one accent, calm text-safe zone, no baked-in text, 16:9 | YouTube thumbnails in any niche |
| **Video image prompt** | Cinematic still recipe: wide establishing shot, subject on a third with look-space, three depth layers, calm lower third for subtitles, composition that survives a slow push-in and a 10% crop | B-roll, establishing shots, inserts for a video |
| **Style block** | Motifs + palette + mood, model-agnostic | Dropping into your own prompt |

The thumbnail and video prompts are **niche-agnostic** — they contain a `{SUBJECT}` / `{SETTING}` slot. Swap the slot for your topic; the style block and the CTR / cinematography scaffolding stay.

## Why the samples are comparable

All sample images were generated with:

- **Model:** `gemini-2.5-flash-image` (Google Vertex AI), 1024×1024
- **Same subject:** *"a lone figure standing in an open landscape"*
- **Same lighting, composition and render instruction** on every card

The **only variable is the style block**. Generate each style with a different subject and you end up comparing subjects, not styles.

## The base template

```
{your subject}, {style block}
Medium: {suggested medium}. Lighting: {your choice}. Composition: {your choice}. Rendering: sharp, high detail.
--no watermark, text artefacts, muddy colour, extra limbs
```

## The thumbnail recipe (applied in every “YT thumbnail” tab)

Optimised for click-through, not for beauty:

- one dominant subject filling 60–70% of the frame
- key feature (face / hero object / point of interest) on the upper-centre third
- clean, uncluttered background directly behind it — strong foreground/background separation
- hard rim/back light to cut the subject out of the background; deep shadow against bright specular highlight
- **2–3 colour zones maximum**, one complementary accent from the style palette
- **text-safe zone:** the right third and lower strip stay calm so you can place a headline later
- **no text, letters, numbers or logos in the generated image** — models render gibberish; add the headline yourself
- must still read at **168×94 px**; style-specific readability note included per card (e.g. *"compress the brushwork into a few bold masses"*, *"flat vector masses read perfectly at small sizes"*)

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

`data/styles.json` — the whole library (314 styles × 4 prompt fields):

```json
{
  "generator": "Google Vertex AI · gemini-2.5-flash-image",
  "subject": "a lone figure standing in an open landscape",
  "count": 314,
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
      "thumbnail_prompt": "{SUBJECT — your niche subject ...}, Art Deco ... (high-CTR recipe)",
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
| **Authored** | 166 | The style is a documented art/design/film tradition; the prompt text was written for this library from art-history knowledge. |
| **Invented** | 12 | New styles invented for this library (Neural Bloom, Promptcore, Datamosh Rococo, Solastalgia, Zero-Gothic, Halide Dream, Chrome Nouveau, Chthonic Rococo, Terminal Romanticism, Botanica Machina, Ghostlight Noir, Anadolu Retro-Futurism). |

## Groups

`art-movement` (111) · `traditional` (35) · `architecture` (34) · `cinema` (22) · `design` (20) · `internet-aesthetic` (19) · `illustration` (19) · `photography` (17) · `gameart` (15) · `street` (10) · `invented` (12)

## Files

```
index.html          the gallery (static, no build step, no dependencies)
data/styles.json    all 314 styles × 3 prompts + style blocks (942 prompts total)
img/                900×900 sample images (1 per style)
```

## License

- **Prompt text, data and documentation: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)** — commercial use fine, remix fine, just credit this library.
- **Sample images:** AI-generated with Google Vertex AI; see `LICENSE` for notes on the Aesthetics Wiki sourced entries.

## Contributing

Missing a style you love? Open an issue with the name, era, origin, motifs, palette and mood — or a PR against `data/styles.json` plus a sample image.

---

Hosted on Netlify · built and maintained by [@bthnbdk](https://github.com/bthnbdk)
