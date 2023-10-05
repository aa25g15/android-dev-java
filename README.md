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
