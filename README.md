# 🩺 Clinical-LLM-Monitor

[![Python](https://img.shields.io/badge/Python-3.9+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white)](https://pytorch.org/)
[![HuggingFace](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Transformers-yellow?style=for-the-badge)](https://huggingface.co/)
[![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

A comprehensive pipeline for **Fine-Tuning, Quantizing, and Deploying** Medical Large Language Models. This project optimizes a **Llama 3.1 8B Instruct** model using **QLoRA** to achieve high-performance clinical dialogue generation on consumer-grade hardware.

---

## 📌 Project Overview
**Clinical-LLM-Monitor** bridges the gap between raw medical datasets and interactive AI applications. By leveraging 4-bit quantization and Parameter-Efficient Fine-Tuning (PEFT), it transforms a general-purpose LLM into a specialized clinical assistant capable of understanding complex medical dialogues.

### Key Highlights:
* **Model:** Llama 3.1 8B Instruct.
* **Technique:** QLoRA (4-bit NF4 Quantization + LoRA adapters).
* **Dataset:** `knowrohit07/know_medical_dialogues`.
* **Architecture:** Full-stack solution featuring a FastAPI backend and a responsive Web UI.

---

## 🛠 Tech Stack & Core Competencies

### 1. Deep Learning & Optimization
* **Quantization:** `bitsandbytes` (NF4, Double Quantization).
* **PEFT:** `lora_r=64`, `lora_alpha=16` for efficient weight updates.
* **Compute:** PyTorch with CUDA mixed-precision (`fp16`).

### 2. Hugging Face Ecosystem
* **Transformers:** `AutoModelForCausalLM`, `SFTTrainer`.
* **Evaluation:** `Sentence Transformers` (`all-MiniLM-L6-v2`) for semantic similarity scoring.

### 3. Deployment & Frontend
* **Backend:** **FastAPI** for high-concurrency asynchronous API endpoints.
* **Frontend:** HTML5, CSS3, and JavaScript for real-time inference visualization.

---

## 🚀 Getting Started

### 1. Environment Setup
Clone the repository and install the dependencies:
```bash
git clone https://github.com/your-username/Clinical-LLM-Monitor.git
cd Clinical-LLM-Monitor
pip install torch transformers datasets peft bitsandbytes fastapi uvicorn sentence_transformers matplotlib seaborn
```

### 2. Training (Fine-Tuning)
Run the fine-tuning script to initialize the QLoRA trainer:
```python
# Example snippet from llama31_fineTuning.py
bnb_config = BitsAndBytesConfig(
    load_in_4bit=True,
    bnb_4bit_quant_type="nf4",
    bnb_4bit_compute_dtype=torch.float16,
    bnb_4bit_use_double_quant=True
)
```

### 3. Deployment
Launch the FastAPI server and access the interactive monitor:
```bash
uvicorn app1:app --reload --host 127.0.0.1 --port 8080
```
📍 **Local UI:** `http://localhost:8080/static/index.html`

---

## 📊 Results & Performance
The model was evaluated against medical test sets to ensure clinical relevance:

| Metric | Value |
| :--- | :--- |
| **Training Epochs** | 5 |
| **Final Training Loss** | 2.1 |
| **Avg. Cosine Similarity** | **0.5294** |

> **Note:** The system automatically generates similarity distribution plots and performance analytics during the evaluation phase to monitor model drift and accuracy.

---

## 📂 Project Structure
```text
├── app1.py                 # FastAPI Backend
├── llama31_fineTuning.py   # Training & QLoRA Logic
├── static/
│   ├── index.html          # Web UI Frontend
│   └── style.css           # Custom Styling
├── requirements.txt        # Dependency List
└── README.md
```

---

## 👨‍💻 Author
**Nguyễn Triệu Gia Khánh**
* *Student at Thuong Mai University*
* Focus: AI Development & Clinical NLP
