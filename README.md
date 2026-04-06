# 🥔 Potato Disease Classifier

A CNN-based image classifier that detects potato leaf diseases from photos. Trained on the [PlantVillage](https://www.tensorflow.org/datasets/catalog/plant_village) dataset via TensorFlow Datasets, with a mobile-responsive Gradio web UI and one-click deploy to HuggingFace Spaces.

---

## 🌿 Classes

| Label | Pathogen | Action |
|---|---|---|
| 🟢 Healthy | — | No action needed |
| 🟠 Early Blight | *Alternaria solani* | Apply mancozeb fungicide promptly |
| 🔴 Late Blight | *Phytophthora infestans* | Remove infected leaves; apply copper-based fungicide urgently |

---

## 🏗️ Model Architecture

Custom CNN (`PotatoCNN_v2`) built with TensorFlow/Keras:

- 6 convolutional blocks with BatchNorm + ReLU
- Filters: 32 → 64 → 128 → 128 → 256 → 256
- Global Average Pooling
- Dense head: 256 → 64 → 3 (softmax) with L2 regularisation + Dropout
- Input size: 224 × 224 RGB

---

## 🚀 Quick Start

### 1. Clone & install

```bash
git clone https://github.com/YOUR_USERNAME/potato-disease-classifier.git
cd potato-disease-classifier
pip install -r requirements.txt
```

### 2. Train (Google Colab recommended)

Open the notebook in Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_USERNAME/potato-disease-classifier/blob/main/PDC-v1_2_fixed.ipynb)

The notebook will:
- Download and filter the PlantVillage dataset automatically
- Train the CNN (or reload a saved model if one exists)
- Plot training curves and a confusion matrix
- Launch the Gradio UI with an ngrok public URL

### 3. Run the Gradio app locally

```bash
# Place your trained model at the repo root first
python app.py
# → http://localhost:7860
```

---

## ☁️ Deploy to HuggingFace Spaces

1. Get a write token from https://huggingface.co/settings/tokens
2. In the notebook, set `HF_TOKEN` and `HF_REPO_ID`
3. Run **Cell 12 → Deploy to HuggingFace Spaces**

The notebook zips `app.py`, `requirements.txt`, and the trained model and pushes them to your Space automatically.

---

## 📁 Repository Structure

```
potato-disease-classifier/
├── PDC-v1_2_fixed.ipynb   # Full training + deployment notebook
├── app.py                 # Standalone Gradio app (run after training)
├── requirements.txt
├── .gitignore
└── README.md
```

> **Note:** The trained model file (`potato_disease_v2.keras`) is excluded from the repo via `.gitignore` because it can be large. Download it from the Colab session (Cell 13) or host it on HuggingFace Hub.

---

## 🛠️ Tech Stack

- **TensorFlow / Keras** — model training
- **TensorFlow Datasets** — PlantVillage data
- **Gradio** — web UI
- **ngrok / pyngrok** — public tunnel for Colab
- **HuggingFace Hub** — Spaces deployment

---

## 📄 License

MIT
