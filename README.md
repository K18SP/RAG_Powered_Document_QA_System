# RAG-Powered Document Q&A System

An AI-powered document question-answering system built with LangChain, Hugging Face embeddings, FAISS vector search, and Groq's LLaMA3 model. Upload any PDF and ask questions in plain English — the system retrieves the most relevant context and generates accurate, cited answers in real time.

---

## Demo

> Upload a PDF → Process it → Ask questions → Get instant AI-powered answers

![RAG Demo](assets/demo.png)

---

## Features

- 📄 **Multi-PDF Upload** — Upload and query multiple PDFs simultaneously
- 🧠 **Semantic Search** — FAISS vector store with Hugging Face sentence-transformer embeddings (`all-MiniLM-L6-v2`)
- ⚡ **Fast Inference** — Groq API with LLaMA3-8B for sub-second LLM responses
- 💬 **Conversation History** — Full chat history with timestamps preserved in session
- ⚙️ **Configurable Chunking** — Adjustable chunk size and overlap via sidebar sliders
- 🎨 **Clean UI** — Streamlit web app with custom styling, progress bars, and status feedback

---

## Tech Stack

| Layer | Technology |
|---|---|
| LLM | Groq API — LLaMA3-8B-8192 |
| Embeddings | Hugging Face — `all-MiniLM-L6-v2` |
| Vector Store | FAISS (CPU) |
| RAG Framework | LangChain |
| PDF Parsing | PyPDFLoader |
| UI | Streamlit |
| Config | python-dotenv |

---

## Project Structure

```
RAG-Document-QA/
│
├── app_huggingfaceembedding.py  # Main app — HuggingFace embeddings (recommended)
├── main.py                      # Alternate version — OpenAI embeddings
├── requirements.txt             # All dependencies
├── .env                         # API keys (not committed)
├── .gitignore
└── README.md
```

---

##  Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/K18SP/RAG-Document-QA.git
cd RAG-Document-QA
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Set up environment variables
Create a `.env` file in the root directory:
```env
GROQ_API_KEY=your_groq_api_key_here
HF_TOKEN=your_huggingface_token_here
```

> Get your free Groq API key at [console.groq.com](https://console.groq.com)  
> Get your Hugging Face token at [huggingface.co/settings/tokens](https://huggingface.co/settings/tokens)

### 4. Run the app
```bash
streamlit run app_huggingfaceembedding.py
```

---

##  How It Works

```
PDF Upload
    ↓
Text Extraction (PyPDFLoader)
    ↓
Chunking (RecursiveCharacterTextSplitter)
    ↓
Embedding Generation (HuggingFace all-MiniLM-L6-v2)
    ↓
Vector Storage (FAISS)
    ↓
User Query → Semantic Search → Top-k Chunks Retrieved
    ↓
LLaMA3 (via Groq) generates answer from context
    ↓
Answer displayed in Streamlit UI
```

---

##  Results

- Handles multi-PDF corpora with semantic retrieval in **< 1 second**
- Accurate context-grounded answers LLM explicitly states when answer is not found in context
- Supports documents of 50+ pages without performance degradation

---

## 🔧 Configuration

| Parameter | Default | Description |
|---|---|---|
| Chunk Size | 1000 | Characters per text chunk |
| Chunk Overlap | 200 | Overlap between chunks |
| Top-k Retrieval | 3 | Number of chunks retrieved per query |
| LLM Model | LLaMA3-8B-8192 | Groq model used for generation |

---

## 📦 Requirements

Key dependencies:
```
langchain
langchain-groq
langchain-huggingface
langchain-community
faiss-cpu
streamlit
pypdf
sentence-transformers
python-dotenv
```

Full list in `requirements.txt`.

---

## 🙋 Author

**Kushal Pandya**  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://www.linkedin.com/in/kushal-pandya-302984251/)
[![GitHub](https://img.shields.io/badge/GitHub-K18SP-black)](https://github.com/K18SP)
