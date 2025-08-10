# Omarchy Theme Development

Start here if you're creating or iterating on a desktop theme for the Omarchy system.

## Where to Begin

1. Read `CONTEXT.md` first. It defines a concise TASK for assistants and contributors and links all relevant guides.
2. Use `color-theory.md` to build a palette (math-driven, accessible, and consistent).
3. Follow `creating-themes.md` to implement the palette across applications.

## Recommended Workflow

1. Define intent: dark/light, mood, contrast requirements, and any wallpaper inspiration.
2. Create a palette using a harmony (complementary, triadic, analogous, or monochrome) and set neutrals.
3. Map palette to roles: Background, Foreground, Accent, Border, Selected, Inactive, plus Error/Warning/Success/Info.
4. Implement per app using the app guides and `color-formats.md` for exact syntax.
5. Validate contrast (target ≥ 4.5:1 for body text) and consistency across terminal, bar, notifications, launcher, OSD, monitor, WM, lock screen, editor, and icons.
6. Optionally add `light.mode` if building a light theme variant.

## Quick Color Terminology (optional, memorable)

- Hue: the color angle (0–360°). Choose a base hue first.
- Saturation: color intensity (0–100%). Lower = more neutral.
- Lightness: brightness (0–100%). Controls readability most.
- Complement: base hue + 180°. High-contrast accent.
- Triadic: base ±120°. Two balanced secondary accents.
- Analogous: base ±30°. Smooth, harmonious neighbors.
- Neutral: low-saturation tones for backgrounds and borders.

## Next Steps

- After palette selection, implement following `creating-themes.md` and validate against the checklist.
- Keep edits focused on colors; avoid changing unrelated settings.


