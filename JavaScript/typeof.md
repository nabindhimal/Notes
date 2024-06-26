
### typeof operator

4 min

While writing code, it can be useful to keep track of the [data types](https://www.codecademy.com/resources/docs/javascript/data-types) of the [variables](https://www.codecademy.com/resources/docs/javascript/variables) in your program. If you need to check the data type of a variable’s value, you can use the `typeof` operator.

The `typeof` operator checks the value to its right and _returns_, or passes back, a string of the data type.

```
const unknown1 = 'foo';console.log(typeof unknown1); // Output: stringconst unknown2 = 10;console.log(typeof unknown2); // Output: numberconst unknown3 = true; console.log(typeof unknown3); // Output: boolean
```

Let’s break down the first example. Since the value `unknown1` is `'foo'`, a string, `typeof unknown1` will return `'string'`.