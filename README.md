# 🐱 Cat vs Dog vs Neither — Image Classifier 🐶

A hands-on machine learning project built to learn the complete workflow of image classification, from preparing a dataset and training a model to evaluating it and deploying it as a simple web application.

## 📌 Project Overview

The first version of this project was a **Cat vs Dog** classifier. During testing, I discovered an important limitation: when given an image that was neither a cat nor a dog, the model was still forced to choose either CAT or DOG.

For example, a car was incorrectly classified as a DOG.

To address this, I expanded the project into a **three-class image classifier**:

* 🐱 CAT
* 🐶 DOG
* 🚫 NEITHER

The NEITHER class contains diverse images such as cars, people, food, buildings, landscapes, other animals, and everyday objects.

## 🎯 Learning Objectives

This project was created as a practical learning exercise to understand:

* Image classification
* Dataset preparation and labeling
* Training and validation splits
* PyTorch datasets and DataLoaders
* Transfer learning
* Hugging Face Transformers
* ResNet-50
* GPU-based model training
* Model evaluation
* Confusion matrices and classification reports
* Prediction confidence
* Real-world model testing
* Basic ML model deployment with Gradio

## 🛠️ Technologies Used

* Python
* PyTorch
* Hugging Face Transformers
* ResNet-50
* scikit-learn
* PIL
* Google Colab
* Google Drive
* Gradio

## 📊 Dataset

The final dataset contained **14,700 images**, balanced across three classes:

| Class     |     Images |
| --------- | ---------: |
| CAT       |      4,900 |
| DOG       |      4,900 |
| NEITHER   |      4,900 |
| **Total** | **14,700** |

The dataset was divided into:

* **80% training:** 11,760 images
* **20% validation:** 2,940 images

The NEITHER class was constructed from seven categories:

* Cars
* People
* Food
* Buildings
* Landscapes
* Other animals
* Objects

The original Cat and Dog images were sampled from a larger collection to create a balanced dataset.

## 🤖 Model

The project uses **ResNet-50** with transfer learning.

The first model was trained for two classes:

```text
0 = CAT
1 = DOG
```

The model was then upgraded to three classes:

```text
0 = CAT
1 = DOG
2 = NEITHER
```

The trained Cat/Dog model was used as the starting point for the three-class model, while the final classification layer was replaced to output three classes.

## 📈 Validation Results

The three-class model achieved:

**98.88% validation accuracy**

Classification results:

| Class   | Precision | Recall | F1-score |
| ------- | --------: | -----: | -------: |
| CAT     |    99.59% | 98.27% |   98.92% |
| DOG     |    98.88% | 98.98% |   98.93% |
| NEITHER |    98.19% | 99.39% |   98.78% |

The validation set contained 2,940 images, with 980 images from each class.

## 🧪 Real-World Testing

I also tested the model on images outside the validation set.

| Image      | Prediction | Confidence |
| ---------- | ---------- | ---------: |
| Cat        | CAT        |       100% |
| Blurry dog | DOG        |        66% |
| Car        | NEITHER    |        91% |
| Building   | NEITHER    |        99% |
| Tree       | NEITHER    |        98% |
| Cat + Dog  | DOG        |        76% |

One of the main observations was the improvement from the original two-class model.

In the original model, a car was classified as:

**DOG — 73.74%**

After introducing the NEITHER class, the same type of image was classified as:

**NEITHER — 91%**

## ⚠️ Limitations

This project is a learning project and is not intended to be a production-ready image classification system.

Some limitations include:

* The model produces one final class for each image.
* An image containing both a cat and a dog cannot currently be represented as two separate predictions.
* Performance on real-world images may differ from the validation accuracy.
* The NEITHER class contains selected categories and may not represent every possible image that is neither a cat nor a dog.
* Confidence scores should not be interpreted as guaranteed probabilities of correctness.

For images containing multiple relevant objects, a future version could explore **multi-label classification or object detection**.

## 🌐 Demo

The model was connected to a simple **Gradio** interface that allows users to upload an image and receive predictions for CAT, DOG, and NEITHER.

## 📚 What I Learned

This project helped me understand the practical machine learning workflow:

```text
Problem Definition
       ↓
Dataset Collection
       ↓
Data Preparation
       ↓
Labeling
       ↓
Train / Validation Split
       ↓
Preprocessing
       ↓
Model Selection
       ↓
Training
       ↓
Evaluation
       ↓
Real-World Testing
       ↓
Deployment
```

A particularly important lesson was that a high validation accuracy does not necessarily mean a model will behave perfectly on every real-world image. Testing the model with unfamiliar and difficult images helped reveal its strengths and limitations.

## 🚀 Future Improvements

Possible future improvements include:

* Testing with a larger and more diverse dataset
* Adding more challenging real-world images
* Data augmentation
* Hyperparameter tuning
* Training for multiple epochs
* Exploring multi-label classification
* Exploring object detection for images containing both cats and dogs
* Deploying the model as a more permanent web application

## 👩🏽‍💻 About This Project

This project was developed as a hands-on learning exercise to build practical understanding of machine learning and computer vision.

Rather than focusing only on achieving a high accuracy score, the goal was to understand the process of building, evaluating, testing, and improving a machine learning model.
