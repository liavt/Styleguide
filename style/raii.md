# RAII

When using a stream, `Closeable`, or any class that uses RAII always properly close it with regard to exceptions.

{% tabs %}
{% tab title="C++" %}
To avoid having to manually do `try...catch`, try to use scoped guards such as `unique_ptr` or `scoped_guard`. Always try to follow RAII principles in `class`es you write by writing a proper constructor and destructor.

{% hint style="info" %}
There are some situations where you can't use RAII due to threading rules \(like with OpenGL\). In these catches, you need to use great care to make sure resources are properly cleaned up when an `exception` occurs.
{% endhint %}
{% endtab %}

{% tab title="Java" %}
Use `try...finally` syntax.

EXAMPLE:

```text
final BufferedReader r = new BufferedReader(new InputStreamReader(address.openStream()));
try{
    String inLine;
    while ((inLine = r.readLine()) != null) {
        System.out.println(inLine);
    }
}finally{
    r.close();
}
```

Or even better:

```text
try(final BufferedReader r = new BufferedReader(new InputStreamReader(address.openStream()))){
    String inLine;
    while ((inLine = r.readLine()) != null) {
        System.out.println(inLine);
    }
}
```
{% endtab %}
{% endtabs %}

