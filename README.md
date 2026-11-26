# 🤖 RAG Chatbot

> Ask questions about your own documents and get answers grounded in their content, without reading them end to end.

A Retrieval-Augmented Generation (RAG) chatbot built with Streamlit. Upload your documents, ask questions in a chat interface, and get answers based on your own content instead of the LLM's general knowledge.

## 🎬 Demo

<!-- Add a screenshot or GIF of the app here -->
![App Screenshot](screenshots/demo.png)

🔗 **Live demo:** _add your Streamlit Community Cloud link here_

## ✨ Features

- Upload and process PDF and Word (`.docx`) documents
- Splits documents into chunks and converts them into embeddings
- Stores embeddings in a local FAISS vector database (`vector_db/`)
- Retrieves the most relevant chunks for each question (semantic search)
- Generates answers with Google Gemini using the retrieved context
- Simple, interactive Streamlit chat interface

## 🏗️ How It Works

```
Documents (PDF / DOCX)
        │
   Text extraction → Chunking → Embeddings (Sentence Transformers)
                                      │
                                 FAISS Vector DB
                                      │
User Question → Embed Query → Retrieve Top-K Chunks
                                      │
                 Prompt (Question + Context) → Gemini → Answer
```

1. **Ingestion:** text is extracted from the uploaded files.
2. **Indexing:** the text is split into chunks, embedded, and saved in FAISS.
3. **Retrieval:** the question is embedded and the closest chunks are found.
4. **Generation:** the LLM answers using only the retrieved context.

## 🧰 Tech Stack

| Component    | Technology                     |
|--------------|--------------------------------|
| Language     | Python                         |
| UI           | Streamlit                      |
| Embeddings   | Sentence Transformers          |
| Vector Store | FAISS (CPU)                    |
| LLM          | Google Gemini (`google-genai`) |
| File Parsing | `pypdf`, `python-docx`         |

## 📁 Project Structure

```
RAG_Chatbot/
├── .devcontainer/     # Dev container configuration
├── vector_db/         # Saved FAISS index
├── app.py             # Main Streamlit application
├── requirements.txt   # Python dependencies
├── .gitignore
└── README.md
```

## 💬 Usage

1. Upload one or more PDF / DOCX files.
2. Wait for the documents to be processed and indexed.
3. Type a question in the chat box.
4. Get an answer based on the content of your documents.

## ⚠️ Limitations

- Works best with text-based PDFs; scanned images are not supported (no OCR).
- Answers are only as good as the retrieved chunks and the quality of the source documents.
- Requires an internet connection and a Gemini API key for answer generation.

## 🛣️ Future Improvements

- [ ] Conversation memory for follow-up questions
- [ ] Show source chunks and page numbers with each answer
- [ ] Support more file types (TXT, Markdown, web pages)
- [ ] Re-ranking of retrieved chunks
- [ ] Docker support and cloud deployment

## 👤 Author

**Yashvanth Naidu**
GitHub: [@TheYashvanth](https://github.com/TheYashvanth) · LinkedIn: [Nagotula Yashvanth Naidu](https://www.linkedin.com/in/nagothula-yashvanth-naidu-3416a1268/)
