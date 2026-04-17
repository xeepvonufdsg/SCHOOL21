# Project Build for Publishing Using Gradle

Summary: In this project, you'll simulate the process of testing, building, and publishing applications to the store using Gradle.

💡 [Tap here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave your feedback on the project**. It's anonymous and will help our team make your educational experience better. We recommend completing the survey immediately after the project.

# Contents

- [Chapter I](#chapter-i)
  - [Introduction](#introduction)
- [Chapter II](#chapter-ii)
  - [Gradle tasks](#gradle-tasks)
- [Chapter III](#chapter-iii)
  - [Project](#project)
  - [Description and Requirements](#description-and-requirements)
- [Chapter IV](#chapter-iv)
  - [Tasks](#tasks)
  - [Chapter 1. Signature of the Application](#chapter-1-signature-of-the-application)
    - [Task 1. Creation of a Signature](#chapter-1-creation-of-the-signature)
  - [Chapter 2. Configuring the Application Build](#chapter-2-configuring-the-application- build)
    - [Task 2. Automatic Update of the Application Version](#task-2-automatic-update-of-the-application-version)
    - [Task 3. Creating a Gradle Build Task](#task-3-creating-a-gradle-build-task)
  - [Chapter 3. Uploading the App to a Telegram Channel](#chapter-3-uploading-the-app to-a-telegram-channel)
    - [Task 4. Getting a Telegram Bot Token](#task-4-getting-a-telegram Bot Token)
    - [Task 5. Creating Your Own Gradle Plugin to Publish Your Application](#task-5-creating-your-own-gradle-plugin-to-publish-your-application)
    - [Task 6. Connecting Your Own Plugin and Publishing an Application](#task-6-connecting-your-own-plugin-and-publishing-an-application)

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

### Gradle tasks

For Android developers, creating custom Gradle tasks is a way to automate many of the mundane tasks involved in developing and publishing applications and libraries.
For example, the `maven-publish` plugin allows you to automate the process of publishing libraries to repositories.
Another example of a mundane task might be consistently updating the version of an app when it is published to stores. You can tie the version to some constant changing parameters - commit number, time - instead of manually updating it.
Gradle has a large set of standard functions that allow you to copy and archive files, build a dependency graph of tasks.
If you need to create your own type of tasks or module configuration, you can create your own Gradle Plugin where you can write the necessary code in Kotlin/Java/Groovy. For example, the [maven-publish](materials/references.md#gradle-maven-publish-plugin) plugin was created to simplify the description of uploading libraries to remote repositories.

## Chapter III

# Project

In this project, you will create Gradle tasks to consistently test, build, and publish an app to a Telegram channel that will help you understand what to do when you build an app in CI/CD.

### Description and Requirements

- The program code must be located in the src folder and not contradict the requirements below
- You can use [Material 3](materials/references.md#material-3-design) as your design guidelines
- The design of the application must be user-friendly
- You need to use the previous project from Unit 6

**For the implementation of mobile application tests, you need to use:**

- Android Studio 2023.1.1
- Kotlin 1.9.0
- Android SDK 34
- Gradle 8.2 (dependency management)
- Material 3 (creating a user interface)

**The following dependencies must be added to the project:**

- io.ktor:ktor-client-android:2.3.7
- io.ktor:ktor-client-okhttp:2.3.7
- plugin kotlin("plugin.serialization")

## Chapter IV

## Tasks

### Chapter 1. Signature of the Application

#### Task 1. Creation of a Signature

1. Go to Build -> Generate Signed Bundle/Apk
2. Create a signature for your app in the appeared window and save the jks file to previously created signing directory. You can see the example of creating and adding the signature [here](materials/references.md#android-application-signing)
3. Add the signature password to the local.properties file as a variable. It does not need to be explicitly specified in build.gradle. Make sure the local.properties file is added to .gitignore, do not upload this file to a remote repository
4. Add a signingConfigs block to the app/build.gradle file at the android level. You can see an example in the [documentation](materials/references.md#android-application-signing-configs). Also Android Studio can add this block automatically if you generate a signed apk using the Build -> Generate Signed Bundle/Apk tab
5. Make gradle sync and assembleRelease. If the signature description is correct, the app-release.apk file will be located in the app/build/outputs/apk/release directory. If the signature description is incorrect, the app-release-unsigned.apk file will be created.

### Chapter 2. Configuring the Application Build

#### Task 2. Automatic Update of the Application Version

1. In build.gradle, create a function that generates a version number for the application that will allow the system to distinguish versions. The result of the function should be a number that matches the yymmddhh format (yy - last two digits of the year, mm - two digits of the month, dd - two digits of the day, hh - two digits of the hour). An example: date and time 07.02.2024 14:21 -> 24020714
2. Save the value returned by the function to the versionCode property inside the android-defaultConfig block
3. Generate the version of the application that will be displayed in the settings. The value must be a string in the "1.0.$date" format, where date is the versionCode value. Save the value to the versionName property inside the android-defaultConfig block

#### Task 3. Creating a Gradle Build Task

1. Create a Gradle `buildRelease` task with `Copy::class` type in build.gradle
2. The `test` and `assembleRelease` tasks must be automatically called before `buildRelease` is executed
3. Add name validation of the builT apk. If it does not match `app-release.apk`, then print an error with the text "Apk is not signed"
4. The built apk from build/outputs/apk/release must be moved to the release directory in the root of the project named `game-$version.apk`, where version is the android.defaultConfig.versionName parameter. The release directory must be created during the build process, or cleared if it already exists
5. If the release directory is cleared, the console must display the text "Directory is cleared", otherwise "The directory was created"

### Chapter 3. Uploading the app to a Telegram channel

#### Task 4. Getting a Telegram Bot Token

1. Create a new Telegram bot using @BotFather (Telegram bot)
2. Get the token of the created bot using @BotFather to access the Bot API
3. Create a Telegram channel to publish the app and add your bot there as an admin with publishing privileges
4. Add the bot token to the local.properties property

#### Task 5. Creating Your Own Gradle Plugin to Publish Your Application

1. Add plugin directory to the project. It will exist as a separate module of creating your own plugin for Gradle
2. Connect the module in settings.gradle using the includeBuild function
3. Create a Kotlin class `PublishFile` inside plugin/src/main/java, which will inherit from org.gradle.api.DefaultTask, the class for creating Gradle API tasks
4. Create an input parameter inside `PublishFile` for the bot token. Use [documentation](materials/references.md#gradle-tasks) to write Gradle tasks
5. Create a function inside `PublishFile` with the annotation `@TaskAction` in which you describe how to publish a file to a Telegram channel using Ktor. The published APK must be taken from the release directory in the root of the project
6. Create a Kotlin class PushPlugin that will inherit from `Plugin<Project>`
7. Override the `apply` method in it and register the created `PublishFile` task
8. Identify plugin id and implementationClass - PushPlugin in plugin/build.gradle

#### Task 6. Connecting Your Own Plugin and Publishing an Application

1. Add the plugin created in app/build.gradle to plugins
2. Implement a task called `pushTg` with the created `PublishFile` type, which takes a token from local.properties or an environment variable as input
3. Make `pushTg` dependent on the previously created `buildRelease` task
4. Run the `pushTg` task. Check its execution and the file upload to your Telegram channel
5. Check the installation of the published app in the Telegram channel and share the result with your friends

💡 [Tap here](https://forms.yandex.ru/cloud/662bb076e010dbcd1dd04d4f/) **to leave your feedback on the project**. Product Team really tries to make your educational experience better.