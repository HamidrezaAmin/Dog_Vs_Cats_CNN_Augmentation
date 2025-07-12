
# Dogs vs. Cats Classification with CNN and Data Augmentation

This project presents a Convolutional Neural Network (CNN) for binary image classification (dogs vs. cats). 
In this version, **data augmentation** techniques are employed to reduce overfitting and improve generalization, 
resulting in noticeable validation accuracy gains.

## Dataset

- A subset of the [Dogs vs. Cats dataset](https://www.kaggle.com/c/dogs-vs-cats/data) was used.
- Due to limited **RAM, storage, and GPU resources**, only **1000 images per category** (cat/dog) were used.
- We used `ImageDataGenerator` to load **batches of 20-32 images** during training to avoid RAM overflow.

## Model Architecture

- Conv2D → MaxPooling2D (4 times)
- Flatten → Dropout(0.5)
- Dense (512, relu) → Dense (1, sigmoid)
- Loss: `binary_crossentropy`
- Optimizer: `RMSprop` with learning rate 1e-4

## Data Augmentation

Applied only on training data using:
- rotation, width/height shift
- shear, zoom, horizontal flip

This helped expose the model to more variation, improving validation performance.

## Performance Comparison

| Model Variant     | Training Accuracy | Validation Accuracy |
|-------------------|-------------------|----------------------|
| With Dropout Only | 99.37%            | 77.85%               |
| With Augmentation | 81.03%            | **81.80%**           |

> 🔍 While augmentation reduced training accuracy (due to less memorization), it improved validation accuracy — indicating better generalization.

## Summary

- Dropout helped mitigate overfitting.
- Augmentation introduced image diversity, leading to a **~4% gain** in validation accuracy.
