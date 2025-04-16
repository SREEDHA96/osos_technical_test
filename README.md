# osos_technical_test
# Document Processing and Evaluation System

## Overview
This system provides a full pipeline for document extraction, translation, summarization, semantic search, and question answering. It supports various document formats and languages and includes evaluation metrics for output quality.

## Key Features

### Document Processing
- **Multi-format Support**: DOCX, PDF, TXT, and HTML.
- **Text Chunking**: Segments text while preserving structure and context.
- **Table Extraction**: Extracts tables from documents with structure maintained.
- **Vector Embeddings**: Generates document embeddings for semantic retrieval.

### Analysis Capabilities
- **Translation**: Multilingual translation with fluency polishing (English and Arabic).
- **Summarization**: Generates concise summaries with quality evaluation.
- **Question Answering**: Context-aware answers using semantic matching.
- **Semantic Search**: Retrieves content by meaning, not just keywords.

## Evaluation Metrics

### Extraction Metrics
- **Chunk Extraction Quality**: Structure and content preservation.
- **Table Preservation**: Accuracy in table formatting and data integrity.
- **Special Format Handling**: For elements like code blocks.

### Processing Metrics
- **Text Evaluation**: ROUGE-1, ROUGE-2, ROUGE-L, BLEU.
- **Semantic Coherence**: ROUGE-L F1 Score (0.00–1.00).
- **Translation Preservation Score**: Measures translation fidelity via cosine similarity between original and back-translated embeddings.
- **Answer Grounding Score**: Measures contextual alignment between the answer and retrieved chunks.

### Summarization Quality Bands
- **Excellent**: 0.85–1.00
- **Good**: 0.70–0.84
- **Adequate**: 0.50–0.69
- **Poor**: < 0.50

## Implementation Details

### Chunking Strategies
- **Sentence-based Chunking**: Uses sentence boundaries.
- **Token-based Chunking**: Based on max token limits.
- **Table-aware Chunking**: Preserves layout and logic of tabular content.

### Vector Embedding and Similarity
- **Model Used**: `all-MiniLM-L6-v2` via `sentence-transformers`
- **Similarity Metric**: Cosine similarity using `util.pytorch_cos_sim`

## CLI Tool Features
- `extract-text-from-file <path>` – Extracts text from supported files
- `extract-text-from-url <url>` – Downloads and extracts web content
- `extract-text-from-specific-element <path>` – Extracts specific elements
- `extract-all-tables` – Extracts tables from documents
- `extract-tables-from-sheet` – For spreadsheet-like tables

## Error Handling
- Connection errors
- Format-related exceptions
- Unsupported file types or corrupted files

## Getting Started

### Requirements
- Python 3.8+
- Google Colab Pro (for optimal GPU performance)
- T4 GPU support (used if available)
- Install dependencies:

```bash
pip install -r requirements.txt
