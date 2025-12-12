# 🕸️ GraphRAG: Logic-Enhanced Retrieval Augmented Generation

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Gradio](https://img.shields.io/badge/Frontend-Gradio-orange)
![LlamaIndex](https://img.shields.io/badge/Framework-LlamaIndex-purple)

## Abstract
Standard RAG (Retrieval-Augmented Generation) systems often fail at "multi-hop reasoning"—answering questions where the answer requires connecting two disparate pieces of information across a document. 

**GraphRAG** is a prototype that solves this by structuring unstructured text into a **Knowledge Graph**. By modeling data as **Nodes (Entities)** and **Edges (Relationships)**, the system can "traverse" the logic of a story to answer complex queries that pure vector search misses.

This repository features a **Full-Stack Implementation** with a Gradio web interface, designed to demonstrate the difference between standard retrieval and graph-based reasoning.

## Key Features

### 1.  Knowledge Graph Architecture
Unlike vector databases that only find "similar words," this system builds a directed graph (using `NetworkX`) to map logical dependencies (e.g., `(Director Vance) --[STOLE_FROM]--> (Dr. Aris)`).

### 2. Hybrid Retrieval Engine
The system employs a dual-path retrieval strategy:
* **Vector Path:** Uses HuggingFace Embeddings (`BAAI/bge-small-en`) for semantic context.
* **Graph Path:** Uses Graph Traversal to find hidden relationships between entities.

### 3. Resilience & Fallback Mode
To ensure high availability during demos, the system includes a **"Curated Graph State"**. If the external LLM API experiences latency or downtime, the system automatically degrades to a robust, pre-computed Knowledge Graph to maintain service continuity.

### 4. Interactive Web Interface
Built with **Gradio**, providing a no-code environment for users to:
* Upload Datasets (`.txt`)
* Visualize System Logs
* Chat with the Graph Engine

## Architecture & Demo

**The Interface:**
The system accepts raw text files and builds a queryable index in real-time.

<img src="images/Interface.png" width="600">

**The Graph Logic:**
An example of the internal graph structure mapping the "Project Chimera" dataset.
<img src="images/Graph.png" width="600">

##  Tech Stack
* **Language:** Python 3.10
* **Orchestration:** LlamaIndex
* **Graph Theory:** NetworkX
* **Frontend:** Gradio
* **Embeddings:** HuggingFace `BAAI/bge-small-en-v1.5`

## Usage Guide

### Prerequisites
* Python 3.10+ installed
* Google Colab (Recommended) or Local GPU environment

### Installation
1.  Clone the repository:
    ```bash
    git clone [https://github.com/YourUsername/GraphRAG-UI.git](https://github.com/YourUsername/GraphRAG-UI.git)
    cd GraphRAG-UI
    ```

2.  Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```

3.  Run the Application:
    ```bash
    python app.py
    ```

### Workflow
1.  **Launch:** Open the generated Gradio link (e.g., `http://127.0.0.1:7860`).
2.  **Upload:** Drag and drop a text file containing the knowledge base.
3.  **Build:** Click "Build Knowledge Graph" to trigger the indexing pipeline.
4.  **Query:** Ask complex questions like *"How is Entity A related to Entity B?"*

## Benchmark Example
* **Dataset:** "Project Chimera" (Sci-Fi Narrative)
* **Query:** *"How is Director Vance related to the Neural Key?"*
* **Standard Search Result:** Fails to find a direct link.
* **GraphRAG Result:** *"Director Vance stole the project from Dr. Aris. Dr. Aris created the Neural Key. Therefore, Vance is indirectly connected via the theft from the creator."*

## Future Scope
* Integration with **Neo4j** for persistent graph storage.
* Deployment of **GNN (Graph Neural Networks)** for link prediction.
* Support for PDF and multi-modal file ingestion.

---
