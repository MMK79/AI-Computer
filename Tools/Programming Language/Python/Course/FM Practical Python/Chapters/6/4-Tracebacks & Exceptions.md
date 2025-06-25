* read them from bottom to top
# Uncaught Exceptions Exit our Program
* Catch them with `try`, `except` block
* Be as specific with your exception as possible
# Types of Exceptions
* AttributeError: Raise when an attribute assignment or reference fail
* ImportError: Raise when the import module not found
* IndexError: Raise when the index of sequence is out of range
* KeyError: Raise when a key is not found in a dictionary
* KeyboardInterrupt: Raise when use hits interrupt key (`Ctrl+c`)
* NameError: Raise when a variable is not found in local or global scope
* SyntaxError: Raise by parser when a syntax error is encounter
* IndentationError: Raised when there is incorrect indentation
* ValueError: Raised when a function gets an argument of correct type but inappropriate value

> [!tip] `sys.exit()` from `sys` library
> To exit your program, instead of `ctrl+c`
> `sys.exit()` with no parameter will with `0` return code
> `sys.exit(int)` to exit with `1` return code (mean some sort of failure condition), you can even pass string to show in your console alongside with `1`
* `sys.exit()` generates a `SystemExit` exception, which inherits from the master `BaseException` class, which make it possible for clean-up handler (like; `finally`) to run.

* `finally`, is an optional block which will get run no matter what happen in `try`, `except`, and `else`
	* Good place for cleanup
# Exception Hierarchy
* list of built in python exception in [python document](https://docs.python.org/3/library/exceptions.html)
> [!important] Exceptions are Object too!
* Exception have inheritance too, like; `ZeroDevisionError` is a subclass of `ArithmeticError`, which is subclass of `Exception`, which itself is a subclass of `BasicException`
  Check the [link](https://docs.python.org/3/library/exceptions.html#exception-hierarchy)
> [!tip]Catch the most Specific Exception First!
> Don't catch `Exceptions`, and Definitely don't catch `BasicExceptions`
# Custom Exception
* create class with parent of `Exception`
* You can use `raise` too!