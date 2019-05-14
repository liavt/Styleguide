# WPILib

{% method -%}

## Which Robot subclass to use?

Use `IterativeRobot`

*REASONING:*
We have been using that for 2 years and it has proven us well. Don't change it if it ain't broke.

{% endmethod %}

{% method -%}

`Robot` class functions will be in this order:
 * robotInit()
 * robotPeriodic()
 * autonomousInit()
 * autonomousPeriodic()
 * teleopInit()
 * teleopPeriodic()
 * disabledInit()
 * disabledPeriodic()
 
*REASONING:*
This order is based on the when the function is called during an FRC match combined with common usage. `robotInit()` is always called first, then `autonomousInit()`, then `teleopInit()`. `disabled` is at the end because it is rarely used and not as important as the other functions.

{% endmethod -%}

{% method -%}

The `Robot` class should have as minimal code as possible. All implementation should be left to other files.

*REASONING:*
Organizational sake. If you want fix a bug on the shooter for example, you would want to look in `Shooter` instead of parsing `Robot`.

{% endmethod %}

{% method -%}

## Drive Mode

Until a different drive system has been proven effective and drivers have enough time to practice, Tank Drive will be used, with the WPILib `RobotDrive` class.

{% endmethod %}

{% method -%}

## Reversing a motor

If a motor is going backwards and it's supposed to logically go forward, check your wiring. Adding `.setReversed()` to the code causes spaghettification. If you do, create a new constant `boolean` in `Mappings.java` to specify whether the motor is reversed.

Basically, make sure the `.set(1.0)` always makes the motor logically go at max speed forward in both phases of the game. If it doesn't a quick code change doesn't help

{% endmethod %}

{% method -%}

Wrap different components of the robot in classes. Save state in variables that can be reset during robot phases. Create all variables in constructor.

For example, the drive base would have a `DriveBase` class. The `DriveBase` creats all of the motors and joysticks using the constants from the `Mappings` class in it's constructor. The contructor would be called in `robotInit()`.

`DriveBase` has a `setMode()` function which takes in an `enum` with at least the following values:
 * AUTON
 * TELOP

In `autonInit()`, `setMode(Mode.AUTON)` is called on the `DriveBase` variable. This allows the class to perform any auton-specific changes.

Maybe this could be implemented in an `interface` to allow for helper functions from a standard library

*REASONING:*
Java/CPP are both object-oriented languages. The robot's components are all different objects. Thus, it makes sense to represent the robot in terms of objects.
Classes allow for separation of implementation and interface from your high level robot code.
It also provides a level of organization of the file based level.
Additionally, having components in terms of objects allow you to easily reset the robot. If you want to reinitialize a component on the robot, you just reassign the variable to a `new Class()`

{% endmethod %}

{% method -%}

### State Machines

Autonomous is to be written with state machines.

Instead of using `int`s to represent state, which has proven annoying and cause more clutter in the end, use `enum`'s.

This fixes the "magic number" problem.

*REASONING:*
We have been using state machines for the past 2 years. We are quite used to them and they work well.

Using numbers has created really crazy state machines where you go from state 1 to state 53 to state -3 to state 16. Enums allow for self-documenting code that can also be changed in the future.

{% sample lang="java" -%}
EXAMPLE:
BAD:
```java
switch(state) {
  case 0:
    //do code
  case 1://what does 1 mean?
    state = 3;//what is state 3?
    break;
    ...
}
```
GOOD:
```java
enum State {
  DO_NOTHING,
  GOING_FORWARD,
  TURNING,
  AIMING
  ...
}

...

switch(state) {
  case DO_NOTHING:
    //do code
  case GOING_FORWARD:
    state = State.AIMING;
    break;
    ...
}
```

{% sample lang="cpp" -%}
EXAMPLE:
BAD:
```cpp
switch(state) {
  case 0:
    //do code
    [[fallthrough]]//C++17 attribute
  case 1://what does 1 mean?
    state = 3;//what is state 3?
    break;
    ...
}
```
GOOD:
```cpp
enum class State {
  DO_NOTHING,
  GOING_FORWARD,
  TURNING,
  AIMING
  ...
}

...

switch(state) {
  case DO_NOTHING:
    //do code
    [[fallthrough]]
  case GOING_FORWARD:
    state = State.AIMING;
    break;
    ...
}
```


{% endmethod %}