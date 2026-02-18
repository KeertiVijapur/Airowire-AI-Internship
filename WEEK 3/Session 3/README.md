# Tools in Data Science (TDS) – Embeddings & Vector Retrieval

This document summarizes the third session of Week 3 in the Tools in Data Science (TDS) course, focusing on embeddings, vector databases, and building a semantic question-answer retrieval workflow.

---

## Session Details

**Course:** Tools in Data Science (TDS)
**Session:** Week 3 – Session 3
**Mode:** Recorded Online Session
(https://youtu.be/qqgBvapfrCc)

**Focus Area:** Embeddings, Vector Databases, Chunking & Semantic Search

---

## Session Overview

This session introduced how modern AI systems retrieve relevant information from large text data. Instead of searching using keywords, text is converted into numerical vectors called embeddings. These vectors are stored in a vector database and similarity search is used to retrieve the most relevant context before generating an answer.

---

## Topics Covered

### Embeddings

Text is converted into numerical vector representations that capture semantic meaning rather than exact words.

* Similar sentences produce similar vectors
* Enables semantic search instead of keyword matching

---

### Multimodal Embeddings

Embeddings are not limited to text — images, audio, and documents can also be represented as vectors and compared using similarity metrics.

---

### Vector Databases

Vector databases store embeddings and allow similarity-based retrieval.

Instead of:

> Search → exact keyword match

We use:

> Search → closest meaning match

---

### Chunking Large Documents

Large text documents are split into smaller pieces before embedding.

Reasons:

* Fits model context limits
* Improves retrieval accuracy
* Faster search

Each chunk contains:

* ID
* Source
* Text
* Embedding vector

---

### Asking Questions (Semantic Retrieval)

When a user asks a question:

1. Convert question into embedding
2. Compare with stored vectors
3. Retrieve most relevant chunks
4. Send context to LLM
5. Generate accurate answer

This forms the base of **Retrieval Augmented Generation (RAG)**.

---

## Key Learnings

* Learned how AI systems understand meaning using embeddings
* Understood difference between keyword search and semantic search
* Learned why chunking is necessary for large documents
* Understood how vector databases retrieve relevant information
* Learned the pipeline used in modern AI assistants

---

## Tools & Concepts Introduced

* Embeddings
* Vector Databases
* Semantic Search
* Chunking
* Similarity Metrics
* Retrieval Augmented Generation (RAG)

---

## Outcome

This session explained the core architecture behind modern AI assistants. Instead of memorizing all knowledge, AI systems retrieve relevant information using vector similarity and then generate responses, making them scalable and accurate.
 next — that one is prompt engineering + agents + evaluation (important interview topic).
