## Features and bugs that I recommend closing

- https://github.com/python/mypy/issues/363
I recommend fixing this in typeshed by changing NotImplemented so it's declared as type NotImplementedError rather than Any

- https://github.com/python/mypy/issues/1021
I don't think this should be allowed; instance variables should be assigned in `__init__`, not in `__new__`

- https://github.com/python/mypy/issues/1052
This is an inappropriate abuse of NoReturn

- https://github.com/python/mypy/issues/2220
Not a type checker error; straightforward workaround

- https://github.com/python/mypy/issues/1314
I don't see a good way to fix this without leading to false positives; plus, it's not a big problem

- https://github.com/python/mypy/issues/1831
Type[C] doesn't imply callable

- https://github.com/python/mypy/issues/2563
`classproperty` is deprecated

- https://github.com/python/mypy/issues/2922
ABCMeta.register is too dynamic

- https://github.com/python/mypy/issues/2980
Odd idiom with obvious workaround

- https://github.com/python/mypy/issues/3060
Type is deprecated, obvious workaround

- https://github.com/python/mypy/issues/3178
This isn't how TypeVar constraints are supposed to work

- https://github.com/python/mypy/issues/3194
Issue too general

- https://github.com/python/mypy/issues/4019
Not feasible in general

- https://github.com/python/mypy/issues/4168
Requires global analysis, not practical

- https://github.com/python/mypy/issues/4266
Not worth special-case logic, use # type: ignore

- https://github.com/python/mypy/issues/4690
Poorly-motivated suggestion

- https://github.com/python/mypy/issues/4819
Working correctly (not a bug)

- https://github.com/python/mypy/issues/5028
This isn't how stubs are designed to work, not feasible

- https://github.com/python/mypy/issues/5382
Working correctly (not a bug)

- https://github.com/python/mypy/issues/5406
Aliases of attrs too dynamic; use PEP 681

- https://github.com/python/mypy/issues/5481
Working correctly (not a bug); use property instead

- https://github.com/python/mypy/issues/5774
I don't think this should be allowed; instance variables should be assigned in `__init__`, not in `__new__`

- https://github.com/python/mypy/issues/5803
Properties are not the same as descriptors or attributes, so this shouldn't be allowed

- https://github.com/python/mypy/issues/5843
Working correctly; insufficient context to infer type of lambda

- https://github.com/python/mypy/issues/6157
Working correctly; bug is in sample code

- https://github.com/python/mypy/issues/6178
Working correctly; class methods should enforce covariance

- https://github.com/python/mypy/issues/6577
Working correctly (not a bug)

- https://github.com/python/mypy/issues/6656
Bug report represents misunderstanding of type narrowing

- https://github.com/python/mypy/issues/6746
Feature request represents misunderstanding of type system

- https://github.com/python/mypy/issues/6933
Working correctly (not a bug)

- https://github.com/python/mypy/issues/7012
`__name__` is writable, so it isn't safe to infer literal type

- https://github.com/python/mypy/issues/7109
Working correctly (not a bug)

- https://github.com/python/mypy/issues/7187
Should not be supported by rules of unions

- https://github.com/python/mypy/issues/7264
Already covered by --strict-equality

- https://github.com/python/mypy/issues/7338
Working correctly (not a bug)

- https://github.com/python/mypy/issues/7339
Type narrowing isn't safe in this case; use one of several workarounds

- https://github.com/python/mypy/issues/7374
Invalid proposal; represent misunderstanding of NoReturn

- https://github.com/python/mypy/issues/7422
Conditional types not feasible to track; not supported

- https://github.com/python/mypy/issues/7435
Working correctly per PEP; proposed change is not type safe

- https://github.com/python/mypy/issues/7456
Working correctly based on typeshed definition; not worth special casing

- https://github.com/python/mypy/issues/7666
Working correctly; if stub is incorrect, then fix the stub

- https://github.com/python/mypy/issues/7752
Too much of an edge case and too complex

- https://github.com/python/mypy/issues/7853
Too much of an edge case and too complex, TypeGuard is solution

- https://github.com/python/mypy/issues/7858
Working correctly (not a bug)

- https://github.com/python/mypy/issues/7905
Too much of an edge case and too complex, easy to work around

- https://github.com/python/mypy/issues/7928
Conditional type narrowing is too complex, easy to work around

- https://github.com/python/mypy/issues/7966
Very specialized feature; recommend using plugin mechanism

