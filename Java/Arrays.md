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




### Traversing 2D Arrays: Introduction

In the last exercise, we reviewed how to use nested [loops](https://www.codecademy.com/resources/docs/java/loops) as well as how to iterate through regular [arrays](https://www.codecademy.com/resources/docs/java/arrays) using loops. In this exercise, we will apply that knowledge in order to learn how to traverse 2D arrays.

Traversing 2D arrays using loops is important because it allows us to access many elements quickly, access elements in very large 2D arrays, and even access elements in 2D arrays of unknown sizes.

Let’s remember the structure of 2D arrays in Java:

```
char[][] letterBlock = {{'a','b','c'},{'d','e','f'},{'g','h','i'},{'j', 'k', 'l'}};
```

In Java, 2D arrays are like normal arrays, but each element is another array. This is shown by the initialized 2D array above. The outer array consists of four elements, where each element consists of a three element subarray.

Let’s see what happens when we access elements of the outer array

```
System.out.println(Arrays.toString(letterBlock[0]) + "\n");System.out.println(Arrays.toString(letterBlock[1]) + "\n");System.out.println(Arrays.toString(letterBlock[2]) + "\n");System.out.println(Arrays.toString(letterBlock[3]) + "\n");
```

Here is the [output](https://www.codecademy.com/resources/docs/java/output) of the above code:

```
[a, b, c][d, e, f][g, h, i][j, k, l]
```

As you can see, we can retrieve the entire subarray from each of the outer array elements. If you look at how we are accessing these subarrays, we are just increasing the index. This means we can access each sub-array in the 2D array using a loop!

Let’s take a look at an example which produces the same output, but can handle any sized 2D array.

```
for(int index = 0; index < letterBlock.length; index++){    System.out.println(Arrays.toString(letterBlock[index]) + "\n");}
```

Here is the result:

```
[a, b, c][d, e, f][g, h, i][j, k, l]
```

Now let’s remember how to access a value from the subarray. Previously, we learned that we can use the double brackets `[][]`, where the first set of brackets contains the index of the element of the outer array and the second set of brackets contains the index of the element in the subarray. If we wanted to retrieve the letter `'f'` we would use:

`char storedLetter = letterBlock[1][2];`

Since we know we can use a loop to retrieve each of the subarrays stored in the outer array, we can then use a nested loop to access each of the elements from the sub-array.

You might be wondering how we can figure out the number of iterations needed in order to fully traverse the 2D array.

- In order to find the number of elements in the outer array, we just need to get the length of the 2D array.
    - `int lengthOfOuterArray = letterBlock.length;`
    - When thinking about the 2D array in matrix form, this is the height of the matrix (the number of rows)
- In order to find the number of elements in the subarray, we can get the length of the subarray after it has been retrieved from the outer array.
    - Remember that we retrieved the sub array earlier using this format:
        - `char[] subArray = letterBlock[0];`
    - Therefore, we can use this to get the length of the first subarray in the 2D array
        - `int lengthOfSubArray = letterBlock[0].length;`
        - When thinking about the 2D array in matrix form, this is the width of the matrix (the number of columns)
    - In most cases, getting the length of the first subarray in the 2D array will apply to the rest of the subarrays (if it is rectangular in shape), but there are rare occasions where the length of the subarrays could be different. This occurs if the 2D array is a jagged array. We won’t be working with any jagged 2D arrays in this lesson, but it’s something to keep in mind.

Let’s look at an example!

```
for(int a = 0; a < letterBlock.length; a++) {    for(int b = 0; b < letterBlock[a].length; b++) {        System.out.print("Accessed: " + letterBlock[a][b] + "\t");    }    System.out.println();}
```

You can think of the variable `a` as being the outer loop index, and the variable `b` as being the inner loop index.

Here is the output:

```
Accessed: a Accessed: b Accessed: c Accessed: d Accessed: e Accessed: f Accessed: g Accessed: h Accessed: i 
```

Within the nested **for** loop, we can see that each of the subarray elements are being accessed by using the outer loop index for the outer array, and the inner loop index for the subarray.

Here is a diagram to help visualize how the 2D array is traversed using nested loops:

![The outer loop controls what row we're in while the inner loop controls which element of that row we're looking at](https://static-assets.codecademy.com/Paths/ap-computer-science/TwoDArrays/traversal.png)

We don’t have to only use regular **for** loops for traversing 2D arrays. We can use enhanced **for** loops if we do not need to keep track of the indices. Since enhanced **for** loops only use the element of the arrays, it is a bit more cumbersome to keep track of which index we are at. This same idea applies to while and do-while loops as well. This is why we usually use regular **for** loops except for when we want to do something simple like printing.

We have gone over how to think about 2D array traversal in terms of arrays of arrays, but there are two main ways of thinking about traversal in terms of rows and columns. These are called row-major order and column-major order.





### Traversing 2D Arrays: Practice with Loops

We have seen how to traverse 2D [arrays](https://www.codecademy.com/resources/docs/java/arrays) using standard **for** [loops](https://www.codecademy.com/resources/docs/java/loops), but in this exercise, we will practice traversing them using some other loop types. For example, you may want to only retrieve elements without keeping track of the indices using enhanced **for** loops, or you could continuously update the 2D array until a condition is met using **while** loops.

In enhanced **for** loops, each element is iterated through until the end of the array. When we think about the structure of 2D arrays in Java (arrays of array objects) then we know that the outer enhanced **for** loop elements are going to be arrays.

Let’s take a look at an example:

Given this 2D array of character data:

```
char[][] charData = {{'a', 'b', 'c', 'd', 'e', 'f'},{'g', 'h', 'i', 'j', 'k', 'l'}};
```

Print out every character using enhanced **for** loops:

```
for(char[] charRow : charData) {    for(char c : charRow) {        System.out.print(c + " ");    }    System.out.println();}
```

Remember that the syntax for enhanced **for** loops looks like so: `for( datatype elementName : arrayName){`. Since 2D arrays in Java are arrays of arrays, each element in the outer enhanced **for** loop is an entire row of the 2D array. The nested enhanced **for** loop is then used to iterate through each element in the extracted row. Here is the [output](https://www.codecademy.com/resources/docs/java/output) of the above code:

```
a b c d e f g h i j k l
```

Here is an example which accomplishes the same thing, but using **while** loops:

```
int i = 0, j=0;while(i<charData.length) {    j = 0;    while(j<charData[i].length) {        System.out.print(charData[i][j] + " ");        j++;    }    System.out.println();    i++;}
```

Here is the output of the above code:

```
a b c d e f g h i j k l
```

Notice how we can use different loop types for traversal, but still receive the same result.

Let’s work some example problems using different loop types!





