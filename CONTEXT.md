# Theme System Documentation

## TASK (for AI Assistants)

- Role: Act as a theme designer/implementer for the Omarchy system, proposing a cohesive color palette and applying it consistently across all documented applications.
- Inputs: User preferences (mood, dark/light, contrast), any starting colors or wallpaper, and this directory's references.
- References: `color-theory.md` (palette math and psychology), `creating-themes.md` (steps and files), `color-formats.md` (app-specific formats), app guides (`alacritty.md`, `waybar.md`, `mako.md`, `walker.md`, `swayosd.md`, `btop.md`, `hyprland.md`, `hyprlock.md`, `neovim.md`, `icons.md`, `backgrounds.md`).

- Process:
  1. Define a palette from `color-theory.md`: pick a base hue and harmony (complementary, triadic, analogous, or monochrome); set neutrals; choose accent(s); target accessibility contrast.
  2. Map palette to semantic roles: Background, Foreground, Accent, Border, Selected, Inactive, plus semantic colors (Error, Warning, Success, Info).
  3. Apply colors per app using `creating-themes.md` and app guides, respecting `color-formats.md`. Keep accent consistent; avoid unrelated config changes.
  4. Validate: contrast ratios, readability, and visual consistency across apps; include light mode via `light.mode` if appropriate.
  5. Deploy: copy the full theme folder to the Config path for the current OS user.
     
     ```bash
     cp -r /home/$(whoami)/PersonalRepos/omarchy/themes/your-theme-name /home/$(whoami)/.config/omarchy/themes/
     ```

- Deliverables (when responding):
  - Palette spec: list each role with Hex and HSL and a 1-line rationale per key color.
  - File creation: Theme file creation for the relevant files (`alacritty.toml`, `waybar.css`, `mako.ini`, `walker.css`, `swayosd.css`, `btop.theme`, `hyprland.conf`, `hyprlock.conf`, `neovim.lua`, `icons.theme`, `backgrounds/`).
  - Validation notes: Perform a review of all created files to confirm theme alignment, perform contrast checks, and any follow-ups.

- Constraints:
  - Maintain accessibility (aim ≥ 4.5:1 for body text). Do not alter unrelated behavior.

- Output structure:
  1) Palette
  2) Mapping per file
  3) Edits
  4) Validation
  5) Next steps


This directory contains detailed instructions for modifying and creating themes in the Omarchy theme system. Each file documents the specific requirements, patterns, and best practices for theming different applications.

## Theme Locations

Themes exist in two locations:
1. **Repository**: `/$GIT_REPO/` - For theme development and version control
2. **Config**: `/home/$YOURUSERNAME/.config/omarchy/themes/` - Active themes used by the system

To make a theme available for use, copy it from the repository to the config location:
```bash
cp -r ~/$GIT_REPO ~/.config/omarchy/themes/
```

## Theme Structure Overview

Each theme folder follows a consistent structure:
```
theme-name/
├── alacritty.toml      # Terminal emulator colors
├── backgrounds/        # Wallpaper images (1-3 files)
├── btop.theme         # System monitor colors
├── hyprland.conf      # Window manager border colors
├── hyprlock.conf      # Lock screen colors
├── icons.theme        # Icon theme selection
├── mako.ini          # Notification daemon colors
├── neovim.lua        # Neovim colorscheme configuration
├── swayosd.css       # On-screen display colors
├── walker.css        # Application launcher colors
├── waybar.css        # Status bar colors
└── light.mode        # (Optional) Light theme indicator
```

## Files in this Directory

### **📖 Essential References**
- `color-theory.md` - **Comprehensive color theory guide for theme design**
- `creating-themes.md` - Complete step-by-step theme creation guide
- `color-formats.md` - Color format reference for all applications

### **🎨 Application-Specific Guides**
- `alacritty.md` - Terminal emulator theming guide
- `btop.md` - System monitor theming guide
- `hyprland.md` - Window manager theming guide
- `hyprlock.md` - Lock screen theming guide
- `icons.md` - Icon theme configuration guide
- `mako.md` - Notification daemon theming guide
- `neovim.md` - Neovim editor theming guide
- `swayosd.md` - On-screen display theming guide
- `walker.md` - Application launcher theming guide
- `waybar.md` - Status bar theming guide
- `backgrounds.md` - Wallpaper guidelines

## Quick Start

### **🎨 For Designing Color Palettes**
1. **Start with `COLORTHEORY.md`** - Learn mathematical color relationships and harmony principles
2. Analyze existing themes to understand successful color patterns
3. Use the mathematical formulas to generate complementary, triadic, or analogous palettes
4. Test accessibility and contrast ratios

### **🛠️ For Implementing Themes**
1. Copy an existing theme folder as a template
2. Apply your color palette using the application-specific guides
3. Follow `creating-themes.md` for complete step-by-step implementation
4. Test your theme by switching to it and ensure consistency across all applications

## Common Color Roles

Most themes define these core colors:
- **Background** - Primary background color
- **Foreground** - Primary text color
- **Accent** - Primary accent/highlight color
- **Border** - UI element borders
- **Selected** - Selected/active elements
- **Inactive** - Disabled/unfocused elements

## Color Format Quick Reference

- **Hex**: `#RRGGBB` or `"#rrggbb"`
- **Hex with prefix**: `0xRRGGBB`
- **RGB function**: `rgb(rrggbb)` (no # prefix)
- **RGBA**: `rgba(r,g,b,a)` where values are 0-255 and alpha is 0.0-1.0
- **RGB triplet**: `"r g b"` where values are 0-255
- **CSS variable**: `@define-color name #RRGGBB;`