# Text Extractor

A Python tool that recursively extracts text from PDF, DOCX, ODT, and TXT files in a directory tree and saves the results to a JSON file.

**Author:** dpmattos  
**Email:** dpmattos@uwaterloo.ca  
**GitHub:** [dpmattos/text-extractor](https://github.com/dpmattos/text-extractor)

## Features

- Recursively scans directories for files
- Supports multiple formats: PDF, DOCX, ODT, TXT
- Configurable file type filtering
- Progress reporting with verbose mode
- JSON output with filename, extension, and extracted text

## Quick Setup

```bash
# Clone the repository
git clone https://github.com/dpmattos/text-extractor.git
cd text-extractor

# Setup virtual environment and install dependencies
make setup

# Activate the environment
source venv/bin/activate
```

## Installation

### Using Make (recommended)

```bash
make setup          # Create venv and install package
make install        # Install package in existing venv
make dev            # Install with development dependencies
make clean          # Remove venv and cache files
```

### Manual installation

```bash
python -m venv venv
source venv/bin/activate
pip install -e .
```

## Usage

```bash
text-extract /path/to/directory [--output=results.json] [--verbose] [--include=pdf,docx,odt,txt]
```

## Options

- `-o, --output` — Output JSON file (default: `extracted_text.json`)
- `-v, --verbose` — Print progress information
- `--include` — Comma-separated list of extensions to include (default: `pdf,docx,odt,txt`)
- `-h, --help` — Show help message

## Examples

Extract from all supported file types:

```bash
text-extract ./documents
```

Extract only PDF and DOCX files:

```bash
text-extract ./documents --include pdf,docx
```

Specify output file with verbose output:

```bash
text-extract ./documents --output my_results.json --verbose
```

## Output Format

The script generates a JSON file with the following structure:

```json
[
  {
    "filename": "/path/to/document.pdf",
    "extension": "pdf",
    "text": "Extracted text content from the file..."
  },
  {
    "filename": "/path/to/document.docx",
    "extension": "docx",
    "text": "Extracted text from Word document..."
  }
]
```

## Requirements

- Python 3.7 or higher
- docopt-ng
- PyPDF2 (for PDF files)
- python-docx (for DOCX files)
- odfpy (for ODT files)

## Development

### Setup development environment

```bash
make dev
pre-commit install
```

### Run tests

```bash
make test
```

### Code formatting

```bash
make format
```

### Type checking

```bash
make typecheck
```

### Clean up

```bash
make clean
```
