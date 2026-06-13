# 🤖 Open-Source Scalable RAG Engine

A production-grade, low-latency Retrieval-Augmented Generation (RAG) system built entirely using an open-source AI stack. This system extracts native text contents from documentation layers, builds vectorized dense representations, caches spatial clusters, and answers arbitrary text prompts with precise mathematical grounding and document source citations.

## 🚀 Live Demo Profile
* **System Interactive UI Interface URL:** [https://14b163cc390b9faa95.gradio.live/]
* **Target Core Infrastructure:** Optimized for isolated hardware/local container execution (No external paid APIs used).

## 🛠️ Architectural Stack & Engineering Rationales
1. **Document Ingestion (`PyMuPDF / fitz`):** Selected for its extreme text extraction throughput. It retains high structural orientation accuracy, allowing us to map chunk elements to absolute 1-indexed document page coordinates for citation tracing.
2. **Text Segmentation Structure (`RecursiveCharacterTextSplitter`):** Configured with a `chunk_size` of 400 characters and a `chunk_overlap` of 50 characters. Rather than processing absolute string boundaries, it isolates concepts via sequential structural boundaries (`\n\n`, `\n`, ` `), preserving core semantic context.
3. **Dense Vector Mapping (`all-MiniLM-L6-v2`):** A lightweight open-source Sentence-Transformer that transforms texts into a 384-dimensional continuous space. It handles semantic search calculations locally within microseconds.
4. **Local Spatially-Indexed Cache (`ChromaDB`):** An open-source vector store operating natively via HNSW graph indexes. It fulfills the non-functional 2–5s total response throughput requirement under scale.
5. **Grounded Synthesis Model (`Qwen2.5-1.5B-Instruct`):** A highly performant 1.5-billion parameter model deployed natively onto hardware VRAM via `transformers` inference pipelines.

## ⚙️ How to Reproduce and Run Locally
1. Clone the repository:
   ```bash
   git clone https://github.com
   cd opensource-rag-engine
   ```
2. Install dependencies:
   ```bash
   pip install pymupdf chromadb transformers reportlab gradio langchain-text-splitters torch
   ```
3. Execute the notebook runtime or python script layout to compile the local collection assets and mount the live interface endpoint.
