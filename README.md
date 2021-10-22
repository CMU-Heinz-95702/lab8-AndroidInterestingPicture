# 95-702 Distributed Systems for ISM
# Lab 8 Android Application Lab


# Part 0: Android Studio
## Do one or the other of:
(1) Because we've had some difficulty with using IntelliJ for this lab last semester, you should install Android Studio from:

https://developer.android.com/studio

The current version is 2020.3.1

(2) If you want to try IntelliJ, make sure that your IntelliJ has the Android Support plugin installed;
it should have been installed on the original download, but check anyway.
Choose Preferences (or File-> Settings) -> Plugins, and click on the Installed tab. You should see
Android Support already installed; if not, IntelliJ will prompt you to install it.

You'll also need the Android SDK installed. You can do this when you create the
Hello Android project (but it might already be installed).
It does *not* replace the Java SDK - you need that, too (at least JDK 16).

Some help is here:
https://www.jetbrains.com/help/idea/create-your-first-android-application.html

# Part 1 - Hello Android
# Create an Android Project in Android Studio

1. Choose "Create New Project" on the startup screen (later, if you have a project already open, do Choose File -> New -> Project like usual).
2. Choose the Phone and Tablet tab; click on Basic Activity, then click Next.
3. Choose an "Application Name" (e.g. "Hello Android"). This will change the Package name and Save location automatically.
4. Change the package name to something reasonable (e.g edu.cmu.<yourAndrewID>)
5. (Optional) Change the Save location by clicking the small file folder icon to bring up the FileChooser. You may need to enter a new directory name.
6. Change the language to "Java" - it probably will default to "Kotlin".
7. Select Minimum SDK API 28 (Android 9.0 Pie) and click Finish.
8. The "Installing Requested Components" window will show next; wait for it to load everything, then click Finish.

**(Optional)** If you have multiple versions of the Java JDK installed - in particular, if you have 1.8 - it might default to an older version, which will not be compatible with the current version of the Android SDK. If you think that's an issue (you project doesn't build and the error message says you're using 1.8, say), then do this:
- click AndroidStudio->Preferences->Build,Execution,Deployment->Build Tool ->Gradle
- click the down arrow at the end of the Gradle JDK field
- if jdk-16 (or higher) shows up, click that; if not, click other, and (hopefully) all your JDK versions will show up: click jdk-16 and Open
- click Apply and OK

You will see an Android project in the IDE; it will take a few moments to build.  It should be a fully-working "Hello Android" app.

## Test Hello Android in the AVD

1. Click on the MainActivity.java tab to view the code.
2. Pixel 5 API 30 will likely be the default showing in the box next to the green triangle. Expand dropdown menu next to the green triangle button. Choose AVD Manager (at the bottom).
3. Click the Create Virtual Device button at the bottom.
- Choose **Nexus 5**; click Next
- choose **API level 28**; download that. Highlight it and click Next.
- Nexus 5 API 28 should show up in the Your Virtual Devices screen. Close that window.
- Nexus 5 API 28 should also show up in the dropdown box next to the green triangle. Make sure it's selected before running.
4. Click the green triangle.
5. Switch to the running AVD and verify that the Hello Android app has successfully launched. It may take a few moments for the emulator's phone to boot up. The emulator should start as a separate program (it may be behind other windows). It should say "Hello First Fragment".

IF YOU HAVE TROUBLE with the AVD - in particular, if you get the message
"Waiting for process to come online" and then it times out - try these fixes,
one at a time:
https://www.technipages.com/android-emulator-stuck-waiting-for-target-to-come-online

IF THE ANDROID EMULATOR BOOTS UP BUT THE APP DOES NOT LAUNCH - check if you're
using "Quick Boot": go to the Tools -> AVD Manager; click the down arrow on the right side of your chosen virtual device, and choose Edit .
Click Show Advanced Settings. Scroll down to Emulated Performance and
check "Cold Boot", not "Quick Boot". Click Finish. Then rebuild the app and run it again.

## Exercises

1. Explore the contents of the project's res directory. These are the static
  resource files that your Android app uses.  They include such things as
  menus, user interface (UI) definitions, icons, and strings.
2. The file res/values/strings.xml defines static strings that are used in your
	application. Change the string named "first_fragment_label" to include your
	name (e.g. "Joe\'s App", with the escape character \ before the apostrophe).
3. Save strings.xml
4. Examine res/layout/activity_main.xml. Notice that this is the UI definition of the main Activity.  It "includes" a layout for content_main. You'll likely be in "Design Mode" initially; change to "Code" using the button at the top right.
5. Edit res/layout/content_main.xml.  This is the part of the screen layout for the overall app. Change the color from colorPrimary to colorSecondary.
6. Edit fragment_first.xml. In the Design view, in the Palette window, click on Text. Drag a new "Plain Text" field onto your screen.
7. In the Properties of this widget, find the Common Attributes, and set
  the text to "Hello Android"
8. Save content_main.xml
9. Use the red square to stop the app (if it was running).
10. Click the green play triangle in the Android Studio menubar to run the app.
11. Choose the AVD you just created to run the app in.
12. Switch to the running AVD and verify that the Hello Android app has
  successfully launched and your changes have been successful.

:checkered_flag: **CHECKPOINT: Part 1 ends here**

# Part 2 Interesting Picture

1. Download the zipped AndroidInterestingPicture from Canvas and unzip it.

2. Open Android Studio. If you already have a window open from Part 1, close it.

3. Choose File->New->Import Project. From the file chooser, choose the folder containing AndroidInterestingPicture.

4. Choose "Import project from external model", then Android Gradle and click
Finish. The project should open; navigate to app->src->main->java, where you'll
see the package directory.

5. Get a Flickr API key from:
	http://www.flickr.com/services/api/misc.api_keys.html

   Note: you will be asked to create a Yahoo account. Don't forget what you use
   as a password. Yep, a Yahoo account.

6. Edit the file GetPicture.java and put your API key where it says
  "<< put your Flickr api key here >>" (replace the << and >> also!).
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
     a. Add a new TextView to res/layout/content_main.xml for this feedback
     b. In the pictureReady method, findViewById your new TextView
     c. Set the text of the TextView to the appropriate string (depending on whether the picture is found or not).
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

:checkered_flag: **Part 2 ends here**
