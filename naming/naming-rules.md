# Naming Rules

Names shouldn't be too long. If they come out to be huge, use an appropriate acronym, or more preferably, find a way to make it shorter. If you can't make it shorter and keep the original meaning, comment its actual purpose.

BAD:

```text
int thisVariableControlsTheThingThatControlsTheFoo
```

GOOD:

```text
int thingFooController
```

And less preferable:

```text
int VCTTTCTF
```

Abbreviations should not be used, except for a few special cases. They are as following:

| _Name_ | _Abbreviation_ |
| :--- | :--- |
| Interator | Iter |
| Implementation | Impl |
| Variable | Var |
| Function | Func |
| Number | Num |
| Constant | Const |
| Utility | Util |
| Argument | Arg |
| Parameter | Param |

Other approved abbreviations are those that are very commonly used, like DNS for Dynamic Name Service, HTTP for HyperText Transfer Protocol, XML for eXtensible Markup Language, JSON for JavaScript Object Notation, etc.

{% hint style="warning" %}
**EXCEPTION:** if you are writing a simple `for` loop, `i`, `j`, `x`, `y`, and `z` are acceptable iterator names. When writing complex algorithms which may involve nested loops, or loops whose iterator isn't so obvious, pertain to using more descriptive iterator names.
{% endhint %}



