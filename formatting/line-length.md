# Line Length

Lines should not be unreasonably long. Use common sense to determine how long a line is. If it is too long, add new lines in between, and indent to be the same indentation level. This is also true with function arguments. Each level of parenthesis is a new indentation level.

Usually, 80 characters wide is a great max width, as that allows for a standard Unix terminal to display the whole line without wrapping.

BAD:

```text
int longVariable = gatherAshes(foo().wombat.consume().digest().intestines.explode().throwAt(blah).retrieveVariable().finally().almostThere().thereWeAre());
```

GOOD:

```text
int longVariable = gatherAshes(
                    foo().wombat.consume()
                    .digest().intestines
                    .explode().throwAt(blah)
                    .retrieveVariable().finally()
                    .almostThere().thereWeAre()
                  );
```

