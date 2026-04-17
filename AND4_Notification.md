# Notification, AppWidget, RemoteViews

💡 [Tap here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave your feedback on the project**. It's anonymous and will help our team make your educational experience better. We recommend completing the survey immediately after the project.

## Contents

- [Information](#information)
  - [RemoteViews](#remoteviews)
  - [AppWidget](#appwidget)
  - [Notification](#notification)
  - [WorkManager](#workmanager)
  - [Ktor](#ktor)
- [Project](#project)
  - [Description and Requirements](#description-and-requirements)
  - [Tasks](#tasks)
    - [Task 0. Creating a Project](#task-0-creating-a-project)
    - [Task 1. Getting the Current Weather](#task-1-getting-the-current-weather)
    - [Task 2. Configuring NotificationChannel and Requesting Authorization](#task-2-configuring-notificationChannel-and-requesting-authorization)
    - [Task 3. Creating RemoteView Weather Notifications](#task-3-creating- remoteView-weather-notifications)
    - [Task 4. Creating and Updating Notifications with the WorkManager](#task-4-creating-and-updating-notifications-with-the-workmanager)
    - [Task 5. Creating and Updating RemoteView Weather Widget](#task-5-creating-and-updating-remoteview-weather-widget)

Hello! Today's goal is to learn about creating notifications and widgets in Android.

# Information

### RemoteViews

RemoteViews is a class that allows you to create a user interface for certain kinds of components outside your application. Such components are widgets, notifications. They are displayed in other processes different from the app, and so require a different approach to interaction from Android.

RemoteViews allows you to define xml layouts of external components in a similar way to regular application screens. But there is a rather limited set of elements supported when creating a RemoteView. For example, TextView, Button, ImageView can be used while RecyclerView cannot.

The key aspect when working with RemoteView is that you first create and customize the View layout, and then link it to a component - a widget/notification.

### AppWidget

AppWidget is a UI component that can be placed on the "home screen" of a device. Widgets give users quick access to app features and can display information updated in real time.

To create an AppWidget, the developer defines a layout and creates an AppWidgetProvider, which is a special class that manages the widget's lifecycle. AppWidgetProvider inherits from BroadcastReceiver and responds to various events, such as updating the widget or clicking on its elements. The appwidget-provider xml file defines parameters such as widget size, update frequency, and the layout itself. Also you need to describe in the AppWidgetProvider the creation of a RemoteView from the appwidget-provider xml file and assigning the created View to all created widgets.

For a more detailed explanation and practices on creating widgets in Android read the documentation in the [Create App Widgets](https://developer.android.com/develop/ui/views/appwidgets/overview) tab.

### Notification

Notifications are an important way to keep the user informed. Android currently allows developers to create options from regular notifications with a simple header to custom notification designs using RemoteView.

Starting with Android 8 (SDK 26), you must create a Notification Channel before sending notifications. This new feature allows for a more competent handling of notifications and updates on existing notifications. For example, Google doesn't send multiple notifications about the weather, but updates the information on an existing one.

You can find the latest information about notifications (name, description and setting of notification sending channels) in the system settings of the application. For example, Telegram separates the sending of notifications by different types of messages: Private Chats, Groups, etc.

Starting with Android 13, the app now needs to grant permission for notifications to be sent.

For a more detailed explanation and practices on creating notifications in Android read the [documentation](https://developer.android.com/develop/ui/views/notifications).

### WorkManager

WorkManager is a library designed to perform background tasks that should run even when the application is closed. WorkManager is good for tasks that require a guarantee. For example, downloading files, synchronizing data with the server.

The library allows developers to conveniently schedule one-time or recurring tasks, manage their execution, and receive notifications of results. The developer creates a class that inherits from Worker or CoroutineWorker, specifying the logic of the scheduled task by overriding the doWork() method. Next, a WorkRequest is created, which can be customized with various constraints such as network connectivity and charge level.

An important point: WorkManager manages background tasks at the system level, not an individual Activity or even an application. This keeps the WorkManager independent of where it runs and is not tied to the life cycle of the component.

You can read a more detailed explanation and practices for using WorkManager in the [documentation](https://developer.android.com/topic/libraries/architecture/workmanager).

### Ktor

Ktor is a set of networking libraries written in Kotlin. Ktor allows you to create both server-side applications and client-side ones. Ktor Client facilitates the development of networking in Android applications by supporting such useful functionality as automatic serialization and deserialization of data in JSON, authentication, session management.

Find more about Ktor's available functionality and connecting it to Android projects in the [documentation](https://ktor.io/docs/getting-started-ktor-client-multiplatform-mobile.html#android-activity). There you need to look at the part that deals specifically with Android apps.

# Project

In this project, you will write a mobile application that will introduce you to creating notifications, widgets, and updating them in the background. Your task is to make an app to display the current weather information in notifications and a widget, which will be updated every 15 minutes.

### Description and Requirements

- The program code must be located in the src folder and not contradict the requirements below
- You can use [Material 3](https://m3.material.io/develop/android) as your design guideline.
- The design of the application must be user-friendly

**For the implementation of mobile application tests, you need to use:**

- Android Studio 2023.1.1;
- Kotlin 1.9.0;
- Android SDK 34;
- Android MinSDK 26;
- Gradle 8.2 (dependency management)
- Material 3 (creating a user interface)

# Tasks

Create a project for a mobile application in Android Studio.

### Task 0. Creating a Project

- Select File->New->New Project... in Android Studio.
- Select Phone and Tablet and Empty Views Activity
- Enter the application name - Unit N (where N is the unit number)
- Select development language - Kotlin
- Select the build configuration language - Kotlin DSL
- The program code must be located in the src folder
- Add support for viewBinding to buildFeatures gradle

**The following dependencies must be added to the project:**

- androidx.core:core-ktx:2.2.0
- androidx.work:work-runtime-ktx:2.8.1
- io.ktor:ktor-client-android:2.3.7
- io.ktor:ktor-client-okhttp:2.3.7
- org.jetbrains.kotlinx:kotlinx-coroutines-android:1.7.3
- plugin kotlin("plugin.serialization")
- org.jetbrains.kotlinx:kotlinx-serialization-json:1.6.0

### Task 1. Getting the Current Weather

1. Build a URL to get the current weather in Moscow using the constructor in the [API documentation](https://open-meteo.com/en/docs/dwd-api/#latitude=55.7522&longitude=37.6156&timezone=Europe%2FMoscow&forecast_days=1).
2. Create a `data class` WeatherResponse with the `@Serializable` annotation to convert JSON into a response model.
3. Create object Dependencies to simulate the dependency injection. The object will create and store references to dependencies to provide to other classes. For example, you will need the weather request call in different classes of your code, and the object to interact with the external service will be provided to each of them through Dependencies.
4. Add an HttpClient property to the Dependencies with the JSON processing configuration.
5. Create a WeatherService class for weather information that will contain:
   - HttpClient property in the constructor;
   - suspend function to get current weather information that returns WeatherResponse on success and null on error.
6. Add the WeatherService property to Dependencies.

### Task 2. Configuring NotificationChannel and Requesting Authorization

1. Add StringResource R.string.channel\_name for the name of the new NotificationChannel.
2. Add a non-zero Int NOTIFICATION\_ID constant to the companion object MainActivity for the id of the NotificationChannel. Use this constant when creating specific notifications as well, so that the user always sees one notification. The constant must be non-zero, as the identifier of specific notifications should not be 0.
3. Create NotificationChannel with id — NOTIFICATION\_ID and the R.string.channel\_name name.
4. Add to AndroidManifest the permission to send notifications.
5. Create a request in MainActivity at app startup to send notifications for devices that support Android 13 and above.

### Task 3. Creating RemoteView Weather Notifications

1. Create an xml layout file for the regular notification form in the layout folder. The layout must contain a TextView for the header including the name of the city (Moscow) and the temperature for the last hour.
2. Create an xml layout file for the expanded notification form in the layout folder. The layout must contain a TextView for the header, like a regular notification, and a TextView comparing the weather in the next hour (it will be warmer/colder in an hour).
3. Create a "Create Notification" Button in the MainActivity, which when clicked will create or update a notification with information about the current weather on request from WeatherService. Use the created notification layouts to create a RemoteView.

### Task 4. Creating and Updating Notifications with the WorkManager

1. Create an UpdateWeatherWorker class, inherited from CoroutineWorker with a private WeatherService field to request an up-to-date weather forecast.
2. Describe in the doWork UpdateWeatherWorker method receiving data from WeatherService, creating and updating the notification using RemoteView with the shared ID from step 2. If there is no data from WeatherService, the notification shall not be created or updated.
3. Create a PeriodicWorkRequest for CoroutineWorker inside onCreate MainActivity with a periodicity of every 15 minutes (minimum for WorkManager).

### Task 5. Creating and Updating RemoteView Weather Widget

1. Create the WeatherAppWidgetProvider and the necessary information for it using the File-New-Widget tab. The result should be:
   - WeatherAppWidgetProvider class with an AppWidgetProvider base class;
   - weather\_app\_widget\_provider in the res-layout folder xml file to create the UI display of the widget;
   - weather\_app\_widget\_provider\_info in the res-xml xml file with a description of the widget display parameters.
2. Create an xml layout file for the small size widget in the layout folder. The layout must contain a TextView to display the current weather and a TextView for the city name.
3. Create an xml layout file for the large size widget in the layout folder. The layout must contain a TextView to display the current weather, a TextView for the city name and a TextView for the weather forecast for the next 2 hours.
4. Add support for different sized widget in the xml appwidget-provider and in the onUpdate AppWidgetProvider method, as presented in [documentation](https://developer.android.com/develop/ui/views/appwidgets/layouts#anatomy_determining_size_). To do this, you need to declare min/maxresize, width/height attributes in the xml appwidget-provider xml. Add mapping of widget sizes and widget layout xml files in the onUpdate AppWidgetProvider method.
5. Set the update interval to 30 minutes (minimum for widgets) in the xml appwidget-provider for your widget.
6. Describe in the OnUpdate AppWidgetProvider method for your widget a request to the WeatherService and a RemoteView update for all created widgets on the device's home screen.
7. Add logic to update weather widgets via RemoteView on clicking Button "Update Widget Data". For example, through sending Intent `AppWidgetManager.ACTION_APPWIDGET_UPDATE` to call the onUpdate method in the WeatherAppWidgetProvider.
8. Likewise, add an Intent sending to the UpdateWeatherWorker to trigger a widget update, which will allow the widget to be updated at a shorter interval.