<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/64dd051b-3310-45fe-8a6d-c24df0b3bbf4"># android-dev-java

## High Level Tips
* Always initialize variables in onCreate, you can declare them as class fields though
* You can use infer constraints button to directly add position constraints
* You can create drawable shapes using xml inside the drawables folder
* If you have unexpected errors in Android Studio, go to build -> clean project
* Whenever you want to access image or store the asset reference to it, just store its int id
* Context actually provides access to various application specific resources, system level services and info about app's environment
* Not sure but we are using 0dp layout_height and layout_width in order to fill space sometimes

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

## theme
* You can use theme to define light and dark themes
* Example, in themes.xml
```xml
<item name="colorPrimary">@color/blue_sky</item>
```

## Menu
* Provides a convenient way to access app features
* Right click res -> new -> Android Resource Directory -> resource type select menu
* Right click menu -> new menu resource file
* You need to inflate the menu in your activity to perform actions, inflating is like creating the DOM of html, but here we are turning the XML into an object instance
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/ec7c13be-ee79-4d28-bd76-158eba4400d5)
* After inflating, you might not see the menu until you change this in themes.xml -> remove the NoActionBar from the parent attribute of the style tag
* To perform actions, you need this:
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/8323f13a-886b-40e5-af5f-4964ca68e478)

## Fonts
* Right click res -> new android resource directory -> select font
* Copy .ttf or .otf file to font folder
* Now use
```xml
<TextView android:fontFamily="@font/my_custom_font" />
```

## Checkbox
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/8ae00b4b-cc78-4da4-8349-2731014fa15c)
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/96e3255f-3a90-4cee-b044-9df6a87ef9fd)

## Radio Buttons
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/24166ce3-833e-4c28-b4a3-643acdc48ad5)
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/c7dc84c9-16bb-4fc1-8261-0b828c20781c)

## Spinner
* Quite weirdly, the spinner is actually a dropdown or select in Android, it is not a loader per say
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/9da23523-43bd-4ef9-8c4b-9323699f3145)
```java
// MainActivity.java

// View
Spinner spinner = findViewById(R.id.spinner);

// Data source
String[] courses = {"Java", "Kotlin", "C++", "JS"};

// ArrayAdapter: Used to populate spinner with items from string array data source
ArrayAdapter<String> adapter = new ArrayAdapter<>(this, Android.R.layout.simple_spinner_item, courses);

// Apply adapter to spinner
spinner.setAdapter(adapter);
```

## Time Picker
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/e0e4ea93-04b8-4bcf-be3a-3583ee508dc1)
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/b914b39b-b2e4-4708-993b-c8c285fb4ad5)

## Date Picker
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/f9df472e-badb-43fb-9c05-49cf3dd67a4c)
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/b01d787c-ea7b-469d-b66f-f4d235aa713d)

## Progress Bar
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/9183c2e4-2646-475a-8952-5e286d8fbdb8)
* Use progressBar.setProgress() to set the progress value, can be 0 - 100

## Raw Folder
* Right click res -> new android resource directory -> raw
* A folder where raw resources are placed
* Raw resources are not processed by the system and are accessed/stored as is, example audio, video, json etc.

## MediaPlayer
```java
// MediaPlayer mediaPlayer = new MediaPlayer();
MediaPlayer mediaPlayer = MediaPlayer.create(getApplicationContext(), R.raw.some_file); // This is more common approach
mediaPlayer.start();
```

## Multiple Buttons in Activity With OnClick
* Instead of adding multiple new View.onClickListener, you can implement the View.onClickListener on the activity class and override the onClick method in the class itself, then you can just use:
```
Button myButton = getViewById(R.id.myButton);
myButton.setOnClickListener(this);
```

## Adapters
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/db59ddee-88c3-46f3-b49b-bb2f17af780e)

## ListViews with Adapters
* Used to display list of components, the data is provided by an adapter
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/7eb71d4a-74de-44d4-aa5f-917ffdd6662b)
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/df060196-ecd5-4b03-a15b-8c4b626c8412)

## Custom Adapter
* You need
  * Item Layout xml file
  * Model Class
  * Custom Adapter Class with ViewHolder static class
  * Data Source
* Can be built by extending BaseAdapter for which you need to define certain methods as follows
* You need to create a new layout file as well for your list item template
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/5c4b4d97-6417-4aa0-bebd-72550876b16a)

### View Holder Class
* You need to use the ViewHolder pattern to recylce and re-use already inflated views to improve list performance
* Basically caches the references to the views of list items so they dont have to be looked up repeatedly using findViewById during scrolling
```java
// Create static class inside CustomAdapter class
static ViewHolder {
 // Hold references to the views within an item layout
 TextView textView;
}
```
* Then, the getView method in the CustomAdpater can be written as follows
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/4aeeefe7-6993-4f15-9a4e-caa8e11afa55)

