# Constants

A constant is defined as a variable that can't be changed.

Constants are in ALL\_UPPERCASE\_WITH\_UNDERSCORES \(capitalized snake case\)

Constants always have `static final`

```text
public static final String THIS_IS_A_CONSTANT = "Constantly following the rules!";
```

Constants can be macros or `const` variables. It is highly recommended to make constants `constexpr` and `inline` as well.

```text

#define MACE_CONSTANT_INOPLE 3.45921321 

namespace mc {
    const constexpr int SPECIAL_NUMBER = 342131;
}
```

If using a macro as a constant, always prefix it with an underscore afterwards. This prefix should be unique to your project.

Functional macros follow the same rules as a normal constant. They must also be verbs.

```text
#define MACE_STRINGIFY(name) #name
#define MACE_SUM(a, b) a + b
```

Functional macros with multiple lines must be wrapped in a `do...while` block

```text
#define MACE_DO_MULTILINE() do{ ... }while(0)
```

{% hint style="info" %}
_REASONING:_ [See this post for the do...while rule](https://stackoverflow.com/a/1067238)
{% endhint %}

## Global Constants <a id="global-constants"></a>

Try to avoid non-constant global variables.

{% hint style="info" %}
_REASONING:_ One of the biggest factors to spaghetti code are global variables. For example, look at this code:

```text
void doSomething(){
  OtherClass.foo = "I like spaghetti";
}
...
woawver.doSomething();
```

This code is a prime example of how spaghetti code is formed. `doSomething()` now affects other classes and variables, so that can cause confusion to anyone using `doSomething()` as to why the global constant has changed it's value!

The better way to do the above code that isn't a delicious italian product is like this:

```java
String doSomething(){
  return "I am still hungry":
}
...
OtherClass.foo = woawver.doSomething()
```

This new technique produces completely identical code, adds more versality as now `doSomething()` can be used anywhere, and reduces confusion. All because you got rid of global constants!
{% endhint %}

## Magic Constants <a id="magic-constants"></a>

A magic constant is a literal in your code that doesn't have any meaning or explanation.

Instead of embedding literals into code, create a constant at the top of the file to reduce spatghetti code and allow for more configurability.

{% tabs %}
{% tab title="C++" %}
You can use `#define` or `const constexpr` constants.

BAD:

```cpp
Renderer::getModel("my-model!");
```

GOOD:

```cpp
#define MACE_MY_MODEL_LOCATION "my-model!"

...
Renderer::getModel(MACE_MY_MODEL_LOCATION);
```
{% endtab %}

{% tab title="Java" %}
BAD:

```java
Renderer.get("my-model!");
```

GOOD:

```java
private static final MY_MODEL_LOCATION "my-model!"

...
Renderer.get(MY_MODEL_LOCATION);
```
{% endtab %}
{% endtabs %}

