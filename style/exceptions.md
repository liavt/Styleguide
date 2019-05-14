# Exceptions

Functions should validate that their arguments are correct and `throw` otherwise.

Functions should also validate that their preconditions are met \(unless documented otherwise.\) If the function's preconditions are not met, `throw`

{% hint style="warning" %}
**EXCEPTION:** Sometimes performance-critical code may need to skip argument validation in favor of speed. In these cases, the documentation should make very clear that arguments are not being validated. I also like to create a special flag to enable strict argument checking in debug modes so that people can feel more confident.
{% endhint %}

Document thrown exceptions in the documenting comment.

Never ignore errors in a `try...catch`. If the error must be ignored, print a warning to console, or at least comment why it is ignored.

"Unreachable" catch statements must still rethrow their errors just in case

When using C++, make sure to catch `exceptions` by `const &`

