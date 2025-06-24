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