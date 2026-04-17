# Maps and Geolocation

Summary: Your task is to familiarize yourself with the basics of working with maps and geolocation in an iOS application

💡 [Tap here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave your feedback on the project**. It's anonymous and will help our team make your educational experience better. We recommend completing the survey immediately after the project.

## Contents

- [Chapter I](#chapter-i)
  - [Introduction](#Introduction)
- [Chapter II](#chapter-ii)
  - [MapKit](#mapkit)
  - [CoreLocation](#corelocation)
  - [Terminology](#terminology)
- [Chapter III](#chapter-iii)
  - [Literature](#literature)
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

Your task is to familiarize yourself with the basics of working with maps and geolocation in an iOS application using the [MapKit](https://developer.apple.com/documentation/mapkit/) and [CoreLocation](https://developer.apple.com/documentation/corelocation) frameworks.

Be sure to read the document through to the end before starting the task.

### **MapKit**

MapKit is a framework provided by Apple for integrating maps into iOS and MacOS applications. With MapKit, you can display maps, annotate them with labels, customize their appearance, and more.

Main components of MapKit:

1. **[MKMapView](https://developer.apple.com/documentation/mapkit/mkmapview)**: The main class for displaying maps, it allows you to control which part of the world is shown, as well as customize various aspects of the map's appearance.
2. **[MKAnnotation](https://developer.apple.com/documentation/mapkit/mkannotation)**: An interface for annotations that can be added to the map. Annotations are typically used to mark specific points on the map.
3. **[MKPinAnnotationView](https://developer.apple.com/documentation/mapkit/mkpinannotationview) and [MKMarkerAnnotationView](https://developer.apple.com/documentation/mapkit/mkmarkerannotationview)**: Classes for customizing the visual representation of annotations.
4. **[MKOverlay](https://developer.apple.com/documentation/mapkit/mkoverlay)**:An interface for overlays, which are graphical layers placed on top of the map. They can be used to display routes, boundaries, and other geometric shapes.
5. **[MKDirections](https://developer.apple.com/documentation/mapkit/mkdirections) and [MKRoute](https://developer.apple.com/documentation/mapkit/mkroute)**: Classes for working with directions and routes on the map.

### **CoreLocation**

[CoreLocation](https://developer.apple.com/documentation/corelocation) is a framework for determining the geographic location and orientation of a device. It provides location data that can be used together with MapKit to display the user's location on the map or to perform other geolocation-related operations.

Main components of CoreLocation:

1. **[CLLocationManager](https://developer.apple.com/documentation/corelocation/cllocationmanager)**: A class for setting up and managing location services.
2. **[CLLocation](https://developer.apple.com/documentation/corelocation/cllocation)**: A class for representing location data, including coordinates and elevation.
3. **[CLGeocoder](https://developer.apple.com/documentation/corelocation/clgeocoder)**: A class for converting between geographic coordinates and addresses (geocoding and reverse geocoding).

### **Terminology**

**Annotation** — an object used to represent information about a specific point on the map. It is not a visual component, but rather a data model that contains information about the location (coordinates) and possibly additional data, such as the name of the location or a description.

**Pin** — a visual marker 📍 used to indicate a specific location or point on the map.

**Cluster** — represents a visual aggregation of multiple annotations into one to reduce map clutter and improve readability. Clustering in MapKit is used to manage and display a large number of annotations that are close together on the map as a single group.

## Chapter III

### **Literature**

- [MapKit Tutorial](https://www.kodeco.com/7738344-mapkit-tutorial-getting-started).
- [WWDC 2023 MapKit SwiftUI](https://developer.apple.com/videos/play/wwdc2023/10043/).
- [MapKit SwiftUI Tutorial](https://medium.com/simform-engineering/mapkit-swiftui-in-ios-17-1fec82c3bf00).
- [CoreLocation Tutorial](https://dwirandyh.medium.com/deep-dive-into-core-location-in-ios-a-step-by-step-guide-to-requesting-and-utilizing-user-location-fe8325462ea9).
- [MapKit Clustering](https://blog.kulman.sk/clustering-annotations-in-mkpampview/).
- [Decluttering with Mapkit](https://developer.apple.com/documentation/mapkit/mkannotationview/decluttering_a_map_with_mapkit_annotation_clustering/).
- [Apple Maps URL Scheme](https://developer.apple.com/library/archive/featuredarticles/iPhoneURLScheme_Reference/MapLinks/MapLinks.html).
- [Pin Icon Pack](https://www.figma.com/community/file/1218031276521685890).

## Chapter IV

## **Assignment**

Your task is to create an alternative screen for displaying a user's list of friends. The screen consists of an interactive map that displays all of the user's friends according to information from their social network profile.

**General requirements:**

- You are allowed to use SwiftUI and UIKit to create the map screen.
- The use of third party libraries is prohibited (except those explicitly mentioned).

### **Task I: Loading User Location Information**

- Implement loading information about friends' locations from the social network.
- The association of the city ID and its coordinates can be hardcoded into the application.

### **Task II: Map Screen of Friends' Locations**

- Implement a map screen that displays friends according to their geolocation.
- If no location data is provided, such friends should not be displayed on the map.
- Clicking on a pin should display a map of the friend / group of friends (if they are in the same place) + a button "Plot a route".
- While data is loading, show the user a loading indicator.

### **Task III: Custom Pin Icons**

- Replace MapKit's default pin and cluster icons with custom ones (any, at your discretion).

### **Task IV: Clustering**

- Add support for clustering (when zooming out, pins should group into a single cluster pin, and when zooming in, the cluster should break up into individual pins).

### **Task V: Sorting Friends**

- On the friends list screen, implement sorting based on distance from the user's current location.
- Display the distance to the user and the city they are in.

### **Task VI: Route Planning to the User**

- When the user clicks on a friend, offer to plan a route to them using the Apple Maps application.
- Use the URL scheme to do this.

### Карта экранов:

![](misc/images/interface.png)

## **Additional Tasks (\*):**

### **Task VII: Support for Google Maps**

- Add support for Google Maps instead of the default Apple Maps.

### **Task VIII: Support for Yandex Maps**

- Add support for Yandex instead of default Apple maps.

### **Task IX: Unified Interface for Working with Maps**

- Hide the implementation of Apple Maps / Google Maps / Yandex Maps behind a unified interface.
- The interface should hide the differences in the implementation of each of the maps and provide a single and clear way to interact.
- Add the ability to switch between Apple / Google / Yandex Maps "on the fly".

### **Task X: User Avatars**

- Display user avatars on the map instead of the standard pin icons.
- If it is a group of users, show 2 icons and a "+" sign.

### **Task XI: Reverse Geocoding**

- Use reverse geocoding (independent of Apple Maps / Google Maps / Yandex Maps) based on the city name to get its coordinates (latitude and longitude).
- Use the new coordinates instead of hardcoded values in cities.json.
- Cache the retrieved values.