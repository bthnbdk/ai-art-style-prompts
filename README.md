# AI Art Style Prompt Library

**314 ready-to-use art style prompts** for AI image generation — each one with a sample image so you can see what the prompt actually does before you use it.

**Live gallery → https://ai-art-style-prompts.netlify.app**

---

## What this is

A curated, machine-readable library of art style prompts spanning art movements, architecture, traditional arts, cinema, illustration and comics, game art, graphic design, photography, street art, internet aesthetics — plus 12 styles invented specifically for this library.

Every style is written as a **style block** (motifs + palette + mood) that you paste into your own prompt. Nothing depends on a specific model.

## Why the samples are comparable

All sample images were generated with:

- **Model:** `gemini-2.5-flash-image` (Google Vertex AI), 1024×1024
- **Same subject:** *"a lone figure standing in an open landscape"*
- **Same lighting, composition and render instruction** for every style

The **only variable is the style block**. That is the whole point: if you generate each style with a different subject, you end up comparing subjects instead of styles.

## How to use a style

```
{your subject}, {style block}
Medium: {suggested medium}. Lighting: {your choice}. Composition: {your choice}. Rendering: sharp, high detail.
--no watermark, text artefacts, muddy colour, extra limbs
```

Example (Bauhaus):

```
a lone figure standing in an open landscape, Bauhaus (1919-1933, Weimar, Germany): Geometric shapes (circles, squares, triangles); industrial materials (steel, glass, concrete); simple geometric forms; sans-serif typography; lack of ornamentation; clean lines; abstract forms. Palette: Primary colors (red, yellow, blue), black, white, gray. Mood: Unification of art and industry, form follows function, rationality, simplicity
Medium: lithograph / screenprinted poster, flat ink colour, sharp geometric edges. Lighting: soft directional daylight, subtle chiaroscuro, long shadows. Composition: centered lone figure, wide open landscape, generous negative space, horizon at lower third. Rendering: sharp, high detail.
--no watermark, text artefacts, muddy colour, extra limbs
```

The gallery has a **Copy prompt** button (full prompt) and **Copy style only** (just the style block) on every card.

## Data

`data/styles.json` — the whole library:

```json
{
  "generator": "Google Vertex AI · gemini-2.5-flash-image",
  "subject": "a lone figure standing in an open landscape",
  "count": 314,
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
      "prompt": "a lone figure standing in an open landscape, Art Deco ...",
      "negative_prompt": "watermark, text artefacts, muddy colour, extra limbs",
      "image": "img/001_art-deco.jpg"
    }
  ]
}
```

## Provenance (labelled on every card)

| Label | Count | Meaning |
|---|---|---|
| **Aesthetics Wiki** | 136 | Style motifs, palettes and mood lines were taken from [aesthetics.fandom.com](https://aesthetics.fandom.com) — the original 96 from *Category:Art Movements*, 40 more from article infoboxes (`key_motifs` / `key_colours` / `key_values`). |
| **Authored** | 166 | The style is a documented art/design/film tradition; the prompt text was written for this library from art-history knowledge. |
| **Invented** | 12 | A new style invented for this library (Neural Bloom, Promptcore, Datamosh Rococo, Solastalgia, Zero-Gothic, Halide Dream, Chrome Nouveau, Chthonic Rococo, Terminal Romanticism, Botanica Machina, Ghostlight Noir, Anadolu Retro-Futurism). |

No motifs were invented for the wiki-sourced entries; the invented entries are explicitly marked.

## Groups

`art-movement` (111) · `traditional` (35) · `architecture` (34) · `cinema` (22) · `design` (20) · `internet-aesthetic` (19) · `illustration` (19) · `photography` (17) · `gameart` (15) · `street` (10) · `invented` (12)

## Files

```
index.html          the gallery (static, no build step, no dependencies)
data/styles.json    all 314 styles, machine-readable
img/                900×900 sample images (1 per style)
```

## License

- **Prompt text, data and documentation: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)** — use them commercially, remix them, just credit this library.
- **Sample images:** AI-generated with Google Vertex AI; treat them as public-domain-style outputs. Check your own provider's terms if you republish.

## Contributing

Missing a style you love? Open an issue with the name, era, origin, motifs, palette and mood — or a pull request against `data/styles.json` plus a sample image.

---

Hosted on Netlify · built and maintained by [@bthnbdk](https://github.com/bthnbdk)
