# PDF Analyzer - Persona-Driven Document Intelligence

## 🎯 Overview

This PDF analyzer extracts and analyzes relevant content from multiple PDF documents based on a specified persona and task. It uses advanced semantic analysis to identify and prioritize the most relevant information for your specific needs.

## 🏗️ Core Components

### Essential Files
- `analyzer.py` - Main PDF analyzer with document diversity and semantic analysis
- `pdf_processor.py` - PDF text extraction and section processing
- `main.py` - Main execution script
- `download_model.py` - Model download utility for offline operation
- `requirements.txt` - Python dependencies

### Key Directories
- `documents/` - Place your PDF files here
- `models/` - Local sentence transformer model for offline operation
- `output/` - Generated analysis results
- `venv/` - Python virtual environment

## 🚀 Key Features

### Intelligent PDF Analysis
- **Document Diversity**: Ensures content is extracted from multiple PDF sources
- **Semantic Ranking**: Uses sentence transformers for intelligent content prioritization
- **Context-Aware Processing**: Adapts analysis based on persona and task requirements
- **Offline Operation**: Works without internet connection using local AI models

### Customizable Analysis
- **Flexible Input**: Supports any number of PDF documents
- **Persona-Driven**: Tailors analysis to specific roles (e.g., Travel Planner, Student, etc.)
- **Task-Specific**: Focuses on relevant content for your specific job to be done
- **Rich Output**: Provides structured JSON with extracted sections and refined content

## 🛠️ Usage

### Setup
1. Place your PDF files in the `documents/` folder
2. Update the JSON data in `main.py` with your PDF filenames, persona, and task
3. Run the analyzer

### Running the Analyzer
```bash
python main.py
```

### Download Model (first time setup)
```bash
python download_model.py
```

## 📋 Requirements

- Python 3.8+
- sentence-transformers
- torch
- PyPDF2
- numpy

Install dependencies:
```bash
pip install -r requirements.txt
```

## 🎨 How to Customize

### 1. Add Your PDFs
Place your PDF files in the `documents/` folder.

### 2. Update main.py
Modify the input JSON in `main.py` to specify:
- Your PDF filenames
- Persona (role/perspective for analysis)
- Job to be done (specific task or goal)

Example:
```python
input_json = {
    "documents": [
        {"filename": "report1.pdf", "title": "Financial Report"},
        {"filename": "report2.pdf", "title": "Market Analysis"}
    ],
    "persona": {"role": "Financial Analyst"},
    "job_to_be_done": {"task": "Identify key investment opportunities"}
}
```

### 3. Run Analysis
Execute `python main.py` to generate your analysis results in the `output/` folder.

## 📝 Output Structure

The analyzer generates structured JSON output containing:
- **Metadata**: Input documents, persona, task, and timestamp
- **Extracted Sections**: Top-ranked sections with importance rankings
- **Subsection Analysis**: Refined content with key insights from each document

## 🎯 Technical Implementation

### Advanced Features
- Document diversity algorithm ensures multi-source content extraction
- Enhanced semantic queries improve relevance scoring
- Improved section title extraction from PDF content
- Balanced ranking considering relevance, content quality, and diversity

### AI Model
- Uses sentence-transformers (all-MiniLM-L6-v2) for semantic understanding
- Local model caching for offline operation
- Efficient similarity calculations for content ranking

This PDF analyzer provides an intelligent way to extract and analyze relevant information from your documents based on your specific needs and perspective.
