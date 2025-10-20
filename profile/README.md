## Overview

ProteinGym has become a widely used resource for comparing the ability of models to predict the effects of protein mutations. ProteinGym Base is an effort to bring more structure to the datasets so that they become easier to work with and to distribute; and to the models in the benchmark so that they become easier to install and run. Less undocumented csv's and more formal schemas. Fewer scripts with hardcoded paths and more Dockerfiles and precise requirements.

## Mission

To advance protein engineering and computational biology by providing:
- Structured, standardized datasets for protein variant effect prediction
- Reproducible benchmarking frameworks for model evaluation
- Open-source tools that facilitate research and development in protein science

## Core Repositories

### 🧬 [proteingym-base](https://github.com/ProteinGym/proteingym-base) 
**Infrastructure for protein variant effect prediction datasets**

- **Purpose**: Provides structured dataset classes and tools to facilitate benchmarking
- **Key Features**:
  - Formal schemas for protein data (sequences, structures, MSAs, assays)
  - Dataset manifest system with TOML configuration
  - Archive/persistence capabilities for easy data sharing
  - Support for multiple data formats (FASTA, PDB, CIF, A3M, CSV)
  - BioPython integration for biological data handling
- **Target Users**: Researchers working with protein datasets, ML practitioners
- **Tech Stack**: Python 3.12+, Pydantic, BioPython, Polars, TOML

### 🏆 [proteingym-benchmark](https://github.com/ProteinGym/proteingym-benchmark)
**Standardized benchmarking framework for protein prediction models**

- **Purpose**: Enables reproducible evaluation of protein variant effect prediction models
- **Key Features**:
  - Two benchmark games: supervised learning and zero-shot prediction
  - Model repository with standardized model cards
  - DVC-based pipeline orchestration
  - Local (HPC) and AWS cloud execution environments
  - Automated metric calculation and comparison
  - Docker containerization for reproducibility
- **Target Users**: Model developers, researchers comparing prediction methods
- **Tech Stack**: Python, DVC, Docker, AWS SageMaker, Polars

## Architecture & Integration

```
┌─────────────────┐    uses datasets    ┌──────────────────┐
│   pg-benchmark  │ ◄─────────────────── │    pg-base       │
│                 │                      │                  │
│ • Model repos   │                      │ • Dataset class  │
│ • Benchmarks    │                      │ • Manifests      │
│ • Metrics       │                      │ • Archives       │
│ • Pipelines     │                      │ • Schemas        │
└─────────────────┘                      └──────────────────┘
```

## Community & Collaboration

### Research Focus Areas
- Protein variant effect prediction
- Machine learning for protein engineering
- Computational biology benchmarking
- Reproducible research practices

### Contribution Guidelines
- Both repositories follow standardized development practices
- Pre-commit hooks for code quality
- Comprehensive testing with pytest
- Documentation-driven development
- Architecture Decision Records (ADRs) for design decisions

### Standards & Best Practices
- **Code Quality**: Ruff linting, type hints, comprehensive testing
- **Documentation**: Jupyter notebooks, markdown guides, API documentation
- **Reproducibility**: Docker containers, dependency locking, DVC pipelines
- **Data Management**: Structured schemas, version control, archival formats

## Getting Started

### For Dataset Users
1. Install `proteingym-base`: `pip install git+https://github.com/ProteinGym/proteingym-base.git`
2. Follow the tutorials in `notebooks/` for your first introduction
3. Load datasets using manifest files
4. Access structured protein data (sequences, structures, MSAs, assays)

### For Model Developers
1. Use `proteingym-base` to work with standardized datasets
2. Follow the tutorials in `notebooks/` for your first introduction
3. Implement models following `proteingym-benchmark` specifications
4. Submit models for benchmarking evaluation

### For Researchers
1. Access curated protein datasets through `proteingym-base`
2. Compare model performance using `proteingym-benchmark` results
3. Contribute new datasets or models to the ecosystem

## Technical Requirements

- **Python**: 3.12+
- **Cloud**: AWS (optional, for large-scale benchmarking)
- **Containerization**: Docker
- **Data Versioning**: DVC
- **Package Management**: UV/pip

## License & Usage

Both repositories are designed for research and development in computational biology, with appropriate licensing for academic and commercial use.

---

*This organization represents a collaborative effort to standardize and advance protein variant effect prediction research through open-source tools and datasets.*
