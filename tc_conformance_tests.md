# MISSING CONFORMANCE TESTS

Distributing type information
 - Stub files (https://github.com/python/typing/issues/1605)


# MISSING CHAPTERS IN TYPING SPEC

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
* The meaning of `...`
* Positional-only parameters
  - `self` and `cls`
* Keyword-only parameters
* Argument defaults
* Annotating `*args` and `**kwargs`
* Subtyping and equivalence rules for callables
  - parameter types
  - return types
  - positional-only
  - positional + keyword
  - keyword-only
  - with ParamSpec
  - *args with tuple
  - *args with TypeVarTuple
  - *kwargs with dict
  - *kwargs with unpacked TypedDict
  - Argument defaults
  - Overloads

Methods
* Instance, class, and static methods
* Using the staticmethod and classmethod calls outside of decorators
https://github.com/python/mypy/issues/15015
* self and cls parameters
* Binding a class or type to a method

Class and Instance Variables
* Including metaclass instance variables

Constructors
* Including: https://github.com/python/typing/issues/1563#issuecomment-1918734439
** Submitted: https://github.com/python/typing/pull/1667 **

Decorators
* Function decorators
* Class decorators

Descriptors
* Descriptors
* Properties
* Asymmetric descriptors

Exceptions
* Try/Except/Final statements
* Context Managers ``__exit__`` return type

Enum
* Enum and type checking
** Submitted: https://github.com/python/typing/pull/1591 **

Type Narrowing
* Narrowing on assignment
* Narrowing rules for Any
* Built-in type guards

Abstract classes

Overloads
* Overloads with decorators (staticmethod, classmethod, etc.) - consistency required
* Overload resolution for calls
* Overload subtyping rules
* Overload implementation consistency
* Overlapping overload detection

Class & function decorators







# PARTIALLY-WRITTEN SECTIONS OF CHAPTERS

Class Decorators
----------------

Type checkers should honor a class decorator if it is typed. If an untyped
class decorator is applied to a class, a type checker may assume that it has
no effect from a typing perspective.

Typically, a class decorator function will accept (and return) a value of
type ``type`` or of type ``Callable``. The former is preferable because it
preserves type compatibility with ``type``.

  ::

    def make_int(cls: type) -> type[int]:
        return int

    @make_int
    class A:
        ...

    reveal_type(A(1))  # ``int``


    def make_callable(cls: Callable[[], Any]) -> Callable[[], int]:
        return int

    @make_callable
    class B: ...

    reveal_type(B())  # ``int``