- https://github.com/python/mypy/issues/7981
@final has no meaning for structural types

- https://github.com/python/mypy/issues/8001
Working correctly (not a bug)

- https://github.com/python/mypy/issues/8083
`@property` requires lots of special-casing

- https://github.com/python/mypy/issues/8166
platform.system() isn't recognized by PEP 484; use sys.platform

- https://github.com/python/mypy/issues/8213
Working correctly (not a bug)

- https://github.com/python/mypy/issues/8355
Working correctly; represents misunderstanding of how unions are type checked

- https://github.com/python/mypy/issues/8358
Working correctly (not a bug); works at runtime, more of a linting feature

- https://github.com/python/mypy/issues/8414
Generic types used in annotations must derive from Generic

- https://github.com/python/mypy/issues/8435
Cannot generally narrow type based on check of a single attribute

- https://github.com/python/mypy/issues/8439
Aliases and partials of @dataclass won't work for static type checking

- https://github.com/python/mypy/issues/8482
Working correctly; variable not allowed in type annotation

- https://github.com/python/mypy/issues/8484
Feature would require massive special-casing, not generally possible

- https://github.com/python/mypy/issues/8526
Working correctly (not a bug)

- https://github.com/python/mypy/issues/8604
Not generally possible to implement, recommend workaround

- https://github.com/python/mypy/issues/8622
Edge case, not worth added complexity; recommend TypeGuard

- https://github.com/python/mypy/issues/8705
Not possible in type system today; workaround provided

- https://github.com/python/mypy/issues/8764
Conditional types not feasible to track; not supported

- https://github.com/python/mypy/issues/8766
Working correctly (not a bug)

- https://github.com/python/mypy/issues/8819
Too dynamic; would require new typing features or global analysis

- https://github.com/python/mypy/issues/8842
Working correctly (not a bug); represents misunderstanding of scopes in Python

- https://github.com/python/mypy/issues/8867
Working correctly (not a bug); Not how overloads work

- https://github.com/python/mypy/issues/8874
Error message seems fine to me

- https://github.com/python/mypy/issues/8890
Working correctly (not a bug); recommend use TypeGuard

- https://github.com/python/mypy/issues/9005
Working correctly (not a bug); cross-function mutations not supported

- https://github.com/python/mypy/issues/9015
Working correctly (not a bug)

- https://github.com/python/mypy/issues/9128
Working correctly (not a bug)

- https://github.com/python/mypy/issues/9194
Working correctly (not a bug)

- https://github.com/python/mypy/issues/9201
Working correctly (not a bug)

- https://github.com/python/mypy/issues/9373
Working correctly; type violation occurs at the use site, so it should be reported there

- https://github.com/python/mypy/issues/9356
Poorly-motivated feature request; Too dynamic to handle in static type checker

- https://github.com/python/mypy/issues/9388
Working correctly; list is invariant

- https://github.com/python/mypy/issues/9464
Too complex to implement in constraint solver

- https://github.com/python/mypy/issues/9484
Straightforward workaround is to break up string; no longer a problem in Python 3.12

- https://github.com/python/mypy/issues/9676
Appears to be fixed; Could not repro

- https://github.com/python/mypy/issues/9710
Code is missing appropriate type annotation

- https://github.com/python/mypy/issues/9712
Classes that are intended to be generic should derive from `Generic`, not define their own `__class_getitem__`

- https://github.com/python/mypy/issues/9779
Type violation is being reported correctly; workaround is to avoid name conflict

- https://github.com/python/mypy/issues/9815
Error is correct; this is why generics are not allowed in ClassVar

- https://github.com/python/mypy/issues/9823
Monkey patching is too dynamic for (and antithetical to) static type checking

- https://github.com/python/mypy/issues/9850
Working correctly (not a bug); cross-function mutations not supported

- https://github.com/python/mypy/issues/9871
Redefining at arbitrary locations won't work because applicable declaration will be ambiguous

- https://github.com/python/mypy/issues/9890
Too complex for automatic type narrowing; use TypeGuard

- https://github.com/python/mypy/issues/9911
Requires plugin; nothing actionable for mypy

- https://github.com/python/mypy/issues/9937
This is an issue with typeshed's definition of `overload`, not mypy

- https://github.com/python/mypy/issues/9938
Mypy is working correctly given the type definitions

- https://github.com/python/mypy/issues/9987
Working correctly (not a bug)

