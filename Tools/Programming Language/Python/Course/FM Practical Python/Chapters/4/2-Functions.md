* Allow us to write a reusable code, and avoid copy and pasting
* Create a function: `def function_name(arguments=defaults):`
## Returns
* Everything that is indented after the function belong to that function
* Functions return None by default
		* To return more than one value $\rightarrow$ Use Tuple
## Arguments
* The arguments that don't have default value need to be provided, and the argument that have default value don't need to be provided (No error)
	* Required arguments need to be first, optional argument need to be last $\xrightarrow{else}$ Error
	* You can call function by providing the labels and it works fine

> [!important] Don't use mutable types as default
> Instead use placeholders (None)
## Scope
* When you call a function you create a new environment and function variables only have meaning inside that environment not anywhere else
* The only times that you can use a variable from outside of a function inside a function is for when that variable is a constant
	* Constant: all caps lock, with underscore