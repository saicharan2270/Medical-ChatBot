# 🩺 Medical PDF Chatbot (End to End LLM Application)

This project is an **end-to-end Medical PDF Question Answering Chatbot** built using **Retrieval-Augmented Generation (RAG)**.  
Users can upload medical PDF documents and ask natural-language questions. Relevant information is retrieved from the documents using vector search and used by a Large Language Model to generate accurate answers.

The application supports:
- Local execution (Python + Conda)
- Docker-based execution
- Running directly from Docker Hub on any machine

---

##  Project Flow

1. Medical PDFs are loaded from the `data/` directory  
2. Text is split into smaller chunks  
3. Embeddings are generated using HuggingFace sentence transformers  
4. Embeddings are stored in **Pinecone Vector Database**  
5. On user query:
   - Relevant document chunks are retrieved from Pinecone  
   - Context is passed to **OpenAI LLM**  
   - A final answer is generated  

---

## Tech Stack

- **Programming Language:** Python 3.10  
- **Backend Framework:** Flask  
- **LLM:** OpenAI  
- **Embeddings:** HuggingFace Sentence Transformers  
- **Vector Database:** Pinecone  
- **Framework:** LangChain  
- **Containerization:** Docker  
- **Image Hosting:** Docker Hub  

---

## 📂 Project Structure

```
Medical-ChatBot/
│
├── app.py                 # Flask application
├── store_index.py         # PDF ingestion & vector indexing
├── requirements.txt
├── Dockerfile
├── .env                   # Environment variables (not committed)
├── src/
│   ├── helper.py          # PDF loading, chunking, embeddings
│   └── prompt.py          # Prompt templates
└── data/
    └── *.pdf              # Medical PDF files
```

---

## 🔑 Prerequisites

- Python 3.10  
- Conda (recommended)  
- OpenAI API key  
- Pinecone API key  
- Docker  

---

##  Step 1: Clone the Repository

```
git clone <your-github-repo-url>
cd Medical-ChatBot
```

---

##  Step 2: Local Environment Setup

```
conda create -n medibot python=3.10
conda activate medibot
pip install -r requirements.txt
```

---

##  Step 3: Configure Environment Variables

Create a `.env` file in the project root:

```
OPENAI_API_KEY=your_openai_api_key
PINECONE_API_KEY=your_pinecone_api_key
PINECONE_ENVIRONMENT=us-east-1
```

Notes:
- Do NOT use quotes
- Do NOT commit `.env` to GitHub

---

##  Step 4: Index Medical PDFs into Pinecone

1. Add medical PDFs to the `data/` folder  
2. Run:

```
python store_index.py
```

This step loads PDFs, creates embeddings, and stores them in Pinecone.  
Run only once unless PDFs change.

---

##  Step 5: Run the Application Locally

```
python app.py
```

Open in browser:

```
http://localhost:8080
```

---

##  Step 6: Build Docker Image

```
docker build -t medibot .
```

---

##  Step 7: Run Application Using Docker

```
docker run --env-file .env -p 8080:8080 medibot
```

Open in browser:

```
http://localhost:8080
```

Stop container:

```
Ctrl + C
```

---

##  Step 8: Run Application from Docker Hub (Any Machine)

```
docker pull saicharanjogam/medibot
docker run --env-file .env -p 8080:8080 saicharanjogam/medibot
```

No Python, Conda, or GitHub clone required.

---

##  Secret Management

- API keys are injected via environment variables
- Secrets are not stored in code or Docker images
- `.env` is excluded using `.gitignore`

---

## 📌 Key Highlights

- End-to-end **RAG-based chatbot**
- Semantic search with Pinecone
- LLM-powered responses using OpenAI
- Fully Dockerized application
- Docker image published to Docker Hub

---

## 🎯 Future Improvements

- Production server (Gunicorn)
- Conversation memory
- UI improvements
- Reduced Docker image size
- Cloud deployment

---

##  Author

**Sai Charan Jogam**  
Data Science | GenAI | LLMs | RAG Systems  

---


