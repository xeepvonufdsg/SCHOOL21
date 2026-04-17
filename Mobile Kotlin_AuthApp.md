# Android. Mobile application

Development and implementation of a mobile application for Android operating system in the Kotlin language.

💡 [Tap here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave your feedback on the project**. It's anonymous and will help our team make your educational experience better. We recommend completing the survey immediately after the project.

## Contents

1. [Chapter 1](#chapter-1)
2. [Chapter 2](#chapter-2) \
   2.1. [Rules](#rules) \
   2.2. [Information](#information)
3. [Chapter 3](#chapter-3) \
   3.1. [Part 1. Description and requirements](#part-1-description-%D0%B8-requirements) \
   3.2. [Part 2. Data and business logic layers implementation](#part-2-data-and-buisness-logic-layers-implementation) \
   3.3. [Part 3. User interface layer implementation](#part-3-user-interface-layer-implementation)

## Chapter 1

## Introduction

You will be developing and implementing a client mobile application to display information about objects using the MVVM pattern. The application will support:

- authorization by login and password (basic auth)
- authorization via a third-party service (OAuth2)
- automatic authorization
- the ability to register
- getting information about an object using tokens
- saving the received information and tokens into the database
- displaying information about an object
- exit to authorization screen

## Chapter 2

## Rules

- Source code must be uploaded to a git repository
- Do you have a question? Ask your neighbor on the right. Otherwise, try with your neighbor on the left.
- Your reference guide: peers / internet / documentation

## Information

### Authorization

Authorization tools control the access of legal users to system resources, giving each of them exactly the rights that have been assigned to them by the administrator.

### Identification, authentication, authorization

Identification is a procedure in which the subject is identified by its unique property, which will be uniquely recognized in the information system.

Authentication is a procedure of checking the authenticity, for example, by comparing the password entered by the user with the password stored in the system.

Authorization means granting a certain person or group of people the rights to perform a certain set of actions.

### Authorization with login and password

This method assumes that the user must provide a login and password to successfully identify and authenticate to the system. The login and password pair is set by the user when he registers in the system.
If authorization on the server is successful, the user is given the rights to perform the available requests.

The client sends a request to the server and receives an "Unauthorized" message as a response, along with information about the authorization order.
After successful authorization, the "Authorization" header is automatically added to each subsequent client request ([forming the authorization header](https://datatracker.ietf.org/doc/html/rfc7617)), which passes the client's data for authentication by the server.

![](misc/images/Auth.png)

There are [other authorization methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication#authentication_schemes).

### OAuth2

OAuth2 is an authorization protocol that allows an application to grant rights to access user data on another service. The protocol eliminates the need to trust the application with a username and password, and allows a limited set of rights to be granted.

Special "keys" that perform authorization automatically — tokens — are used so that the user does not have to go through authorization before performing each action.

### Token, session token, refresh token

A **Token** is a unique sequence of characters that replaces a user's login and password to prevent confidential information leaks. Tokens have a certain validity period, after which they stop working.

**Session token** grants the user the rights to perform available actions during the session. It is reusable and has a short validity period.

**Refresh token** extends the validity period of a session token. It is a disposable and has a long validity period.

### How does OAuth2 work?

1. The user clicks the authorization button.
2. A server redirects the user from OAuth2 to authorize an external service.
3. The user enters his credentials and also accepts permissions.
4. A server with OAuth2 redirects the user back to the application using authorization code.
5. The mobile app sends an authorization code to the server with OAuth2 to receive the tokens.
6. The server with OAuth2 returns tokens.

You can find more information [here](https://auth0.com/docs/get-started/authentication-and-authorization-flow/authorization-code-flow).

![](misc/images/OAuth2.png)

### MVVM pattern

The MVVM (Model-View-ViewModel) is an architectural pattern for designing an application. It consists of three components: business logic model (Model), view model (ViewModel) and view (View).
The bindings mechanism provides a link between the View and ViewModel components.

#### Business logic model

Describes the data used in the application. Models can contain logic directly linked by this data, such as validation logic for model properties. At the same time, the model should not contain any logic related to data mapping and interaction with visual controls.

#### View

Defines the visual interface through which the user interacts with the application.
The view passes the user's actions to the view model via commands.

#### View model

Links the view and the business logic model via the data binding mechanism. If property values change in the business logic model, the displayed data in the view automatically changes, although the business logic model and the view are not directly linked.

It contains the logic for retrieving data from the business logic model, which is then transferred to the view. The view model defines the logic for updating the data in the business logic model.

Visual components, such as the entry field, do not use events, and the view interacts with the view model via commands. For example, a user wants to save data entered in a text field. He clicks a button and thereby sends a command to the view model. And the view model receives the data and updates the model accordingly.

![](misc/images/MVVM.png)

## Chapter 3

### Part 1. Description and requirements

**General requirements:**

- The program code must be located in the src folder and not contradict the requirements below
- As a design reference, you can use [Material 2](https://m2.material.io/develop/android)
- The application design must be intuitive

**To implement a mobile application, you need to use the following standard tools:**

- Android Studio 2022.1.1
- Kotlin 1.8.10
- Android SDK 32
- Gradle 7.6 (dependency management)
- Material 2 (creating a user interface)

**The following dependencies should be added to the project:**

- Room 2.5.0 (working with the database)
- Kotlinx.Serialization 1.4.1 (JSON serialization)
- Retrofit 2.9.0 (networking)
- Dagger 2.45 (dependency injection)
- Kotlin Coroutines 1.6.4 (asynchronous operation)

**The application must meet the following requirements in terms of architecture:**

- Use of the MVVM architecture pattern
- Presence of three main application layers: data, business logic and user interface

### Part 2. Data and business logic layers implementation

**Implementation requirements:**

1. Data layer (datasource)
   - Database
     - Separate models (Entity) for the database tables must be created
     - The model name must be formed as a NameEntity (e.g. UserEntity)
     - The CRUD operations must be implemented
   - Network service
     - Separate models (Dto) with a serializer must be created
     - The model name must be formed as NameDto (e.g. UserDto)
2. Business logic layer (domain)
   - Separate models must be created (Domain)
   - The name of the model must be formed as a Name (e.g. User)
   - Mappers must be implemented for Dto<-> Domain, Entity<->Domain
   - Mappers must be formed as [extension methods](https://kotlinlang.org/docs/extensions.html)
   - A repository for working with the database must be implemented
   - A repository for network service must be implemented
3. Dependencies Implementation (DI)

You can check whether the data is correctly retrieved and saved by logging

### Part 3. User interface layer implementation

In this part you need:

1. User interface layer (presentation)
   - Authorization screen
     - There must be a field for entering a login and a field for entering a password
     - The field with the password must have an option to hide the characters you enter
     - Sign up button
       - Clicking the button must take you to the sign up screen
     - Button for authorization with a pair of login and password
       - When you click the button, the data for the login and password fields must be validated
       - If there is a validation error, a pop-up notification must display
       - If the validation is successful, then the authorization request must be sent to the server
       - If there is an authorization error, a pop-up notification with the reason must display
       - If the authorization is successful, the login and password must be saved in the database, and the screen with information about the object must display
       - The operation of retrieving data from the server must be performed asynchronously and not block the main thread
       - The operation of saving data from the server must be performed asynchronously and not block the main thread
     - Button for OAuth2 authorization
       - When you click on the button, it must take you to the third-party service authorization
       - If there is an authorization error, a pop-up notification with the reason must display
       - If the authorization is successful, the refresh token and the session token must be saved in the database, and it must also take you to the screen with information about the object
       - The operation of retrieving data from the server must be performed asynchronously and not block the main thread
       - The operation of saving data from the server must be performed asynchronously and not block the main thread
     - Automatic authorization
       - If the session and refresh tokens are saved in the database, check their validity
       - If there is a validation error, a pop-up notification must display
       - If validation is successful, send a request to update the session token to the server using the refresh token
       - If the update fails, a pop-up notification with the reason must display
       - If the update is successful, it should take you to the screen with information about the object
       - The operation of sending data to the server must be performed asynchronously and not block the main thread
     - Progress indicator
       - A progress indicator must be displayed during authorization and verification of the session token
       - If there is an error or successful authorization, the progress indicator must be hidden
     - Horizontal and vertical orientation of the device must be supported
   - Sign up screen
     - There must be a field for entering a login, a field for entering a password and a field for re-entering the password to confirm
     - The fields with password must have the ability to hide the characters you enter
     - Sign up Button
       - When you click sign up, a request must be sent to the server to register
       - Successful registration must take you to the authorization screen
       - If there is an error, a pop-up notification with the reason must display
       - The operation of sending data to the server must be performed asynchronously and not block the main thread
   - Screen with information about the object
     - Detailed information about the object
       - Full information about the object must be displayed
       - The data must be downloaded from the network to the database
       - The operation of loading data from the network to the database must be performed asynchronously and not block the main thread
       - The data to be displayed must be retrieved from the database
       - The operation of retrieving information from the database must be performed asynchronously and not block the main thread
       - It must be possible to scroll through the displayed data if not all of the content fits on the screen
     - Exit button
       - Clicking on the exit button must send a request to the server to exit
       - After sending the request (the server's response is not important) the database must be completely cleared
       - After clearing the database, the authorization screen must display
       - The operation of sending data to the server must be performed asynchronously and not block the main thread
       - The operation of clearing information from the database must be performed asynchronously and not block the main thread
     - Updating object information
       - The [SwipeRefreshLayout](https://developer.android.com/develop/ui/views/touch-and-input/swipe/add-swipe-interface) method must be supported to update the information about the object
       - When you use refreshable or go to a screen with information about an object, a request should be sent to the server to get information about the object using a token
       - If the request fails, a pop-up notification with the reason must display
       - The data retrieved from the server must be stored in the database
       - The operation of retrieving data from the server must be performed asynchronously and not block the main thread
       - Operation of saving information to the database must be performed asynchronously and not block the main thread
     - Horizontal and vertical orientation of the device must be supported
   - Separate models must be created (ViewData)
   - The model name must be formed as NameViewData (For example, UserViewData)
   - ViewData<->Domain mappers must be implemented
   - At the end of the refresh token lifetime, a request for a new session token and refresh token must be sent to the server
   - The operation of getting new tokens must be performed asynchronously and not block the main thread
   - Once you finish working with the application, the session token is erased from the database
   - Mappers must be formed as [extension methods](https://kotlinlang.org/docs/extensions.html)
2. Provide communication between the user interface layer and the business logic layer