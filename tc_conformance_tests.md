# MISSING CONFORMANCE TESTS

Distributing type information
 - Stub files (https://github.com/python/typing/issues/1605)


# MISSING CHAPTERS IN TYPING SPEC

Module-level `__getattr__`
Module-level Final constants for module protocols

Metaclasses
* Class objects vs. class instances
* Metaclass hierarchy and type
* `__init_subclass__`

Class Overrides
* The LSP
* LSP exemptions
* MRO
* Allowed and disallowed overrides
  - types (invariance, read-only, properties vs. attributes, etc.)
  - type qualifiers (class variables, final variables, etc.)
* Overrides within a class hierarchy
* Overrides within multiple inheritance
* super()
* Inheriting from Any

Callables
* Positional-only parameters
* Keyword-only parameters
* Argument defaults
* Annotating *args and **kwargs
* Subtyping rules for callables

Methods
* Instance, class, and static methods
* self and cls parameters
* Binding a class or type to a method

Class and Instance Variables
* Including metaclass instance variables

Constructors
* Including: https://github.com/python/typing/issues/1563#issuecomment-1918734439

Descriptors
* Descriptors
* Properties
* Asymmetric descriptors

Enum
* Enum and type checking

Type Narrowing
* Narrowing on assignment
* Narrowing rules for Any
* Built-in type guards

Abstract classes

Overloads

Class & function decorators


