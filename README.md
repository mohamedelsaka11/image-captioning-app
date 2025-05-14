# 🧠 Image Captioning using Transfer Learning (DenseNet201)

This project presents an end-to-end deep learning solution to automatically **generate captions for images** using a **custom model** built on top of **DenseNet201** as a feature extractor and LSTM-based decoder for text generation.

## 📌 Project Objectives

- Extract image features using Transfer Learning (DenseNet201).
- Generate natural language captions for images using a sequence model.
- Build a **Streamlit** web app for interactive real-time caption generation.
- Save and load model/tokenizer for deployment and testing.

---

## 📁 Dataset

- Dataset used: **Flickr8k** (images + 5 captions per image).
- Images are preprocessed to (224, 224, 3).
- Text captions are tokenized and cleaned:
  - Lowercase
  - Removed punctuation, numbers, and special characters

---

## 🧠 Model Overview

### 🔹 Feature Extraction

- Model: `DenseNet201`
- Pretrained on: `ImageNet`
- Custom top layers removed
- Output: 1920-dimensional feature vector

### 🔹 Caption Generator

- Tokenizer: Fitted on all training captions
- Max sequence length: 35
- Architecture:
  - DenseNet features → Dense Layer
  - Caption input → Embedding + LSTM
  - Concatenate image & caption vector → Dense → Output word

---

## 🧪 Evaluation

- Loss: Categorical Crossentropy
- Optimizer: Adam
- Trained with teacher forcing using the `fit()` method

---

## 🖥️ Streamlit App

- Upload an image and get a predicted caption in real-time.
- The app loads:
  - `feature_extractor.keras`: DenseNet201 model
  - `model.keras`: Trained caption generation model
  - `tokenizer.pkl`: Fitted tokenizer used during training

---
