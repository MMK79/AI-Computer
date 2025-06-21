# Tuples
* Light-weight collection use to keep track of related but different item
* Are immutable, no change after you created them
* It is good for times that you want to pass your data, but data structure don't change in the process
* One item tuple = `(item,)`
* Tuple Unpacking: You can get multiple items out of a tuple at once
  > [!important] Number of argument on the left hand side (variables) need to match with number of items in tuple
* You can use underscore (\_) if you don't want to match the number but don't save it 
# Sets
* Mutable data type, that allow you to only store immutable items in them in a unsorted way
	* Store, only unique items in themselves $\xrightarrow{cause}$ Fast membership testing (They are fast)
	* No index available
* Have powerful functions like; union, intersect, etc.
* To create empty set: `set()`
* Can De-duplicate lists :D
> [!important] Shortcut to Check Mutability = `hash()`
> If it gets hash = immutable
> If it doesn't = mutable
* `add()` to add an item to a set, `discard()` to remove item from it
* `update(set)` to add a set to another set
# Dictionaries
* Store data in key and value pairs, Dictionary itself is mutable, but keys can only immutable $\xrightarrow{why?}$ Because dictionaries key need to be hash-able $\rightarrow$ Enable fast item lookup, fast membership test
* Instead of accessing with index, we access items in Dictionary with providing key = `dict[key]`
	* There is no order in dictionary
	* To not get an error if a key doesn't exist we can use `get(key, "default")` method
		* `"default"` can be anything, you will see it if the key that you provided doesn't exist
* `.update(dict)` to combine two dictionaries with each other
> [!important] You can Chain Actions
* `my_dict.keys()` return keys, `my_dict.values()` return values, `my_dict.items()` return pair of key and values