# Project 03 — Go\_Bootcamp

**Overview**: In this project, you will learn how to build a web application in Go using the net/http package.\
💡 [Click here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) to share your feedback on this project. It's anonymous and will help our team improve the learning experience. We recommend completing the survey right after finishing the project.

## Contents

- [Chapter I](#chapter-i)
  - [Instructions](#instructions)
- [Chapter II](#chapter-ii)
  - [General Information](#general-information)
- [Chapter III](#chapter-iii)
- [Project: Tic-Tac-Toe](#project-tic-tac-toe)
  - [Task 0. Project Initialization](#task-0-project-initialization)
  - [Task 1. Project Structure](#task-1-project-structure)
  - [Task 2. Implement the Domain Layer](#task-2-implement-the-domain-layer)
  - [Task 3. Implement the Datasource Layer](#task-3-implement-the-datasource-layer)
  - [Task 4. Implement the Web Layer](#task-4-implement-the-web-layer)
  - [Task 5. Implement the DI Layer](#task-5-implement-the-di-layer)

## Chapter I

### Instructions

1. Throughout the course, you may feel uncertain and underinformed — that’s normal. Don’t forget that the repository and Google are always with you. So are your peers and Rocket.Chat. Communicate. Search. Trust your common sense. Don’t be afraid to make mistakes.
2. Be critical of your sources. Verify. Think. Analyze. Compare.
3. Read the tasks carefully. Reread them more than once.
4. It’s also best to read examples closely. They may contain details not explicitly mentioned in the task.
5. You may come across inconsistencies — where something new in a task or example contradicts what you’ve already learned. If so, try to figure it out. If you can’t, write down your question and resolve it as you go. Don’t leave open questions unresolved.
6. If a task seems unclear or impossible — it only seems that way. Try breaking it down. Most likely, individual parts will become clearer.
7. You’ll encounter various types of tasks along the way. Bonus tasks are for the curious and meticulous. These are more difficult and optional but give you extra experience and knowledge if you complete them.
8. Don’t try to cheat the system or those around you. Ultimately, you’ll only be cheating yourself.
9. Got a question? Ask the person to your right. If that doesn’t help — ask the person to your left.
10. When using help, always make sure you fully understand: why, how, and what for. Otherwise, the help won’t be useful.
11. Always push only to the develop branch! The master branch will be ignored. Work inside the src directory.
12. Your directory should not contain any files except those specified in the tasks.

## Chapter II

### General Information

A web application is a client-server application where the client interacts with the web server using a browser. The application logic is distributed between the server and the client; data is stored primarily on the server, and communication happens over a network.

The net/http package is a powerful standard Go library for building web applications.

Advantages of net/http:

- **Ease of use**: net/http has a simple and intuitive syntax, making it ideal for beginners or developers who prefer clean and readable code.
- **Maintainability**: Any network-related task can be solved either using net/http itself or with community-built packages designed for it.

These advantages make net/http an appealing choice for both beginners and advanced developers looking to build fast, scalable, and maintainable web applications in Go.

**Topics to study**:

- Web application
- net/http
- API
- Minimax algorithm
- MVC

## Chapter III

## Project: Tic-Tac-Toe

### Task 0. Project Initialization

You need to create a project that will be used for all subsequent tasks.

### Task 1. Project Structure

- Each layer should be its own module.
- The project structure must follow the **Standard Go Project Layout**.
- Separate the **API contracts layer** for client interaction.
- Separate the **application layer** for business logic implementation.
- Separate the **infrastructure layer** for handling data operations (e.g., with a database).
- Separate the **DI (dependency injection) layer**, where configurations for dependency injection are described (e.g., using the uber/fx library).

### Task 2. Implement the Domain Layer

- Define a **game board model** as an integer matrix.
- Define a **current game model**, which should include a UUID and the game board.
- Define a **service interface** with the following methods:
  - A method to compute the next move of the current game using the **Minimax algorithm**.
  - A method to **validate** the game board of the current game (check that previous moves haven't been altered).
  - A method to **check for game completion**.
- Models, interfaces, and implementations must be placed in **separate files**.

### Task 3. Implement the Datasource Layer

- Implement a **storage structure** to keep track of ongoing games.
- Use **thread-safe collections** (e.g., sync.Map?) for storing data.
- Define models for the current game’s game board.
- Implement **mappers** between domain and datasource layers (domain <-> datasource).
- Implement a **repository** to interact with the storage structure. It must provide the following methods:
  - A method to **save the current game**.
  - A method to **retrieve the current game**.
- Create a structure that implements the **service interface** and accepts a **repository interface** as a parameter to work with the storage structure.
- Models, interfaces, and implementations must be placed in **separate files**.

### Task 4. Implement the Web Layer

- Define **models** for the current game’s game board.
- Implement **mappers** between the domain and web layers (domain <-> web).
- Implement a **handler** using net/http, with a method:
  - POST /game/{current\_game\_UUID} — sends the current game with the user’s updated game board and returns the current game with the computer’s updated game board.
- If an **invalid game** with an incorrect updated board is sent, an **error with a description** must be returned.
- The application must support **multiple games simultaneously**.
- Models, interfaces, and implementations must be placed in **separate files**.

### Task 5. Implement the DI Layer

- Use the uber/fx library to define a **dependency injection graph**.
- The graph must include at least the following components:
  - The **storage structure**, registered as a **singleton**;
  - The **repository** for working with the storage structure;
  - The **service** for working with the repository.