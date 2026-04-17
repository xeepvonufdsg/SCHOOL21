# Starting Activity and Fragment

Summary: In this project, you'll learn about system components in Android through the creation of a mobile app.

💡 [Tap here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave your feedback on the project**. It's anonymous and will help our team make your educational experience better. We recommend completing the survey immediately after the project.

## Contents

- [Chapter I](#chapter-i)
  - [Introduction](#introduction)
- [Chapter II](#chapter-ii)
  - [System components in Android](#components)
  - [Activity](#activity)
  - [AndroidManifest](#androidmanifest)
  - [Fragment](#fragment)
  - [FragmentManager](#fragmentmanager)
  - [BroadcastReceiver](#broadcastreceiver)
  - [ContentProvider](#contentprovider)
  - [RecyclerView](#recyclerview)
  - [ViewBinding](#viewbinding)
- [Chapter III](#chapter-iii)
  - [Description and Requirements](#requirements)
- [Chapter IV](#chapter-iv)
  - [Tasks](#tasks)

## Chapter I

### Introduction

1. Along the way, you may feel a sense of uncertainty and a severe lack of information: that's OK. Remember, the information in the repository and on Google is always with you. So are your peers and Rocket.Chat. Communicate. Search. Use common sense. Don't be afraid to make mistakes.
2. Pay attention to sources of information. Check. Think. Analyse. Compare.
3. Look at the text of each assignment. Read it several times.
4. Read the examples carefully. There may be something in them that is not explicitly stated in the task itself.
5. You may find inconsistencies where something new in the terms of the task or examples conflicts with something you already know. If you come across such an inconsistency, try to work it out. If not, write it down as an open question and find out as you work. Do not leave open questions unanswered.
6. If a task seems confusing or impossible, it only seems that way. Try to break it down. It is likely that some parts will become clear.
7. There will be several tasks. Those marked with an asterisk (\*) are for the more meticulous students. These tasks are more difficult and are not compulsory. But doing them will give you extra experience and knowledge.
8. Don't try to fool the system or the people around you. You will fool yourself first.
9. Got a question? Ask your neighbour to the right. If that doesn't help, ask your neighbour on the left.
10. When you use help, you should always understand why and how. Otherwise the help is useless.
11. Always push only to the develop branch! The master branch will be ignored. Work in the src directory.
12. There should be no files in your directory other than those specified in the tasks.

## Chapter II

## System components in Android

### Activity

An activity is one of the main components of an application in Android. It is a screen that the user can interact with. Each activity must be declared in AndroidManifest, has its own lifecycle and can be started by an Intent with different trigger modes.

### AndroidManifest

AndroidManifest.xml in Android is a configuration file that is included in any application. It has the unique name of the application package as well as major components such as Activity, Services, BroadcastReceiver, and ContentProvider. This file also defines the necessary permissions that the application needs, such as internet or camera access. In addition, AndroidManifest contains information about the Android SDK minimum and target version that the application supports, additional settings that affect the behavior of the application in the system, including the Activity and IntentFilter properties.

### Fragment

A Fragment is a part of an Activity that has its own lifecycle and interface. An Activity can have several Fragments. They can be added, replaced, deleted using the FragmentManager within a single Activity. Also, the Fragment can be reused in different areas in the application.

### FragmentManager

FragmentManager is a class that is used to manage the Fragment inside the Activity. FragmentManager allows you to add, remove, replace and manage their lifecycle. Usually, the FragmentManager performs operations in a special View class FragmentContainerView. This allows you to build navigation in an application where Fragments are the application screens and Activity is their keeper with FragmentContainerView.

### BroadcastReceiver

BroadcastReceiver is a component of an application in Android that allows the application to respond to system and user broadcast messages. Broadcasts are a mechanism for notifying applications of events or changes within the system or the application itself. An IntentFilter must be used to define the specific events that the BroadcastReceiver will respond to. Examples of events that can be handled by the BroadcastReceiver are SMS messages, low battery alerts. In some cases, BroadcastReceiver needs to be declared in AndroidManifest.

### ContentProvider

ContentProvider is an application component in Android that provides a unified interface for accessing data and enables data sharing between different applications. It is used to manage and provide secure access to structured data such as SQLite databases, files and other resources. Must be declared in AndroidManifest.

### RecyclerView

A view class that implements the display of the elements of a given list. A developer can define how each element should be displayed and pass these elements to RecyclerView, which will dynamically create the required elements.

The main advantage of RecyclerView is that it does not create a separate view for each stored element, but reuses already created views to display elements that are placed on the screen. Such elements are called ViewHolder. They are usually created in a limited number - the number of elements displayed on the screen and a few additional ones that can be seen at the top and bottom of the list. This prevents excessive creation and deletion of ViewHolder objects when scrolling through the list, which has a positive impact on performance. Thanks to this feature of RecyclerView, a huge number of elements can be stored efficiently.

### ViewBinding

ViewBinding is a code generation function for interacting with View interface elements. After including ViewBinding in build.gradle, some binding class is generated for each XML layout file. This class represents a set of values associated with labeled layout elements. For example, for a TextView with id "@+id/text\_name", you can simply refer via a field of the generated class "binding.textName", which will be of type TextView. When accessed similarly via findViewById, the result will not have a final type and must be labeled independently.

The advantages of ViewBinding over findViewById are NullSafety of values and types, since direct View references are created without the risk of NullPointerException and ClassCastException exceptions. ViewBinding also simplifies code because it does not require special XML layout files and is automatically applied to all layouts in the module.

## Chapter III

## Description and Requirements

Your task is to make an application that engages the modern practice of creating an application with multiple screens, handling system events, storing data, and making it available to applications externally.

- The program code must be located in the src folder and not contradict the requirements below
- You can use Material 3 as your design recommendations
- The design of the application must be user-friendly
- A FragmentManager must be used to navigate between Fragments
- Use the advantages of ViewModel to save data when the device is rotated
- Provide interaction with View screens using ViewBinding
- MainActivity must be the only Activity in the application
- The Single Activity principle must be followed: each screen has its own Fragment, displaying all Fragments in the MainActivity

For implementing a mobile application, you need to use: - Android Studio 2023.1.1.1 - Kotlin 1.9.0 - Android SDK 34 - Gradle 8.2 (dependency management) - Material 3 (UI creation)

## Chapter IV

## Tasks

Create a project for a mobile application in Android Studio.

### Task 0. Creating a Project

- Select File->New->New Project... in Android Studio.
- Select Phone and Tablet and Empty Views Activity
- Enter the application name - Unit N (where N is the unit number)
- Select development language - Kotlin
- Select the build configuration language - Kotlin DSL
- The program code must be located in the src folder
- Add support for viewBinding to the buildFeatures gradle

The following dependencies must be added to the project: - androidx.datastore:datastore-preferences:1.0.0 - com.google.android.gms:play-services-location:21.0.1 - androidx.ads:ads-identifier:1.0.0-alpha05 - androidx.recyclerview:recyclerview:1.3.1 - androidx.recyclerview:recyclerview-selection:1.1.0

### Task 1. Start Screen Implementation

1. Add a FragmentContainerView to the MainActivity layout, which should be the root and only element.
2. Create a DataStore with some key to store the user data that the user will enter on the first run
   - Describe the access keys to the user data parameters - name and age
3. Create the application start screen as a Fragment, which must contain:
   - TextInputLayout with nested TextInputEditText to fill in user information: name, age
   - Button "Login", which will save the user's information in the DataStore and switch to the Fragment of the main screen (you can create an empty Fragment in this item).
4. Launch the starting Fragment using the FragmentManager in the MainActivity or a declaration inside the FragmentContainerView
5. Create a ContentProvider to further access the DataStore

### Task 2. Main Screen Implementation

1. Create a Fragment for the main screen that contains:
   - TextView with user information from DataStore
   - TextView with information about the device (manufacturer, model)
   - TextView with current charge level, which will be updated in onResume Fragment
   - TextView with advertising id of the device, if any, otherwise "Advertising id is not available"
   - Button "Create email", which will launch Activity in standard mode using the corresponding Intent
   - Button "Open Search Engine", which will launch Intent to open the page in the browser in singleTop mode
   - Button "View Events", which will open a Fragment with the list of events for the current month in the calendar application (you can create an empty Fragment in this item).
   - Button "View Location", which will open a Fragment showing the current location (you can create an empty Fragment in this item).
   - Button “Exit”, which deletes all data from the DataStore and opens the starting Fragment
2. Ensure that the main screen opens when the application starts and when there is data in the DataStore about the user
3. Add a BroadcastReceiver that will track connection and disconnection events to the charger. Add these events to BroadcastReceiver for tracking using IntentFilter. When such an event occurs, the device must vibrate

### Task 3. Calendar Events List Implementation

In order to display a list of calendar events using RecyclerView, you need to implement: - Calendar event model class including id, name and date fields of the event - XML template for calendar event inside the list - custom DiffUtil to efficiently update the event list inside RecyclerView - RecyclerView.Adapter<RecyclerView.ViewHolder> to handle the display of the list of elements containing calendar event models

### Task 4. Calendar Events Screen Implementation

Create a Fragment for the calendar events screen, which should contain - getting permission to access the calendar when there is no permission - TextView - "Calendar is not available" when there is no permission - retrieving calendar events using ContentResolver for the current month - RecyclerView with xml template created for calendar events, RecyclerView.Adapter<RecyclerView.ViewHolder> and DiffUtil

### Task 5. Location Screen Implementation

1. Add a tag to AndroidManifest and include an with
2. Create a location display Fragment that must contain:
   - getting a location permit if there is none
   - TextView - "Location is not available" when no permission is given
   - getting coordinates of the last location using FusedLocationProviderClient
   - request and display in TextView coordinate in OnResume using DefaultLifecycleObserver
   - button "View on map", which will show a choice of Activity map applications to display coordinates in standard mode, using Intent.ACTION\_VIEW and a reference to coordinates of "geo:longitude,latitude" format, or will show Toast "No map applications available" if there are none.