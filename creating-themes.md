# Complete Theme Creation Guide

## Overview
This guide walks through creating a new theme from scratch, covering all applications and ensuring consistency across the entire desktop environment.

## Step 1: Planning Your Theme

### Choose Your Color Palette
1. **Base Colors**
   - Background (dark or light)
   - Foreground (contrasting text color)
   - Secondary background (cards, panels)

2. **Accent Colors**
   - Primary accent (buttons, highlights)
   - Success/positive (green tones)
   - Warning (yellow/orange tones)
   - Error/critical (red tones)
   - Information (blue tones)

3. **Neutral Colors**
   - Border colors
   - Inactive/disabled elements
   - Comment text
   - Separators

### Theme Style Decision
- **Dark vs Light**: Primary background brightness
- **Colorful vs Monochrome**: Saturation levels
- **High vs Low Contrast**: Accessibility considerations
- **Modern vs Traditional**: Color palette approach

## Step 2: Create Theme Directory

```bash
# Create new theme directory
mkdir my-theme-name

# Copy existing theme as template (recommended)
cp -r catppuccin/ my-theme-name/

# Or create empty structure
mkdir -p my-theme-name/backgrounds
```

## Step 3: Terminal Foundation (Alacritty)

Start with the terminal as it sets the foundation:

1. **Edit `alacritty.toml`**
2. **Define core colors first:**
   ```toml
   [colors.primary]
   background = "#1a1a1a"    # Your dark background
   foreground = "#e0e0e0"    # Your light text
   ```

3. **Set the 16 terminal colors:**
   - Follow semantic meanings (red=error, green=success, etc.)
   - Ensure good contrast
   - Test with common terminal applications

4. **Validation:**
   ```bash
   # Test with various commands
   ls --color=always
   git status
   vim
   htop
   ```

## Step 4: Window Manager (Hyprland)

1. **Edit `hyprland.conf`**
2. **Choose accent color:**
   ```conf
   general {
       col.active_border = rgb(your_accent_color)
   }
   ```
3. **Match with alacritty accent or cursor color**

## Step 5: Status Bar (Waybar)

1. **Edit `waybar.css`**
2. **Define basic colors:**
   ```css
   @define-color foreground #e0e0e0;
   @define-color background #1a1a1a;
   ```
3. **Use alacritty primary colors**

## Step 6: Notifications (Mako)

1. **Edit `mako.ini`**
2. **Core configuration:**
   ```ini
   text-color=#e0e0e0
   border-color=#your_accent
   background-color=#1a1a1a
   
   # Keep standard layout
   font=Liberation Sans 11
   width=420
   height=110
   padding=10
   border-size=2
   anchor=top-right
   default-timeout=5000
   
   [app-name=Spotify]
   invisible=1
   
   [mode=do-not-disturb]
   invisible=1
   ```

## Step 7: Application Launcher (Walker)

1. **Edit `walker.css`**
2. **Essential colors:**
   ```css
   @define-color selected-text #your_accent;
   @define-color text #e0e0e0;
   @define-color base #1a1a1a;
   @define-color border #your_accent;
   ```

## Step 8: On-Screen Display (SwayOSD)

1. **Edit `swayosd.css`**
2. **Unified approach:**
   ```css
   @define-color background-color #1a1a1a;
   @define-color border-color #your_accent;
   @define-color label #e0e0e0;
   @define-color image #e0e0e0;
   @define-color progress #your_accent;
   ```

## Step 9: System Monitor (Btop)

1. **Edit `btop.theme`**
2. **Start with basics:**
   ```bash
   theme[main_bg]="#1a1a1a"
   theme[main_fg]="#e0e0e0"
   theme[title]="#your_accent"
   theme[selected_bg]="#333333"
   theme[selected_fg]="#ffffff"
   ```

