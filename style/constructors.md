# Constructors

Always try to provide a default constructor if possible.

Always try to initialize variables with their declaration.

{% tabs %}
{% tab title="C++" %}
Delegating constructors is much faster than using assignment.

```text
Foo(const unsigned int f, const bool b) : foo(f), bar(b) {}
```

Always follow the rule of three: if you include one of the following, you have to include all of them.

* Constructor
* Destructor
* Copy constructor

In `virtual` classes, always declare the destructor `virtual`.

Aggregate initialization for `struct`s is great. Use them.

Not required, but declaring your constructor and destructor `noexcept` is good practice.
{% endtab %}

{% tab title="Java" %}
When extending a class, always make sure to call `super()` unless the documentation explicitly tells you not to.
{% endtab %}
{% endtabs %}



