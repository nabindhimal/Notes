
### Methods

6 min

Remember that [methods](https://www.codecademy.com/resources/docs/javascript/methods?page_ref=catalog) are actions we can perform. Data types have access to specific methods that allow us to handle instances of that data type. JavaScript provides a number of string methods.

We _call_, or use, these methods by appending an instance with:

- a period (the dot operator)
- the name of the method
- opening and closing parentheses

E.g. `'example string'.methodName()`.

Does that syntax look a little familiar? When we use `console.log()` we’re calling the `.log()` method on the `console` object. Let’s see `console.log()` and some real string methods in action!

```
console.log('hello'.toUpperCase()); // Prints 'HELLO'console.log('Hey'.startsWith('H')); // Prints true
```

Let’s look at each of the lines above:

- On the first line, the [`.toUpperCase()`](https://www.codecademy.com/resources/docs/javascript/strings/toUpperCase) method is called on the string instance `'hello'`. The result is logged to the console. This method returns a string in all capital letters: `'HELLO'`.
- On the second line, the [`.startsWith()`](https://www.codecademy.com/resources/docs/javascript/strings/startsWith) method is called on the string instance `'Hey'`. This method also accepts the character `'H'` as an input, or _argument_, between the parentheses. Since the string `'Hey'` does start with the letter `'H'`, the method returns the boolean `true`.

You can find a list of built-in string methods in the [JavaScript documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/prototype). Developers use documentation as a reference tool. It describes JavaScript’s keywords, methods, and syntax.