## Model Class
* A Model Class will define the data structure and behaviour of each item in a list view
* Define constructor, getters, setters

## Click Events on List View
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/f0e1ea9e-83ad-4d8f-8fb1-be7bb39414e9)

## getView When Using ArrayList in Custom Adapter
* This is a bit tricky, so writing this for understanding
```java
@NonNull
@Override
public View getView(int position, @Nullable View convertView, @NonNull ViewGroup parent){
 // Get the planet object for the current position
 Planet planet = getItem(position);

 // Inflate layout
 MyViewHolder myViewHolder;
 final View result;

 if(convertView == null){
  myViewHolder = new MyViewHolder();
  LayoutInflater layoutInflater = LayoutInflater.from(getContext());
  convertView = layoutInflater.inflate(
   R.layout.item_list_layout, // custom layout xml
   parent,
   false
  );

  // Finding Views
  myViewHolder.planetName = (TextView) convertView.findViewById(R.id.planet_name);
  myViewHolder.moonCount = (TextView) convertView.findViewById(R.id.moon_count);
  myViewHolder.planetImg = (TextView) convertView.findViewById(R.id.imageView);

  result = convertView;
  convertView.setTag(myViewHolder); // setTag can be used to attach an object to convertView to be retrieved later
 } else {
  // The view is recycled
  myViewHolder = (MyViewHolder) comvertView.getTag(); // Gets the attached object using setTag
  result = convertView;
 }

 // Getting data from modal class
 myViewHolder.planetName.setText(planets.getPlanetName());
 myViewHolder.moonCount.setText(planets.getMoonCount());
 myViewHolder.planetImg.setImageResource(planets.getPlanetImage());

 return result;
}
```

## Grid Layout
* Create layout xml also, right click res -> new resource file
* Use numColumns or setNumColumns to set number of columns in GridView
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/83e73e4e-5da0-438e-aad0-fc247d9b1aec)

## Recycler Views
* Good for displaying large amounts of data
* Reduces power consumption, makes app performant
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/4790678f-877e-4069-9cf6-2e405b81ba9a)
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/0d249ad1-2ab1-422a-a2c3-5677a06c00a5)
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/053db075-3c04-40e0-b8ab-eedbaf49d627)
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/a3cd699b-9782-4d9c-bbd4-db08383079b0)
* When creating the Custom Adapter for recycler view, there are methods which you need to implement, check this online
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/e05e8e31-00d4-4568-bc88-f21a57be63df)
* Other than this, you can declare the ViewHolder class like this
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/c5f60b8d-2db8-4070-8161-30ecd73d83ce)

## LinearLayoutManager
* RecyclerView will not show on UI without the LinearLayoutManager
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/825f662a-4ef4-4977-8c2d-764645be31b1)

## Adding Click Event Listener to Recycler View Item
* You need to implement View.onClickListener in appropriate classes
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/3f67f4da-07cd-4ab1-a9dc-b8e885c3e483)

## CardView
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/0d079469-d2f9-4354-8a4a-5265e4d0e478)
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/199d321c-b46f-4646-9364-2ccdd2523519)
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/867da226-625f-4bab-aafa-088766142282)
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/c22f9077-1b66-4946-ac17-54e20b39922b)

