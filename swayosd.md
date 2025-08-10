# SwayOSD On-Screen Display Theme Configuration

## File Format
CSS format with `@define-color` variable definitions

## File Location
`theme-name/swayosd.css`

## Structure Template
```css
@define-color background-color #hexcode;
@define-color border-color #hexcode;
@define-color label #hexcode;
@define-color image #hexcode;
@define-color progress #hexcode;
```

## Color Properties

### Required Colors
- `background-color` - OSD popup background
- `border-color` - OSD popup border
- `label` - Text/label color
- `image` - Icon/image color
- `progress` - Progress bar fill color

## Color Format
Standard CSS hex format: `#RRGGBB`
- Always use 6-digit hex codes
- Include the `#` prefix
- Case insensitive
- Semicolon required at end of each line

## Common Patterns

### Unified Foreground
Most themes use the same color for label, image, and progress:
```css
@define-color background-color #1e1e2e;
@define-color border-color #89b4fa;
@define-color label #cdd6f4;
@define-color image #cdd6f4;
@define-color progress #cdd6f4;
```

### Accent Progress Bar
Different color for progress bar:
```css
@define-color background-color #1e1e2e;
@define-color border-color #45475a;
@define-color label #cdd6f4;
@define-color image #cdd6f4;
@define-color progress #a6e3a1;  /* Green progress */
```

### Monochrome
All elements in grayscale:
```css
@define-color background-color #000000;
@define-color border-color #333333;
@define-color label #ffffff;
@define-color image #ffffff;
@define-color progress #ffffff;
```

## Color Selection Guidelines

### Background Color
- Should match or be similar to notification background
- Dark themes: Usually matches terminal background
- Light themes: Slightly darker than terminal background
- Provides sufficient contrast for content

### Border Color
- Can match theme accent color
- Often same as waybar border/accent
- Should be visible but not too prominent
- 1-2 shades lighter/darker than background

### Label (Text) Color
- High contrast against background
- Usually matches terminal foreground
- Must be clearly readable
- Consistent with other UI text

### Image (Icon) Color
- Typically same as label color
- Can use accent color for emphasis
- Should be clearly visible
- SVG icons will be tinted this color

### Progress Bar Color
- Can be same as text or use accent color
- Green often used for volume (positive action)
- Blue for information
- Should stand out against background

## Theme Examples

### Dark Theme
```css
@define-color background-color #1e1e2e;
@define-color border-color #89b4fa;
@define-color label #cdd6f4;
@define-color image #cdd6f4;
@define-color progress #cdd6f4;
```

### Light Theme
```css
@define-color background-color #eff1f5;
@define-color border-color #1e66f5;
@define-color label #4c4f69;
@define-color image #4c4f69;
@define-color progress #40a02b;
```

### High Contrast
```css
@define-color background-color #000000;
@define-color border-color #ffffff;
@define-color label #ffffff;
@define-color image #ffffff;
@define-color progress #00ff00;
```

### Colorful Accent
```css
@define-color background-color #282828;
@define-color border-color #d79921;  /* Yellow border */
@define-color label #ebdbb2;
@define-color image #ebdbb2;
@define-color progress #b8bb26;      /* Green progress */
```

## What SwayOSD Controls

These colors affect:
- Volume change overlay
- Brightness change overlay
- Keyboard backlight overlay
- Microphone mute overlay
- Any other system OSD popups

## Testing Your Theme

Test the OSD with:
- Volume keys (increase/decrease/mute)
- Brightness keys (if available)
- Microphone mute key
- Media control keys

## Integration with System

SwayOSD colors should:
- Match or complement mako notification colors
- Be consistent with waybar theme
- Have similar style to walker launcher
- Use same color palette as terminal

## CSS Syntax Rules

1. Each line must end with semicolon `;`
2. Color name and value separated by single space
3. Use `@define-color` not `@define-colors`
4. No quotes around color values
5. Comments use CSS syntax: `/* comment */`

## Minimal Working Example
```css
@define-color background-color #1e1e2e;
@define-color border-color #89b4fa;
@define-color label #cdd6f4;
@define-color image #cdd6f4;
@define-color progress #a6e3a1;
```

## Validation Checklist
- [ ] All 5 colors defined
- [ ] Proper CSS syntax with semicolons
- [ ] Valid 6-digit hex codes
- [ ] `#` prefix on all colors
- [ ] Good contrast between background and foreground
- [ ] Colors align with overall theme palette