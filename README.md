# android-dev-java

## High Level Tips
* Always initialize variables in onCreate, you can declare them as class fields though
* You can use infer constraints button to directly add position constraints
* You can create drawable shapes using xml inside the drawables folder

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

## android:id
* This is the most critical attribute and must be defined on all elements
```xml
<TextView android:id="@+id/myTextView" />
```

## TextView
* Can be used to add texts and style them
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/87bbb17c-0dfa-4d98-af03-d1057acaa6de)

## Initialising Views in Java Code
* Define id
 * Make sure its unqiue
 * Make sure you define it correctly
```xml
<TextView android:id="@+id/myTextView" />
```
* Now in MainActivity.java
```java
TextView myTextView = findViewById(R.id.myTextView);
// Now you can perform runtime manipulations on this View in your Java code
```

## EditText
* When user input is needed such as inputs, search bars etc.
```xml
<EditText
 android:id="@+id/myTextView"
 android:hint="Please enter name"
 android:inputType="text"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:layout_margin="20dp"
 android:maxLength="120"
/>
```
```java
// MainActivity.java
EditText myEditText = findViewById(R.id.myEditText);
String inputText = myEditText.getText().toString();
```

## Buttons
* Do not define onClick listener in xml itself, define in Java files
* Do not forget to define id
```xml
<Button
 android:id="@+id/myButton"
 android:clickable="true" // or false
 android:enabled="true" // or false
/>
```
### Adding a Click Listener to a Button
```java
Button myButton = findViewById(R.id.myButton);
myButton.setOnClickListener(new View.onClickListener() {
 @Override
 public void onClick(View v){
  // This code will be executed when the button is clicked
  Toast.makeText(MainActivity.this, "You clicked the button", Toast.LENGTH_SHORT).show();
 }
});
```

## ImageView
* Do not have spaces, uppercase letters or numbers in image files
* Make sure they are jpg or png
* Place them in drawable folder
```xml
<ImageView
 android:layout_width="100dp"
 android:layout_height="100dp"
 android:src="@drawable/testimage"
 android:id="@+id/myImage"
 android:scaleType="centerCrop"
 android:contentDescription="this is the alt text of the image"
/>
```
```java
ImageView myImage = findViewById(R.id.myImage);
myImage.setImageResource(R.drawable.testimage)
```
### Using Image as Background
* Define this attribute in a Layout
```xml
android:background="@drawable/background"
```

## Converting String to double
```java
double kilos = Double.parseDouble(inputText);
```

## Layouts
* Define the UI structure of your app, such as in an activity
* Created using a heirarchy of Views and ViewGroups
 * View
  * A View usually draws something a user can interact with
  * Views are also called widgets, example EditText, ImageView, Button etc.
 * ViewGroups
  * ViewGroups are invisible containers that define layout of child Views and ViewGroups
  * ViewGroup objects are usually called layouts
* Each layout file must contain exactly one root element which must be a valid View or ViewGroup object
* Save xml file in res/layout/
* layout_something - Way to define layout attributes
 * layout_width or layout_height
  * Either pixels or match_parent or wrap_content
  * wrap_content tells the view to acquire width or height as per content
<img width="864" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/6b1d5dfa-cd30-48c8-a325-1dc80827e661">

## Loading the View
* The onCreate() callback method in your activity is called by the Android framework when your activity is launched, this is part of the app life-cycle
<img width="1792" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/4e2cad79-8078-4674-965a-8f5616e8f0a3">

## Different Types of Layout
<img width="1792" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/f60015e8-02ec-43b8-83f4-fb7fa1dcf271">

## Boilerplate Code
<img width="1792" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/bee09091-fe3f-46f0-a59c-d12f042e061e">

## Relative Layout
* This way you can position elements relative to each other or the layout
* Can get complicated for more complex layouts
* For more complex layouts, constraint view is preferred
```java
<TextView
 android:layout_below="@+id/text1"
 android:id="@+id/text2"
/>
```

## Constraint Layout
* Each element in constraint layout must define at least 2 anchor points to position correctly, a vertical and a horizontal
* The position reference can be the layout itself or some other element or even some guide lines that you can create which are invisible datum lines

## Activity
An activity is one screen of an app. In that way the activity is very similar to a window in the Windows operating system. The most specific block of the user interface is the activity. An Android app contains activities, meaning one or more screens.

## App Life Cycle
* onCreate
  * Called when activity is created
  * Good place to initialize widgets, elements or variables
* onStart
  * Called when activity is visible to the user but not interactive
  * Good place to initialize animations or other UI related tasks
* onResume
  * Activity in foreground and is ready for user interaction
  * Its where you should start components which should be actively running such as sensors or location updates
* onPause
  * When the activity is about to lose focus cause another activity is starting or device is going into multi-window mode
  * You should do cleanup, pause ongoing operations and release resources
* onStop
  * When activity is no longer visible to user
  * Again, we can free up resources
* onRestart
  * When activity restarts after stopping
  * Is followed by the onStart method
* onDestroy
  * Last chance to do cleanup, this is called when activity is destroyed
  * Quite interestingly, this is called when we change device orientation, a new activity then starts again

## Intents
* Action to be performed, either within the same app or different apps
  * Implicit
  * Explicit
    * To start a specific component within your own app
```java
// Explicit intent example
public void goToSecondActivity(){
 Intent intent = new Intent(this, SecondActivity.class);
 startActivity(intent); 
}
```
```java
// Implicit intent
public void openWebPage(){
 Uri webPage = Uri.parse("https://www.flipkart.com");
 Intent intent = new Intent(Intent.ACTION_VIEW, webPage);
 startActivity(intent);
}
```
* When you use ACTION_VIEW with a uri, the system will try to find the appropriate component to handle that uri

## Android Manifest
* A file which tells Android OS and other apps about your app and how to interact with it
* <intent-filter> will tell what implicit intents your activity can handle
* You can even define permissions in Android Manifest file

## Gradle
<img width="1792" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/6d2770b3-83da-458d-b47e-07efad345f26">
<img width="1792" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/892d5f61-f2b4-4c38-ad18-5e2c36a2fa19">
* You will mostly work with module-level build.gradle file 

## Using Explicit Intents to Send Data To Another Activity
```java
// MainActivity.java
Intent intent = new Intent(getApplicationContext(), SecondActivity.class);
intent.putExtra("name", userName);
startActivity(intent);
```
```java
// SecondActivity.java
Intent intent = getIntent();
String userName = intent.getStringExtra("name");
```

## Share Data Via Intent
```java
public void shareData(String userName, int randomNumber){
 // Implicit intent
 // ACTION_SEND is used to typically send data other applications or components 
 Intent intent = new Intent(Intent.ACTION_SEND);
 intent.setType("text/plain");

 intent.putExtra(Intent.EXTRA_SUBJECT, userName + " just got lucky!");
 intent.putExtra(Intent.EXTRA_TEXT, "His lucky number is " + randomNumber);

 // Allows you to choose from a range of applications that can handle that intent
 startActivity.createChooser(intent, "Choose a Platform"); 
}
```

## Using Colors from colors.xml in res/values
```xml
<TextView
 android:textColor="@colors/blue_sky"
/>
```

## Using strings from strings.xml in res/values
```
<TextView
 android:text="@atring/blue_sky"
/>
```
