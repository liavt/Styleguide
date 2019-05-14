# Members

In a `class`, members will be ordered as following:

* Nested classes
* Enums
* Constants
* Static variables
* Static functions
* Instance variables
* Default constructor
* Constructor with arguments
* Member functions

All `public` members go to the top of their respective categories, `protected` goes under `public`, package goes under `protected`, and `private` goes last.

{% hint style="info" %}
_REASONING:_ When you look at a `class`, the most important thing you usually look for is what you can use. By putting `public` members first, you are allowing people who read your `class` to find what they are usually looking for. Having constants first also show configuration for your class. Another way of explaining it is that when people read your class, the want to see the interface of the component, not the implementation. This order puts the public interface before the ugly private implementation. Good documentation plus a consistent ordering = easy to read classes Also, brains like patterns, so if every file has the same ordering, you will eventually be used to knowing where to scroll to.
{% endhint %}

EXAMPLE:

{% tabs %}
{% tab title="C++" %}
```text
class Foo {
public:
  
  enum class Foonums {
    FOO1,
    FOO2,
    ...
  }

  
  const int FOOBAR = 3;
  const bool IS_FOO = true;

  VERBOSE_FOO = false;

  void runFoo();

  std::string fooName = "";

  Foo() noexcept;
  ~Foo() = default;
private:
  private int fooAmount = 2;

  ...
}
```
{% endtab %}

{% tab title="Java" %}
```text
class Foo {
  
  enum Foonums {
    FOO1,
    FOO2,
    ...
  }

  
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
{% endtab %}
{% endtabs %}

## Getters and setters <a id="getters-and-setters"></a>

Never use `public` variables. Always use getters and setters.

`protected` and package variables are okay.

{% hint style="warning" %}
**EXCEPTION:** There are very specific cases in which it's okay to use `public`, however those should be evaluated on a case-by-case basis. Usually, you can use `public` variables in POD \(Plain Old Data\) classes, where the `class` only contains variables and no methods at all.
{% endhint %}

{% hint style="info" %}
_REASONING:_

* Getters and setters provide more verbosity
* Can provide argument checking when setting variables
* Can check for `null`
* More versatility and future-proofing coding
{% endhint %}

