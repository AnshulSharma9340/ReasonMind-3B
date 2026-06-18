# 🚀 ReasonMind-3B  
### Distilling Deep Reasoning into a 3B Parameter LLM using Unsloth, QLoRA & Llama-3.1

ReasonMind-3B is an advanced **reasoning-distilled** language model built on **Llama-3.1 (3B)**, fine-tuned using **Unsloth** and **4-bit QLoRA**.  
The model learns to perform **Chain-of-Thought (CoT)** reasoning inspired by DeepSeek-R1 — enabling structured, step-by-step logical thinking even on small hardware.

This project demonstrates how reasoning capabilities can be **compressed, distilled, and efficiently deployed** in a compact model format that runs fully offline.

---

## 🔍 Project Overview

Standard small LLMs struggle with complex reasoning. ReasonMind-3B solves this by

- Using DeepSeek-R1 reasoning traces through the **R1-Distill-SFT** dataset  
- Fine-tuning with **Unsloth** to reduce VRAM usage by ~60%  
- Leveraging **4-bit QLoRA**, training only ~0.5% parameters  
- Adding a built-in `<think>` reasoning phase for structured problem solving  
- Deploying in **GGUF (Q8_0)** format for offline inference  

The model achieves improved performance on multi-step math, word puzzles, logic problems, and analytical tasks — all on a single GPU or CPU.

---

## 🧠 Key Features

- **Chain-of-Thought Reasoning**  
  Generates a hidden `<think>` block replicating step-by-step thought process.

- **Unsloth-Optimized Training**  
  2× faster training and ~60% VRAM reduction.

- **4-bit QLoRA Fine-Tuning**  
  Lightweight training — updating only a tiny slice of parameters.

- **Distilled from DeepSeek-R1 Logic**  
  High-quality reasoning examples → stronger logic abilities.

- **Offline Deployment via GGUF**  
  Runs on **Ollama**, **LM Studio**, **llama.cpp**, and **llama-cpp-python**.

---

## 📁 Repository Structure

ReasonMind-3B/
│
├── train_model.ipynb # Complete Unsloth + QLoRA training workflow
├── evaluation.ipynb # Multi-step reasoning evaluation
├── inference_demo.py # Offline inference using GGUF + llama.cpp
│
├── unsloth_config.py # Training hyperparameters & LoRA settings
├── prompt_template.txt # Llama-3.1 chat template
│
├── data/
│ └── r1_distill/ # Instructions for dataset download
│
├── model/
│ └── gguf/ # Final exported model (Q8_0 GGUF)
│
├── requirements.txt
└── README.md


---

## 🔧 Technical Details

### **Base Model**
- Llama-3.1 (3B Instruct)

### **Fine-Tuning Stack**
- Unsloth (memory-efficient engine)
- QLoRA (4-bit quantization)
- LoRA Ranks / Adapters
- Gradient Checkpointing  
- PagedAttention

### **Dataset**
- `ServiceNow-AI / R1-Distill-SFT`  
  Distilled from DeepSeek-R1 reasoning samples.

### **Hardware Requirements**
- Single GPU  
- < 16GB VRAM  
- Extremely lightweight training

### **Deployment Format**
- GGUF (Q8_0)  
- Works with:
  - Ollama  
  - LM Studio  
  - llama.cpp  

---

## 🔥 Inference Example (Python)

```python
from llama_cpp import Llama

llm = Llama(
    model_path="model/gguf/reasonmind-3b-q8_0.gguf"
)

response = llm("Solve: If A has 3 apples and buys 5 more, how many total?")
print(response["choices"][0]["text"])
```
🧪 Sample Output
<think>
A has 3 apples. He buys 5 more.
3 + 5 = 8 apples.
</think>

Final Answer: 8 apples.
⚙️ Installation
1. Clone the Repository
git clone https://github.com/yourusername/ReasonMind-3B.git
cd ReasonMind-3B
2. Install Dependencies
pip install -r requirements.txt
3. Add GGUF Model
Place your GGUF file into:

model/gguf/
🏁 Training Instructions
Run the complete training pipeline:

Load Llama-3.1 3B

Apply LoRA adapters

Integrate Unsloth optimization

Format reasoning dataset

Train QLoRA

Export to GGUF

Everything is inside:

train_model.ipynb
📊 Evaluation
Evaluate reasoning ability using:

evaluation.ipynb
Includes:

Multi-step logical reasoning

Math CoT

Word puzzles

Analytical tasks

🎯 Why This Project Matters
ReasonMind-3B demonstrates how deep reasoning abilities can be distilled into tiny models, enabling:

Offline private inference

Low-cost intelligent agents

Domain-specific reasoning LLMs

Teaching models structured thinking

This project brings powerful reasoning AI closer to everyone — on everyday hardware.

🤝 Contributing
Pull requests and improvements are welcome!

⭐ Support the Project
If you found this useful, please star the repo — it helps a lot! ⭐
