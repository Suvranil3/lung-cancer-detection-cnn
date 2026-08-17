# 🫁 Lung Cancer Detection using CNN

## 1. Tell us about the project's reach and impact

**Lung Cancer Detection using CNN** is an open-source deep learning project developed as a B.Tech AI/ML final-year project. The system uses the **LIDC-IDRI CT scan dataset** and a Convolutional Neural Network to classify CT images into **Normal** and **Cancer** categories.

The current system provides a reproducible pipeline covering medical-image preprocessing, CNN training, evaluation, and inference. The model currently achieves approximately **75% test accuracy**, with precision, recall, F1-score, and confusion-matrix analysis used for evaluation.

### 🌍 Why this project matters

Medical AI can be difficult for students, researchers, and independent developers to reproduce because datasets, preprocessing pipelines, model implementations, and deployment workflows are often fragmented.

This project aims to provide a transparent and accessible starting point for experimenting with **open-source medical image analysis**.

The longer-term vision is to move beyond a standalone image classifier and develop an accessible research platform following:

**CT Scan → AI Analysis → Visual Explanation → Structured Result**

A major planned extension is **Explainable AI using Grad-CAM**, which would generate heatmaps showing the regions of a CT image that contributed most strongly to the CNN's prediction. This would make the model easier to inspect and help researchers understand its behavior instead of treating the prediction as a black box.

The project can further evolve into a cloud-based inference platform where researchers can upload CT data, run the trained model through an API, visualize predictions and explanations, and reproduce experiments without having to configure the complete ML environment locally.

---

## 🏗️ Planned Architecture

```text
                         ┌─────────────────────────┐
                         │     User / Researcher   │
                         └────────────┬────────────┘
                                      │
                                      ▼
                         ┌─────────────────────────┐
                         │     Web Application     │
                         │                         │
                         │  • Upload CT/DICOM      │
                         │  • View Prediction      │
                         │  • View Heatmap         │
                         └────────────┬────────────┘
                                      │
                                      ▼
                         ┌─────────────────────────┐
                         │       Backend API       │
                         │     Python / FastAPI    │
                         └────────────┬────────────┘
                                      │
                                      ▼
                    ┌─────────────────────────────────┐
                    │         Preprocessing            │
                    │                                 │
                    │  DICOM/CT → Image/Tensor        │
                    │  Resize → Normalize → Augment    │
                    └────────────────┬────────────────┘
                                     │
                                     ▼
                         ┌─────────────────────────┐
                         │       CNN Model         │
                         │                         │
                         │ Conv → Pool → Dropout   │
                         │       → Dense            │
                         └────────────┬────────────┘
                                      │
                         ┌────────────┴────────────┐
                         ▼                         ▼
              ┌────────────────────┐    ┌────────────────────┐
              │   Classification   │    │     Grad-CAM       │
              │                    │    │                    │
              │ Normal / Cancer    │    │ Visual Explanation │
              └──────────┬─────────┘    └──────────┬─────────┘
                         │                         │
                         └────────────┬────────────┘
                                      ▼
                         ┌─────────────────────────┐
                         │    Results Dashboard    │
                         │                         │
                         │ Prediction              │
                         │ Confidence              │
                         │ Visual Explanation      │
                         └─────────────────────────┘
```

This architecture provides a path from a **local academic CNN implementation to a scalable, explainable medical-AI research platform**.

The project is intended for **research and educational purposes** and is not designed to replace professional medical diagnosis.

---

# ⚙️ 2. How to Install and Run the Project

One of the project's goals is reproducibility. A developer should be able to clone the repository, install the required dependencies, prepare the dataset, and run the training or inference pipeline.

### 📥 Clone the Repository

```bash
git clone https://github.com/Suvranil3/lung-cancer-detection-cnn.git

cd lung-cancer-detection-cnn
```

### 🐍 Create a Virtual Environment

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

On Linux/macOS:

```bash
source venv/bin/activate
```

### 📦 Install Dependencies

```bash
pip install -r requirements.txt
```

The project uses technologies including:

* Python
* TensorFlow
* Keras
* OpenCV
* NumPy
* Matplotlib

### 🗂️ Prepare the Dataset

Download the **LIDC-IDRI dataset** and place the required CT scan data in the project's dataset directory.

The preprocessing pipeline then performs operations such as:

```text
Raw CT Data
     ↓
Image Extraction
     ↓
Resizing
     ↓
Normalization
     ↓
Data Augmentation
     ↓
Training Dataset
```

The dataset should be prepared according to the project's expected directory structure before training.

### 🧠 Train the CNN

The training notebook can be opened using Jupyter Notebook or Google Colab:

```bash
jupyter notebook
```

Then open:

```text
final year project.ipynb
```

Alternatively, the notebook can be uploaded directly to **Google Colab**.

The training pipeline performs:

