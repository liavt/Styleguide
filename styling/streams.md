#RAII

{% method -%}

When using a stream, `Closeable`, or any class that uses RAII always properly close it with regard to exceptions.

{% sample lang="java" -%}

Use `try...finally` syntax.

EXAMPLE:
```java
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
```java
try(final BufferedReader r = new BufferedReader(new InputStreamReader(address.openStream()))){
    String inLine;
    while ((inLine = r.readLine()) != null) {
        System.out.println(inLine);
    }
}
```

{% sample lang="cpp" -%}

To avoid having to manually do `try...catch`, try to use scoped guards such as `unique_ptr` or `scoped_guard`. Always try to follow RAII principles in `class`es you write.

{% endmethod %}
