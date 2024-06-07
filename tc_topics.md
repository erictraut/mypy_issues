This document contains my informal notes about topics that I think are missing
or incomplete in the Python typing spec and related conformance tests. In many
cases, these ideas are not fully fleshed out, and they require more work.


# Missing Chapters in Typing Spec

When Jelle initially suggested a formal typing spec, I posted a [proposed list
of chapters](https://discuss.python.org/t/proposed-initial-typing-spec/39389/6).
Many of these chapters were completely missing from the spec initially, but
we've made good headway toward filling them in. Here are the chapters that
are still missing from the spec.

Core Typing Concepts & Terminology
* Gradual typing
* Consistent subtyping
* etc.
** Work in progress by carljm: https://github.com/python/typing/pull/1743 **

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

Methods & Attributes
* Instance, class, and static methods
* Using the staticmethod and classmethod calls outside of decorators
* `self` and `cls` parameters
  - inferred types (including metaclasses)
  - Positional-only parameters (https://github.com/python/mypy/issues/15015)
* Binding a class or object to a method or attribute
* Unimplemented methods (in protocols and ABCs)
* Properties & descriptors
* Asymmetric descriptors
* Instance and class variables

Overloads
* Overloads with decorators (staticmethod, classmethod, etc.) - consistency required
* Overload resolution for calls
* Overload implementation consistency
* Overlapping overload detection (partial and full)
* Overloads and ParamSpec

Distributing Type Information
(Chapter exists, but is missing information about Type information in libraries)
* Contents of https://github.com/python/typing/blob/main/docs/source/libraries.rst

Type Narrowing
* Narrowing on assignment
* Narrowing rules for `Any`
* Standard type guards



# Missing Conformance Tests

The conformance tests for the typing spec are pretty complete at this point
with coverage of most of the chapters. There is one chapter that is not yet
covered, mainly because the current test framework isn't especially well suited
for import resolution testing.

Distributing type information
 - Stub Files (https://typing.readthedocs.io/en/latest/spec/distributing.html)



# Other Unresolved Questions in Spec

This section includes a free-form (unsorted) list of questions that the typing
spec should arguably cover at some point. Some of these will be controversial,
and almost all of them will require discussion and input.


### Already Posted

Should "type" statements in class be allowed to reference class-scoped TypeVars?
https://discuss.python.org/t/class-scoped-type-statement-that-references-outer-scoped-typevar/40026

Are self and cls always positional-only?
What if a double-underscore parameter appears after a non-double-underscore parameter?
https://discuss.python.org/t/ambiguities-about-positional-only-parameters/42328
https://github.com/python/typing/pull/1619
https://github.com/python/typing/issues/1355

Should name consistency be enforced for TypeVar-like, TypeAliasType, Enum, NamedTuple, namedtuple, NewType, TypedDict?
https://discuss.python.org/t/draft-of-typing-spec-chapter-for-enums/43496/15

Is a protocol class or an ABC compatible with `type[T]`, `type[Any]` or `type[object]`? 
https://discuss.python.org/t/compatibility-of-protocol-class-object-with-type-t-and-type-any/48442/7


### Not Yet Posted

Variance computation: Which attributes and methods are exempt?

Override computation: Which attributes and methods are exempt?

Protocol matching: Which attributes and methods are exempt?

`__init__` methods in protocols
https://github.com/microsoft/pyright/issues/7249

Argument defaults for parameter annotated with TypeVar
```def func[T](x: T = None)```

TypeVar matching for unions

Overload matching behaviors

Overload overlap detection algorithm; is this required by type checkers?

Overload override algorithm; is this required by type checkers?

What does it mean for the `self` parameter of an `__init__` method to be annotated?
https://github.com/microsoft/pyright/issues/2909

`# type: ignore` comments and type-checker-specific forms

Scoping of annotations: How should identifiers within an annotation be resolved?

Binding and partial specialization
https://github.com/python/mypy/issues/16554
Also see comments in annotations_methods.py in conformance test suite

Type of self and cls parameters? What about within a metaclass?

Should (*Any, **Any) imply ...?
https://github.com/python/mypy/issues/5876

Should explicit specialization for a constrained TypeVar allow for subclasses?
```python
T = TypeVar("T", float, str)
class Foo(Generic[T]): ...
x: Foo[float] # Is this allowed? What is its type?
```

Should `Any` be allowed as a bound for a TypeVar?

Should `Any` be allowed as a constraint in a constrained TypeVar?

If a constraint within a constrained TypeVar is a subtype of another constraint, should that be allowed?

Should `Never` be a valid type argument for a constrained TypeVar if Never isn't a constraint?

When explicitly providing a type argument for a constrained TypeVar, is it OK to use a subtype of one of the constraints, or does it need to match exactly?

When specifying a constrained TypeVar, is it OK for one constraint to be a subtype of another (like int and float)? What does that mean?

Are unions always order-independent? Under what circumstances does ordering matter? What order should be used?

How should unpacked arguments be treated?
def func1(a: int, b: int, c: str): ...
def func2(*args: int):
    func1(*args, "")

Should overloads require consistent @staticmethod and @classmethod decorators?

Dataclass transform: default argument values for custom field classes
https://github.com/microsoft/pyright/issues/6573

Where are type aliases allowed?
Global and class scopes but not function scopes

Scoping rules for TypeVars in Callable return types?

TypeVarTuples that capture callables with indeterminate param count
https://github.com/microsoft/pyright/issues/6613

Can `Final` be used to define a variable in a protocol?
https://discuss.python.org/t/pep-705-read-only-typeddict-items/37867/7?u=erictraut

Can `Final` be used for a module-level constant to satisfy a protocol?

Can TypedDict and Protocol be used as an upper bound (or anywhere in a type annotation)?
https://github.com/python/mypy/issues/11030

What are the type evaluation rules for `super`?
https://github.com/microsoft/pyright/issues/6660

What does it mean for a method in a non-Protocol, non-ABC class to be marked `abstractmethod`?

Should a class that does not derive from ABC allow methods that are abstract? Should that class then be treated as abstract?

How should `Any | T` be treated? Should it be reduced to `Any`? Treated as irreducible?

Are byte or raw strings allowed for type annotations? How about f-strings?

Is `type[Self]` allowed in a metaclass?

What expression forms are allowed ane disallowed in type annotations? What about string concatenation?

What type should the synthesized `get` method return for a TypedDict?

More generally, how should all of the synthesized methods work in TypedDict?

Bugs in TypedDict for **kwargs PEP:
https://typing.readthedocs.io/en/latest/spec/callables.html#source-and-destination-contain-kwargs
accept_dog sample is incorrect: both examples should be type errors

https://typing.readthedocs.io/en/latest/spec/callables.html#passing-kwargs-inside-a-function-to-another-function
This entire section is incorrect from a type standpoint

Should NewType work with Any?

Should ClassVar with no type arguments have implied type of Any or infer type from assignment (like Final)?

Should Self be allowed in a ClassVar type declaration?

Should `sys.version < (3, 10, 2)` form (with three numbers in version tuple) be understood? Should `os.name === 'xxx'` be understood?

Spec says that NoReturn cannot appear anywhere other than return annotation; should be amended
https://typing.readthedocs.io/en/latest/spec/special-types.html#noreturn

If a class that explicitly derives from a protocol doesn't implement attributes required by the protocol, should a type checker immediately report the error, or should it defer until the class is instantiated? Mypy defers, but the other three type checkers immediately report. The spec is noncommittal.

Should TypeVarTuple enforce that all instances of Ts be the same?
See https://github.com/microsoft/pyright/issues/6888

Does Concatenate support `...`?

Does parameter type inference violate the spec?

Should we document type promotions for bytes, bytearray, and memoryview?

For a protocol that is implemented in a stub file, how is a default method implementation distinguished from a non-implemented one? What about implemented versus not-implemented variables?
https://github.com/microsoft/pyright/issues/6624

What constitutes a "trivial implementation" for purposes of determining whether a protocol method or abstract method is implemented?
See https://discuss.python.org/t/calling-abstract-methods/42576/3

Should a type checker enforce the return type for a function that is implemented with a `pass` statement? Or a `...` statement?

What type forms are compatible with `type[object]`? What are the principles that should be used?

Should type(X) be allowed if X is a protocol?
https://github.com/python/mypy/issues/16919

How does ParamSpec work with overloaded methods? How does this work with classes that are parameterized by ParamSpecs?

Should a non-instantiable protocol be compatible with `type[T]`?
https://github.com/microsoft/pyright/issues/7475
https://discuss.python.org/t/compatibility-of-protocol-class-object-with-type-t-and-type-any/48442

Should it be an error if a dataclass overrides a field in its parent and does not provide a default value, where its parent does?
https://github.com/microsoft/pyright/issues/7702

`type[A] | type[B]` should be equivalent to `type[A | B]`; This isn't generally true for covariant types
