
#  Quran Recitation Audio Classification

Identifying Qur’an reciters from short audio clips using deep learning on mel-spectrogram images.

---

##  Overview

This project focuses on classifying Qur’an reciters based on their voice.
The workflow includes:

* Loading audio files and labels from a dataset.
* Visualizing how many samples each reciter has.
* Converting each audio clip into a mel-spectrogram image.
* Building a custom dataset structure for feeding the spectrograms into a neural network.
* Training a Convolutional Neural Network (CNN) for multi-class classification.
* Evaluating the model on a test set and visualizing training performance.

The final model achieves **~99% test accuracy**, demonstrating strong performance in recognizing reciters from short audio segments.

---

##  Dataset

The dataset includes:

* A CSV file containing paths to recitation audio files.
* A class label for each file indicating the name of the reciter.

A class distribution plot is used to show how many samples exist for each reciter.
This ensures awareness of dataset balance before training.

---

##  Audio Preprocessing

Each audio clip undergoes a series of transformations:

* Loaded at a fixed sample rate.
* Trimmed or padded to a consistent duration.
* Converted into a mel-spectrogram, which represents frequency intensity over time.
* Resized into a fixed image shape to serve as CNN input.

These spectrograms become the “images” on which the model is trained.

---

##  Dataset Handling

A custom dataset structure is created to:

* Store file paths and class labels.
* Convert each audio file into a spectrogram.
* Cache spectrograms for faster training.
* Return both the spectrogram and its corresponding label when requested by the model.

This setup ensures consistency and efficiency during training.

---

##  Model Architecture

The model consists of:

1. **Three convolutional blocks**
   Each block includes a convolution layer followed by a pooling operation, which reduces spatial dimensions and extracts features.

2. **A deep fully connected classification head**
   The final layers progressively reduce the feature representation and apply dropout for regularization.

3. **An output layer with 12 units**
   Each output corresponds to one reciter.

A summary of the model reveals approximately **139 million trainable parameters**, mainly contributed by the large fully connected layers.

---

##  Training

The audio classification model is trained using:

* A stratified train/validation/test split to maintain class balance.
* A multi-epoch training loop that records:

  * Training loss
  * Validation loss
  * Training accuracy
  * Validation accuracy

Performance metrics are plotted over the epochs to track learning progress.

---

##  Results

### ✔ Test Accuracy

The trained model reached a test accuracy of **approximately 0.99**, indicating excellent generalization.

### ✔ Loss Curves

The training and validation loss curves decrease smoothly, reaching very low values.

### ✔ Accuracy Curves

Both training and validation accuracy climb rapidly, achieving nearly perfect classification after several epochs.

These results confirm the model is learning effectively while maintaining stable performance across different dataset splits.

---


