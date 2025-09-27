Here’s an updated **README.md** for your app with your specific model choices added in.

---

# Local RAG App

A **100% local Retrieval-Augmented Generation (RAG)** application built with:

* [Ollama](https://ollama.ai) (local LLM inference – running **LLaMA 3.2:1B** model)
* [Streamlit](https://streamlit.io) (interactive UI)
* [Sentence-Transformers](https://www.sbert.net) with **ms-marco-MiniLM-L-6-v2**
* [ChromaDB](https://www.trychroma.com) (vector database)
* [PyMuPDF](https://pymupdf.readthedocs.io/) (PDF/text extraction)
* [LangChain Community](https://python.langchain.com/docs/modules) (RAG pipeline)

All components run **locally on your machine** — no external API calls, no cloud costs, and no data leaving your system.

---

## ✨ Features

* Upload PDFs or text files and extract content locally with PyMuPDF.
* Create embeddings using **nomic-embed-text** (Sentence-Transformers) and store them in ChromaDB.
* Retrieve relevant chunks and pass them to a **local LLaMA 3.2:1B** model via Ollama.
* Interactive question-answering interface built with Streamlit.
* Optional **re-ranking** of retrieved documents for improved answer quality.

---

## 🚀 Getting Started

### 1. Prerequisites

* Python 3.9+
* Ollama installed and running locally
* `pip`

### 2. Clone the repository

```bash
git clone https://github.com/yourusername/local-rag-app.git
cd local-rag-app
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

*(Example `requirements.txt`)*

```
streamlit
ollama
sentence-transformers
chromadb
pymupdf
langchain-community
```

### 4. Run the app

```bash
streamlit run app.py
```

Then open the URL shown in your terminal (usually `http://localhost:8501`).

---

## 📝 Usage

1. Upload one or more PDF/text files in the Streamlit UI.
2. The app extracts content with PyMuPDF.
3. Embeddings are generated with **nomic-embed-text** and stored in ChromaDB.
4. Ask a question about the documents in the chat box.
5. The app retrieves the most relevant chunks and passes them to **LLaMA 3.2:1B** via Ollama for local LLM generation.

---

## 🔄 Re-Ranking

By default, the app retrieves top-k results from ChromaDB based on cosine similarity.
We added an **optional re-ranking step** that reorders retrieved chunks using a cross-encoder (Sentence-Transformers or other model).

This yields:
| Before Re-Ranking                      | After Re-Ranking                                   |
| ----------------------------------     | -------------------------------------------------- |
| ![Before](assets/Initial%20Result.png) | ![After Re-Ranking](assets/After%20Re-ranking.png) |


---

## 📂 Project Structure

```
local-rag-app/
├─ app.py                # Streamlit front-end
├─ rag_pipeline.py       # RAG logic (embeddings, retrieval, re-ranking)
├─ requirements.txt
└─ README.md
```

---

## 🛡️ Privacy

All data, embeddings, and model inference run on your local machine.
No information is sent to external servers.

---
