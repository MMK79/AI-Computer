# For
* `in` keyword combination with `for` loop, to iterate over all elements in your iterable
  `for i in list:`
> [!important] Loops don't have their own environment like functions
> If you create a variable inside a loop it will exist even after your loop run
* range function: let you generate range of numbers `range(start, stop, step)`
	* you actually start at your start point, but you will stop before your stop point
> [!important] range is a Generator type
> In python 2 it would actually return all the values and save them in memory (Very inefficient)
> But in python 3 it won't create that data structure, and it only work when you use it in a loop
* Use `enumerate` to keep track of index of a list, and its value
	* `enumerate` return a tuple
		* you can use tuple unpacking on it
# While
* `while expression:` expression need to be evaluated to bool
	* Be careful that your expression at some point become `False`, or your while loop will go forever
# Break & Continues
To stop inside loop use `break`, to stop inside function use `return`
* `break` will quit the inner loop