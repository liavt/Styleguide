## Code Formatting

### Variable names

![](http://www.commitstrip.com/wp-content/uploads/2016/09/Strip-Le-stagiaire-et-la-variable-english650-final.jpg)

#### Functions and variables formatting

You will use camelCase for names of functions and variables, which means no underscores, and every word but the first is capitalized.

BAD:
```java
int ThisIsAVariable
int this_is_a_variable
int thisisavariable
int thIsiSaVariABLE
```
GOOD:
```java
int thisIsAVariable
```

Names should be descriptive, and explain their purpose.

BAD:
```java
int foo
int blah
int poop
int woawver
```
GOOD:
```java
int pidControllerState
int currentTime
int keyIterator
```

#### Constants Formatting

Constants are in ALL_UPPERCASE_WITH_UNDERSCORES

#### Classes

A `class` is PascalCase, which means no spaces, and every word is capitalized, including the first. An `interface` follows the same rules.

EXAMPLE:
BAD:
```java
class FoObAR {
class foo_bar {
class fooBar {
```
GOOD:
```java
class FooBar {
```

#### Enums

When making an `enum`, it follows the same rules for naming as a `class`. The values of the `enum` follows the rules for constant.

EXAMPLE:
BAD:
```java
enum FOO{
  Bar,
  wOaWvEr,
  baz,
  iAmBread
}
```
GOOD:
```java


`
enum Foo {
  BAR,
  WOAWVER,
  BAZ,
  I_AM_BREAD
}



```

#### General Rules

Names shouldn't be too long. If they come out to be huge, use an appropriate acronym, or more preferably, find a way to make it shorter. If you can't make it shorter and keep the original meaning, comment its actual purpose.

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

![](https://imgs.xkcd.com/comics/smfw.png)

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

![](https://imgs.xkcd.com/comics/third_way.png)

### Tabs vs Spaces

We will use tabs, which will be equal to 4 spaces.

*REASONING:*
Tabs can be configured to be any size on any platform. Plus, they are also a uniform way to keep all indentation the same.

### Brackets

When typing anything that requires curly brackets (conditionals, loops, functions, classes, etc), the first bracket goes on the same line as the definition. There is a space between the curly bracket and the end of the definition
BAD:
```java
void wombatEater()
{

void wombatEater()




{

void wombatEater(){//needs a space between bracket and wombatEater()
```
GOOD:
```java
void wombatEater() {
```

The second curly bracket will have its own line after the last line of the function

BAD:
```java
void wombatEater(){foo();}
void wombatEater(){
foo();}
```
GOOD:
```java
void wombatEater() {
  foo();
}
```

**EXCEPTION:** If a function is empty, it is okay to use `{}` syntax on the same line

Each time an opening curly bracket is encountered, indent by an extra tab.

EXAMPLE:
```java
int wombatEater(){
  if(blah){
    for(loop){
      bar();
    }
    foo();
  }
  return 1;
}
```

### If

`if` statements always have curly brackets on seperate lines. Even if they are one line statements.

EXAMPLE:
BAD:
```java
if(condition) code();

if(condition) { code(); }
```
GOOD:
```java
if(condition) {//don't forget the space!
  code();
}
```

*REASONING:*
There is a very important reason for this seemingly petty rule. It clarifies a lot of confusion.

For example, this code is very confusing at first glance:
```java
if(condition) foo(); bar(); //WARNING: bar() is NOT part of the if statement!
```

With this style guide, the above code will become much clearer:
```java
if(condition) {
  foo();
}
bar();
```

Another example of why this rule is absolutely important is because of what happend to OSX developers. They had some code which checked the signature of an SSL certificate. For those who don't know what that is, the function checked if an encryption was valid. Here was the code (in C:)
```c
hashOut.data = hashes + SSL_MD5_DIGEST_LEN;
hashOut.length = SSL_SHA1_DIGEST_LEN;
if ((err = SSLFreeBuffer(&hashCtx)) != 0)
    goto fail;
if ((err = ReadyHash(&SSLHashSHA1, &hashCtx)) != 0)
    goto fail;
if ((err = SSLHashSHA1.update(&hashCtx, &clientRandom)) != 0)
    goto fail;
if ((err = SSLHashSHA1.update(&hashCtx, &serverRandom)) != 0)
    goto fail;
if ((err = SSLHashSHA1.update(&hashCtx, &signedParams)) != 0)
    goto fail;
    goto fail;  /* MISTAKE! THIS LINE SHOULD NOT BE HERE */
if ((err = SSLHashSHA1.final(&hashCtx, &hashOut)) != 0)
    goto fail;

err = sslRawVerify(...);
```

Notice that the second `goto fail` always ran. This was a typo by OSX developers that actually opened up a HUGE security vulnerability. By always putting curly brackets, you prevent very hard-to-find errors such as this.

### Else
![](https://imgs.xkcd.com/comics/code_quality.png)

If you have an else-if the closing bracket and the else goes on the same line. Spaces go after the brackets.

BAD:
```java
}
else{

}else
if(){

}
else
if()
{
```
GOOD:
```java
} else if() {

} else{
```

### Long lines
Lines should not be unreasonably long. Use common sense to determine how long a line is. If it is too long, add new lines in between, and indent to be the same indentation level. This is also true with function arguments. Each level of parenthesis is a new indentation level.

BAD:
```java
int longVariable = gatherAshes(foo().wombat.consume().digest().intestines.explode().throwAt(blah).retrieveVariable().finally().almostThere().thereWeAre());
```
GOOD:
```java
int longVariable = gatherAshes(
                    foo().wombat.consume()
                    .digest().intestines
                    .explode().throwAt(blah)
                    .retrieveVariable().finally()
                    .almostThere().thereWeAre()
                  );
```

### Operators and Math operations

Put spaces between all operators and math operations so it doesn't look like a bunch of jumbled up math. Don't put spaces for parenthesis.
<br>
BAD:
```java
System.out.println("hello"+Blah.SPACE+"world");
int a=(1+b/(s+2));
```

GOOD:
```java
System.out.println("hello" + Blah.SPACE + "world");
int a = (1 + b / (s + 2));
```

### Newline and escape characters

Instead of `\n` or `\r\n`, use System.lineSeparator()<br>

BAD:
```java
System.out.println("Hello!\n");
```

GOOD:
```java
System.out.println("Hello!" + System.lineSeparator());
```

*REASONING:*
Some platforms use `\n`, some use `\r\n`. Hardcoding these values into your program could cause some compatibility issues with other platforms. `System.lineSeparator()` always returns the correct line separator for your platform.

### Comments

Comments can get hazy and a little more hazy depending on the program you are using. We would really
appreciate it if all coders follow these standards for commenting code. We will dedicate one person as
the code documenter and manager. To make sure the current code follows all of these standards.

First things first are single line comments. **Please don't put pointless comments**
When we mean pointless comments we mean comments that are obviouslt explaining nothing and is already
viewable by the code itself no explanation, such as these. <br>
BAD:
```java
int first = 1; //Sets first to one
int second = 2; //Sets second to two

int combined = first + second; //Adds first and second together
```
Those comments just take up space, aren't funny and just bother the reader because it's quite obvious
what the coder is doing. It's okay to put comments right above the line of code you want to comment, if 
you feel as if it's more readable <br>
GOOD:
```java
int motorPortOne = 123; //Check mapping on robot left motor is on CAN line 123
int motrPortTwo = 543; //Same as above, mapped to right motor

//Show users that motors have been initialized
System.out.println(motorPortOne + System.lineSeperator() + motorPortTwo);
```

**EXCEPTION:** The occasional funny joke is allowed, as long as it's not too distracting and replacing actual important comments.

Multiline comments are mainly used for functions, classes, structs, really important stuff and beginning
of files.
EXAMPLE: <br>
```java
/*
 * Beginning of file text
 * Created by Robotics Programming
 */
package org.usfirst.frc.team5431
 
/*
 * This class handles basic motor control
 * And movement, mapping -1 - 0 - 1 to a raw value
 */
public class Motor {
  /*
   * Sets the premapped motor values to a common
   * One between (Description provided by class)
   * Careful for explosion of function
   * No errror handling
   */
  public void setMotorSpeed(int newSpeed){
    ...
  }
}
```

Every function you write should have a JavaDoc comment documenting:
 * Parameters
 * Return value
 * Exceptions thrown
 * Preconditions/postconditions of params
 * Behavior of function

### Main code

`main()` should always return 0 if the program executed sucessfully. Specific error codes can be returned.

`main()` should not be too long, and no actual computations should be done there. It must only call functions or create variables.

### Loops

Put spaces in between mathmatical operators as if they are alone.

Put spaces after semicolons.

EXAMPLE:
BAD:
```java
for(int i=0;i<100;i++){
  //code
}
```
GOOD:
```java
for(int i = 0; i < 100; ++i) {
  //code
}
```

In a `for` loop, instead of `i++`, try `++i`. The latter has one less operation.

EXAMPLE:
BAD:
```java
for(int i = 0; i < 3; i++) {
  //code
}
```
GOOD:
```java
for(int i = 0; i < 3; ++i) {
  //code
}
```

**EXCEPTION:** Whether the `++` goes before or after the variable affects operator precendence. If the postfix version (`i++`) is required for order of operations purpose, use it.

Prefer `while` loops to `do...while`. The former is easier to understand at a glance.

### Goto

![](https://imgs.xkcd.com/comics/goto.png)

No. Do not use `goto`. If this were C, then maybe. But this is Java. If you absolutely have to use a `goto` statement, use a `switch case` instead or restructure your code.

### Switch Case

Do not put spaces in the parenthesis of the `switch` declaration.

The curly bracket goes on the same line with a space after the closing parenthesis.

EXAMPLE:
BAD:
```java
switch ( variable ) {

switch(variable){//no space
```
GOOD:
```java
switch(variable) {
```

`case` is not indented.

Always put `break` unless you intend fallthrough. If you are falling through, put each case on seperate lines.

Always put a `default` case. `default` should always be the very last case, unless you are intentionally falling through with it.

EXAMPLE:
BAD:
```java
case A:
  case B: case C: 
  //code
  break;
default:
case D: 
  //code
  break;
```
GOOD:
```java
case A:
case B:
case C:
  //code
  break;
case D:
default:
  break;
```

### Initialization

Always try to provide a default constructor if possible.

Always try to initialize variables with their declaration.

### Ordering of members

In a `class`, members will be ordered as following:
 * Enums
 * Nested classes
 * Constants
 * Static variables
 * Static functions
 * Instance variables
 * Default constructor
 * Constructor with arguments
 * Member functions
 
All `public` members go to the top of their respective categories, `protected` goes under `public`, package goes under `protected`, and `private` goes last.

EXAMPLE:
```java
class Foo {
  /**
  Foonums represents an enum of foos
  */
  enum Foonums {
    FOO1,
    FOO2,
    ...
  }
  
  /**
  ...
  */
  public static final int FOOBAR = 3;
  private static final bool IS_FOO = true;
  
  public static VERBOSE_FOO = false;
  
  public static void runFoo() {
    ...
  }
  
  public String fooName = "";
  private int fooAmount = 2;
  
  public Foo() {
  }

  ...
}
```

*REASONING:*
When you look at a class, the most important thing you usually look for is what you can use. By putting `public` members first, you are allowing people who read your `class` to find what they are usually looking for.
Having constants first also show configuration for your class.
Another way of explaining it is that whe people read your class, the want to see the interface of the component, not the implementation. This order puts the public interface before the ugly private implementation.
Good documentation plus a consistent ordering = easy to read classes
Also, brains like patterns, so if every file has the same ordering, you will eventually be used to knowing where to scroll to.

### Exceptions

Functions should validate that their arguments are correct and `throw` otherwise.

Functions should also validate that their preconditions are met, such as all of the `Motors` being initialized, robot being in a certain state, etc. If the function's preconditions are not met, `throw`

Document thrown exceptions in the JavaDoc

Never ignore errors in a `try...catch`. Use an error handler or `printStackTrace()`. If the error must be ignored, print a warning to console.

### Finally

When using a resources that needs to be closed (such as a `FileStream`) use the `try with...finally` syntax.

EXAMPLE:
```java
final BufferedReader r = new BufferedReader(new InputStreamReader(address.openStream()));
try{
    String inLine;
    while ((inLine = r.readLine()) != null) {
        System.out.println(inLine);
    }
}finally{
    r.close();
}
```
Or even better:
```java
try(final BufferedReader r = new BufferedReader(new InputStreamReader(address.openStream()))){
    String inLine;
    while ((inLine = r.readLine()) != null) {
        System.out.println(inLine);
    }
}
```

*REASONING:*
This makes sure that streams are always properly closed in the case of an exception

### Lambdas

Use lambda expressions and interfaces to increase modularity in your code.

When defining a functional interface, use the `@FunctionalInterface` annotation:
```java
@FunctionalInterface
public interface Footerface {
  public void doFoo();
}
```

### Overriding

When overriding a function from a parent, use the `@Override` annotation.

### Final Variables

Add the `final` keyword to every variable that you can

*CLARIFICATION:*
In Java, `final` simply means you can't reassign a variable. You can still call all member functions. For example, the following code works:
```java
final List<String> out = new ArrayList<String();
out.add("I can add stuff");
out.add("Even though it is final!");
```

This also works:
```java
class Position {
  public int x;
  public int y;
  public int z;
}

final Position pos = new Position();
pos.x = 5;//even though pos is final, pos.x isn't. Java is weird...
```

*REASONING:*
Sounds strange, but adding `final` to every read-only variable, no matter how small, has 2 purposes:
 * Clarifies confusion to other developers
 * Allows for the JVM to heavily optimize
 
Once you do it enough, it will become habit to add `final` to a variable by default. Of course, `final` shouldn't be applied to variables you are going to reassign.

### Final classes/methods

If you *really* don't want people to override your class, add `final` to it.

## Coding Style

### Global Constants

Try to avoid non-constant global variables.

*CLARIFICATION:*
Global constants are `static` variables.

*REASONING:*
One of the biggest factors to spaghetti code are global variables. For example, look at this code:

```java
void doSomething(){
  OtherClass.foo = "I like spaghetti";
}
...
woawver.doSomething();
```

This code is a prime example of how spaghetti code is formed. `doSomething()` now affects other classes, so that can cause confusion to anyone using `doSomething()` as to why `OtherClass.foo` suddenly changed value. Plus, anyone trying to read through the code will wonder "What is `OtherClass.foo`?"

The better way to do the above code that isn't a delicious italian product is like this:

```java
String doSomething(){
  return "I am still hungry":
}
...
OtherClass.foo = woawver.doSomething()
```
This new technique produces completely identical code, adds more versality as now `woawver.doSomething()` can be used anywhere, and reduces confusion. All because you got rid of `static` variables!

### Mappings

Mappings (such as for that like a joystick or motor) go into a single file, called `Mappings.java`. Every mapping type is organized by category, in the following order:
 * Buttons
 * Joysticks
 * Motors
 * DIO, Analog, or any other port on RoboRIO
 * Pneumatics
 * Other mappings
 
Each section will have a comment with the section name.

Mappings will be `public static final` and follow the naming for a constant.

EXAMPLE:
```java
class Mappings {
  //BUTTONS
  public static final int BALL_SHOOT = 0;
  public static final int BALL_LOAD = 1;
  ...

  //JOYSTICKS
  public static final int JOY_LEFT = 4;
  public static final int JOY_RIGHT = 5;
  ...
  
}
```

*REASONING:*
Time and time again we get to competition and change a motor or a limit switch and have to change it's ID. Time and time again we forget where we stored the ID. Having one file that is always consistently organized allows you to quickly find the mapping you are looking for.

### Magic constants

![](https://imgs.xkcd.com/comics/int_pi.png)

A magic constant is a literal in your code that doesn't have any meaning or explanation. Here is an example of a magic constant:

```java
NetworkTable.get("roborio-frc-5431.local");//"roborio-frc-5431.local" is a magic constant
```

Instead of embedding literals into code, create a constant at the top of the file to reduce spatghetti code and allow for more configurability.

```java
private static final NETWORKTABLE_LOCATION "roborio-frc-5431.local"

...
NetworkTable.get(NETWORKTABLE_LOCATION);
```

### Which Robot type to use

Use `IterativeRobot`

*REASONING:*
We have been using that for 2 years and it has proven us well. Don't change it if it ain't broke.

### Oredering of robot functions

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
This order is based on the when the funciton is called during an FRC match combined with common usage. `robotInit()` is always called first, then `autonomousInit()`, then `teleopInit()`. `disabled` is at the end because it is rarely used and not as important as the other functions.

### Getters and setters

Never use `public` variables. Always use getters and setters.

`protected` and package variables are okay.

**EXCEPTION:** There are very specific cases in which it's okay to use `public`, however those should be evaluated on a case-by-case basis. Usually, you can use `public` variables in POD (Plain Old Data) classes, where the `class` only contains variables and no methods at all.

*REASONING:*
 * Getters and setters provide more verbosity
 * Can provide argument checking when setting variables
 * Can check for `null`
 * More versatility and future-proofing coding

### Casts

Always be as explicit as possible when casting primitive types

*REASONING:*
The compiler will throw an error or warning when doing a conversion you shouldn't. Plus, explicit casting clarifies any confusion to the compiler or other developers.

### State Machines

Autonomous is to be written with state machines.

Instead of using `int`s to represent state, which has proven annoying and cause more clutter in the end, use `enum`'s.

This fixes the "magic number" problem

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

*REASONING:*
We have been using state machines for the past 2 years. We are quite used to them and they work well.

Using numbers has created really crazy state machines where you go from state 1 to state 53 to state -3 to state 16. Enums allow for self-documenting code that can also be changed in the future.

### Teleop functionality

Wrap different components of the robot in classes. Save state in variables that can be reset during robot phases. Create all variables in constructor.

For example, the drive base would have a `DriveBase` class. The `DriveBase` creats all of the motors and joysticks using the constants from the `Mappings` class in it's constructor. The contructor would be called in `robotInit()`.

`DriveBase` has a `setMode()` function which takes in an `enum` with at least the following values:
 * AUTON
 * TELOP

In `autonInit()`, `setMode(Mode.AUTON)` is called on the `DriveBase` variable. This allows the class to perform any auton-specific changes.

Maybe this could be implemented in an `interface` to allow for helper functions from a standard library

*REASONING:*
Java is an object-oriented langauge. The robot's components are all different objects. Thus, it makes sense to represent the robot in terms of objects, just like Java intends.
Classes allow for seperation of implementation and interface from your high level robot code.
It also provides a level of organization of the file based level.
Additionally, having components in terms of objects allow you to easily reset the robot. If you want to reinitialize a component on the robot, you just reassign the variable to a `new Class()`

### Robot class

The `Robot` class should have as minimal code as possible. All implementation should be left to other files.

*REASONING:*
Organizational sake. If you want fix a bug on the shooter for example, you would want to look in `Shooter.java` instead of parsing `Robot.java`.

### Drive Mode

Until a different drive system has been proven effective and drivers have enough time to practice, Tank Drive will be used, with the WPILib `DriveBase` class.

### Reversing a motor

If a motor is going backwards and it's supposed to logically go forward, check your wiring. Adding `.setReversed()` to the code causes spaghettification. If you do, create a new constant `boolean` in `Mappings.java` to specify whether the motor is reversed.

Basically, make sure the `.set(1.0)` always makes the motor logically go at max speed forward in both phases of the game. If it doesn't a quick code change doesn't help

### Do it right the first time

![](https://imgs.xkcd.com/comics/fixing_problems.png)

This is difficult for us. We are all guilty of it. That small change that "will be fixed later."

Doing it right the first time prevents stress, breaking down, and bugs later on. It will be hard, but each time you say "I'll fix this later," stop yourself and say "I'll spend 5 minutes now to write it correctly as opposed to spending 10 minutes later fixing it while sleep deprived." You'll thank yourself later when you are sleep deprived staying up until 2 to get Themis a shooter.

### Versioning

In the `Robot.java` file, add a `public static final String` constant with the name of `ROBOT_VERSION`. Whenever you make a major change to the robot, update this to the date you edited it plus a major feature of this build.

EXAMPLE:
```java
public static final ROBOT_VERSION = "8/21/2017 - 10 gear autonomous"
```

Then, in `robotInit()`, add the following line:

```java
System.out.println(ROBOT_VERSION);
```

*REASONING:*
This is to make sure we always have the right version of the code deployed, whether it be during competition or 2 years after competition.

## Meta

### Licensing and Credit

People do want credit for their own credit and work for their code.
Yet you can't just assume code is yours so Titan Robotics will have their own header. The header is located in a file called `LICENSE` in this repo. This header must be present in every file you create for Team 5431. Replace `<class documentation>` with JavaDoc style documentation for the class you are writing, and replace `<your name>` with your own name. 

### Github

![](https://imgs.xkcd.com/comics/git_commit.png)

If you are writing code for Titan Robotics, you must put the code in this organization, `frc5431`. Commit as frequently as possible. Commit titles should be brief, preferably under 50 characters, and commit descriptions should be as descriptive as possible.

If you are writing competition-critical code and competition is coming up, save the best working version to the `master` branch of the repo. Continue prototyping and pushing code to another branch which could be named `unstable` or `proto`.

### Adding changes on a whim

We all know that feeling. That feeling when you are thinking of a new feature and are getting really excited to add it and see it in action. It's fun to just add a bunch of cool features, but it is imperative that EVERY THING YOU ADD IS TESTED.

Even by adding 1 minor line of code, you must test the whole function again.

Sounds annoying, but this makes sure we don't have the robot spinning around during autonomous or inverted controls.

If you want to add cool prototype features, you can create a new branch called `unstable` and push to there. Once it is tested and proven to be 100% working, merge with `master`.

