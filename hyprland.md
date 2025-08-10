# Hyprland Window Manager Theme Configuration

## File Format
Simple configuration format with `property = value` syntax

## File Location
`theme-name/hyprland.conf`

## Structure
```conf
general {
    col.active_border = rgb(hexcode)
}
```

## Properties

### Required
- `col.active_border` - Color of active window borders

### Color Format
**RGB Function Format**: `rgb(hexcode)`
- No `#` prefix
- 6-character hex code
- Case insensitive (both `rgb(c6d0f5)` and `rgb(C6D0F5)` work)

## Examples

### Dark Theme
```conf
general {
    col.active_border = rgb(89b4fa)  # Blue accent
}
```

### Light Theme
```conf
general {
    col.active_border = rgb(1e66f5)  # Darker blue for light background
}
```

### Green Accent
```conf
general {
    col.active_border = rgb(a7c080)  # Soft green
}
```

## Color Selection Guidelines

1. **Visibility**: Choose a color that stands out against your wallpaper
2. **Theme Consistency**: Match your theme's primary accent color
3. **Not Too Bright**: Avoid pure/neon colors that can be distracting
4. **Common Choices**:
   - Blue shades: Popular for productivity themes
   - Green shades: Natural, calming themes
   - Purple/Pink: Creative, aesthetic themes
   - Orange/Yellow: Warm, energetic themes

## Integration with Theme

The active border color typically should:
- Match the accent color used in waybar
- Complement the terminal cursor color
- Be visible against the most common wallpaper colors
- Align with highlight colors in other applications

## Testing

After setting the border color:
1. Open multiple windows
2. Switch focus between windows
3. Ensure the active border is clearly visible
4. Test against different wallpapers if your theme includes multiple

## Common Color Values

### Blues
- `rgb(89b4fa)` - Catppuccin blue
- `rgb(81a1c1)` - Nord blue
- `rgb(7aa2f7)` - Tokyo Night blue

### Greens
- `rgb(a6e3a1)` - Catppuccin green
- `rgb(a7c080)` - Everforest green
- `rgb(a3be8c)` - Nord green

### Purples/Pinks
- `rgb(cba6f7)` - Catppuccin mauve
- `rgb(d699b6)` - Everforest purple
- `rgb(b48ead)` - Nord purple

### Warm Colors
- `rgb(fab387)` - Catppuccin peach
- `rgb(ebcb8b)` - Nord yellow
- `rgb(e67e80)` - Everforest red

## Minimal Configuration

The absolute minimum required:
```conf
general {
    col.active_border = rgb(your_hex_color)
}
```

## Notes

- This file only handles the window border color
- Other Hyprland configurations are managed elsewhere
- The color should be tested with your specific monitor and lighting conditions
- Consider users who may have different wallpapers when choosing colors