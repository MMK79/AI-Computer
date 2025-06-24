* Store data in key and value pairs, Dictionary itself is mutable, but keys can only immutable $\xrightarrow{why?}$ Because dictionaries key need to be hash-able $\rightarrow$ Enable fast item lookup, fast membership test
* Instead of accessing with index, we access items in Dictionary with providing key = `dict[key]`
	* There is no order in dictionary
	* To not get an error if a key doesn't exist we can use `get(key, "default")` method
		* `"default"` can be anything, you will see it if the key that you provided doesn't exist
* `.update(dict)` to combine two dictionaries with each other
> [!important] You can Chain Actions
* `my_dict.keys()` return keys, `my_dict.values()` return values, `my_dict.items()` return pair of key and values