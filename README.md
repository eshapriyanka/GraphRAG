# 🕸️ GraphRAG: Knowledge Graph Retrieval Engine

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![NetworkX](https://img.shields.io/badge/Graph-NetworkX-green)

## Abstract
Standard RAG (Retrieval-Augmented Generation) systems often fail at "multi-hop reasoning"—answering questions where the answer requires connecting two disparate pieces of information across a document. 

## Key Features
* **Structured Knowledge Representation:** Utilizes `NetworkX` to model entities as nodes and relationships as directed edges.
* **Hybrid Data Modeling:** Combines unstructured text embeddings (HuggingFace BGE) with structured graph data.
* **Interactive Visualization:** Uses `Pyvis` to generate dynamic HTML network representations.

## Methodology
1.  **Ingestion:** Raw narrative text is analyzed to identify key Entities.
2.  **Graph Construction:** Entities are mapped into a `DiGraph` structure.
3.  **Visualization:** The network is rendered to visually verify reasoning paths.

## Visualization
<img src="images/graph.png" width="600">

## How to Run
1. Install dependencies:
   ```bash
   pip install networkx pyvis llama-index-embeddings-huggingface
2. Run the notebook GraphRAG.ipynb.
3. Open graph.html to see the interactive network.
---
