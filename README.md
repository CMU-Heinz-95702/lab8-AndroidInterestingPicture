# 95-702 Distributed Systems for ISM
# Lab 8 Android Application Lab


# Part 0
Make sure that your IntelliJ has the Android Support plugin installed;
it should have been installed on the original download, but check anyway.
Choose Preferences (or File-> Settings) -> Plugins, and click on the Installed tab. You should see
Android Support already installed; if not,

You'll also need the Android SDK installed. You can do this when you create the
Hello Android project (but it might already be installed).
It does *not* replace the Java SDK.

# Part 1 - Hello Android
# Create an Android Project in Android Studio

1. Choose File -> New -> Project
2. Scroll down to Android (about 7 items down), *not* Java.
3. If the Android SDK is not installed, you'll be prompted to install it -
follow the directions. Then click Next.
4. Then from the Phone and Tablet tab, choose "Basic Activity" and
click Next.
5. Choose an "Application Name" (e.g. "Hello Android")
6. Choose a package name (e.g edu.cmu.yourAndrewID)
7. Select Minimum SDK API 28 and click Next
8. Leave defaults unchanged and click "Finish"

You will see an Android project in the IDE.  It should be a fully-working "Hello
Android" app.


1. Click on the MainActivity.java tab to view the code.
(Need to add Android Module, Module SDK not defined. Added Android 28 )
2. Click the green arrow button to run. You should get a window that says, no
USB dfevices or running emulators detected.
3. Choose Nexus 5x API 28 and click OK.
4. The emulator should start as a separate program (it may be behind other
windows). It should say "Hello World".
5. Click OK

## Test Hello Android in the AVD

Test your Hello Android app by launching it in your Android Virtual Device (AVD,
also known as the Emulator):
1) Click the green play triangle in the Android Studio menubar to run the app.
2) Choose the AVD you just created to run the app in.
3) Switch to the running AVD and verify that the Hello Android app has
  successfully launched.

IF YOU HAVE TROUBLE with the AVD - in particular, if you get the message
"Waiting for process to come online" and then it times out - try these fixes,
one at a time:
https://www.technipages.com/android-emulator-stuck-waiting-for-target-to-come-online

IF THE ANDROID EMULATOR BOOTS UP BUT THE APP DOES NOT LAUNCH - check if you're
using "Quick Boot": go to the AVD Tools -> Android -> AVD Manager; and edit the
configuration (the pencil) of the AVD,
then click Show Advanced Settings. Scroll down to Emulated Performance and
check "Cold Boot", not "Quick Boot".

## Exercises

1. Explore the contents of the project's res directory. These are the static
  resource files that your Android app uses.  They include such things as
  menus, user interface (UI) definitions, icons, and strings.
2. The file res/values/strings.xml defines static strings that are used in your
	application. Change the string named "app_name" to include your
	name (e.g. "Joe\'s App", with the escape character \ before the apostrophe).
3. Save strings.xml
4. Edit res/layout/activity_main.xml. Notice that this is the UI definition of
  the main Activity.  It "includes" a layout for content_main.
5. Edit res/layout/content_main.xml.  This is the part of the screen layout
  that has the "Hello World" message.  Change the text from "Hello World" to
  "Welcome to my new app".
6. Notice the "Design" and "Text" tabs.  Toggle between them to understand what
  they allow you to do.
7. In the Design view, scroll down the Palette to find the "Text Fields".
  Drag a new "Plain Text" field onto your screen. (Make sure you are not using
  a "Plain TextView".  Scroll down further if you can't find "Plain Text" under
  "Text Fields".)
8. In the Properties of this widget (Android calls it an editText element) set
  the "Hint" to "Your answer..."
9. Save content_main.xml
Test it by launching it in your AVD:
10. Click the green play triangle in the Android Studio menubar to run the app.
11. Choose the AVD you just created to run the app in.
12. Switch to the running AVD and verify that the Hello Android app has
  successfully launched and your changes have been successful.

:checkered_flag: **CHECKPOINT: show Part 1 to your TA **

# Part 2 Interesting Picture

1. Download the zipped AndroidInterestingPicture from Canvas
	into your IntelliJ workspace and unzip it.

2. Open IntelliJ
  If you already have a window open from Part 1, close it

3. You should be back to the smaller IntelliJ window; choose Import Project
(or File -> New -> Project from existing sources...).  From the file chooser,
choose the folder containing AndroidInterestingPicture.

4. Choose "Import project from external model", then Android Gradle and click
Finish. The project should open; navigate to app->src->main->java, where you'll
see the package directory.

5. Get a Flickr API key from:
	http://www.flickr.com/services/api/misc.api_keys.html

   Note: you will be asked to create a Yahoo account. Don't forget what you use
   as a password. Yep, a Yahoo account.

6. Edit the file GetPicture.java and put your API key where it says
  "<<<put your Flickr api key here>>>" (replace the << and >> also!).
  Remember to save the file.

7. Click the green play triangle in the Android Studio menubar to run the app.
8. Choose the AVD you just created to run the app in.
9. Switch to the running AVD and verify that the InterestingPicture app has
  successfully launched.  Type in a keyword to search such as "boat" and
  click Submit and you should see a picture displayed.

Explore the project folders. The most important are the "java" and "res"
folders.  The java folder has the source code for the application, and
the res folder has the static resources as you saw in Part 1.

Within the java folder, you will see two classes:
ds.cmu.edu.interestingpicture.InterestingPicture
ds.cmu.edu.interestingpicture.GetPicture

Study the InterestingPicture class.  Android applications are organized into
"activities" and this is the main activity for this application.  Read the
comments and the code and understand how it works.

The GetPicture class is used to first search Flickr for a pictures related to
a keyword, and then fetch a picture.  So that the phone user interface is not
frozen while these network activities take place, these network actions must
take place in a helper thread.  AsyncTask makes it easy to use a helper
thread.  Read the comments in GetPicture and review the AsyncTask API:
http://developer.android.com/reference/android/os/AsyncTask.html

10. The application is missing the feedback "Here is a picture of a ..." or
	"Sorry, I could not find a picture of a..."
     a. Add a new TextView to res/layout/main.xml for this feedback
     b. In the pictureReady method, findViewById your new TextView
     c. Set the text of the TextView to the appropriate string (depending on
     		whether the picture is found or not).
       (Where can you get the search term from to add to this string?)
11. Run and test it.

12. Sort the following list of methods into the order they are invoked when
	"submit" is clicked, and indicate whether they are being run in the "UI"
	thread or a helper thread. See for reference the AsyncTask API:
	http://developer.android.com/reference/android/os/AsyncTask.html

      AsyncFlickrSearch.search
      doInBackground
      GetPicture.search
      getRemoteImage
      getRemoteXML
      onClick
      onPostExecute
      pictureReady

:checkered_flag: Show a TA

For credit for the lab, show a TA:
	- Working Part 1
	- Working Part 2 through step 11
	- Your sorted list from Part 2 step 12
	  (BTW, a question regarding UI and helper threads is likely on the test.)
