# android-dev-java

## SDK
SDK is a collection of software and libs that devs use for Android development.

## Project Structure
* AndroidManifest.xml - Tells the Android build tools important info such as OS, Google Play
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
The super keyword is used to access the blueprint of the immediate parent class, its members, fields, methods and constructors.

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
