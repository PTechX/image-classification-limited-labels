# image-classification-limited-labels
A transfer-learning project that classifies bean leaf images into three
categories using only 60 labelled training images.
Project Overview
This project explores image classification when only a small amount of
labelled data is available. It uses the Beans dataset from Hugging
Face and a pretrained MobileNetV2 model.

The classifier predicts one of the following classes:
- angular_leaf_spot
- bean_rust
- healthy
The project was implemented and executed in Google Colab using
Python, TensorFlow/Keras, and the Hugging Face Datasets library.
Objectives
- Load and inspect the Beans image dataset.
- Select 20 training images from each class (60 images in total).
- Preprocess images into a consistent format.
- Apply transfer learning using an ImageNet-pretrained MobileNetV2
  model.
- Train a three-class classification head.
- Evaluate the model on the separate test split.
Dataset
Dataset: AI-Lab-Makerere/beans on Hugging
Face
  Split                                       Images Use
  Training                                     1,034 Source training
split; 20 images per
class are selected

  Validation                                     133 Monitor model
performance during
training
Test                                           128 Final evaluation
Only 60 images from the training split are used to train the
classification head. The validation and test splits remain separate.
Technologies Used
- Python
- Google Colab
- TensorFlow / Keras
- Hugging Face Datasets
- MobileNetV2
- NumPy
- Matplotlib
- scikit-learn
Model and Method
The project uses transfer learning:
1. Load MobileNetV2 with ImageNet-pretrained weights.
2. Freeze the MobileNetV2 base so its pretrained weights are not
   updated.
3. Add a classification head:
   - GlobalAveragePooling2D
   - Dropout(0.3)
   - Dense(3, activation="softmax")
4. Compile the model with the Adam optimiser, sparse categorical
   crossentropy loss, and accuracy metric.
5. Train for 10 epochs with a batch size of 16.
Image Preprocessing
- Convert images to RGB.
- Resize images to 224 × 224 pixels.
- Apply MobileNetV2's preprocess_input function.
- Convert class labels to integer indices.
How to Run
1. Open the project notebook in Google Colab:
   Open Image Classification
   notebook
2. Select Runtime → Run all (or run the cells in order).
3. Allow the notebook to install/import the required libraries and load
   the dataset.
4. Run the preprocessing, model-building, training, and evaluation
   cells.
5. Follow the notebook's image-upload cell to test the trained model on
   another leaf image.
A GPU runtime can be selected in Runtime → Change runtime type to
speed up model execution, if available.
Results
The recorded test-set results are:

  Metric                              Result
  Test loss                           0.5761
Test accuracy                       76.56%
Correct test predictions     98 out of 128
Per-class performance
  Class                 Precision   Recall   F1-score   Support
  angular_leaf_spot          0.78     0.81       0.80        43
bean_rust                  0.67     0.65       0.66        43
healthy                    0.85     0.83       0.84        42

The notebook also produces a confusion matrix, an accuracy curve, and
sample predictions.
Example Prediction
The recorded test example was classified as angular_leaf_spot with
68.64% confidence. A separately uploaded image was predicted as
bean_rust with 69.50% confidence; because no ground-truth label
was supplied for that image, its prediction could not be verified.
Limitations
- The model is trained using only 60 labelled images, so it may not
  capture the full variation in bean leaf images.
- Dataset images may not represent all field conditions, lighting,
  backgrounds, cameras, or bean varieties.
- The model predicts only the three classes included in the dataset.
- A high prediction confidence does not guarantee that a prediction is
  correct.
- The model is intended for learning and preliminary image screening,
  not as a replacement for expert agricultural advice.
Future Improvements
- Train with larger labelled subsets and compare the results.
- Repeat experiments with different random selections of training
  images.
- Explore data augmentation and carefully controlled fine-tuning.
- Test with more images collected under real farming conditions.
References
- Beans dataset -- Hugging
  Face
- MobileNetV2 paper (CVPR
  2018)
- TensorFlow MobileNetV2
  documentation
- MobileNetV2 preprocessing
  documentation
- Google Colab
Project: Image Classification with Limited Labels
Author: Praveena
Academic year: 2026
