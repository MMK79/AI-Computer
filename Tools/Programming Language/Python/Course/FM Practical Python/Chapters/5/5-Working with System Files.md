* There are different mods to read a file `open()`
	* `r`: open in read mode (default)
	* `w`: open for writing, truncating the file first (empty it)
	* `x`: exclusive creation, fail if the file already exist
	* `a`: open for writing, but appending to the end of the file if it already exist
	* `b`: binary mode
	* `t`: text mode (default)
	* `+`: open a list file for updating (reading and writing)
example:
`my_file = open("my_file.txt", "a")`
> [!important] `close()` after your done with an open file $\xrightarrow{so}$ program don't leave open files handles dangling.

question: What happens if you have a open file and your program crash in middle of it?
answer: Context Manager
# Context Manager
`with` keyword, it takes care of file for you + any clean up if your program throw exceptions
* Think of it as a code block, that auto-magically provisions a resource before your code runs and afterward
example:
```
with open("my_text.txt", "a") as my_file:
	contents = my_file.read()
```
> [!tip] Work with json file $\rightarrow$ `import json`