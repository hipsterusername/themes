# Neovim Theme Configuration

## File Format
Lua table format for LazyVim configuration

## File Location
`theme-name/neovim.lua`

## Configuration Patterns

UNLESS INSTRUCTED OTHERWISE, DEFAULT TO PATTERN 5


### Pattern 1: Simple Built-in Theme
```lua
return {
  { "LazyVim/LazyVim", opts = { colorscheme = "theme-name" } },
}
```

### Pattern 2: External Plugin Theme
```lua
return {
  { "author/theme-name.nvim" },
  { "LazyVim/LazyVim", opts = { colorscheme = "theme-name" } },
}
```

### Pattern 3: Plugin with Configuration
```lua
return {
  {
    "author/theme-name.nvim",
    opts = {
      -- Theme-specific options
      style = "dark",
      transparent = false,
    },
  },
  { "LazyVim/LazyVim", opts = { colorscheme = "theme-name" } },
}
```

### Pattern 4: Complex Setup with Overrides
```lua
return {
  {
    "author/theme-name.nvim",
    lazy = false,
    priority = 1000,
    config = function()
      require("theme-name").setup({
        -- Configuration options
        style = "dark",
        colors = {
          bg = "#1e1e2e",
          fg = "#cdd6f4",
        },
        highlights = {
          -- Custom highlight overrides
          Normal = { bg = "#1e1e2e" },
          Comment = { fg = "#6c7086", italic = true },
        },
      })
    end,
  },
  { "LazyVim/LazyVim", opts = { colorscheme = "theme-name" } },
  
  -- Optional: Icon color overrides
  {
    "echasnovski/mini.icons",
    opts = {
      style = "glyph",
    },
    init = function()
      -- Custom icon colors
    end,
  },
}
```

### Pattern 5: Complete Custom Colorscheme (Recommended)
For maximum control and consistency with your theme, create a fully custom colorscheme using a function that sets all highlights manually:

