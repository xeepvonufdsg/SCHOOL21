# Tests

💡 [Tap here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave your feedback on the project**. It's anonymous and will help our team make your educational experience better. We recommend completing the survey immediately after the project.

## Contents

- [Information](#information)
  - [Unit Tests](#unit-tests)
  - [Instrumented Tests](#instrumented-tests)
  - [UI Tests](#ui-tests)
  - [JUnit](#junit)
  - [ConcurrentUnit](#concurrentunit)
  - [Robolectric](#robolectric)
  - [Espresso](#espresso)
  - [Mockito](#mockito)
  - [Hamcrest](#hamcrest)
  - [PowerMock](#powermock)
- [Project](#project)
  - [Description and Requirements](#description-and-requirements)
  - [Tasks](#tasks)
    - [Task 0. Setting Up the Testing Environment for a Minigame Application](#task-0-setting-up-the-testing-environment-for-a-minigame-application)
    - [Task 1. Memory Minigame Unit Testing](#task-1-memory-minigame-unit-testing)
    - [Task 2. Reaction Minigame Unit Testing](#task-2-reaction-minigame-unit-testing)
    - [Task 3. Unit Testing the Result of Minigames When the Button is Clicked](#task-3-unit-testing-the-result-of-minigames-when-the-button-is-clicked)
    - [Task 4. Unit Testing of Memory Minigame Card Mappers](#task-4-unit-testing-of-memory-minigame-card-mappers)
    - [Task 5. PreferenceStorage Instrumented Testing](#task-5-preferencestorage-instrumented-testing)
    - [Task 6. CardStorage Instrumented Testing](#task-6-cardstorage-instrumented-testing)
    - [Task 7. Memory Minigame UI Testing](#task-7-memory-minigame-ui-testing)
    - [Task 8. Reaction Minigame UI Testing](#task-8-reaction-minigame-ui-testing)
    - [Task 9. Memory Minigame Progress UI Testing](#task-9-memory-minigame-progress-ui-testing)
    - [Task 10. Reaction Minigame Progress UI Testing](#task-10-reaction-minigame-progress-ui-testing)
    - [Task 11. Settings Fragment UI Testing](#task-11-settings-fragment-ui-testing)
    - [Task 12. Toolbar UI Testing](#task-12-toolbar-ui-testing)
    - [Task 13. Menu Fragment UI Testing](#task-13-menu-fragment-ui-testing)
    - [Task 14. Create fragment Unit testing based on UI fragment testing](#task-14-create-fragment-unit-testing-based-on-UI-fragment-testing)
    - [Task 15. Matcher Implementation with Hamcrest](#task-15-matcher-implementation-with-hamcrest)

Hello! Today's goal is to implement tests for a minigame application.

# Information

### Unit Tests

Perform testing on individual modules that contain a portion of the software logic. There are two main approaches to unit testing: the classical (Detroit) approach and the London approach.
In the classical approach, a module is considered as a unit of program behavior, i.e. it tests the scenario that the program should execute.
In the London approach, a module is considered a separate class, isolated from external dependencies and the rest of the program logic.
One thing that both approaches have in common is that any dependencies that are not implemented in the current program must be swapped. To swap out such dependencies, it is common to use mock and stub objects.

### Instrumented Tests

These tests require a special environment. For mobile device testing, this environment is either a physically connected mobile device or a running mobile device emulator.

### UI Tests

Perform tests on the software user interface. UI testing simulates user interaction with the program interface.
Testing focuses primarily on the visual elements of the interface.

### JUnit

A library for automating software unit testing.

### ConcurrentUnit

A library for unit testing asynchronous and multithreaded code. It is used when you want to test the interaction between threads or the behavior of asynchronous code.

### Robolectric

A library that turns instrumented tests into unit tests. Robolectric can speed up the process of running instrumented tests by replacing a specialized environment with its own tools.
However, there may be cases where Robolectric is not able to fully replicate a specific functional test environment. Can be used with JUnit.

### Espresso

A library for writing UI tests. Testing is performed on view elements such as `View`.
Implies that only one specific event can occur at a time while the user action is pending.

### Mockito

A library that allows you to create mock elements needed to test software logic. A mock element is considered to be a stub element, i.e. an element created without an implementation.
Mock is used in tests where you need an element that participates in the creation of the tested object.

### Hamcrest

A library for flexibly defining the match between the expected result and the resulting output. Provides only a set of matches between data and cannot be used separately from libraries directly aimed at testing (e.g. JUnit).

### PowerMock

A library that allows you to create mock elements just like Mockito. Unlike Mockito, PowerMock allows you to define private fields, final classes, static methods, etc.

# Project

In this project, you will need to implement unit and UI tests for a minigame application that you've already implemented.
Your task is to test the application menu and settings fragments and the toolbar. You will also need to test key elements of the minigame logic and the games themselves.

### Description and Requirements

- The program code must be located in the src folder and must not contradict the following requirements.
- The tested code is taken from the minigames application.
- Each task must be in a separate file with a name corresponding to the topic of the task.
- Tests that include Android tools must be located in the androidTest folder.
- Tests that do not contain Android tools must be located in the test folder.

**For the implementation of mobile application tests, you need to use:**

- Android Studio 2023.1.1
- Kotlin 1.9.0
- Android SDK 34
- Gradle 8.2 (dependency management)
- Material 3 (creating a user interface)

## Tasks

### Task 0. Setting Up the Testing Environment for a Minigame Application

- Select File->New->New Project... in Android Studio.
- Select Phone and Tablet and Empty Views Activity.
- Enter the name of the application — nit N (where N is the unit number).
- Select development language — Kotlin.
- Select build configuration language — Kotlin DSL.
- Copy the code from the minigame application.
- Correct the package names in the copied files.
- The program code must be in the src folder.

**The following dependencies need to be added to the project:**.

- androidx.test.espresso:espresso-core:3.4.0
- androidx.test:runner:1.4.0
- androidx.test:rules:1.4.0
- junit:junit:4.13.2
- androidx.test:core:1.6.0
- org.mockito:mockito-core:4.2.0
- org.mockito.kotlin:mockito-kotlin:5.1.0
- org.hamcrest:hamcrest:2.1
- org.powermock:powermock-core:2.0.9
- net.jodah:concurrentunit:0.4.0
- org.robolectric:robolectric:4.11.1

### Task 1. Memory Minigame Unit Testing

1. Implement unit tests for the memory game:
   - Tests must be done in a classical style.
   - Test to check the uniqueness of the generated cards.
   - Test to check the length of the generated string.
   - Tests to verify that the card you are looking for matches the card you are handing over .
   - Use the Mockito.mock() method to swap the dependencies used by the ViewModel of the memory minigame fragment.
   - Use the Mockito.when() and Mockito.thenReturn() methods to set the behavior of the mock object.
   - In Mockito.when(), specify the mock object method involved in the tested logic of the response minigame.
   - Specify in Mockito.thenReturn() the data that the mock object method specified in Mockito.when() should return.
   - Specify the @RunWith(PowerMockRunner::class) annotation before the signature of the function that executes the test to use PowerMock.
   - Use the PowerMock.mockStatic() method before the PowerMock.when() and PowerMock.thenReturn() methods to specify the behavior of the static method.
   - Use the PowerMock.doReturn() and PowerMock.when() methods to specify the behavior of a private method.
   - Specify the class that contains the static method to be tested in PowerMock.mockStatic().
   - Specify the mock object method in Mockito.when() that is involved in the tested logic of the response minigame.
   - In PowerMock.when(), specify the mock object and mock object method involved in the tested Reaction Minigame logic.
   - In PowerMock.when(), specify the mock object and the mock object method involved in the tested reaction minigame logic.
   - When testing a static method, specify in PowerMock.thenReturn() the data that the mock object method specified in PowerMock.when() should return.
   - When testing a private method, specify in PowerMock.doReturn() the data that the mock object method specified in PowerMock.when() should return.

### Task 2. Reaction Minigame Unit Testing

1. Implement unit tests for the Reaction game:
   - Tests must be done in a classic style.
   - Test for generated timer time.
   - Test for a false start.
   - First click test.

### Task 3. Unit Testing the Result of Minigames When the Button is Clicked

1. Implement unit tests that check the result of minigames when the button is clicked:
   - Tests must be done in a classical style.
   - Test the correctness of the result after clicking the button in the reaction game before it starts.
   - Test the correctness of the result after clicking the button in the reaction game during the game.
   - Test the correctness of the result after clicking the button in the reaction game after the game.
   - Test the correctness of the result after clicking the button in the memory game before it starts.
   - Test the correctness of the result after clicking the button in the Memory game during the game.
   - Test the correctness of the result after clicking the button in the memory game after the game.
   - Use the await() method called from the Waiter class instance of the ConcurrentUnit library to lock the main thread during testing.
   - Use the resume() method called from the Waiter class instance of the ConcurrentUnit library to unlock the main thread during testing.
   - Use the assertEquals() method called from the Waiter class instance of the ConcurrentUnit library to check the result of execution after clicking the button.

### Task 4. Unit Testing the Memory Minigame Card Mapper

1. Implement unit tests for the memory minigame card mapper:
   - Tests must be done in London style.
   - Tests for correct conversion CardEntity <-> CardData.
   - Tests for correct conversion CardData <-> CardView.

### Task 5. PreferenceStorage Instrumented Testing

1. Implement PreferenceStorage instrumented testing:
   - Tests must be done in a classical style.
   - Tests for saving and loading application mode values.
   - Tests for saving and loading the shape values of game cards in the Memory game.
   - Tests to save and load the border color values of the cards in the Memory game.
   - Tests for saving and loading text style values.
   - An actual PreferenceStorage instance must be created.
   - Must create an actual PreferenceService instance.
   - A current PreferenceRepository instance must be created.
   - PreferenceStorage tests must be run with PreferenceRepository.

### Task 6. CardStorage Instrumented Testing

1. Implement CardStorage instrumented testing:
   - Tests need to be done in a classical style.
   - Tests for adding a CardEntity instance.
   - Tests to add a list of CardEntity instances.
   - Tests for updating a CardEntity instance.
   - Tests to update a list of CardEntity instances.
   - Tests for deleting a CardEntity instance.
   - Tests for retrieving a list of CardEntity instances.
   - An actual CardStorage instance needs to be created.
   - An actual CardService instance needs to be created.
   - A current CardRepository instance must be created.
   - CardStorage tests must be run with CardRepository.

### Task 7. Memory Minigame UI Testing

1. Implement UI tests for the memory game:
   - Test for the "Start" button before the game starts.
   - Test for the "Restart" button during the game.
   - Test for the "Restart" button after the game.
   - Test for the absence of the searched card before the game starts.
   - Test for the absence of cards before the game starts.
   - Test for the absence of the card you are looking for while the timer is running.
   - Test for the presence of the card while the timer is running.
   - Test for the appearance of the sought card when the timer stops running.
   - Test for coloring the cards while the timer is running.
   - Test for changing the color of a card if it turns out to be the card you are looking for.
   - Test for changing the color of a card when it turns out not to be the card you are looking for.
   - When testing RecyclerView, use custom matchers to compare the obtained result with the expected result.
   - Use the Espresso.onView() method to perform actions on the widget located on the fragment.
   - Use the ViewMatchers.withId() method to specify the widget on which the action will be performed.
   - Use the Espresso.onView().perform() method to specify an action to be performed on the widget.
   - Use the Espresso.onView().check() method to check if the widget parameter matches.

### Task 8. Reaction Minigame UI Testing

1. Implement UI tests for the Reaction game:
   - Test the "Start" button text before the game starts.
   - Test for the "Restart" button text during the game.
   - Test for the "Restart" button text after the game.
   - Test for area color before game start.
   - Test for area color during the game.
   - Test for area color after the game.
   - Use the Espresso.onView() method to perform actions on the widget on the fragment.
   - Use the ViewMatchers.withId() method to specify the widget on which to perform the action.
   - Use the Espresso.onView().perform() method to specify an action to be performed on the widget.
   - Use the Espresso.onView().check() method to check if the widget parameter matches.

### Task 9. Memory Minigame Progress UI Testing

1. Implement UI tests that simulate the progress of a memory game:
   - Click Test while the timer is running:
   - Test the correct identification of the card you are looking for.
   - Test for incorrect identification of the card you are looking for.
   - Use PowerMock to exchange data.
   - Use the Espresso.onView() method to perform actions on the widget on the fragment.
   - Use the ViewMatchers.withId() method to specify the widget on which to perform the action.
   - Use the Espresso.onView().perform() method to specify an action to be performed on the widget.
   - Use the Espresso.onView().check() method to check if the widget parameter matches

### Task 10. Reaction Minigame Progress UI Testing

1. Implement UI tests that simulate the progress of a reaction game
   - Test for a false start
   - Test for first player to win
   - Test for second player to win
   - Use the Espresso.onView() method to perform actions on the widget on the fragment
   - Use the ViewMatchers.withId() method to specify the widget on which to perform the action
   - Use the Espresso.onView().perform() method to specify an action to be performed on the widget.
   - Use the Espresso.onView().check() method to check if the widget parameter matches.

### Task 11. Settings Fragment UI Testing

1. Implement UI tests for setting changes:
   - Tests for changing the application mode.
   - Tests for changing the shape of game cards in a memory game.
   - Tests for changing the shape of cards in a memory game.
   - Tests for changing the text style.
   - Using the Espresso.onView() method to perform actions on the widget located on the fragment.
   - Use the ViewMatchers.withId() method to specify the widget on which to perform the action.
   - Use the Espresso.onView().perform() method to specify an action to be performed on the widget.
   - Use the Espresso.onView().check() method to check if the widget parameter matches.

### Task 12. Toolbar UI Testing

1. Implement UI tests for setting changes:
   - Tests for changing the application mode.
   - Transition test to the Settings fragment.
   - Use the Espresso.onView() method to perform actions on the widget located on the fragment.
   - Use the ViewMatchers.withId() method to specify the widget on which to perform the action.
   - Use the Espresso.onView().perform() method to specify an action to be performed on the widget.
   - Use the Espresso.onView().check() method to check if the widget parameter matches.

### Task 13. Menu Fragment UI Testing

1. Implement menu fragment UI tests:
   - Transition test to a memory game fragment.
   - Transition test to a response game fragment.
   - Use the Espresso.onView() method to perform actions on the widget on the fragment.
   - Use the ViewMatchers.withId() method to specify the widget on which to perform the action.
   - Use the Espresso.onView().perform() method to specify an action to be performed on the widget.
   - Use the Espresso.onView().check() method to check if the widget parameter matches.

### Task 14. Create Fragment Unit Testing Based on UI Fragment Testing

1. Turn UI tests of menu and settings fragments into Unit tests:
   - Add the @RunWith(RobolectricTestRunner::class) annotation in front of the class with tests.
   - Use the Robolectric.buildActivity() method to prepare the activity.
   - Use the Robolectric.startFragment() method to test the fragment.
   - Use the findViewById() method to retrieve the widget fragment.

### Task 15. Matcher Implementation Using Hamcrest

1. Implement custom matchers using the Hamcrest library:
   - Implement Hamcrest matchers in unit tests of the memory game.
   - Implement Hamcrest matchers in unit tests of the reaction game.
   - Custom matchers must inherit from the TypeSafeMatcher() class.
   - You must override describeMismatchSafely(item: Description) for custom matchers.
   - You must override the describeMismatchSafely(item: T) method for custom matchers.
   - You must override the describeMismatchSafely(item: T, mismatchDescription: Description) method for custom matchers.