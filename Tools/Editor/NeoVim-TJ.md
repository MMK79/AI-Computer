Reference: [TJ-Neovim-Kickstart](https://youtu.be/m8C0Cq9Uv9o?si=mX5YQdirscFJJ8ty)
* Run `:Tutor` and read the document
* If you are familiar with NeoVim a little then go and run `:help`
	* You can use `<leader>sh` to search in NeoVim help document
* Each time you see a `Note` it introduce a new important concept
* You can test your options by `:lus vim.opt.number = false` for example
* Key map will help you to instead of typing in the command line adding the functionality to your fingertips so instead of typing `lua vim.diagnostic.goto_next` you simply `]d` simple!
* Instead of add functionality to our finger tips we can add functionality to when a special events happening (like EventListeners in JavaScripts) We call them Auto Commands in NeoVim
* We use Lazy as a Plugin Manager for NeoVim
	* run lazy `:Lazy`
		* most use thing is `:Lazy update`
* To install a plugin if it is on github just give the `owner/plugin` if it is from other places just give the whole url
* Many NeoVim Plugins use a setup function to Control When & How a plugin is loaded and lazy support this by `opt` if you use `opt = {}` means that lazy open this plugin with default setting
* You can manage plugins with more than just tables you can run a lua code whenever a plugin is actually loaded, lazy help you to handle when and how a plugin is loaded just like the setup
	* this help you to isolate your plugins from each other
* plugins can specify dependencies, dependencies are actually the same kinds of tables like the ones that we built before
* Language Server Protocol, NeoVim speaks the protocols of language server and needs to know both how to run and execute those external process as well as how to trigger different requests that you want to do
	* Start, Run, Control
* capabilities: you informing the LSP what the client (NeoVim) is capable of doing
* mason to install the Fucking LSP
	* brew install for neovim
* after mason install the Fucking LSP we need some way to connect those installation to NeoVim
	* simplest way, LSP config