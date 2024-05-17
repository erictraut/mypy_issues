# MISSING CONFORMANCE TESTS

Distributing type information
 - Stub files (https://github.com/python/typing/issues/1605)


# MISSING CHAPTERS IN TYPING SPEC

Enum
* Enum and type checking
** Submitted: https://github.com/python/typing/pull/1591 **

Classes
* MRO
* LSP (with exemptions)
* Allowed and disallowed overrides
  - types (invariance, read-only, properties vs. attributes, etc.)
  - type qualifiers (class variables, final variables, etc.)
* Overrides within a class hierarchy
* Overrides within multiple inheritance
* super()
* Inheriting from Any
* Metaclasses
* `__init_subclass__`

Methods
* Instance, class, and static methods
* Using the staticmethod and classmethod calls outside of decorators
* `self` and `cls` parameters
  - inferred types (including metaclasses)
  - Positional-only parameters (https://github.com/python/mypy/issues/15015)
* Binding a class or object to a method
* Unimplemented methods (in protocols and ABCs)
* Asymmetric descriptors

Overloads
* Overloads with decorators (staticmethod, classmethod, etc.) - consistency required
* Overload resolution for calls
* Overload implementation consistency
* Overlapping overload detection (partial and full)
* Overloads and ParamSpec

Types for Libraries
* Contents of https://github.com/python/typing/blob/main/docs/source/libraries.rst



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



Self and cls parameters
^^^^^^^^^^^^^^^^^^^^^^^

Instance methods and class methods have a first parameter that is, by convention,
named ``self`` and ``cls``, respectively. Type checkers should always treat
these parameters as implicitly positional-only even if they are not explicitly
designated as such. This distinction affects type compatibility checks and
validation of function calls. For example::

    class A:
        def instance_method(self) -> None: ...

    A.instance_method(A())  # OK
    A.instance_method(self=A())  # Error: self is positional-only


