# Waybar Status Bar Theme Configuration

## File Format
CSS format with `@define-color` variable definitions

## File Location
`theme-name/waybar.css`

## Structure Template
```css
@define-color foreground #hexcode;
@define-color background #hexcode;
```

## Color Properties

### Essential Colors
- `foreground` - Primary text/icon color
- `background` - Primary background color

## Color Format
Standard CSS hex format: `#RRGGBB`
- Always use 6-digit hex codes
- Include the `#` prefix
- Lowercase hex digits common
- Semicolon required at end of each line

## Minimal Configuration

Most themes only define these two colors:
```css
@define-color foreground #cdd6f4;
@define-color background #1e1e2e;
```

The waybar configuration uses these variables throughout its stylesheets for consistent theming.

## Color Selection Guidelines

### Foreground Color
- Primary text and icon color
- Must have high contrast against background
- Usually matches terminal foreground
- Should be clearly readable at small sizes

### Background Color
- Bar background color
- Usually matches or complements terminal background
- Can be slightly different for visual separation
- Consider transparency if desired (configured elsewhere)

## Theme Examples

### Dark Themes
```css
/* Catppuccin */
@define-color foreground #cdd6f4;
@define-color background #1e1e2e;

/* Tokyo Night */
@define-color foreground #c0caf5;
@define-color background #1a1b26;

/* Gruvbox */
@define-color foreground #ebdbb2;
@define-color background #282828;

/* Nord */
@define-color foreground #D8DEE9;
@define-color background #2E3440;
```

### Light Themes
```css
/* Catppuccin Latte */
@define-color foreground #4c4f69;
@define-color background #eff1f5;

/* Rose Pine Dawn */
@define-color foreground #575279;
@define-color background #faf4ed;
```

### High Contrast
```css
@define-color foreground #ffffff;
@define-color background #000000;
```

## Integration Notes

These colors are used by waybar for:
- Module text (clock, battery, network, etc.)
- Module icons
- Workspace indicators
- System tray icons (when possible)
- Bar background

Additional styling (hover effects, active states, specific module colors) is handled by the main waybar configuration, using these base colors as variables.

## CSS Usage

In the main waybar stylesheet, these colors are referenced as:
```css
* {
    color: @foreground;
    background-color: @background;
}

#workspaces button {
    color: @foreground;
}

#clock {
    color: @foreground;
}
```

## Testing Your Theme

After setting colors:
1. Restart waybar or reload configuration
2. Check text readability across all modules
3. Verify workspace indicators are visible
4. Test hover states if configured
5. Check system tray icon visibility

## Relationship to Other Components

Waybar colors should:
- Match terminal foreground/background
- Complement hyprland border colors
- Align with notification (mako) scheme
- Be consistent with launcher (walker) theme

## Advanced Customization

While this file only defines two colors, you can:
1. Add more color variables for complex themes
2. Use these as base for calculated colors in main config
3. Override specific module colors in main stylesheet

Example of additional colors:
```css
@define-color foreground #cdd6f4;
@define-color background #1e1e2e;
@define-color accent #89b4fa;
@define-color warning #f9e2af;
@define-color critical #f38ba8;
```

## File Syntax Rules

1. Use `@define-color` directive
2. Single space between elements
3. End with semicolon `;`
4. No quotes around hex values
5. CSS comments allowed: `/* comment */`

## Minimal Working Example
```css
@define-color foreground #cdd6f4;
@define-color background #1e1e2e;
```

## Validation Checklist
- [ ] Both foreground and background defined
- [ ] Valid CSS syntax with semicolons
- [ ] Valid 6-digit hex codes with # prefix
- [ ] Good contrast between colors
- [ ] Colors align with terminal theme
- [ ] Text readable at small sizes