Class methods are shared among all class instances and all subclasses, they can be overwrite for a specific instance or in subclass.
* Need annotation over that method: `@classmethod`
```
    @classmethod
    def get_number_of_wheels(cls):
        return cls.number_of_wheels
```
* the `cls` enable you to get access to variables inside of the class
> [!important] `type()`, `isinstance()`, `issubclass()`
> to investigate about our objects nature
# Magic Methods / Dunder Methods / Double Underscore Functions
`__init__`
* If you want to save values in init you need to save them in the instance, how?
	* with `self`
`__str__`
* return string
* pass to end user, to know how this object is represented
`__repr__`
* return string
* should return a python code that maybe necessary to rebuild the object
* use for debugging, show for under the hood, other programmer