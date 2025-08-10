## Info about task

This folder contains Python files that compare the following CNN models on a binary image classification task: 

1. VGG (1 block)
2. VGG (3 blocks)
3. VGG (3 blocks) with data augmentation
4. Transfer learning using VGG16 or VGG19 with tuning all layers (including tuning convolution layers) 
5. Transfer learning using VGG16 or VGG19 with tuning only final MLP layers (excluding convolution layers)

For 4. and 5. I have utilised VGG16 instead of 19. A handmade 2-class dataset has been created for the purpose and can be referred in this folder. 80% of the dataset has been reserved for training purposes. Code has been run and tested on Google Colab using CPU runtime type.

## Architecture of VGG16 and VGG19:

* VGG16 is already pre-trained on ImageNet dataset. VGG16 consists of 16 layers (13 convolutional and 3 fully connected), whereas VGG-19 consists of 19 layers (16 convolutional and 3 fully connected). The convolutional layers are the "feature-extractor" part and the fully connected layers are the "classifier" part. Each layer consists of a convolutional layer followed by a max-pooling layer. The convolutional layers use 3x3 filters with a stride of 1 and padding of 1. The max-pooling layers use 2x2 filters with a stride of 2. VGG-16 has two convolutional layers in each block, while VGG-19 has three convolutional layers in each block.

* VGG1 has a single convolutional layer with 32 filters (size = 3x3) followed by max pooling layer (size = 2x2) followed by a dense layer of 128 neurons (activation = relu) followed by a final dense layer of one output neuron (activation = signmoid).

* VGG3 has 3 convolutional layers, first with 32 filters, second with 64 filters and third with 128 filters, followed by the same dense layers as above.

* Loss used = binary cross entropy.

## Result

The following is the result of the analysis:

![image](https://github.com/KaveriVisavadiya/projects/assets/145709121/12f2b2ab-c977-48c4-acb7-3f134bcd0f41)

Expected and observed result of testing accuracy for models: 

### VGG16_MLP_layers > VGG16_all_layers > VGG3_data_augmentation > VGG3 > VGG1.

* Data augmentation is expanding the size of the training dataset by modifying some of the original images via shifting/rotation, etc. This can improve the ability of VGG3 to generalise what it has learnt to new images, improving its testing accuracy.
* VGG16 (pre-trained on ImageNet) gives higher testing accuracy than VGG3 or VGG1 because the former has higher depth of convolutional layers (13 conv layes vs. 3 or 1 respectively), so it has already learnt higher representations of images -> this takes advantage of the "Transfer Learning" of the pre-trained VGG16 convolutional layers. by simply modifying the "classifier" (FCN) part of the VGG, we can interpret the features extracted from the "feature extractor" (conv) layer.
* Training only fully-connected layers of VGG16 gives higher testing accuracy than fine-tuning all layers of VGG16 (fully-connected + convolutional) because the convolutional network is already trained on the ImageNet dataset and our binary dataset is not large enough or informative enough to add any significant addition to the already learnt/pre-trained representations, moreover doing so is expensive in time and compute.
* VGG1 has the highest number of parameters. This is because there is only one convolutional block, which means that the image size will not reduce by much by the time it reaches the fully connected layer which will create a lot of params within the dense layer. In contrast VGG16 has 13 convolutional layers which means that the image size will reduce drastically by the time its reaches the fully connected layer, reducing the number of params.

## References

1. Code for model creation has been referred from the website https://machinelearningmastery.com/how-to-develop-a-convolutional-neural-network-to-classify-photos-of-dogs-and-cats/
2. Architecture has been referred from https://www.kaggle.com/discussions/getting-started/518971 
