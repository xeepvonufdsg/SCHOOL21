# Advanced Features

Summary: In this project, you'll explore additional features of the iOS platform.

💡 [Tap here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave your feedback on the project**. It's anonymous and will help our team make your educational experience better. We recommend completing the survey immediately after the project.

## Contents

- [Chapter I](#chapter-ii)
  - [Introduction](#Introduction)
- [Chapter II](#chapter-ii)
  - [Keychain](#keychain)
  - [Biometrics Touch ID / Face ID](#biometrics-touch-id--face-id)
  - [Localization](#localization)
  - [Accessibility](#accessibility)
- [Chapter III](#chapter-iii)
  - [Literature](#Literature)
- [Chapter IV](#chapter-iv)
  - [Assignment](#assignment)
  - [Additional Tasks](#additional-tasks)

## Chapter I

## Introduction

1. Along the way, you may feel a sense of uncertainty and a severe lack of information: that's OK. Remember, the information in the repository and on Google is always with you. So are your peers and Rocket.Chat. Communicate. Search. Use common sense. Don't be afraid to make mistakes.
2. Pay attention to information sources. Check. Think. Analyze. Compare.
3. Look at the text of each problem. Read it several times.
4. Read the examples carefully. There may be something in them that is not explicitly stated in the task itself.
5. You may find inconsistencies where something new in the terms of the task or examples conflicts with something you already know. If you find such an inconsistency, try to resolve it. If not, write it down as an open question and figure it out as you work. Do not leave an open question unanswered.
6. If a task seems confusing or impossible, it only seems that way. Try to break it down. It is likely that some parts will become clear.
7. There will be several tasks. Those marked with an asterisk (\*) are for the more meticulous students. These tasks are more difficult and are not mandatory. But doing them will give you extra experience and knowledge.
8. Don't try to fool the system or the people around you. You will fool yourself first.
9. Got a question? Ask your neighbor to the right. If that doesn't help, ask your neighbor to the left.
10. When you ask for help, always understand why and how. Otherwise, the help is useless.
11. Always push only to the develop branch! The master branch will be ignored. Work in the src directory.
12. There should be no files in your directory other than those specified in the tasks.

## Chapter II

Your task is to explore additional features of the iOS platform, such as secure data storage, biometrics, localization, and designing interfaces for people with disabilities.

Be sure to read the document in its entirety before beginning the task.

### **Keychain**

[Keychain](https://developer.apple.com/documentation/security/keychain_services/) is a secure storage for confidential data such as passwords, tokens, and encryption keys. It provides secure access to data using encryption mechanisms provided by Apple.

**Features:**

- Isolated for each application: Data stored by one application is not accessible to others (there is a possibility to share data between a group of applications from one developer).
- Supports secure data storage, even if the device is lost or stolen.
- Uses an API for data operations: create, read, update, delete.
- Can be synchronized across the user's devices via iCloud.

**Terminology:**

- **Keychain Item**: The primary object that represents data stored in the Keychain, such as passwords or keys.
- **Keychain Services API**: A set of functions provided by Apple for interacting with Keychain, including creating, finding, updating, and deleting Keychain items.
- **Access Control List (ACL)**: Defines access rules for Keychain items, including usage and access restrictions.
- **SecItem Classes**: Classes of items, such as kSecClassGenericPassword and kSecClassInternetPassword, that define the type of data stored.
- **Security Framework**: A library that provides interfaces for working with security and encryption, including Keychain Services.

### Biometrics Touch ID / Face ID

[Touch ID / Face ID](https://developer.apple.com/documentation/localauthentication/) are biometric technologies used by Apple to authenticate users on iOS devices. Touch ID uses fingerprints, and Face ID uses facial recognition. Both technologies provide a convenient and secure way to unlock devices, authorize purchases, and sign into applications. They enhance security by minimizing the risk of unauthorized access to the device and user data.

**Terminology:**

- **Local Authentication Framework**: A framework that provides an API for authentication using Face ID and Touch ID.
- **Biometric Authentication**: The process of verifying a user through unique biological characteristics, such as fingerprints (Touch ID) or facial features (Face ID).
- **Authentication Request**: A request initiated by an application to authenticate a user using Face ID or Touch ID.
- **Fallback Mechanism**: A mechanism that allows the user to enter a password or PIN if biometric authentication fails.
- **Security and Privacy Guidelines**: A set of Apple policies and recommendations designed to ensure the security and privacy of user data when using biometric technologies.

### **Localization**

**Localization** is the process of adapting an application for different languages and regional features. In mobile development, this can include:

1. **Content Translation**: Changing the language of the interface, images, etc.
2. **Data Formatting**: Adjust formats for dates, times, numbers and currencies.
3. **Support for Different Writing Standards**: For example, support for left-to-right (LTR) and right-to-left (RTL) writing directions, important for languages such as Arabic or Hebrew.

### **Accessibility**

Apple's iOS includes several accessibility features that help developers create applications that are enjoyable for all users, including those with disabilities. Here are some of them:

- **Dynamic Type**: Support for changing the size of text that users can adjust on their devices. This is especially useful for users with visual impairments.
- **VoiceOver**: A screen reader that speaks screen content. Developers can customize their applications to work properly with VoiceOver by providing descriptive labels and instructions for UI elements.
- **Enhanced features for the visually impaired**: Includes settings such as increased contrast, color inversion, and more.
- **Voice Control**: Allows users to control their device using voice commands.

This is just a short list of the accessibility features available on the iOS platform.

## Chapter III

### **Literature:**

- [Keychain API](https://developer.apple.com/documentation/security/keychain_services/).
- [Keychain Tutorial](https://www.advancedswift.com/secure-private-data-keychain-swift/).
- [Local Authentication](https://developer.apple.com/documentation/localauthentication/).
- [Tutorial Touch ID / Face ID](https://www.advancedswift.com/face-id-touch-id-swift/).
- [Application Localization](https://developer.apple.com/documentation/xcode/localization).
- [Scaling Fonts](https://developer.apple.com/documentation/uikit/uifont/scaling_fonts_automatically/#).
- [Dynamic Type Tutorial](https://www.hackingwithswift.com/quick-start/swiftui/how-to-use-dynamic-type-with-a-custom-font).
- [Secure Password Storage](https://www.vaadata.com/blog/how-to-securely-store-passwords-in-database/).
- [Settings Bundle](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/UserDefaults/Preferences/Preferences.html).
- [Settings Bundle Configuration](https://swiftsenpai.com/xcode/settings-bundles-management/).

## Chapter IV

## **Assignment**

The main part of the application is already written, all that remains is to add additional features.

**General requirements:**

- The interface can be designed using SwiftUI and UIKit.
- Use of the [CryptoSwift](https://github.com/krzyzanowskim/CryptoSwift) library is allowed.

### **Task I: Store token in Keychain**

- Store the authorization token in the secure Keychain store.
- Develop a convenient, reusable class (KeychainWrapper) to work with the keychain to easily store and retrieve data.

### **Task II: Support for Touch ID / Face ID**

- Extend the user authorization story.
- The application interface should be modified so that after successful authorization, the user is prompted to set a short (4-digit) numeric pincode for login, and after setting the pincode — Touch ID.
- Subsequent application logins will be made by entering Touch ID or the pincode. A registration reset button should be provided on the pincode entry screen.
- The successful Pincode / Touch ID setup scenario is roughly as follows:
  1. When setting the pincode: the application generates random data — salt, extends the pincode with salt using the PBKDF2 algorithm, the derived key encrypts the access token (the token used for authorized server requests).
  2. The application stores two parameters in the Keychain: the encrypted access token and the salt. The next time the user enters the application, he or she enters the pincode. The pincode and salt are used to regenerate the key that encrypted the access token.
  3. If the user agrees to use Touch ID, the application also stores the pincode in the Keychain. The use of third-party libraries is permitted.
  4. Perform a similar scenario for the refresh token. (You can concatenate access token + refresh token + expiration date into one string and perform the procedure once, or you can do it separately for each field).

### **Task III: Secure input**

- Input fields should disable the ability to paste/copy, autocorrect.
- Password entry should be masked.

### **Task IV: Application localization**

- Localize the application to English:
  - All text (embedded in the application).
  - The application name (it should be in Russian in the Russian version and in English in the English version).

### **Task V: Dynamic fonts**

- Add support for dynamic fonts (Dynamic Type) to the application.
- When the text size is changed in the iOS settings (Settings → Accessibility → Display & Text Size), the text size in the application should change accordingly.
- The application layout should not break when the text size changes.

### **Task VI: Update avatar**

- Add the ability to change the user's avatar in the application.
- Add a method to upload the user's avatar to the server.
- When the user clicks on the avatar (on the profile screen), the user is prompted to select a source to replace the photo.
- The user can take a photo or select a photo from the gallery.
- Implement an editing (cropping) screen for the photo.
- The design for editing (cropping) the photo can be of your choice.

### **Task VII: Link contacts in phone with social network profile**

- Add a contact Sync button to the Friends List screen.
- When the Sync button is pressed:
  - The application retrieves the user's entire contact list from the phonebook.
  - The application retrieves the user's entire Friends List from the social network.
  - The application compares the Friends List and the contact list to find matches by the user's first and last name.
  - For the matched contacts in the phonebook, the application adds a "Social Network" field and inserts the ID/nickname.
- At the end, the user is presented with a list of updated contacts (the design is as simple as possible, at your discretion).

### **Task VIII: Add application settings (for developers)**

- Add a Settings Bundle with application settings for developers.
- Developer settings should only be available in the debug build; they should not be visible in the release build.
- Add the option to force the application language in the application settings (regardless of the system language).
- Move all of the application's technical settings from previous lessons into a unified developer menu.

## **Additional Tasks** (\*):

### **Task IX: Data encryption in DB**

- Add additional encryption of data when stored in the DB (such functionality is already implemented in Realm, with CoreData you need to think about and implement it independently).

### **Task X: Check the device for Jailbreak**

- Implement a series of checks to ensure that Jailbreak is not installed on the device, and deny access to the application if it is detected.

### **Task XI: Automatic deauthorization**

- Automatically deauthorize the user after 2 minutes of the application being in the background mode.

### **Task XII: Blur screen when application is minimized**

- When the application goes into background mode, add a blur effect to the screen so that the contents of the application are not visible.
- When the application returns to active mode, the blur effect should disappear.

### **Task XIII: Add RTL support**

- Add support for RTL languages (e.g. Arabic) to the interface.
- Localization should include not only text translation, but also layout adjustments (it should automatically align to the right margin).