```text
Dataset
   ↓
Preprocessing
   ↓
Train / Validation / Test Split
   ↓
CNN Training
   ↓
Model Evaluation
   ↓
Save Trained Model
```

The trained model is saved as:

```text
lung_cancer_model.h5
```

### 🔎 Run Inference

Once the model has been trained, the saved model can be loaded and used to classify new CT images.

The intended inference workflow is:

```text
CT Image
   ↓
Preprocessing
   ↓
Trained CNN
   ↓
Prediction
   ↓
Normal / Cancer
```

The exact inference command can be provided through the project's inference script as the deployment layer is expanded.

---

# 🧠 3. Expand the CNN and Medical-AI Pipeline

I will use the Claude Max subscription to improve and experiment with the existing CNN architecture, preprocessing pipeline, evaluation methodology, and training workflow.

The planned improvements include:

* Transfer learning with modern CNN architectures
* Better data augmentation and preprocessing
* Hyperparameter optimization
* Class-imbalance handling
* More rigorous validation
* Improved error analysis
* Explainable AI using Grad-CAM

Claude will help me understand, implement, test, and document these experiments rather than treating the model as a black box.

---

# ☁️ 4. Move the Model toward Cloud Deployment

The current project primarily runs in a local/Google Colab environment. My next step is to transform the trained model into a deployable inference service.

The planned workflow is:

**CT/DICOM Upload → Secure API → Preprocessing → CNN Inference → Grad-CAM → Result**

I plan to explore technologies such as **Python/FastAPI, Docker, cloud object storage, and scalable inference infrastructure**.

Claude will help me design the backend architecture, implement APIs, containerize the model, handle errors and validation, and prepare the system for cloud deployment.

---

# 🔬 5. Build Explainable Medical AI

A major planned improvement is making the CNN more interpretable.

Instead of returning only:

> **Prediction: Cancer**

the future system should provide:

> **Prediction + Confidence + Visual Explanation**

Using techniques such as **Grad-CAM**, I want to generate heatmaps over CT images to visualize the regions that influenced the model's prediction.

Claude will help me implement this pipeline, validate the generated visualizations, and document the limitations of the approach.

---

# 🤖 6. Explore Multimodal AI

In a later stage, I want to explore combining visual information from CT scans with structured or unstructured clinical information such as medical reports.

The long-term architecture could become:

```text
                         CT Scan
                            │
                            ▼
                     CNN / Vision Model
                            │
                            │
Medical Report ─────────────┤
                            ▼
                     Multimodal AI
                            │
                            ▼
                  Structured Research Output
```

This could allow the project to investigate how medical imaging and clinical text can be combined in a research environment.

Claude will help me design the interfaces between these components, develop the supporting software, and experiment with multimodal workflows responsibly.

---

# 🧪 7. Make the Project Reproducible and Open Source

I also want to make the repository easier for other developers and researchers to understand, reproduce, and contribute to.

I will use Claude to help with:

* Unit and integration testing
* CI/CD workflows
* API documentation
* Model documentation
* Reproducible training pipelines
* Code quality and refactoring
* Docker configuration
* Contribution guidelines
* Technical documentation
* Installation and deployment documentation

The goal is to turn the project from a **final-year CNN experiment into a reproducible open-source foundation for further medical-AI research and cloud deployment**.

---

## 🚀 Project Roadmap

```text
                 CURRENT
                    │
                    ▼
        ┌──────────────────────┐
        │ CNN Classification   │
        │ Normal / Cancer      │
        └──────────┬───────────┘
                   │
                   ▼
        ┌──────────────────────┐
        │ Model Improvement    │
        │ Transfer Learning    │
        │ Better Validation    │
        └──────────┬───────────┘
                   │
                   ▼
        ┌──────────────────────┐
        │ Explainable AI       │
        │ Grad-CAM             │
        └──────────┬───────────┘
                   │
                   ▼
        ┌──────────────────────┐
        │ API + Web Application │
        │ FastAPI + Frontend   │
        └──────────┬───────────┘
                   │
                   ▼
        ┌──────────────────────┐
        │ Cloud Deployment     │
        │ Docker + Cloud       │
        └──────────┬───────────┘
                   │
                   ▼
        ┌──────────────────────┐
        │ Multimodal Research  │
        │ CT + Clinical Text   │
        └──────────────────────┘
```

### 🎯 Final Vision

The ultimate goal is to evolve this project from a **standalone CNN trained on CT images** into an **open-source, explainable, reproducible, and cloud-deployable medical-AI research platform**.

It would provide developers and researchers with a complete path from:

**Dataset → Preprocessing → CNN → Evaluation → Explainability → API → Cloud Deployment → Multimodal AI**

while keeping the system transparent, reproducible, and clearly positioned as a **research/decision-support tool rather than a replacement for clinical diagnosis**.
