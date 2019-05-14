#Variables

{% method -%}

You will use camelCase for names of functions and variables, which means no underscores, and every word but the first is capitalized.

{% sample lang="java" -%}
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

{% sample lang="cpp" -%}

BAD:
```cpp
int ThisIsAVariable
int this_is_a_variable
int thisisavariable
int thIsiSaVariABLE
```
GOOD:
```cpp
int thisIsAVariable
```

{% endmethod %}

{% method -%}

Names should be descriptive, and explain their purpose.

Names should also ALWAYS be nouns, never verbs, never adjectives. If you feel the need to have it's name be a verb, consider a [function](/functions.md) instead.

{% sample lang="java" -%}
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
{% sample lang="cpp" -%}
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

{% endmethod %}

![](http://www.commitstrip.com/wp-content/uploads/2013/04/Strip-Nom-de-variable-550-finalenglish1.jpg)