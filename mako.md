# Mako Notification Daemon Theme Configuration

## File Format
INI format with key-value pairs and optional sections

## File Location
`theme-name/mako.ini`

## Complete Structure Template
```ini
# Display Configuration
font=Liberation Sans 11
width=420
height=110
padding=10
margin=10
border-size=2
border-radius=5
max-icon-size=32
anchor=top-right
default-timeout=5000
ignore-timeout=0
layer=overlay

# Theme Colors
text-color=#hexcode
border-color=#hexcode
background-color=#hexcode

# Optional: Progress bar color
progress-color=#hexcode

# Optional: Urgency-specific colors
[urgency=low]
text-color=#hexcode
border-color=#hexcode
background-color=#hexcode

[urgency=high]
text-color=#hexcode
border-color=#hexcode
background-color=#hexcode
default-timeout=0

# Application-specific rules
[app-name=Spotify]
invisible=1

# Do not disturb mode
[mode=do-not-disturb]
invisible=1
```

## Color Properties

### Required Colors
- `text-color` - Notification text color
- `border-color` - Notification border color  
- `background-color` - Notification background color

### Optional Colors
- `progress-color` - Progress bar color (if not set, uses text-color)

### Color Format
Hex format with `#` prefix: `#RRGGBB`
- Always 6 digits
- Case insensitive
- No quotes

## Standard Layout Configuration

These values are consistent across themes:
```ini
font=Liberation Sans 11      # Can be 11 or 12
width=420                     # Notification width
height=110                    # Maximum height
padding=10                    # Inner padding
margin=10                     # Margin from screen edge
border-size=2                 # Border thickness
border-radius=5               # Corner radius
max-icon-size=32             # Maximum icon size
anchor=top-right             # Screen position
default-timeout=5000         # 5 seconds default
ignore-timeout=0             # Honor app timeouts
layer=overlay                # Display layer
```

## Sections

### Urgency Levels
```ini
[urgency=low]
# Optional overrides for low urgency

[urgency=normal]
# Optional overrides for normal urgency (default)

[urgency=high]
# Optional overrides for high urgency
default-timeout=0  # Often set to never timeout
```

### Application-Specific Rules
```ini
[app-name=Spotify]
invisible=1  # Hide Spotify notifications

[app-name=Discord]
# Custom settings for Discord

[app-name=Firefox]
# Custom settings for Firefox
```

### Modes
```ini
[mode=do-not-disturb]
invisible=1  # Hide all notifications in DND mode

[mode=gaming]
anchor=top-left  # Move notifications for gaming
```

## Color Selection Guidelines

### Background Color
- Dark themes: 10-20% lighter than terminal background
- Light themes: 10-20% darker than terminal background
- Consider transparency if supported

### Text Color
- High contrast against background
- Usually matches terminal foreground color
- Ensure readability at small sizes

### Border Color
- Often matches theme accent color
- Can be same as text color for minimal look
- Should be visible but not distracting

### Progress Bar Color
- Usually matches accent or success color
- Green for completion/success
- Blue for information
- Can match border color

## Theme Examples

### Dark Theme
```ini
text-color=#cdd6f4
border-color=#89b4fa
background-color=#1e1e2e
progress-color=#a6e3a1
```

### Light Theme
```ini
text-color=#4c4f69
border-color=#1e66f5
background-color=#eff1f5
progress-color=#40a02b
```

### High Contrast
```ini
text-color=#ffffff
border-color=#ffffff
background-color=#000000
```

## Common Patterns

### Monochrome
All colors from same hue, varying brightness

### Accent Border
Neutral background/text with colorful border

### Urgency Differentiation
- Low: Dimmer colors
- Normal: Standard theme colors
- High: Red/orange border or background

## Special Rules

### Spotify Notifications
Always included:
```ini
[app-name=Spotify]
invisible=1
```
This hides Spotify's frequent track change notifications

### Do Not Disturb Mode
Standard implementation:
```ini
[mode=do-not-disturb]
invisible=1
```

## Testing Notifications

Test your theme with:
```bash
notify-send "Test" "This is a test notification"
notify-send -u low "Low urgency" "Test message"
notify-send -u high "High urgency" "Test message"
notify-send -h int:value:50 "Progress" "50% complete"
```

## Integration Tips

Mako colors should:
- Match or complement waybar colors
- Have sufficient contrast against wallpapers
- Be consistent with terminal color scheme
- Stand out enough to catch attention
- Not be too bright/distracting

## Validation Checklist
- [ ] All three required colors defined
- [ ] Hex codes are valid 6-character format
- [ ] Standard layout values present
- [ ] Spotify invisible rule included
- [ ] DND mode configured
- [ ] Colors have good contrast
- [ ] Border visible against common backgrounds