## Android Components
* Building blocks of Android app
* 4 types
![image](https://github.com/aa25g15/android-dev-java/assets/26576978/8fb206d9-21d9-44d1-aa4f-ee8f46651d09)

## Services
* Foreground services include things like media playback, they show a permanent notification indicating the user that the service is running
* Background services include things like data sync, a persistent notification is not shown and the user is unaware of them running
* Bound services are tightly bound to components, they are destroyed when all components have unbounded
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/01cd4262-95ac-44f2-9116-fc834d4f9493">
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/ab18207c-e341-4593-8363-6f1a3724b1aa">
* Carefully handle service lifecycle else you can create instability, weird behaviour and resource leaks
* onCreate
  * For 1 time initialization tasks
* onStartCommand
  * Called when service is started using startService method, provides intent to startService method and other params.
  * You perform background tasks in this method.
  * You can return values like start sticky or start non-sticky to tell how the system should handle the service if it is killed due to resource constraints.
* onDestroy
  * When service is about to be destroyed, perform cleanup
* bindService
  * Bind the service to a component
* onBind
  * When a component binds to the service
* onUnbind
  * When all components have unbound. You can return true if you want the service to keep running even after all have unbounded.
  * Default is to return false.
* onRebind
  * A component which was bound earlier, binds again

### Creating a Service
* Create in the same folder as the Mainactivity.java
* START_STICKY will tell the system to restart the service if killed but you need to handle reinitialization
* START_NOT_STICKY will tell system to not start if killed
* IBinder interface is used to establish a communication channel between the bound component and the bound service, returning null simply indicates that the service you created does not bind to anything
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/0ffb471d-d106-4929-95b6-30bde18d2773">

### Starting Service
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/be687a11-99e3-44cc-9798-1bfc04215c29">

### Stopping Service
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/9e4295e1-8a6f-412e-aa19-8e1ce9063869">

### Declaring in Manifest
* A service will not be able to perform tasks unless you declare it inside Application tag in manifest
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/97bdebb7-4856-4034-ab94-d191b6ae281c">

## Broadcast Receiver
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/8edd6dbb-b609-46cd-87b3-b307554d2f92">
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/b0d5bb29-22f2-49d5-aa1b-a9315c6bac82">

### Static Way to Register
* Will only work with API level 25 or lower
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/2c0f0e71-68a4-4201-a444-ba2c49f3b10a">

### Dyanmic Way to Register
* WIll work with API level 26 or higher
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/ff2c2b8c-d329-40fb-a1cf-f9758ce75b6f">

## Fragments
* Basically components like in React Native
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/1fcea16c-5a02-4c6a-bd0c-e3792ac44c80">
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/809f7482-a436-4a85-885e-a54aebc76e19">
* onCreate is when the fragment is created, use this for initialization
* onCreateView is when UI is created or inflated, can also be used to programatically create UI elements
* onStart is when it is ready to interact with user
* onAttach is when fragment is attached to an activity
* onActivityCreated is when fragment is fully initialized, good to add tasks which need fragment to be fully initialized

### Creating Fragment
* Use FrameLayout
* Fragment has one XML and one Java file
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/98c4ded4-dd75-4897-a0da-d65bec7acdc8">
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/c3e2df71-a395-4b24-be5f-1512281c09b6">
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/bbe6c4d2-de4c-4259-a6b9-ae2f58808463">

### FragmentManager
FragmentManager is the class responsible for performing actions on your app's fragments, such as adding, removing, or replacing them and adding them to the back stack.

### Using Fragment
* Create a FrameLayout in Activity XML to be replaced by fragment in Java code via something called Fragment transaction
* Declare loadFragment function in MainActivity.java and use it like this to load fragments:
```java
loadFragment(new FirstFragment());
```
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/c9ccec82-d24b-4f00-aadd-cc759a8148d0">
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/f0254052-141e-4877-b80e-d6116e46f3f9">

## ViewPager
* Can create swipable UI with fragments
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/3102eb9d-0bd0-44bf-adaf-e853825097de">
* Use ViewPager2
* For that you also need to add dependency in build.gradle
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/40671554-10dd-4407-86c0-4006eec25a59">
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/57dd4e92-35b0-4604-bd2e-16310dea47cc">
* You need to create an adapter for your ViewPager
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/ad1613ae-1a52-44da-85dc-c074687f9383">
* Basically in the adapter class, we are managing an ArrayList of all fragment instances pushed to the array by a method

### Using ViewPager
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/5415beaa-dcb3-4d93-b70f-9a01e5529e48">
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/cf1a4065-955c-42fe-91dd-131d0a20beba">

### Hooking up TabLayout to ViewPager
* Create TabLayout
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/a7c46d10-6f40-4d52-b4e1-3492c34c2806">
* Use TabLayoutMediator for hooking up, note that we can even pass a lambda function in the third param
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/387b73f5-bac1-45bf-945b-fcb4a737b3a6">
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/09f574d3-7fcd-4987-a132-62df6846a9b6">

## Android Jetpack
* Jetpack is a suite of libraries to help developers follow best practices, reduce boilerplate code, and write code that works consistently across Android versions and devices so that developers can focus on the code they care about.
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/17fc87cc-c4bb-4e8b-ae7f-3adbdacd6586">

## Data Binding
* Using findViewById cannot be used repeatedly for large apps cause the Android system will have to go through the entire tree to find the View
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/f1e12e64-1bb9-45ee-8819-b26b1cd12967">
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/7164b6de-6309-4de3-8b8b-c5c3261bffc0">
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/2c9c0cce-64d0-4f13-b8c9-deef37c7539b">
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/f962480b-e503-440b-a931-958e8f27b2d5">
* Data binding library already comes with Gradle, but you need to enable it in the app level build.gradle
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/bb593c25-1026-426f-85d3-c1ee82ea7a98">

### Implementing Data Binding
* Wrap XML Layout Container such as ConstraintLayout with <Layout></Layout> tag
* Now you need to add <data> tag above all children, this tag will have <variable> tags
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/55818b84-b137-42fc-9d76-e4fa814a7a4c">
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/fba9fd0c-b5c3-47aa-869c-c0ec942ef79d">
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/b5832246-1b46-4565-aac2-e97296ee35e1">
* If you get duplicate class Kotlin errors, try this
<img width="1440" alt="image" src="https://github.com/aa25g15/android-dev-java/assets/26576978/2755cfc5-fca4-4893-b096-66557c690a56">




