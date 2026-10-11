# Everforest for Home Assistant

An independent, Everforest-themed Home Assistant theme with two separately selectable variants:

- **Everforest Light** — warm cream backgrounds, light surfaces, and muted gray text.
- **Everforest Dark** — charcoal backgrounds, green-gray surfaces, and warm text.

The theme uses Home Assistant theme variables and requires no additional runtime dependencies.

## Bubble Card

Bubble Card support is optional. The theme provides Bubble Card's documented global CSS variables for a coordinated appearance; Bubble Card is not required to use the theme. For a single Bubble light button, you can optionally use the theme accent instead of the light's own color:

```yaml
type: custom:bubble-card
card_type: button
entity: light.example
use_accent_color: true
```

This per-card option is optional and leaves other cards free to display their actual light or RGB colors.

Bubble Card v3.3.0 or newer applies the dark Everforest on-state surface to this button while keeping its icon teal. Earlier versions may fall back to the lighter accent color.

On Bubble Card v3.3.0 or newer, climate heat and cool states use distinct icon accents while the card background stays neutral for readability.

## Manual installation

1. Copy the `themes/` directory into `config/themes/` in your Home Assistant configuration.
2. Add the following to `configuration.yaml` if it is not already present:

   ```yaml
   frontend:
     themes: !include_dir_merge_named themes
   ```

   If `frontend:` already exists, add the `themes` entry under it rather than creating a second `frontend:` section.
3. Reload themes from **Developer Tools → YAML → Reload themes**, or restart Home Assistant.
4. Select **Everforest Light** or **Everforest Dark** in your user profile's theme settings.

## HACS installation

Add this public GitHub repository as a custom repository in HACS and select the **Theme** category. Install the theme, reload themes or restart Home Assistant, then select the desired variant in your user profile.
