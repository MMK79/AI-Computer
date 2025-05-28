# Primeagen-init.lua

Reference: [Primeagen-Neovim-from-Scratch](https://youtu.be/w7i4amO_zaE?si=T0PUaLsqCpuR00ox)
[Repo](https://github.com/ThePrimeagen/init.lua)
* `:h rtp` will show you paths that NeoVim will look for the config, RuntimePath
## Create Config file
1. You need to be in home, then simply go to config `cd ~/.config`
2. make the directory `mkdir nvim`
3. go in the directory `cd nvim`
4. now go in NetWr basic file navigation for nvim and vim by simply `nvim .`
5. `%` in file navigation form to make file `% init.lua` now you have your config file, write some lua code in it for fun `print("Hello World from init.lua")`
# Create your own Config folder
1. `d` in file navigation form to make directory `d lua`
	* Any directory within `lua` directory is requirable by lua
2. Now cd into the folder by `cd lua`
3. Now again create folder for your own config by simply `d <name-you-want>`
4. cd into the folder `cd <name-you-put>`
5. Create your init.lua in this folder too `% init.lua`
6. put something in it `print("Hello World from <name-you-put>")`
7. Now you need to require it in your main file so go to `nvim ~/.config/nvim/init.lua` and:
```
require("<name-you-put>")
```

## Create remap config file
1. go to your created folder `cd ~/.config/nvim/lua/<name-you-put>`
2. create the file `% remap.lua`
```
vim.g.mapleader = " " # set map leader to space
vim.keymap.set("n", "<leader>pv", vim.cmd.Ex) # n for normal mode, second part is what you want to set, third part is the thing that will be run when you press the second part, secnod part = left-hand-side, third part = right-hand-side
```
3. source it so it apply the changes by `:so`
4. you need to put it into the init.lua so it get source every time you open neovim by simply `cd ~/.config/nvim/lua/<name-you-put>` then you need to open your config `nvim init.lua` now require your key-map config by adding this line to your config `require("remap.lua")`
## Set up Plugin manager and FuzzyFinder
* You can use packer.nvim or if you using kickstart it is using Lazy
1. go to the lua folder and make new file `cd ~/.config/nvim/lua/<name-you-put>` 
2. create the new file in `nvim .` after this `% packer.lua` 
3. copy the content from the internet into it
4. quite and reopen nvim to install packer
5. `:so` to source the file
6. `:PackerSync`

to install a fuzzy finder which we will use Telescope by TJ:
1. after grabbing what you need to paste from telescope repo go to `packer.lua` file that you made and paste the thing in it
2. `:so` source it
3. `:PackerSync` to install the plugin
* Now you installed telescope but you don't have any way to use it except command So time to do some remap
* create a directory after `~/.config/nvim` and `d after` then go in after and make directory call plugin `d plugin` then go in the folder and make a file `telescope.lua` now set your keybinding
```
local builtin = require('telescope.builtin')
vim.keymap.set('n', '<leader>pf, builtin.find_files, {}) # work for every directory
vim.keymap.set('n', '<C-p>, builtin.git_files, {}) # only work in directories that have git set in them
vim.keymap.set('n', '<leader>ps, function()
	builtin.grep_string({ search = vim.fn.input("Grep > ")})
end)
```

## Set up ColorScheme
copy and paste the code from the color scheme repo into your `packer.lua` file and `=ap` for indenting, `:so` and then `:PackerSync` to install color schema
to fix everything that has been ruined go to `~/.config/nvim/after/plugin` create a new file `% colors.lua`, now we want to set the color scheme and set a transparent background
```
function ColorMyPencils(color)
	color = color or 'rose-pine'
	vim.cmd.colorscheme(color) # set the color scheme

	vim.api.nvim_set_hl(0, "Normal", { bg = "none"})
	vim.api.nvim_set_hl(0, "NormalFloat", { bg = "none"}) # set the transparent background
end

ColorMyPencils()
```
But the colors are still not right, what we need now is tree-sitter
What is tree-sitter? allows for an amazingly fast parsing of your code that it is in your editor right now and it will build and incremental tree so every change will change a small part of it, and it provides highlighting, indenting, and it is incredibly fast

again you need to go and add the github repo instruction to the `packer.lua` file that you previously built
```
use('nvim-treesitter/nvim-treesitter', {run = ':TSUpdate'})
```
Now you need to set it up
again go to your `~/.config/nvim/after/plugin` and make a new file `% treesitter.lua` 
paste the things from the internet, if you need any other language just simply add them in `ensure_install` 
* Go and install `treesitter-playground` and then `:TSPlaygroundToggle`
	* you will get access to actual AST that exist inside your editor
		* You can use this to write your own plugin

## Harpoon
1. install harpoon by putting its code in `packer.lua`
2. `PackerSync` to install it
3. make a config file for harpoon in `~/.config/nvim/after/plugin` + `% harpoon.lua`
```
local mark = require("harpoon.mark")
local ui = require("harpoon.ui")

vim.keymap.set("n", "<leader>a", mark.add_file)
vim.keymap.set("n", "<C-e>", ui.toggle_quick_menu)

vim.keymap.set("n", "<C-h>", fucntion() ui.nav_file(1) end)
vim.keymap.set("n", "<C-t>", fucntion() ui.nav_file(2) end)
vim.keymap.set("n", "<C-n>", fucntion() ui.nav_file(3) end)
vim.keymap.set("n", "<C-s>", fucntion() ui.nav_file(4) end)
```
## Undotree
1. install undotree by putting its code in `packer.lua`
2. `PackerSync` to install it
3. make a config file for harpoon in `~/.config/nvim/after/plugin` + `% undotree.lua`
```
vim.keymap.set("n", "<leader>u", vim.cmd.UndotreeToggle)
```
## Fugitive
1. install Fugitive by putting its code in `packer.lua`
2. `PackerSync` to install it
3. make a config file for harpoon in `~/.config/nvim/after/plugin` + `% fugitive.lua`
```
vim.kepmap.set("n", "<leader>gs", vim.cmd.Git)
```
# Set up LSP
* Go to [LSP-Zero](https://github.com/VonHeikemen/lsp-zero.nvim)
1. install Zero LSP plugins by putting its code in `packer.lua`
2. `PackerSync` to install it
3. make a config file for harpoon in `~/.config/nvim/after/plugin` + `% lsp.lua`
4. now you can config it the way you want, the LSP zero have a base config, Primeagen use his own config
	* he use some keybinding for the current buffer that his on, which means that key maps will only live for one buffer, which means if you have a buffer that lsp is activate on it it will use the key maps of lsp instead of vim, and if you are in a buffer that don't have lsp set up for it, the key maps will doing their default thing
* LSP use Mason under the hood to manage packages, you can uninstall and install packages with Mason for your LSP
# Setup Editor settings
`cd ~/.config/nvim/lua/<name-you-put>` and create a file `% set.lua`
you need to require this file
`cd ~/.config/nvim/lua/<name-you-put>` and then `nvim init.lua` and add `require("<name-you-put>.set`
set.lua config:
```
-- Fat Cursor
vim.opt.guicursor = "" 

-- Line number + relative line number
vim.opt.nu = true
vim.opt.relativenumber = true

-- Indenting space
vim.opt.tabstop = 4
vim.opt.softtabstop = 4
vim.opt.shiftwidth = 4
vim.opt.expandtab = true

vim.opt.smartindent = true

vim.opt.wrap = false

-- Don't need Vim backups, but want my undotree plugin to access long running undos
vim.opt.swapfile = false
vim.opt.backup = false
vim.opt.undodir = os.getenv("HOME") .. "/.vim/undodir"
vim.opt.undofile = true

-- no highlighted search, but having increamental serach
vim.opt.hlsearch = false
vim.opt.incsearch = true

vim.opt.termguicolors = true

-- Automatic Scroll
vim.opt.scrolloff = 8
vim.opt.signcolumn = "yes"
vim.opt.isfname:append("@-@")

-- Fast Update time
vim.opt.updatetime = 50

-- Color column
vim.opt.colorcolumn = "80"

-- Set leader key
vim.g.mapleader = " "
```

# Remap keys
```
vim.g.mapleader = " "
vim.keymap.set("n", "<leader>pv", vim.cmd.Ex)

-- move the highlighted regions
vim.keymap.set("v", "J", ":m '>+1<CR>gv=gv")
vim.keymap.set("v", "K", ":m '<-2<CR>gv=gv")

-- keep your cursor in place
vim.keymap.set("n", "J", "mzJ`z")
-- move half page and keep the cursor in the middle
vim.keymap.set("n", "<C-d>", "<C-d>zz")
vim.keymap.set("n", "<C-u>", "<C-u>zz")
vim.keymap.set("n", "n", "nzzzv")
vim.keymap.set("n", "N", "Nzzzv")
vim.keymap.set("n", "<leader>zig", "<cmd>LspRestart<cr>")

-- Keep your yank buffer in the by sending the highlighted place to the void register
vim.keymap.set("x", "<leader>p", [["_dP]])

-- yank into the clipboard
vim.keymap.set({"n", "v"}, "<leader>y", [["+y]])
vim.keymap.set("n", "<leader>Y", [["+Y]])

-- delete into the void register
vim.keymap.set({"n", "v"}, "<leader>d", "\"_d")

-- This is going to get me cancelled
vim.keymap.set("i", "<C-c>", "<Esc>")

vim.keymap.set("n", "Q", "<nop>")
-- switch project
vim.keymap.set("n", "<C-f>", "<cmd>silent !tmux neww tmux-sessionizer<CR>")
vim.keymap.set("n", "<leader>f", vim.lsp.buf.format)

-- quick list navigation
vim.keymap.set("n", "<C-k>", "<cmd>cnext<CR>zz")
vim.keymap.set("n", "<C-j>", "<cmd>cprev<CR>zz")
vim.keymap.set("n", "<leader>k", "<cmd>lnext<CR>zz")
vim.keymap.set("n", "<leader>j", "<cmd>lprev<CR>zz")

-- replace the world that you are currently on
vim.keymap.set("n", "<leader>s", [[:%s/\<<C-r><C-w>\>/<C-r><C-w>/gI<Left><Left><Left>]])
-- make files executable
vim.keymap.set("n", "<leader>x", "<cmd>!chmod +x %<CR>", { silent = true })

vim.keymap.set(
    "n",
    "<leader>ee",
    "oif err != nil {<CR>}<Esc>Oreturn err<Esc>"
)

vim.keymap.set(
    "n",
    "<leader>ea",
    "oassert.NoError(err, \"\")<Esc>F\";a"
)

vim.keymap.set(
    "n",
    "<leader>ef",
    "oif err != nil {<CR>}<Esc>Olog.Fatalf(\"error: %s\\n\", err.Error())<Esc>jj"
)

vim.keymap.set(
    "n",
    "<leader>el",
    "oif err != nil {<CR>}<Esc>O.logger.Error(\"error\", \"error\", err)<Esc>F.;i"
)

vim.keymap.set("n", "<leader>vpp", "<cmd>e ~/.dotfiles/nvim/.config/nvim/lua/theprimeagen/packer.lua<CR>");
vim.keymap.set("n", "<leader>mr", "<cmd>CellularAutomaton make_it_rain<CR>");

vim.keymap.set("n", "<leader><leader>", function()
    vim.cmd("so")
end)

```