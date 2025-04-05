# pyextract

> 📂 A Python utility for recursively extracting files matching a regex pattern from archives (.zip, .tar.gz, .gz)

[![Python Support](https://img.shields.io/badge/python-3.12%2B-blue)](https://www.python.org/downloads/)
[![License](https://img.shields.io/github/license/fxyzbtc/pyextract.svg)](LICENSE) <!-- Assuming MIT License like the example -->

## ✨ Features

- 🔍 Extract files based on regular expression patterns
- 📦 Supports `.zip`, `.tar.gz`, `.tgz`, and `.gz` archives
- 🔄 Handles nested archives recursively (e.g., zip inside tar.gz)
- 🎯 Simple and clear CLI interface using Typer
- 🐍 Built with modern Python (3.12+)

## 📦 Installation

### Using pip
```bash
pip install pyextract
```

### Using uv (Recommended)
[uv](https://github.com/astral-sh/uv) is a blazing-fast Python package installer:

```bash
# Install uv (if you haven't already)
pip install uv

# Install pyextract using uv
uv pip install pyextract
```

## 🚀 Quick Start

### Command Line Usage
```bash
# Basic usage: Extract all .txt files from my_archive.zip to the 'output' directory
pyextract my_archive.zip "\.txt$" ./output/

# Extract specific log file from a tar.gz archive
pyextract logs.tar.gz "app\.log" ./extracted_logs/

# Extract from a gzipped file (pattern matches the archive name for .gz)
pyextract config.json.gz "config\.json\.gz" ./config_files/
```

### Python Module Usage
```bash
python -m pyextract [OPTIONS] INPUT_FILE TARGET_PATTERN OUTPUT_PATH
```

## 🎛️ Command Line Arguments

| Argument         | Description                                                               | Required |
|------------------|---------------------------------------------------------------------------|----------|
| `INPUT_FILE`     | Path to the input archive file (.zip, .tar.gz, .tgz, .gz).                | Yes      |
| `TARGET_PATTERN` | Regular expression pattern to match filenames within the archive.         | Yes      |
| `OUTPUT_PATH`    | Directory to extract matching files into (will be created if needed).     | Yes      |

## 🛠️ Development

### Setup Development Environment

1.  Clone the repository
    ```bash
    git clone https://github.com/fxyzbtc/pyextract.git
    cd pyextract
    ```

2.  Create and activate virtual environment (using uv)
    ```bash
    uv venv .venv
    # On Windows
    .venv\Scripts\activate
    # On macOS/Linux
    source .venv/bin/activate
    ```

3.  Install dependencies (including development tools)
    ```bash
    uv pip install -e ".[dev]"
    ```

### Running Tests
```bash
# Run all tests
uv run pytest

# Run tests with coverage report
uv run pytest --cov=pyextract tests/
```

### Code Style
This project uses `black` for formatting and `isort` for import sorting.

```bash
# Format code
uv run black .
uv run isort .

# Linting (if Ruff or similar is added later)
# uv run ruff check .

# Type checking (if MyPy is added later)
# uv run mypy .
```

## 📝 Example

**Command:**
```bash
pyextract my_documents.zip "\.docx?$" ./extracted_docs/
```

**Input:** `my_documents.zip` containing:
```
- report.docx
- notes.txt
- archive/
  - presentation.pptx
  - backup.zip
    - important.doc
```

**Output:** Files extracted to `./extracted_docs/`:
```
extracted_docs/
  - report.docx
  - important.doc
```
*(Note: `important.doc` is extracted from the nested `backup.zip`)*

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1.  Fork the repository.
2.  Create your feature branch (`git checkout -b feature/your-feature`).
3.  Commit your changes (`git commit -m 'Add some feature'`).
4.  Push to the branch (`git push origin feature/your-feature`).
5.  Open a Pull Request.

## 📄 License

This project is licensed under the MIT License. (Please add a LICENSE file if one doesn't exist).

## 🙏 Acknowledgments

- [Typer](https://github.com/tiangolo/typer) for the easy-to-use CLI interface.
- Python's built-in `zipfile`, `tarfile`, and `gzip` modules for archive handling.

## 📞 Support

- 📫 Report issues on [GitHub Issues](https://github.com/fxyzbtc/pyextract/issues)
- 💬 Ask questions or discuss ideas in the project's discussion forum (if available).

---
Made with ❤️ using Python
