# Folder Synchronization Tool

A simple, yet efficient tool that maintains a replica of a source folder by performing one-way synchronization at specified intervals.

## Features

- One-way sync from source to replica folder
- Configurable synchronization interval
- Detailed logging to both console and file
- File integrity verification using checksums
- Handles all file operations: create, modify and delete.
- Cross-platform compatibility.

## Requirements

- Python 3.8 or higher
- No external dependencies for core functionality

## Installation

```bash
git clone https://github.com/edszen/folder_sync.git
cd folder-sync
pip install -r requirements.txt  # If any dependencies are added
```

## Usage

```bash
python main.py --source /path/to/source --replica /path/to/replica --interval 60 --log /path/to/logfile.log
```

## Parameters
* --source: Path to the source folder
* --replica: Path to the replica folder
* --interval: Synchronization interval in seconds
* --log: Path to the log file

## Design

The application follows a modular design with separation of concerns:

* sync_manager.py: Deals with the synchronization process
* file_operations.py: Handles file system operations
* comparison.py: Compares files and folders
* logger.py: Sets up logging to console and file

## Testing
Run tests with:
pytest

Run tests with coverage report:
pytest --cov=src


## License
MIT

## Author
Edson Da Costa

## Additional features to possibly implement

1. **Checksum Verification**: Use MD5 to verify file integrity, not just dates/sizes
2. **Progress Indicator**: Show progress during large synchronizations
3. **Error Recovery**: Handle network interruptions or prmission issues gracefully.
4. **Dry Run Mode**: Show what would be synced without making changes
5. **Exclusion Patterns**: Allow specifying files/patterns to exclude
6. **Detailed Statistics**: Show summary of operations after each sync
7. **Performance Optimization**: Use threading for large file operations
8. **Unit Test Coverage**: Comprehensive test suite with high coverage
9. **Documentation**: Code comments that follow industry standards

## Requirements.txt

Minimal for now, as no third-party library that implement folder synchronization should be used.

Although allowed and recommended to use external libraries implementing
other well-known algorithms.

## No external dependencies for core funcionality

## For testing
pytest==7.4.0
pytest-cov==4.1.0

## setup.py (for packaging)

```python
from setuptools import setup, find_packages

setup(
    name="folder-sync",
    version="0.1.0"
    packages=find_packages(),
    install_requires=[],
    entry_points={
        "console_scripts": [
            "folder-sync=main:main",
        ],
    },
    python_requires=">=3.12",
)
