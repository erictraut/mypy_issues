# Partially-written Specs

Here are some partially-written sections of chapters that I had included
in early drafts of submitted chapters. These were removed because I didn't
think they fit into those chapters or were too controversial to include at
the time.


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



