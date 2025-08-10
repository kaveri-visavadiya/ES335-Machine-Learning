## Info about task

This folder contains Python files that compare the following CNN models on a binary image classification task: 

1. VGG (1 block) 
2. VGG (3 blocks)
3. VGG (3 blocks) with data augmentation
4. Transfer learning using VGG16 or VGG19 with tuning all layers (including tuning convolution layers) 
5. Transfer learning using VGG16 or VGG19 with tuning only final MLP layers (excluding convolution layers)

For 4. and 5. I have utilised VGG16 instead of 19. A handmade 2-class dataset has been created for the purpose and can be referred in this folder. 80% of the dataset has been reserved for training purposes. Code has been run and tested on Google Colab using CPU runtime type.

## Architecture of VGG16 and VGG19:

VGG-16 consists of 16 layers (13 convolutional and 3 fully connected), whereas VGG-19 consists of 19 layers (16 convolutional and 3 fully connected). Each layer consists of a convolutional layer followed by a max-pooling layer. The convolutional layers use 3x3 filters with a stride of 1 and padding of 1. The max-pooling layers use 2x2 filters with a stride of 2. VGG-16 has two convolutional layers in each block, while VGG-19 has three convolutional layers in each block.

## Result

The following is the result of the analysis:
![image](https://github.com/KaveriVisavadiya/projects/assets/145709121/12f2b2ab-c977-48c4-acb7-3f134bcd0f41)

Expected and observed result of testing accuracy for models: 

### VGG16_MLP_layers > VGG16_all_layers > VGG3_data_augmentation > VGG3 > VGG1.

* VGG16 gives higher testing accuracy than VGG3 or VGG1 because the former has a 
* Training only fully-connected layers of VGG16 gives higher testing accuracy than fine-tuning all layers (fully-connected + convolutional) because the convolutional network is already trained on the ImageNet dataset and changing these weights is expensive and loses information

## References

1. Code for model creation has been referred from the website https://machinelearningmastery.com/how-to-develop-a-convolutional-neural-network-to-classify-photos-of-dogs-and-cats/
2. Architecture has been referred from https://www.kaggle.com/discussions/getting-started/518971 
1. 