3. **Define gradients:**
   ```bash
   # CPU usage gradient (green -> yellow -> red)
   theme[cpu_start]="#a6e3a1"
   theme[cpu_mid]="#f9e2af"
   theme[cpu_end]="#f38ba8"
   
   # Temperature gradient (blue -> yellow -> red)
   theme[temp_start]="#89b4fa"
   theme[temp_mid]="#f9e2af"
   theme[temp_end]="#f38ba8"
   ```

4. **Box outlines:**
   ```bash
   theme[cpu_box]="#your_accent"
   theme[mem_box]="#your_accent"
   theme[net_box]="#your_accent"
   theme[proc_box]="#your_accent"
   ```

## Step 10: Lock Screen (Hyprlock)

1. **Edit `hyprlock.conf`**
2. **With transparency:**
   ```conf
   $color = rgba(26,26,26,0.9)        # Semi-transparent background
   $inner_color = rgba(51,51,51,0.8)  # Input fields
   $outer_color = rgba(accent_r,accent_g,accent_b,1.0)  # Border
   $font_color = rgba(224,224,224,1.0)  # Text
   $check_color = rgba(accent_r,accent_g,accent_b,1.0)  # Checkmarks
   ```

## Step 11: Text Editor (Neovim)

1. **Edit `neovim.lua`**
2. **Choose approach:**

   **Simple (built-in theme):**
   ```lua
   return {
     { "LazyVim/LazyVim", opts = { colorscheme = "default" } },
   }
   ```

   **Plugin-based:**
   ```lua
   return {
     { "author/theme-plugin.nvim" },
     { "LazyVim/LazyVim", opts = { colorscheme = "theme-name" } },
   }
   ```

## Step 12: Icons

1. **Edit `icons.theme`**
2. **Choose matching variant:**
   ```
   Yaru-blue-dark     # For blue accent themes
   Yaru-green         # For green accent themes
   Yaru-purple        # For purple accent themes
   Yaru-dark          # For monochrome themes
   ```

## Step 13: Wallpapers

1. **Create `backgrounds/` directory**
2. **Add wallpapers:**
   - Primary: `1-themename.jpg`
   - Optional: `2-themename-alt.png`

3. **Wallpaper criteria:**
   - Complements color scheme
   - Doesn't interfere with UI readability
   - Appropriate resolution (1920x1080+)
   - Under 5MB file size

## Step 14: Light/Dark Mode Configuration

### Dark Mode (Default)
By default, themes without a `.mode` file are treated as dark themes. The system will set GTK applications to prefer dark mode variants.

### Light Mode Support
To configure a theme as a light mode theme:

1. **Create `light.mode` file** in your theme directory
   ```bash
   echo '# This will set "prefer-light" and use "Adwaita" as the theme' > light.mode
   ```
   
