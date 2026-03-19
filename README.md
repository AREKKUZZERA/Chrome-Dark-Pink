# 🌑 Chrome Dark Pink Theme

<p align="left">
  <a href="https://developer.chrome.com/docs/extensions/develop/ui/themes">
    <img src="https://img.shields.io/badge/Chrome%20Themes-Docs-blue?style=for-the-badge&logo=google-chrome" />
  </a>
  <a href="https://developer.chrome.com/docs/extensions/reference/manifest">
    <img src="https://img.shields.io/badge/Manifest-Reference-green?style=for-the-badge&logo=json" />
  </a>
  <a href="https://source.chromium.org/chromium/chromium/src/+/main:chrome/browser/themes/theme_properties.h">
    <img src="https://img.shields.io/badge/Theme%20API-Chromium-orange?style=for-the-badge&logo=google" />
  </a>
</p>

Minimalistic dark theme for Google Chrome with pink accents.

---

## 📦 Installation

1. Click → **[Download raw file](https://github.com/AREKKUZZERA/Chrome-Dark-Pink/blob/main/manifest.json)**
2. Go to `chrome://extensions/`
3. Enable **Developer mode**
4. Click **Load unpacked**
5. Select the folder containing the downloaded `manifest.json`

---

## 📸 Preview

![Preview](preview.png)

---

## 🎨 Theme Configuration

### Structure

```json
"theme": {
  "colors":     { ... },
  "tints":      { ... },
  "properties": { ... }
}
```

---

## 🧩 `colors`

All color values use `[R, G, B]` format (0–255).

### Window frame

| Key | Value | Description |
|-----|-------|-------------|
| `frame` | `[18, 18, 20]` | Frame color — active window |
| `frame_inactive` | `[24, 24, 28]` | Frame color — inactive window |
| `frame_incognito` | `[22, 22, 26]` | Frame color — incognito, active |
| `frame_incognito_inactive` | `[20, 20, 24]` | Frame color — incognito, inactive |

### Toolbar

| Key | Value | Description |
|-----|-------|-------------|
| `toolbar` | `[31, 31, 31]` | Toolbar background (below tabs) |
| `toolbar_button_icon` | `[214, 72, 142]` | Toolbar icon color (extensions, menu) |

### Tabs

| Key | Value | Description |
|-----|-------|-------------|
| `tab_text` | `[195, 195, 202]` | Text on the active tab |
| `tab_background_text` | `[214, 72, 142]` | Text on inactive tabs |
| `tab_background_text_inactive` | `[160, 50, 105]` | Inactive tab text — unfocused window |
| `tab_background_text_incognito` | `[214, 72, 142]` | Inactive tab text — incognito |
| `tab_background_text_incognito_inactive` | `[160, 50, 105]` | Inactive tab text — incognito, unfocused |
| `background_tab` | `[24, 24, 26]` | Background of inactive tabs |
| `background_tab_inactive` | `[20, 20, 22]` | Inactive tabs — unfocused window |
| `background_tab_incognito` | `[26, 22, 30]` | Inactive tabs — incognito |
| `background_tab_incognito_inactive` | `[22, 20, 26]` | Inactive tabs — incognito, unfocused |

### Bookmarks bar

| Key | Value | Description |
|-----|-------|-------------|
| `bookmark_text` | `[220, 220, 220]` | Text color on the bookmarks bar |

### Buttons

| Key | Value | Description |
|-----|-------|-------------|
| `button_background` | `[18, 18, 20]` | Window control buttons background (minimize / maximize / close). Matches `frame` to blend in seamlessly |

### New Tab Page (NTP)

| Key | Value | Description |
|-----|-------|-------------|
| `ntp_background` | `[18, 18, 20]` | New Tab Page background color |
| `ntp_text` | `[238, 238, 238]` | Main text on the New Tab Page |
| `ntp_link` | `[245, 40, 154]` | Link color on the New Tab Page |
| `ntp_header` | `[245, 40, 154]` | Section header color on the New Tab Page |

---

## 🎛️ `tints`

Tints are applied as HSL filters on top of existing colors.  
Format: `[Hue, Saturation, Lightness]` — values from `0.0` to `1.0`.  
Use `-1.0` on any channel to leave it unchanged.

| Key | Value | Description |
|-----|-------|-------------|
| `buttons` | `[0.92, 0.85, 0.55]` | Applies a pink-warm hue to toolbar buttons |
| `frame` | `[-1.0, -1.0, -1.0]` | No tint — uses raw `colors.frame` value |
| `frame_inactive` | `[-1.0, -1.0, -1.0]` | No tint |
| `frame_incognito` | `[-1.0, -1.0, -1.0]` | No tint |
| `frame_incognito_inactive` | `[-1.0, -1.0, -1.0]` | No tint |
| `background_tab` | `[-1.0, -1.0, -1.0]` | No tint — uses raw `colors.background_tab` |

> Setting all frame tints to `-1.0` is important — without it, Chrome may override your RGB colors with its own HSL adjustments.

---

## ⚙️ `properties`

| Key | Value | Options | Description |
|-----|-------|---------|-------------|
| `ntp_background_alignment` | `"center"` | `"bottom"` `"center"` `"top"` `"left"` `"right"` | Alignment of the NTP background image |
| `ntp_background_repeat` | `"no-repeat"` | `"no-repeat"` `"repeat"` `"repeat-x"` `"repeat-y"` | Tiling of the NTP background image |
| `ntp_logo_alternate` | `0` | `0` `1` | Use the white Google logo on NTP (`1` = white, `0` = default) |

---

## ⚠️ Notes

- Some elements (tab separators, scrollbars, focus rings) are **not directly configurable** and depend on contrast between surrounding colors.
- Adding `theme_ntp_background` as an image in `images` will activate `ntp_background_alignment` and `ntp_background_repeat`.
- `tints` act as filters — they override `colors` unless all channels are set to `-1.0`.