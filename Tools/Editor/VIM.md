# References
[Primeagen-github-site](https://theprimeagen.github.io/vim-fundamentals/) (you can access the link of videos through this link)
[Primeage-Youtube-playlist](https://youtube.com/playlist?list=PLm323Lc7iSW_wuxqmKx_xxNtJC_hJbQ7R&si=PRzGKaP-JyUGfVou)
[Setup-your-NeoVim-Kickstart-TJ](https://www.youtube.com/watch?v=m8C0Cq9Uv9o&t=3s) (Good way to start using NeoVim)
	[Learn Lua Basic](https://youtu.be/CuWfgiwI73Q?si=I4jX9z45FWfzKFil)

# How to use Vim?
* VIM
* NeoVim
* SpaceVim
* OniVim2
# Resource to learn Vim
* vimtutor
* vim-adventures
* ThePrimeagent's Youtube:
	* 6 part series
	* Learning lua plugin dev
	* VimRC
* In vim command mode `:h user <tab>`
# The Terminology
## Files, Buffers, Windows, Splits, and Tabs
* LiveOverflow's Video on Files $\rightarrow$ How vim handles files
### Buffer
A Buffer contains the text of the file and what you edit
`:h buffer` $\rightarrow$ help menu in vim for buffer
Representation of your file in memory, if you edit buffer it doesn't mean that you edited the file directly your but instead you are editing a buffer, when you write a buffer you are writing that buffer to the file and replacing it with whatever the context is it inside the buffer.
* Visual Representation of in Memory, Can be in disk, can be temporary
`:lua =vim.api.nvim_get_current_buf()`
###  Window
Contains a buffer to display. Windows can be closed but the underlying buffer can remain in memory.
`:h window`
`:lua =vim.api.nvim_get_current_win()`
### Tabs
A tab is like another viewport. you can have many windows|splits open per tab
`:h tab`
### Splits:
A split simply refers to splitting the viewport in N sections (various sizing and orientations available) to display windows.
`:h split`
### Help Menue
Help menu can be accessed by typing `:h<enter>`. There is so much documentation, that is pretty good, available. If you find yourself lost, RTFM (Read Through Friendly Manual OR Read The Fucking Manual)
### Motion
A command that moves the cursor `:h motion`
### Abbreviations
Ctrl+a will be abbreviated `<C-a>`. This is also how its referenced in VimL, Vim's editor language.
Enter will often be abbr as `<CR>`
Tab, Escape, and space will be `<tab>`, `<esc>`, `<space>`
When you see something that starts with a `:` that means it will execute a command.
* If your language have LSP (language server protocol) vim can use that
* For Java (JDK), IntelJ is much better than vim
# Modes
* Normal: Edit things
* Command: `:` in normal mode
* Insert: Type new things
* Visual: highlight things and change things
* Visual Line

## How to quit Insert mode
* `Esc` to get out of the mode that you are in to get back to Normal mode
* `C-c` as same as `esc` but have a difference
* `C-[` too

# Move in Lines
```bash
curl https://raw.githubusercontent.com/ThePrimeagen/vim-fundamentals/master/course-website/lessons/exercise-0-hjkl-x.md > exercise.md && vim exercise.md
```
* Don't be in a situation that you just hold something
* Vim will maintain cursor position, it can be move around base on your last known furthest cursor location
# Delete, Yank, Visual Mode
```bash
curl https://raw.githubusercontent.com/ThePrimeagen/vim-fundamentals/master/course-website/lessons/exercise-1-dyp.md > exercise.md && vim exercise.md
```
* instead of `dd` to delete a line you can `shift+v d` to delete a line, do as you please
* when you are you `Visual mode` and yank a partial part when you paste it, it will paste it in line
* In Vim when you delete `d` you also yank `y`
	* this is so great, when you want to change a position of a block of code instead of ctrl+c and then paste you simply delete it and paste it where you want.
* `:reg` keep what you delete and yank in a history, the last thing that you deleted/yanked is on top 
* yanks will preserve to one register, while deletes will be kept in order in history
	* when you press p what you actually doing is copying the context from `""` register and put it in your programs
# Insert Mode
```bash
curl https://raw.githubusercontent.com/ThePrimeagen/vim-fundamentals/master/course-website/lessons/exercise-2-insert.md > exercise.md && vim exercise.md
```
`i`: means in the inside, left side of your cursor
`a`: means on the outside, right side of your cursor
`I`: Start from first non-whitespace character in the line
`A`: End of the line, include whitespace too
`o`: makes a new line, respect the indenting of the language that you are using, and put you insert mode
`O`: makes a new line on above the line, respect indent, insert mode
* `o`, `O` most useful, `a`, `A` next, and in the last `i`, `I`
# Command Mode On
* instead of `zz` to recenter your vim, lets execute `:set scrolloff=8`, when you 8 lines away it automatically scroll for you
* instead of `dd` lines one by one you can do `<number>dd` to delete the amount of number of line that you want
	* You can also do `d<number>j`, with this you will delete 6 line downward
* to see the line number execute `:set number`
	* to see the number of line compare to the line that you currently at `:set relativenumber` or `:set rnu`
		* how to unset in vim `set no<command>`, `set <command>&`, `set <command>!`
* Vim don't save your settings
	* `vim ~/.vimrc`
	* neovim `:echo stadpath("config")`
		* `vim ~/.config/nvim/init.vim`
* `w` to save settings
* see your options
	* `:h options`
	* `:h <use-tab or C-d>`
		* `ctrl+n`, `ctrl+p` to go back and forth between the suggestions
	* `/<term>` to search for a term in a document
		* `n`, `N` back and forth
		* Another way to search for a keyword is, if you are currently in a position that word is exist there you can simply use `*` then the vim will show you the result for that word
			* for backward search instead of `*` you can use `#`
	* `ctrl+d` to move down in document
# Files and Navigation - NetRW
NetRW is the default browsing of the filesystem plugin. it is available in both Vim and NeoVim.
when Primeagen use file tree? create, delete, find a folder which don't remember the name + in js project with tons of index file fuzzy file finder are useless
* The thing that you see is a buffer, it is a representation of something underneath that you can interact with
* To get back to your file tree, without `:q + vim .` instead we use `:Ex` (explore view)
	* you can `:Vex` vertical explore to have your current file open and have the file tree open too, `:Sex` for horizontal view, in vim it is Split
		* open window of a same buffer, `C+w s` Split (horizontal) and `C+w v` to open vertical window
		* `Ctrl+w` make you go in window mode, and you can navigate with `hjkl` through them
			* quit current windows with `C+w q`
			* `C+w o` just keep the current one open
# Remap
`let mapleader = " "` what does it mean? what is a mapleader? special key that from now on should be known as leader
`nnoremap <leader>pv :Vev<CR>` what does it mean?
`n`: mode you're in, it could be `i` (insert mode), `t` (terminal), `v` (visual) and etc.
`nore`: stands for No Recursive Execution, don't use other command in this command, your remap of other side could execute more remap
```
imap xx yy
impa y zz
imap z aa

result of typing xx in insert mode after this remap
aaaaaaaa
```
`map`: it is a map command 
left-hand-side: `<leader>pv` (set of key to press for remap) + ` ` to separate them + right-hand-side `:Vex<CR>` (what will be executed when the left-hand-side is typed)
* For your changes in .vimrc to take place you need to source it: `so %`, % stands for my current buffer file
* as you execute commands it will stay in vim until you restart it, even if you delete it and source it, you need to exit and reopen to lose that command
* there is a time delay when you press the leader key or the start of remap key, this is a way of vim to give you time to use your remap, keep this in mind so you don't make remap on keys that have a important action
	* space is a good leader key cause you don't use it for navigation (it do the same thing as l key do)
# Edit
instead of opening file directly you can use `:e <filename>`, you can do some fuzzy finder with it `:e **/*` or anything else but it is just ok, for daily use you need something else
# Mark
* Global
`m <CapitalLetter>` in the line that you want to put mark
How to use it?
`' <your letter>`
* File level
`m <lower-case letter>` to make a mark inside a current buffer
* this mark only work inside your current buffer
	* to delete a specific mark you can use `delmark <letter>` or `delm <letter>`
* `%` always store your current file, `#` store your previous file, `ctrl+^` to switch between current file and previous file
# Jumplist
`:jumplist` then you can navigate through the places that you have been with `Ctrl+O` to go to the previous locations and `Ctrl+I` to go through the next files
# Plugin
## Plugin Manager
* VimL for vim plugins
* NeoVim use Lua for writing plugins
	* You can write plugins in VimL and use Typescript to convert them, Lua converter #qeustion
* Plugins in vim are repos that are setup in a way that work with vim
* All functions with `#` in them are special function, they are called autoload functions
* You can find the plugins that you want for vim from github repo and by simply placing them in your config minus the github start, by simply use the command `:PlugInstall` you will install the plugin
# Theme
Find the theme that you like, same as plugin install it and use it ;D
# Quickfix
* FZF would pipe ripgrep results into a quickfix list
* You have `grep` installed in any system
	* `:grep SOCKET **/*.c` it will show list of results when you press enter it will show you the first file of the results, you can use `!` to don't open any file, now that you are in the file to access the list that you already created you can simply use `copen` it will show you the previous list plus the command that resulted to the list, `cnext` and `cprev` to switch between the files of the list
		* `:cdo` allow you to do command across your quicklist list
			* `getqflist` and `setqflist`
# Search and Replace
```bash
curl https://raw.githubusercontent.com/ThePrimeagen/vim-fundamentals/master/course-website/lessons/exercise-3-search-and-replace.md > exercise.md && vim exercise.md
```
* `:set nohls`, `:set noic`, `:set hls ic`, highlight search result, incremental search show you how your search is working
	* `:set ic` don't work, use `:set incsearch` instead
* `/<term>` to search for a thing in file
* you can go in visual mode `v` select the region and then type `:` then you can search in that region
* `%s/<term>/<replace-term>`, search in whole file, you can do it in visual mode too
	* this command will replace them one at a time
	* to replace the whole thing you can `:s/<term>/<replace-term>/g` g for globally
		* to replace them one by one by asking you question you can use `:s/<term>/<replace-term>/gc`
	* to do it on the whole file you can use `:%s/<term>/<replace-term>/gc`
	* to do it on the whole project you can do `grep` and use `cdo` to change them globally on the whole project
# Macro
`q` to go in macro mode `<letter>` any letter to set the macro key to that letter then now you are recording your macro, when you done with your thing you press `q` again, and done.
to use the macro you simply `@<macro-letter>` , you can even use it multiple time by simply typing number of time you want to use it `<number>@<macro-letter>`
* go to the first non-white space in the line `_` or `^`
* go to the end of the line `$`
* `dt<sign/letter>` `t` for till
* `f<sign/letter>` to go to the next one of that thing that you said it
# Register
a key (character) to a stored value (string)
* some register are automatically filled for you and some of them are open for you to fill them the way you want
How to interact with register? `"`
What can it do? your macros are getting saved in the register key so you can get access to it, after you got access to it you can simply edit it the way you want and then again assign it to a different character or even overwrite the current one
How to access macros? `@<macro-assigned-character>`
# Advance Motion
```bash
curl https://raw.githubusercontent.com/ThePrimeagen/vim-fundamentals/master/course-website/lessons/exercise-6-motions.md > exercise.md && vim exercise.md
```
Way to Combine things:
$$Command\ \textcolor{red}{Count}\ Motion$$
## Horizontal Movement
* using `c` instead of `d`, it will delete the line and enter insert mode
* `_` go to the non-whitespace start of the line, you can use `^` to but there is a slight difference
* `0` go to the start of a line, even the whitespace
* `$` go to the end of the line
* `D` delete from the cursor to the end of the line
* `C` delete from the cursor to the end of the line + enter insert mode
* `S` delete the whole line, respect indenting, enter insert mode
* `s` delete the current character like `x` and enter insert mode
* `f<character>` find the character, you can go forward with `;` and go backward with `,`
* `t<character>` is like f, but instead of going on the character it will go to the character (before the character)
*  `F` and `T` are just simply `f` and `t` but in backward way
## Vertical Movement
* Rely on relative jumps
	* VimBeGood
* `{`, `}` to jump between white space of paragraphs
	* it will alter your jump list and will ruin your movement with `Ctrl+o` and `Ctrl+i`
	* usage of this motion completely depends on the code writer style, if they use space between line so much it will have no use to it, other way this can be so cool
* `Ctrl+d` jump down by half page, `Ctrl+u` jump up by half page
	* `[m / ]m` and `[M / ]M`, will move by function
* You can jump between pairs by using `%`
* You can delete inside the pairs by `i` and if you want to delete outside too by use of `a` 
	* `da{`, `di{`
* You can jump between your visual selection by `o`
 * You can delete the whole world from the inside by simply using `diw` if you want to delete everything that doesn't have whitespace you can simply use `diW`
 * To delete paragraphs you can use `dap` or `dip`
 * `=` auto indent base on rules
 * `r` for replace things
 * `Ctrl+v` multiple cursor