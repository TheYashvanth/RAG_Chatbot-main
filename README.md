# 🤖 RAG Chatbot

A Retrieval-Augmented Generation (RAG) chatbot built with Streamlit. Upload your documents, ask questions in a chat interface, and get answers grounded in your own content instead of the LLM's general knowledge.

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

| Component    | Technology                         |
|--------------|------------------------------------|
| Language     | Python                             |
| UI           | Streamlit                          |
| Embeddings   | Sentence Transformers              |
| Vector Store | FAISS (CPU)                        |
| LLM          | Google Gemini (`google-genai`)     |
| File Parsing | `pypdf`, `python-docx`             |

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

## 🛣️ Future Improvements

- [ ] Conversation memory for follow-up questions
- [ ] Show source chunks and page numbers with each answer
- [ ] Support more file types (TXT, Markdown, web pages)
- [ ] Re-ranking of retrieved chunks
- [ ] Docker support and cloud deployment

## 📄 License

This project is licensed under the MIT License.

## 👤 Author

**Yashwanth**
GitHub: [@your-username](https://github.com/TheYashvanth) · LinkedIn: [your-profile](https://www.linkedin.com/in/nagothula-yashvanth-naidu-3416a1268/)
