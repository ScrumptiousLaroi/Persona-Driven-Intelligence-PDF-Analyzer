# Persona-Driven Intelligence PDF Analyzer

A sophisticated AI-powered document analysis system that extracts, ranks, and analyzes PDF content based on specific personas and tasks. The system uses semantic analysis to identify the most relevant sections from multiple documents and provides intelligent content refinement.

## Features

- **Semantic Document Analysis**: Uses advanced NLP models to understand document content contextually
- **Persona-Driven Ranking**: Prioritizes content based on specific roles and tasks
- **Intelligent Section Extraction**: Automatically detects meaningful sections using TOC or content analysis
- **Offline Operation**: Runs completely offline after initial model download
- **Structured Output**: Provides clean JSON output with ranked sections and refined content

## Quick Start

### 1. Install Dependencies

```bash
cd document_analyst
pip install -r requirements.txt
```

### 2. Download AI Model (Required - First Time Only)

⚠️ **Important**: You need to run this once with internet connection to download the AI model locally.

```bash
python download_model.py
```

This will download the sentence transformer model (~191MB) to the local `models/` directory, enabling offline operation.

### 3. Add Your PDF Documents

Place your PDF files in the `documents/` folder.

### 4. Configure Analysis

Edit `main.py` to specify:
- Your PDF filenames
- Persona role (e.g., "Travel Planner", "Business Analyst")
- Job to be done (e.g., "Plan a 4-day trip for college friends")

### 5. Run Analysis

```bash
python main.py
```

Results will be saved to the `output/` directory with timestamps.

## Project Structure

```
document_analyst/
├── main.py                 # Main execution script
├── analyzer.py             # Core analysis engine
├── pdf_processor.py        # PDF text extraction
├── download_model.py       # Model download utility
├── requirements.txt        # Python dependencies
├── documents/              # Place your PDF files here
├── output/                 # Analysis results (JSON)
└── models/                 # AI models (auto-created)
```

## Output Format

The system generates JSON output with:

```json
{
  "metadata": {
    "input_documents": ["doc1.pdf", "doc2.pdf"],
    "persona": "Travel Planner",
    "job_to_be_done": "Plan a trip",
    "processing_timestamp": "2025-07-23T19:27:00.068013"
  },
  "extracted_sections": [
    {
      "document": "doc1.pdf",
      "section_title": "Introduction",
      "importance_rank": 1,
      "page_number": 1
    }
  ],
  "subsection_analysis": [
    {
      "document": "doc1.pdf",
      "refined_text": "Most relevant content...",
      "page_number": 1
    }
  ]
}
```

## How It Works

1. **PDF Processing**: Extracts text sections using Table of Contents or intelligent page analysis
2. **Semantic Analysis**: Creates embeddings for content and query using sentence transformers
3. **Relevance Ranking**: Ranks sections by semantic similarity to persona + task
4. **Content Refinement**: Extracts the most relevant sentences from top sections
5. **Structured Output**: Generates clean JSON with metadata and ranked results

## Requirements

- Python 3.8+
- Internet connection (first run only, for model download)
- ~200MB disk space for AI model

## Dependencies

- `sentence-transformers`: For semantic analysis
- `PyMuPDF`: For PDF text extraction
- `torch`: Deep learning framework
- `numpy`: Numerical computing

## Offline Operation

After running `download_model.py` once, the system works completely offline. The AI model is stored locally in the `models/` directory and doesn't require internet access.

## Troubleshooting

### "Model not found" Error
```bash
python download_model.py
```

### "Document not found" Warning
Ensure your PDF files are in the `documents/` folder and filenames match those in `main.py`.

### Import Errors
```bash
pip install -r requirements.txt
```

## Customization

### Change AI Model
Edit `analyzer.py` and `download_model.py` to use a different sentence transformer model.

### Adjust Output Size
Modify the `top_n` variable in `analyzer.py` to change the number of sections analyzed.

### Custom Document Processing
Extend `pdf_processor.py` to handle different document formats or extraction methods.

## License

This project is open source. See LICENSE file for details.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

---

**Note**: The `models/` directory is excluded from version control due to file size. Users must run `download_model.py` to set up the AI model locally.
