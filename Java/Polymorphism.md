
### Introducing Polymorphism

In Java, if `Orange` is a `Fruit` through [inheritance](https://www.codecademy.com/resources/docs/java/inheritance), you can then use `Orange` in the same contexts as `Fruit` like this:

```
String makeJuice(Fruit fruit) {  return "Apple juice and " + fruit.squeeze();}// inside main()Orange orange = new Orange();System.out.println(juicer.makeJuice(orange));
```

Wait, how does that work?

This is because Java incorporates the object-oriented programming principle of _polymorphism_. Polymorphism, which derives from Greek meaning “many forms”, allows a child class to share the information and behavior of its parent class while also incorporating its own functionality.

The main advantages of polymorphic programming:

- Simplifying syntax
- Reducing cognitive overload for developers

These benefits are particularly helpful when we want to develop our own Java packages for other developers to import and use.

For example, the built-in operator `+` can be used for both `double`s and `int`s. To the computer, the `+` means something like `addDouble()` for one and `addInt()` for the other, but the creators of Java (and of other languages) didn’t want to burden us as developers with recalling each individual method.

Note that the reverse situation is not true; you cannot use a generic parent class instance where a child class instance is required. So an `Orange` can be used as a `Fruit`, but a `Fruit` cannot be used as an `Orange`.



### Method Overriding

One common use of polymorphism with Java [classes](https://www.codecademy.com/resources/docs/java/classes) is something we mentioned earlier — _overriding_ parent class [methods](https://www.codecademy.com/resources/docs/java/methods) in a child class. Like the `+` operator, we can give a single method slightly different meanings for different classes. This is useful when we want our child class method to have the same name as a parent class method but behave a bit differently in some way.

Let’s say we have a `BankAccount` class that allows us to print the current balance. We want to build a `CheckingAccount` class that inherits the functionality of a `BankAccount` but with a modified `printBalance()` method. We can do the following:

```
class BankAccount {  protected double balance;  public BankAccount(double balanceIn){    balance = balanceIn;  }  public void printBalance() {    System.out.println("Your account balance is $" + balance);  }}class CheckingAccount extends BankAccount {    public CheckingAccount(double balance) {    super(balance);  }  @Override  public void printBalance() {    System.out.println("Your checking account balance is $" + balance);  }}
```

Notice that in order to properly override `printBalance()`, in `CheckingAccount` the method has the following in common with the corresponding method in `BankAccount`:

- Method name
- Return type
- Number and type of parameters

You may have also noticed the `@Override` keyword above `printBalance()` in `CheckingAccount`. This annotation informs the [compiler](https://www.codecademy.com/resources/docs/java/compiler) that we want to override a method in the parent class. If the method doesn’t exist in the parent class, we’ll get a helpful error when we compile the program.

**Keep Reading: AP Computer Science A Students**

In a previous exercise, we learned that the `super` keyword can be used to call the constructor of a superclass. That’s not the only use of `super`; we can also use this keyword to call the methods of a parent class. While we now have the ability to override methods from a superclass, we may find ourselves in a unique situation where we want to use the superclass method instead of the subclass’ overridden method.

If that’s the case, we can call the parent class method by prepending `super` followed by the dot operator (`.`) to the method call. Note that this only works if we pass in the proper method parameters. Let’s see this in action by adding a `checkBalances()` method to `CheckingAccount` that calls both versions of `printBalance()`:

```
class CheckingAccount extends BankAccount {  public CheckingAccount(double balance) {    super(balance);  }  @Override  public void printBalance() {    System.out.println("Your checking account balance is $" + balance);  }  public void checkBalances() {    // calls method from CheckingAccount    printBalance();    // calls method from BankAccount    super.printBalance();  }  public static void main(String[] args) {    CheckingAccount myCheckings = new CheckingAccount(5000);    myCheckings.checkBalances();  }}
```

This program will output:

```
Your checking account balance is $5000Your account balance is $5000
```





### Using a Child Class as its Parent Class

An important facet of polymorphism is the ability to use a child class object where an object of its parent class is expected.

One way to do this explicitly is to instantiate a child class object as a member of the parent class. We can instantiate a `CheckingAccount` object as a `BankAccount` like this:

```
BankAccount kaylasAccount = new CheckingAccount(600.00);
```

We can use `kaylasAccount` as if it were an instance of `BankAccount`, in any situation where a `BankAccount` object would be expected. (This would be true even if `kaylasAccount` were instantiated as a `CheckingAccount`, but using the explicit child as parent syntax is most helpful when we want to declare objects in bulk.)

It is important to note here that the [compiler](https://www.codecademy.com/resources/docs/java/compiler) just considers `kaylasAccount` to be any old `BankAccount`. But because method overriding is handled at runtime, if we call `printBalance()`, we’ll see something `CheckingAccount` specific:

```
Your checking account balance is $600.00
```

This is because at runtime, `kaylasAccount` is recognized as the `CheckingAccount` it is. So, what if `CheckingAccount` has a method `transferToSavings()` that `BankAccount` does not have? Can `kaylasAccount` still use that method?

Well, no. The compiler believes that `kaylasAccount` is just a `BankAccount` that doesn’t have some fancy child class `transferToSavings()` method, so it would throw an error.


### Child Classes in Arrays and ArrayLists

Usually, when we create an array or an [`ArrayList`](https://www.codecademy.com/resources/docs/java/array-list), the list items all need to be the same type. But polymorphism puts a new spin on what is considered the same type…

In fact, we can put instances of different [classes](https://www.codecademy.com/resources/docs/java/classes) that share a parent class together in an array or `ArrayList`! For example, let’s say we have a `Monster` parent class with a few child classes: `Vampire`, `Werewolf`, and `Zombie`. We can set up an array with instances of each:

```
Monster dracula, wolfman, zombie1;dracula = new Vampire();wolfman = new Werewolf();zombie1 = new Zombie();Monster[] monsters = {dracula, wolfman, zombie1};
```

We can even iterate through the list of items — regardless of subclass — and perform the same action with each item:

```
for (Monster monster : monsters) {  monster.attack();}
```

In the code above, we were able to call `attack()` on each monster in `monsters` despite the fact that, in the for-each loop, `monster` is declared as the parent class type `Monster`.



### Child Classes in Method Parameters

When we call a method that contains parameters, the arguments we place in our method call must match the parameter type. Similar to the previous exercise, polymorphism gives us a little more flexibility with the arguments we can use.

If we use a superclass reference as a method parameter, we can call the method using subclass reference arguments!

For example, imagine the class `ScaryStory`, whose constructor takes in a reference to the `Monster` class:

```
class ScaryStory {  Monster monster;  String setting;  public ScaryStory(Monster antagonist, String place) {    monster = antagonist;    setting = place;  }  public void tellStory(){    System.out.println("Once upon a time, " + monster.name + " was at " + setting + " looking to scare some mortals.");  }  public static void main(String[] args) {    Monster dracula;    dracula = new Vampire("Dracula");    ScaryStory countDracula = new ScaryStory(dracula, "Dracula Castle");    countDracula.tellStory();  }}
```

In the `main()` method, we used a reference of the class `Vampire` as our argument even though the constructor requested an object of class `Monster`. This is allowed because `Vampire` is a subclass of the `Monster` class.



### Review of Inheritance and Polymorphism

Excellent work! You’ve learned quite a bundle about [inheritance](https://www.codecademy.com/resources/docs/java/inheritance) and polymorphism in Java:

- A Java class can inherit fields and [methods](https://www.codecademy.com/resources/docs/java/methods) from another class.
- Each Java class requires its own file, but only one class in a Java package needs a `main()` method.
- Child [classes](https://www.codecademy.com/resources/docs/java/classes) inherit the parent constructor by default, but it’s possible to modify the constructor using `super()` or override it completely.
- You can use `protected` and `final` to control child class access to parent class members.
- Java’s OOP principle of polymorphism means you can use a child class object like a member of its parent class, but also give it its own traits.
- You can override parent class methods in the child class, ideally using the `@Override` keyword.
- It’s possible to use objects of different classes that share a parent class together in an array or [`ArrayList`](https://www.codecademy.com/resources/docs/java/array-list).







