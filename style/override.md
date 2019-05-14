# Override

When using inheritance, always use the appropriate keyword to mark that a function is overriding another function.

{% tabs %}
{% tab title="C++" %}
Mark functions you want overridden as `virtual`. Make sure the proper visibility is used IE `protected` or `public`.

When overriding functions, always include the `override` or `final` keyword so the compiler can raise errors if you use the wrong function signature or the base class changes.

If your class contains any `virtual` functions, make sure to declare the destructor `virtual` as well.

If you don't want a function to be overridden, use the `final` keyword on the `class` or function.

If you have an abstract class \(meaning the base class should never be constructed on it's own, only it's subclasses\) mark functions you want abstract with `= 0` . Also, if you are using Visual Studio, mark the class with `__declspec(novtable)` to save memory on the virtual pointer table on the base class.
{% endtab %}

{% tab title="Java" %}
Use the `@Override` annotation when overriding a function.

Always make sure to call the `super` version of the function unless the documentation explicitly says otherwise.
{% endtab %}
{% endtabs %}

