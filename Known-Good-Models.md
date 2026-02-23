# 🤖 Known-Good Models for Vishwagyan

This document lists the Base LLMs and Embedding models that have been tested and verified for the Vishwagyan ecosystem. We prioritize models that show high performance in **Indic languages** and **Reasoning capabilities**.

---

## 🧠 Large Language Models (LLMs)

We categorize our tested models based on their efficiency and accuracy for UPSC-level queries.

### 1. Sarvam-1 (2B) - 🏆 *Top Choice for Indic Speed*
- **Developer:** Sarvam AI (Made in India)
- **Status:** **Verified**
- **Why:** Optimized specifically for 10+ Indian languages. It outperforms much larger models in Hindi and Marathi tokenization.
- **Use Case:** Fast, real-time multilingual chat.

### 2. Llama 3.1 (8B/70B) - 🛡️ *Best for Complex Reasoning*
- **Developer:** Meta
- **Status:** **Verified** (with Fine-tuning)
- **Why:** Excellent general intelligence and instruction-following. Requires custom prompting for high-quality Hindi output.
- **Use Case:** Solving complex Ethics (GS-4) and Essay papers.

### 3. Mistral-7B-v0.3 - ⚡ *Best for Local Deployment*
- **Developer:** Mistral AI
- **Status:** **Verified**
- **Why:** Very efficient and lightweight. Works great on mid-range GPUs (RTX 3090/4090).

---

## 🔎 Embedding Models (The Search Engine)

To find the right answer from thousands of UPSC pages, we use these verified Embedding models:

| Model Name | Performance | Multilingual Support | Status |
| :--- | :--- | :--- | :--- |
| **BGE-M3** | High | 100+ Languages (Excellent) | **Recommended** |
| **Indic-BERT** | Medium | All 22 Scheduled Indian Languages | Verified |
| **Cohere Multilingual v3** | Very High | Excellent Nuance Detection | Tested (Cloud) |



---

## 🧪 Model Selection Criteria (The "Bharat Test")

How we decide if a model is "Known-Good":
1.  **Tokenization Efficiency:** Can the model represent Hindi/Tamil words without wasting memory?
2.  **Cultural Sensitivity:** Does the model understand Indian historical context correctly?
3.  **Accuracy (UPSC Benchmark):** Can the model answer Prelims-level questions based on our RAG data?

---

## 🛠️ How to use these models?

We recommend running these models using **Ollama** or **vLLM** for the fastest performance.
```bash
# Example: Running the verified Sarvam model
ollama run sarvam-1
