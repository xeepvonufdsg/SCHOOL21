# Fried Eggs

## Fried Eggs Quality Assessment

*Summary: this project is an introduction to Deep Learning and computer vision (CNN, instance segmentation, object detection, data labeling).*

## Contents

1. [Chapter I](#chapter-i) \
   1.1. [Preamble](#preamble)
2. [Chapter II](#chapter-ii) \
   2.1. [Introduction](#introduction)
3. [Chapter III](#chapter-iii) \
   3.1. [Goals](#goals)
4. [Chapter IV](#chapter-iv) \
   4.1. [General instructions](#general-instructions)
5. [Chapter V](#chapter-v) \
   5.1. [Mandatory part](#mandatory-part)
6. [Chapter VI](#chapter-vi) \
   6.1. [Bonus part](#bonus-part)
7. [Chapter VI](#chapter-vi) \
   7.1. [Submission and peer-correction](#submission-and-peer-correction)

## Chapter I

How to learn at “School 21”:

- Here, you’ll find a unique learning experience with a lot of freedom. You’re given a task and left to find your own way to solve it, using whatever resources work best for you — whether that’s the Internet or AI tools like GigaChat. Just be mindful of information quality: verify, think critically, analyze, and compare.
- Peer-to-peer (P2P) learning is the exchange of knowledge and experience with peers, where everyone acts as both mentor and student. This approach allows you to gain a deeper understanding of the material by learning from one another.
- Feel free to ask for help: around you are peers who are also navigating this path for the first time. Share your own experience and ideas with others. Join Rocket.Chat to stay updated with the latest community announcements.
- Your learning is meaningless if you just copy someone else’s solutions. When receiving help from others, always make sure you fully understand the “why”, “how”, and “purpose” behind the solution. Don’t be afraid to make mistakes.
- Does the task seem impossible? Take a break, get some fresh air and clear your mind — this has helped many people. Maybe after that, the solution will come to you naturally.
- The learning process is just as important as the result. It’s not just about completing the task — it’s about understanding HOW to solve it.

### Preamble

What could be more incredible than teaching machines to see? But before we can teach someone to do something, we must first understand it. Without understanding, there can be no teaching. It's no surprise that the first breakthrough in computer vision occurred after researchers discovered in 1959 how animals, specifically cats, perceive visual information.

During an experiment, one neuron fired when the researchers slipped a new slide into the projector. This neuron was activated by "the movement of the line created by the shadow of the sharp edge of the glass slide". They later realized that there are simple and complex neurons, and that processing visual information starts with simple edges and shapes.

In 1982, another researcher discovered that we first perceive simple edges, then simple shapes, and finally, how these shapes are organized into more complex shapes and structures. This means that the processing of visual information is hierarchical. This concept became central to deep learning.

Shortly thereafter, convolutional layers began to be used in computer vision. The main idea behind them is that they are essentially rectangular receptive fields containing a weight vector (filter). These layers slide over an image and create a new representation of it through the convolutional operation.

In 1989, Yann LeCun applied the backpropagation learning algorithm with which you are already familiar to the convolutional architecture of neural networks. Since then, it has become part of the field of machine learning. Previously, researchers tried to create these filters themselves. However, in terms of quality, CNNs could not outperform other approaches or humans.

It was not until 2012 that a new architecture, AlexNet, was applied to the famous ImageNet competition and produced the best results. Since then, CNNs have become mainstream in computer vision and deep learning. Around that time, a committee of CNNs demonstrated greater-than-human accuracy in recognizing traffic signs.

Today, computer vision is widely used in healthcare, agriculture, entertainment, and the automotive industry.

## Chapter II

### Introduction

Several popular tasks in computer vision include image classification, detection, and semantic segmentation. What is the difference between them?

In **image classification**, we try to answer the question, "Does this object exist in the image?" We don't care where. In **detection** tasks, however, we care about the object's location, and the desired answer is a bounding box around the object. In **semantic segmentation** tasks, we also care about the position, and we want information about each pixel of the image: "Which object does it belong to?" **Classification** is simpler, while **segmentation** is harder. In any case, CNNs are widely used in all of them.

The central element of CNNs is the **kernel**.

![0](assets/img_1426.png)

It "looks" at the image from its own point of view (i.e., it considers the weights inside) by sliding over the image and performing simple calculations, such as the element-wise product of matrices and the sum of the results. See the example in the picture above. This process creates a feature map. This feature map can then go to the next convolutional layer or undergo other processing, such as pooling. The purpose of pooling is to reduce the size of the image. This allows the network to work with higher-level features and increases training speed. There are different types of pooling. Max pooling, for example, takes the maximum element in the receptive field frame. Average pooling takes the average of those elements.

![1](assets/img_0956.png)

The final layers of a CNN are **fully connected layers (FCN)** from a classical neural network architecture with which you are already familiar. The output from the last convolutional layer is flattened and sent to a sequence of FCN. The output of these layers is a layer with a number of neurons equal to the number of classes in your classification task.

In simple terms, that's how CNNs work. Of course, there are more sophisticated architectures and techniques, which you will learn about as you work on the project.

## Chapter III

### Goals

The goal of this project is to introduce you to Deep Learning and Computer Vision. You will help a restaurant maintain the quality of its fried eggs. To do so, you will also have to work with data labeling tools and approaches.

## Chapter IV

### General instructions

- This project will only be evaluated by humans. You may organize and name your files as you wish.
- Here and throughout, we use Python 3 as the only version of Python.
- You can use any useful framework, such as TensorFlow or PyTorch.
- The norm does not apply to this project. Nevertheless, you are asked to be clear and structured in the conception of your source code.
- Store the datasets in the **data** subfolder.

## Chapter V

### Mandatory part

#### A. Task

In this project, you will analyze photos of restaurant-made fried eggs to determine whether they are fit for consumption. There can be various issues in the cooking process, such as too few or too many yolks, some yolks being broken, or overcooking.

Here are the tasks that you need to do:

1. data labeling with instance segmentation,
2. data preprocessing,
3. fried eggs classification.

#### B. Dataset

You will work with the [dataset](https://git.21-school.ru/masters/DS8_Fried_Eggs.ID_886426/-/blob/4/./datasets/P07.%20Fried%20eggs.zip) of fried eggs. It contains 199 unlabeled images of fried eggs (train) and 65 images from the hidden test sample for which we know classes.

![2](assets/img_1361.png)

The classes are as follows:

- 0 — good fried eggs (three yolks, parsley in the center, well-cooked and looking like one whole piece, not several separate pieces);
- 1 — overcooked or overturned fried eggs;
- 2 — fried eggs with two yolks;
- 3 — fried eggs with a broken yolk;
- 4 — fried eggs with four yolks;
- 5 — fried eggs with the ingredients in the wrong position, missing ingredients, or incorrect placement or composition.

#### C. Implementation

You can work in [Google Colab](https://colab.research.google.com/) or Jupyter Notebooks on your computer.

**Data Labeling**

1. Using the six classes described above, label the images from the train sample.
2. To solve the project with good quality, you must solve the instance segmentation task. To do so, you must annotate your images with instances of different objects to show where a piece of bacon, a yolk, or a piece of parsley is located. Convert the inference annotations to polygon masks (XMLs).

![3](assets/img_7100.png)

1. Automate this process using an active learning approach to train a neural net that learns from you which objects are in the image.

**Data Preprocessing**

1. Resize the images to 1024x768.
2. Learn to crop images so that only a plate with fried eggs goes to a CNN.

![4](assets/img_2489.png)

1. Extract masks of the ingredients. Use them as an input to CNN.

![5](assets/img_7231.png)

**Classification**

1. Use raw images and masks as input for a CNN.
2. Try different approaches and algorithms. Achieve a log loss of no more than 9.56 on the test dataset.

#### D. Submission

Your repository should contain one or more notebooks with your solutions and visualizations. It should also contain a CSV file listing the filenames and their corresponding classes. You can download the template from [here](https://git.21-school.ru/masters/DS8_Fried_Eggs.ID_886426/-/blob/4/./datasets/fried_eggs.csv).

## Chapter VI

### Bonus part

- Work with data augmentation.
- Achieve a better logloss of 2.66.

## Chapter VII

### Submission and peer-to-peer evaluation

Submit your work to your Git repository as usual. Only work submitted to your repository will be graded.

Here are the points that your peer corrector will have to check:

- If images are labeled using classes and instance segmentation.
- If an active learning approach was used to automate data labeling.
- If the images were resized or cropped.
- If masks were extracted from segmentation.
- Whether the required logloss was achieved in the classification.