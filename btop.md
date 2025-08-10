# Btop System Monitor Theme Configuration

## File Format
Key-value format with `theme[property]="value"` syntax

## File Location
`theme-name/btop.theme`

## Complete Property List

### Main UI Colors
```bash
theme[main_bg]="#hexcode"          # Main background
theme[main_fg]="#hexcode"          # Main text color
theme[title]="#hexcode"            # Window titles
theme[hi_fg]="#hexcode"            # Highlighted text
theme[selected_bg]="#hexcode"      # Selected item background
theme[selected_fg]="#hexcode"      # Selected item text
theme[inactive_fg]="#hexcode"      # Inactive/disabled text
theme[graph_text]="#hexcode"       # Graph labels
theme[meter_bg]="#hexcode"         # Meter background
theme[proc_misc]="#hexcode"        # Process miscellaneous info
theme[cpu_box]="#hexcode"          # CPU box outline
theme[mem_box]="#hexcode"          # Memory box outline
theme[net_box]="#hexcode"          # Network box outline
theme[proc_box]="#hexcode"         # Process box outline
theme[div_line]="#hexcode"         # Divider lines
```

### CPU Colors
```bash
theme[cpu_start]="#hexcode"        # CPU graph gradient start
theme[cpu_mid]="#hexcode"          # CPU graph gradient middle
theme[cpu_end]="#hexcode"          # CPU graph gradient end
```

### Temperature Colors
```bash
theme[temp_start]="#hexcode"       # Temperature gradient start (cool)
theme[temp_mid]="#hexcode"         # Temperature gradient middle (warm)
theme[temp_end]="#hexcode"         # Temperature gradient end (hot)
```

### Memory/Swap Colors
```bash
theme[free_start]="#hexcode"       # Free memory gradient start
theme[free_mid]="#hexcode"         # Free memory gradient middle
theme[free_end]="#hexcode"         # Free memory gradient end
theme[cached_start]="#hexcode"     # Cached memory gradient start
theme[cached_mid]="#hexcode"       # Cached memory gradient middle
theme[cached_end]="#hexcode"       # Cached memory gradient end
theme[available_start]="#hexcode"  # Available memory gradient start
theme[available_mid]="#hexcode"    # Available memory gradient middle
theme[available_end]="#hexcode"    # Available memory gradient end
theme[used_start]="#hexcode"       # Used memory gradient start
theme[used_mid]="#hexcode"         # Used memory gradient middle
theme[used_end]="#hexcode"         # Used memory gradient end
```

### Network Colors
```bash
theme[download_start]="#hexcode"   # Download graph gradient start
theme[download_mid]="#hexcode"     # Download graph gradient middle
theme[download_end]="#hexcode"     # Download graph gradient end
theme[upload_start]="#hexcode"     # Upload graph gradient start
theme[upload_mid]="#hexcode"       # Upload graph gradient middle
theme[upload_end]="#hexcode"       # Upload graph gradient end
```

### Process Colors
```bash
theme[process_start]="#hexcode"    # Process gradient start
theme[process_mid]="#hexcode"      # Process gradient middle
theme[process_end]="#hexcode"      # Process gradient end
```

## Color Format Options

1. **Hex format**: `"#RRGGBB"` (most common)
2. **RGB format**: `"R G B"` where R, G, B are 0-255
3. **Empty string**: `""` for transparent/default

## Gradient Patterns

Btop uses three-color gradients for graphs and meters:
- `_start` - Low values/beginning of gradient
- `_mid` - Middle values
- `_end` - High values/end of gradient

### Common Gradient Schemes

**Temperature (Cool to Hot)**
- Start: Blue/Green (#8fbcbb, #a7c080)
- Mid: Yellow/Orange (#ebcb8b, #dbbc7f)
- End: Red (#bf616a, #e67e80)

**CPU Usage (Low to High)**
- Start: Green (#a3be8c, #a7c080)
- Mid: Yellow (#ebcb8b, #dbbc7f)
- End: Red/Magenta (#bf616a, #d699b6)

**Memory (Free to Full)**
- Start: Green tones
- Mid: Yellow/Orange tones
- End: Red tones

**Network (Low to High Traffic)**
- Download: Blue to cyan gradient
- Upload: Green to yellow gradient

## Box Outline Colors

Each major section can have a unique border color:
- `cpu_box` - CPU section border
- `mem_box` - Memory section border
- `net_box` - Network section border
- `proc_box` - Process list border

Common approaches:
1. **Uniform**: All boxes use the same color
2. **Semantic**: Each box uses related gradient color
3. **Accent**: Boxes use theme accent color

## Best Practices

1. **Contrast**: Ensure text is readable against backgrounds
2. **Gradient Logic**: Use intuitive color progressions (green→yellow→red for usage)
3. **Consistency**: Match overall theme palette
4. **Box Colors**: Should be visible but not distracting
5. **Inactive Text**: Should be dimmer than main text but still readable

## Minimal Theme Example
```bash
theme[main_bg]="#1e1e2e"
theme[main_fg]="#cdd6f4"
theme[title]="#cba6f7"
theme[hi_fg]="#89dceb"
theme[selected_bg]="#45475a"
theme[selected_fg]="#cdd6f4"
theme[inactive_fg]="#7f849c"
theme[cpu_box]="#f38ba8"
theme[mem_box]="#a6e3a1"
theme[net_box]="#89b4fa"
theme[proc_box]="#f9e2af"
# ... (gradients and other colors)
```

## Validation Checklist
- [ ] All main UI colors defined
- [ ] All gradient triads complete (_start, _mid, _end)
- [ ] Box outline colors defined
- [ ] Colors use valid format (hex or RGB)
- [ ] Sufficient contrast for readability
- [ ] Gradients follow logical progression