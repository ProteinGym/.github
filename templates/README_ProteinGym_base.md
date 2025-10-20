# ProteinGym-base

[![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

## Overview

ProteinGym-base provides the foundational infrastructure and core utilities for the ProteinGym benchmarking platform. This repository contains the essential tools, data processing pipelines, and evaluation frameworks used across all ProteinGym benchmarks.

## Features

- **Data Processing Pipeline**: Tools for standardizing and processing protein variant data
- **Evaluation Framework**: Core metrics and evaluation utilities for model assessment
- **Utility Functions**: Common functions used across ProteinGym projects
- **File Format Specifications**: Standards for data interchange and storage
- **Baseline Implementations**: Reference implementations of core algorithms

## Installation

### From PyPI (Recommended)

```bash
pip install proteingym-base
```

### From Source

```bash
git clone https://github.com/ProteinGym/ProteinGym-base.git
cd ProteinGym-base
pip install -e .
```

## Quick Start

### Basic Usage

```python
from proteingym_base import DataLoader, Evaluator

# Load benchmark data
loader = DataLoader()
data = loader.load_benchmark("substitution")

# Evaluate predictions
evaluator = Evaluator()
metrics = evaluator.compute_metrics(predictions, ground_truth)
print(f"Spearman correlation: {metrics['spearman']:.3f}")
```

### Processing Custom Data

```python
from proteingym_base import DataProcessor

# Initialize processor
processor = DataProcessor()

# Process your variant data
processed_data = processor.process_variants(
    sequences=sequences,
    mutations=mutations,
    format="standard"
)
```

## Project Structure

```
ProteinGym-base/
├── proteingym_base/          # Main package
│   ├── data/                 # Data processing modules
│   ├── evaluation/           # Evaluation metrics and utilities
│   ├── io/                   # Input/output handlers
│   ├── utils/                # Utility functions
│   └── constants.py          # Constants and configurations
├── tests/                    # Unit tests
├── examples/                 # Example scripts and notebooks
├── docs/                     # Documentation
├── setup.py                  # Package setup
└── README.md                 # This file
```

## Core Modules

### Data Processing (`proteingym_base.data`)

- `DataLoader`: Load and parse ProteinGym benchmark files
- `DataProcessor`: Standardize and transform variant data
- `SequenceHandler`: Handle protein sequences and mutations

### Evaluation (`proteingym_base.evaluation`)

- `Evaluator`: Compute performance metrics
- `MetricsCalculator`: Calculate correlation and ranking metrics
- `StatisticalTests`: Statistical significance testing

### I/O Operations (`proteingym_base.io`)

- `FileReader`: Read various file formats (CSV, JSON, etc.)
- `FileWriter`: Write results in standard formats
- `FormatValidator`: Validate data format compliance

## Data Format Standards

### Mutation Format

Mutations should be specified in the following format:
- **Substitutions**: `{WT}{Position}{MUT}` (e.g., `A123V`)
- **Multiple substitutions**: Separated by `:` (e.g., `A123V:D456E`)
- **Insertions**: `ins{Position}_{Sequence}` (e.g., `ins123_ABC`)
- **Deletions**: `del{Start}_{End}` (e.g., `del123_125`)

### Input File Format

```csv
mutant,mutated_sequence,DMS_score
A123V,MVKL...VASS,1.234
D456E,MVKL...EASS,0.567
```

## Documentation

Full documentation is available at [docs link to be added].

### Key Topics

- [Installation Guide](docs/installation.md)
- [Data Format Specifications](docs/data_formats.md)
- [Evaluation Metrics](docs/metrics.md)
- [API Reference](docs/api_reference.md)
- [Contributing Guide](CONTRIBUTING.md)

## Testing

Run the test suite:

```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=proteingym_base

# Run specific test module
pytest tests/test_data.py
```

## Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details on:

- Code style and standards
- Testing requirements
- Pull request process
- Issue reporting

### Development Setup

```bash
# Clone the repository
git clone https://github.com/ProteinGym/ProteinGym-base.git
cd ProteinGym-base

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install development dependencies
pip install -e ".[dev]"

# Run tests
pytest
```

## Dependencies

Core dependencies:
- Python >= 3.8
- NumPy >= 1.20.0
- Pandas >= 1.3.0
- SciPy >= 1.7.0

See `requirements.txt` for a complete list.

## Version History

See [CHANGELOG.md](CHANGELOG.md) for detailed version history.

### Current Version: 1.0.0
- Initial release with core functionality
- Data processing pipeline
- Evaluation framework
- Utility functions

## Related Projects

- **[OATML-Markslab/ProteinGym](https://github.com/OATML-Markslab/ProteinGym)**: Main benchmark repository
- **[ProteinGym-benchmark](https://github.com/ProteinGym/ProteinGym-benchmark)**: Benchmark implementations
- **[ProteinGym Organization](https://github.com/ProteinGym)**: All ProteinGym projects

## Citation

If you use ProteinGym-base in your research, please cite the ProteinGym paper:

```bibtex
@inproceedings{NEURIPS2023_cac723e5,
 author = {Notin, Pascal and Kollasch, Aaron and Ritter, Daniel and van Niekerk, Lood and Paul, Steffanie and Spinner, Han and Rollins, Nathan and Shaw, Ada and Orenbuch, Rose and Weitzman, Ruben and Frazer, Jonathan and Dias, Mafalda and Franceschi, Dinko and Gal, Yarin and Marks, Debora},
 booktitle = {Advances in Neural Information Processing Systems},
 pages = {64331--64379},
 publisher = {Curran Associates, Inc.},
 title = {ProteinGym: Large-Scale Benchmarks for Protein Fitness Prediction and Design},
 volume = {36},
 year = {2023}
}
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

- **Issues**: [GitHub Issues](https://github.com/ProteinGym/ProteinGym-base/issues)
- **Website**: [proteingym.org](https://www.proteingym.org/)
- **Main Repository**: [OATML-Markslab/ProteinGym](https://github.com/OATML-Markslab/ProteinGym)

## Acknowledgments

ProteinGym-base is developed and maintained by the ProteinGym team. We thank all contributors and the broader protein engineering community for their support and feedback.

---

*Part of the ProteinGym ecosystem for protein fitness prediction and design.*
