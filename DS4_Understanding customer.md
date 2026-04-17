# Understanding customer

## Intent Classification

*Summary:* This project is an introduction to deep learning and NLP: recurrent neural nets (RNN), LSTM, Transformer, BERT.

💡 [Tap here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave your feedback on the project**. It's anonymous and helps our team improve your educational experience. We recommend you complete the survey immediately after completing the project.

## Contents

1. [Chapter I](#chapter-i) \
   1.1. [Preamble](#preamble)
2. [Chapter II](#chapter-ii) \
   2.1. [Introduction](#introduction)
3. [Chapter III](#chapter-iii) \
   3.1. [Rules of project](#rules-of-project)
4. [Chapter IV](#chapter-iv) \
   4.1. [Instructions](#instructions)
5. [Chapter V](#chapter-v) \
   5.1. [Mandatory part](#mandatory-part)
6. [Chapter VI](#chapter-vi) \
   6.1. [Bonus part](#bonus-part)

## Chapter I

How to learn at “School 21”:

- Here, you’ll find a unique learning experience with a lot of freedom. You’re given a task and left to find your own way to solve it, using whatever resources work best for you — whether that’s the Internet or AI tools like GigaChat. Just be mindful of information quality: verify, think critically, analyze, and compare.
- Peer-to-peer (P2P) learning is the exchange of knowledge and experience with peers, where everyone acts as both mentor and student. This approach allows you to gain a deeper understanding of the material by learning from one another.
- Feel free to ask for help: around you are peers who are also navigating this path for the first time. Share your own experience and ideas with others. Join Rocket.Chat to stay updated with the latest community announcements.
- Your learning is meaningless if you just copy someone else’s solutions. When receiving help from others, always make sure you fully understand the “why”, “how”, and “purpose” behind the solution. Don’t be afraid to make mistakes.
- Does the task seem impossible? Take a break, get some fresh air and clear your mind — this has helped many people. Maybe after that, the solution will come to you naturally.
- The learning process is just as important as the result. It’s not just about completing the task — it’s about understanding HOW to solve it.

### Preamble

The story of humans trying to create an AI agent that can have a meaningful conversation with us began many years ago. One of the most prominent examples is ELIZA. It is an NLP computer program created in the mid-60s that simulated conversations with a therapist.

![0](assets/img_3005.png)

The author of the program identified 5 main problems that needed to be solved to create such a program: 1) the identification of critical words; 2) the discovery of a minimal context; 3) the choice of appropriate transformations; 4) the generation of responses appropriate to the transformation; or 5) in the absence of critical words and the provision of an ending capacity for ELIZA scripts. He solved them through a script of instructions on how to respond to user input.

Today, chatbots are ubiquitous, but the principles are still almost the same when we talk about chatbots that help automate support. The first thing we need to do is classify the intent — what the user wants from us. The phrases can be
"What's the weather like?" or "What's the temperature right now?" or "Is it raining?" but the intent is still the same — the user is interested in the weather. The second thing is that we need to generate a response (or extract it from somewhere) and send it back to the user.

## Chapter II

### Introduction

You are already familiar with the basics of NLP and neural networks. In this project, you will work with more advanced people — applying deep learning algorithms to an intent classification problem.

In deep learning, we have specific architectures for NLP tasks. Why is that? Well, text is a different data structure than ordinary tables. It is sequential. The order of words matters. It has context, which may appear in one sentence and then be used in another. Generic architectures like fully connected neural networks do not take this into account.

One architecture that can help us solve NLP problems better is RNN (recurrent neural net). It is sequential. It can work with text word by word or letter by letter. But it has no memory to store any useful context.

So another architecture was invented — [LSTM](https://colah.github.io/posts/2015-08-Understanding-LSTMs/) (Long Short-Term Memory). It is even more complicated. What it does is it tries to find optimal weights for different gates that are used to send the signal on, store it, stop it, etc.

Both architectures are time-consuming because of their sequential nature. And time is important — because the more iterations you can do in time, the faster you get good results.

The breakthrough came with the Transformers and their attention mechanism. [Transformers](https://medium.com/mlearning-ai/long-short-term-memory-networks-are-dying-whats-replacing-it-5ff3a99399fe)
do not use recursion. Instead of processing each word sequentially, Transformers process the entire sequence at once to create an "attention matrix" where each output is a weighted sum of the inputs. It is a faster architecture, and it works better with context.

The most prominent example of the Transformer architecture is [BERT](https://jalammar.github.io/illustrated-bert/) (Bidirectional En-coder Representations from Transformers). The main technical innovation of BERT is the application of Transformer's bidirectional training to language modeling.

There are some other architectures that show promising results, but they are beyond the scope of this project. However, one fact worth mentioning is that training such models can be [quite expensive](https://syncedreview.com/2019/06/27/the-staggering-cost-of-training-sota-ai-models/). But there is a way — transfer learning. You can use a pre-trained model and fine-tune it on your dataset, optimizing only a small fraction of the weights. This lifehack can produce shockingly good results.

This was a short introduction to deep learning and NLP. It covers all the important stuff from the helicopter view. Now you know where to start your own journey of mastering the skills and knowledge of this field.

## Chapter III

### Rules of project

The goal of this project is to give you a first approach to Deep learning algorithms applied to NLP tasks. You will try to preprocess text data and train different architectures for intent classification: RNN, LSTM, BERT.

## Chapter IV

### Instructions

- This project will be evaluated by humans only. You are free to organize and name your files as you wish.
- Here and throughout, we use Python 3 as the only correct version of Python.
- For training deep learning algorithms you can try [Google Colab](https://colab.research.google.com/). It offers free kernels (runtime) with GPU that are faster than CPU for such tasks.
- The standard does not apply to this project. However, you are asked to be clear and structured in your source code design.
- Place the datasets in the **data** subfolder.

## Chapter V

### Mandatory part

#### a. Task

In this project, you will work on intent classification. This task may be part of a larger project to create a chatbot or virtual assistant. The problem is that people may use different phrases and words to ask for something that is really the same in terms of the answer. "Is it raining?" or "What is the temperature right now?" can lead to a weather application or a weather forecast. The better you can classify intentions, the more impact you can have with a chatbot or virtual assistant.

To do this, you need to try different architectures:

1. RNN,
2. LSTM,
3. BERT.

#### b. Dataset

You will work with the dataset of intents used in a bike shop chatbot. The phrases are labeled with intents in the training file. And you have to make predictions for the test file.

> **Note:** You can find the dataset on the project page:
>
> 1. intents\_test.csv;
> 2. intents\_train.csv.

#### c. Implementation

You can work in the [Google Colab](https://colab.research.google.com/). It provides Jupyter notebooks with GPU Runtime. GPU is more efficient than CPU for Deep learning tasks. You can install any additional packages directly from the cells in the notebooks.

You can use any framework you like: PyTorch, TensorFlow, Keras, etc.

**Fallback Intent**

In the test file, there are several sentences that are not from any intent from the train subset. In our hidden file, they are labeled "Fallback Intent". This is widely used in chatbots. If your chatbot is "not sure" about its prediction, it's a good practice to send back to the user something like "I couldn't understand you. Please rephrase." or simply redirect the request to a human. Keep this in mind, because the score of your predictions will depend on the fallback intent as long as it exists in the test file.

**Research Journal**

You should keep a research journal. You will try different architectures with different weights, number of layers, etc. It is easy to get lost in the chaos and lose track of where your best solutions are. Your journal should track all the changes you make: architecture, weights, preprocessing, number of layers, framework, etc. and of course the metrics on the training and validation subset.

#### d. Submission

Save your model in Pickle format. Your peer will load it and use it to make predictions again for the test dataset. The predictions should be saved in a file named `intents.csv`.

You must achieve an accuracy of at least 0.8 on the test dataset.

Your repository should contain one or more notebooks with your solutions.

## Chapter VI

### Bonus Part

- Try using CNNs for intent classification.
- Try to extend the training dataset by adding more different phrases and corresponding intents to get better results.
- Try to get an even better accuracy on the test dataset — 0.873.