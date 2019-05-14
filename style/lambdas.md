# Lambdas

Use lambda expressions and interfaces to increase modularity in your code.

{% tabs %}
{% tab title="C++" %}
Avoid catching all by value `[=]` or by reference `[&]` when declaring a lambda function. Try to list out every variable your lambda will need, and prefer to pass by reference as opposed to by value.

When using a function pointer, always put the `&` \(dereference operator\) to avoid any confusion.

BAD:

```text
foo(frc5431::myLambda);
```

GOOD:

```text
foo(&frc5431::myLambda);
```
{% endtab %}

{% tab title="Java" %}
When defining a functional interface, use the `@FunctionalInterface` annotation:

```text
@FunctionalInterface
public interface Footerface {
  public void doFoo();
}
```
{% endtab %}
{% endtabs %}

