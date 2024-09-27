# Muffin vs Chihuahua

<img src="https://github.com/user-attachments/assets/b06b782c-cc77-4f19-8469-282d942f8fb5" width=400>

## Overview
This project involves the application of machine learning methods in the binary classification of images of muffins and chihuahuas using neural networks. The goal is to accurately distinguish between images of muffins and chihuahuas using advanced neural network architectures.

## Problem Statement
In the world of image classification, certain objects can look surprisingly similar, creating a challenge for both humans and machine learning models. A classic example is the difficulty in distinguishing between images of muffins and chihuahuas. This project aims to tackle this problem by leveraging neural networks to build a robust classifier.

## Project Structure

- **Data**: The dataset used in this project can be downloaded from the [Kaggle repository](https://www.kaggle.com/datasets/samuelcortinhas/muffin-vs-chihuahua-image-classification). Ensure that the dataset is placed in your Google Drive under `/Datasets/archive`.
  
- **Configurations**: The architecture for training and testing can be configured by editing the `architecture` entry in the `configs` dictionary located in the setup section. The accepted values are:
  - `nn` (Neural Network)
  - `cnn` (Convolutional Neural Network)
  - `vit` (Vision Transformer)

## Getting Started

1. **Clone the repository**:
    ```bash
    git clone https://github.com/mirtorande/muffin-vs-chihuahua.git
    cd muffin-vs-chihuahua
    ```

2. **Download the dataset**:
    Download the dataset from the [Kaggle repository](https://www.kaggle.com/datasets/samuelcortinhas/muffin-vs-chihuahua-image-classification) and upload it to your Google Drive in the following folder structure:
    ```
    /Datasets/archive
    ```

3. **Install dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

4. **Run the setup**:
    ```python
    python setup.py
    ```

## Methodology

The project employs three distinct neural network architectures to tackle the classification problem:

### Fully Connected Neural Network

The first network we propose is a Fully Connected Neural Network. Each neuron layer is fully connected with the following. It grants a simple architecture with no inductive bias for images. This fully connected NN represents our baseline for later comparisons with other architectures.

#### Architecture Details

The network we propose accepts the input as RGB triplets, which are then augmented and converted into greyscale. The input gets flattened before being processed further. Following the input layer, there are two dense layers with ReLU activation. The number of neurons for the first is four times the image’s length in pixels (96 * 4 = 384). The second layer has a number of neurons equal to the image’s edge in pixels (96). The two dense layers are followed by a dropout layer. The output neuron is set to have a sigmoid activation function.

#### Results

- **Validation Accuracy**: 0.67
- **5-Fold CV Accuracy**: 0.6652
- **Test Accuracy**: 0.6394

### Convolutional Neural Network

The second network we propose is a Convolutional Neural Network. This network architecture is intended for image recognition tasks. It scales far better than a fully connected neural network with respect to image dimension.

#### Architecture Details

As in the previous model, the input is accepted as RGB triplets and passed to the augmentation layer. The first convolution produces a feature map of half the size of the input image where 64 filters are applied. The normalized data is then passed to an activation layer where ReLU is being used. This is followed by a series of convolution, pooling, and activation layers.

#### Results

- **Validation Accuracy**: 0.9
- **5-Fold CV Accuracy**: 0.8923
- **Test Accuracy**: 0.8699

### Vision Transformer

The Vision Transformer (ViT) is the state of the art for image recognition tasks. Literature has shown that a ViT can surpass a CNN in performance on large-scale problems.

#### Architecture Details

The input is taken as RGB triplets, which are immediately augmented, divided into patches, and then encoded. What follows is a pattern of layers where attention is involved. Input vectors are normalized and fed to the self-attention layer. After the repeating pattern of layers, data gets flattened and fed to a series of dropout and dense layers.

#### Results

- **Validation Accuracy**: 0.88
- **5-Fold CV Accuracy**: 0.8059
- **Test Accuracy**: 0.8725

## Conclusion

This project demonstrates the effectiveness of different neural network architectures in solving the binary classification problem of distinguishing between muffins and chihuahuas. The Vision Transformer (ViT) model achieved the highest accuracy, showcasing the potential of transformer-based models in image classification tasks.

## Report

The detailed report for this project is available in the root folder.

## Acknowledgements

We would like to thank the contributors of the [Kaggle dataset](https://www.kaggle.com/datasets/samuelcortinhas/muffin-vs-chihuahua-image-classification) for providing the essential data for this project.
