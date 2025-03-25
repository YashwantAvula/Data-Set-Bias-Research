# Dataset Bias in Deep Learning

This project investigates the presence and impact of dataset bias in deep learning models. Despite advances in dataset construction and model architecture, our study finds that convolutional neural networks (CNNs) can still detect subtle biases across well-known datasets like Pascal VOC, ImageNet, and Flickr30K — achieving high classification accuracy by identifying the source dataset of an image.

---

## Objectives

- Examine if modern CNNs can classify datasets based solely on images, indicating inherent bias.
- Compare performance across architectures (AlexNet, VGG-16, ResNet-50) and training sizes.
- Assess robustness under image corruptions and data augmentations.
- Analyze how model size affects bias detection accuracy.

---

## Datasets Used

- **Pascal VOC:** Diverse objects and scenes, strong benchmark for detection/classification.
- **ImageNet (64x64):** Large-scale labeled dataset with extensive variety.
- **Flickr30K:** Everyday scenes with rich textual captions, diverse content.

---

## Models Implemented

- **AlexNet:** Adapted to 64×64 images, standard normalization, dropout regularization.
- **VGG-16:** Deep stack of 3x3 convolutions with ReLU activations and max pooling.
- **ResNet-50:** Residual connections to counter vanishing gradients, global average pooling.

> All models were trained with Adam optimizer (LR = 0.001) using shuffled data loaders and batch normalization.

---

## Preprocessing

- **Image Resizing:** All images were standardized to 64×64 pixels for computational efficiency.
- **Normalization:** Used ImageNet standards:  
  `mean = [0.485, 0.456, 0.406]`,  
  `std = [0.229, 0.224, 0.225]`

---

## Key Results

### Dataset Classification Accuracy

| Dataset Combo                 | Accuracy (%) |
|------------------------------|--------------|
| Pascal + ImageNet            | 92.83        |
| Pascal + Flickr              | 63.20        |
| ImageNet + Flickr            | 90.99        |
| All Three Combined           | 78.08        |

### Architecture Comparison

| Model     | Accuracy (%) |
|-----------|--------------|
| AlexNet   | 78.08        |
| VGG-16    | 50.00        |
| ResNet-50 | 85.68        |

### Training Size Comparison

| Model     | Size  | Accuracy (%) |
|-----------|-------|---------------|
| AlexNet   | 10K   | 59.76         |
|           | 20K   | 78.08         |
|           | 29K   | 85.85         |
| ResNet-50 | 10K   | 79.45         |
|           | 20K   | 85.68         |
|           | 29K   | 84.06         |

### Effect of Image Corruptions

| Corruption                  | Accuracy (%) |
|----------------------------|--------------|
| None                       | 78.08        |
| Gaussian Noise             | 50.00        |
| Gaussian Blur              | 65.00        |
| Color Jitter (0.75)        | 0.00         |
| Downsampled (32x32)        | 0.00         |
| Upsampled (227x227)        | 50.00        |

---

## Insights

- Neural networks can reliably detect dataset origin, even at low resolution, revealing subtle biases.
- Data augmentation (e.g., random cropping) can help but doesn't fully eliminate bias detectability.
- Larger models aren't always more accurate at dataset classification—model size vs performance trade-offs exist.

---

## Authors

- Yashwant Sai Avula  
- Yash Sanghani  
- Siddharth Yalamanchali  
- **Course:** Data Mining | Group 7  
- **Instructor:** [Add instructor name if applicable]

---

## Conclusion

This project highlights that despite efforts to create unbiased datasets, CNNs can still pick up on dataset-specific patterns. These findings encourage the machine learning community to critically reassess how we define, clean, and standardize datasets.
