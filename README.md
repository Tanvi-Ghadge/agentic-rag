Autonomous Agentic RAG Framework with Web Search and Tool-Use:


This repository showcases a sophisticated, agent-driven RAG system capable of dynamically handling complex queries that require multiple steps: real-time web ingestion, retrieval-augmented generation, and mathematical calculation.

The core of this project is a Router Agent built on LangChain, which intelligently orchestrates various specialized tools to deliver a grounded, accurate, and high-speed response.

Key Features:

Agentic Routing: A central "Router Agent" decides the optimal flow of execution based on the user's prompt, automatically triggering the correct sequence of tools (e.g., ingest URL, then retrieve, then answer, or simply calculate).

Triple-Stage Optimized Retrieval: Implements a highly effective retrieval pipeline:

Hybrid Retrieval (EnsembleRetriever): Combines keyword search (BM25) and semantic search (Pinecone) to ensure high recall.

Cross-Encoder Re-ranking: A cross-encoder/ms-marco-MiniLM-L-6-v2 model is used to re-score and prioritize the most relevant documents, significantly boosting precision.

On-Demand Web Ingestion: Features a custom, depth-limited web crawler (requests, BeautifulSoup) tool that can scrape new URLs, chunk the content, and vectorize it into the Pinecone index for immediate RAG use.

High-Speed LLM Inference: Utilizes the Groq API with a high-performance model (meta-llama/llama-4-scout-17b-16e-instruct) for rapid decision-making and final answer generation.

Tool Utilization: Equipped with a calculator_tool to handle numerical and cost-estimation questions accurately

## Project Architecture & Technologies

| Component | Technology / Function | Role in Pipeline |
| :--- | :--- | :--- |
| **Agent Core** | **LangChain Agent** | Decision-making, Tool Orchestration |
| **LLM Inference** | **Groq API** (`llama-4-scout-17b-16e-instruct`) | Low-latency response and reasoning |
| **Data Ingestion** | **Custom Web Crawler** (`requests`, `BeautifulSoup4`) | Real-time fetching and text extraction |
| **Vector Store** | **Pinecone** | Storing and retrieving vectorized content |
| **Retrieval** | **EnsembleRetriever (BM25 + Dense)** | Maximize recall and contextual completeness |
| **Re-ranking** | **Cross-Encoder** | Maximize precision of retrieved documents |
| **Utility Tool** | **calculator_tool** **ingestion_tool** **answering_tool** **retriever_tool** | Handles mathematical expressions and budget calculation |
