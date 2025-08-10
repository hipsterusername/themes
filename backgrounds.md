# Backgrounds (Wallpapers) Configuration

## Directory Structure
```
theme-name/
└── backgrounds/
    ├── 1-wallpaper.jpg  # Primary wallpaper
    ├── 2-wallpaper.png  # Optional secondary
    └── 3-wallpaper.jpg  # Optional tertiary
```

## File Location
`theme-name/backgrounds/` directory

## Naming Convention

Files are numbered to indicate priority/preference:
- `1-` prefix: Primary/default wallpaper
- `2-` prefix: Secondary option
- `3-` prefix: Tertiary option

Common patterns:
- `1-themename.jpg`
- `1-themename-variant.png`
- Numbers followed by descriptive names

## Supported Formats

- **JPEG/JPG**: Best for photographs, complex images
- **PNG**: Best for illustrations, graphics with transparency
- **WebP**: Modern format with good compression (if supported)

## File Guidelines

### Resolution
- Minimum: 1920x1080 (Full HD)
- Recommended: 2560x1440 (2K) or higher
- Consider common aspect ratios: 16:9, 16:10, 21:9

### File Size
- Recommended: Under 5MB per image
- Optimize images to reduce file size without quality loss
- Use JPEG for photos, PNG for graphics

### Color Considerations
- Should complement theme colors
- Consider how UI elements will look against it
- Test with both light and dark UI elements
- Avoid too much contrast in areas where UI appears

## Wallpaper Selection Guidelines

### Dark Themes
- Darker backgrounds (not necessarily black)
- Avoid bright spots where UI elements appear
- Consider subtle gradients or patterns
- Examples: Night scenes, dark abstracts, deep colors

### Light Themes
- Lighter backgrounds without being pure white
- Soft, muted colors work well
- Avoid harsh contrast
- Examples: Minimal designs, soft gradients, pastels

### Content Guidelines
- **Avoid busy patterns** where UI elements appear (top bar, dock)
- **Consider blur** for photographs to reduce distraction
- **Test readability** of desktop icons and text
- **Check all monitors** if using multiple displays

## Multiple Wallpapers

Reasons for multiple wallpapers:
1. **User choice**: Different preferences
2. **Monitor variations**: Different aspect ratios
3. **Mood options**: Light/dark variants
4. **Seasonal**: Different times of day/year

## Integration with Theme

Wallpapers should:
- Use colors from theme palette
- Not clash with accent colors
- Allow UI elements to remain visible
- Support the theme's mood/atmosphere

## Examples by Theme Type

### Minimalist Themes
- Solid colors with subtle gradients
- Simple geometric patterns
- Abstract designs with few colors
- Lots of negative space

### Nature Themes
- Landscapes with theme-appropriate colors
- Forest scenes for green themes
- Ocean/sky for blue themes
- Mountains for gray/monochrome themes

### Abstract Themes
- Gradient meshes using theme colors
- Geometric patterns
- Digital art matching color scheme
- Particle effects or waves

### Photographic Themes
- Architecture for urban themes
- Nature photography for organic themes
- Space/astronomy for dark themes
- Minimal objects for clean themes

## Color Extraction

Some themes extract accent colors from wallpaper:
- Ensure wallpaper has colors matching theme
- Primary accent color should be present
- Avoid wallpapers that would generate clashing colors

## Optimization Tips

### JPEG Optimization
```bash
# Using ImageMagick
convert input.jpg -quality 85 -strip output.jpg

# Using jpegoptim
jpegoptim --max=85 --strip-all image.jpg
```

### PNG Optimization
```bash
# Using optipng
optipng -o5 image.png

# Using pngquant for lossy compression
pngquant --quality=90-100 image.png
```

### Resize for Screen
```bash
# Resize to specific resolution
convert input.jpg -resize 2560x1440 output.jpg

# Resize maintaining aspect ratio
convert input.jpg -resize 2560x1440^ -gravity center -crop 2560x1440+0+0 output.jpg
```

## Testing Checklist

- [ ] UI elements visible against wallpaper
- [ ] No distracting elements behind common UI locations
- [ ] Colors complement theme palette
- [ ] File size optimized (under 5MB)
- [ ] Resolution appropriate for target displays
- [ ] Multiple options provided if applicable
- [ ] Numbered according to preference

## Special Considerations

### Light Mode Indicator
If theme has `light.mode` file, wallpaper should work for light theme

### Dynamic Wallpapers
Some setups rotate wallpapers:
- Ensure all provided wallpapers work with theme
- Consider time-of-day appropriate images
- Maintain consistent color palette across all options

### Transparency Effects
If using transparent UI elements:
- Test wallpaper with transparency
- Ensure text remains readable
- Consider blur effects for better readability

## Common Issues and Solutions

### UI Text Unreadable
- Add subtle dark/light overlay in problem areas
- Choose wallpapers with uniform areas where UI appears
- Consider blur or darkening/lightening the wallpaper

### Wallpaper Too Distracting
- Reduce saturation
- Apply blur effect
- Choose simpler alternatives
- Use gradient or abstract instead

### Color Mismatch
- Adjust wallpaper hue to match theme
- Choose different wallpaper
- Create color-matched version using photo editing