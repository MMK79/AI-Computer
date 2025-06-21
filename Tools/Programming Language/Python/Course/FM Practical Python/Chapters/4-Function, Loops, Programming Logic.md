# Working with File
## Naming
* File name should all be lower case
* Word should separate with underscore
* Filenames should be short
> [!important] .pyc
> Compiled intermediary python code.
> > [!warning] Don't commit them to git
> > to delete them
> > `find . -name "*.pyc" -delete`
> > Or simpler way is to add them to your `.gitignore`
* `python filename` to run python file
> [!important] print() or logger for Debugging
> Logger module: Let you control how your output outside of program is presented
> Don't keep your prints in the code if you want to share it with others
## Output Formatting Tips
* `\n` new line, `\t` tab
* Pretty Print: `pprint()` in standard library so $\rightarrow$ `from pprint import pprint`