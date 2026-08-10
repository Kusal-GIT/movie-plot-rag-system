# Movie Plot RAG System

## Overview

This project implements a lightweight Retrieval-Augmented Generation (RAG) system for answering questions about movie plots.

The system uses semantic retrieval with FAISS, cross-encoder reranking, and Gemini for grounded answer generation.

Answers are generated using the retrieved movie plot context, with a fallback when the required information is not available in the retrieved context.

## Architecture

The system follows a multi-stage RAG pipeline:

1. Movie plot dataset
2. Data preprocessing and text chunking
3. Sentence embeddings
4. FAISS vector retrieval
5. Cross-encoder reranking
6. Relevant context selection
7. Gemini-based answer generation
8. Structured JSON output
9. Evaluation using test questions

## Technologies Used

- Python
- Google Colab
- FAISS
- Sentence Transformers
- Cross-Encoder
- Gemini API
- Pandas
- NumPy

## RAG Pipeline

The question is first converted into an embedding and searched against the FAISS vector index to retrieve a broad set of candidate movie-plot chunks.

The retrieved candidates are then reranked using a cross-encoder. The highest-ranked contexts are selected and provided to Gemini as the only source of information for answer generation.

If the retrieved context does not contain enough information to answer the question, the system returns an explicit unavailable-answer response instead of relying on outside knowledge.

## Evaluation

The system was tested with different types of movie-plot questions.

### Test Cases

- **Robot Gort:** Correctly retrieved *The Day the Earth Stood Still*.
- **Dog-shaped mecha:** Correctly retrieved *Yatterman*.
- **Klaatu:** Correctly used relevant movie-plot contexts to answer the question.
- **Out-of-scope question:** The system returned an unavailable-answer response when the required information was not present in the retrieved context.

These tests evaluate retrieval quality, reranking, grounded generation, and the system's ability to avoid unsupported answers.

## How to Run

1. Open the Google Colab notebook.
2. Install the required Python libraries.
3. Load the movie plot dataset.
4. Run the preprocessing and chunking steps.
5. Generate embeddings and build the FAISS index.
6. Run the retrieval and cross-encoder reranking pipeline.
7. Configure the Gemini API key.
8. Run the evaluation queries.

The project is designed to run in Google Colab without requiring a local Python, Docker, or VS Code setup.

## Project Structure

```text
Movie_Plot_RAG_System/
│
├── Movie_Plot_RAG_System.ipynb
├── README.md

```

