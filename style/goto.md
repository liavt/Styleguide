# Goto

No. Do not use `goto`. If you absolutely have to use a `goto` statement, use a `switch case` instead or restructure your code.

{% hint style="info" %}
_REASONING:_ `goto`'s lead to spaghetti code and unsafe practices. If you have to use `goto` and not `continue`, `return`, or `break`, then your code is not structured correctly \(or you are using assembly\)
{% endhint %}

