# Hybrid RAG System

This project implements a **Hybrid Retrieval-Augmented Generation (RAG) system** that combines **vector-based retrieval (Vector-RAG)** with **graph-based retrieval (Graph-RAG)**.  
The goal is to integrate semantic search with structured knowledge in order to generate more precise and context-rich responses from Large Language Models (LLMs).

**Neo4j** is used as the underlying knowledge database, while the entire application is **containerized using Docker**.  
For text generation, a locally hosted LLM is used via **Ollama (`llama3.1:8b`)**.


## Quick Start

### Using Docker Compose
```bash
# Start all services
docker-compose up --build

# Services will be available at:
# - neo4j: http://localhost:7474
# - Ollama: http://localhost:11434
```



## ✨ Features

- 🔗 **Hybrid Retrieval**
  - Semantic similarity search (Vector-RAG)
  - Structural and relationship-based queries (Graph-RAG)
- 🧠 **Neo4j as a Central Knowledge Base**
  - Graph data model
  - Vector indexes for embeddings
- 🤖 **Local LLM**
  - `llama3.1:8b` via Ollama
- 🐳 **Docker-Based Execution**
  - Easy reproducibility
  - Clear separation of services
- 🔌 Modular architecture (retrieval, ranking, generation)

---

## 🏗️ File Structure

```text
Hybrid-RAG/
├── docker-compose.yaml              # Services orchestration
└── Hybrid-RAG/
    ├── config/
    │   └── settings.py
    ├── graph/
    │   ├── create_index.py
    │   ├── graph_builder.py
    │   ├── neo4j_connector.py
    │   └── vectorstore_builder.py
    ├── neo4j/
    │   ├── plugins/
    │   └── Dockerfile
    └── rag/
        ├── rag_chain.py
        ├── retriever.py
        └── schemas.py




# Environment Variables

## Neo4j (for Graph-RAG)
NEO4J_AUTH=neo4j/ps_neo4jj
NEO4J_URI=bolt://localhost:7687


## Test Queries
    - Who is Isabel?
    - Describe the structure of the Moreno family: who belongs to each generation, how they  are related to each other, and where each nuclear family lives.

## Instructions
    1. Make sure Docker is running 
    2. Check port 7474, 7687, 8008 and 11434 is accessible
    3. Ensure Ollama is running: docker-compose ps ollama
    4. Ensure the model llama3.1:8b is installed in Ollama