2. **What this does:**
   - Sets system preference to "prefer-light" for applications that support theme detection
   - Uses Adwaita GTK theme (GNOME's default theme) in light variant
   - Ensures GTK applications (Firefox, GIMP, file managers) use light UI elements

3. **Adjust all colors for light background:**
   - Invert background/foreground relationship
   - Ensure sufficient contrast (darker text on light backgrounds)
   - Test readability in bright environments
   - Consider using warmer, softer colors for reduced eye strain

4. **Light theme examples in this repository:**
   - `catppuccin-latte` - Light variant of Catppuccin
   - `rose-pine` - Has light mode support
   - `milkmatcha` - Light green tea-inspired theme

## Step 15: Testing Your Theme

### Visual Testing
1. **Terminal Applications:**
   ```bash
   ls --color=always
   git log --oneline --graph --color=always
   vim /etc/passwd
   htop
   ```

2. **Desktop Environment:**
   - Switch window focus (border visibility)
   - Open application launcher
   - Trigger notifications
   - Adjust volume/brightness (OSD)
   - Lock screen test

3. **File Manager:**
   - Check folder icons
   - Verify text readability
   - Test selection colors

### Color Consistency Check
- All accent colors should match across applications
- Background/foreground pairs consistent
- Border colors unified
- Text remains readable everywhere

### Accessibility Testing
- Sufficient contrast ratios (WCAG guidelines)
- Color-blind friendly palette
- Readable at different font sizes

## Step 16: Color Palette Documentation

Create a color reference for your theme:

```markdown
# My Theme Palette

## Base Colors
- Background: #1a1a1a
- Foreground: #e0e0e0
- Secondary Background: #333333

## Accent Colors
- Primary: #89b4fa (Blue)
- Success: #a6e3a1 (Green)
- Warning: #f9e2af (Yellow)
- Error: #f38ba8 (Red)

## Terminal Colors
- Black: #1e1e2e / #45475a
- Red: #f38ba8 / #f2cdcd
- Green: #a6e3a1 / #c9f2c9
- Yellow: #f9e2af / #fcf4d9
- Blue: #89b4fa / #b6d7ff
- Magenta: #cba6f7 / #e5d4ff
- Cyan: #94e2d5 / #c7f0ec
- White: #cdd6f4 / #ffffff
```

## Step 17: Final Validation

Use this checklist:

### Files Present
- [ ] `alacritty.toml`
- [ ] `btop.theme`
- [ ] `hyprland.conf`
- [ ] `hyprlock.conf`
- [ ] `icons.theme`
- [ ] `mako.ini`
- [ ] `neovim.lua`
- [ ] `swayosd.css`
- [ ] `walker.css`
- [ ] `waybar.css`
- [ ] `backgrounds/` directory with wallpaper(s)
- [ ] `light.mode` (required for light themes, contains comment about prefer-light)

### Color Consistency
- [ ] Accent colors match across all applications
- [ ] Background colors are consistent
- [ ] Text has sufficient contrast everywhere
- [ ] Border colors are unified

### Functionality
- [ ] Terminal colors work with common applications
- [ ] Window borders are visible
- [ ] Notifications are readable
- [ ] Launcher is functional
- [ ] OSD displays correctly
- [ ] System monitor is readable
- [ ] Lock screen is functional

### Integration
- [ ] Wallpaper doesn't interfere with UI
- [ ] Icons match theme style
- [ ] All applications feel cohesive
- [ ] Theme works across different lighting conditions

## Common Issues and Solutions

### Poor Contrast
- Increase difference between background and foreground
- Test with color contrast analyzers
- Consider users with vision impairments

### Inconsistent Accents
- Document your accent color early
- Use color picker to ensure exact matches
- Test all applications after color changes

### Wallpaper Conflicts
- Choose simpler wallpapers
- Test UI visibility in all corners
- Consider blur or overlay effects

### Terminal Color Issues
- Follow standard terminal color semantics
- Test with syntax highlighting
- Ensure bright colors are actually brighter

## Theme Maintenance

1. **Version Control:** Track changes with git
2. **Screenshots:** Document how the theme looks
3. **Testing:** Regularly test with updates
4. **Documentation:** Keep color palette documented
5. **Feedback:** Test with other users

## Publishing Your Theme

1. **Clean up files** - Remove any test/temporary files
2. **Add README** with installation instructions
3. **Include screenshots** showing the theme in action
4. **Test on fresh system** to ensure completeness
5. **Share with community** for feedback and improvements

## Deploying Your Theme

### Theme Locations
- **Development**: Create themes in `/home/hipsterusername/PersonalRepos/omarchy/themes/`
- **Active Use**: Copy to `/home/hipsterusername/.config/omarchy/themes/` for the system to use

### Making Your Theme Available
```bash
# Copy your theme to the config directory
cp -r ~/PersonalRepos/omarchy/themes/your-theme-name ~/.config/omarchy/themes/

# The theme will now be available in your theme switcher
```

Remember: A good theme is not just visually appealing but also functional, accessible, and consistent across all applications.