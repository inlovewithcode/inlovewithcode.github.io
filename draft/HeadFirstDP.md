# Strategy Pattern

Duck Class

- quack
- display # override for each sub-class category

__[Problem]__

(Newly requested speacial features)

- quacking (optional) # would be bad to have in all the sub-classes

- fly (optional) # would be bad to have in all the sub-classes


(Since inheritance would, copy the cold --> destroys all dependents)


> Identify the aspect of your app that vary, and separate them from what stays the same.

(or)

> Take what varies and "encapsulate" it, so it won't effect the rest of the code

__[solution 1]__

3 classes

As usual parent class - Duck

* Duck class
* Flying Ducks class
* Quacking Ducks class

Q. How to get a Flying + Quacking class ??

> Program to interface, not to implementation

(or)

> NOTE: Use an interface to represent each behaviour

* Flying
	* DoFlyDucks
	* NoFlyDucks

* Quacking
	* QuackDucks
	* SqueakDucks
	* MuteDucks


