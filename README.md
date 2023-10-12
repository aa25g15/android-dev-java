# android-dev-java

## SDK
SDK is a collection of software and libs that devs use for Android development.

## Project Structure
* AndroidManifest.xml - Tells the Android build tools important info such as OS, Google Play
* MainActivity.java - Entry point of Java logic
* java folder - Contains java packages and source code of the app
* res (resources) - Contains sub-folders:
  * drawable - Contains different types of images used in development, add all images here
  * layout - As it suggests, has layout xml files
  * mipmap - Used for placing app/launcher icons, store all other assets in drawable folder
  * values
    * colors.xml - To store colors
    * strings.xml - To store strings which can be used throughout app, can be used for translation also, like it happens in i18n in React
  * themes - Styles and themes much like stylesheets in web dev, themes can be applied to entire app, activity or View hierarchy, styles are only for a single View
 
 ## Gradle
 It is a powerful build system to manage and automate the build process for Android apps, helps organize and compile code, manage dependencies, package the final APK or app bundles for distribution
 * There is a build.gradle file for app and each module
 * gradle-wrapper is a script that ensures the same version of Gradle is used across different development environments

## main Method
* It is the entry point of your java program, has specific syntax:
```java
public static void main(String[] args){
 // Do something
}
```

## Printing
```java
System.out.print("Hello World!");
```

## Vars
```java
int age = 25; // Do not forget the semi-colon!
```
<img width="591" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/5b2752c4-24dd-4ac1-aa6d-6725554b998c">

Just look at how to define variables online for these different data types.

## Type Casting
Process of converting one data type to another.
* Implicit
  * Happens automatically when conversion is safe and does not result in loss of data
  * Happens when a variable of smaller data type is assigned to larger
  * Eg - Converting int to double
* Explicit
  * Results in data loss so is done manually
  * Eg - Converting double to int
```java
int age = 25;
double age2 = age; // 25.0, implicit

double pi = 3.14;
int piInt = (int) pi; // 3

int val = 5;
char myChar = 'A';

char res = (char) (val + myChar); // 70
System.out.print(res); // F
```

## Method Overloading
It is a concept where the same method can be defined multiple times with different signature and depending on the args, the correct implementation of the method will be invoked.

## Classes and Objects
<img width="1048" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/02946868-b6fe-4df5-b6a4-0f4072aba631">

* Class is a blueprint for the object instance
* Object is an instance of a class

## Access Modifiers
* There are packages, which have one or more classes

### Private
Within class only.

### Public
Can be accessed by all classes within same package without importing but need to import in another package if you want to access.

### Protected
Can be accessed by classes within same package and also by sub-classes.

### Default - When nothing is mentioned
Also called package private, means can only be accessed by classes in same package.

## super Keyword
* The super keyword is used to access the blueprint of the immediate parent class, its members, fields, methods and constructors.
* Use extend keyword to create a child class from a particular class.

## Annotations or Decorators
In Java, annotations are used to provide metadata to the compiler, for example, @override is written on top of a method which in delcared in parent class but is overridden in the child class. But in this specific example, it is not mandatory to add override annotation. Also, you cannot override static and final methods and we should try to override abstract methods of the super class.

## Polymorphism
Objects of the different classes are treated as the objects of a common parent class.

Example:
* We create a class Vehicle, has method honk() which prints "Vehicle honks"
* We create a class Car which extends Vehicle, overrides method honk() which prints "Car honks"
* We create a class Truck which extends Vehicle, overrides method honk() which prints "Truck honks"

```java
Vehicle v1 = new Car("BMW");
Vehicle v2 = new Truck("Mercedes");

v1.honk(); // Car honks
v2.honk(); // Truck honks
```

Polymorphism allows us to write consistent code.

## Abstraction
* Used to hide details or complexity, like in an API.
* To create an abstract class in Java, use abstract keyword before class and before methods
* Abstract classes can have abstract and normal methods, both
* You cannot create an instance of an abstract class, only of its children classes

## Interfaces
* Interfaces is also used to enforce the concept of abstraction.
* Use implements keywords to implement a class with an interface
* The class which implements the interface must follow the rules declared in the interface such as methods definitions etc.
* One key advantage of using interfaces is that, in Java only mono-extend of classes is possible, you cannot extend multiple classes but you can implements multiple interfaces which can allow you to have multiple rule-sets when creating your class!

## Views and ViewGroups
* Views are like divs in web dev
* ViewGroups contain multiple Views, Layout is also a ViewGroup
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/ba895c70-15ba-41b5-acc9-6f7836242662)

## Android Studio
* Code, split and design are 3 working modes in Android Studio
* xml files are markup files which you can use to define the UI of the app
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/4a332ce2-47fc-42a7-864a-2f3224a1450a)

## sp and dp
* They both are units in Android Studio
* Scalable pixels (sp) serve the same function as density-independent pixels (dp), but for fonts. The default value of an sp is the same as the default value for a dp. The primary difference between an sp and a dp is that sp's preserve a user's font settings.

# TextView
* Can be used to add texts and style them
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/87bbb17c-0dfa-4d98-af03-d1057acaa6de)

# Initialising Views in Java Code
* Define id
 * Make sure its unqiue
 * Make sure you define it correctly
```xml
<TextView android:id="@+id/myTextView">
```
* Now in MainActivity.java
```java
TextView myTextView = findViewById(R.id.myTextView);
// Now you can perform runtime manipulations on this View in your Java code
```
