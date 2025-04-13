# AI Plant Disease Detection

This repository showcases a **Vue.js** frontend and a **Python(flask)** backend for detecting plant diseases using a **Convolutional Neural Network (CNN)**. The frontend allows users to upload images of plant leaves, while the backend handles inference using a trained model.

---

## Table of Contents
1. [Overview](#overview)
2. [Project Structure](#project-structure)
3. [Dataset](#dataset)
4. [Prerequisites](#prerequisites)
5. [Installation](#installation)
6. [Usage](#usage)
   - [Running the Frontend](#running-the-frontend)
   - [Running the Backend](#running-the-backend)
7. [Model Details](#model-details)


---

## Overview
- **Goal**: Detect plant diseases from leaf images using a trained CNN model.
- **Frontend**: Built with Vue.js (Vite as the build tool).
- **Backend**: Python (Flask in `app.py`) for model inference.
- **Machine Learning**: A Jupyter Notebook (`model.ipynb`) for training the CNN model.

---
## Project Structure
1. 
   ```bash
    AI_plant_disease_detection
    ├── node_modules/                 # Node.js dependencies
    ├── src/
    │   ├── components/
    │   │   └── PlantDiseaseDetection.vue  # Vue component for disease detection UI
    │   ├── App.vue                        # Root Vue component
    │   ├── index.html                     # Main HTML template for Vite
    │   └── main.js                        # Entry point for Vue application
    ├── app.py                         # Python backend for model inference
    ├── model.ipynb                    # Jupyter notebook for training the CNN model
    ├── package.json                   # Node.js project configuration
    ├── package-lock.json              # Auto-generated file for exact dependency versions
    ├── Procfile.txt                   # Deployment configuration (e.g., Heroku)
    ├── README.md                      # Project documentation (this file)
    ├── requirements.txt               # Python dependencies
    └── vite.config.js                 # Vite configuration
   
   
---



## Dataset
To train or retrain the CNN model, you need a labeled dataset of plant leaf images. One popular dataset is available on Kaggle. Steps:

Download the [dataset](#https://www.kaggle.com/datasets/vipoooool/new-plant-diseases-dataset) from Kaggle.

Unzip and place the images in a suitable directory (e.g., data/) at the project root.

Update any file paths in model.ipynb as needed.

Note: The dataset is not included in this repository. You must download it separately from Kaggle.

---

## Prerequisites
Node.js (version 14+ recommended)

Python 3.7+

pip (Python package manager)

Virtual environment tool (optional but recommended)

---

## Installation
1. Clone the Repository
   ```bash

    git clone https://github.com/vara-prasad-07/ AI_plant_disease_detection.git
    
---

2. Install Node.js Dependencies
   ```bash
    npm install

3. Install Python Dependencies
   ```bash

     pip install -r requirements.txt

---

## Usage
1. running frontend:
   ```bash
     npx vite

This starts a local development server. By default, open http://localhost:5173 (or the URL shown in the console) in your browser.

---

## Running the Backend
1. Ensure your virtual environment is active (if used).

1. **start python server**:
   ```bash
   python app.py

This will run a Flask (or similar) app on a local port (e.g., http://127.0.0.1:5000).

3. **Check API Endpoints (if any)**:

For instance, POST /predict might be where images are sent from the frontend.

---

## Model Details
Architecture: Convolutional Neural Network (CNN) with multiple convolution, pooling, and dense layers.
![image](https://github.com/user-attachments/assets/e43b0b86-011f-432f-8f29-5521424ea5d9)



**Frameworks**:

1. **Python**: TensorFlow/Keras (or PyTorch, depending on your setup)

2. **Vue**: Composition API or Options API (depending on your preference)

3. **Training**:

Use model.ipynb to train or fine-tune the CNN.

Hyperparameters (learning rate, batch size, epochs) can be modified in the notebook.





