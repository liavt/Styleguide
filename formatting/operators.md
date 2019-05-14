# Operators

Put spaces between all multi-operand operators so it doesn't look like a bunch of jumbled up math. Don't put spaces for parenthesis.

Accessing an array has no spaces: `a[3]`

A multi operand operator is such that has a left and right value, such as `2 + 3`.

A single operand operator is one that only has a single value, like `-2` or `~0x32`

{% tabs %}
{% tab title="C++" %}
Lambdas are weird and they have weird spacing. Just treat every segment as a separate section and apply the relevant style. Here is an example of the proper spacing of a lambda:

```text
(final int foo, final boolean bar) -> int {
    return 42;
}
```

The `sizeof`, `alignof`, `*_cast`, `noexcept`, and `typeid` operators follow the same rules of [functions.](../naming/functions.md)

There are no spaces for the `*`, `&`, and `->` \(pointer accessing\) operators

BAD:

```text
std:: cout<<std::string("hello")+Blah.SPACE +"world";
int a=(1+b/-(s+2));
```

GOOD:

```text
std::cout << std::string("hello") + Blah.SPACE +"world";
int a = (1 + b / -(s + 2));
```
{% endtab %}

{% tab title="Java" %}
In addition to the above section, the following Java-specific operators require spaces: ```>>>`` `>>>=` `instanceof` `->`

The `::` operator in Java 8 does not require a space: `Foo::blah`

BAD:

```text
System.out.println("hello"+Blah.SPACE+"world");
int a=(1+b/-(s+2));
```

GOOD:

```text
System.out.println("hello" + Blah.SPACE + "world");
int a = (1 + b / -(s + 2));
```
{% endtab %}
{% endtabs %}

