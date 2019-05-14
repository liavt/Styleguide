# Variables

You will use camelCase for names of functions and variables, which means no underscores, and every word but the first is capitalized.

BAD:

```text
int ThisIsAVariable
int this_is_a_variable
int thisisavariable
int thIsiSaVariABLE
```

GOOD:

```text
int thisIsAVariable
```

Names should be descriptive, and explain their purpose.

Names should also ALWAYS be nouns, never verbs, never adjectives. If you feel the need to have it's name be a verb, consider a [function](functions.md) instead.

BAD:

```text
int foo
int blah
int poop
int memer
```

GOOD:

```text
int controllerState
int currentTime
int keyIterator
```

When variables are inside of a class, they should be marked `private` if possible. Use getters and setters to access the variable publicly.

{% hint style="info" %}
_REASONING:_ By keeping the raw data `private` and limiting access to public functions, you are future proofing your API and protecting your raw data from misuse. What if, in the future, the class needs to store the data in a different type? Because you made everything getters and setters, the implementation details are hidden from the caller and you can easily migrate existing code!
{% endhint %}

