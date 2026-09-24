# 🧠 Brain Tumor Detection using Attention-Enhanced ML-UNet and Multi-Level Feature Fusion

> **A Still in progess clinically motivated deep learning framework for robust brain tumor detection from MRI scans using Attention mechanisms, ML-UNet architecture, and hierarchical feature fusion, looking for collaborators for research and development**

---

## 📌 Motivation

Brain tumor diagnosis from MRI scans is a **high-stakes medical imaging problem** where:

- Tumors vary significantly in size, shape, and texture  
- Important pathological regions may occupy only a small portion of the scan  
- False negatives can have severe clinical consequences  

Conventional CNN-based approaches often:
- Focus on irrelevant background regions
- Lose fine-grained spatial information
- Fail to integrate global context with local tumor cues  

This project addresses these limitations through:
- **ML-UNet (Multi-Level U-Net)**
- **Attention Gates**
- **Multi-scale and hierarchical feature fusion**

---

## 🧬 Key Contributions

- Attention-guided tumor localization  
- Multi-level semantic feature extraction  
- Encoder–decoder fusion at multiple resolutions  
- Clinically relevant evaluation metrics  
- Modular, research-friendly codebase  

---

## 🏗️ Overall Architecture


---

## 🧠 ML-UNet Architecture (Multi-Level U-Net)

### Why ML-UNet?

Standard U-Net architectures extract features at fixed spatial scales.  
However, **brain tumors appear at multiple resolutions**, from small localized lesions to large diffuse regions.

ML-UNet improves upon standard U-Net by:
- Capturing **low-level features** (edges, textures)
- Learning **mid-level representations** (tumor boundaries, shapes)
- Extracting **high-level semantic context** (global brain structure)

---

### Encoder Design

Each encoder block consists of:
- Convolution layers  
- Batch Normalization  
- ReLU activation  
- Max Pooling for downsampling  

With increasing depth:
- Spatial resolution decreases
- Semantic richness increases

This design enables **multi-scale representation learning**.

---

## 🎯 Attention Mechanism (Attention Gates)

### Why Attention?

MRI images contain large irrelevant regions such as:
- Skull
- Cerebrospinal fluid
- Healthy tissue  

Attention Gates allow the network to **focus on tumor-relevant regions** while suppressing background noise.

---

### How Attention Works

At each skip connection:
- Decoder features act as a **query**
- Encoder features act as **keys**
- Attention coefficients weight encoder activations spatially


Where:
- σ is a sigmoid activation
- Only salient regions are passed forward

This results in:
- Improved tumor localization
- Reduced false positives
- Better boundary delineation

---

## 🔗 Multi-Level Feature Fusion Strategy

Feature fusion is the **core strength** of this framework.

### Fusion Steps

#### 1️⃣ Encoder-Level Fusion
- Features from multiple encoder depths are preserved
- Captures both local texture and global semantics  

#### 2️⃣ Attention-Filtered Skip Fusion
- Encoder features pass through Attention Gates
- Irrelevant spatial activations are suppressed  

#### 3️⃣ Decoder-Level Fusion
- Upsampled decoder features are concatenated with attention-refined encoder features
- Enables precise spatial reconstruction  

#### 4️⃣ Final Multi-Scale Aggregation
- Outputs from different decoder stages are combined
- Improves robustness to tumor size and shape variations  

---

## 🔄 End-to-End Pipeline

### Step 1: Data Loading
- MRI images loaded from disk
- Resized to a fixed resolution
- Supports grayscale or multi-channel inputs  

---

### Step 2: Preprocessing
- Intensity normalization
- Noise reduction
- Optional preprocessing extensions (e.g., skull stripping)

---

### Step 3: Feature Encoding
- ML-UNet encoder extracts hierarchical features
- Multi-scale representations preserved  

---

### Step 4: Attention-Guided Fusion
- Attention Gates refine skip connections
- Feature maps filtered based on relevance  

---

### Step 5: Decoding & Reconstruction
- Progressive upsampling
- Skip connections restore spatial precision  

---

### Step 6: Prediction
- Final convolution layer produces tumor prediction
- Sigmoid or Softmax activation depending on task  

---

## 📊 Evaluation Metrics (Clinically Relevant)

| Metric | Clinical Importance |
|------|---------------------|
| Recall (Sensitivity) | Minimizes missed tumors |
| Precision | Reduces false alarms |
| F1-Score | Balances precision and recall |
| Accuracy | Overall correctness |

> **Recall is prioritized** due to its critical importance in medical diagnosis.

---

## 📁 Project Structure
notebooks/ → Experiments and visual analysis
utils/ → Modular ML utilities
├── data_loader.py
├── preprocessing.py
├── model_utils.py
├── metrics.py
└── visualization.py
configs/ → Configuration files
data/ → MRI datasets
results/ → Metrics and visual output

🔬 Future Research Extensions

3D ML-UNet for volumetric MRI analysis

Transformer-based attention mechanisms

Explainability using Grad-CAM

Multi-modal MRI fusion (T1, T2, FLAIR)

Clinical deployment and validation

🧠 Target Use Cases

Medical imaging research

AI-assisted radiology

Internship and thesis projects

Research paper prototyping

Brain-Tumor-Detection/
│
├── notebooks/
│   └── BRAIN_TUMOR3.ipynb
│
├── utils/
│   ├── __init__.py
│   ├── data_loader.py
│   ├── preprocessing.py
│   ├── model_utils.py
│   ├── metrics.py
│   └── visualization.py
│
├── configs/
│   └── config.yaml
│
├── data/
│   ├── raw/
│   └── processed/
│
├── results/
│   ├── figures/
│   └── metrics/
│
├── requirements.txt
├── .gitignore
└── README.md

Mathematically:

