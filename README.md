RAG-over-PDF with Qdrant + LangChain + OpenAI

A tiny Retrieval-Augmented Generation (RAG) script that:
embeds your PDF chunks into Qdrant,
retrieves the most relevant chunks for a query, and
asks an OpenAI chat model to answer only from those chunks, pointing you to the page numbers.
The script assumes you already have a Qdrant collection named learning_rag populated with embeddings created using OpenAIEmbeddings.

Features
🔎 Similarity search over your PDF chunks stored in Qdrant
🧠 Answers constrained to retrieved context (page text + page number + source file)
🧰 Minimal dependencies, simple CLI run

Prerequisites
Python: 3.10 or 3.11 recommended
OpenAI API key
Qdrant running locally on http://localhost:6333
Docker (quick start):
docker run -d --name qdrant -p 6333:6333 qdrant/qdrant


A Qdrant collection named learning_rag already loaded with your PDF embeddings
(vectors must be generated with an OpenAI embeddings model, e.g., text-embedding-3-large, to match this script)

Project Structure (suggested)
.
├─ .env
├─ requirements.txt
├─ main.py               # your script (paste your code here)
└─ data/                 # optional: where your PDFs live for ingestion

Environment Variables
Create a .env file in the project root:
OPENAI_API_KEY=sk-...


If you want to change the chat model or collection name, you can hardcode or add env vars like:
CHAT_MODEL=gpt-4o
QDRANT_URL=http://localhost:6333
QDRANT_COLLECTION=learning_rag

Installation
# create & activate a virtual environment (recommended)
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate

# install deps
pip install -U pip
pip install langchain langchain-openai langchain-qdrant qdrant-client python-dotenv openai
