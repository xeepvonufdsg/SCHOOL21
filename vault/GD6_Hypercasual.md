# Hypercasual

Development of hypercasual games.

💡 [Tap here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave your feedback on the project**. It's anonymous and will help our team make your educational experience better. We recommend completing the survey immediately after the project.

## Contents

1. [Chapter I](#chapter-i) \
   1.1. [Introduction](#introduction)
2. [Chapter II](#chapter-ii) \
   2.1. [Hypercasual games](#hypercasual-games) \
   2.2. [Searching for new project ideas](#searching-for-new-project-ideas) \
   2.3. [Filter](#filter)
3. [Chapter III](#chapter-iii) \
   3.1. [Part 1. Market analysis](#part-1-market-analysis) \
   3.2. [Part 2. Shaping the idea](#part-2-shaping-the-idea) \
   3.3. [Part 3. Implementation](#part-3-implementation)

## Chapter I

## Introduction

In this project you will get a closer look at the Hypercasual game genre, learn how to choose and design an idea for a game from scratch and consolidate the material you learned earlier.

## Chapter II

## Hypercasual games

The hypercasual game genre is characterized by the following features:

- Simple mechanic
- Instant gameplay. Literally "click and play".
- Easy to play
- Minimalistic UI
- Usually the game is only played with "taps" on the screen

The user experience that is accessible and incredibly addictive without any learning makes you come back to these kinds of games again and again.

## Searching for new project ideas

There are several ways to look for ideas for new projects:

- come up with the idea yourself - new gameplay and a new setting
- take an existing hit and change its theme - old gameplay and a new setting
- take an existing hit and change its gameplay without changing the mechanics
- take a game at the start and quickly make a clone

### Your own game

The first option is the most risky, it requires a lot of iterations, good experience in development, as well as a lot of time and money.

### A hit with a different theme

This option can be implemented in the following way:

- find a popular and recent video on youtube, tiktok, giphy
- Search for a popular recent game
- combining the theme of the video and the gameplay of the game

**Important**!

Sometimes developers start coming up with new gameplay while watching videos in search of themes.

This is a good way to go only if you have confidence in your team. Otherwise, you should only look for themes in the videos, without thinking about new gameplay.

### A hit with a different gameplay

This option can be implemented in the following way:

- find a popular recent game
- replace:
  - character
  - control
  - camera

It is better to take two or three choices of replacement. If you just replace the character - it will become a regular clone and such a project will not pass the filter.

You need to change the points above without changing the mechanics. It's a complicated method, but a lot of games have really become popular because of it.

### Take a game at the start

If you manage to find a recently released game that has not yet gained popularity, you can consider making a better clone of the game.

It works if the team has enough experience and resources to quickly release games with good quality, and then actively promote them.

## Filter

When choosing one of the first three options, you should always run the idea through a filter:

1. **Is my game based on solid, proven mechanic?**
2. **Does the gameplay that is in the product differ from the games that are out there with this mechanic?**
3. **Is the experience level as cool as in the hit games?**

## Chapter III

You have to come up with a game that fits the current market and implement it on the Unity engine.

## Part 1. Market analysis

It is necessary to analyze the trends of hypercasual games, youtube, tiktok, etc. According to the results of the analysis it is necessary to write a small report in *.md* format, containing:

- Popular game mechanics
- Popular themes (settings)

## Part 2. Shaping the idea

Come up with an idea for a hypercasual game based on the analysis and make a design document in *.md* format. In this document you need to include the following:

- A brief description of the game (title, platforms, technologies used)
- The setting and style of play
- Gameplay components (core gameplay, meta-gameplay, additional features)
- Target audience and market research
- Examples of such games on the market and how they are treated (competitors or not, whether there is a crossover of audiences, borrowing or opposing ideas)
- USP (Unique Selling Points) of the game (something that will make the game stand out in the marketplace)
- Business model (monetization and promotion)

## Part 3. Implementation

Implement the previously formulated idea. The general requirements for projects must be followed.

**General project requirements:**

- The selected project must be implemented on the **Unity** engine of the latest version **2021.3 LTS**.
- The code must be formatted according to the **Microsoft style**
- You need to prepare a game build for mobile OS (Android/IOS)
- Use the TextMeshPro library for text in the UI
- Use SerializedField for configurable parameters
- Use ScriptableObject for configuration settings
- The game must contain at least two scenes: the loader scene (runs when loading between game sessions, including when opening an application) and the game scene
- The menu must be implemented as an overlay of the game scene
- The game must be developed using MV\* or ECS patterns