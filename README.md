# 🤖 FusionMind AI – Intelligent RAG Agent

FusionMind AI is an intelligent chatbot system that combines **Retrieval-Augmented Generation (RAG)** with **web search**, allowing it to answer user queries using both **uploaded PDFs** and **live internet information**. It provides accurate, context-aware, and traceable responses through an interactive Streamlit interface.

---

## ⭐ Main Objective

The primary goal of FusionMind AI is to build an **AI assistant capable of understanding user queries and responding using two knowledge sources**:

1. **Documents uploaded by the user** (internal knowledge base)
2. **Real-time web search information**, when needed

The agent intelligently decides **how to answer**, ensuring the most relevant, trustworthy, and up-to-date information is used.

---

## 🎯 Purpose of the Project

FusionMind AI aims to solve a common problem:

> *“How can an AI assistant use both private knowledge (PDFs) and the live internet to answer questions accurately?”*

This project demonstrates:

- How to build a RAG pipeline with vector search  
- How to integrate LLMs with decision-making graphs  
- How to create a hybrid AI system combining static and dynamic knowledge  
- How to offer transparent, traceable AI reasoning to the user  

It can be used for:

- Study assistants  
- Resume/Q&A analysis  
- Document-based chatbots  
- AI research tools  
- Customer support bots  

---

## 📌 About the Project

FusionMind AI consists of a **FastAPI backend** and a **Streamlit frontend**, connected to a vector database for RAG.  

The system workflow:

1. **User uploads a PDF**  
2. Document text is extracted, chunked, and stored in a **vector index**  
3. User asks a question  
4. The agent routes the query using an LLM:  
   - Use **RAG** if relevant info exists in uploaded PDFs  
   - Use **Web Search** if the information is missing  
   - Provide a **direct LLM answer** if appropriate  
5. A final response is generated with transparent reasoning  
6. The user also sees a **workflow trace**, showing exactly how the agent thought  

---

## ✨ Key Features

### 🔍 PDF Knowledge Base (RAG)
- Upload PDF documents  
- Automatic text extraction and chunking  
- Semantic search through vector embeddings  
- Answers grounded in your documents  

### 🌐 Optional Web Search
- If PDF data is insufficient, the agent retrieves real-time information from the internet  
- Can be toggled ON/OFF  

### 🧠 Intelligent Routing  
The agent decides:
- **RAG first** when document knowledge is available  
- **Web search** only when necessary  
- **Direct answer** for simple questions  
- **End** for greetings or small talk  

### 💬 Chat Interface
- Clean and modern Streamlit UI  
- Interactive chat messages  
- Document upload panel  
- Agent settings panel  

### 🔬 Workflow Trace Visualization
- Shows each step: routing → RAG → web search → final answer  
- Displays how decisions were made  
- Helps debug and understand agent behavior  

---

## 🔗 APIs & Services Used in This Project

FusionMind AI integrates multiple modern AI APIs and cloud services:

### 🧠 **Groq API**
Used for:
- Running LLMs  
- Routing decisions (router)  
- RAG sufficiency judging  
- Final answer generation  

Groq provides extremely fast inference for LLaMA models.

---

### 📚 **Pinecone Vector Database**
Used for:
- Storing document embeddings  
- Retrieving top semantic chunks during RAG  

Pinecone enables high-speed, scalable vector search.

---

### 🌐 **Tavily Web Search API**
Used for:
- Real-time internet search when RAG does not have enough information  

Provides reliable, structured web search results.

---

### ⚡ **FastAPI Backend**
Used for:
- Handling chat requests  
- Uploading & processing PDFs  
- Exposing REST API endpoints  
- Connecting frontend ↔ backend  

Endpoints:

| Method | Endpoint | Purpose |
|--------|----------|---------|
| POST | `/upload-document/` | Uploads a PDF and stores chunks in Pinecone |
| POST | `/chat/` | Sends chat query to the agent |
| GET | `/health` | Health check |

---

### 🎨 **Streamlit Frontend**
Used for:
- Chat interface  
- PDF uploader  
- Agent settings  
- Workflow trace visualization  