```lua
return {
  {
    "LazyVim/LazyVim",
    opts = {
      colorscheme = function()
        -- Your theme color palette
        local colors = {
          -- Base colors
          bg0 = '#1c1f26',    -- Main background
          bg1 = '#2c2f36',    -- Slightly lighter background
          bg2 = '#3c3f46',    -- UI elements background
          bg3 = '#4c4f56',    -- Selection/highlight background
          bg4 = '#5c5f66',    -- Inactive elements
          bg5 = '#6c6f76',    -- Comments/subtle text
          
          -- Foreground colors
          fg0 = '#e8e8e8',    -- Main text
          fg1 = '#d8d8d8',    -- Slightly dimmed text
          fg2 = '#c8c8c8',    -- Subdued text
          
          -- Accent colors (customize to match your theme)
          primary = '#7ea67c',    -- Primary accent
          secondary = '#7ec8c8',  -- Secondary accent
          warning = '#d4af37',    -- Warning/yellow
          error = '#cd9575',      -- Error (soft, not harsh red)
          info = '#6b8cae',       -- Info/blue
          hint = '#9b8aa0',       -- Hint/purple
        }

        -- Reset highlighting
        vim.cmd('highlight clear')
        if vim.fn.exists('syntax_on') then
          vim.cmd('syntax reset')
        end
        
        vim.o.termguicolors = true
        vim.o.background = 'dark'  -- or 'light'
        vim.g.colors_name = 'your-theme-name'
        
        local hl = vim.api.nvim_set_hl
        
        -- Editor highlights
        hl(0, 'Normal', { fg = colors.fg0, bg = colors.bg0 })
        hl(0, 'NormalFloat', { fg = colors.fg0, bg = colors.bg1 })
        hl(0, 'FloatBorder', { fg = colors.secondary, bg = colors.bg1 })
        hl(0, 'Cursor', { fg = colors.bg0, bg = colors.warning })
        hl(0, 'CursorLine', { bg = colors.bg1 })
        hl(0, 'CursorLineNr', { fg = colors.warning, bold = true })
        hl(0, 'LineNr', { fg = colors.fg1 })
        hl(0, 'Visual', { bg = colors.bg2 })
        hl(0, 'Search', { fg = colors.bg0, bg = colors.warning })
        hl(0, 'IncSearch', { fg = colors.bg0, bg = colors.primary })
        hl(0, 'MatchParen', { fg = colors.secondary, bold = true })
        
        -- Syntax highlighting
        hl(0, 'Comment', { fg = colors.bg5, italic = true })
        hl(0, 'Constant', { fg = colors.secondary })
        hl(0, 'String', { fg = colors.primary })
        hl(0, 'Number', { fg = colors.secondary })
        hl(0, 'Boolean', { fg = colors.secondary })
        hl(0, 'Identifier', { fg = colors.fg0 })
        hl(0, 'Function', { fg = colors.info })
        hl(0, 'Statement', { fg = colors.warning })
        hl(0, 'Keyword', { fg = colors.warning })
        hl(0, 'PreProc', { fg = colors.hint })
        hl(0, 'Type', { fg = colors.info })
        hl(0, 'Special', { fg = colors.fg1 })
        hl(0, 'Error', { fg = colors.error, bold = true })
        hl(0, 'Todo', { fg = colors.warning, bold = true })
        
        -- UI elements
        hl(0, 'StatusLine', { fg = colors.fg0, bg = colors.bg2 })
        hl(0, 'TabLineSel', { fg = colors.warning, bg = colors.bg0, bold = true })
        hl(0, 'Pmenu', { fg = colors.fg0, bg = colors.bg1 })
        hl(0, 'PmenuSel', { fg = colors.warning, bg = colors.bg3, bold = true })
        hl(0, 'SignColumn', { fg = colors.primary, bg = colors.bg0 })
        
        -- Diagnostics
        hl(0, 'DiagnosticError', { fg = colors.error })
        hl(0, 'DiagnosticWarn', { fg = colors.warning })
        hl(0, 'DiagnosticInfo', { fg = colors.info })
        hl(0, 'DiagnosticHint', { fg = colors.hint })
        
        -- Git signs
        hl(0, 'GitSignsAdd', { fg = colors.primary })
        hl(0, 'GitSignsChange', { fg = colors.warning })
        hl(0, 'GitSignsDelete', { fg = colors.error })
        
        -- Treesitter highlights (modern syntax highlighting)
        hl(0, '@variable', { fg = colors.fg0 })
        hl(0, '@variable.builtin', { fg = colors.secondary })
        hl(0, '@constant', { fg = colors.secondary })
        hl(0, '@string', { fg = colors.primary })
        hl(0, '@function', { fg = colors.info })
        hl(0, '@keyword', { fg = colors.warning })
        hl(0, '@type', { fg = colors.info })
        hl(0, '@comment', { fg = colors.bg5, italic = true })
        hl(0, '@punctuation', { fg = colors.fg1 })
        
        -- Terminal colors
        vim.g.terminal_color_0 = colors.bg1
        vim.g.terminal_color_1 = colors.error
        vim.g.terminal_color_2 = colors.primary
        vim.g.terminal_color_3 = colors.warning
        vim.g.terminal_color_4 = colors.info
        vim.g.terminal_color_5 = colors.hint
        vim.g.terminal_color_6 = colors.secondary
        vim.g.terminal_color_7 = colors.fg1
        vim.g.terminal_color_8 = colors.bg4
        vim.g.terminal_color_9 = colors.error
        vim.g.terminal_color_10 = colors.primary
        vim.g.terminal_color_11 = colors.warning
        vim.g.terminal_color_12 = colors.info
        vim.g.terminal_color_13 = colors.hint
        vim.g.terminal_color_14 = colors.secondary
        vim.g.terminal_color_15 = colors.fg0
      end,
    },
  },
}
```

**Advantages of Pattern 5 (Custom Colorscheme):**
- **Perfect consistency** with your theme colors across all UI elements
- **No external dependencies** - theme works immediately without downloading plugins
- **Complete control** over every highlight group
- **No harsh reds** - use soft, themed colors for errors/warnings
- **Comprehensive coverage** including LSP, Git, Treesitter, and modern plugins
- **Easy maintenance** - all colors defined in one place
- **Theme coherence** - ensures Neovim matches your system theme perfectly

**When to use each pattern:**
- **Pattern 1-4**: When you want to use an existing popular theme
- **Pattern 5**: When creating custom themes or when you need perfect color consistency

## Common Theme Plugins

### Catppuccin
```lua
return {
  { "catppuccin/nvim", name = "catppuccin" },
  { "LazyVim/LazyVim", opts = { colorscheme = "catppuccin" } },
}
```

### Tokyo Night
```lua
return {
  { "folke/tokyonight.nvim" },
  { "LazyVim/LazyVim", opts = { colorscheme = "tokyonight" } },
}
```

### Gruvbox
```lua
return {
  { "ellisonleao/gruvbox.nvim" },
  { "LazyVim/LazyVim", opts = { colorscheme = "gruvbox" } },
}
```

### Everforest
```lua
return {
  { "sainnhe/everforest" },
  { "LazyVim/LazyVim", opts = { colorscheme = "everforest" } },
}
```

### Rose Pine
```lua
return {
  { "rose-pine/neovim", name = "rose-pine" },
  { "LazyVim/LazyVim", opts = { colorscheme = "rose-pine" } },
}
```

### Nord
```lua
return {
  { "shaunsingh/nord.nvim" },
  { "LazyVim/LazyVim", opts = { colorscheme = "nord" } },
}
```

