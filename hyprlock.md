# Hyprlock Screen Lock Theme Configuration

## File Format
Configuration format with variable definitions using `$variable = value` syntax

## File Location
`theme-name/hyprlock.conf`

## Structure Template
```conf
$color = rgba(r,g,b,a)
$inner_color = rgba(r,g,b,a)
$outer_color = rgba(r,g,b,a)
$font_color = rgba(r,g,b,a)
$check_color = rgba(r,g,b,a)
```

## Variable Definitions

### Required Variables
- `$color` - Primary background color (usually semi-transparent)
- `$inner_color` - Inner element colors (input fields, etc.)
- `$outer_color` - Border/outline colors
- `$font_color` - Text color
- `$check_color` - Accent/highlight color (checkmarks, active elements)

## Color Format

**RGBA Format**: `rgba(r,g,b,a)`
- `r`, `g`, `b`: Color values (0-255)
- `a`: Alpha/transparency (0.0-1.0)
  - 0.0 = Fully transparent
  - 1.0 = Fully opaque
  - 0.5 = 50% transparent

## Examples

### Dark Theme with Transparency
```conf
$color = rgba(30,30,46,0.9)        # Dark background, 90% opaque
$inner_color = rgba(49,50,68,0.8)  # Slightly lighter, 80% opaque
$outer_color = rgba(137,180,250,1.0) # Blue border, fully opaque
$font_color = rgba(205,214,244,1.0)  # Light text, fully opaque
$check_color = rgba(166,227,161,1.0) # Green accent, fully opaque
```

### Light Theme
```conf
$color = rgba(239,241,245,0.95)    # Light background
$inner_color = rgba(220,224,232,0.9) # Slightly darker inner
$outer_color = rgba(30,102,245,1.0)  # Blue border
$font_color = rgba(76,79,105,1.0)    # Dark text
$check_color = rgba(64,160,43,1.0)   # Green check
```

### Minimal Dark
```conf
$color = rgba(0,0,0,0.8)           # Black with transparency
$inner_color = rgba(40,40,40,0.8)  # Dark gray
$outer_color = rgba(255,255,255,0.3) # White border, semi-transparent
$font_color = rgba(255,255,255,1.0)  # White text
$check_color = rgba(255,255,255,0.8) # White accent
```

## Color Selection Guidelines

### Background (`$color`)
- Use high transparency (0.7-0.95) to show wallpaper
- Dark themes: RGB values 0-50
- Light themes: RGB values 200-255

### Inner Color (`$inner_color`)
- Slightly different from background for depth
- Usually less transparent than background
- Should provide good contrast for input text

### Outer Color (`$outer_color`)
- Often uses theme accent color
- Usually fully opaque (1.0) for clear borders
- Should be visible against various wallpapers

### Font Color (`$font_color`)
- High contrast against inner_color
- Always fully opaque (1.0) for readability
- Light themes: Dark colors
- Dark themes: Light colors

### Check Color (`$check_color`)
- Accent color for active elements
- Often green for "success" indication
- Can match theme primary accent
- Usually fully opaque

## Transparency Best Practices

1. **Wallpaper Visibility**: Keep main background at 0.7-0.9 alpha
2. **Readability**: Text and borders should be 0.9-1.0 alpha
3. **Depth**: Use varying transparency levels to create depth
4. **Testing**: Test against multiple wallpapers

## Common Patterns

### Monochromatic
All colors from same hue family with varying brightness/transparency

### Accent Border
Neutral backgrounds with colorful border matching theme accent

### Gradient Effect
Using transparency to create subtle gradient appearance

## Integration Tips

The lock screen colors should:
- Allow wallpaper to show through
- Maintain readability in all lighting conditions
- Match the overall theme aesthetic
- Use consistent transparency levels with other UI elements

## System Integration

### Main Configuration Structure
The main hyprlock configuration at `config/hypr/hyprlock.conf` sources the theme file and provides:
- A default background using `$color`
- A standard input-field positioned at center (0, 0)
- Default animations and authentication settings

**Important**: The main config creates its own input-field, so theme files should NOT define additional input-field elements to avoid duplicates.

### Theme File Best Practices

