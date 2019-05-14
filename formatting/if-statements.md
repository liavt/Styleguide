# If statements

Control statements like `if` , `else if`, `for`, `while`, `switch`, and `else` statements always have curly brackets on separate lines. Even if they are one line statements.

{% tabs %}
{% tab title="C++" %}
C++17 adds `if` initalizers. Similar to `for` loops, there should be a space in between the initializer and condition.

```text
if(int foo = 5; foo != 4) {
    
}
```
{% endtab %}

{% tab title="Java" %}
You can configure your Eclipse to apply this formatting whenever you press `Ctrl` `Shift` `R`

BAD:

```text
if(condition) code();

if(condition) { code(); }
```

GOOD:

```text
if(condition) {
  code();
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
_REASONING:_ There is a very important reason for this seemingly petty rule. It clarifies a lot of confusion.

For example, this code is very confusing at first glance:

```text
if(condition) foo(); bar(); 
```

With this style guide, the above code will become much clearer:

```text
if(condition) {
  foo();
}
bar();
```

Another example of why this rule is absolutely important is because of what happend to OSX developers. They had some code which checked the signature of an SSL certificate. For those who don't know what that is, the function checked if an encryption was valid. Here was the code \(in C:\)

```text
hashOut.data = hashes + SSL_MD5_DIGEST_LEN;
hashOut.length = SSL_SHA1_DIGEST_LEN;
if ((err = SSLFreeBuffer(&hashCtx)) != 0)
    goto fail;
if ((err = ReadyHash(&SSLHashSHA1, &hashCtx)) != 0)
    goto fail;
if ((err = SSLHashSHA1.update(&hashCtx, &clientRandom)) != 0)
    goto fail;
if ((err = SSLHashSHA1.update(&hashCtx, &serverRandom)) != 0)
    goto fail;
if ((err = SSLHashSHA1.update(&hashCtx, &signedParams)) != 0)
    goto fail;
    goto fail;  
if ((err = SSLHashSHA1.final(&hashCtx, &hashOut)) != 0)
    goto fail;

err = sslRawVerify(...);
```

Notice that the second `goto fail` always ran. This was a typo by OSX developers that actually opened up a HUGE security vulnerability. By always putting curly brackets, you prevent very hard-to-find errors such as this.
{% endhint %}

## Logical Operators <a id="logical-operators"></a>

When using logical operators such as `&&` and `||` always put a space in between the operands. Single operand operators such as `!`, `-`, or `~` don't have a space.

See more details in the [operators](operators.md) section.

Also, the same rules specified on the [Line Length](line-length.md) page apply to `if` statements.

```text
if(condition1 && !condition2 || (condition3() && ~condition4)) {
    
}
```

## Else <a id="else"></a>

If you have an else-if the closing bracket and the else goes on the same line. Spaces go after the brackets.

BAD:

```text
}
else{

}else
if(){

}
else
if()
{
```

GOOD:

```text
} else if() {

} else{
```

