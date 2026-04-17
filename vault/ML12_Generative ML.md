# Generative Models

Summary: This project allows you to dive into a new family of models used for generating purposes.

💡 [Tap here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave your feedback on the project**. It's anonymous and will help our team make your educational experience better. We recommend completing the survey immediately after the project.

## Contents

1. [Chapter I. Preamble](#chapter-i-preamble)
2. [Chapter II. Introduction](#chapter-ii-introduction) \
   2.1. [Discriminative and Generative models](#discriminative-and-generative-models) \
   2.2. [Variational AutoEncoder](#variational-autoencoder) \
   2.3. [Generative Adversarial Network](#generative-adversarial-network)
3. [Chapter III. Goal](#chapter-iii-goal)
4. [Chapter IV. Instructions](#chapter-iv-instructions)
5. [Chapter V. Task](#chapter-v-task)
6. [Chapter VI. Bonus part](#chapter-vi-bonus-part)

## Chapter I. Preamble

This project will introduce us to another machine learning problem that we have not yet identified. This is the task of building generative models — the goal of which is to create data that looks real. In fact, we've trained such models before: remember the name generator from the Recurrent Neural Networks project. Another less obvious example is the PCA model we trained to compress the feature space. But not the direct use of this model, but the inverse — when we recover the original vector from the latent representation.

So it turns out that our task is, given a set of observations, to somehow understand the process that generates them and then reproduce it. The importance of this task lies in the fact that our world stores a lot of different information, most of which can be easily processed by a human. But how do you teach a machine to analyze and understand the nature of that information? Once we find the answer to this question, it will be easier for us to realize the potential of these models.

If you follow the news related to AI, you have probably already heard about well-known implementations of generative models: such as ChatGPT and LaMDA for text generation, Dall-e and MidJourney for generating images from the description, Photoshop++ for image modification on demand, DLSS for generating images with upscaled resolution, many different models for text voicing, MuseNet for generating music, models for generating video, and many more. And each of these models has immediately found a pool of applications where it can be useful for humans. In this project we will learn about the main architectures used to solve this problem.

## Chapter II. Introduction

### Discriminative and Generative models

Parallel to the division of machine learning tasks into supervised and unsupervised, there is an alternative division into Discriminative and Generative. Simply put, the difference is this:

- Generative models generate new instances of data. In a probabilistic setting, the model tries to learn the joint distribution of data p(x, y) (or p(x) if there is no target variable) in a multidimensional space.
- Discriminative models distinguish between different types of data instances. That is, the model attempts to learn the conditional probability p(y|x).

As you can see, generative models actually solve a more complex problem than similar discriminative models. While a discriminative model needs to find a pattern to distinguish dogs from cats, generative models need to match all the parts of the animal's body, how they should interact with the environment, and much more. Generative models should model more, many times more.

This is also confirmed mathematically — finding a probability distribution in a multidimensional space is quite a difficult task, so the task is often simplified. One of the main approaches is to introduce a latent variable z and try to learn a function that transforms z into an observable variable x. This trick is actually very familiar to humans. When we encounter complex patterns, we try to describe them with a small number of variables. For example, instead of describing the motion of a car as a set of positions of atoms, we describe its position in terms of initial coordinates, set the velocity and acceleration, and simply apply the equation of motion. It is only worth mentioning that in this case z is usually given as a random multidimensional vector with simple distributions. So ‘P(x)=∫P(x|z)P(z)dz‘‘P(x)=∫P(x|z)P(z)dz‘`P(x) = \int P(x|z)P(z)dz`.

As a result, our task is to train the model for ‘P(x|z)‘‘P(x|z)‘`P(x|z)`, for which neural networks are very well suited.

### Variational AutoEncoder

AutoEncoder is a neural network architecture that compresses input information and decompresses it in such a way that it should restore the input vector:

![AutoEncoder](assets/img_9690.png)

Actually at this step we get what we want: compressed representation is z and decoder is a function to restore the real vector. And this will work great! All we need is to understand how compressed representations are distributed in low-dimensional space.

But we also want to show you how neural networks can be easily used to optimize the distributions. To do this, we:

1. Replace our compressed representation layer with a random vector that is normally distributed ~N(mean, std), where mean and std are defined by the neural network.
2. Randomly sample our compressed representation from the normal distribution and pass it to the decoder:

![Encoder](assets/img_3923.png)

The advantage of this change is that the model can now use uncertainty during pattern fitting. If the model has not seen many examples of people wearing glasses, the representations of these instances will have a high deviation. It also helps the model avoid overfitting and have a more smooth latent space, since each input can be sampled into similar but different representations. For any sampling of the latent distributions, we expect our decoder model to be able to accurately reconstruct the input:

![reconstruct](assets/img_6581.png)

Along with changing the architecture, it's better to change the loss function for neural network training. For VAEs we use ELBO. To derive what it is and why we use it is part of your task.

Note also that both models could be used for dimensionality reduction tasks.

### Generative Adversarial Network

To finally convince you that neural networks are a very flexible tool, let us consider the GAN model. Imagine that you want to teach a model to play chess, but you do it without any stored games of other players, but by having the computer play online. And at the same time you let the computer play against another model. Who wins then? Of course, if the models are "raw", you can hardly call it a game. But if the loss functions are set correctly, then the models will begin to understand the game as they play, and subsequently be able to beat even the most experienced grandmasters. Generative **Adversarial** networks do something similar. Within such a network there are 2 models playing against each other. The first player is the generator, which is trying to learn how to imitate real data (vectors x), and the second player is the discriminator, which is trying to learn how to distinguish the real data from the data created by the generator. In other sources, this task is often described using an example where the generator is a counterfeiter who prints banknotes to deposit them in a bank — the discriminator.

Let's take a closer look at the architecture. As in VAE, we represent our data by a random hidden (latent) variable that we feed into the generator. The generator mimics real data and feeds it to the discriminator. In parallel, real data is fed into the discriminator, which processes it simultaneously with the artificial data. Since the 2 models have different goals, they cannot be trained at the same time. Therefore, GAN has 2 loss functions, each of which updates its part of the network. As a result, each time the discriminator detects a difference between the two distributions, the generator adjusts its parameters slightly to make it disappear, until the end.

![Generative Adversarial Network](assets/img_7878.png)

Describing how the loss function works for each model within a GAN is part of your assignment.

## Chapter III. Goal

The goal of this project is to understand the architecture of the major generative models: VAE and GAN.

## Chapter IV. Instructions

How to learn at “School 21”:

- Here, you’ll find a unique learning experience with a lot of freedom. You’re given a task and left to find your own way to solve it, using whatever resources work best for you — whether that’s the Internet or AI tools like GigaChat. Just be mindful of information quality: verify, think critically, analyze, and compare.
- Peer-to-peer (P2P) learning is the exchange of knowledge and experience with peers, where everyone acts as both mentor and student. This approach allows you to gain a deeper understanding of the material by learning from one another.
- Feel free to ask for help: around you are peers who are also navigating this path for the first time. Share your own experience and ideas with others. Join Rocket.Chat to stay updated with the latest community announcements.
- Your learning is meaningless if you just copy someone else’s solutions. When receiving help from others, always make sure you fully understand the “why”, “how”, and “purpose” behind the solution. Don’t be afraid to make mistakes.
- Does the task seem impossible? Take a break, get some fresh air and clear your mind — this has helped many people. Maybe after that, the solution will come to you naturally.
- The learning process is just as important as the result. It’s not just about completing the task — it’s about understanding HOW to solve it.

How to work with the project:

- This project will be evaluated by humans only. You are free to organize and name your files as you wish.
- We use Python 3 as the only correct version of Python.
- For training deep learning algorithms you can try Google Colab. It offers free kernels (Runtime) with GPU, which is faster than CPU for such tasks. The standard is not applied to this project. However, you are asked to be clear and structured in your source code design.
- Store the datasets in the data subfolder.

## Chapter V. Task

### Dataset

Mnist — [source](http://yann.lecun.com/exdb/mnist/).

"Hello world" dataset for handwritten digit recognition. Many libraries have built-in tools to load this dataset.

![Dataset](assets/img_9830.png)

### Task

1. Answer the questions from the Preamble and Introduction \
   a. Derive the formula for ELBO and explain why this loss is used for VAE training. \
   b. Explain which loss is used for the generator and discriminator in GAN.
2. Generative Model of the Variational AutoEncoder \
   a. Train VAE using the MNIST data set. Use a 2-dimensional vector as the latent vector. Use ELBO as loss function. \
   b. Plot the distribution of the latent vectors using different colors for each digit. \
   c. Create a 15x15 mesh in the 2-dimensional latent space. Use the decoder as a generator model to reconstruct handwritten digits. Combine all reconstructed digits into a 15x15 figure. \
   d. What can you tell from the plots?
3. Supervised Generative Model of VAE \
   a. Train a supervised variational autoencoder using the MNIST dataset, where:

   - i. encoder returns 1-dimensional latent vector;
   - ii. decoder input consists of latent vector and digit label (as a single hot vector).

   b. Create a mesh of 15 points in latent space. Combine them with 10 digit labels and plot 15x10 reconstructed digits. What can you tell from the plots?
4. Generative Adversarial Network \
   a. Implement a Generator that takes a 2-dimensional random vector as input. \
   b. Implement a Discriminator to classify real and fake images. \
   c. Train GAN to generate handwritten digits. \
   d. Plot loss progress for both generator and discriminator? Who wins? \
   e. Create a 15x15 grid in 2-dimensional latent space. Use the generator to reconstruct handwritten digits. Combine all reconstructed digits into a 15x15 figure. \
   f. What can you tell from the plot?
5. Gradient Reversal \
   a. Explain what this layer is and why it is useful. \
   b. Instead of using 2 separate backward steps for the generator and discriminator, use 1, but with a gradient reversal layer. \
   c. Achieve similar quality.
6. Supervised Generative Adversarial Network \
   a. Think about how you can modify GAN to allow control over the number to be generated. Explain what you will change. \
   b. Implement the modification and train the model. \
   c. Visualize all 10 generated handwritten digits with the same random portion of the input variable.

### Submission

Your repository should contain one or more notebooks with your solutions.

## Chapter VI. Bonus Part

- What is the idea behind the diffusion model? Try to implement it on the mnist dataset.

> Please leave feedback on the project in the [feedback form.](https://forms.yandex.ru/cloud/646b47de73cee708d97f0b1a/)