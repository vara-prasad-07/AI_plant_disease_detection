# Plant Disease Detection using CNN

This repository contains a Convolutional Neural Network (CNN) based approach to detect plant diseases from leaf images. By leveraging a deep learning model, users can quickly identify if a leaf is diseased or healthy. The project includes a simple web app for ease of use.

---

## Table of Contents
1. [Introduction](#introduction)
2. [Features](#features)
3. [Dataset](#dataset)
4. [Project Structure](#project-structure)
5. [Installation](#installation)
6. [Usage](#usage)
7. [Model Details](#model-details)
8. [Contributing](#contributing)
9. [License](#license)

---

## Introduction
Plant diseases can severely affect agricultural yield and quality. Early detection is crucial for effective management. This project uses a CNN model trained on images of plant leaves to classify them into different disease categories or identify them as healthy.

## Features
- **Deep Learning Model**: A CNN architecture trained to classify plant leaf images.
- **Web App Interface**: Simple front-end to upload an image and get predictions.
- **Scalable Deployment**: Includes a `Procfile.txt` for deploying on platforms like Heroku.
- **Easy to Customize**: Jupyter notebook for training and experimenting with the model.

## Dataset
This project relies on a labeled dataset of plant leaf images, which you can download from [Kaggle](https://www.kaggle.com/) (for example, the “PlantVillage” dataset or any other relevant plant disease dataset).

> **Note**: Make sure to download the dataset from Kaggle and place it in the appropriate directory (e.g., `data/`) before training or running the application.

## Project Structure

. ├── app.py # Flask or other web framework application file
  ├── index.html # Front-end file for uploading images
  ├── model.ipynb # Jupyter notebook used for training and experimenting with the CNN
  ├── requirements.txt # Python dependencies
  ├── Procfile.txt # Deployment configuration (Heroku or similar)
  └── README.md # Project documentation (this file)

bash
Copy

## Installation
1. **Clone this repository**  
   ```bash
   git clone https://github.com/vara-prasad-07/AI_plant_disease_detection.git
   
Create and activate a virtual environment (optional but recommended)

bash
Copy
python3 -m venv venv
source venv/bin/activate  # On Linux/Mac
# or
venv\Scripts\activate     # On Windows
Install dependencies

bash
Copy
pip install -r requirements.txt
Download the dataset from Kaggle

Visit Kaggle and download your desired plant disease dataset.

Unzip or place the files in a data/ folder at the root of this project.

Usage
Train the Model (optional if you already have a saved model)

Open model.ipynb in Jupyter Notebook or another environment.

Run the cells to train the CNN model on your dataset.

This process will generate a saved model file (e.g., model.h5).

Run the Web App

Ensure your model file (e.g., model.h5) is in the correct path used by app.py.

Start the Flask server:

1. **how to run python file**
   ```bash
   python app.py
# how to test
Open your web browser and go to http://127.0.0.1:5000 (or the displayed address).

Upload a leaf image and see the predicted disease classification.

##Model Details
Architecture: A Convolutional Neural Network with multiple convolutional layers, pooling layers, and dense layers at the end for classification.

Frameworks: TensorFlow/Keras.

Hyperparameters: Learning rate, batch size, and number of epochs can be tuned in model.ipynb.

Performance: Varies based on dataset quality, model architecture, and hyperparameters.




