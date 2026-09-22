# 🦙 Fine-Tuned Llama 3.1 Inference Engine

A high-performance, production-ready local LLM serving system built by fine-tuning `Llama-3.1-8B-Instruct` using QLoRA, quantizing the model to 4-bit GGUF, and exposing it through a FastAPI backend and Streamlit interface.

---

## 🏗️ Architecture & Tech Stack

[ Unsloth QLoRA ] ──► [ Q4_K_M GGUF ] ──► [ Ollama ] ──► [ FastAPI Backend ] ──► [ Streamlit UI ]


* **Model:** Meta Llama 3.1 8B Instruct
* **Fine-Tuning:** QLoRA via Unsloth (Google Colab T4 GPU)
* **Quantization Format:** GGUF (`Q4_K_M`, ~4.58 GB)
* **Inference Engine:** Ollama
* **Backend API:** FastAPI + Uvicorn
* **Frontend:** Streamlit

---

## 🚀 Quickstart Guide

### 1. Prerequisites
* Python 3.10+
* [Ollama](https://ollama.com) installed and running locally

### 2. Set Up the Model
Move your exported `Meta-Llama-3.1-8B-Instruct.Q4_K_M.gguf` file into the `models/` directory, then register it in Ollama:

```powershell
ollama create llama3-fine-tuned -f models/Modelfile
3. Install Dependencies
PowerShell
pip install -r requirements.txt
4. Run the API Backend
PowerShell
uvicorn app:app --reload --port 8000
Swagger UI Docs: http://127.0.0.1:8000/docs

Health Check: http://127.0.0.1:8000/health

5. Launch the Streamlit App
In a separate terminal:

PowerShell
streamlit run streamlit_app.py
Access the web chat application at http://localhost:8501.

📡 API Reference
POST /generate
Generates text responses from the fine-tuned model.

Request Body:

JSON
{
  "prompt": "Explain QLoRA in simple terms.",
  "temperature": 0.7,
  "max_tokens": 512
}
Response:

JSON
{
  "model": "llama3-fine-tuned",
  "response": "QLoRA (Quantized Low-Rank Adaptation) is..."
}
