# Maze

Implementation of the Maze project.

The russian version of the task can be found in the repository.

💡 [Tap here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave your feedback on the project**. It's anonymous and will help our team make your educational experience better. We recommend completing the survey immediately after the project.

## Contents

1. [Chapter I](#chapter-i) \
   1.1. [Introduction](#introduction)
2. [Chapter II](#chapter-ii) \
   2.1. [Information](#information)
3. [Chapter III](#chapter-iii) \
   3.1. [Part 1](#part-1-implementation-of-the-maze-project) \
   3.2. [Part 2](#part-2-generation-of-a-perfect-maze) \
   3.3. [Part 3](#part-3-solving-the-maze) \
   3.4. [Part 4](#part-4-bonus-cave-generation) \
   3.5. [Part 5](#part-5-bonus-ml-reinforcement-learning) \
   3.6. [Part 6](#part-6-bonus-web-interface)

## Chapter I

![Maze](assets/img_1131.png)

Eve approached the head's office just as the familiar, muted shouting emerged out of it:

`-` How…think of opening …cess to the INTERNET to thes..vers?! And most importantly why …ns?!

Going into the office now was clearly not the best idea, so Eve decided to wait out the obviously unpleasant conversation in the hallway. \
After an unintelligible answer, the boss's outrages continued:

`-` You clearly don't understand the importance of this project to our... This is... And now go fix all these screw-ups!

The door opened, and Alice and Charlie hurried out of the office, looking downcast.

`-` And God help us if something gets leaked! – he shouted after.

Alice and Charlie walked away in the opposite direction, not paying attention to Eve standing nearby. She waited a few minutes, then braced herself and knocked on the door.

`-` Come in. Oh, Eve, yes, come in, — the boss said. The spacious room with wide windows was full of various books on algorithms, mathematics, and programming. In the middle of the room was a table with a plastic sign that said "Robert M."

`-` Bob, about the experiments for the task...''

`-` With the mazes, yes, I know. They tested your developments. They are interesting, but too simple. We sent generation examples to our partners, but their brainchild went through the mazes in an embarrassingly short period of time. And in our case we need something much more complicated. \
Try to reduce the number of correct ways. Browse the Internet again, look in the direction of caves and cellular automata, and then back to tests and experiments again. And remember: the more complicated the better!

Eve left the office and went to her workplace, wondering what other algorithms she could try. On the way, she was looking for Alice or Charlie to find out what had happened but couldn't find them, so she sat down at her computer and continued the work.

## Introduction

In this project you’ll learn about mazes and caves, including the basic algorithms of their handling, such as: generation, rendering, solving.

## Chapter II

## Information

A maze with "thin walls" is a table of *n* rows by *m* columns size. There may be "walls" between the cells of a table. The table as a whole is also surrounded by "walls".

The following is an example of such a maze: \
![maze](assets/img_7194.png)

The solution to a maze is the shortest path from a given starting point (table cell) to the ending one.

When traversing a maze, you can move to neighboring cells that are not separated by a "wall" from the current cell and that are on the top, bottom, right or left.
A route is considered the shortest if it passes through the smallest number of cells.

An example of a maze with its solution: \
![solution](assets/img_0241.png)

In this example, the starting point is 10; 1, and the ending point is 6; 10.

## Maze description

The maze can be stored in a file as a number of rows and columns, as well as two matrices containing the positions of vertical and horizontal walls respectively.

The first matrix shows the wall to the right of each cell, and the second — the wall at the bottom.

An example of such a file:

```
4 4
0 0 0 1
1 0 1 1
0 1 0 1
0 0 0 1

1 0 1 0
0 0 1 0
1 1 0 1
1 1 1 1
```

The maze described in this file: \
![maze4](assets/img_3626.png)

See materials for more examples of maze descriptions.

## Flaws in mazes

Maze flaws include isolated areas and loops.

An isolated area is a part of the maze with passages that you cannot access from the rest of the maze. For example: \
![isolated](assets/img_8068.png)

A loop is a part of the maze with passages that can be walked in "circles". The walls in the loops are not connected to the walls surrounding the maze. For example: \
![loop](assets/img_6419.png)

## Generation using a cellular automaton

In many games there is a need for branching locations, such as caves.
They can be created by generation using the cellular automaton.
This kind of generation uses an idea similar to the Game of Life you are already familiar with. The idea of the proposed algorithm consists of implementing only two steps: first, the whole field is filled randomly with walls — i.e., for each cell it is randomly determined whether it will be free or impassable — and then the map state is updated several times according to the conditions, similar to the birth/death ones in the Game of Life.

The rules are simpler than in the Game of Life — there are two special variables, one for "birth" of "dead" cells (the "birth" limit) and one for destruction of "live" cells (the "death" limit).
If "live" cells are surrounded by "live" cells, the number of which is less than the "death" limit, they "die". In the same way, if "dead" cells are next to "live" cells, the number of which is greater than the "birth" limit, they become "live".

An example of the algorithm's result (the first picture shows only the initialized maze, and the second picture shows a maze in which there are no more changes in subsequent steps): \
![cave1](assets/img_0407.png)
![cave2](assets/img_8360.png)

## Caves description

A cave that has passed 0 simulation steps (only initialized) can be stored in the file as a number of rows and columns, as well as a matrix containing the positions of "live" and "dead" cells.

An example of such a file:

```
4 4
0 1 0 1
1 0 0 1
0 1 0 0
0 0 1 1
```

The cave described in this file: \
![cave3](assets/img_1932.png)

See materials for more examples of cave descriptions.

## Chapter III

## Part 1. Implementation of the Maze project

You need to implement a Maze program that can generate and render perfect mazes and caves:

- The program must be developed in C# language
- The program code must be located in the src folder
- When writing code it is necessary to follow the Google style
- The program must be built with Makefile which contains standard set of targets for GNU-programs: all, install, uninstall, clean, dvi, dist, tests. Installation directory could be arbitrary, except the building one
- GUI implementation, based on any GUI library for C#
- The program has a button to load the maze from a file, which is set in the format described [above](#maze-description)
- Maximum size of the maze is
  50x50
- The loaded maze must be rendered on the screen in a field of 500 x 500 pixels
- "Wall" thickness is 2 pixels
- The size of the maze cells themselves is calculated so that the maze occupies the entire field allotted to it.

## Part 2. Generation of a perfect maze

Add the ability to automatically generate a perfect maze. \
A maze is considered perfect if it is possible to get from each point to any other point in exactly one way.

- You must generate the maze according to **Eller's algorithm**
- The generated maze must not have isolations and loops
- Prepare full coverage of the perfect maze generation module with unit-tests
- The user enters only the dimensionality of the maze: the number of rows and columns
- The generated maze must be saved in the file format described [above](#maze-description)
- The created maze should be displayed on the screen as specified in the [first part](#part-1-implementation-of-the-maze-project)

## Part 3. Solving the maze

Add the ability to show the solution to *any* maze currently shown on the screen:

- The user sets the starting and ending points
- The route, which is the solution, must be displayed with a line 2 pixel thick, passing through the middle of all the cells in the maze through which the solution runs.
- The color of the solution line must be different from the color of the walls, and the field
- Prepare full coverage of the maze solving module with unit-tests

## Part 4. Bonus. Cave Generation

Add cave generation [using a cellular automaton](#generation-using-a-cellular-automaton):

- The user selects the file that describes the cave according to the format described [above](#caves-description)
- Use a separate window or tab in the user interface to display the caves
- Maximum size of the cave is 50 x 50
- The loaded cave must be rendered on the screen in a field of 500 x 500 pixels
- The user sets the limits for "birth" and "death" of a cell, as well as the chance for the starting initialization of the cell
- The "birth" and "death" limits can have values from 0 to 7
- Cells outside the cave are considered alive
- There should be a step-by-step mode for rendering the results of the algorithm in two variants:
  - Pressing the next step button will lead to rendering the next iteration of the algorithm
  - Pressing the automatic work button starts rendering iterations of the algorithm with a frequency of 1 step in `N` milliseconds, where the number of milliseconds `N` is set through a special field in the user interface
- The size of cells in pixels is calculated so that the cave occupies the entire field allotted to it
- Prepare full coverage of the cave generation module with unit-tests

## Part 5. Bonus. ML. Reinforcement learning

With the help of reinforcement learning, it is necessary to develop an algorithm for teaching an agent the shortest passage of mazes:

- The user specifies a file which describes the maze and an ending point
- The agent must be able to find a way out of the maze from any starting point
- It is necessary to use the Q-learning method
- The agent is trained on a single maze, which does not change either during the training process or during the testing phase; the endpoint is also fixed
- The agent's training module must be fully covered by unit tests

It is required to provide the user with the opportunity to interact with a trained agent:

- The user defines the starting point
- The route built by the agent from a given point is displayed in accordance with the rules described above

Agent training and interaction modules should be developed in C# language without using ready-made reinforcement learning libraries.

## Part 6. Bonus. Web-interface

Add a Web-based version of the user interface in any format (MPA, SPA) using appropriate frameworks. The Web interface must meet at least all the basic functional requirements from the parts above ([Part 1](#part-1-implementation-of-the-maze-project)-[Part 3](#part-3-solving-the-maze)).