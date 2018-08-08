# Short Notes on Python - OOPS


## OOPs - Definitions

* Class - is a template model for creating classes.
* Class Variables - variables shared by all object
* Instance Variables - variable specific to a object, gets created during object creation
* Data members - Class/Instance Variables - that hold some data related to that class
* Method - A special function related to a class.
* Instance - an **individual object** of a class.
* Instantiation - the task of creating an instance of a class
* Object - A uniq instance of a **data structure** that is defined by a class. This contains 1. Data Members(Instance & Class variables) 2. Methods

* Operator Overloading - the assignment of more than one function to a particular operator.

* Inheritance - transfer of **characteristics** of a class to other class that its derived from it.

* Class Variables are accessed as <<class_name>>.<<class_variable_name>>

## OOPs - way of working with variables

* getattr(obj, name[, default]) - to get a variable from an obj
* hasttr(obj, name) 		- return True/False - to check if the obj has a variable
* setattr(obj, name, value) 	- setting a new value to a obj's attribute
* delattr(obj, name)		- deleting the obj variable



## OOPs - Built in Class Attributes

* __dict__ 	- contains class name space
* __doc__ 	- class documentation
* __name__ 	- class name
* __module__	- module name which that this object's class
* __bases__	- empty tuple/order of occurrence of its base class list


## Destroying Objects (Garbage Collection)

* When an object's reference count reaches zero, Python collects it automatically.


## Class Inheritance

* A child class can also override data members and methods from the parent
* Functions - issubclass() or isinstance() are used to check a relationships of two classes and instances.

## Data Hiding

* attributes with a double underscore prefix
