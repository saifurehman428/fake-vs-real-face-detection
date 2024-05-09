# GAN-Based Image Detection with CNN Models

## Introduction
With the advancements in AI, particularly in generative adversarial neural networks (GANs), the quality of generated images has reached a point where distinguishing between real and fake images is challenging. This study focuses on training various convolutional neural network (CNN) models to detect GAN-generated images using a large dataset of real and fake human faces. Additionally, a cropping technique is proposed to increase the accuracy of these models by focusing on specific regions, such as the eyes.

## Dataset
We used the "All GAN Data" dataset, which contains around 262,000 fake and real images. The data is open source and available on Kaggle. The dataset includes training, validation, and testing subsets, with a total size of around 12GB.

## Methodology
GAN-generated images often replicate most parts of the human face accurately, but they tend to struggle with certain features, like the eyes. The eyes in GAN-generated images can appear "painted" or unnatural due to fewer textures and less natural reflections.

The proposed methodology focuses on cropping the central region of the face to include only the eyes, thereby directing the CNN's attention to this critical area. This approach aims to leverage the differences in realism between real and fake eyes to improve the accuracy of fake image detection.

## Training
We trained GoogleNet, AlexNet, and VGG-16 on the training dataset, monitoring the training process with the validation dataset. The first round of training was conducted without any cropping applied, yielding the following results:

| Model    | Validation Accuracy | Test Accuracy |
|----------|--------------------|---------------|
| GoogleNet | 96.34%              | 97.12%         |
| AlexNet   | 96.82%              | 97.54%         |
| VGG-16    | 95.88%              | 96%            |

Next, we applied the proposed cropping technique, focusing solely on the eyes of each image. This involved cropping the central part of the image and normalizing it with a mean of (0.5, 0.5, 0.5) and standard deviation of (0.5, 0.5, 0.5). Here are the results after applying the proposed methodology:

| Model    | Validation Accuracy | Test Accuracy |
|----------|--------------------|---------------|
| GoogleNet | 96.89%              | 98.01%         |
| AlexNet   | 97.31%              | 97.97%         |
| VGG-16    | 95.33%              | 95.07%         |

## Results and Discussion
With the proposed methodology, GoogleNet and AlexNet showed a slight improvement in accuracy, while VGG-16's accuracy decreased. The results suggest that focusing on specific facial features, like the eyes, can lead to better performance for some CNN models. However, deep networks like VGG-16, which use several layers of 3x3 convolutions followed by pooling layers, might be excessive for smaller images like those obtained after cropping, especially if there are too many down-sampling layers. This could explain why VGG-16 underperformed compared to GoogleNet and AlexNet.

Overall, the proposed methodology shows promise in improving the accuracy of fake image detection using CNN models, particularly GoogleNet and AlexNet.
