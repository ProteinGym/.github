# ProteinGym

[![Website](https://img.shields.io/badge/Website-proteingym.org-blue)](https://www.proteingym.org/)
[![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 🧬 About ProteinGym

ProteinGym is a comprehensive benchmarking platform for protein fitness prediction and design. Our mission is to enable rigorous and fair comparisons of computational methods that predict the effects of mutations on protein function.

## 📊 What We Provide

- **Large-Scale Benchmarks**: Extensive Deep Mutational Scanning (DMS) assays covering millions of protein variants
- **Standardized Evaluation**: Fair comparison frameworks for mutation effect predictors
- **Open Resources**: Publicly available datasets, scores, and evaluation tools
- **Community Hub**: A platform for researchers to share and compare their models

## 🔬 Key Features

### Substitution Benchmark
- ~2.7M missense variants across 217 DMS assays
- 2,525 clinical proteins with variant annotations
- Comprehensive coverage of protein families and functions

### Indel Benchmark
- ~300K indel mutants across 74 DMS assays
- 1,555 clinical proteins
- Support for insertion and deletion mutations

## 🚀 Our Repositories

### Main Resources
- **[OATML-Markslab/ProteinGym](https://github.com/OATML-Markslab/ProteinGym)**: Official benchmark repository with code, baselines, and documentation
- **dvc-dataset-registry**: Data version control for ProteinGym datasets

## 📖 Get Started

Visit our [official repository](https://github.com/OATML-Markslab/ProteinGym) to:
- Access benchmark datasets
- Download model predictions
- Explore baseline implementations
- Learn how to evaluate your model
- Contribute new baselines

## 🤝 Contributing

We welcome contributions from the community! Whether you're:
- Developing new prediction models
- Curating experimental data
- Improving evaluation metrics
- Enhancing documentation

Please see our [contribution guidelines](https://github.com/OATML-Markslab/ProteinGym#how-to-contribute) to get involved.

## 📚 Citation

If you use ProteinGym in your research, please cite:

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

## 🔗 Links

- **Website**: [proteingym.org](https://www.proteingym.org/)
- **Paper**: [NeurIPS 2023](https://papers.nips.cc/paper_files/paper/2023/hash/cac723e5ff29f65e3fcbb0739ae91bee-Abstract-Datasets_and_Benchmarks.html)
- **Datasets**: [HuggingFace](https://huggingface.co/datasets/OATML-Markslab/ProteinGym_v1)
- **Package**: [PyPI](https://pypi.org/project/proteingym/)
- **Archive**: [Zenodo](https://zenodo.org/records/15293562)

## 📧 Contact

For questions, suggestions, or collaborations, please open an issue in the relevant repository or reach out through our website.

---

*Building better tools for protein engineering through open science and collaborative benchmarking.*
