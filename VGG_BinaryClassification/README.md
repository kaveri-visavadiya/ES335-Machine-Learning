Some info:

VGG stands for Visual Geometry Group. VGG-16 and VGG-19 have 16 and 19 convolutional layers respectively.

This folder contains Python files that compare the following CNN models on a binary image classification task: 

1. VGG (1 block) 
2. VGG (3 blocks)
3. VGG (3 blocks) with data augmentation
4. Transfer learning using VGG16 or VGG19 with tuning all layers (including tuning convolution layers)
5. Transfer learning using VGG16 or VGG19 with tuning only final MLP layers (excluding convolution layers)

A handmade 2-class dataset has been created for the purpose and can be referred in this folder. 80% of the dataset has been reserved for training purposes. Code for model creation has been referred from the website https://machinelearningmastery.com/how-to-develop-a-convolutional-neural-network-to-classify-photos-of-dogs-and-cats/. Code has been run and tested on Google Colab using CPU runtime type.

The following is the result of the analysis:
![image](https://github.com/KaveriVisavadiya/projects/assets/145709121/12f2b2ab-c977-48c4-acb7-3f134bcd0f41)

