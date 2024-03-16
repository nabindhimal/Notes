
### While We're Here

A `while` loop looks a bit like an `if` statement:

```
while (silliness > 10) {  // code to run}
```

Like an `if` statement, the code inside a `while` loop will only run if the condition is `true`. However, a `while` loop will continue running the code over and over until the condition evaluates to `false`. So the code block will repeat until `silliness` is less than or equal to 10.

```
// set attempts to 0int attempts = 0;// enter loop if condition is truewhile (passcode != 0524 && attempts < 4) {  System.out.println("Try again.");  passcode = getNewPasscode();  attempts += 1;  // is condition still true?  // if so, repeat code block}// exit when condition is not true
```

`while` [loops](https://www.codecademy.com/resources/docs/java/loops) are extremely useful when you want to run some code until a specific change happens. However, if you aren’t certain that change will occur, beware the infinite loop!

_Infinite loops_ occur when the condition will never evaluate to `false`. This can cause your entire program to crash.

```
int hedgehogs = 5;// This will cause an infinite loop:while (hedgehogs < 6) {  System.out.println("Not enough hedgehogs!");}
```

In the example above, `hedgehogs` remains equal to `5`, which is less than `6`. So we would get an infinite loop.




### Incrementing While Loops

When looping through code, it’s common to use a counter variable. A _counter_ (also known as an _iterator_) is a variable used in the conditional logic of the loop and (usually) incremented in value during each iteration through the code. For example:

```
// counter is initializedint wishes = 0;// conditional logic uses counterwhile (wishes < 3) {  System.out.println("Wish granted.");  // counter is incremented  wishes++;}
```

In the above example, the counter `wishes` gets initialized before the loop with a value of `0`, then the program will keep printing `"Wish granted."` and adding `1` to `wishes` as long as `wishes` has a value of less than `3`. Once `wishes` reaches a value of `3` or more, the program will exit the loop.

So the [output](https://www.codecademy.com/resources/docs/java/output) would look like:

```
Wish granted.Wish granted.Wish granted.
```

We can also decrement counters like this:

```
int pushupsToDo = 10;while (pushupsToDo > 0) {  doPushup();  pushupsToDo--;}
```

In the code above, the counter, `pushupsToDo`, starts at 10, and increments down one at a time. When it hits 0, the loop exits.





### For Loops

Incrementing with [loops](https://www.codecademy.com/resources/docs/java/loops) is actually so common in programming that Java (like many other programming languages) includes syntax specifically to address this pattern: `for` loops.

A `for` _loop_ header is made up of the following three parts, each separated by a semicolon:

1. The initialization of the loop control variable.
2. A [`boolean`](https://www.codecademy.com/resources/docs/general/data-types/boolean) expression.
3. An increment or decrement statement.

The opening line might look like this:

```
for (int i = 0; i < 5; i++) {  // code that will run}
```

In a `for` loop, an initialization statement is run once in order to initialize the loop control variable. This variable is modified in every iteration, can be referenced in the loop body, and used to test the boolean condition. In the example above, `i` is the loop control variable.

Let’s breakdown the above example:

1. `i = 0`: `i` is initialized to `0`
2. `i < 5`: the loop is given a `boolean` condition that relies on the value of `i`. The loop will continue to execute until `i < 5` is `false`.
3. `i++`: `i` will increment at the end of each loop and before the condition is re-evaluated.

So the code will run through the loop a total of five times.

We’ll also hear the term “iteration” in reference to loops. When we _iterate_, it just means that we are repeating the same block of code.




### Using For Loops

Even though we can write `while` [loops](https://www.codecademy.com/resources/docs/java/loops) that accomplish the same task, `for` loops are useful because they help us remember to increment our counter — something that is easy to forget when we increment with a `while` loop.

Leaving out that line of code would cause an infinite loop — yikes!

Fortunately, equipped with our new understanding of `for` loops, we can help prevent infinite loops in our own code.

It’s important to be aware that, if we don’t create the correct `for` loop header, we can cause the iteration to loop one too many or one too few times; this occurrence is known as an “off by one” error.

For example, imagine we wanted to find the sum of the first ten numbers and wrote the following code:

```
int sum = 0;for (int i = 0; i < 10; i++) {  sum += i}
```

This code would produce an incorrect value of `45`. We skipped adding `10` to `sum` because our loop control variable started with a value of `0` and stopped the iteration after it had a value of `9`. We were off by one! We could fix this by changing the condition of our loop to be `i <= 10;` or `i < 11;`.

These [errors](https://www.codecademy.com/resources/docs/java/errors) can be tricky because, while they do not always produce an error in the terminal, they can cause some miscalculations in our code. These are called logical errors — the code runs fine, but it didn’t do what you expected it to do.




### Iterating Over Arrays and ArrayLists

One common pattern we’ll encounter as a programmer is _traversing_, or looping, through a list of data and doing something with each item. In Java, that list would be an [array](https://www.codecademy.com/resources/docs/java/arrays?page_ref=catalog) or [`ArrayList`](https://www.codecademy.com/resources/docs/java/array-list?page_ref=catalog) and the loop could be a `for` loop. But wait, how does this work?

In order to traverse an array or `ArrayList` using a loop, we must find a way to access each element via its index. We may recall that `for` [loops](https://www.codecademy.com/resources/docs/java/loops) are created with a counter variable. We can use that counter to track the index of the current element as we iterate over the list of data.

Because the first index in an array or `ArrayList` is `0`, the counter would begin with a value of `0` and increment until the end of the list. So we can increment through the array or `ArrayList` using its indices.

For example, if we wanted to add `1` to every `int` item in an array `secretCode`, we could do this:

```
for (int i = 0; i < secretCode.length; i++) {  // Increase value of element value by 1  secretCode[i] += 1;}
```

Notice that our condition in this example is `i < secretCode.length`. Because array indices start at 0, the length of `secretCode` is 1 larger than its final index. A loop should stop its traversal before its counter variable is equal to the length of the list.

To give a concrete example, if the length of an array is `5`, the last index we want to access is `4`. If we were to try to access index `5`, we would get an [`ArrayIndexOutOfBoundsException`](https://www.codecademy.com/resources/docs/java/errors/arrayindexoutofboundsexception?page_ref=catalog) error! This is a very common mistake when first starting to traverse arrays.

Traversing an `ArrayList` looks very similar:

```
for (int i = 0; i < secretCode.size(); i++) {  // Increase value of element value by 1  int num = secretCode.get(i);  secretCode.set(i, num + 1);}
```

We can also use `while` loops to traverse through arrays and `ArrayList`s. If we use a `while` loop, we need to create our own counter variable to access individual elements. We’ll also set our condition to continue looping until our counter variable equals the list length.

For example, let’s use a `while` loop to traverse through an array:

```
int i = 0; // initialize counterwhile (i < secretCode.length) {  secretCode[i] += 1;  i++; // increment the while loop}
```

Traversing through an `ArrayList` with a `while` loop would look like this:

```
int i = 0; // initialize counterwhile (i < secretCode.size()) {  int num = secretCode.get(i);  secretCode.set(i, num + 1);  i++; // increment the while loop}
```




### break and continue

If we ever want to exit a loop before it finishes all its iterations or want to skip one of the iterations, we can use the `break` and `continue` keywords.

The `break` keyword is used to exit, or break, a loop. Once `break` is executed, the loop will stop iterating. For example:

```
for (int i = 0; i < 10; i++) {  System.out.println(i);  if (i == 4) {    break;  }}
```

Even though the loop was set to iterate until the condition `i < 10` is `false`, the above code will [output](https://www.codecademy.com/resources/docs/java/output) the following because we used `break`:

```
01234
```

The `continue` keyword can be placed inside of a loop if we want to skip an iteration. If `continue` is executed, the current loop iteration will immediately end, and the next iteration will begin. We can use the `continue` keyword to skip any even valued iteration:

```
int[] numbers = {1, 2, 3, 4, 5};    for (int i = 0; i < numbers.length; i++) {  if (numbers[i] % 2 == 0) {    continue;  }  System.out.println(numbers[i]);}
```

This program would output the following:

```
135
```

In this case, if a number is even, we hit a `continue` statement, which skips the rest of that iteration, so the print statement is skipped. As a result, we only see odd numbers print.

**Keep Reading: AP Computer Science A Students**

Loops can exist all throughout our code - including inside a method. If the `return` keyword was executed inside a loop contained in a method, then the loop iteration would be stopped and the method/constructor would be exited.

For example, we have a method called `checkForJacket()` that takes in an array of `String`s. If any of the elements are equivalent to the `String` value `"jacket"`, the method will return `true`:

```
public static boolean checkForJacket(String[] lst) {  for (int i = 0; i < lst.length; i++) {    System.out.println(lst[i]);    if (lst[i] == "jacket") {      return true;    }  }  return false;} public static void main(String[] args) {  String[] suitcase = {"shirt", "jacket", "pants", "socks"};     System.out.println(checkForJacket(suitcase));}
```

As soon as an element equals `"jacket"`, `return true;` is executed. This causes the loop to stop and the [compiler](https://www.codecademy.com/resources/docs/java/compiler) to exit `checkForJacket()`. Running this code would output the following:

```
shirtjackettrue
```




### For-Each Loops

Sometimes we need access to the elements’ indices or we only want to iterate through a portion of a list. If that’s the case, a regular `for` loop or `while` loop is a great choice.

For example, we can use a `for` loop to print out each element in an array called `inventoryItems`:

```
for (int inventoryItem = 0; inventoryItem < inventoryItems.length; inventoryItem++) {  // Print element at current index  System.out.println(inventoryItems[inventoryItem]);}
```

But sometimes we couldn’t care less about the indices; we only care about the element itself.

At times like this, for-each [loops](https://www.codecademy.com/resources/docs/java/loops) come in handy.

_For-each loops_, which are also referred to as _enhanced loops_, allow us to directly loop through each item in a list of items (like an array or [`ArrayList`](https://www.codecademy.com/resources/docs/java/array-list)) and perform some action with each item.

If we want to use a for-each loop to rewrite our program above, the syntax looks like this:

```
for (String inventoryItem : inventoryItems) {  // Print element value  System.out.println(inventoryItem);}
```

Our enhanced loop contains two items: an enhanced `for` loop variable (`inventoryItem`) and a list to traverse through (`inventoryItems`).

We can read the `:` as “in” like this: for each `inventoryItem` (which should be a `String`) in `inventoryItems`, print `inventoryItem`.

If we try to assign a new value to the enhanced `for` loop variable, the value stored in the array or `ArrayList` will not change. This is because, for every iteration in the enhanced loop, the loop variable is assigned a copy of the list element.

**Note:** We can name the enhanced `for` loop variable whatever we want; using the singular of a plural is just a convention. We may also encounter conventions like `String word : sentence`.




### Removing Elements During Traversal

If we want to remove elements from an [`ArrayList`](https://www.codecademy.com/resources/docs/java/array-list) while traversing through one, we can easily run into an error if we aren’t careful.

When an element is removed from an `ArrayList`, all the items that appear after the removed element will have their index value shift by negative one — it’s like all elements shifted to the left! We’ll have to be very careful with how we use our counter variable to avoid skipping elements.

#### Removing An Element Using `while`

When using a `while` loop and removing elements from an `ArrayList`, we should **not** increment the `while` loop’s counter whenever we remove an element. We don’t need to increase the counter because all of the other elements have now shifted to the left.

For example, if we removed the element at index `3`, then the element that was at index `4` will be moved to index `3`. If we increase our counter to `4`, we’ll skip that element!

Take a look at this block of code that will remove all odd numbers from an `ArrayList`. Think about what the value of `i` is, when we’re increasing the value of `i`, and when `i < lst.size()` becomes `False`.

```
int i = 0; // initialize counterwhile (i < lst.size()) {  // if value is odd, remove value  if (lst.get(i) % 2 != 0){    lst.remove(i);  } else {    // if value is even, increment counter    i++;  }}
```

#### Removing An Element Using `for`

We can use a similar strategy when removing elements using a `for` loop. When using a `while` loop, we decided to not increase our loop control variable whenever we removed an element. This ensured that we would not skip an element when all of the other elements shifted to the left.

When using a `for` loop, we, unfortunately, _must_ increase our loop control variable — the loop control variable will always change when we reach the end of the loop (and it will usually change by `1` because we often use something like `i++`.) Since we can’t avoid increasing our loop control variable, we can take matters into our own hands and decrease the loop control variable whenever we remove an item.

For example:

```
for (int i = 0; i < lst.size(); i++) {  if (lst.get(i) == "value to remove"){    // remove value from ArrayList    lst.remove(lst.get(i));    // Decrease loop control variable by 1    i--;      }}
```

Now whenever we remove an item, we’ll decrease `i` by `1`. Then when we reach the end of the loop, `i` will increase by `1`. It will be like `i` never changed!

**Note:** Avoid manipulating the size of an `ArrayList` when using an enhanced `for` loop. Actions like adding or removing elements from an `ArrayList` when using a `for each` loop can cause a [`ConcurrentModificationException`](https://www.codecademy.com/resources/docs/java/errors/concurrentmodificationexception) error.




### Review

Nice work! Let’s iterate over what you’ve just learned about loops:

- `while` loops: These are useful to repeat a code block an unknown number of times until some condition is met. For example:

```
int wishes = 0;while (wishes < 3) {  // code that will run  wishes++;}
```

- `for` loops: These are ideal for when you are incrementing or decrementing with a counter variable. For example:

```
for (int i = 0; i < 5; i++) {  // code that will run}
```

- For-each loops: These make it simple to do something with each item in a list. For example:

```
for (String inventoryItem : inventoryItems) {  // do something with each inventoryItem}
```


### Traversing 2D Arrays: Row-Major Order

Row-major order for 2D [arrays](https://www.codecademy.com/resources/docs/java/arrays) refers to a traversal path which moves horizontally through each row starting at the first row and ending with the last.

Although we have already looked at how 2D array objects are stored in Java, this ordering system conceptualizes the 2D array into a rectangular matrix and starts the traversal at the top left element and ends at the bottom right element.

Here is a diagram which shows the path through the 2D array:

![Traversing across each row](https://static-assets.codecademy.com/Paths/ap-computer-science/TwoDArrays/row_major.png)

This path is created by the way we set up our nested [loops](https://www.codecademy.com/resources/docs/java/loops). In the previous exercise, we looked at how we can traverse the 2D array by having nested loops in a variety of formats, but if we want to control the indices, we typically use standard **for** loops.

Let’s take a closer look at the structure of the nested **for** loops when traversing a 2D array:

Given this 2D array of [strings](https://www.codecademy.com/resources/docs/java/strings) describing the element positions:

```
String[][] matrix = {{"[0][0]", "[0][1]", "[0][2]"},                      {"[1][0]", "[1][1]", "[1][2]"},                     {"[2][0]", "[2][1]", "[2][2]"},                     {"[3][0]", "[3][1]", "[3][2]"}};
```

Lets keep track of the total number of iterations as we traverse the 2D array:

```
int stepCount = 0;        for(int a = 0; a < matrix.length; a++) {    for(int b = 0; b < matrix[a].length; b++) {        System.out.print("Step: " + stepCount);        System.out.print(", Element: " + matrix[a][b]);        System.out.println();        stepCount++;    }}
```

Here is the [output](https://www.codecademy.com/resources/docs/java/output) of the above code:

```
Step: 0, Element: [0][0]Step: 1, Element: [0][1]Step: 2, Element: [0][2]Step: 3, Element: [1][0]Step: 4, Element: [1][1]Step: 5, Element: [1][2]Step: 6, Element: [2][0]Step: 7, Element: [2][1]Step: 8, Element: [2][2]Step: 9, Element: [3][0]Step: 10, Element: [3][1]Step: 11, Element: [3][2]        
```

The step value increases with every iteration within the inner **for** loop. Because of this, we can see the order in which each element is accessed. If we follow the step value in the output shows us that the elements are accessed in the same order as the row-major diagram above. Now why is that?

This is because in our **for** loop, we are using the number of rows as the termination condition within the outer **for** loop header `a < matrix.length;` Additionally, we are using the number of columns `b < matrix[a].length` as the termination condition for our inner loop. Logically we are saying: “For every row in our matrix, iterate through every single column before moving to the next row”. This is why our above example is traversing the 2D array using row-major order.

Here is a diagram showing which loop accesses which part of the 2D array for row-major order:

![Starting at the first row, looping through each column in that row. When the end of the row is reached, we move on to the next row](https://static-assets.codecademy.com/Paths/ap-computer-science/TwoDArrays/row_major_loop.png)

**Why Use Row-Major Order?**

Row-major order is important when we need to process data in our 2D array by row. You can be provided data in a variety of formats and you may need to perform calculations of rows of data at a time instead of individual elements. Let’s take one of our previous checkpoint exercises as an example. You were asked to calculate the sum of the entire 2D array of integers by traversing and accessing each element. Now, if we wanted to calculate the sum of each row, or take the average of each row, we can use row-major order to access the data in the order that we need. Let’s look at an example!

Given a 6X3 2D array of doubles:

```
double[][] data = {{0.51,0.99,0.12},                   {0.28,0.99,0.89},                   {0.05,0.94,0.05},                   {0.32,0.22,0.61},                   {1.00,0.95,0.09},                   {0.67,0.22,0.17}};
```

Calculate the sum of each row using row-major order:

```
double rowSum = 0.0;for(int o = 0; o < data.length; o++) {    rowSum = 0.0;    for(int i = 0; i < data[o].length; i++) {        rowSum += data[o][i];    }    System.out.println("Row: " + o +", Sum: " + rowSum);}
```

The output of the above code is:

```
Row: 0, Sum: 1.62Row: 1, Sum: 2.16Row: 2, Sum: 1.04Row: 3, Sum: 1.15Row: 4, Sum: 2.04Row: 5, Sum: 1.06
```

An interesting thing to note is that, due to the way 2D arrays are structured in Java, enhanced **for** loops are always in row-major order. This is because an enhanced **for** loop iterates through the elements of the outer array which causes the terminating condition to be the length of the 2D array which is the number of rows.






### Traversing 2D Arrays: Column-Major Order

Column-major order for 2D arrays refers to a traversal path which moves vertically down each column starting at the first column and ending with the last.

This ordering system also conceptualizes the 2D array into a rectangular matrix and starts the traversal at the top left element and ends at the bottom right element. Column-major order has the same starting and finishing point as row-major order, but it’s traversal is completely different

Here is a diagram which shows the path through the 2D array:

![Showing column-major ordering - walking down one column at a time](https://static-assets.codecademy.com/Paths/ap-computer-science/TwoDArrays/column_major.png)

In order to perform column-major traversal, we need to set up our nested loops in a different way. We need to change the outer loop from depending on the number of rows, to depending on the number of columns. Likewise we need the inner loop to depend on the number of rows in its termination condition.

Let’s look at our example 2D array from the last exercise and see what needs to be changed.

Given this 2D array of strings describing the element positions:

```
String[][] matrix = {{"[0][0]", "[0][1]", "[0][2]"},                      {"[1][0]", "[1][1]", "[1][2]"},                     {"[2][0]", "[2][1]", "[2][2]"},                     {"[3][0]", "[3][1]", "[3][2]"}};
```

Let’s keep track of the total number of iterations as we traverse the 2D array. We also need to change the termination condition (middle section) within the outer and inner **for** loop.

```
int stepCount = 0;                for(int a = 0; a < matrix[0].length; a++) {    for(int b = 0; b < matrix.length; b++) {        System.out.print("Step: " + stepCount);        System.out.print(", Element: " + matrix[b][a]);        System.out.println();        stepCount++;    }}   
```

Here is the output of the above code:

```
Step: 0, Element: [0][0]Step: 1, Element: [1][0]Step: 2, Element: [2][0]Step: 3, Element: [3][0]Step: 4, Element: [0][1]Step: 5, Element: [1][1]Step: 6, Element: [2][1]Step: 7, Element: [3][1]Step: 8, Element: [0][2]Step: 9, Element: [1][2]Step: 10, Element: [2][2]Step: 11, Element: [3][2]
```

As you can see in the code above, the way we accessed the elements from our 2D array of strings called `matrix` is different from the way we accessed them when using row-major order. Let’s remember that the way we get the number of columns is by using `matrix[0].length` and the way we get the number of rows is by using `matrix.length`. Because of these changes to our **for** loops, our iterator `a` now iterates through every column while our iterator `b` iterates through every row. Since our iterators now represent the opposite values, whenever we access an element from our 2D array, we need to keep in mind what indices we are passing to our accessor. Remember the format we use for accessing the elements `matrix[row][column]`? Since `a` now iterates through our column indices, we place it in the right set of brackets, and the `b` is now placed in the left set of brackets.

Here is a diagram showing which loop accesses which part of the 2D array for column-major order:

![The outer loop controls the column while the inner loop controls the row in that column.](https://static-assets.codecademy.com/Paths/ap-computer-science/TwoDArrays/column_major_loops.png)

**Why Use Column-Major Order?**

Column major order is important because there are a lot of cases when you need to process data vertically. Let’s say that we have a chart of information which includes temperature data about each day. The top of each column is labeled with a day, and each row represents an hour. In order to find the average temperature per day, we would need to traverse the data vertically since each column represents a day. As mentioned in the last exercise, data can be provided in many different formats and shapes and you will need to know how to traverse it accordingly.

Let’s look at our sum example from the last exercise, but now using column-major order.

Given a 6X3 2D array of doubles:

```
double[][] data = {{0.51,0.99,0.12},                   {0.28,0.99,0.89},                   {0.05,0.94,0.05},                   {0.32,0.22,0.61},                   {1.00,0.95,0.09},                   {0.67,0.22,0.17}};
```

Calculate the sum of each column using column-major order:

```
double colSum = 0.0;for(int o = 0; o < data[0].length; o++) {    colSum = 0.0;    for(int i = 0; i < data.length; i++) {        colSum += data[i][o];    }    System.out.println("Column: " + o +", Sum: " + colSum);}
```

The output of the above code is:

```
Column: 0, Sum: 2.83Column: 1, Sum: 4.31Column: 2, Sum: 1.93
```

Let’s try an example!

We will be using the same runner data from the last exercise, but this time we are going to take the average times per lap rather than per runner. This requires that we use column-major traversal.




### Combining Traversal and Conditional Logic

When working with 2D [arrays](https://www.codecademy.com/resources/docs/java/arrays), it is important to be able to combine traversal logic with conditional logic in order to effectively navigate and process the data. Here are a few ways in how conditional logic can affect 2D array traversal:

- Skipping or selecting certain rows and columns
- Modifying elements only if they meet certain conditions
- Complex calculations using the 2D array data
- Formatting the 2D array
- Avoiding exceptions / smart processing

Let’s go over a few examples which use these ideas:

First, let’s think about a situation where you have some string data inside a 2D array. We have an application which allows users to input events on a [calendar](https://www.codecademy.com/resources/docs/java/calendar). This is represented by a 5x7 2D array of [strings](https://www.codecademy.com/resources/docs/java/strings). Due to the fact that the number of days in each month is slightly different and that there are less than 35 days in a month, we know that some of our elements are going to be empty. We want our application to do a few things:

- Detect which days of which weeks have something planned and alert us about the event.
- Count the number of events for each week
- Count the number of events for each day

Here is a visualization of what our calendar data looks like after a user has entered in some event information:

![A calendar](https://static-assets.codecademy.com/Paths/ap-computer-science/TwoDArrays/calendar.png)

Here’s what our calendar data looks like in our application

```
String[][] calendar = {{"volunteer", "delivery", null, null, "doctor", null, "soccer"}, {null, "exam 1", null, "mechanic", null, null, "soccer"}, {"volunteer", "off work", null, "birthday", null, "concert", null}, {null, "exam 2", null, null, "doctor", null, "soccer"}, {"visit family", null, null, null, null, null, null}};
```

Let’s look at some code which accomplishes the requirements above. Carefully look through each line of code and read all of the [comments](https://www.codecademy.com/resources/docs/java/comments).

There are a few things to note:

- Row-major or column-major order can be used to access the individual events
- Row-major order must be used to count the number of events per week since each row represents a week

Let’s take care of the first 2 requirements in one set of nested row-major loops

```
for(int i = 0; i < calendar.length; i++) {    numberOfEventsPerWeek = 0;    for(int j = 0; j < calendar[i].length; j++) {        // We need conditional logic to ensure that we do not count the empty days        String event = calendar[i][j];        if(event!=null && !event.equals("")) {            // If the day does not have a null value and an empty string for an event, then we print it and count it            System.out.println("Week: " + (i+1) + ", Day: " + (j+1) + ", Event: " + event);            numberOfEventsPerWeek++;        }    }    System.out.println("Total number of events for week "+ (i+1) +": " + numberOfEventsPerWeek + "\n");}
```

The above code produces this output:

```
Week: 1, Day: 1, Event: volunteerWeek: 1, Day: 2, Event: deliveryWeek: 1, Day: 5, Event: doctorWeek: 1, Day: 7, Event: soccerTotal number of events for week 1: 4Week: 2, Day: 2, Event: exam 1Week: 2, Day: 4, Event: mechanicWeek: 2, Day: 7, Event: soccerTotal number of events for week 2: 3Week: 3, Day: 1, Event: volunteerWeek: 3, Day: 2, Event: off workWeek: 3, Day: 4, Event: birthdayWeek: 3, Day: 6, Event: concertTotal number of events for week 3: 4Week: 4, Day: 2, Event: exam 2Week: 4, Day: 5, Event: doctorWeek: 4, Day: 7, Event: soccerTotal number of events for week 4: 3Week: 5, Day: 1, Event: visit familyTotal number of events for week 5: 1
```

Now let’s complete the third requirement. Since we need to count all of the events for each of the weekdays, we will need to traverse the calendar vertically.

```
int numberOfEventsPerWeekday = 0;// We will use this array of day strings for our output later on so we don't have (day: 1)String[] days = {"Sundays", "Mondays", "Tuesdays", "Wednesdays", "Thursdays", "Fridays", "Saturdays"};for(int i = 0; i < calendar[0].length; i++) {    numberOfEventsPerWeekday = 0;    for(int j = 0; j < calendar.length; j++) {        // Don't forget to flip the iterators in the accessor since we are flipping the direction we are navigating.        // Remember, i now controls columns and j now controls rows        String event = calendar[j][i];        if(event!=null && !event.equals("")) {            // Make sure we have an event for the day before counting it            numberOfEventsPerWeekday++;        }    }    // Use the days string array from earlier to convert the day index to a real weekday string    System.out.println("Number of events on " + days[i] + ": " + numberOfEventsPerWeekday);}
```

The [output](https://www.codecademy.com/resources/docs/java/output) is:

```
Number of events on Sundays: 3Number of events on Mondays: 4Number of events on Tuesdays: 0Number of events on Wednesdays: 2Number of events on Thursdays: 2Number of events on Fridays: 1Number of events on Saturdays: 3
```

This example uses many of the concepts we have learned before. We use row-major order, column-major order, as well as including conditional logic to ensure that we have data for the elements we are accessing.

Additionally, we can use conditional logic to skip portions of the 2D array. For example, let’s say we wanted to print the events for weekdays only and skip the weekends.

We could use a conditional statement such as `if(j!=0 && j!=6)` in order to skip Sunday (`0`) and Saturday (`6`).

These modifications to our 2D array traversal are very common when processing data in applications. We need to know which cells to look at (skipping column titles for example), which cells to ignore (empty data, invalid data, outliers, etc.), and which cells to convert (converting string input from a file to numbers).

Let’s try an example!

We are making a simple grayscale image editor program and we want to apply some modifications to the image. We have a 4x8 pixel image that is stored as a 2D array of integers. The integer value represents the brightness of the pixel, where the acceptable values are between `0` and `255`, inclusive.






### 2D Array Review

Let’s review the concepts we have learned throughout this lesson.

Arrays are objects in Java, we can have [arrays](https://www.codecademy.com/resources/docs/java/arrays) of objects, therefore we can also have arrays of arrays. This is the way 2D arrays are structured in Java.

We can declare and initialize 2D arrays in a few different ways depending on the situation:

```
// Declaring without initializingint[][] intTwoD;// Initializing an empty 2D array which has already been declaredintTwoD = new int[5][5];// Declaring and initializing an empty 2D array at onceString[][] stringData = new String[3][6];// Declaring and initializing a 2D array using initializer listsdouble[][] doubleValues = {{1.5, 2.6, 3.7}, {7.5, 6.4, 5.3}, {9.8,  8.7, 7.6}, {3.6, 5.7, 7.8}};// Initializing a 2D array using initializer lists after it has already been declared, or already contains data;char[][] letters = new char[100][250];letters = new char[][]{{'a', 'b', 'c'}, {'d', 'e', 'f'}};
```

We retrieve elements in a 2D array by providing a row and column index `char c = letters[0][1];`

- We can also think of them as the index of the outer array and the index of the subarray
- We can modify elements the same way `letters[1][2] = 'z';`

We traverse 2D arrays using nested [loops](https://www.codecademy.com/resources/docs/java/loops).

- We can use loops of any type, but we typically use nested **for** loops to keep track of the indices
- Row-major order traverses through each row moving horizontally to the right through each row
- Column-major order traverses through each column moving vertically down through each column
- Row-major order and column-major order start and end on the same elements, but the paths are different.
- In order to convert row-major to column-major, we need to make the outer loop terminating condition depend on the number of columns, make the inner loop terminating condition depend on the number of rows, and flip the [variables](https://www.codecademy.com/resources/docs/java/variables) in our accessor within the inner loop to ensure that we don’t try to access outside of the 2D array since we flipped the direction of traversal.

Here are examples of row-major and column-major order:

```
// Row-major orderfor(int o = 0; o < letters.length; o++) {    for(int i = 0; i < letters[o].length; i++) {        char c = letters[o][i];    }}// Column-major orderfor(int o = 0; o < letters[0].length; o++) {    for(int i = 0; i < letters.length; i++) {        char c = letters[i][o];    }}
```

Conditional logic in our 2D array traversal allows us to use the data in a meaningful way. We can control which rows and columns we look at, ensure that the data we are looking at is what we want, perform calculations on specific elements, avoid throwing exceptions, and more.

Here is an example of traversal with conditional logic.

Given this 2D array of Strings:

```
String[][] words = {{"championship", "QUANTITY", "month"},{"EMPLOYEE", "queen", "understanding"},{"method", "writer", "MOVIE"}};
```

We are going to flip the capitalization of the words:

```
System.out.println("Before...");System.out.println(Arrays.deepToString(words).replace("],", "],\n") + "\n");for(int i=0; i<words.length; i++) {    for(int j = 0; j<words[i].length; j++) {        if(words[i][j]!=null) {            // Check the capitalization            boolean allCaps = true;            for(char c : words[i][j].toCharArray())                 if(!Character.isUpperCase(c))                     allCaps = false;                            // Flip the capitalization            if(allCaps)                words[i][j] = words[i][j].toLowerCase();            else                words[i][j] = words[i][j].toUpperCase();        }    }}System.out.println("After...");System.out.println(Arrays.deepToString(words).replace("],", "],\n") + "\n");
```

Here is the [output](https://www.codecademy.com/resources/docs/java/output) of the above code:

```
Before...[[championship, QUANTITY, month], [EMPLOYEE, queen, understanding], [method, writer, MOVIE]]After...[[CHAMPIONSHIP, quantity, MONTH], [employee, QUEEN, UNDERSTANDING], [METHOD, WRITER, movie]]
```

Time to work some review problems!

After learning about 2D arrays, you have decided to become a CS professor and you are now teaching your class about 2D arrays. You are making an application which will keep track of their exam grades and show you statistics about their performance. You will be using 2D arrays to keep track of their exam grades