### Kanagawa
```lua
return {
  { "rebelot/kanagawa.nvim" },
  { "LazyVim/LazyVim", opts = { colorscheme = "kanagawa" } },
}
```

## Theme Configuration Options

### Common Options
```lua
{
  style = "dark",           -- or "light", "auto"
  transparent = false,      -- Transparent background
  terminal_colors = true,   -- Set terminal colors
  italic_comments = true,   -- Italic comments
  dim_inactive = false,     -- Dim inactive windows
  borders = true,          -- Show borders
}
```

### Theme-Specific Options

**Catppuccin:**
```lua
{
  flavour = "mocha",  -- latte, frappe, macchiato, mocha
  background = {
    light = "latte",
    dark = "mocha",
  },
}
```

**Tokyo Night:**
```lua
{
  style = "night",  -- storm, night, moon, day
  light_style = "day",
  transparent = false,
}
```

**Gruvbox:**
```lua
{
  contrast = "medium",  -- hard, medium, soft
  palette_overrides = {},
  overrides = {},
}
```

## Custom Highlight Overrides

Add custom highlights to match your theme:
```lua
highlights = {
  Normal = { bg = "#1e1e2e", fg = "#cdd6f4" },
  Comment = { fg = "#6c7086", italic = true },
  Keyword = { fg = "#cba6f7", bold = true },
  String = { fg = "#a6e3a1" },
  Function = { fg = "#89b4fa" },
  Variable = { fg = "#f5e0dc" },
  -- UI Elements
  StatusLine = { bg = "#313244", fg = "#cdd6f4" },
  VertSplit = { fg = "#45475a" },
  LineNr = { fg = "#6c7086" },
  CursorLine = { bg = "#313244" },
  -- Diagnostic
  DiagnosticError = { fg = "#f38ba8" },
  DiagnosticWarn = { fg = "#f9e2af" },
  DiagnosticInfo = { fg = "#89b4fa" },
  DiagnosticHint = { fg = "#a6e3a1" },
}
```

## MiniIcons Color Configuration

For custom file/folder icon colors:
```lua
{
  "echasnovski/mini.icons",
  opts = {
    style = "glyph",
  },
  init = function()
    require("mini.icons").setup({
      default = {
        file = { color = "#89b4fa" },
        folder = { color = "#f9e2af" },
      },
      extension = {
        lua = { color = "#89b4fa" },
        js = { color = "#f9e2af" },
        ts = { color = "#89b4fa" },
        -- Add more as needed
      },
    })
  end,
}
```

## Best Practices

1. **Plugin Loading**: Set `lazy = false` and `priority = 1000` for themes
2. **Consistency**: Match colors with terminal theme
3. **Testing**: Test in different file types (code, markdown, config files)
4. **Performance**: Avoid heavy computations in config functions
5. **Fallback**: Ensure theme works even if plugin fails to load

## Minimal Example
```lua
return {
  { "LazyVim/LazyVim", opts = { colorscheme = "default" } },
}
```

## Full Featured Example
```lua
return {
  {
    "catppuccin/nvim",
    name = "catppuccin",
    lazy = false,
    priority = 1000,
    config = function()
      require("catppuccin").setup({
        flavour = "mocha",
        transparent_background = false,
        show_end_of_buffer = false,
        term_colors = true,
        compile_path = vim.fn.stdpath("cache") .. "/catppuccin",
        styles = {
          comments = { "italic" },
          functions = { "bold" },
          keywords = { "italic" },
        },
        integrations = {
          cmp = true,
          gitsigns = true,
          treesitter = true,
          mini = true,
        },
      })
    end,
  },
  { "LazyVim/LazyVim", opts = { colorscheme = "catppuccin" } },
}
```

## Validation Checklist

### For External Themes (Patterns 1-4):
- [ ] LazyVim configuration with colorscheme specified
- [ ] Theme plugin properly declared if external
- [ ] Plugin name matches colorscheme name
- [ ] Configuration syntax is valid Lua
- [ ] Any required setup() calls are included
- [ ] Colors align with overall theme

### For Custom Themes (Pattern 5):
- [ ] LazyVim configuration with colorscheme function
- [ ] Color palette includes all necessary base colors (bg0-bg5, fg0-fg2)
- [ ] Accent colors match your theme's palette exactly
- [ ] All essential highlight groups are defined (Normal, Comment, String, Function, etc.)
- [ ] Diagnostic colors use soft/themed colors (avoid harsh reds)
- [ ] Terminal colors are set to match the theme
- [ ] Treesitter highlights are included for modern syntax highlighting
- [ ] Function properly resets existing highlights
- [ ] colors_name is set to your theme name
- [ ] Background is set appropriately ('dark' or 'light')