# Tools in Data Science (TDS) – APIs, Embeddings & Function Calling

This document summarizes Week 3 – Session 4 of the Tools in Data Science (TDS) course.
The session focused on interacting with Large Language Models using APIs, understanding embeddings in practice, vector similarity calculations, and using function calling to extract structured information from data.

---

## Session Details

**Course:** Tools in Data Science (TDS)
**Session:** Week 3 – Session 4
**Mode:** Recorded Online Session
(https://youtu.be/PYj9eOPpH7k)

**Focus Area:** API usage, embeddings, vector operations, multimodal inputs & function calling

---

## Session Overview

This session moved from theory to implementation. We learned how applications communicate with AI models using APIs, how embeddings are computed and compared mathematically, and how LLMs can call functions to return structured outputs. The session also demonstrated building a chatbot workflow and extracting information from images and text.

---

## Topics Covered

### API Calls & HTTP Requests

Understanding how applications communicate with AI services using HTTP requests.

* POST requests
* Headers & authentication
* JSON data exchange
* Chat completion APIs

---

### Setting Up Environment

Configured API keys and environment variables using `.bashrc` for secure access to AI services.

---

### Chat Completion Workflow

Basic chatbot architecture:

1. User message
2. System prompt
3. Assistant response
4. Conversation history

---

### Base64 Encoding

Used for sending images and binary data through APIs.

Used in:

* Image input
* Multimodal models
* File transfer

---

### Embeddings & Vector Databases

Practical implementation of embeddings and storing vectors.

Operations performed:

* Generate embeddings
* Store vectors
* Retrieve similar vectors

---

### Cosine Similarity & Distance Calculation

Measured similarity between vectors mathematically.

Used to:

* Find related text
* Retrieve context
* Rank search results

---

### Multimodal Embeddings

Models can understand multiple formats:

* Text
* Images
* Documents

Allows extracting product details from images.

---

### Function Calling

LLMs can call predefined functions to produce structured outputs instead of plain text.

Examples:

* Extract manufacturing date
* Extract expiry date
* Structured JSON responses

---

### Tool Usage & Schema Definition

Defined schemas to guide model responses and control output format.

---

## Key Learnings

* Learned how applications interact with LLMs through APIs
* Understood vector similarity mathematically using cosine distance
* Learned how chatbots maintain conversation history
* Understood multimodal AI (text + image processing)
* Learned how function calling produces structured outputs

---

## Tools & Concepts Introduced

* HTTP APIs
* JSON Requests
* Embeddings
* Cosine Similarity
* Vector Databases
* Multimodal Models
* Function Calling
* Structured Outputs

---

## Outcome

This session demonstrated how real-world AI applications are built — combining APIs, embeddings, and structured function outputs to create reliable and controllable AI systems rather than simple text generators.
