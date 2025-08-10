# Neovim Theme Configuration

## File Format
Lua table format for LazyVim configuration

## File Location
`theme-name/neovim.lua`

## Configuration Patterns

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
- [ ] LazyVim configuration with colorscheme specified
- [ ] Theme plugin properly declared if external
- [ ] Plugin name matches colorscheme name
- [ ] Configuration syntax is valid Lua
- [ ] Any required setup() calls are included
- [ ] Colors align with overall theme