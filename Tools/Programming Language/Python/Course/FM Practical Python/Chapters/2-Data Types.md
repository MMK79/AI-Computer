Python is a Dynamic Language, You just create a variable without stating what kind of variable it will be, and even it can change through your program to another data type too (type does not need to be consistent);
```
x = 5 # no defenition that this x is integer
x = "hi" # change its type of value without doing anything
```
* It can cause bugs! $\xrightarrow{solution}$ You need to be careful with your variable naming; Be as explicit as you can be, Be Descriptive as possible
> [!important] Snake-Casing: all lower case, and separate with underscore (_)
# Variables in Python
* snake_case
* No special case at start of variable name
* Don't use any python special keyword/method name
```
list() # to create new empty list
list = "hi" # work fine
list() # you will get error cause what python interpreter doing now is:
"hi"() # which result to bug
```
## NoneType
You can define variable, without it having any value (good initializer)
## Useful REPL methods:
help(), type(), dir()
* dir(): will help you to know all of the methods that are available for that class/type
	* double under score methods, are not suppose to be used
	  `dir(str)`
* help(): see the python documentation without needing to open a browser
  `help(str)`, space to scroll down and q to quit
	* you can do this on a method specifically (more useful)
	  `help(str.find)`
# Numbers in Python
* int
* float; you have valid float which means `0.` (no syntax error, but confusing)
* complex; end with j, `12j`
> [!important] You can convert types with casting them
> `int(3.0)`, `float(3)`
* for integer division use `//` instead of `/` (float division)
* Parentheses to make sure of the order
> [!important] What is built in modules?
modules that you don't need to import to use
# Boolean
> [!warning] Everything in Python is an Object
> Even Booleans (True, False)

* Under the hood of python, Booleans are a subclass of integer, True = 1, False = 0
# String
* You can use both single quote, and double quote
	* But make sure they match
	* Prefer double quotes, or you can use `\` for not getting error
		* Single quotes can be nested inside double quotes
* For long quotes we use `"""`
	* `\n` symbol for new line, `\t` symbol for tab
* You can Concatenate Strings with `+`
	* Don't use it for a large chunk
* Be comfortable with f strings
* Strings are immutable
	* if you want to keep the change you need to assign them to variable
# Print
* You can print multiple things together with `,` separate them
# List
* Create empty list: `[]`(mostly use), `list()` (when you are converting)
* Find the length of the list: `len()`
* Python is a Zero index
* List is mutable, you can change it indexes
* To sort temporary `sorted(L)` , To sort and mutate it `L.sort()`
* To reverse a list temporary `sorted(L, reverse=True)`, to reverse and mutate `L.reverse()`
* Add items to list: `list.append(value)`
* Add item in a specific location: `list.insert(index, value)`
* To check if a item in a list: `in`