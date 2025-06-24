Truthiness: Evaluating expressions to be `True` or `False`, which help us to control the flow of the program
* int: `0` is `False`, all other numbers (include negatives) are `True`
* containers (`list`, `tuple`, `set`, `dict`): empty container equal `False`, with items equal `True`
* None: `False`
* To access it, we use `bool()`
	* Expressions that result in bool: `!=`, `==`, `>`, `<`, `<=`, `>=`
	* We have `and`, `or`, `not`
## Equality for Different types
* list: check items
	* `is` to check for identity, check if objects point into the same memory location
		* To differentiate between `None` value and empty list or etc.
# IF statement (Branching)
* Only run when the expression result into `True`
	* To check if your expression evaluate into bool, pass it into `bool()`
> [!warning] Don't use `if a == True:` it will work but it is not a good programming
* instead of del, use pop