# Chrome Home — Themes

This folder contains pre-made themes for the Chrome Home extension.

---

## Folder Structure

```
themes/
  themes.json        ← Registry of all available themes
  1/
    theme.json       ← Theme settings
    background.jpg   ← Theme background image
  2/
    theme.json
    background.jpg
  ...
```

Themes are numbered starting from **1**. Theme 1 is the default theme.

---

## Adding a New Theme

1. Create a new numbered folder (e.g. `themes/2/`).
2. Add a `background.jpg` (the background image for the theme).
3. Add a `theme.json` (see schema below).
4. Register the theme in `themes/themes.json` by appending an entry.

### `themes/themes.json` — Registry

An array of theme descriptor objects:

```json
[
  { "id": 1, "name": "Default" },
  { "id": 2, "name": "My Theme" }
]
```

| Field | Type   | Description                          |
|-------|--------|--------------------------------------|
| `id`  | number | Unique theme number (folder name)    |
| `name`| string | Display name shown in the UI         |

---

## `theme.json` Schema

All fields are optional. Omitted fields keep the user's existing value.

```json
{
  "name": "My Theme",

  "bgColor": "#003056",
  "highlightColor": "#be9da8",
  "textColor": "#eeb8b7",

  "clockSize": "8",
  "clockX": "0",
  "clockY": "0",

  "fontUrl": "https://fonts.googleapis.com/css2?family=Inter&display=swap",
  "fontFamily": "'Inter', sans-serif",

  "bgBrightness": "0",
  "bgImageEnabled": true,
  "bgImageCap": "1080p",

  "tabName": "",
  "favicon": ""
}
```

### Field Reference

| Field            | Type             | Description                                                                |
|------------------|------------------|----------------------------------------------------------------------------|
| `name`           | string           | Human-readable theme name                                                  |
| `bgColor`        | CSS hex color    | Page background color (shown when no image, or behind the image)           |
| `highlightColor` | CSS hex color    | Accent / highlight color used for interactive elements                     |
| `textColor`      | CSS hex color    | Primary text color                                                         |
| `clockSize`      | numeric string   | Clock font size in `rem` units (range: `2`–`14`, default `"8"`)            |
| `clockX`         | numeric string   | Horizontal offset of the clock in pixels (range: `-300`–`300`)             |
| `clockY`         | numeric string   | Vertical offset of the clock in pixels (range: `-300`–`300`)               |
| `fontUrl`        | URL string       | URL of a CSS font stylesheet (e.g. Google Fonts). Empty string = no custom font |
| `fontFamily`     | CSS font stack   | CSS `font-family` value applied to the whole page                          |
| `bgBrightness`   | numeric string   | Background image brightness adjustment (range: `-100`–`100`, default `"0"`) |
| `bgImageEnabled` | boolean          | Whether the background image is shown (`true`) or hidden (`false`)         |
| `bgImageCap`     | `"default"` \| `"1080p"` \| `"1440p"` \| `"4K"` | Maximum resolution cap when processing the background image. `"default"` saves the image without any scaling or re-encoding. |
| `tabName`        | string           | Browser tab title. Empty string = `"New Tab"`                             |
| `favicon`        | URL string       | URL of a custom favicon image. Empty string = browser default              |

### `background.jpg`

Place the theme's background image as `background.jpg` inside the theme folder.
It is used as the page background whenever the theme is applied.
JPEG format is required; recommended size is 1920×1080 or larger.
