# Brackets

When typing anything that requires curly brackets \(conditionals, loops, functions, classes, etc\), the first bracket goes on the same line as the definition. There is a space between the curly bracket and the end of the definition

BAD:

```text
public void eatWombats()
{

public void eatWombats()




{

void eatWombats(){
```

GOOD:

```text
public void eatWombats() {
```

The second curly bracket will have its own line after the last line of the function

BAD:

```text
void eatWombats(){foo();}
void eatWombats(){
foo();}
```

GOOD:

```text
void eatWombats() {
  foo();
}
```

{% hint style="warning" %}
**EXCEPTION:** If a function is empty, it is okay to use `{}` syntax on the same line. Remember to put the space!
{% endhint %}

Each time an opening curly bracket is encountered, indent by an extra tab.

```text
int eatWombat(){
  if(descriptiveBooleanName){
      for(int i = 0; i < 100; ++i){
        bar();
      }
      return foo();
  }
  return 1;
}
```

