# Color Format Reference Guide

## Overview
Different applications require different color format syntaxes. This guide provides a complete reference for all color formats used in the theme system.

## Format Types

### 1. Hex Format
Standard 6-digit hexadecimal color notation.

#### Basic Hex
```
#RRGGBB
```
- R, G, B are hex digits (0-9, A-F)
- Case insensitive
- Most common format

**Used in:**
- Walker CSS: `#89b4fa`
- Waybar CSS: `#cdd6f4`
- SwayOSD CSS: `#1e1e2e`
- Mako INI: `#282828`

#### Quoted Hex
```
"#RRGGBB"
```
**Used in:**
- Alacritty TOML: `"#24273a"`
- Btop theme: `"#1e1e2e"`

#### Hex with 0x Prefix
```
"0xRRGGBB"
```
**Used in:**
- Alacritty TOML (alternative): `"0x282828"`

### 2. RGB Function Format
RGB function notation without # prefix.

#### RGB Function (Hex Inside)
```
rgb(RRGGBB)
```
- No # prefix inside parentheses
- Hex digits for color values

**Used in:**
- Hyprland config: `rgb(89b4fa)`
- Hyprland config: `rgb(D8DEE9)`

### 3. RGBA Format
RGB with alpha channel for transparency.

#### RGBA Function
```
rgba(R,G,B,A)
```
- R, G, B: Decimal values (0-255)
- A: Alpha/opacity (0.0-1.0)
- Commas required between values

**Used in:**
- Hyprlock config: `rgba(30,30,46,0.9)`
- Hyprlock config: `rgba(255,255,255,1.0)`

### 4. RGB Triplet Format
Space-separated RGB values in quotes.

#### Quoted RGB Triplet
```
"R G B"
```
- R, G, B: Decimal values (0-255)
- Spaces between values
- Must be quoted

**Used in:**
- Btop theme (alternative): `"255 255 255"`

### 5. CSS Variable Format
CSS custom property definition.

#### @define-color
```css
@define-color name #RRGGBB;
```
- Standard CSS hex format
- Semicolon required
- No quotes around hex value

**Used in:**
- Walker CSS
- Waybar CSS
- SwayOSD CSS

## Format Conversion Reference

### Hex to RGB Decimal
```
#89b4fa → 137, 180, 250
```
- 89 (hex) = 137 (decimal)
- b4 (hex) = 180 (decimal)
- fa (hex) = 250 (decimal)

### RGB Decimal to Hex
```
137, 180, 250 → #89b4fa
```
- 137 (decimal) = 89 (hex)
- 180 (decimal) = b4 (hex)
- 250 (decimal) = fa (hex)

### Adding Transparency
```
#89b4fa → rgba(137,180,250,0.8)
```
Add alpha channel for 80% opacity

## Application-Specific Requirements

### Alacritty
```toml
# All valid formats:
color = "#89b4fa"
color = "0x89b4fa"
color = '#89b4fa'
```

### Btop
```bash
# All valid formats:
theme[color]="#89b4fa"
theme[color]="137 180 250"
```

### Hyprland
```conf
# Only valid format:
col.active_border = rgb(89b4fa)
```

### Hyprlock
```conf
# Only valid format:
$color = rgba(137,180,250,1.0)
```

### Mako
```ini
# Only valid format:
text-color=#89b4fa
```

### CSS Files (Walker, Waybar, SwayOSD)
```css
/* Only valid format: */
@define-color name #89b4fa;
```

### Neovim
```lua
-- Lua strings or tables:
colors = {
  bg = "#1e1e2e",
  fg = "#cdd6f4",
}
```

## Special Values

### Transparency
- Empty string `""` - Transparent/no color (Btop)
- `rgba(r,g,b,0.0)` - Fully transparent (Hyprlock)
- `rgba(r,g,b,1.0)` - Fully opaque (Hyprlock)

### Cell References
- `"CellForeground"` - Current cell foreground (Alacritty)
- `"CellBackground"` - Current cell background (Alacritty)

## Common Color Codes

### Dark Backgrounds
```
#1a1b26  Tokyo Night
#1e1e2e  Catppuccin Mocha
#282828  Gruvbox Dark
#2e3440  Nord Dark
#2f383e  Everforest Dark
```

### Light Backgrounds
```
#eff1f5  Catppuccin Latte
#faf4ed  Rose Pine Dawn
#fbf1c7  Gruvbox Light
#ffffff  Pure White
```

### Common Foregrounds
```
#cdd6f4  Catppuccin Text
#c0caf5  Tokyo Night Text
#ebdbb2  Gruvbox Text
#d8dee9  Nord Text
#d3c6aa  Everforest Text
```

### Popular Accent Colors
```
#89b4fa  Blue (Catppuccin)
#7aa2f7  Blue (Tokyo Night)
#a6e3a1  Green (Catppuccin)
#a7c080  Green (Everforest)
#cba6f7  Purple (Catppuccin)
#f38ba8  Red (Catppuccin)
#f9e2af  Yellow (Catppuccin)
```

## Validation Tools

### Hex Validation Regex
```regex
^#[0-9A-Fa-f]{6}$
```

### RGB Function Validation
```regex
^rgb\([0-9A-Fa-f]{6}\)$
```

### RGBA Function Validation
```regex
^rgba\(\d{1,3},\d{1,3},\d{1,3},(0|1|0?\.\d+)\)$
```

## Quick Conversion Script

```bash
#!/bin/bash
# Convert hex to RGB decimal
hex_to_rgb() {
  hex="${1#\#}"
  r=$((16#${hex:0:2}))
  g=$((16#${hex:2:2}))
  b=$((16#${hex:4:2}))
  echo "$r, $g, $b"
}

# Usage: hex_to_rgb "#89b4fa"
```

## Common Mistakes

1. **Missing # in CSS**: `color: 89b4fa` ❌ → `color: #89b4fa` ✅
2. **# in rgb()**: `rgb(#89b4fa)` ❌ → `rgb(89b4fa)` ✅
3. **Wrong decimal range**: `rgba(256,256,256,1)` ❌ → `rgba(255,255,255,1)` ✅
4. **Wrong alpha range**: `rgba(255,255,255,255)` ❌ → `rgba(255,255,255,1.0)` ✅
5. **Missing quotes**: `theme[color]=89b4fa` ❌ → `theme[color]="#89b4fa"` ✅
6. **Wrong separator**: `"255,255,255"` ❌ → `"255 255 255"` ✅ (Btop RGB)