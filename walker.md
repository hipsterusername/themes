# Walker Application Launcher Theme Configuration

## File Format
CSS format with `@define-color` variable definitions

## File Location
`theme-name/walker.css`

## Structure Template
```css
@define-color selected-text #hexcode;
@define-color text #hexcode;
@define-color base #hexcode;
@define-color border #hexcode;
@define-color foreground #hexcode;
@define-color background #hexcode;
```

## Color Properties

### Core Colors (Most Common)
- `selected-text` - Text color for selected/highlighted items
- `text` - Default text color
- `base` - Base background color
- `border` - Border color for UI elements

### Additional Colors (Optional)
- `foreground` - General foreground color
- `background` - General background color

## Color Format
Standard CSS hex format: `#RRGGBB`
- Always use 6-digit hex codes
- Include the `#` prefix
- Case insensitive (but often lowercase)
- Semicolon required at end of each line

## Common Patterns

### Pattern 1: Four Core Colors
Many themes only define the four essential colors:
```css
@define-color selected-text #89dceb;
@define-color text #cdd6f4;
@define-color base #1e1e2e;
@define-color border #89b4fa;
```

### Pattern 2: Six Colors
Some themes include foreground/background:
```css
@define-color selected-text #7aa2f7;
@define-color text #c0caf5;
@define-color base #1a1b26;
@define-color border #7aa2f7;
@define-color foreground #c0caf5;
@define-color background #1a1b26;
```

## Color Selection Guidelines

### Selected Text
- Should be noticeably different from regular text
- Often uses theme accent color
- Can be brighter/more saturated version of text color
- Must remain readable against base background

### Text
- Primary text color for unselected items
- High contrast against base background
- Usually matches terminal foreground color
- Should be easy to read

### Base
- Main background color of the launcher
- Usually matches or is close to terminal background
- Dark themes: Dark colors (#1a1b26, #1e1e2e)
- Light themes: Light colors (#eff1f5, #fafafa)

### Border
- Outline color for the launcher window
- Often matches theme accent color
- Can be same as selected-text for consistency
- Should be visible against desktop wallpaper

### Foreground/Background
- When present, usually duplicate text/base values
- May be used for specific UI elements
- Provides additional customization options

## Theme Examples

### Dark Theme with Blue Accent
```css
@define-color selected-text #89b4fa;
@define-color text #cdd6f4;
@define-color base #1e1e2e;
@define-color border #89b4fa;
```

### Dark Theme with Green Accent
```css
@define-color selected-text #a7c080;
@define-color text #d3c6aa;
@define-color base #2f383e;
@define-color border #a7c080;
```

### Light Theme
```css
@define-color selected-text #1e66f5;
@define-color text #4c4f69;
@define-color base #eff1f5;
@define-color border #1e66f5;
```

### High Contrast Monochrome
```css
@define-color selected-text #ffffff;
@define-color text #cccccc;
@define-color base #000000;
@define-color border #ffffff;
```

### Warm Theme
```css
@define-color selected-text #d79921;
@define-color text #ebdbb2;
@define-color base #282828;
@define-color border #d79921;
```

## Visual Hierarchy

The colors create this visual hierarchy:
1. **Selected item**: Most prominent (selected-text on base)
2. **Regular items**: Readable but less prominent (text on base)
3. **Window border**: Defines launcher boundaries (border)
4. **Background**: Provides context (base)

## Integration with System

Walker colors should:
- Match terminal color scheme
- Use same accent color as waybar/hyprland borders
- Complement notification (mako) colors
- Be consistent with overall desktop theme

## Testing Your Theme

After setting colors:
1. Open walker (usually Super/Meta key)
2. Type to search for applications
3. Use arrow keys to navigate selections
4. Verify all text is readable
5. Check border visibility
6. Test against different wallpapers

## CSS Syntax Rules

1. Use `@define-color` directive
2. Single space between color name and value
3. End each line with semicolon `;`
4. No quotes around hex values
5. Comments: `/* comment */`

## Minimal Configuration
```css
@define-color selected-text #89b4fa;
@define-color text #cdd6f4;
@define-color base #1e1e2e;
@define-color border #89b4fa;
```

## Extended Configuration
```css
@define-color selected-text #89b4fa;
@define-color text #cdd6f4;
@define-color base #1e1e2e;
@define-color border #89b4fa;
@define-color foreground #cdd6f4;
@define-color background #1e1e2e;
/* Additional custom colors can be defined */
```

## Common Color Relationships

- `selected-text` often equals `border` (consistent accent)
- `text` often equals `foreground` (when both present)
- `base` often equals `background` (when both present)
- `selected-text` is usually brighter than `text`

## Validation Checklist
- [ ] At minimum, four core colors defined
- [ ] Proper CSS syntax with semicolons
- [ ] Valid 6-digit hex codes with # prefix
- [ ] Good contrast between text and base
- [ ] Selected-text distinguishable from regular text
- [ ] Border visible against common wallpapers
- [ ] Colors align with overall theme palette