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

## 📦 Installation (.crx file)

1. Download the latest release:
   👉 [theme.crx](https://github.com/AREKKUZZERA/Chrome-Dark-Pink/releases/download/1.4.0/theme.crx)

2. Open Chrome and go to:
   `chrome://extensions/`

3. Enable **Developer mode** (toggle in the top-right corner)

4. Drag & drop the `theme.crx` file into the Extensions page

5. Confirm installation when prompted

---

## 📸 Preview

![Preview](preview.png)

---

## 🎨 Theme Configuration

Chrome themes are defined entirely inside a single `manifest.json` file. There are no HTML, CSS, or JavaScript files — only color values, image paths, and display properties.

```json
"theme": {
  "colors":     { },
  "tints":      { },
  "properties": { },
  "images":     { }
}
```

| Section | Purpose |
|---------|---------|
| `colors` | Direct RGB color values for UI elements |
| `tints` | HSL filters applied on top of colors or images |
| `properties` | Layout and display options for the New Tab Page |
| `images` | Optional background images for frame, toolbar, and NTP |

---

## 🧩 `colors`

All values use `[R, G, B]` format where each channel is an integer from `0` to `255`.  
An optional 4th value `[R, G, B, A]` sets opacity (0–255), though most keys ignore it.

---

### 🪟 Window frame

The frame is the outermost chrome of the browser window — the area behind and around the tabs, above the toolbar. On Windows it also contains the title bar and window control buttons (minimize / maximize / close).

| Key | Value | Description |
|-----|-------|-------------|
| `frame` | `[18, 18, 20]` | Frame color when the window is **active and focused**. This is the primary color of the entire top area of the browser |
| `frame_inactive` | `[24, 24, 28]` | Frame color when the window is **open but not focused** (e.g. another app is in front). Slightly lighter than `frame` to signal the inactive state |
| `frame_incognito` | `[22, 22, 26]` | Frame color for an **incognito window** when it is active and focused |
| `frame_incognito_inactive` | `[20, 20, 24]` | Frame color for an **incognito window** when it is unfocused |

> **Tip:** Keep these values close to each other for a subtle transition. Large contrast between `frame` and `frame_inactive` creates a noticeable flash when switching windows.

---

### 🔧 Toolbar

The toolbar sits directly below the tab strip. It contains the address bar (omnibox), navigation arrows, and extension icons.

| Key | Value | Description |
|-----|-------|-------------|
| `toolbar` | `[31, 31, 31]` | Background color of the toolbar. Also used as the background for the omnibox. Setting this slightly lighter than `frame` creates visible separation between the frame and toolbar layers |
| `toolbar_button_icon` | `[214, 72, 142]` | Color of icon glyphs inside toolbar buttons — navigation arrows, the extension puzzle icon, the three-dot menu icon. Does not affect the button background, only the icon itself |

---

### 🗂️ Tabs

Chrome has several tab states: the active (foreground) tab in the focused window, inactive (background) tabs, and all of the above in incognito mode or an unfocused window. Each combination can be styled independently.

#### Tab text

Controls the color of text (page title) rendered inside each tab.

| Key | Value | Description |
|-----|-------|-------------|
| `tab_text` | `[195, 195, 202]` | Text color of the **active (selected) tab** in a focused window. Should have enough contrast against `toolbar` |
| `tab_background_text` | `[214, 72, 142]` | Text color of all **inactive tabs** in a focused window |
| `tab_background_text_inactive` | `[160, 50, 105]` | Text color of inactive tabs when the **window is unfocused**. Dimmed compared to `tab_background_text` |
| `tab_background_text_incognito` | `[214, 72, 142]` | Text color of inactive tabs inside an **incognito window** |
| `tab_background_text_incognito_inactive` | `[160, 50, 105]` | Text color of inactive tabs in an **incognito window that is unfocused** |

#### Tab background

Controls the background fill of the inactive tab strip area.

| Key | Value | Description |
|-----|-------|-------------|
| `background_tab` | `[24, 24, 26]` | Background fill of **inactive tabs** in a focused window. Slightly lighter than `frame` separates them visually from the frame layer |
| `background_tab_inactive` | `[20, 20, 22]` | Background fill of inactive tabs when the **window is unfocused** |
| `background_tab_incognito` | `[26, 22, 30]` | Background fill of inactive tabs in an **incognito window**. Subtle purple tint distinguishes incognito from normal mode |
| `background_tab_incognito_inactive` | `[22, 20, 26]` | Background fill of inactive tabs in an **incognito window that is unfocused** |

> **Note:** The active tab has no explicit background color key. Its background is derived from `toolbar`, making it appear to merge seamlessly with the toolbar below.

---

### 🔖 Bookmarks bar

The bookmarks bar appears below the toolbar when enabled via `Ctrl+Shift+B`.

| Key | Value | Description |
|-----|-------|-------------|
| `bookmark_text` | `[220, 220, 220]` | Color of bookmark labels, folder names, and the "Other bookmarks" text. The bar background itself inherits from `toolbar` |

---

### 🔲 Buttons

| Key | Value | Description |
|-----|-------|-------------|
| `button_background` | `[18, 18, 20]` | Background color of the window control buttons (minimize, maximize, close) in the top-right corner on **Windows and Linux**. Set equal to `frame` so the buttons blend into the frame and the only visible elements are the icon glyphs themselves. Has no effect on macOS (uses native traffic-light buttons) |

---

### 🆕 New Tab Page (NTP)

The New Tab Page is what Chrome shows when you open a new tab. It contains the Google search bar, shortcuts, and optionally a background image.

| Key | Value | Description |
|-----|-------|-------------|
| `ntp_background` | `[18, 18, 20]` | Solid background color of the New Tab Page. Visible when no `theme_ntp_background` image is set, or as the color behind a transparent/partial image |
| `ntp_text` | `[238, 238, 238]` | Color of general text on the NTP — shortcut labels, "Most visited" titles, and other UI text |
| `ntp_link` | `[245, 40, 154]` | Color of clickable links on the NTP. In current Chrome versions this primarily affects the Doodle and some informational text |
| `ntp_header` | `[245, 40, 154]` | Color of section headers on the NTP (e.g. "Most visited"). Often matches `ntp_link` for a consistent accent palette |

---

## 🎛️ `tints`

Tints are **HSL color filters** applied multiplicatively on top of a color or image. They shift the appearance without replacing it entirely.

**Format:** `[Hue, Saturation, Lightness]`

| Channel | Range | Special value | Effect |
|---------|-------|---------------|--------|
| Hue | `0.0` – `1.0` | `-1.0` | Rotates the hue. `0.0` and `1.0` are both red. `0.5` is cyan |
| Saturation | `0.0` – `1.0` | `-1.0` | `0.0` = fully desaturated (grayscale), `0.5` = unchanged, `1.0` = fully saturated |
| Lightness | `0.0` – `1.0` | `-1.0` | `0.0` = black, `0.5` = unchanged, `1.0` = white |

Use `-1.0` on any individual channel to leave it untouched.

| Key | Value | Description |
|-----|-------|-------------|
| `buttons` | `[0.92, 0.85, 0.55]` | Shifts toolbar button icons toward a warm pink hue. Hue `0.92` maps to the pink/magenta region of the color wheel. Saturation `0.85` keeps icons vivid. Lightness `0.55` brightens them slightly above neutral |
| `frame` | `[-1.0, -1.0, -1.0]` | Disables tinting entirely — Chrome uses the raw `colors.frame` RGB value as-is |
| `frame_inactive` | `[-1.0, -1.0, -1.0]` | Same — preserves `colors.frame_inactive` without modification |
| `frame_incognito` | `[-1.0, -1.0, -1.0]` | Same — preserves `colors.frame_incognito` |
| `frame_incognito_inactive` | `[-1.0, -1.0, -1.0]` | Same — preserves `colors.frame_incognito_inactive` |
| `background_tab` | `[-1.0, -1.0, -1.0]` | Disables tinting on inactive tab backgrounds — preserves `colors.background_tab` |

> ⚠️ **Important:** If a `tints` entry for `frame` exists but uses non-neutral values, Chrome applies it *over* your `colors.frame` and the final rendered color will differ from what you specified. Always set frame tints to `[-1.0, -1.0, -1.0]` unless you intentionally want to shift the frame color via HSL.

---

## ⚙️ `properties`

Properties control layout and display options for the New Tab Page. They have no effect unless a `theme_ntp_background` image is defined in `images`.

| Key | Current value | All options | Description |
|-----|---------------|-------------|-------------|
| `ntp_background_alignment` | `"center"` | `"bottom"` `"center"` `"top"` `"left"` `"right"` | Where to anchor the NTP background image within the page. Supports combined values like `"bottom right"` |
| `ntp_background_repeat` | `"no-repeat"` | `"no-repeat"` `"repeat"` `"repeat-x"` `"repeat-y"` | Whether to tile the NTP background image. Use `"no-repeat"` for full-page wallpapers, `"repeat"` for patterns or textures |
| `ntp_logo_alternate` | `0` | `0` `1` | Selects which Google logo variant to show on the NTP. `0` = default color logo, `1` = white monochrome logo (better contrast on dark backgrounds) |

---

## 🖼️ `images` *(optional)*

Image paths are relative to the theme folder root. All images must be **PNG** files.

| Key | Description |
|-----|-------------|
| `theme_frame` | Background image for the frame — active window. Tiled horizontally from the top-left. Overlays on top of `colors.frame` |
| `theme_frame_inactive` | Frame image — inactive window |
| `theme_frame_incognito` | Frame image — incognito, active |
| `theme_frame_incognito_inactive` | Frame image — incognito, inactive |
| `theme_frame_overlay` | Overlay image composited *on top of* `theme_frame`. Useful for adding a subtle pattern without replacing the base color |
| `theme_frame_overlay_inactive` | Frame overlay — inactive window |
| `theme_toolbar` | Background image for the toolbar area. Overrides `colors.toolbar` |
| `theme_tab_background` | Image applied to inactive tab backgrounds. Tiled to fit |
| `theme_tab_background_inactive` | Inactive tab background — unfocused window |
| `theme_tab_background_incognito` | Inactive tab background — incognito |
| `theme_tab_background_incognito_inactive` | Inactive tab background — incognito, unfocused |
| `theme_ntp_background` | Background image for the New Tab Page. Position and tiling are controlled by `properties` |
| `theme_ntp_attribution` | Small attribution logo placed in the bottom-right corner of the NTP (e.g. photographer credit). Recommended size: 200×100 px or smaller |
| `theme_button_background` | Background image for toolbar buttons. Rarely used |
| `theme_window_control_background` | Background image for window control buttons (Windows only) |

---

## ⚠️ Notes

- **macOS:** `button_background` and `theme_window_control_background` have no effect — macOS uses its own native traffic-light buttons regardless of theme settings.
- **Active tab background:** There is no dedicated key for the active tab's background. Chrome derives it from `toolbar`, making the active tab appear to seamlessly extend into the toolbar.
- **Omnibox colors:** The omnibox (address bar) background and text colors are not directly configurable via the theme manifest in current Chrome versions. They inherit from `toolbar` and system contrast settings.
- **Non-configurable elements:** Tab separators, scrollbars, focus rings, and context menus are rendered by the OS or Chrome's internal UI engine and cannot be themed.
- **Tints override colors:** If a tint key exists with non-neutral values, it is applied *after* the color value and will change the final rendered color. Always use `[-1.0, -1.0, -1.0]` to fully disable a tint.
- **Images override colors:** Any `images` entry will take visual priority over the corresponding `colors` entry. The color remains as a fallback for areas not covered by the image.
