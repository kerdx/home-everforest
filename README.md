<div align="center">

# Everforest for Home Assistant

**A calm, nature-inspired interface for Home Assistant.**

[![HACS Custom](https://img.shields.io/badge/HACS-Custom-41BDF5.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=kerdx&repository=home-everforest&category=theme)
[![Release](https://img.shields.io/github/v/release/kerdx/home-everforest)](https://github.com/kerdx/home-everforest/releases/latest)
[![Last commit](https://img.shields.io/github/last-commit/kerdx/home-everforest)](https://github.com/kerdx/home-everforest/commits/main)

</div>

Everforest is a theme-only customization for Home Assistant. Choose **Everforest Light** or **Everforest Dark** in your user profile. No runtime dependencies are required.

## Features

- Two coordinated light and dark themes, selectable per user.
- Nature-inspired colors for common Home Assistant surfaces, text, and active states.
- Optional theme tokens for Bubble Card; Bubble Card is not needed to use the themes.
- Straightforward HACS or manual installation.

## Visual previews

The images below are **static concept mockups generated for this project**, not screenshots of a Home Assistant instance.

| Everforest Light | Everforest Dark |
| --- | --- |
| ![Everforest Light static concept mockup](assets/everforest-light-preview.png) | ![Everforest Dark static concept mockup](assets/everforest-dark-preview.png) |

## Palette

| Theme | Background | Surface 1 | Surface 2 | Accent |
| --- | --- | --- | --- | --- |
| Everforest Light | `#fdf6e3` | `#f4f0d9` | `#efebd4` | `#3a94c5` |
| Everforest Dark | `#2d353b` | `#343f44` | `#3d484d` | `#7fbbb3` |

## Accessibility

Both themes are measured against WCAG 2.2: **4.5:1** for text (SC 1.4.3) and **3:1** for non-text such as icons, borders, focus rings and chart strokes (SC 1.4.11).

The ratios are computed for the **real pair each token is used in**, so they do not all share one background:

- state, text, focus-ring and primary-ramp colours are checked against the page, surface and card backgrounds of their theme, and the weakest of the three is what the tables report;
- header, sidebar, switch, filled-button and Bubble Card pairs are each checked against their own single background, which the row states;
- label badges need their own note, because `ha-label-badge` has three distinct pairs (see below);
- chart strokes are checked against the card, which is where they are drawn.

Each ratio measures the **actual foreground/background pair** used by the frontend; the token's role depends on the component. For example, state colours are compared as foregrounds on the page, while badge colours and switch tracks are compared as fills with their text or surrounding surface. Some tokens are used in more than one direction; any remaining low-contrast pair is called out under [Known limits](#known-limits). All figures were computed from the YAML with a relative-luminance script; nothing was verified on a running Home Assistant instance.

### Everforest Light

| Token | Before | After | Use / contrast pair |
| --- | --- | --- | --- |
| `primary-color` | `#3a94c5` · 2.81:1 | `#2b708e` · 4.59:1 | links, icons and sliders on the page/surface/card |
| `text-primary-color` | `#1e2326` on `#3a94c5` · 4.70:1 | `#ffffff` on `#2b708e` · 5.51:1 | text on primary fills |
| `error-color` | `#e67e80` · 2.28:1 | `#c8272a` · 4.63:1 | error text on the page/surface/card |
| `warning-color` | `#e69875` · 1.92:1 | `#ad4b1f` · 4.60:1 | warning text on the page/surface/card |
| `success-color` | `#a7c080` · 1.67:1 | `#5a6f37` · 4.65:1 | success text on the page/surface/card |
| `state-unavailable-color` | `#a6b0a0` · 1.87:1 | `#616c5a` · 4.61:1 | unavailable icons on the page/surface/card |
| `disabled-text-color` | `#a6b0a0` · 1.87:1 | `#7a8872` · 3.13:1 | disabled controls (exempt under SC 1.4.3) |
| `switch-checked-color` / `-track-color` | `#a7c080` · 1.67:1 | `#728d46` · 3.12:1 | switch track on the page/surface/card (legacy token) |
| `label-badge-red/green/yellow/blue` | chip 1.82–3.38:1 | chip 5.51–5.58:1 | chip label text on the badge colour |
| `graph-color-2`…`graph-color-5` | 1.52–2.28:1 | 3.11–3.13:1 | chart strokes on the card |
| `ha-color-focus` | not set | `#2b708e` · 4.59:1 | focus ring on the page/surface/card |
| `ha-color-on-primary-loud` | not set (stock white) | `#ffffff` · 5.51:1 | filled-button text on `ha-color-primary-40` |

`primary-color` is now aligned with `ha-color-primary-40`, which is where Home Assistant Core 2026.10.1 derives it from; `accent-color` stays `#3a94c5`, so Light deliberately has a darker primary than its accent. `text-primary-color` is white so it remains legible on that darker primary fill. `info-color` (`#2b708e` · 4.59:1) already met the text target and was left unchanged. For status and graph colours adjusted for contrast, the existing hue family was preserved where possible: for example, `warning-color` stays orange (`#e69875` → `#ad4b1f`, hue 18.6°), while `label-badge-yellow` stays in the yellow/ochre family it shares with `graph-color-3`.

### Everforest Dark

| Token | Before | After | Use / contrast pair |
| --- | --- | --- | --- |
| `error-color` | `#e67e80` · 3.43:1 | `#eda2a3` · 4.61:1 | error text on the page/surface/card |
| `warning-color` | `#e69875` · 4.08:1 | `#e9a688` · 4.60:1 | warning text on the page/surface/card |
| `info-color` | `#7fbbb3` · 4.33:1 | `#88c0b8` · 4.60:1 | info text (ANSI log colours) and icons on the page/surface/card |
| `state-unavailable-color` | `#859289` · 2.90:1 | `#8b978f` · 3.10:1 | unavailable icons on the page/surface/card |
| `disabled-text-color` | `#859289` · 2.90:1 | `#8b978f` · 3.10:1 | disabled controls (exempt under SC 1.4.3) |
| `sidebar-selected-text/-icon-color` | `#7fbbb3` · 4.33:1 | `#8ac2ba` · 4.71:1 | text and icon on the selected row |
| `ha-label-badge-label-color` | white · 1.82–2.74:1 | `#1e2326` · 5.79–8.70:1 | chip label text on the badge colour |

`success-color` (`#a7c080` · 4.70:1) already met the text target and was left unchanged, as were `graph-color-4` (`#e69875` · 4.08:1) and `graph-color-5` (`#e67e80` · 3.43:1), which are chart strokes and only need 3:1. Lightening error, warning and info also improved those colours as backgrounds, so the dark ink `text-primary-color` (`#2d353b`) now measures **6.10–6.23:1** against the four fills. Only `ha-assist-chat.ts:959-961` actually lays that ink on one of them; see [Known limits](#known-limits).

### The three label badge pairs

`ha-label-badge` renders three separate foreground/background combinations, and they are measured separately here:

1. **Circle value text** — `label-badge-text-color` on `label-badge-background-color`: **4.66:1** Light, **5.57:1** Dark.
2. **Circle border** — `label-badge-red/green/yellow/blue/grey` against the card behind the badge: **4.59–4.66:1** Light, **3.43–5.16:1** Dark.
3. **Embedded chip label** — `ha-label-badge-label-color` on `label-badge-red/green/yellow/blue/grey`: white on **5.51–5.59:1** Light, `#1e2326` on **5.79–8.70:1** Dark.

The chip label defaults to `white` in the frontend. That is fine on Light's dark chips, but every Dark badge fill is a light Everforest colour, so white text would have failed there; Everforest Dark therefore sets `ha-label-badge-label-color` explicitly.

### Known limits

- **Dark link text on cards.** `--primary-color` (`#7fbbb3`) is the colour of anchors: `styles.ts:81` and `:170`, the `ha-card a` rules at `ha-config-device-page.ts:1872`, `ha-config-dashboard.ts:432` and `ha-config-system-navigation.ts:258`, and every markdown link through the `--markdown-link-color` fallback at `ha-markdown.ts:69`. Against the Dark card (`#3d484d`) it measures **4.33:1**, under the 4.5:1 text target; against the page (`#2d353b`) and the surface (`#343f44`) it measures **5.74:1** and **4.98:1**. Both values are unchanged palette values — Dark's accent *is* its primary (`accent-color`, `ha-color-primary-40`, `graph-color-1`, `label-badge-blue`, `state-icon-active-color` and `bubble-accent-color` are all `#7fbbb3`) — so the pair predates this work. Closing it would mean lightening that accent (for example to `#88c0b8`, the value `info-color` already uses, which reaches 4.60:1) across all of those keys to keep the palette coherent, and would move the Dark row of the palette table. That is a palette decision, so the shortfall is recorded here rather than changed silently.
- **Text on ANSI semantic fills.** The `.bg-*` rules in `ha-ansi-to-html` set only `background-color`, so log body text inherits `--primary-text-color` on top of the error/warning/success/info fills: **1.00–1.01:1** in Light and **1.73–1.77:1** in Dark. This pair already failed before these changes (**1.01–2.79:1** and **1.73–2.37:1**). It cannot be corrected with a single shared fill colour without making that same colour unreadable when used as text elsewhere. The explicit `ha-assist-chat` error pair now uses white `text-primary-color` on `error-color` and measures **5.56:1** in Light; the Dark pair remains above **6:1**.
- **Bubble Card accent on the card.** Light `bubble-accent-color` (`#3a94c5`, which follows `accent-color`, not `primary-color`) on `bubble-main-background-color` (`#f4f0d9`) is **2.94:1**, just under the 3:1 icon target. Both are documented palette values, so they were left unchanged.

## Install with HACS

Open the [Everforest HACS repository page](https://my.home-assistant.io/redirect/hacs_repository/?owner=kerdx&repository=home-everforest&category=theme), or add `kerdx/home-everforest` as a custom repository and select the **Theme** category. Install the theme, reload themes or restart Home Assistant, then choose **Everforest Light** or **Everforest Dark** in your user profile.

## Manual installation

1. Copy this repository's `themes/` directory into your Home Assistant configuration directory, so the themes are in `config/themes/`.
2. Add the following under the existing top-level `frontend:` key in `configuration.yaml`:

   ```yaml
   frontend:
     themes: !include_dir_merge_named themes
   ```

   If there is no `frontend:` key yet, add the complete snippet at the top level. Do not create a duplicate `frontend:` key.
3. Reload themes from **Developer Tools → YAML → Reload themes**, or restart Home Assistant.
4. Select **Everforest Light** or **Everforest Dark** in your user profile.

## Optional Bubble Card

Bubble Card is optional for the themes. Install Bubble Card separately only if you want to use Bubble Card cards; the included [demo dashboard](demo/dashboard.yaml) uses it for its light and climate examples. The demo also uses standard Home Assistant cards.

On a Bubble Card light button, `use_accent_color: true` opts into the theme accent:

```yaml
type: custom:bubble-card
card_type: button
entity: light.example
use_accent_color: true
```

The Bubble Card [v2.3.2 release notes](https://github.com/Clooos/Bubble-Card/releases/tag/v2.3.2) document `use_accent_color` under "Accent color for lights (Optional)". Use an up-to-date Bubble Card release; this setting is intended for light buttons, and can be left unset to preserve a light's own color.

In Bubble Card [v3.4.1](https://github.com/Clooos/Bubble-Card/tree/v3.4.1), the active button uses `bubble-button-accent-color` for its surface while the icon keeps `bubble-accent-color`. The theme defines the surface explicitly in both modes:

| Theme | Active surface | Icon | Contrast |
| --- | --- | --- | --- |
| Everforest Light | `#1e2326` | `#3a94c5` | 4.70:1 |
| Everforest Dark | `#425047` | `#7fbbb3` | 3.91:1 |

In Bubble Card v3.4.1, `bubble-button-accent-color` is also used as a slider-fill fallback. Bubble Card's token fallbacks have changed between releases, so other versions may render differently; these values describe the tested release, not a guarantee for every version.

Climate cards use a neutral surface with distinct heat and cool icon accents, rather than a heat- or cool-tinted background. These are theme-level defaults; dashboard card settings may override them. No card-mod setup is required for the theme's Bubble Card styling.

## Example dashboard

`demo/dashboard.yaml` is a complete Lovelace YAML dashboard example. Bubble Card is required only for its Bubble Card light and climate cards. Replace every listed placeholder entity ID with an entity from your own Home Assistant instance before using it:

- `weather.home`
- `climate.living_room`
- `light.living_room`
- `cover.garage_door`
- `sensor.living_room_humidity`

To load it as a YAML dashboard:

1. Copy `demo/dashboard.yaml` to `/config/dashboards/everforest-demo.yaml`.
2. Register it in `configuration.yaml`:

   ```yaml
   lovelace:
     dashboards:
       everforest-demo:
         mode: yaml
         title: Everforest Demo
         icon: mdi:palette
         show_in_sidebar: true
         filename: dashboards/everforest-demo.yaml
   ```

   If `lovelace:` already exists, merge `dashboards:` under it instead of creating a duplicate key.
3. Restart Home Assistant, install Bubble Card if you want to use the Bubble examples, and replace the placeholder entity IDs.

The example intentionally does not set a dashboard theme, so you can choose Everforest Light or Dark in your user profile.

The example contains no automations or schedules.

## Themes in Lovelace

This section describes how these themes behave in **Home Assistant Core 2026.10.1** and its bundled frontend **20260930.3**, which is the version the behaviour below was verified against. Theme composition is frontend logic and can change in later releases, so treat this as a description of the version named above rather than as a permanent guarantee.

### Where a theme comes from

Home Assistant picks the base theme for a user like this:

1. **User profile** (Profile → Theme) — if it names a theme, that theme is used. This is what these themes are designed for.
2. **Instance default** — used when the profile is left on *Use default*. It is set with the `frontend.set_theme` action and defaults to the stock Home Assistant theme.
3. **Per-view `theme:`** (and the `theme:` key on sections and on cards that support it) — overrides the result above for that element only.

**Everforest Light** defines only `modes.light` and **Everforest Dark** only `modes.dark`. In the version named above, the selected theme therefore also decides the active mode for that user: choosing Everforest Light forces light styling and choosing Everforest Dark forces dark styling, even when the browser or the profile prefers the other mode.

### Per-view `theme:` composes with the global mode

A view-level `theme:` does not restyle the whole dashboard. It is applied to that view's container alone, so the header, the sidebar, the dashboard tabs and every other view keep the globally active theme.

In the frontend named above, the view theme is combined with the **globally active mode**, not with the mode the view theme itself defines:

- Global mode dark, view theme without `modes.dark` (for example `theme: Everforest Light`): the view receives Home Assistant's stock dark variables, so it looks like the default Home Assistant dark theme rather than Everforest.
- Global mode light, view theme without `modes.light` (for example `theme: Everforest Dark`): that mode is not available, so the view keeps the globally active light theme.

This is the composition rule of that frontend, not a sign of a broken installation, and it applies to every single-mode theme, not only this one: a single-mode theme has no other mode to render on a view. If you want per-view themes that follow the active mode, use a theme that defines both `modes.light` and `modes.dark`. How a future frontend composes per-view themes is up to that release.

The [demo dashboard](demo/dashboard.yaml) deliberately sets no `theme:` key, so it follows the theme chosen in your user profile.

### Setting instance defaults with `frontend.set_theme`

`frontend.set_theme` is an admin action that sets the instance-wide default theme, used when a user leaves their profile on *Use default*:

```yaml
action: frontend.set_theme
data:
  name: Everforest Light
  name_dark: Everforest Dark
```

- `name` sets the default used in light mode; on its own it sets the light default.
- `name_dark` sets the default used in dark mode, and replaces the light default while the browser or the profile is in dark mode.
- At least one of `name` or `name_dark` is required. These two are the fields the action exposes in Home Assistant 2026.10.1.
- The literal string `none` clears a default again: `name_dark: "none"` drops the dark override so dark mode falls back to the light default, and `name: "none"` returns the light default to the stock Home Assistant theme. `default` is also accepted and selects the stock theme explicitly.
- Theme names must already be installed; the action rejects an unknown name.
- A theme chosen in a user's profile always wins over this default, and picking **Home Assistant** in the profile selects the stock theme directly instead of this default.

### The `ha-color-*` keys are a best-effort mapping

Both themes set a run of `ha-color-primary-05` … `ha-color-primary-95` and `ha-color-on-primary-loud`; Light additionally sets `ha-color-focus`, while Dark sets `ha-label-badge-label-color`. These are **not** documented theme keys. They are the internal CSS custom properties that the bundled frontend derives newer controls from, and Home Assistant Core 2026.10.1 maps several well-known keys onto them — for example `--primary-color: var(--ha-color-primary-40)`.

Every one of these keys was checked to exist in the bundled frontend **20260930.3** before it was used here, so the mapping is verified for that version only. These tokens are internal, undocumented and carry no stability promise: a later frontend may rename, split, drop or stop consuming them. If that happens, some controls may lose Everforest-specific colours or revert to Home Assistant defaults; recheck the mapping after frontend upgrades. In particular, do not assume Dark's badge-chip text will retain its contrast if `ha-label-badge-label-color` is no longer consumed. Do not treat these keys as a support guarantee from Home Assistant.

## Notes and contributions

- This repository provides themes, not dashboard cards or entity configurations.
- Appearance can vary with Home Assistant, card versions, and individual dashboard settings.
- Contributions and issue reports are welcome through this repository's [issues](https://github.com/kerdx/home-everforest/issues) and [pull requests](https://github.com/kerdx/home-everforest/pulls).
