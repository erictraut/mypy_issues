This document contains my informal notes about topics that I think are missing
or incomplete in the Python typing spec and related conformance tests. In many
cases, these ideas are not fully fleshed out, and they require more work.


# Missing Chapters in Typing Spec

When Jelle initially suggested a formal typing spec, I posted a [proposed list
of chapters](https://discuss.python.org/t/proposed-initial-typing-spec/39389/6).
Many of these chapters were completely missing from the spec initially, but
we've made good headway toward filling them in. Here are the chapters that
are still missing from the spec.

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
* Overloads with decorators (staticmethod, classmethod, async, etc.) - consistency required
* Overload resolution for calls
* Overload implementation consistency
* Overlapping overload detection (partial and full)
* Overloads and ParamSpec

Distributing Type Information
(Chapter exists, but is missing information about Type information in libraries)
* Contents of https://github.com/python/typing/blob/main/docs/source/libraries.rst

Type Narrowing?
* Narrowing on assignment
* Narrowing rules for `Any`
* Standard type guards

Constraint Solving?


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


#### Overloads

Overload matching behaviors

Overload overlap detection algorithm; is this required by type checkers?

Overload override algorithm; is this required by type checkers?

Should overloads require consistent @staticmethod and @classmethod decorators?

How does ParamSpec work with overloaded methods? How does this work with classes that are parameterized by ParamSpecs?


#### Classes

Override computation: Which attributes and methods are exempt?

What are the type evaluation rules for `super`?
https://github.com/microsoft/pyright/issues/6660

Is `type[Self]` allowed in a metaclass?


#### Methods & Attributes

Are self and cls always positional-only?
What if a double-underscore parameter appears after a non-double-underscore parameter?
https://discuss.python.org/t/ambiguities-about-positional-only-parameters/42328
https://github.com/python/typing/pull/1619
https://github.com/python/typing/issues/1355

Type of self and cls parameters? What about within a metaclass?

What does it mean for a method in a non-Protocol, non-ABC class to be marked `abstractmethod`?

Should a class that does not derive from ABC allow methods that are abstract? Should that class then be treated as abstract?

Should ClassVar with no type arguments have implied type of Any or infer type from assignment (like Final)?

Should Self be allowed in a ClassVar type declaration?
See https://github.com/microsoft/pyright/issues/9011

What constitutes a "trivial implementation" for purposes of determining whether a protocol method or abstract method is implemented?
See https://discuss.python.org/t/calling-abstract-methods/42576/3

If @final is used to decorate a method that has a subsequent decorator applied, and that decorator transforms the type (e.g. @functools.cache or @property), is the resulting type final? What about a property setter with a @final def statement?


#### Generics

Constraint solving rules for unions

Variance computation: Which attributes and methods are exempt?

Should explicit specialization for a constrained TypeVar allow for subclasses?
```python
T = TypeVar("T", float, str)
class Foo(Generic[T]): ...
x: Foo[float] # Is this allowed? What is its type?
```

Should `Any` be allowed as a bound for a TypeVar?

Should `Any` be allowed as a constraint in a constrained TypeVar?

If a constraint within a constrained TypeVar is a subtype of another constraint, should that be allowed?

Is `list[T]` assignable to a type of `list[A] | list[B] | list[C]` if `T` is value constrained to ``(A, B, C)`?

For a value constrained TypeVar, is a union of its constraints assignable to it? For example, is `str | bytes` assignable to `AnyStr`?

Should `Never` be a valid type argument for a constrained TypeVar if Never isn't a constraint?

When explicitly providing a type argument for a constrained TypeVar, is it OK to use a subtype of one of the constraints, or does it need to match exactly?

When specifying a constrained TypeVar, is it OK for one constraint to be a subtype of another (like int and float)? What does that mean?

Scoping rules for TypeVars in Callable return types?

TypeVarTuples that capture callables with indeterminate param count
https://github.com/microsoft/pyright/issues/6613

Can TypedDict and Protocol be used as an upper bound (or anywhere in a type annotation)?
https://github.com/python/mypy/issues/11030

How do ParamSpecs work with instance methods and class methods?


#### Protocols

Protocol matching: Which attributes and methods are exempt?

`__init__` methods in protocols
https://github.com/microsoft/pyright/issues/7249

Can `Final` be used to define a variable in a protocol?
https://discuss.python.org/t/pep-705-read-only-typeddict-items/37867/7?u=erictraut

Can `Final` be used for a module-level constant to satisfy a protocol?

If a class that explicitly derives from a protocol doesn't implement attributes required by the protocol, should a type checker immediately report the error, or should it defer until the class is instantiated? Mypy defers, but the other three type checkers immediately report. The spec is noncommittal.

For a protocol that is implemented in a stub file, how is a default method implementation distinguished from a non-implemented one? What about implemented versus not-implemented variables?
https://github.com/microsoft/pyright/issues/6624

Should type(X) be allowed if X is a protocol?
https://github.com/python/mypy/issues/16919

Should a non-instantiable protocol be compatible with `type[T]`?
https://github.com/microsoft/pyright/issues/7475
https://discuss.python.org/t/compatibility-of-protocol-class-object-with-type-t-and-type-any/48442


#### Callables

Argument defaults for parameter annotated with TypeVar
```def func[T](x: T = None)```

How should unpacked arguments be treated?
def func1(a: int, b: int, c: str): ...
def func2(*args: int):
    func1(*args, "")

Does parameter type inference violate the spec? Is it allowed under certain circumstances?

#### Type Checker Directives

`# type: ignore` comments and type-checker-specific forms


#### Type Annotations

Scoping of annotations: How should identifiers within an annotation be resolved?

Are raw strings allowed for type annotations? How about f-strings?

Is string concatenation allowed in a type annotation?


#### Methods & Attributes

Binding and partial specialization
https://github.com/python/mypy/issues/16554
Also see comments in annotations_methods.py in conformance test suite

Should a type checker enforce the return type for a function that is implemented with a `pass` statement? Or a `...` statement?


#### Type System Concepts

Are unions always order-independent? Under what circumstances does ordering matter? What order should be used?


#### Dataclasses

Dataclass transform: default argument values for custom field classes
https://github.com/microsoft/pyright/issues/6573

Should it be an error if a dataclass overrides a field in its parent and does not provide a default value, where its parent does?
https://github.com/microsoft/pyright/issues/7702


#### Type Aliases

Where are type alias definitions allowed?
Proposal: Global and class scopes but not function scopes

Should NewType work with Any?

Should NewType work with structural types (protocols and TypedDicts)?
https://github.com/microsoft/pyright/discussions/8256#discussioncomment-9920744

Should name consistency be enforced for TypeVar-like, TypeAliasType, Enum, NamedTuple, namedtuple, NewType, TypedDict?
https://discuss.python.org/t/draft-of-typing-spec-chapter-for-enums/43496/15

Should "type" statements in class be allowed to reference class-scoped TypeVars?
https://discuss.python.org/t/class-scoped-type-statement-that-references-outer-scoped-typevar/40026


#### TypedDicts

What type should the synthesized `get` method return for a TypedDict?

More generally, how should all of the synthesized methods work in TypedDict?

Bugs in TypedDict for **kwargs PEP:
https://typing.readthedocs.io/en/latest/spec/callables.html#source-and-destination-contain-kwargs
accept_dog sample is incorrect: both examples should be type errors

https://typing.readthedocs.io/en/latest/spec/callables.html#passing-kwargs-inside-a-function-to-another-function
This entire section is incorrect from a type standpoint


#### Type Checker Directives

Should `sys.version < (3, 10, 2)` form (with three numbers in version tuple) be understood? Should `os.name === 'xxx'` be understood?


#### Special Types

`type[A] | type[B]` should be equivalent to `type[A | B]`; This isn't generally true for covariant types

Is a protocol class or an ABC compatible with `type[T]`, `type[Any]` or `type[object]`? 
https://discuss.python.org/t/compatibility-of-protocol-class-object-with-type-t-and-type-any/48442/7

Should `Final` variables be disallowed in a loop?
https://github.com/microsoft/pyright/issues/8560
