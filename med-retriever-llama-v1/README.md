Base_model: C:\Project\Clinical-LLM-Monitor
library_name: peft
---

# Model Card for med-retriever-llama-v1

Mô hình này là một phiên bản tinh chỉnh (fine-tuned) của **Llama 3.1 8B Instruct** dành riêng cho lĩnh vực y tế, tối ưu hóa khả năng truy xuất và phản hồi hội thoại lâm sàng.

## Model Details

### Model Description

- **Developed by:** Nguyễn Triệu Gia Khánh
- **Model type:** Causal Language Model (Fine-tuned with QLoRA)
- **Language(s) (NLP):** Tiếng Anh (Y khoa)
- **License:** MIT
- **Finetuned from model:** Meta-Llama-3.1-8B-Instruct

### Model Sources

- **Repository:** [https://github.com/giakhanhhii/Clinical-LLM-Monitor](https://github.com/giakhanhhii/Clinical-LLM-Monitor)
- **Project Path:** `C:\Project\Clinical-LLM-Monitor`

## Uses

### Direct Use

Hỗ trợ giải đáp các thắc mắc về triệu chứng bệnh và cung cấp thông tin dựa trên dữ liệu hội thoại giữa bác sĩ và bệnh nhân.

### Out-of-Scope Use

Không sử dụng mô hình này để thay thế hoàn toàn chẩn đoán chuyên môn từ bác sĩ thực tế trong các tình huống cấp cứu.

## Training Details

### Training Data

Mô hình được huấn luyện trên tập dữ liệu **knowrohit07/know_medical_dialogues** từ Hugging Face, bao gồm các hội thoại lâm sàng thực tế.

### Training Procedure

#### Training Hyperparameters

- **Quantization:** 4-bit NormalFloat (NF4) với Double Quantization.
- **PEFT (LoRA) Config:** `r=64`, `lora_alpha=16`, `target_modules=["q_proj", "v_proj"]`.
- **Optimizer:** Paged AdamW 32-bit.
- **Training regime:** fp16 mixed precision.

#### Speeds, Sizes, Times

- **Epochs:** 5.
- **Training Loss:** 2.1.
- **Training Time:** Khoảng 10 giờ trên phần cứng cá nhân.

## Evaluation

### Results

- **Avg. Cosine Similarity (Test Set):** 0.5294 (Sử dụng `all-MiniLM-L6-v2` để đánh giá độ tương đồng ngữ nghĩa).

## Technical Specifications

### Compute Infrastructure

#### Hardware
- **GPU:** Nvidia GeForce GTX (3 GiB VRAM trở lên để inference).

#### Software
- **Frameworks:** FastAPI, PyTorch, Transformers, PEFT, BitsAndBytes.

### Framework versions

- PEFT 0.12.0
- Transformers 4.43.3
- PyTorch 2.4.0
