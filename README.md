<div align="center">

# Everforest for Home Assistant

**A calm, nature-inspired interface in two selectable color themes.**

[![HACS Custom](https://img.shields.io/badge/HACS-Custom-41BDF5.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=kerdx&repository=home-everforest&category=theme)
[![Release](https://img.shields.io/github/v/release/kerdx/home-everforest)](https://github.com/kerdx/home-everforest/releases/latest)
[![Last commit](https://img.shields.io/github/last-commit/kerdx/home-everforest)](https://github.com/kerdx/home-everforest/commits/main)

</div>

Everforest is a theme-only customization for Home Assistant. Choose **Everforest Light** or **Everforest Dark** from your user profile. No runtime dependencies are required.

## Features

- Two independently selectable light and dark variants.
- Coordinated colors for common Home Assistant surfaces, text, and active states.
- Optional theme tokens for Bubble Card; Bubble Card itself is not required.
- No extra runtime dependencies.

## Palette

| Theme | Background | Surface 1 | Surface 2 | Accent |
| --- | --- | --- | --- | --- |
| Everforest Light | `#fdf6e3` | `#f4f0d9` | `#efebd4` | `#3a94c5` |
| Everforest Dark | `#2d353b` | `#343f44` | `#3d484d` | `#7fbbb3` |

## Install with HACS

Use the [HACS repository link](https://my.home-assistant.io/redirect/hacs_repository/?owner=kerdx&repository=home-everforest&category=theme) to open this repository in HACS. Alternatively, add `kerdx/home-everforest` as a custom repository and choose the **Theme** category. Install it, reload themes or restart Home Assistant, then select **Everforest Light** or **Everforest Dark** in your user profile.

## Manual setup

1. Copy the repository's `themes/` directory into your Home Assistant configuration directory as `config/themes/`.
2. Add this to `configuration.yaml`:

   ```yaml
   frontend:
     themes: !include_dir_merge_named themes
   ```

   If `frontend:` already exists, add `themes` beneath it instead of creating a second `frontend:` section.
3. Reload themes using **Developer Tools → YAML → Reload themes**, or restart Home Assistant.
4. In your user profile, select **Everforest Light** or **Everforest Dark**.

## Optional Bubble Card

Bubble Card is optional. The theme includes Bubble Card styling tokens, but Bubble Card must be installed separately to use Bubble Card dashboard cards. Theme token support is distinct from per-card dashboard configuration.

For an individual Bubble Card light button, `use_accent_color: true` opts into the theme accent:

```yaml
type: custom:bubble-card
card_type: button
entity: light.example
use_accent_color: true
```

With `use_accent_color: true` on Bubble Card **3.3.0 or newer**, an active light button uses the theme's dark on-state surface while retaining its teal icon. Leave the option unset to preserve the light's own color.

Climate cards use neutral surfaces, with distinct heat and cool icon accents. The theme sets the climate background to transparent, so the card uses its surrounding neutral surface rather than a heat/cool-tinted background. These are theme-level defaults; dashboard card settings may override them. The Bubble Card theme customizations do not require card-mod.

## Notes and contributions

- This repository provides themes only; it does not install or configure dashboard cards.
- Appearance can vary with Home Assistant and card versions, as well as individual dashboard configuration.
- Contributions and issue reports are welcome through this repository's [issues](https://github.com/kerdx/home-everforest/issues) and [pull requests](https://github.com/kerdx/home-everforest/pulls).
