
### Introduction to String Methods

As you may recall, a [`String`](https://www.codecademy.com/resources/docs/java/strings?page_ref=catalog), which is widely used in Java, is an object that represents a sequence of characters. It is a great way to store information.

Because character strings are so vital to programming, Java dedicated an entire class to them. This is great news for us because the `String` class has a lot of useful [methods](https://www.codecademy.com/resources/docs/java/methods) to help us perform operations on `Strings` and data manipulation. We don’t have to import anything to use the `String` class because it’s part of the `java.lang` package which is available by default.

In this lesson, we will go over several `String` methods:

- `length()`
- `concat()`
- `equals()`
- `indexOf()`
- `charAt()`
- `substring()`
- `toUpperCase()` / `toLowerCase()`

Let’s get started!



### length()

In Java, the [`length()`](https://www.codecademy.com/resources/docs/java/strings/length?page_ref=catalog) string method returns the length ⁠— total number of characters ⁠— of a `String`.

Suppose we have a `String` called `str`, `str.length()` would return its length.

Take a look at this code for example:

```
String str = "Hello World!";  System.out.println(str.length());
```

`12` would be printed because `str` has 12 characters:

`H` `e` `l` `l` `o` `_` `W` `o` `r` `l` `d` `!`

In theory, the length of a `String` is the same as the [Unicode](https://en.wikipedia.org/wiki/Unicode) units of the `String`. For example, escape sequences such as `\n` count as only one character.



### concat()

The [`concat()`](https://www.codecademy.com/resources/docs/java/strings/concat?page_ref=catalog) method concatenates one string to the end of another string. Concatenation is the operation of joining two strings together.

Suppose we have a `String` called `str1` and another `String` called `str2`, using `str1.concat(str2)` would return `str1` with `str2` appended to the end of it.

For example:

```
String name = new String("Code");name = name.concat("cademy");System.out.println(name);
```

`Codecademy` would be printed.

`String`s are immutable objects which means that `String` [methods](https://www.codecademy.com/resources/docs/java/methods), like `concat()` do not actually change a `String` object.

Our variable, `name` holds a reference to the `String` object, `"Code"`. When we use `concat()` on `name`, we changed its value so that it references a new object — `"Code"`, combined with the String literal, `"cademy"`.

Suppose we do something slightly different. We’ll use `concat()` on `name` without reassigning its value:

```
String name = "Code";name.concat("cademy");System.out.println(name);
```

`Code` would be printed instead. The value of the `String` can’t change! Instead, we create a new object and need to assign that new object to some variable.

**Keep Reading: AP Computer Science A Students**

When we first discussed Objects we learned that if we tried printing an Object, we’d get an [output](https://www.codecademy.com/resources/docs/java/output) of the class name and the Object’s memory address. If we wanted to get a more useful printout, we’d have to call the Object’s `toString()` method.

This `toString()` method comes into play with `concat()`. If we concatenate a String with another Object, we’re really adding the result of that Object’s `toString()` method to our original String. We can even see this when we concatenate two Strings together (remember a String is an Object). When we use `concat()` on another String, we don’t concatenate its memory address to the original String. Instead, we combine the result of its `toString()` method to the original String.

You can refresh yourself on the `toString()` method in [this exercise](https://www.codecademy.com/courses/learn-java/lessons/learn-java-methods/exercises/the-tostring-method).





### equals()

With objects, such as `String`s, we can’t use the primitive equality operator `==` to check for equality between two strings. To test equality with strings, we use a built-in method called [`equals()`](https://www.codecademy.com/resources/docs/java/strings/equals?page_ref=catalog).

For example:

```
String flavor1 = "Mango";String flavor2 = "Peach";System.out.println(flavor1.equals("Mango"));// prints trueSystem.out.println(flavor2.equals("Mango"));// prints false
```

Side note, there’s also an [`equalsIgnoreCase()`](https://www.codecademy.com/resources/docs/java/strings/equalsIgnoreCase?page_ref=catalog) method that compares two strings without considering upper/lower cases.

**Keep Reading: AP Computer Science A Students**

We can also compare `String` values lexicographically (think dictionary order) using the [`.compareTo()`](https://www.codecademy.com/resources/docs/java/strings/compareTo?page_ref=catalog) method. When we call the `.compareTo()` method, each character in the `String` is converted to Unicode; then the Unicode character from each `String` is compared.

The method will return an `int` that represents the difference between the two Strings.

For example:

```
String flavor1 = "Mango";String flavor2 = "Peach";System.out.println(flavor1.compareTo(flavor2)); 
```

Our program above will [output](https://www.codecademy.com/resources/docs/java/output) `-3`.

When we use `.compareTo()`, we must pay attention to the return value:

- If the method returns `0`, the two `String`s are equal.
- If the value is less than `0`, then the `String` object is lexicographically less than the `String` object argument.
- If the value is greater than `0`, then the `String` object is lexicographically greater than the `String` object argument.

In the example above, `"Mango"` comes before `"Peach"`, so we get a negative number (we specifically get `-3` because the Unicode values of `"M"` and `"P"` differ by 3). If we did `flavor2.compareTo(flavor1)`, we would get `3`, signifying that `"Peach"` is greater than `"Mango"`.

**Note:** Make sure to pay attention to capitalization when using `.compareTo()`. Upper case and lower case letters have different Unicode values. For example, when comparing `"Mango"` and `"Peach"`, we got `-3`, meaning that `"Mango"` was smaller. But if we compare `"mango"` and `"Peach"` we get `29`. The Unicode value for lower case `"m"` is actually larger than upper case `"P"`. Using [`.compareToIgnoreCase()`](https://www.codecademy.com/resources/docs/java/strings/compareToIgnoreCase?page_ref=catalog) will perform the same task, but will not consider upper/lower case.





### indexOf()

If we want to know the index of the first occurence of a character in a string, we can use the [`indexOf()`](https://www.codecademy.com/resources/docs/java/strings/indexOf?page_ref=catalog) method on a string.

Remember that the indices in Java start with 0:

```
String letters = "ABCDEFGHIJKLMN";System.out.println(letters.indexOf("C"));
```

This would [output](https://www.codecademy.com/resources/docs/java/output) `2`.

Although `C` is the third letter in the English alphabet, it is located in the second index of the string.

Suppose we want to know the index of the first occurrence of an entire substring. The `indexOf()` instance method can also return where the substring begins (the index of the first character in the substring):

```
String letters = "ABCDEFGHIJKLMN";System.out.println(letters.indexOf("EFG"));
```

This would output `4`, because `EFG` starts at index 4.

If the `indexOf()` doesn’t find what it’s looking for, it’ll return a `-1`.






### charAt()

The [`charAt()`](https://www.codecademy.com/resources/docs/java/strings/charAt?page_ref=catalog) method returns the character located at a `String`‘s specified index.

For example:

```
String str = "qwer";System.out.println(str.charAt(2));
```

It would [output](https://www.codecademy.com/resources/docs/java/output) `e` because that’s what’s at index 2. (Once again, indices start with 0.)

Suppose we try to return the character located at index 4. It would produce an `IndexOutOfBoundsException` error because index 4 is out of `str`‘s range:

```error
java.lang.StringIndexOutOfBoundsException: String index out of range: 4
```




### substring()

There may be times when we only want a part of a string. In such cases, we may want to extract a _substring_ from a string.

The [`substring()`](https://www.codecademy.com/resources/docs/java/strings/substring?page_ref=catalog) method does exactly that. For example:

```
String line = "The Heav'ns and all the Constellations rung";System.out.println(line.substring(24));
```

It would [output](https://www.codecademy.com/resources/docs/java/output) `Constellations rung` because that’s what begins at index 24 and ends at the end of `line`. The substring begins with the character at the specified index and extends to the end of the string.

Suppose we want a substring from the middle of the string. We can instead include two arguments in this method. For example:

```
String line = "The Heav'ns and all the Constellations rung";System.out.println(line.substring(27, 33));
```

When `substring()` is called with two arguments, the first argument is _inclusive_ and the second is _exclusive_. This means the resulting substring will begin at index 27 and extend up to, but _not_ including, index 33. Therefore, the example above would output `stella` because that’s the substring that begins at index 27 and ends at index 32, one index before 33.

We can use this method to return a single-element substring at a specific index. We do this by calling `substring()` with the desired index value as the first argument and then the index value plus one as the second argument.

For example, we can use this method to output just `C`:

```
String line = "The Heav'ns and all the Constellations rung";System.out.println(line.substring(24, 25));// Prints: C
```




### toUpperCase() / toLowerCase()

There will be times when we have a word in a case other than what we need it in. Luckily, Java has a couple `String` [methods](https://www.codecademy.com/resources/docs/java/methods) to help us out:

- [`toUpperCase()`](https://www.codecademy.com/resources/docs/java/strings/toUpperCase?page_ref=catalog): returns the string value converted to uppercase
- [`toLowerCase()`](https://www.codecademy.com/resources/docs/java/strings/toLowerCase?page_ref=catalog): returns the string value converted to lowercase

For example:

```
String input = "Cricket!";String upper = input.toUpperCase();// stores "CRICKET!"String lower = input.toLowerCase();// stores "cricket!"
```

A good use of this functionality is to ensure consistency of the data you store in a database. Making sure all of the data you get from a user is lowercase before you store it in your database will make your database easier to search through later.





### Review

Congratulations! 🙌

We have learned some of the string [methods](https://www.codecademy.com/resources/docs/java/methods) that come with the `String` class:

- `length()`
- `concat()`
- `indexOf()`
- `charAt()`
- `equals()` / `equalsIgnoreCase()`
- `substring()`
- `toUpperCase()` / `toLowerCase()`



