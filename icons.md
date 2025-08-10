# Icons Theme Configuration

## File Format
Plain text file with a single line containing the icon theme name

## File Location
`theme-name/icons.theme`

## Content Format
```
IconThemeName
```

## Available Icon Themes

The system uses Yaru icon theme variants that match color schemes:

### Standard Yaru Variants
- `Yaru` - Default Ubuntu icons
- `Yaru-dark` - Dark variant
- `Yaru-blue` - Blue accent
- `Yaru-blue-dark` - Blue accent, dark variant
- `Yaru-green` - Green accent
- `Yaru-green-dark` - Green accent, dark variant
- `Yaru-orange` - Orange accent
- `Yaru-orange-dark` - Orange accent, dark variant
- `Yaru-pink` - Pink accent
- `Yaru-pink-dark` - Pink accent, dark variant
- `Yaru-purple` - Purple accent
- `Yaru-purple-dark` - Purple accent, dark variant
- `Yaru-red` - Red accent
- `Yaru-red-dark` - Red accent, dark variant
- `Yaru-yellow` - Yellow accent
- `Yaru-yellow-dark` - Yellow accent, dark variant

### Extended Variants
- `Yaru-sage` - Sage green accent
- `Yaru-sage-dark` - Sage green, dark variant
- `Yaru-magenta` - Magenta accent
- `Yaru-magenta-dark` - Magenta accent, dark variant

## Color Matching Guidelines

Match icon theme to your color scheme's primary accent:

### Blue Themes
- Catppuccin → `Yaru-blue` or `Yaru-blue-dark`
- Nord → `Yaru-blue-dark`
- Tokyo Night → `Yaru-blue-dark`

### Green Themes
- Everforest → `Yaru-sage` or `Yaru-green`
- Gruvbox → `Yaru-green` or `Yaru-sage`

### Purple/Pink Themes
- Rose Pine → `Yaru-purple` or `Yaru-pink`
- Catppuccin Mocha → `Yaru-purple-dark`

### Warm Themes
- Gruvbox → `Yaru-orange` or `Yaru-yellow`
- Kanagawa → `Yaru-red` or `Yaru-orange`

### Monochrome Themes
- Matte Black → `Yaru-dark`
- Minimal themes → `Yaru` or `Yaru-dark`

## Selection Criteria

1. **Accent Color Match**: Choose variant matching your theme's primary accent
2. **Background Compatibility**: 
   - Dark themes → Use `-dark` variants
   - Light themes → Use standard variants
3. **Folder Colors**: Consider how folder icons will look in file manager
4. **System Tray**: Ensure icons are visible in your waybar/system tray

## Examples

### Dark Theme with Blue Accent
```
Yaru-blue-dark
```

### Light Theme with Green Accent
```
Yaru-green
```

### Purple Aesthetic Theme
```
Yaru-purple
```

## Testing Your Selection

After setting the icon theme:
1. Open file manager to see folder icons
2. Check system tray icon visibility
3. Look at application launcher icons
4. Verify icons in notifications

## Fallback Options

If specific variant isn't available:
- Dark themes → `Yaru-dark`
- Light themes → `Yaru`
- Any theme → `Yaru` (default)

## Custom Icon Themes

While the system primarily uses Yaru variants, you can specify other icon themes if installed:
- `Papirus`
- `Papirus-Dark`
- `Numix`
- `Numix-Circle`
- etc.

Ensure the theme is installed system-wide or in `~/.icons/`

## Integration Notes

The icon theme affects:
- File manager icons
- Application launcher icons
- System tray icons
- Notification icons
- Desktop application icons

Choose a theme that maintains visibility and consistency across all these contexts.

## File Format Rules
- Single line only
- No quotes or extra characters
- No trailing spaces or newlines
- Case-sensitive theme name