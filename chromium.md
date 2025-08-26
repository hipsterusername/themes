# Chromium Theme Configuration

Chromium themes are simple text files that set the browser UI background color using RGB values.

## File Location
- **Path**: `chromium.theme`
- **Format**: Single line with comma-separated RGB values

## Format

The chromium.theme file contains a single line with three comma-separated numbers representing RGB color values (0-255):

```
R,G,B
```

Where:
- **R**: Red value (0-255)
- **G**: Green value (0-255)  
- **B**: Blue value (0-255)

## Purpose

This theme file sets the background color for Chromium's UI elements, providing visual consistency with your desktop theme. The color typically matches or complements your theme's main background color.

## Examples

### Dark Theme (Gruvbox)
```
40,40,40
```
*A neutral dark gray background*

### Dark Theme (Tokyo Night)
```
26,27,38
```
*A deep blue-tinted dark background*

### Light Theme (Rose Pine Dawn)
```
250,244,237
```
*A soft, warm light background*

## Integration Tips

1. **For dark themes**: Use your theme's main background color or a slightly lighter variant
2. **For light themes**: Use light background colors or accent colors based on your preference
3. **Color harmony**: Match or complement your terminal and window manager colors

## Color Selection Guidelines

- **Dark themes**: RGB values typically range from 10-60 for each channel
- **Light themes**: RGB values typically range from 200-255 for each channel
- **Consistency**: Match the tone of your hyprland/alacritty background colors