- https://github.com/python/mypy/issues/10005
Working correctly; represents misunderstanding of how type declarations work

- https://github.com/python/mypy/issues/10079
Goes against the principles for mypy (don't infer parameter types)

- https://github.com/python/mypy/issues/10164
Would involve a complete rewrite of the constraint solver, not going to happen

- https://github.com/python/mypy/issues/10198
Working correctly (not a bug); the behavior is agreed upon in python/typing

- https://github.com/python/mypy/issues/10224
Conditional types not feasible to track; not supported

- https://github.com/python/mypy/issues/10225
Conditional types not feasible to track; not supported

- https://github.com/python/mypy/issues/10246
Not worth special casing for this edge case

- https://github.com/python/mypy/issues/10371
Bidirectional type inference can't work across iteration

- https://github.com/python/mypy/issues/10380
Conditional types not feasible to track; not supported

- https://github.com/python/mypy/issues/10439
Type guard pattern too complex; recommend TypeGuard

- https://github.com/python/mypy/issues/10465
Runtime state can't be tracked statically, so this check isn't feasible for a static type checker

- https://github.com/python/mypy/issues/10484
Working correctly (not a bug); default arg values are not part of signature

- https://github.com/python/mypy/issues/10516
Appears to have been fixed, no repro with 1.5

- https://github.com/python/mypy/issues/10530
Stubs issue; mypy is working correctly here

- https://github.com/python/mypy/issues/10559
Conditional types not feasible to track; not supported

- https://github.com/python/mypy/issues/10574
Use one of the supported techniques mentioned in the bug report

- https://github.com/python/mypy/issues/10673
Not how TYPE_CHECKING is designed to work

- https://github.com/python/mypy/issues/10691
Working correctly, not a bug (as explained)

- https://github.com/python/mypy/issues/10765
`allow-redefinition` is working as intended

- https://github.com/python/mypy/issues/10806
Working correctly (not a bug); cross-function mutations not supported

- https://github.com/python/mypy/issues/10823
Working correctly (not a bug)

- https://github.com/python/mypy/issues/10878
This isn't how overloads work

- https://github.com/python/mypy/issues/10970
Mypy is working correctly (not a bug)

- https://github.com/python/mypy/issues/10978
Too complex to support type narrowing

- https://github.com/python/mypy/issues/11004
Working correctly; simple workaround provided

- https://github.com/python/mypy/issues/11008
`@property` requires lots of special-casing

- https://github.com/python/mypy/issues/11009
Appears to have been fixed

- https://github.com/python/mypy/issues/11023
Runtime state can't be tracked statically, so this check isn't feasible for a static type checker

- https://github.com/python/mypy/issues/11051
Working correctly (not a bug); cross-function mutations not supported

- https://github.com/python/mypy/issues/11056
Dynamic use of `dataclass` (outside of decorator) cannot be supported statically

- https://github.com/python/mypy/issues/11065
Working correctly

- https://github.com/python/mypy/issues/11097
Working correctly (for reasons explained in bug)

- https://github.com/python/mypy/issues/11116
Probably never going to happen

- https://github.com/python/mypy/issues/11129
This would promote further use of TYPE_CHECKING in cases where it would be inadvisable to do so

- https://github.com/python/mypy/issues/11291
Poorly-motivated feature request

- https://github.com/python/mypy/issues/11301
Working correctly (not a bug); represents misunderstanding of constrained TypeVars

- https://github.com/python/mypy/issues/11302
`new_class` is too dynamic to support statically

- https://github.com/python/mypy/issues/11404
Conditional types not feasible to track; not supported

- https://github.com/python/mypy/issues/11427
Working correctly (not a bug in mypy)

- https://github.com/python/mypy/issues/11477
Working correctly (not a bug)

- https://github.com/python/mypy/issues/11486
Working correctly (not a bug)

- https://github.com/python/mypy/issues/11505
Poorly motivated feature request

- https://github.com/python/mypy/issues/11529
Occurs only on older versions of Python; increasingly irrelevant

- https://github.com/python/mypy/issues/11565
This is not how constrained (restricted) TypeVars work according to the specs

- https://github.com/python/mypy/issues/11613
Working correctly (nothing actionable)

- https://github.com/python/mypy/issues/11655
Working correctly (not a bug)

- https://github.com/python/mypy/issues/11659
Working correctly (not a bug)

- https://github.com/python/mypy/issues/11661
Working correctly (not a bug)

- https://github.com/python/mypy/issues/11853
Working correctly (not a bug); cross-function mutations not supported

- https://github.com/python/mypy/issues/11854
Not able to repro; looks like it has been fixed

- https://github.com/python/mypy/issues/11956
Working correctly (not a bug)

- https://github.com/python/mypy/issues/11959
Working correctly; there's no potential typing hole if expression is unused

- https://github.com/python/mypy/issues/11969
Working correctly (not a bug); cross-function mutations not supported

- https://github.com/python/mypy/issues/11970
Working correctly (not a bug)

- https://github.com/python/mypy/issues/12016
Feature request not well motivated

- https://github.com/python/mypy/issues/12046
Working correctly; incompatible type declarations are a type violation

- https://github.com/python/mypy/issues/12082
There is no such option as "redundant-expression"

- https://github.com/python/mypy/issues/12102
This isn't how import resolutions work in type checkers

- https://github.com/python/mypy/issues/12146
Working correctly; wouldn't make sense to narrow to a TypeVar because there is no way to solve that TypeVar; it would lead to a cascade of false positive errors

- https://github.com/python/mypy/issues/12156
Working correctly (not a bug)

- https://github.com/python/mypy/issues/12206
Suggested fix would be inconsistent and would almost never apply, so not worth it

- https://github.com/python/mypy/issues/12247
Working correctly (not a bug)

- https://github.com/python/mypy/issues/12285
Poorly-motivated feature request; not worth special-casing

- https://github.com/python/mypy/issues/12328
Working correctly; if anything, this is just poorly-worded documentation

- https://github.com/python/mypy/issues/12361
Working correctly (not a bug)

- https://github.com/python/mypy/issues/12369
Poorly-motivated feature request

- https://github.com/python/mypy/issues/12401
Working correctly (not a bug); making the suggested change would be incredibly disruptive with little or no benefit

- https://github.com/python/mypy/issues/12402
Poorly-motivated feature request

- https://github.com/python/mypy/issues/12409
Working as designed; Poorly-motivated change request

- https://github.com/python/mypy/issues/12413
Working as designed; dynamic (variable) subscripts too complex to track

- https://github.com/python/mypy/issues/12457
This isn't a reasonable type narrowing pattern, too complex

- https://github.com/python/mypy/issues/12466
Current output looks fine to me; request is poorly motivated

- https://github.com/python/mypy/issues/12570
Poorly-motivated feature request; fragile code that doesn't work with deferred annotation evaluation

- https://github.com/python/mypy/issues/12573
Working correctly (not a bug)

- https://github.com/python/mypy/issues/12599
This is legal code, shouldn't be flagged as error

- https://github.com/python/mypy/issues/12672
Poorly-motivated feature request; obvious workaround

- https://github.com/python/mypy/issues/12682
Working correctly (not a bug)

- https://github.com/python/mypy/issues/12754
Working correctly (not a bug)

- https://github.com/python/mypy/issues/12779
Not able to repro; appears to have been fixed

- https://github.com/python/mypy/issues/12785
Working correctly (not a bug); `# type: ignore` simply suppressed the errors on that line; it doesn't affect any other behaviors

- https://github.com/python/mypy/issues/12796
Poorly-motivated suggestion; current badge looks fine

- https://github.com/python/mypy/issues/12799
Working correctly (not a bug)

- https://github.com/python/mypy/issues/12829
Working correctly (not a bug)

- https://github.com/python/mypy/issues/12842
Working correctly (not a bug); bug represents misunderstanding of variance

- https://github.com/python/mypy/issues/12971
Can't handle due to circularity

- https://github.com/python/mypy/issues/12944
Working correctly (not a bug)

- https://github.com/python/mypy/issues/13051
Type checkers don't generally verify that `super.__init__` is called, so this shouldn't apply to `dataclass` either

- https://github.com/python/mypy/issues/13071
Working correctly (not a bug); class lacks a `__getattr__`

- https://github.com/python/mypy/issues/13120
Working correctly (not a bug in mypy); `field` is designed to use within dataclass, not outside

- https://github.com/python/mypy/issues/13127
Asymmetric properties are legit, so this isn't an error

- https://github.com/python/mypy/issues/13134
Not practical to implement; unlikely to ever happen

- https://github.com/python/mypy/issues/13180
This is how dataclass are intended to work in static type checking; not a bug

- https://github.com/python/mypy/issues/13185
Variance checks for type variables in nominal classes would be too noisy; problem will go away with PEP 695

- https://github.com/python/mypy/issues/13194
These are not equivalent; mypy is correct in flagging these as errors

- https://github.com/python/mypy/issues/13224
Working correctly (not a bug); second example doesn't involve a delete

- https://github.com/python/mypy/issues/13240
Working correctly (not a bug); cross-function mutations not supported

- https://github.com/python/mypy/issues/13309
Typeshed bug; mypy is doing the right thing here

- https://github.com/python/mypy/issues/13363
Poorly-motivated feature request

- https://github.com/python/mypy/issues/13365
Poorly-motivated feature request; requires special-casing

- https://github.com/python/mypy/issues/13426
Working correctly (no bug)

- https://github.com/python/mypy/issues/13434
`@staticmethod` must be used as decorator; type system is not expressive enough to handle otherwise

- https://github.com/python/mypy/issues/13548
This would be incredibly complicated to support for non-static conditionals; unlikely to ever be implemented

- https://github.com/python/mypy/issues/13719
Not feasible to implement in static type checker

- https://github.com/python/mypy/issues/13766
There is no "redundant-expr" feature

- https://github.com/python/mypy/issues/13816
Conditional types not feasible to track; not supported

- https://github.com/python/mypy/issues/13894
Invalid use of `__getitem__` in attempt to implement generic semantics

- https://github.com/python/mypy/issues/13918
Working correctly (not a bug)

- https://github.com/python/mypy/issues/13921
Working correctly (not a bug)

- https://github.com/python/mypy/issues/13946
Working as designed; suggested change is not pragmatic and would result in massive churn with very little benefit

- https://github.com/python/mypy/issues/13958
Working correctly; error message looks fine to me

- https://github.com/python/mypy/issues/13960
Working correctly (not a bug)

- https://github.com/python/mypy/issues/13990
Poorly-motivated feature request with no support in past year

- https://github.com/python/mypy/issues/13992
Working as designed (not a bug)

- https://github.com/python/mypy/issues/14052
Dynamic manipulation of namespaces not supportable in static type checker

- https://github.com/python/mypy/issues/14106
Working as designed

- https://github.com/python/mypy/issues/14145
Problem with numpy type annotations, not a mypy bug

- https://github.com/python/mypy/issues/14160
Conditional types not feasible to track; not supported

- https://github.com/python/mypy/issues/14220
Suggested workarounds are preferable

- https://github.com/python/mypy/issues/14227
Working correctly (not a bug in mypy)

- https://github.com/python/mypy/issues/14256
More of a linting error and very obscure

- https://github.com/python/mypy/issues/14261
Working correctly; represents misunderstanding of type narrowing

- https://github.com/python/mypy/issues/14266
Requires global analysis, not practical

- https://github.com/python/mypy/issues/14289
Poorly-motivated feature request, very odd coding pattern, not worth special-casing

- https://github.com/python/mypy/issues/14305
Requires global analysis, not practical

- https://github.com/python/mypy/issues/14314
`@property` requires significant special-casing because it's not generic; third-party property-like classes won't work

- https://github.com/python/mypy/issues/14315
Code sample misuses type alias

- https://github.com/python/mypy/issues/14346
Poorly-motivated feature request; type annotations should be explicit

- https://github.com/python/mypy/issues/14365
Working correctly (not a bug)

- https://github.com/python/mypy/issues/14392
Working correctly (not a bug)

- https://github.com/python/mypy/issues/14467
Working correctly (not a bug); may be worth turning into a feature request, but it's unlikely to ever be implemented

- https://github.com/python/mypy/issues/14421
This isn't how unions are evaluated; working as designed

- https://github.com/python/mypy/issues/14425
Working correctly (not a bug); represents misunderstanding of how TypeGuard works

- https://github.com/python/mypy/issues/14539
Working correctly; represents misunderstanding of difference between type expressions and value expressions; later part of bug represents misunderstanding of TYPE_CHECKING

- https://github.com/python/mypy/issues/14559
Working as designed; poorly-motivated feature request

- https://github.com/python/mypy/issues/14666
Feature request represents misunderstanding of overloads

- https://github.com/python/mypy/issues/14741
Working correctly (not a bug in mypy); not worth special casing

- https://github.com/python/mypy/issues/14742
Working correctly (not a bug)

- https://github.com/python/mypy/issues/14764
Poorly-motivated feature request; would harm analyzer performance for extreme edge case when there is an obvious and straightforward workaround

- https://github.com/python/mypy/issues/14766
This isn't a reasonable type narrowing pattern, too complex; use walrus operator instead

- https://github.com/python/mypy/issues/14776
Working correctly (not a bug)

- https://github.com/python/mypy/issues/14777
Represents misunderstanding of PEP 612

- https://github.com/python/mypy/issues/14813
Working correctly (not a bug)

- https://github.com/python/mypy/issues/14863
Working correctly (not a bug)

- https://github.com/python/mypy/issues/14895
Working correctly (not a bug); meaningful errors for overloads are difficult

- https://github.com/python/mypy/issues/14911
Working correctly (not a bug); feature request isn't feasible

- https://github.com/python/mypy/issues/14931
Fixed in latest version

- https://github.com/python/mypy/issues/14967
Unclear bug report; waiting for more info, but none provided

- https://github.com/python/mypy/issues/15026
Working correctly (not a bug); base is not staticmethod

- https://github.com/python/mypy/issues/15175
Poorly-motivated feature; unlikely to ever be implemented

- https://github.com/python/mypy/issues/15509
Requires global analysis, not practical

- https://github.com/python/mypy/issues/15692
Working correctly

- https://github.com/python/mypy/issues/15755
Working correctly (not a bug)

- https://github.com/python/mypy/issues/15835
Working correctly (not a bug)

- https://github.com/python/mypy/issues/15872
This isn't how union type checking works

- https://github.com/python/mypy/issues/15848
Working correctly (not a bug); sample code is buggy

- https://github.com/python/mypy/issues/15977
Working correctly (not a bug)

- https://github.com/python/mypy/issues/15997
Working correctly (not a bug)

- https://github.com/python/mypy/issues/15998
Working correctly (not a bug)

- https://github.com/python/mypy/issues/15999
Working correctly (not a bug)

- https://github.com/python/mypy/issues/16007
Code is buggy; mypy is working as intended

- https://github.com/python/mypy/issues/15850
Very old unsupported version of mypy

- https://github.com/python/mypy/issues/16031
Far outside the intended use of `dataclass_transform`

- https://github.com/python/mypy/issues/16041
Comparison overlap cannot be precise because of `__eq__` overrides

- https://github.com/python/mypy/issues/16072
Working correctly (not a bug)

- https://github.com/python/mypy/issues/16086
Working correctly (not a bug)

- https://github.com/python/mypy/issues/16089
Working correctly (not a bug)

- https://github.com/python/mypy/issues/16185
Behavior is correct (not a bug)

- https://github.com/python/mypy/issues/16191
Behavior is correct (not a bug); need to refactor code

- https://github.com/python/mypy/issues/16200
Behavior is correct (not a bug)

- https://github.com/python/mypy/issues/16243
Behavior is correct (not a bug)

- https://github.com/python/mypy/issues/16261
Mypy is correct; due to the way `lru_cache` is defined

- https://github.com/python/mypy/issues/16291
Not a bug

- https://github.com/python/mypy/issues/16295
Error message seems fine

- https://github.com/python/mypy/issues/16313
Not a well-motivated feature request

- https://github.com/python/mypy/issues/16333
Not a bug

- https://github.com/python/mypy/issues/16384
Illegal use of type parameters in a variable type declaration

- https://github.com/python/mypy/issues/16437
Bug in stubs

- https://github.com/python/mypy/issues/16476
Not a bug

- https://github.com/python/mypy/issues/16501
Not a bug

- https://github.com/python/mypy/issues/16506
Incorrect use of annotations

- https://github.com/python/mypy/issues/16515
Not a bug

- https://github.com/python/mypy/issues/16549
Not a bug

- https://github.com/python/mypy/issues/16558
Not a bug

- https://github.com/python/mypy/issues/16563
Not a bug

- https://github.com/python/mypy/issues/16565
Not a bug

- https://github.com/python/mypy/issues/16595
Not a bug

- https://github.com/python/mypy/issues/16597
Not well motivated

- https://github.com/python/mypy/issues/16605
Not a bug

- https://github.com/python/mypy/issues/16612
Not a bug

- https://github.com/python/mypy/issues/16618
Not a bug

- https://github.com/python/mypy/issues/16626
Not a bug

- https://github.com/python/mypy/issues/16645
Not a bug

- https://github.com/python/mypy/issues/16647
Not a bug

- https://github.com/python/mypy/issues/16650
Duplicate

- https://github.com/python/mypy/issues/16671
Not enough information

- https://github.com/python/mypy/issues/16677
Duplicate

- https://github.com/python/mypy/issues/16709
User error, not a bug

- https://github.com/python/mypy/issues/16716
User error, not a bug

- https://github.com/python/mypy/issues/16722
Behavior is as designed

- https://github.com/python/mypy/issues/16771
Not a bug

- https://github.com/python/mypy/issues/16773
Not a bug

- https://github.com/python/mypy/issues/16777
Union expansion does not include bool in overloads

- https://github.com/python/mypy/issues/16785
User error, not a bug

- https://github.com/python/mypy/issues/16790
User error, not a bug

- https://github.com/python/mypy/issues/16796
User misunderstanding

- https://github.com/python/mypy/issues/16802
Bug in pandas stubs, not a bug in mypy

- https://github.com/python/mypy/issues/16810
User error, not a bug

- https://github.com/python/mypy/issues/16815
Error message seems fine

- https://github.com/python/mypy/issues/16828
User error, not a bug

- https://github.com/python/mypy/issues/16840
Incorrect use of @overload

- https://github.com/python/mypy/issues/16862
User misunderstanding, not a bug

- https://github.com/python/typeshed/issues/11431
Not a bug, potential issue in typeshed

- https://github.com/python/mypy/issues/16982
User misunderstanding, not a bug

- https://github.com/python/mypy/issues/16985
User unable to provide minimal repro

- https://github.com/python/mypy/issues/16993
Unrealistic expectations

- https://github.com/python/mypy/issues/16999
Behavior is correct, not a bug

- https://github.com/python/mypy/issues/17026
User misunderstanding, not a bug

- https://github.com/python/mypy/issues/17030
Behavior is correct, not a bug

- https://github.com/python/mypy/issues/17034
Not a bug

- https://github.com/python/mypy/issues/17045
Works as designed, not a bug

- https://github.com/python/mypy/issues/17055
Behavior is correct, not a bug

- https://github.com/python/mypy/issues/17061
Typeshed bug, not a mypy issue

- https://github.com/python/mypy/issues/17076
Not a bug

- https://github.com/python/mypy/issues/17082
User error, not a bug

- https://github.com/python/mypy/issues/17087
Not a bug

- https://github.com/python/mypy/issues/17089
Not a bug in mypy; limitation of type system

- https://github.com/python/mypy/issues/17106
Working as designed

- https://github.com/python/mypy/issues/17107
User misunderstanding, not a bug

- https://github.com/python/mypy/issues/17166
Working as intended, not a bug

- https://github.com/python/mypy/issues/17172
Not a bug in mypy, user question

- https://github.com/python/mypy/issues/17177
Appears to be a bug in a plugin

- https://github.com/python/mypy/issues/17187
Not realistic to expect type checker to work this way

- https://github.com/python/mypy/issues/17193
Not a bug

- https://github.com/python/mypy/issues/17194
Not a bug, user misunderstanding

- https://github.com/python/mypy/issues/17209
Not a mypy bug, may be a typeshed issue

- https://github.com/python/mypy/issues/17213
Creates a cyclical dependency between metaclass and class

- https://github.com/python/mypy/issues/17218
Not a bug, a feature request, and probably not a feasible one

- https://github.com/python/mypy/issues/17238
Not a bug

- https://github.com/python/mypy/issues/17242
Not a bug, incorrect use of dataclass

- https://github.com/python/mypy/issues/17296
Not a bug, user misunderstanding

- https://github.com/python/mypy/issues/17299
User misunderstanding

- https://github.com/python/mypy/issues/17316
Not a bug, user misunderstanding

- https://github.com/python/mypy/issues/17322
Not a mypy bug, typeshed issue

- https://github.com/python/mypy/issues/17325
User misunderstanding of how overloads work

- https://github.com/python/mypy/issues/17340
Not a bug, user misunderstanding

- https://github.com/python/mypy/issues/17360
Not a bug, user misunderstanding

- https://github.com/python/mypy/issues/17364
Old version of mypy, no longer repro

- https://github.com/python/mypy/issues/17379
Not a bug, user misunderstanding

- https://github.com/python/mypy/issues/17406
User misunderstanding; property is special-cased

- https://github.com/python/mypy/issues/17426
Mypy is working correctly, feature not well justified

- https://github.com/python/mypy/issues/17438
Limitation of type system, not a mypy bug

- https://github.com/python/mypy/issues/17446
Duplicate

- https://github.com/python/mypy/issues/17483
Mypy is working correctly, user misunderstanding

- https://github.com/python/mypy/issues/17529
User misunderstanding

- https://github.com/python/mypy/issues/17537
User misunderstanding

- https://github.com/python/mypy/issues/17545
User misunderstanding

- https://github.com/python/mypy/issues/17550
User misunderstanding

- https://github.com/python/mypy/issues/17568
Mypy is working as intended here

- https://github.com/python/mypy/issues/17577
Mypy is working correctly here

- https://github.com/python/mypy/issues/17593
User error; invalid type expression

- https://github.com/python/mypy/issues/17613
Mypy is correct; code violates the typing spec

- https://github.com/python/mypy/issues/17622
Atypical use of match statement; switch to typical use

- https://github.com/python/mypy/issues/14833
Not a bug; user misunderstanding

- https://github.com/python/mypy/issues/17666
Not well motivated; more of a linter feature

- https://github.com/python/mypy/issues/17668
Not something that mypy should do; appropriate for a plugin

- https://github.com/python/mypy/issues/17688
Mypy working as designed

- https://github.com/python/mypy/issues/17693
Mypy is working correctly here

- https://github.com/python/mypy/issues/17711
Not specific to dataclasses; mypy is working as designed here

- https://github.com/python/mypy/issues/17715
Insufficient type information to correctly infer type of lambda

- https://github.com/python/mypy/issues/17721
Type narrowing not possible here; user misunderstanding

- https://github.com/python/mypy/issues/17734
Duplicate

- https://github.com/python/mypy/issues/17737
Mypy is working as designed here

- https://github.com/python/mypy/issues/17756
Mypy is working correctly here

- https://github.com/python/mypy/issues/17758
User misunderstanding

- https://github.com/python/mypy/issues/17791
Error message seems fine to me

- https://github.com/python/mypy/issues/17799
Mypy is working correctly here

- https://github.com/python/mypy/issues/17837
Mypy is working correctly here

- https://github.com/python/mypy/issues/17838
Mypy is working correctly here

- https://github.com/python/mypy/issues/17844
User misunderstanding

- https://github.com/python/mypy/issues/17857
User misunderstanding

- https://github.com/python/mypy/issues/17892
Feature is not well motivated, causes too many false positives

- https://github.com/python/mypy/issues/17907
User misunderstanding

- https://github.com/python/mypy/issues/17909
User misunderstanding

- https://github.com/python/mypy/issues/17910
User misunderstanding

- https://github.com/python/mypy/issues/17935
User misunderstanding

- https://github.com/python/mypy/issues/17968
Can't be fixed because typeshed stubs lie about Protocol

- https://github.com/python/mypy/issues/17981
Mypy is working as designed here

- https://github.com/python/mypy/issues/17996
User misunderstanding

- https://github.com/python/mypy/issues/18002
Poorly motivated request

- https://github.com/python/typing/issues/1872
Poorly motivated request; requires typing spec change

- https://github.com/python/mypy/issues/18060
User misunderstanding

- https://github.com/python/mypy/issues/18073
User misunderstanding

- https://github.com/python/mypy/issues/18075
This isn't how overload matching works

- https://github.com/python/mypy/issues/18086
User misunderstanding

- https://github.com/python/mypy/issues/18109
Poorly motivated request

- https://github.com/python/mypy/issues/18189
Properties are not the same as an attribute

- https://github.com/python/mypy/issues/18190
User misunderstanding

- https://github.com/python/mypy/issues/18204
User hasn't provided minimal repro

- https://github.com/python/mypy/issues/18239
User misunderstanding

- https://github.com/python/mypy/issues/18296
User misunderstanding

- https://github.com/python/mypy/issues/18297
Error message is fine

- https://github.com/python/mypy/issues/18394
User misunderstanding

- https://github.com/python/mypy/issues/18400
User misunderstanding

- https://github.com/python/mypy/issues/18425
User misunderstanding

- https://github.com/python/mypy/issues/18431
User misunderstanding

- https://github.com/python/mypy/issues/18435
Poorly motivated feature

- https://github.com/python/mypy/issues/18437
Poorly motivated feature
