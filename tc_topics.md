# What are the subtyping rules for `tuple[T, ...]`?
Is it a gradual type, or is it shorthand for a union?
https://discuss.python.org/t/what-are-the-subtyping-rules-for-tuple-t/39837

# Should "type" statements in class be allowed to reference class-scoped TypeVars?
https://discuss.python.org/t/class-scoped-type-statement-that-references-outer-scoped-typevar/40026

# Meaning of `type`, `Type`, `type[Any]` and `Type[Any]`
https://discuss.python.org/t/inconsistencies-between-type-and-type/37404/12

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

# What does it mean for the `self` parameter of an `__init__` method to be annotated?
https://github.com/microsoft/pyright/issues/2909

# `# type: ignore` comments and type-checker-specific forms

# Scoping of annotations
How should identifiers within an annotation be resolved?

# Binding and partial specialization
https://github.com/python/mypy/issues/16554

# Type of self and cls parameters

# Are self and cls always positional-only?

# Should (*Any, **Any) imply ...?
https://github.com/python/mypy/issues/5876

# Should explicit specialization for a constrained TypeVar allow for subclasses?
T = TypeVar("T", float, str)
class Foo(Generic[T]): ...
x: Foo[float] # Is this allowed? What is its type?

# Should "Any" be allowed as a bound for a TypeVar?

# Should "Any" be allowed as a constraint in a constrained TypeVar?

# If a constraint within a constrained TypeVar is a subtype of another constraint, should that be allowed?

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

# How should `Any | T` be treated? Should it be reduced to `Any`? Treated as irreducible?

