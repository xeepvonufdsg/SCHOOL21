# Starting Activity and Fragment

Summary: Today’s goal is to learn about multithreading in Android.

💡 [Tap here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave your feedback on the project**. It's anonymous and will help our team make your educational experience better. We recommend completing the survey immediately after the project.

# Contents

- [Chapter I](#chapter-i)
- [Introduction](#introduction)
- [Chapter II](#chapter-ii)
  - [Information](#information)
  - [Thread](#thread)
  - [Handler, Looper and HandlerThread](#Handler, Looper and HandlerThread)
  - [Coroutines](#coroutines)
  - [Android Service](#android-service)
  - [BroadcastReceiver](#broadcastreceiver)
- [Chapter III](#chapter-iii)
  - [Project](#project)
  - [Description and Requirements](#description-and-requirements)
- [Chapter IV](#chapter-iv)
  - [Tasks](#tasks)
    - [Task 0. Creating a Project](#task-0-creaing-a-project)
    - [Task 1. Preparing the Model, ViewBinding and Layout](#task-1-preparing-the-model-viewBinding-and-layout)
    - [Task 2. Sending a Message with Handler](#task-1-preparing-the-model-viewBinding-and-layout)
    - [Task 3. Sending a Message with Handler Using Looper’s Main Thread](#task-1-preparing-the-model-viewBinding-and-layout)
    - [Task 4. Sending a Message with Handler Using Looper Retrieved From HandlerThread](#task-4-sending-a-message-with-handler-using-looper-retrieved-from-handlerThread)
    - [Task 5. Sending a Message with Coroutine](#task-5-sending-a-message-with-coroutine)
    - [Task 6. Sending a message with Service and BroadcastReceiver](#task-6-sending-a-message-with-service-and-broadcastReceiver)

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

# Information

Multithreading in Android refers to the ability of an application to perform multiple tasks at the same time. This is important to provide a responsive user interface and efficient utilization of device resources. There are several ways of multithreading implementation in Android:

### Thread

You can use Thread to execute code in a new thread. However, using Thread directly can be inconvenient, especially when interacting with the user interface.

### Handler, Looper and HandlerThread

- **Handler** in Android is a mechanism that allows messages to be processed and exchanged between threads. It is associated with a specific thread (Looper) and can be used to schedule code execution in that thread. Handler is usually binded to the main thread (UI thread), but can also be used to process messages in background threads.
- **Looper** in Android represents a message processing loop within a thread. Each thread that wants to process messages must have its own Looper. It allows a thread to loop through messages that have been sent to its MessageQueue. The thread cannot efficiently process asynchronous messages without Looper.
- **HandlerThread** in Android represents a thread with a message loop (Looper). This is a convenient way to organize background task execution associated with Handler. HandlerThread creates a new thread in which a Looper is automatically created and started, and the associated Handler allows messages to be sent and processed in that thread. HandlerThread provides a convenient mechanism for performing operations in the background without having to explicitly manage threads and message loops.

### Coroutines

Coroutines are a concept in asynchronous programming that allows efficient management of concurrent tasks and simplifies asynchronous code. In Kotlin, coroutines are provided as part of the standard library. Basic aspects of coroutine:

- **Lightweightness** Coroutines are lightweight and consume fewer resources compared to traditional threads. They provide a convenient way to organize asynchronous tasks without creating a large number of threads.
- **Functions**. Functions are used for coroutines, which are declared using the suspend keyword. Functions can be suspended and resumed, allowing asynchronous code execution.
- **CoroutineScope**. Coroutines are usually executed inside a CoroutineScope, which defines the scope of the coroutine. CoroutineScope defines the lifecycle of coroutines and provides management of their execution.
- **Dispatchers**. Dispatchers define the context of a coroutine's execution. For example, Dispatchers.Main is used to execute code in the main thread and Dispatchers.IO for background IO operations.
- **Async/Await**. The async and await functions are used for asynchronous operations and waiting for results. They allow you to run multiple coroutines in parallel and get the results of their execution.

### Android Service

In Android, a service is a component of an application that runs in the background even when the user is not interacting with the application. Services are intended to perform long-running operations, handle background tasks, interact with remote components, or provide functionality that can be used by multiple parts of an application or by different applications.

### BroadcastReceiver

In Android, BroadcastReceiver is an application component that allows an application to respond to system broadcast messages, messages sent by other applications, and custom broadcast messages. BroadcastReceiver executes code in response to certain events, such as a change in device status, a new SMS arriving, a change in network connectivity, etc.

## Chapter III

# Project

You will have to design and implement a mobile application for multithreaded message output. The app will allow: - receiving messages using Thread, Handler, HandlerThread, Looper - receiving messages using Coroutine - receiving messages using Service and BroadcastReceiver - displaying messages in TextView - starting to receive messages by Button - stopping to receive messages by Button

## Description and Requirements

- You can use**Material 3** as your design recommendations
- The design of the application must be user-friendly

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

**The following dependencies must be added to the project:** - Kotlin Parcelize

### Task 1. Preparing the Model, ViewBinding and Layout

- Add support for viewBinding to the buildFeatures gradle
- Create a MessageInfo model using data class that includes information about:
  - sending time in seconds
  - the name of the thread in which the sending occurred (use Thread.currentThread().name to get the thread name)
  - the name of the thread (nullable) in which the processing occurred (default value is null)
- Add a Button with the text "Run All" to the MainActivity layout
- Add a Button with the text "Stop All" to the MainActivity layout

### Task 2. Sending a Message with Handler

- Add a TextView to the MainActivity layout with id - handlerMessage
- Create a private function in the MainActivity handlerMessageExample that neither accepts nor returns anything
- Create a Handler.Callback instance in the function and leave the handleMessage body empty
- Create a Handler instance in the function using the created Handler.Callback (deprecated approach)
- A certain number of times and at a certain periodicity do the following in the function:
  - call the postDelayed method of the Handler object
  - create MessageInfo without filling in the last property
  - send Message to handler taking into account MessageInfo
  - MessageInfo must be passed to obj Message
- Add a body to the handleMessage function:
  - retrieve MessageInfo from Message inside the handleMessage
  - use the data class benefits: use the copy function of MessageInfo to fill in the information about the last property
  - use the data class benefits: get a text description of the copied class
  - enter the text description into the TextView text with the id handlerMessage
- The sending periodicity and the specified number of times must be set as constants to the companion object
- The periodicity must be unique
- Add a call of the handlerMessageExample function when you click on the "Run All" button

### Task 3. Sending a Message with Handler Using Looper’s Main Thread

- Add a TextView to the MainActivity layout with id - handlerWithLooperMessage, it should be placed below the previous TextView
- Create a private function in the MainActivity handlerWithLooperMessageExample that neither accepts nor returns anything
- Create a Handler.Callback instance in the function and leave the handleMessage body empty
- Create a Handler instance in the function using the main thread's Looper and the created Handler.Callback (which is the analog of the deprecated Handler creation without Looper)
- Create a Thread in the function, within which while the thread is not interrupted repeat the following with some periodicity (interrupted mechanism):
  - create MessageInfo without filling in the last property
  - send Message to handler taking into account MessageInfo
  - MessageInfo must be passed to obj Message
- Create a property that stores a list of created Threads in MainActivity
- Save the Thread to the list of created Threads in the function
- Run the Thread in a function to execute in another thread
- Add a body to the handleMessage function:
  - retrieve MessageInfo from Message inside the handleMessage
  - use the data class benefits: use the copy function of MessageInfo to fill in the information about the last property
  - use the data class benefits: get a text description of the copied class
  - enter the text description into the TextView text with the id handlerWithLooperMessage
- The sending periodicity should be set in the companion object as a constant
- The periodicity must be unique
- Add logic to interrupt all created Threads and remove all interrupted ones from the list by clicking on the "Stop All" button
- Add a call of the handlerWithLooperMessageExample function when you click on the "Run All" button

### Task 4. Sending a Message with Handler Using Looper Retrieved From HandlerThread

- Add a TextView to the MainActivity layout with id - handlerWithHandlerThreadMessage, it should be placed below the previous TextView
- Create a private function in the MainActivity handlerWithHandlerThreadMessageExample that neither accepts nor returns anything
- Create a HandlerThread instance in the function
- Save the created Thread to the list of Threads in the function
- Run the HandlerThread in a function to execute in another thread
- Create a Handler.Callback instance in the function and leave the handleMessage body empty
- Create a Handler instance in the function using the Looper retrieved from the created HandlerThread and Handler.Callback
- Create a Thread in the function, within which while the thread is not interrupted repeat the following with some periodicity (interrupted mechanism):
  - create MessageInfo without filling in the last property
  - send Message to handler taking into account MessageInfo
  - MessageInfo must be passed to obj Message
- Save the Thread to the list of created Threads in the function
- Run the Thread in a function to execute in another thread
- Add a body to the handleMessage function:
  - retrieve MessageInfo from Message inside the handleMessage
  - use the data class benefits: use the copy function of MessageInfo to fill in the information about the last property
  - use the data class benefits: get a text description of the copied class
  - enter the text description into the TextView text with the id handlerWithHandlerThreadMessage
  - when setting the TextView text, the post function must be used, because it is not accessed from the main thread
- The sending periodicity should be set in the companion object as a constant
- The periodicity must be unique
- Add logic to stop HandlerThread and logic to remove all stopped HandlerThreads from the list of created Threads by clicking on the "Stop All" button
- Add a call of the handlerWithHandlerThreadMessageExample function when you click on the "Run All" button

### Task 5. Sending a Message with Coroutine

- Add a TextView to the MainActivity layout with id - coroutineMessage, it should be placed below the previous TextView
- Create a property that stores a list of created Jobs in MainActivity
- Create a private function in the MainActivity coroutineMessageExample that neither accepts nor returns anything
- Start a new Coroutine in the function using lifecycleScope not on the main thread (use launch and Dispatchers.Default)
- In the function, save the Job of the running Coroutine to the list of created Jobs
- In function in a new coroutine at some interval while the coroutine is active (use coroutineContext):
  - create MessageInfo without filling in the last property
  - use main thread to fill text in TextView (use withContext and Dispatchers.Main):
    - use the data class benefits: use the copy function of MessageInfo to fill in the information about the last property
    - use the data class benefits: get a text description of the copied class
    - enter the text description into the TextView text with the id coroutineMessage
- The sending periodicity should be set in the companion object as a constant
- The periodicity must be unique
- Add a call of the coroutineMessageExample function when you click on the "Run All" button
- Add logic to interrupt all created Jobs and remove all interrupted ones from the list by clicking on the "Stop All" button

### Task 6. Sending a message with Service and BroadcastReceiver

- Create a new MessageService class that inherits from android.app.Service
- The MessageService class must be in a separate file
- Add information about the created service to AndroidManifest
- In MessageService, override the onBind function: just return null
- Add a MessageInfo of Parcelable parent and @Parcelize annotation (to be able to pass the model to Intent's extras)
- Override the onStartCommand function in the MessageService:
  - create a new Thread:
    - call Thread.sleep with some value to emulate service operation
    - create MessageInfo without filling in the last property
    - create an Intent with a unique action
    - put MessageInfo with a unique key into Intent's extras
  - run the Thread in a function to execute in another thread
- The value for service emulation, action and unique key must be set in the companion object MessageService as constants
- Add a TextView to the MainActivity layout with id - coroutineMessage, it should be placed below the previous TextView
- Create a property in the MainActivity that stores a BroadcastReceiver instance with an overridden onReceive function:
  - get MessageInfo by the key specified in MessageService from Intent (use getParcelableExtra)
  - use the data class benefits: use the copy function of MessageInfo to fill in the information about the last property
  - use the data class benefits: get a text description of the copied class
  - enter the text description into the TextView text with the id serviceMessage
- Create an IntentFilter in the companion object by the action specified in the MessageService
- Register BroadcastReceiver with IntentFilter in onResume Activity (use registerReceiver)
- Unregister the BroadcastReceiver in the onPause Activity (use unregisterReceiver)
- Create a private function in the MainActivity serviceMessageExample that neither accepts nor returns anything
- Start a new Coroutine in the function using lifecycleScope not on the main thread (use launch and Dispatchers.Default)
- In the function, save the Job of the running Coroutine to the list of created Jobs
- In function in a new coroutine at some interval while the coroutine is active (use coroutineContext):
  - create an Intent to start the MessageService
  - start MessageService (use startService)
- The sending periodicity should be set in the companion object as a constant
- The periodicity must be unique
- Add a call of the serviceMessageExample function when you click on the "Run All" button