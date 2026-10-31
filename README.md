# University Student Support AI Assistant

### RAG-Based Question Answering System using ChromaDB and Qwen 2.5

An AI-powered university student support assistant that answers student queries using university documents. The system uses **Retrieval-Augmented Generation (RAG)** to retrieve relevant information from a knowledge base and generate context-aware answers using a Large Language Model (LLM).

## Project Overview

Students often need quick access to university information such as attendance requirements, library rules, internship opportunities, and examination procedures.

This project provides a conversational AI assistant that retrieves relevant information from university documents and generates answers grounded in the retrieved context.

Instead of relying only on the LLM's pretrained knowledge, the system uses document retrieval to provide relevant and context-specific responses.

## Features

- Document-based question answering
- Text chunking with overlapping chunks
- Semantic search using sentence embeddings
- Vector storage and retrieval using ChromaDB
- Context-aware answer generation using Qwen 2.5
- Metadata storage for document identification
- Responses grounded in retrieved information
- Fallback response for questions not covered by the knowledge base

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Sentence Transformers | Generate text embeddings |
| all-MiniLM-L6-v2 | Embedding model |
| ChromaDB | Vector database |
| Qwen 2.5 0.5B Instruct | Answer generation |
| Hugging Face Transformers | Load and run the LLM |
| PyTorch | Model inference |

## System Architecture

```text
University Documents
        |
        v
Document Chunking
        |
        v
Sentence Transformer
        |
        v
Generate Chunk Embeddings
        |
        v
Store in ChromaDB
        |
        |
Student Question
        |
        v
Generate Query Embedding
        |
        v
Retrieve Relevant Chunks
        |
        v
Build Context
        |
        v
Qwen 2.5 LLM
        |
        v
Generate Context-Aware Answer
        |
        v
Final Answer to Student
```

## Knowledge Base

The current implementation uses sample university documents covering:

- **Attendance Policy:** Minimum attendance requirements and examination eligibility.
- **Library Policy:** Library timings, borrowing limits, and return periods.
- **Internship Information:** Placement cell procedures and resume submission.
- **Examination Procedures:** Exam registration, fee payment, and hall ticket downloads.

## How It Works

### 1. Load the Models

The Sentence Transformer model converts text into numerical embeddings. Qwen 2.5 generates answers from the retrieved context.

### 2. Prepare Documents

University policy documents are stored as text with unique document IDs.

### 3. Chunk Documents

Documents are divided into smaller chunks to improve retrieval.

Current configuration:

- Chunk size: 150 characters
- Chunk overlap: 30 characters

### 4. Generate Embeddings

Each document chunk is converted into a 384-dimensional embedding using `all-MiniLM-L6-v2`.

### 5. Store in ChromaDB

The system stores:

- Chunk text
- Embeddings
- Unique chunk IDs
- Document metadata

### 6. Retrieve Relevant Information

When a student asks a question, the system generates a query embedding and retrieves the top 3 relevant chunks from ChromaDB.

### 7. Generate the Answer

The retrieved chunks are combined into a context and passed to Qwen 2.5 with the student's question.

The LLM generates an answer using the provided context.

## Example

**Student Question:**

```text
What is the minimum attendance requirement?
```

**Retrieved Context:**

```text
Students must maintain at least 75% attendance
to be eligible for semester examinations.
```

**AI Answer:**

```text
Students must maintain at least 75% attendance
to be eligible for semester examinations.
``

## Sample Questions

```text
What is the minimum attendance requirement?

How many books can students borrow?

How long can I borrow books?

How can students apply for internships?

How do I download my hall ticket?

What is the hostel fee?
```


## Learning Outcomes

Through this project, I explored:

- Retrieval-Augmented Generation (RAG)
- Text chunking and overlapping chunks
- Sentence embeddings
- Semantic search
- Vector databases
- ChromaDB retrieval
- Prompt engineering
- Context-grounded LLM responses
- End-to-end LLM application development

## Author

**S. Shakeel Ahmad**

Aspiring AI Engineer | Python | Machine Learning | Deep Learning | Generative AI | RAG

---

*This project was developed as a hands-on learning project to understand and implement an end-to-end Retrieval-Augmented Generation pipeline.*
