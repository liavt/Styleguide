#Naming

{% method -%}

Names shouldn't be too long. If they come out to be huge, use an appropriate acronym, or more preferably, find a way to make it shorter. If you can't make it shorter and keep the original meaning, comment its actual purpose.

{% common %}
BAD:
```java
int thisVariableControlsThePIDControllerInAutonomousModeForShooting
```
GOOD:
```java
//controls the pid for auton to shoot
int autonPIDShooting
```
And less preferable:
```java
int APIDSC
```

{% endmethod %}

{% method -%}

Abbreviations should not be used, except for a few special cases. They are as following:

| *Name*         | *Abbreviation* |
|----------------|----------------|
| Interator      | Iter           |
| Implementation | Impl           |
| Variable       | Var            |
| Function       | Func           |
| Teleoperated   | Teleop         |
| Autonomous     | Auton          |
| Practice       | Prac           |
| Number         | Num            |
| Constant       | Const          |
| Utility        | Util           |
| Argument       | Arg            |
| Parameter      | Param          |

Other approved abbreviations are those that are very commonly used, like DNS for Dynamic Name Service, HTTP for HyperText Transfer Protocol, XML for eXtensible Markup Language, JSON for JavaScript Object Notation, etc.

**EXCEPTION:** if you are writing a `for` loop, `i`, `j`, `x`, `y`, and `z` are acceptable iterator names.

{% endmethod %}
