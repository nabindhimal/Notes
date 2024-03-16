

### Introducing Inheritance

When you hear the word “inheritance,” code may not be the first thing that springs to mind; you’re probably more likely to think of inheriting genetic traits, like eye color from your mother or a smile from your grandfather. But [inheritance](https://www.codecademy.com/resources/docs/java/inheritance?page_ref=catalog) is also an important feature of object-oriented programming in Java.

Suppose we are building a `Shape` class in Java. We might give it some points in 2D, a method for calculating the area, and another method for displaying the shape. But what happens if we want a class for a triangle that has some triangle-specific methods? Do we need to redefine all of the same [methods](https://www.codecademy.com/resources/docs/java/methods) that we created for `Shape`?

No! (Phew.) Lucky for us, a Java class can also _inherit_ traits from another class. Because a `Triangle` is a `Shape`, we can define `Triangle` so that it inherits fields and methods directly from `Shape`. A reference of type `Shape` can refer to an object of `Shape` or an object of `Triangle`. The object-oriented principle of inheritance saves us the headache of redefining the same class members all over again.

Our `Triangle` class will inherit all the traits of `Shape`, but `Triangle` can also contain its own unique methods and [variables](https://www.codecademy.com/resources/docs/java/variables). For example, we could have an instance variable called `hypotenuse` and a method called `findHypotenuse()` that can only be accessed by `Triangle` class references. Objects of `Triangle` can call any method contained in `Triangle` or `Shape`. This gives us a bunch of possibilities!

There are several terms you’ll encounter frequently:

- _Parent class_, _superclass_, and _base class_ refer to the class that another class inherits from (like `Shape`).
- _Child class_, _subclass_, and _derived class_ refer to a class that inherits from another class (like `Triangle`).


### Inheritance in Practice

So how do we define a child class so that it inherits from a parent class? We use the keyword `extends` like this:

```
class Shape {  // Shape class members}class Triangle extends Shape {  // additional Triangle class members}
```

Now `Triangle` has inherited traits from `Shape`, meaning it copied over class members from `Shape`. When we use [inheritance](https://www.codecademy.com/resources/docs/java/inheritance) to extend a subclass from a superclass, we create an “is-a” relationship from the subclass to the superclass. For example, an object of `Triangle` _is a_ member of the `Shape` class; however, an object of `Shape` is not necessarily an object of `Triangle`.

Until now, we’ve only been working with one class and one file. However, most Java programs utilize multiple [classes](https://www.codecademy.com/resources/docs/java/classes), each of which requires its own file. Only one file needs a `main()` method — this is the file we will run.

Note: the various classes in our Java package — even though they are in different [files](https://www.codecademy.com/resources/docs/java/files) — will have access to each other, so we can instantiate one class inside of another.




### Inheriting the Constructor

Hang on, you might be thinking, if the child class inherits its parent’s fields and [methods](https://www.codecademy.com/resources/docs/java/methods), does it also inherit the constructor? Let’s take a look at how the `super()` constructor works!

Let’s say `Shape` has a `numSides` field that is set by passing an integer into the constructor. If we’re instantiating a `Triangle`, we would want that number to always be `3`, so we’d want to modify the constructor to automatically assign `numSides` with a value of `3`.

Can we do that?

As it happens, Java has a trick up its sleeve for just this occasion: using the `super()` method which acts like the parent constructor inside the child class constructor:

```
class Triangle extends Shape {  Triangle() {    super(3);  }  // additional Triangle class members}
```

By passing `3` to `super()`, we are making it possible to instantiate a `Triangle` without passing in a value for `numSides`.

Meanwhile, `super(3)` (behaving as `Shape(3)`) will shoulder the responsibility of setting `numSides` to `3` for our `Triangle` object. It’s like we called `Shape(3)`.

It is also possible to write a constructor without making a call to any `super()` constructor:

```
class Triangle extends Shape {  Triangle() {    this.numSides = 3;  }  // additional Triangle class methods}
```

In this situation, Java secretly calls the parent class’ no-argument constructor (`super()`). So in this specific example, the `Triangle()` constructor first calls the `Shape()` constructor. That `Shape()` takes care of whatever business it needs to take care of. And then after that is complete, we go in and set `this.numSides` to `3`.

If you’re writing a constructor of a child class, and don’t explicitly make a call to a constructor from a parent class using `super`, it’s important to remember that Java will automatically (and secretly) call `super()` as the first line of your child class constructor.



### Parent Class Aspect Modifiers

You may recall that Java class members use `private` and `public` access modifiers to determine whether they can be accessed from outside the class. So does a child class inherit its parent’s `private` members?

Well, no. But there is another access modifier we can use to keep a parent class member accessible to its child classes and to files in the package it’s contained in — and otherwise private: `protected`. ![public is visible everywhere; protected is visible in the class, the package, and child classes; a member with no modifier is visible in the class and package; private is visible only in the class itself](https://content.codecademy.com/courses/learn-java/revised-2019/access-modifiers-chart.png) Here’s what `protected` looks like in use:

```
class Shape {  protected double perimeter;}// any child class of Shape can access perimeter
```

In addition to access modifiers, there’s another way to establish how child classes can interact with inherited parent class members: using the `final` keyword. If we add `final` after a parent class method’s access modifier, we disallow any child classes from changing that method. This is helpful in limiting bugs that might occur from modifying a particular method.

Though it is not required, there is an established order when two or more field modifiers are used (eg. `public final`). To learn more about this read the [documentation](https://docs.oracle.com/javase/specs/jls/se11/html/jls-8.html#jls-8.3.1).






