* Is a type of iterable object, however unlike others generators evaluate elements on demand! (instead of assembling them at once)
	* it won't store in memory, it doesn't have any state
	* instead of \[] we use () for generator comprehension
* Once you use generator it get exhausted (it doesn't know how to get back to previous state)