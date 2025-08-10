# Alacritty Terminal Theme Configuration

## File Format
TOML format with nested color sections

## File Location
`theme-name/alacritty.toml`

## Structure Template
```toml
[colors.primary]
background = "#hexcode"
foreground = "#hexcode"
dim_foreground = "#hexcode"     # Optional
bright_foreground = "#hexcode"   # Optional

[colors.normal]
black = "#hexcode"
red = "#hexcode"
green = "#hexcode"
yellow = "#hexcode"
blue = "#hexcode"
magenta = "#hexcode"
cyan = "#hexcode"
white = "#hexcode"

[colors.bright]
black = "#hexcode"
red = "#hexcode"
green = "#hexcode"
yellow = "#hexcode"
blue = "#hexcode"
magenta = "#hexcode"
cyan = "#hexcode"
white = "#hexcode"

[colors.dim]  # Optional section
black = "#hexcode"
red = "#hexcode"
green = "#hexcode"
yellow = "#hexcode"
blue = "#hexcode"
magenta = "#hexcode"
cyan = "#hexcode"
white = "#hexcode"

[colors.cursor]  # Optional
text = "#hexcode"
cursor = "#hexcode"

[colors.selection]  # Optional
text = "CellForeground"  # Or hex code
background = "#hexcode"

[colors.search]  # Optional
[colors.search.matches]
foreground = "#hexcode"
background = "#hexcode"
[colors.search.focused_match]
foreground = "#hexcode"
background = "#hexcode"

[colors.vi_mode_cursor]  # Optional
text = "#hexcode"
cursor = "#hexcode"

[[colors.indexed_colors]]  # Optional, can have multiple
index = 16
color = "#hexcode"

[colors.hints]  # Optional
[[colors.hints.start]]
foreground = "#hexcode"
background = "#hexcode"
[[colors.hints.end]]
foreground = "#hexcode"
background = "#hexcode"

[colors.footer_bar]  # Optional
foreground = "#hexcode"
background = "#hexcode"
```

## Color Format Variations

The following formats are all valid:
- Quoted hex: `"#24273a"`
- Quoted with 0x prefix: `"0x282828"`
- Single quotes: `'#1a1b26'`

## Required Sections
- `[colors.primary]` with at least `background` and `foreground`
- `[colors.normal]` with all 8 standard terminal colors
- `[colors.bright]` with all 8 bright variants

## Optional Sections
- `[colors.dim]` - Dimmed color variants
- `[colors.cursor]` - Cursor colors
- `[colors.selection]` - Text selection colors
- `[colors.search]` - Search highlight colors
- `[colors.vi_mode_cursor]` - Vi mode cursor colors
- `[[colors.indexed_colors]]` - Extended palette (indices 16-255)
- `[colors.hints]` - URL/hyperlink hint colors
- `[colors.footer_bar]` - Footer bar colors

## Standard Terminal Colors

The 16 standard colors should follow semantic meanings:
- **black/bright black** - Darkest/dark grays
- **red/bright red** - Error, danger, deletion
- **green/bright green** - Success, addition, confirmation
- **yellow/bright yellow** - Warning, modification
- **blue/bright blue** - Information, links
- **magenta/bright magenta** - Special, keywords
- **cyan/bright cyan** - Strings, quotes
- **white/bright white** - Light gray/pure white

## Best Practices

1. **Maintain Contrast**: Ensure adequate contrast between background and foreground
2. **Bright vs Normal**: Bright colors should be noticeably brighter/more saturated
3. **Dim Colors**: If included, should be less saturated than normal colors
4. **Consistency**: Match primary colors with your overall theme palette
5. **Testing**: Test with common terminal applications (vim, htop, ls --color, git diff)

## Common Patterns

### Dark Themes
- Background: Dark color (#1a1b26, #24273a, #282828)
- Foreground: Light color (#cdd6f4, #a9b1d6, #fbf1c7)
- Normal black: Slightly lighter than background
- Bright white: Pure or near-pure white

### Light Themes
- Background: Light color (#eff1f5, #fafafa)
- Foreground: Dark color (#4c4f69, #333333)
- Normal white: Slightly darker than background
- Bright black: Dark gray, not pure black

## Special Values
- `"CellForeground"` - Use current cell's foreground color
- `"CellBackground"` - Use current cell's background color
- Empty string `""` - Transparent/default

## Validation Checklist
- [ ] All required sections present
- [ ] All 8 colors defined in normal and bright sections
- [ ] Hex codes are valid 6-character format
- [ ] Background and foreground have sufficient contrast
- [ ] Colors align with theme's overall palette