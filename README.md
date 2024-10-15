
# PDF Question Answering System Using RAG (Retrieval-Augmented Generation)

This repository implements a simple question-answering system that extracts relevant information from PDFs using **Retrieval-Augmented Generation (RAG)**. The process involves embedding PDF text chunks, searching with FAISS (Facebook AI Similarity Search), and generating answers using a T5 language model.

## Table of Contents
- [Installation](#installation)
- [Overview](#overview)
- [Usage](#usage)
- [Model Loading](#model-loading)
- [Workflow](#workflow)
- [Example](#example)

## Installation

To run this code, you need to install the following dependencies:

```bash
pip install PyPDF2 sentence-transformers faiss-cpu transformers
```

These libraries are required for PDF processing, vector search, embedding, and generating answers.

## Overview

This system allows you to query a PDF file and retrieve relevant text along with a generated answer. It follows a structured workflow:
1. Extract text from a PDF.
2. Chunk the extracted text into manageable pieces.
3. Create embeddings for the text chunks using a SentenceTransformer model.
4. Index the embeddings using FAISS for efficient similarity search.
5. Use FAISS to find relevant chunks based on your query.
6. Generate a concise answer using the relevant chunks with a T5 model.

## Usage

1. **Load the PDF**: Provide the path to the PDF from which you'd like to extract text.
2. **Run the pipeline**: Execute the process to extract relevant information from the document by querying a specific question.
3. **Answer generation**: The system will generate a short and context-aware answer.

## Model Loading

- **Sentence Transformer**: We use the lightweight model `all-MiniLM-L6-v2` for efficient text embedding.
- **T5 Language Model**: The `flan-t5-large` model is used to generate human-like answers from the extracted PDF content.
- Both models can be loaded on CPU or GPU (recommended).

## Workflow

1. **Extract Text from PDF**: Text is extracted from each page of the PDF using `PyPDF2`.
2. **Chunk Text by Sequence Length**: The text is split into chunks of 500 tokens to ensure efficient processing.
3. **Embedding the Text Chunks**: Each text chunk is embedded using `SentenceTransformer`.
4. **Create FAISS Index**: The embeddings are indexed using FAISS for fast similarity search.
5. **Vector Search**: Given a query, the most relevant text chunks are retrieved by searching the FAISS index.
6. **Answer Generation**: Using the T5 model, an answer is generated based on the relevant chunks.

## Example

Here’s an example of how you can run the process:

1. **PDF Input**: Load a PDF file.
2. **Query**: Ask a question, for instance, "Who are eligible to take Input Tax Credit?"
3. **Generated Answer**: The system will return a concise and relevant answer based on the content of the PDF.

### Running the Script

```bash
python main.py
```

### Sample Output

```plaintext
Answer: Persons eligible to take Input Tax Credit include ...
```

## Conclusion

This project demonstrates a practical application of **Retrieval-Augmented Generation (RAG)** using FAISS and T5 for question answering from PDFs. You can extend it to various domains by adjusting the input PDF and refining the models.
