# Building Interfaces with SwiftUI

💡 [Tap here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave your feedback on the project**. It's anonymous and will help our team make your educational experience better. We recommend completing the survey immediately after the project.

## Contents

- [Chapter 1](#chapter-1)
  - [Intro](#intro)
- [Chapter 2](#chapter-2)
  - [SwiftUI](#swiftui)
- [Chapter 3](#chapter-3)
  - [Layout in SwiftUI](#layout-in-swiftui)
- [Chapter 4](#chapter-4)
  - [SwiftUI Application Lifecycle](#swiftui-application-lifecycle)
- [Chapter 5](#chapter-5)
  - [MVVM](#mvvm)
- [Chapter 6](#chapter-6)
  - [Assignment](#assignment)
  - [Additional Tasks](#additional-tasks-)

## Introduction

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

## Chapter 1

**Greetings!**

Your task is to familliarize yourself with the basics of adaptive layout for iOS applications using the new declarative framework [SwiftUI](https://developer.apple.com/xcode/swiftui/).

Be sure to read the entire document before starting the assignment, and only then proceed with the implementation.

### Intro

Mobile development is much younger than web development, and the major trends and approaches reach it with some delay. In web development, declarative layout has existed almost from the beginning, while in mobile development, it has appeared relatively recently. It is much easier and faster to create interfaces on it, which is why Apple decided to release the new framework [SwiftUI](https://developer.apple.com/xcode/swiftui/).

The main advantages of SwiftUI are its declarativity and support for all iOS, iPadOS, macOS, watchOS, and tvOS platforms at once.

Apple has long been moving toward a unified technology stack for development across all of its operating systems. This was evident in the case of Mac OS. Despite the fact that programming for iOS became popular almost immediately with the advent of mobile devices, programming for Mac OS remained very specialized. It was difficult to find Mac OS programmers in the market, and they were expensive. In addition, the most popular platform for personal computers was Windows.

To attract developers and begin the gradual integration of its platforms into a single ecosystem, Apple added the ability to run the same application on different platforms. The final step was the introduction of a unified processor architecture across all devices and the move away from Intel architectures in favor of their own ARM processors.

SwiftUI code is more readable and easier to write, and Apple aims to make this framework the target solution for all platforms, completely replacing UIKit.

## Chapter 2

### SwiftUI

**[SwiftUI](https://developer.apple.com/xcode/swiftui/)** — a framework released by Apple in 2019. Its main advantages are its declarativity and support for all iOS, iPadOS, macOS, watchOS, and tvOS platforms at once.

The main difference with the imperative approach is that instead of manually creating graphical objects, we describe at a high level what the final result should look like. In UIKit, we manage graphical objects directly, while in SwiftUI, we only describe what those objects will look like.

Apple developers understood that implementing a graphical framework with a new paradigm is a long and labor-intensive process. So they added mutual compatibility between SwiftUI and UIKit. This means that components written in UIKit can be used in SwiftUI, and SwiftUI components can be used in UIKit. This is necessary because initially SwiftUI did not have enough functionality to satisfy all the developers' needs.

## Chapter 3

### Layout in SwiftUI

When working with graphical elements in SwiftUI, you will almost forget about classes. Also, forget about inheritance and passing objects by reference. Remember, in Swift, structures are value types and are passed as a copy of the object.

Unlike UIKit, which was used in conjunction with [storyboard](https://developer.apple.com/library/archive/documentation/General/Conceptual/Devpedia-CocoaApp/Storyboard.html), SwiftUI is based entirely on program code. However, the syntax is very easy to understand, and the Automatic Preview allows you to quickly check your project.

When developing interfaces in SwiftUI, forget about the Auto-Layout mechanism and its main principle based on constraints. Instead there are Stacks ([HStack](https://developer.apple.com/documentation/swiftui/hstack), [VStack](https://developer.apple.com/documentation/swiftui/vstack), [ZStack](https://developer.apple.com/documentation/swiftui/zstack)), not to be confused with [UIStackView](https://developer.apple.com/documentation/uikit/uistackview) from [UIKit](https://developer.apple.com/documentation/uikit). Layout on Stacks is somewhat similar to layout on [div](https://www.w3schools.com/tags/tag_div.ASP) in [HTML](https://en.wikipedia.org/wiki/HTML), or Row and Column in [Compose](https://developer.android.com/jetpack/compose), or [Row](https://api.flutter.dev/flutter/widgets/Row-class.html) and [Column](https://api.flutter.dev/flutter/widgets/Column-class.html) in [Flutter](https://flutter.dev/).

When we layout on Stacks, we simply combine and nest containers into each other (vertically, horizontally).

The advantage is that it doesn't matter how deep the nesting of elements is, because the system will still optimize the final rendering at compile time (remember that in SwiftUI we only describe graphical elements, and the system itself decides how and when to create them).

## Chapter 4

### SwiftUI Application Lifecycle

When you created a project in UIKit and Storyboard, the AppDelegate file was automatically created as the entry point to the application.

In SwiftUI, the developers have introduced a new more declarative concept based on modifiers. We create a structure that supports the [App](https://developer.apple.com/documentation/swiftui/app) protocol and mark it as the entry point to the application using the @main modifier.

This allows the application to be written in a single declarative style. The easiest way to check how this works is to create a new, separate project and select SwiftUI as the main framework for development. Apple will automatically generate the necessary files and entry points.

## Chapter 5

### MVVM

MVVM is an architectural pattern that divides application components into three main elements: Model, View, and ViewModel. MVVM is used in software development to provide more efficient management of data and user interfaces.

- **Model:** Provides the data and business logic of the application. The model responds to requests from the ViewModel and updates its state accordingly. It has no binding to the UI.
- **View:** Displays the data provided by the ViewModel and is responsible for rendering the user interface. The View can handle user actions and interact with the ViewModel to retrieve and update data.
- **ViewModel:** Contains presentation logic and handles user interaction. The ViewModel accepts requests from the View, updates the Model, and manages the data needed to properly display of the user interface. It provides the data that the View uses for display and responds to changes in the Model.

The key aspect of MVVM is that the ViewModel serves as the link between the Model and the View, providing separation of the application logic from the user interface. This also allows the user interface state to be more effectively managed and updated in response to data changes in the Model.

Implementing the MVVM pattern on iOS is very convenient using the reactive programming framework [Combine](https://developer.apple.com/documentation/combine).

### **Literature**

- [Basics of Building Layout with Stack](https://developer.apple.com/documentation/swiftui/building-layouts-with-stack-views).
- [WWDC on SwiftUI Layout](https://developer.apple.com/videos/play/wwdc2022/10056/).
- [iOS Design Patterns](https://habr.com/ru/companies/badoo/articles/281162/).
- [Integration of SwitUI and UIKit](https://developer.apple.com/tutorials/swiftui/interfacing-with-uikit).
- [Article on Application Performance Monitoring](https://medium.com/@peteliev/diagnose-and-solve-performance-problem-with-xcode-instruments-5c25c27f21d5).
- [Dark Mode in SwiftUI](https://zappycode.com/tutorials/dark-mode-in-swiftui).
- [Article on Design System](https://habr.com/ru/companies/innotech/articles/703176/).

## Chapter 6

## Assignment

Your task is to create the layout of new screens for a social network (layout only) in SwiftUI and integrate existing screens written in UIKit.

**General Requirements:**

- Do not use third-party libraries.
- Use SwiftUI for developing new components.
- Ensure layout adaptability for various screen sizes.
- Eliminate the AppDelegate.swift file from the project.
- Eliminate all [UITabbarController](https://developer.apple.com/documentation/uikit/uitabbarcontroller) / [UINavigationController](https://developer.apple.com/documentation/uikit/uinavigationcontroller) from the project.
- Use the MVVM pattern at the UI layer (in new screens).
- Use mock data from the MockService.swift file.

### Task I: Lifecycle (SwiftUI Approach)

- Change the application lifecycle to the SwiftUI approach.
- The application should not contain the outdated AppDelegate.swift file.
- The entry point should be a structure supporting the [App](https://developer.apple.com/documentation/swiftui/app) protocol.

### Task II: Profile Screen:

- Create a user profile screen in SwiftUI, displaying basic information (first name, last name, age, city, nickname).
- Place a placeholder at the user's avatar location.

### Task III: Feed Screen:

- Redesign the feed screen, but now in SwiftUI.
- Include the feed title, image, and text of each post.
- Add control elements such as a **Like** button, comment count, and view count.
- When clicking on a post in the feed, a full-screen post page should open (a placeholder page is sufficient).

### Task IV: Integration of Friends Screen

- Integrate the friends screen, written in UIKit, into SwiftUI.
- The screen should be integrated without rewriting it in SwiftUI.

### Task V: Integration of Custom Spinner

- Integrate the custom loading spinner from the previous lesson into all necessary screens (feed, profile).
- Implement the ability to use the spinner on UIKit in any element on SwiftUI.

### Screen Map:

![](misc/images/ui.png)

## Additional Tasks (\*):

### Task VI: Dark Theme

- Add support for dark mode in the application.

### Task VII: Parallax Header

- Add a parallax effect (enlargement/compression) to the user avatar when scrolling up/down.

### Task VIII: Design System

- Extract all common visual components reused in the application into a separate folder or module (create a mini design system).

### Task IX: Pull to Refresh

- Add [pull to refresh](https://ui-patterns.com/patterns/pull-to-refresh) on the user and feed screens.

### Task X: Detailed Feed Screen

- Implement a detailed post screen in the feed.

#### Task XI: Performance

- Achieve stable 60/120 FPS in the news feed.

[Tap here](https://forms.yandex.ru/cloud/65fc45b9068ff011ddd03e11/) **to leave your feedback on the project**. Product Team really tries to make your educational experience better.