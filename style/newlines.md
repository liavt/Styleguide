# Newlines

Always use the language-specific alternative to a platform-specific newline.

{% hint style="info" %}
_REASONING:_ Some platforms use `\n`, some use `\r\n`. Hardcoding these values into your program could cause some compatibility issues with other platforms.
{% endhint %}

{% tabs %}
{% tab title="C++" %}
Using `std::endl` or `\n`. `std::cout` will correctly format `\n` to the correct platform newline character. It is recommended to still use `std::endl`. HOWEVER, `std::endl` will flush the `ostream`, so if you want to avoid that, use a plain `\n` \(not `\r\n`\)
{% endtab %}

{% tab title="Java" %}
Use `System.lineSeperator()`

BAD:

```text
System.out.println("Hello!\n");
```

GOOD:

```text
System.out.println("Hello!" + System.lineSeparator());
```
{% endtab %}
{% endtabs %}

