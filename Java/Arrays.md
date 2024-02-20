An array holds a fixed number of values of one type. Arrays hold `double`s, `int`s, `boolean`s, or any other primitives. Arrays can also contain `String`s as well as object references!



### Creating an Array Explicitly

Imagine that we’re using a program to keep track of the prices of different clothing items we want to buy. We would want a list of the prices and a list of the items they correspond to. To create an array, we provide a name and declare the type of data it holds:

```
double[] prices;
```

Just like with [variables](https://www.codecademy.com/resources/docs/java/variables), we can declare and initialize in the same line. This allows us to explicitly initialize the array to contain the data we want to store :

```
double[] prices = {13.15, 15.87, 14.22, 16.66};
```

We can use [arrays](https://www.codecademy.com/resources/docs/java/arrays) to hold `String`s and other objects as well as primitives:

```
String[] clothingItems = {"Tank Top", "Beanie", "Funny Socks", "Corduroys"};
```


### Importing Arrays

When we printed out the array we created in the last exercise, we saw a memory address that did not help us understand what was contained in the array.

If we want to have a more descriptive printout of the array itself, we need a `toString()` method that is provided by the [`Arrays`](https://www.codecademy.com/resources/docs/java/arrays) _package_ in Java.

```
import java.util.Arrays;
```

We put this at the top of the file, before we even define the class!

When we import a package in Java, we are making all of the [methods](https://www.codecademy.com/resources/docs/java/methods) of that package available in our code.


The `Arrays` package has many useful methods, including `Arrays.toString()`. When we pass an array into `Arrays.toString()`, we can see the contents of the array printed out:

```
import java.util.Arrays;public class Lottery(){    public static void main(String[] args){    int[] lotteryNumbers = {4, 8, 15, 16, 23, 42};    String betterPrintout = Arrays.toString(lotteryNumbers);    System.out.println(betterPrintout);  }}
```

This code will print:

```
[4, 8, 15, 16, 23, 42]
```


### Get Element By Index

Now that we have an array declared and initialized, we want to be able to get values out of it.

We use square brackets, `[` and `]`, to access data at a certain index:

```
double[] prices = {13.1, 15.87, 14.22, 16.66};System.out.println(prices[1]);
```

This command would print:

```
15.87
```

This happens because `15.87` is the item at the `1` index of the array. Remember, the index of an array starts at `0` and ends at an index of one less than the number of elements in the array.

If we try to access an element outside of its appropriate index range, we will receive an [`ArrayIndexOutOfBoundsException`](https://www.codecademy.com/resources/docs/java/errors/arrayindexoutofboundsexception) error.

For example, if we were to run the command `System.out.println(prices[5])`, we’d get the following output:

```error
java.lang.ArrayIndexOutOfBoundsException: 5
```



### Creating an Empty Array

We can also create empty [arrays](https://www.codecademy.com/resources/docs/java/arrays) and then fill the items one by one. Empty arrays have to be initialized with a fixed size:

```
String[] menuItems = new String[5];
```

Once you declare this size, it cannot be changed! This array will always be of size `5`.

After declaring and initializing, we can set each index of the array to be a different item:

```
menuItems[0] = "Veggie hot dog";menuItems[1] = "Potato salad";menuItems[2] = "Cornbread";menuItems[3] = "Roasted broccoli";menuItems[4] = "Coffee ice cream";
```

This group of commands has the same effect as assigning the entire array at once:

```
String[] menuItems = {"Veggie hot dog", "Potato salad", "Cornbread", "Roasted broccoli", "Coffee ice cream"};
```

We can also change an item after it has been assigned! Let’s say this restaurant is changing its broccoli dish to a cauliflower one:

```
menuItems[3] = "Baked cauliflower";
```

Now, the array looks like:

```
["Veggie hot dog", "Potato salad", "Cornbread", "Baked cauliflower", "Coffee ice cream"]
```

**Keep Reading: AP Computer Science A Students**

When we use `new` to create an empty array, each element of the array is initialized with a specific value depending on what type the element is:

|Data Type|Initialized Value|
|---|---|
|int|`0`|
|double|`0.0`|
|boolean|`false`|
|Reference|`null`|

For example, consider the following arrays:

```
String[] my_names = new String[5];int[] my_ages = new int[5];
```

Because a String is a reference to an Object, `my_names` will contain five `null`s. `my_ages` will contain five `0`s to begin with.



### Length

What if we have an array storing all the usernames for our program, and we want to quickly see how many users we have? To get the length of an array, we can access the `length` field of the array object:

```
String[] menuItems = new String[5];System.out.println(menuItems.length);
```

This command would print `5`, since the `menuItems` array has `5` slots, even though they are all empty.

If we print out the length of the `prices` array:

```
double[] prices = {13.1, 15.87, 14.22, 16.66};System.out.println(prices.length);
```

We would see `4`, since there are four items in the `prices` array!




### String[] args

When we write `main()` [methods](https://www.codecademy.com/resources/docs/java/methods) for our programs, we use the parameter `String[] args`. Now that we know about array syntax, we can start to parse what this means.

A `String[]` is an array made up of `String`s. Examples of `String` arrays:

```
String[] humans = {"Talesha", "Gareth", "Cassie", "Alex"};String[] robots = {"R2D2", "Marvin", "Bender", "Ava"};
```

The `args` parameter is another example of a `String` array. In this case, the array `args` contains the arguments that we pass in from the terminal when we run the class file. (So far, `args` has been empty.)

So how can you pass arguments to `main()`? Let’s say we have this class `HelloYou`:

```
public class HelloYou {  public static void main(String[] args) {    System.out.println("Hello " + args[0]);    }}
```

When we run the file `HelloYou` in the terminal with an argument of `"Laura"`:

```
java HelloYou Laura
```

We get the output:

```
Hello Laura
```

The `String[] args` would be interpreted as an array with one element, `"Laura"`.

When we use `args[0]` in the main method, we can access that element like we did in `HelloYou`.

### Review

We have now seen how to store a list of values in [arrays](https://www.codecademy.com/resources/docs/java/arrays). We can use this knowledge to make organized programs with more complex [variables](https://www.codecademy.com/resources/docs/java/variables).

Throughout the lesson, we have learned about:

- Creating arrays explicitly, using `{` and `}`.
- Accessing an index of an array using `[` and `]`.
- Creating empty arrays of a certain size, and filling the indices one by one.
- Getting the length of an array using `length`.
- Using the argument array `args` that is passed into the `main()` method of a class.


