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
