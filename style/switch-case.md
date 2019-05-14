# Switch Case

Do not put spaces in the parenthesis of the `switch` declaration.

The curly bracket goes on the same line with a space after the closing parenthesis.

EXAMPLE: BAD:

```text
switch ( variable ) {

switch(variable){
```

GOOD:

```text
switch(variable) {
```

`case` is not indented.

Always put `break` unless you intend fallthrough. If you are falling through, put each case on seperate lines.

Always put a `default` case. `default` should always be the very last case, unless you are intentionally falling through with it.

Try to use `enum`'s whenever possible.

EXAMPLE: BAD:

```text
case A:
  case B: case C: 
  
  break;
default:
case D: 
  
  break;
```

GOOD:

```text
case A:
case B:
case C:
  
  break;
case D:
default:
  break;
```

When using `C++17` always include the `[[fallthrough]]` attribute when falling to the next block

