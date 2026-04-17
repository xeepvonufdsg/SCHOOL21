# DOD

Introduction to the principles of Data-Oriented Design and the Entity Component System pattern

💡 [Tap here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave your feedback on the project**. It's anonymous and will help our team make your educational experience better. We recommend completing the survey immediately after the project.

## Contents

1. [Chapter I](#chapter-i) \
   1.1. [Introduction](#introduction)
2. [Chapter II](#chapter-ii) \
   2.1. [Information](#information) \
   2.2. [Data-Oriented Design](#data-oriented-design) \
   2.3. [Benefits of Data-Oriented Design](#benefits-of-data-oriented-design) \
   2.4. [Differences between DOD and OOP](#differences-between-DOD-and-OOP) \
   2.5. [ECS pattern](#ecs-pattern) \
   2.6. [ECS frameworks in Unity](#ecs-frameworks-in-unity)
3. [Chapter III](#chapter-iii) \
   3.1. [Part 1. More refactor](#part-1-more-refactor)

## Chapter I

## Introduction

In this project you will learn about the principle of Data-Oriented Design and the Entity Component System pattern, and rewrite the code from project 2 using one of the proposed ECS frameworks in the DOD approach.

## Chapter II

## Information

Data-Oriented Design (DOD) is an approach to software design based on a more efficient use of CPU cache, used in video games development instead of the usual OOP.

### Data-Oriented Design

A code written in the classic OOP style forces developers to use patterns that focus on abstractions and inheritance. While these concepts have their place in programming, they can become a serious obstacle when it comes to writing efficient and optimizable code.

DOD allows, first of all, focusing on data, on how its processing and storage are organized. The main reason for the power of the DOD concept is that it works very well with large groups of objects. OOP, by definition, works with a single object, which is not very typical for games, where, as a rule, at one point in time you need to calculate the logic of several NPCs, particles, bullets, objects, working on the same or similar principles.

### Benefits of Data-Oriented Design

- ****Сoncurrency.**** In DOD, we have a certain array of identical data and a function that processes them, which greatly simplifies the process of parallelization, avoiding the danger of simultaneous access to data from multiple streams;
- ****Using cache.**** DOD allows a very efficient use of the command cache, because it constantly executes the same code. In addition, by arranging data in large adjacent blocks, it can be processed sequentially, achieving almost perfect use of the data cache;
- ****Modularity.**** The code in DOD is made up of small functions with very few dependencies with other parts of the code, which makes it easier to understand, replace and update the code, increasing extensibility;
- ****Testing.**** It is easy to write unit tests for small data processor functions: create some incoming data, call the function that converts it, and check if the output corresponds to the expected data.

### Differences between DOD and OOP

| ООP | DOD |
| --- | --- |
| A class is a set of data and functions that operate on that data | Data and the logic that operates on them exist independently of each other |
| Data are considered as elements of the state of the object | Data are considered as information that needs to be processed |
| Abstraction, inheritance, encapsulation | Dividing objects into separate components - the data that are supposed to be processed together |
| An object is an instance of a class | An object is a composition of components that contain data describing its properties |
| "Array Structure" - all data of each object are in the common data stream, regardless of whether they are used or not | "Array Structure" - identical data is organized in a separate array. The data stream contains only the data with which you work |
| Polymorphism, virtual calls | Lack of hidden behavior |
| Targeting vertical binding, the complexity of object allocation and inheritance hierarchies for games | Targeting horizontal binding |

### ECS Pattern

The Entity Component System (ECS) is an architectural pattern that allows you to implement the principles of Data-Oriented Design in object-oriented programming languages. ECS is based on the following 3 terms: entity, component and system.

- An Entity is any object in the game. For example, it can be a player unit, a button in an interface, an event with data from one system to another, etc. Entities themselves have no properties and act as containers for components. Similar to unity, this is a `GameObject`. Usually it is an index pointing to the data in the array that characterizes this particular entity;
- Components are data blocks that define all sorts of properties of any game objects or events. Ideally, they are objects with a simple data structure. They can be added and removed from an entity during its life cycle;
  - Components are structures with data that are associated with an entity for a long time. For example, `PositionComponent`, which contains data about the position of the entity in space;

    ```
    public struct PositionComponent
    {
    		public Vector3 Position;
    }
    ```
  - Events are structures with (or without) data that are associated with an entity during a single frame. For example, `HitEvent`, saying that the entity was hit in this frame;

    ```
    public struct HitEvent
    {
    		public int Damage;
    }
    ```
  - Tags are structures without data that are permanently associated with an entity. For example, the `PlayerTag`, which indicates that the entity is a player, serves as a label to separate the player from other entities when filtering;

    ```
    public struct PlayerTag { }
    ```
- A System is a class with defined methods over defined components. Systems do not contain any local data or references to entities or components, they only serve to handle arrays of conditionally filtered entities and components attached to those entities. The conditions for entity filtering are components, which must either be contained or not contained by an entity.\
  For example, `var filter1 = GetEntities().With<PositionComponent, HitEvent>()` could return an array of all entities that contain `PositionComponent` and `HitEvent`, i.e. all those in space in which a hit was made in this frame.
  Or, for example, `var filter2 = GetEntities().With<PositionComponent>().Without<PlayerTag>()` could return an array of all entities that contain `PositionComponent` and do not contain `PlayerTag`, i.e. all those in the non-player space.
  It is important to consider that the systems work in sequence, one after another, so it is necessary to follow the order of their call.

### ECS frameworks in Unity

- **LeoECSLite -** a lightweight C# Entity Component System framework that contains the bare minimum and is completely abstracted from Unity, so additional extensions may be needed for easy integration;
- **Morpeh -** ECS framework, which is more focused on integration with Unity. To use some of the convenience of integration (creating entities, adding components through the editor), you need a paid asset - Odin Inspector.
- **Entities (Unity DOTS) -** The ECS framework from Unity is still under development and is often seriously reworked. The most current version is only available for Unity 2022.2+.

## Chapter III

### Part 1. More Refactor

You need to rewrite the code from Game Design project using one of the proposed ECS frameworks in DOD approach. Only the game logic needs to be rewritten, UI can still be in OOP approach.

- The player's game object must be an ECS entity
- NPCs under AI control must be ECS entities
- All game objects with which interaction is supposed to take place must be ECS entities
- All runtime data from `MonoBehaviour` must be transferred to the ECS components
- In `MonoBehaviour` only readonly `SerializeField` fields are allowed, which are used to configure objects from the editor.
- The division of data into components should be logically reasonable: you cannot store data that is always or in most cases processed separately in one component, but you should not divide it up to the point where all components will have a single field. It is worth avoiding duplication of data in components. If such a need arises, it is better to put duplicate data in separate components. When distributing data, you should be guided by the algorithm:
  1. If the data are used to implement the same mechanics and are processed together, it is worth combining them into one component
  2. If there are entities or systems that only need some data from this data, it is worth splitting the component into two new
- Components must be simple data structures and must not contain any processing logic. Only various kinds of "helpers" provided by the framework are allowed (e.g., a method for cleaning a component or restoring fields to their default values)
- All logic from the `Update()` methods in `MonoBehaviour` must be transferred to the ECS system.
- ECS systems must not contain any state. It is allowed to store some data in class fields, such as pool caches, filters, auxiliary service classes, or constants
- Generally, systems must contain no more than one external filter enumeration cycle. There is no limit on the number of nested cycles.
- If you need to perform the same or very similar logic on different filters, you need to allocate a separate system for each filter, and the common logic should be put into service classes (static or thrown into systems in the constructor or during initialization).
  - The service class must only be a set of general methods for data processing
  - Systems enumerate the filter and call services methods, passing there data from components
- To connect Unity and the ECS world (physics, UI, various scene/level loaders, and so on):
  - In the **Unity → ECS** direction. You need to implement `MonoBehaviour` with Unity event handlers (`OnCollisionEnter()`, `OnCollisionStay()` etc. for physics, `OnButtonClick()` etc. for UI). These handlers must create the appropriate ECS event containing the event data. The event must be created in a world separate from the rest of the ECS entities (the world for events)
  - In the **ECS → Unity** direction. It is necessary to route the `MonoBehaviour` system to ECS through a component and call its methods