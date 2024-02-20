### Introduction

When we work with [arrays](https://www.codecademy.com/resources/docs/java/arrays) in Java, we’ve been limited by the fact that once an array is created, it has a fixed size. We can’t add or remove elements.

But what if we needed to add to the book lists, newsfeeds, and other structures we were using arrays to represent?

To create mutable and dynamic lists, we can use Java’s [`ArrayList`](https://www.codecademy.com/resources/docs/java/array-list?page_ref=catalog) class. `ArrayList` allows us to:

- Store object references as elements
- Store elements of the same type (just like arrays)
- Access elements by index (just like arrays)
- Add elements
- Remove elements

Remember how we had to import `java.util.Arrays` in order to use additional array methods? To use an `ArrayList` at all, we need to import them from Java’s `util` package as well:

```
import java.util.ArrayList;
```

Let’s learn how to make use of this powerful object…



### Creating ArrayLists

To create an `ArrayList`, we need to declare the type of objects it will hold, just as we do with arrays:

```
ArrayList<String> babyNames;
```

We use angle brackets `<` and `>` to declare the type of the `ArrayList`. These symbols are used for _generics_. Generics are a Java construct that allows us to define classes and objects as parameters of an `ArrayList`. For this reason, we can’t use primitive types in an `ArrayList`:

```
// This code won't compile:ArrayList<int> ages;// This code will compile:ArrayList<Integer> ages;
```

The `<Integer>` generic has to be used in an `ArrayList` instead. You can also use `<Double>` and `<Character>` for types you would normally declare as `double`s or `char`s.

We can initialize to an empty `ArrayList` using the `new` keyword:

```
// Declaring:ArrayList<Integer> ages;// Initializing:ages = new ArrayList<Integer>();// Declaring and initializing in one line:ArrayList<String> babyNames = new ArrayList<String>();
```


### Adding an Item

Now we have an empty `ArrayList`, but how do we get it to store values?

`ArrayList` comes with an [`add()`](https://www.codecademy.com/resources/docs/java/array-list/add?page_ref=catalog) method which inserts an element into the structure. There are two ways we can use `add()`.

If we want to add an element to the end of the `ArrayList`, we’ll call `add()` using only one argument that represents the value we are inserting. In this example, we’ll add objects from the `Car` class to an `ArrayList` called `carShow`:

```
ArrayList<Car> carShow = new ArrayList<Car>();carShow.add(ferrari);// carShow now holds [ferrari]carShow.add(thunderbird);// carShow now holds [ferrari, thunderbird]carShow.add(volkswagen);// carShow now holds [ferrari, thunderbird, volkswagen]
```

If we want to add an element at a specific index of our `ArrayList`, we’ll need two arguments in our method call: the first argument will define the index of the new element while the second argument defines the value of the new element:

```
// Insert object corvette at index 1carShow.add(1, corvette);// carShow now holds [ferrari, corvette, thunderbird, volkswagen]// Insert object porsche at index 2carShow.add(2, porsche);// carShow now holds [ferrari, corvette, porsche, thunderbird, volkswagen]
```

By inserting a value at a specified index, any elements that appear after this new element will have their index value shift over by 1.

Also, note that an error will occur if we try to insert a value at an index that does not exist.

**Keep Reading: AP Computer Science A Students**

When using `ArrayList` [methods](https://www.codecademy.com/resources/docs/java/methods) (like `add()`), the reference parameters and return type of a method must match the declared element type of the `ArrayList`. For example, we cannot add an `Integer` type value to an `ArrayList` of `String` elements.

We’ve discussed how to specify the element type of an `ArrayList`; however, it is possible to create an `ArrayList` that holds values of different types.

In the following snippet, `assortment` is an `ArrayList` that can store different values because we do not specify its type during initialization.

```
ArrayList assortment = new ArrayList<>();assortment.add("Hello"); // Stringassortment.add(12); // Integerassortment.add(ferrari); // reference to Car// assortment holds ["Hello", 12, ferrari]
```

In this case, the items stored in this `ArrayList` will be considered `Objects`. As a result, they won’t have access to some of their methods without doing some fancy casting. Although this type of `ArrayList` is allowed, using an `ArrayList` that specifies its type is preferred.



### ArrayList Size

Let’s say we have an [`ArrayList`](https://www.codecademy.com/resources/docs/java/array-list) that stores items in a user’s online shopping cart. As the user navigates through the site and adds items, their cart grows bigger and bigger.

If we wanted to display the number of items in the cart, we could find the size of it using the `size()` method:

```
ArrayList<String> shoppingCart = new ArrayList<String>();shoppingCart.add("Trench Coat");System.out.println(shoppingCart.size());// 1 is printedshoppingCart.add("Tweed Houndstooth Hat");System.out.println(shoppingCart.size());// 2 is printedshoppingCart.add("Magnifying Glass");System.out.println(shoppingCart.size());// 3 is printed
```

In dynamic objects like `ArrayList`s, it’s important to know how to access the amount of objects we have stored.


### Accessing an Index

With [arrays](https://www.codecademy.com/resources/docs/java/arrays), we can use bracket notation to access a value at a particular index:

```
double[] ratings = {3.2, 2.5, 1.7};System.out.println(ratings[1]);
```

This code prints `2.5`, the value at index `1` of the array.

For [`ArrayList`](https://www.codecademy.com/resources/docs/java/array-list)s, bracket notation won’t work. Instead, we use the method `get()` to access an index:

```
ArrayList<String> shoppingCart = new ArrayList<String>();shoppingCart.add("Trench Coat");shoppingCart.add("Tweed Houndstooth Hat");shoppingCart.add("Magnifying Glass");System.out.println(shoppingCart.get(2));
```

This code prints `"Magnifying Glass"`, which is the value at index 2 of the `ArrayList`.


### Changing a Value

When we were using [arrays](https://www.codecademy.com/resources/docs/java/arrays), we could rewrite entries by using bracket notation to reassign values:

```
String[] shoppingCart = {"Trench Coat", "Tweed Houndstooth Hat", "Magnifying Glass"};shoppingCart[0] = "Tweed Cape";// shoppingCart now holds ["Tweed Cape", "Tweed Houndstooth Hat", "Magnifying Glass"]
```

[`ArrayList`](https://www.codecademy.com/resources/docs/java/array-list) has a slightly different way of doing this, using the `set()` method:

```
ArrayList<String> shoppingCart = new ArrayList<String>();shoppingCart.add("Trench Coat");shoppingCart.add("Tweed Houndstooth Hat");shoppingCart.add("Magnifying Glass");shoppingCart.set(0, "Tweed Cape");// shoppingCart now holds ["Tweed Cape", "Tweed Houndstooth Hat", "Magnifying Glass"]
```


### Removing an Item

What if we wanted to get rid of an entry altogether? For [arrays](https://www.codecademy.com/resources/docs/java/arrays), we would have to make a completely new array without the value.

Luckily, `ArrayList`s allow us to remove an item by specifying the index to [remove](https://www.codecademy.com/resources/docs/java/array-list/remove?page_ref=catalog):

```
ArrayList<String> shoppingCart = new ArrayList<String>();shoppingCart.add("Trench Coat");shoppingCart.add("Tweed Houndstooth Hat");shoppingCart.add("Magnifying Glass");shoppingCart.remove(1);// shoppingCart now holds ["Trench Coat", "Magnifying Glass"]
```

We can also remove an item by specifying the value to remove:

```
ArrayList<String> shoppingCart = new ArrayList<String>();shoppingCart.add("Trench Coat");shoppingCart.add("Tweed Houndstooth Hat");shoppingCart.add("Magnifying Glass");shoppingCart.remove("Trench Coat");// shoppingCart now holds ["Tweed Houndstooth Hat", "Magnifying Glass"]
```

**Note:** This command removes the FIRST instance of the value `"Trench Coat"`.


### Getting an Item's Index

What if we had a really large list and wanted to know the position of a certain element in it? For instance, what if we had an [`ArrayList`](https://www.codecademy.com/resources/docs/java/array-list) `detectives` with the names of fictional detectives in chronological order, and we wanted to know what position `"Fletcher"` was.

```
// detectives holds ["Holmes", "Poirot", "Marple", "Spade", "Fletcher", "Conan", "Ramotswe"];System.out.println(detectives.indexOf("Fletcher"));
```

This code would print `4`, since `"Fletcher"` is at index `4` of the `detectives` `ArrayList`.


### Review

Nice work! You now know the basics of [`ArrayList`](https://www.codecademy.com/resources/docs/java/array-list)s including:

- Creating an `ArrayList`.
- Adding a new `ArrayList` item using `add()`.
- Accessing the size of an `ArrayList` using `size()`.
- Finding an item by index using `get()`.
- Changing the value of an `ArrayList` item using `set()`.
- Removing an item with a specific value using `remove()`.
- Retrieving the index of an item with a specific value using `indexOf()`.

Now if only there were some way to move through an array or `ArrayList`, item by item…