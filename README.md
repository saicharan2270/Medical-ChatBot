# Medical PDF Chatbot (End-to-End RAG Application)

An end-to-end Medical PDF Question Answering Chatbot built using Retrieval-Augmented Generation (RAG).
Users can upload medical PDF documents and ask questions in natural language. The system retrieves relevant document context using vector search and generates accurate answers using a Large Language Model.

The project supports:

Local development

Docker-based deployment

Docker Hub distribution

📌 Project Overview

This application follows a RAG pipeline:

Medical PDFs are loaded and processed

Text is split into semantic chunks

Embeddings are generated using HuggingFace models

Embeddings are stored in Pinecone Vector Database

Relevant chunks are retrieved for each query

OpenAI LLM generates answers using retrieved context

🧠 Architecture Flow
PDF → Text Loader → Chunking → Embeddings
     → Pinecone Vector Store
     → Retriever
     → OpenAI LLM
     → Answer

🛠 Tech Stack

Language: Python 3.10

Backend: Flask

LLM: OpenAI

Embeddings: HuggingFace Sentence Transformers

Vector DB: Pinecone

Framework: LangChain

Deployment: Docker, Docker Hub

📂 Project Structure
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
    └── *.pdf              # Medical PDFs

🔑 Prerequisites

Python 3.10

Conda (recommended)

Pinecone account

OpenAI API key

Docker (for deployment)

🚀 STEP 1: Clone the Repository
git clone <your-github-repo-url>
cd Medical-ChatBot

🧪 STEP 2: Local Environment Setup (Development)
Create and activate environment
conda create -n medibot python=3.10
conda activate medibot

Install dependencies
pip install -r requirements.txt

🔐 STEP 3: Environment Variables

Create a file named .env in the project root:

OPENAI_API_KEY=your_openai_api_key
PINECONE_API_KEY=your_pinecone_api_key
PINECONE_ENVIRONMENT=us-east-1


⚠️ Important:

Do NOT wrap values in quotes

Do NOT commit .env to GitHub

📥 STEP 4: Index Medical PDFs into Pinecone

Place your medical PDFs inside the data/ folder.

Run:

python store_index.py


This will:

Load PDFs

Split text into chunks

Generate embeddings

Store vectors in Pinecone

Run this only once unless PDFs change.

▶️ STEP 5: Run the Application Locally
python app.py


Open in browser:

http://localhost:8080

🐳 STEP 6: Dockerize the Application
Build Docker image
docker build -t medibot .

▶️ STEP 7: Run Using Docker (Recommended)
docker run --env-file .env -p 8080:8080 medibot


Open:

http://localhost:8080


Stop with:

Ctrl + C

🌍 STEP 8: Run from Docker Hub (Any Machine)

The image is published to Docker Hub.

Pull image
docker pull saicharanjogam/medibot

Run container
docker run --env-file .env -p 8080:8080 saicharanjogam/medibot


No Python.
No Conda.
No GitHub clone required.

🔐 Secret Management

API keys are injected at runtime

Keys are not baked into the Docker image

.env file is ignored by Git

🧠 Key Learnings

Built a complete RAG pipeline

Understood vector search & semantic retrieval

Solved real-world dependency & environment issues

Containerized ML application using Docker

Published and shared application via Docker Hub

🎯 Future Enhancements

Replace Flask dev server with Gunicorn

Pinecone host-based authentication

Chat history & memory

Cloud deployment (AWS / GCP)

Reduce Docker image size

🧑‍💻 Author

Sai Charan Jogam
Data Science | GenAI | LLMs | RAG Systems
