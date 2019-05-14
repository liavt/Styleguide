# Loops

Put spaces in between mathematical operators as if they are alone.

Put spaces after semicolons.

BAD:

```text
for(int i=0;i<100;i++){
  
}
```

GOOD:

```text
for(int i = 0; i < 100; ++i) {
  
}
```

In a `for` loop, instead of `i++`, try `++i`. The latter has one less operation.

{% hint style="warning" %}
**EXCEPTION:** Whether the `++` goes before or after the variable affects operator precedence. If the post fix version \(`i++`\) is required for order of operations purpose, use it.
{% endhint %}

Prefer `while` loops to `do...while`. The former is easier to understand at a glance.

