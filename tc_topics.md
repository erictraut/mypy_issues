# What are the subtyping rules for `tuple[T, ...]`?
Is it a gradual type, or is it shorthand for a union?
https://discuss.python.org/t/what-are-the-subtyping-rules-for-tuple-t/39837

# Should "type" statements in class be allowed to reference class-scoped TypeVars?
https://discuss.python.org/t/class-scoped-type-statement-that-references-outer-scoped-typevar/40026

# Meaning of `type`, `Type`, `type[Any]` and `Type[Any]`
https://discuss.python.org/t/inconsistencies-between-type-and-type/37404/12

# Are self and cls always positional-only?
# What if a double-underscore parameter appears after a non-double-underscore parameter?
https://discuss.python.org/t/ambiguities-about-positional-only-parameters/42328

# Should type checker report an error if a function-scoped or type-alias-scoped TypeVar is marked as covariant or contravariant?
See https://typing.readthedocs.io/en/latest/spec/generics.html#variance
https://discuss.python.org/t/rejecting-the-use-of-a-covariant-contravariant-typevar-in-a-function-or-type-alias/42769

# In a triple-quoted type expression, should it be treated as implicitly parenthesized?
https://discuss.python.org/t/newlines-within-triple-quoted-type-expressions/42833

# Should we deprecate @no_type_check? What does it mean in the age of language servers?
https://discuss.python.org/t/no-type-check-decorator/43119


^ Already Filed
------------------------------------
v Not Yet Filed

# Variance computation
Which attributes and methods are exempt?

# Override computation
Which attributes and methods are exempt?

# Protocol matching
Which attributes and methods are exempt?

# Argument defaults for parameter annotated with TypeVar
```def func[T](x: T = None)```

# TypeVar matching for unions

# Overload matching behaviors

# Overload overlap detection algorithm; is this required by type checkers?

# Overload override algorithm; is this required by type checkers?

# What does it mean for the `self` parameter of an `__init__` method to be annotated?
https://github.com/microsoft/pyright/issues/2909

# `# type: ignore` comments and type-checker-specific forms

# Scoping of annotations
How should identifiers within an annotation be resolved?

# Binding and partial specialization
https://github.com/python/mypy/issues/16554
Also see comments in annotations_methods.py in conformance test suite

# Type of self and cls parameters? What about within a metaclass?

# Should (*Any, **Any) imply ...?
https://github.com/python/mypy/issues/5876

# Should explicit specialization for a constrained TypeVar allow for subclasses?
T = TypeVar("T", float, str)
class Foo(Generic[T]): ...
x: Foo[float] # Is this allowed? What is its type?

# Should "Any" be allowed as a bound for a TypeVar?

# Should "Any" be allowed as a constraint in a constrained TypeVar?

# If a constraint within a constrained TypeVar is a subtype of another constraint, should that be allowed?

# Should `Never` be a valid type argument for a constrained TypeVar if Never isn't a constraint?

# When explicitly providing a type argument for a constrained TypeVar, is it OK to use a subtype of one of the constraints, or does it need to match exactly?

# Are unions always order-independent? Under what circumstances does ordering matter? What order should be used?

# How should unpacked arguments be treated?
def func1(a: int, b: int, c: str): ...
def func2(*args: int):
    func1(*args, "")

# How should constructor calls be evaluated?

# How should a constructor be converted into a callable?

# Should overloads require consistent @staticmethod and @classmethod decorators?

# Dataclass transform - default argument values for custom field classes
https://github.com/microsoft/pyright/issues/6573

# Where are type aliases allowed?
Global and class scopes but not function scopes

# Scoping rules for TypeVars in Callable return types?

# TypeVarTuples that capture callables with indeterminate param count
https://github.com/microsoft/pyright/issues/6613

# Can `Final` be used to define a variable in a protocol?
https://discuss.python.org/t/pep-705-read-only-typeddict-items/37867/7?u=erictraut

# How should type checkers differentiate between protocol methods and "default implementations" in stubs?
https://github.com/microsoft/pyright/issues/6624

# Can TypedDict and Protocol be used as an upper bound (or anywhere in a type annotation)?
https://github.com/python/mypy/issues/11030

# What are the type evaluation rules for `super`?
https://github.com/microsoft/pyright/issues/6660

# What does it mean for a method in a non-Protocol, non-ABC class to be marked `abstractmethod`?

# Should a class that does not drive from ABC allow methods that are abstract? Should that class then be treated as abstract?

# How should `Any | T` be treated? Should it be reduced to `Any`? Treated as irreducible?

# Are byte or raw strings allowed for type annotations? How about f-strings?

# Is `type[Self]` allowed in a metaclass?

# What expression forms are allowed ane disallowed in type annotations? What about string concatenation?

# What type should the synthesized `get` method return for a TypedDict?

# More generally, how should all of the synthesized methods work in TypedDict?

# Bugs in TypedDict for **kwargs PEP:
https://typing.readthedocs.io/en/latest/spec/callables.html#source-and-destination-contain-kwargs
accept_dog sample is incorrect: both examples should be type errors

https://typing.readthedocs.io/en/latest/spec/callables.html#passing-kwargs-inside-a-function-to-another-function
This entire section is incorrect from a type standpoint

# Should NewType work with Any?

# Should ClassVar with no type arguments have implied type of Any or infer type from assignment (like Final)?

# Should Self be allowed in a ClassVar type declaration?

# Should `sys.version < (3, 10, 2)` form (with three numbers in version tuple) be understood? Should `os.name === 'xxx'` be understood?

# Spec says that NoReturn cannot appear anywhere other than return annotation; should be amended
https://typing.readthedocs.io/en/latest/spec/special-types.html#noreturn

# If a class that explicitly derives from a protocol doesn't implement attributes required by the protocol, should a type checker immediately report the error, or should it defer until the class is instantiated? Mypy defers, but the other three type checkers immediately report. The spec is noncommittal.

# Should TypeVarTuple enforce that all instances of Ts be the same?
See https://github.com/microsoft/pyright/issues/6888

# Does Concatenate support `...`?

# Does parameter type inference violate the spec?

# Should we document type promotions for bytes, bytearray, and memoryview?

# What constitutes a "trivial implementation" for purposes of determining whether a protocol method or abstract method is implemented?
See https://discuss.python.org/t/calling-abstract-methods/42576/3

# For a protocol that is implemented in a stub file, how is a default method implementation distinguished from a non-implemented one? What about implemented versus not-implemented variables?

# Should a type checker enforce the return type for a function that is implemented with a `pass` statement? Or a `...` statement?

# What type forms are compatible with `type[object]`? What are the principles that should be used?

