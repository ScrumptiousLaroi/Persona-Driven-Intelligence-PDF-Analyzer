# Document Analyst - Persona Driven Intelligence

An intelligent document analysis system that uses AI to extract and rank the most relevant information from PDF documents based on specific personas and tasks.

## 🚀 Features

- **PDF Text Extraction**: Supports both Table of Contents (TOC) based and page-by-page extraction
- **Intelligent Section Titles**: Automatically extracts meaningful section titles from content
- **Semantic Analysis**: Uses sentence transformers to rank content by relevance
- **Persona-Based Analysis**: Tailors analysis based on specific roles and tasks
- **Offline Operation**: Runs completely offline once models are downloaded
- **JSON Output**: Structured output with metadata, ranked sections, and refined analysis

## 📋 Prerequisites

- Python 3.8 or higher
- Internet connection (for initial model download only)

## 🛠️ Setup Instructions

### 1. Clone the Repository

```bash
git clone <your-repo-url>
cd "Persona Driven Intelligence/document_analyst"
```

### 2. Create Virtual Environment

#### On macOS/Linux:
```bash
# Create virtual environment
python3 -m venv venv

# Activate virtual environment
source venv/bin/activate
```

#### On Windows:
```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Download AI Model (One-time setup)

**Important**: This step requires internet connection and will download ~191MB of model files.

```bash
python download_model.py
```

This will download the sentence transformer model locally to the `models/` directory, enabling offline operation.

### 5. Add Your PDF Documents

Place your PDF files in the `documents/` directory. Update the `main.py` file to reference your specific documents.

## 📖 Usage

### Basic Usage

```bash
python main.py
```

This will:
1. Load the AI model from local storage
2. Process all PDF documents specified in `main.py`
3. Perform semantic analysis based on the defined persona and task
4. Save results to `output/analysis_result_[timestamp].json`

### Customizing Analysis

Edit `main.py` to customize:

```python
input_json = {
    "documents": [
        {
            "filename": "your-document.pdf",
            "title": "Your Document Title"
        }
        # Add more documents here
    ],
    "persona": {
        "role": "Your Role Here"  # e.g., "Travel Planner", "Research Analyst"
    },
    "job_to_be_done": {
        "task": "Your specific task"  # e.g., "Plan a 4-day trip"
    }
}
```

## 📁 Project Structure

```
document_analyst/
├── analyzer.py              # Main analysis engine
├── pdf_processor.py         # PDF text extraction
├── main.py                  # Entry point and configuration
├── download_model.py        # Model download script
├── requirements.txt         # Python dependencies
├── documents/              # Place your PDF files here
├── output/                 # Analysis results
├── models/                 # AI models (created after setup)
└── venv/                   # Virtual environment (created during setup)
```

## 📊 Output Format

The system generates a JSON file with:

```json
{
  "metadata": {
    "input_documents": ["list of processed files"],
    "persona": "specified role",
    "job_to_be_done": "specified task",
    "processing_timestamp": "ISO timestamp"
  },
  "extracted_sections": [
    {
      "document": "filename.pdf",
      "section_title": "Meaningful section title",
      "importance_rank": 1,
      "page_number": 5
    }
  ],
  "subsection_analysis": [
    {
      "document": "filename.pdf",
      "refined_text": "Most relevant content extracted...",
      "page_number": 5
    }
  ]
}
```

## 🔧 Troubleshooting

### Model Download Issues
```bash
# If model download fails, try again:
python download_model.py
```

### PDF Processing Issues
- Ensure PDF files are not password protected
- Check that PDF files contain readable text (not just images)
- Verify file paths in `main.py` match your actual file names

### Virtual Environment Issues
```bash
# Deactivate and recreate if needed:
deactivate
rm -rf venv
python3 -m venv venv
source venv/bin/activate  # macOS/Linux
# or
venv\Scripts\activate     # Windows
pip install -r requirements.txt
```

## 🤖 How It Works

1. **PDF Processing**: Extracts text using PyMuPDF, respecting TOC structure when available
2. **Content Enhancement**: Automatically improves section titles for better organization
3. **Semantic Analysis**: Uses sentence transformers to understand content meaning
4. **Relevance Ranking**: Ranks all sections based on similarity to persona/task query
5. **Content Refinement**: Extracts the most relevant sentences from top sections
6. **JSON Generation**: Outputs structured results with timestamps and metadata

## 📦 Dependencies

- `PyMuPDF`: PDF text extraction
- `sentence-transformers`: AI-powered semantic analysis
- `torch`: Deep learning framework
- `numpy`: Numerical computations

## 🔒 Privacy & Offline Operation

- **Fully Offline**: After initial setup, no internet connection required
- **Local Processing**: All analysis happens on your machine
- **No Data Sharing**: Your documents never leave your computer

## 📄 License

This project is provided as-is for educational and research purposes.

## 🤝 Contributing

Feel free to submit issues, feature requests, or pull requests to improve the system.

---

**Note**: The `models/` and `venv/` directories are excluded from version control due to their large size. Follow the setup instructions to create them locally.
