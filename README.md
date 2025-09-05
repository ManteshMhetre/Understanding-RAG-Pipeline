Complete RAG Pipeline
        
        
        
        ┌─────────────────────────┐
        │        User Query        │
        │ "What steps in ... ?"    │
        └────────────┬────────────┘
                     │
                     ▼
        ┌─────────────────────────┐
        │ Retriever (FAISS DB)    │
        │ • Converts query → emb  │
        │ • Finds similar chunks  │
        └────────────┬────────────┘
                     │  Relevant Docs
                     ▼
        ┌─────────────────────────┐
        │ Document Chain          │
        │ • Format docs into text │
        │ • Stuff into prompt     │
        └────────────┬────────────┘
                     │  Prompt with context
                     ▼
        ┌─────────────────────────┐
        │ Gemini LLM (1.5 Flash)  │
        │ • Reads context         │
        │ • Generates grounded    │
        │   natural answer        │
        └────────────┬────────────┘
                     │  Answer
                     ▼
        ┌─────────────────────────┐
        │      Final Output       │
        │ response['answer']      │
        └─────────────────────────┘
