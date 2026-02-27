# AlgoMatch — Local DSA Pattern Intelligence Engine

AlgoMatch is a fully local Retrieval-Augmented Generation (RAG) system that maps natural language software problems to the most suitable Data Structures & Algorithm patterns and produces compiling C++ boilerplate.

It combines semantic similarity search with agent-style LLM reasoning to recommend optimal computational strategies based on constraints.

---

## ⚙️ Architecture

- **Frontend:** Streamlit (interactive UI + formatted output)
- **Vector Database:** Endee (384-dimension cosine similarity index)
- **Embeddings:** Sentence-Transformers (`all-MiniLM-L6-v2`)
- **LLM Runtime:** Ollama
- **Model:** LLaMA 3
- **Output:** Pattern explanation + STL-compliant C++ template

---

## 🔄 Processing Flow

1. User submits a problem statement  
2. Query is converted into a 384-dim embedding  
3. Endee retrieves top matching DSA patterns  
4. Retrieved metadata is injected into LLaMA 3  
5. Model evaluates tradeoffs and generates final C++ code  

---

## 🛠 Local Setup

### 1. Start Endee Server
```bash
docker run -p 8080:8080 -v endee-data:/data --name endee-server -d endeeio/endee-server:latest
```

### 2. Pull LLaMA 3 Model
```bash
ollama pull llama3
```

### 3. Configure Python Environment
```bash
cd AlgoMatch
python -m venv venv

# macOS/Linux
source venv/bin/activate

# Windows
.\venv\Scripts\activate

pip install -r requirements.txt
```

### 4. Launch Application
```bash
streamlit run app.py
```

The vector index is automatically initialized on first execution.

---

## 🔐 Highlights

- Fully local (no external APIs)
- Fast semantic retrieval
- Agent-based algorithm selection
- Clean, production-ready C++ output
