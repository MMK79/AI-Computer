Object Oriented Programming (OOP) is a language model (paradigm) in which properties/behavior are organized into "Object", and we provide methods for these objects to communicate with each other.
# What is Object?
Anything can be Object; function, variable, property, class, etc.
* At the end of the day, every expression that you write, will get evaluate to something, that something is an object, which have some type, that type determine what methods you can use on it, or what property that object will have.
* Every Object have:
	* Attribute
	* Method
* You can use python without any OOP, as a script language or procedural, but OOP will help you to organize your code better
# Classes vs. Instances
* Class is a recipe of a object itself
* Instance is when you call that class and give it a value base on its instruction
Exp:
`int` is a Class/Type, `x = 5`; `x` is an instance of a `int` class
## `self`
`self` is used inside classes to refer to a bound instance variable or object.
* `self` refer to an instance
* All instance methods of a class get `self` as their first argument
* 2 important errors and its cause:
	* `start() missing 1 required positional argument: 'self'` $\xrightarrow{because}$ You call a method of a class, call a instance of a class without creating it and give it `self`
	* `start() takes 0 positional argument but 1 was given` $\xrightarrow{because}$ Call a method that pass `self` under the hood, but your method don't get self.