#### Variable Requirements
Theme files MUST define these variables for the main config:
```conf
$color = rgba(r,g,b,a)         # Background color
$inner_color = rgba(r,g,b,a)   # Input field interior
$outer_color = rgba(r,g,b,a)   # Input field border
$font_color = rgba(r,g,b,a)    # Input text color
$check_color = rgba(r,g,b,a)   # Success indicator
```

#### Custom Elements
Theme files can add custom elements like:
- Time/date displays
- ASCII art or decorative elements
- Custom backgrounds with wallpapers
- Additional labels or shapes

## Element Positioning Guidelines

### Coordinate System
- Center screen = (0, 0)
- Positive Y = above center
- Negative Y = below center
- Main password input is always at (0, 0)

### Safe Positioning Zones
To avoid overlap with the main password input field:

```
               Y = +300 to +400    ← ASCII Art / Decorative
               Y = +200 to +250    ← Date
               Y = +100 to +150    ← Time
               Y = +50 to +80      ← Secondary info
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
               Y = 0               ← PASSWORD INPUT (600x100px)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
               Y = -100 to -200    ← Status/error messages
               Y = -250 to -350    ← Footer elements
```

### Recommended Spacing
- **Time Display**: Position +120 to +150 (large, prominent)
- **Date Display**: Position +200 to +250 (above time)
- **ASCII Art**: Position +280 to +400 (top of screen)
- **Footer Text**: Position -150 to -250 (below input)

## ASCII Art Implementation

### Multi-line ASCII Requirements
hyprlock labels display only single lines. For multi-line ASCII art, create separate label elements:

```conf
# ASCII Art - Line 1
label {
    monitor =
    text = ╱╲╱╲╱╲╱╲
    color = $text_color
    font_size = 18
    font_family = JetBrainsMono Nerd Font Mono
    position = 0, 320
    halign = center
    valign = center
}

# ASCII Art - Line 2
label {
    monitor =
    text = ╲╱╲╱╲╱╲╱
    color = $text_color
    font_size = 18
    font_family = JetBrainsMono Nerd Font Mono
    position = 0, 300
    halign = center
    valign = center
}
```

### ASCII Art Guidelines
1. **Positioning**: Use Y positions 280-400 for top placement
2. **Spacing**: 20-pixel gaps between lines (320, 300, 280, etc.)
3. **Font**: Use `JetBrainsMono Nerd Font Mono` for consistent spacing
4. **Color**: Match theme secondary or accent colors
5. **Size**: 16-18px font size works well for most ASCII art

## Background Configuration

### Wallpaper vs Solid Color
Theme files can override the default solid background:

```conf
background {
    monitor =
    path = ~/.config/omarchy/themes/theme-name/backgrounds/wallpaper.jpg
    blur_size = 5
    blur_passes = 2
    noise = 0.01
    contrast = 0.96
    brightness = 0.88
    vibrancy = 0.15
}
```

### Background Best Practices
- **Blur**: 4-8 pixels for readability
- **Brightness**: 0.8-0.9 to prevent overwhelming text
- **Contrast**: 0.9-1.0 for clear definition
- **Vibrancy**: 0.1-0.2 for subtle color enhancement

## Testing and Validation

### Element Overlap Check
1. Test lock screen activation
2. Verify password input is clearly visible and functional
3. Ensure ASCII art doesn't interfere with input
4. Check time/date positioning across different screen sizes
5. Test against various wallpapers if using transparency

### Multi-line ASCII Verification
1. Count ASCII art lines in design
2. Create one label per line
3. Position from top to bottom with 20px spacing
4. Test complete display renders properly

## Validation Checklist
- [ ] All 5 required variables defined
- [ ] RGBA values in correct range (0-255 for RGB, 0.0-1.0 for alpha)
- [ ] NO input-field elements in theme file
- [ ] Text has sufficient contrast against background
- [ ] Border color visible against typical wallpapers
- [ ] ASCII art positioned above Y=+200
- [ ] Time/date positioned to avoid password input overlap
- [ ] Multi-line ASCII implemented as separate labels
- [ ] Element spacing maintains readability
- [ ] Colors align with overall theme palette