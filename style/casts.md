# Casts

Always be as explicit as possible when casting primitive types. This also means using `static_cast<T>()` in C++ instead of the standard C-Style cast `(T)`.

{% hint style="info" %}
_REASONING:_ The compiler will throw an error or warning when doing a conversion you shouldn't. Plus, explicit casting clarifies any confusion to the compiler or other developers.
{% endhint %}

