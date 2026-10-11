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

The active-surface treatment for this option requires Bubble Card **3.3.0 or newer**. It uses the theme's dark on-state surface while retaining the teal icon. This setting is intended for light buttons; leave it unset to preserve a light's own color.

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

## Notes and contributions

- This repository provides themes, not dashboard cards or entity configurations.
- Appearance can vary with Home Assistant, card versions, and individual dashboard settings.
- Contributions and issue reports are welcome through this repository's [issues](https://github.com/kerdx/home-everforest/issues) and [pull requests](https://github.com/kerdx/home-everforest/pulls).
