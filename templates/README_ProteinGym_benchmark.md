# ProteinGym-benchmark

[![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Website](https://img.shields.io/badge/Website-proteingym.org-blue)](https://www.proteingym.org/)

## Overview

ProteinGym-benchmark provides benchmark implementations, model baselines, and evaluation scripts for the ProteinGym platform. This repository contains ready-to-use implementations of state-of-the-art protein fitness prediction models and standardized benchmarking workflows.

## Features

- **Model Baselines**: Implementations of 50+ protein fitness prediction models
- **Benchmarking Workflows**: End-to-end pipelines for model evaluation
- **Scoring Scripts**: Standardized scripts for scoring variants
- **Performance Analysis**: Tools for analyzing and comparing model performance
- **Leaderboard Integration**: Direct integration with ProteinGym leaderboards

## Benchmarks

### Zero-Shot DMS Benchmarks

#### Substitution Benchmark
- **Coverage**: ~2.7M missense variants across 217 DMS assays
- **Models**: 50+ baseline implementations
- **Metrics**: Spearman correlation, NDCG, AUC

#### Indel Benchmark
- **Coverage**: ~300K indel mutants across 74 DMS assays
- **Models**: Specialized indel-compatible baselines
- **Metrics**: Spearman correlation, Kendall's tau

### Supervised Learning Benchmarks

- **Clinical Variants**: Pathogenicity prediction on human variants
- **Cross-validation**: Rigorous evaluation protocols
- **Transfer Learning**: Pre-training and fine-tuning strategies

## Installation

### Prerequisites

```bash
# Create conda environment
conda create -n proteingym python=3.8
conda activate proteingym
```

### Install from Source

```bash
git clone https://github.com/ProteinGym/ProteinGym-benchmark.git
cd ProteinGym-benchmark
pip install -e .
```

### Install Model Dependencies

```bash
# Install dependencies for specific model families
pip install -r requirements/esm.txt          # ESM models
pip install -r requirements/tranception.txt  # Tranception
pip install -r requirements/eve.txt          # EVE
# ... (see requirements/ directory for all models)
```

## Quick Start

### Running a Baseline Model

```bash
# Score variants using ESM-1v
python scripts/scoring_DMS_zero_shot/scoring_ESM1v_substitutions.sh \
    --DMS_data_folder /path/to/DMS_data \
    --output_folder /path/to/output
```

### Evaluating Model Performance

```python
from proteingym_benchmark import PerformanceEvaluator

# Initialize evaluator
evaluator = PerformanceEvaluator(
    benchmark="substitution",
    reference_file="reference_file.csv"
)

# Load model predictions
predictions = evaluator.load_predictions("model_scores/")

# Compute performance metrics
results = evaluator.evaluate(predictions)
print(results.summary())
```

### Custom Model Integration

```python
from proteingym_benchmark import BaselineModel

class MyModel(BaselineModel):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        # Initialize your model
        
    def score_variants(self, sequence, mutations):
        # Implement scoring logic
        scores = self.model.predict(sequence, mutations)
        return scores

# Use your model
model = MyModel()
scores = model.score_variants(sequence, mutations)
```

## Project Structure

```
ProteinGym-benchmark/
├── proteingym_benchmark/          # Main package
│   ├── baselines/                # Baseline model implementations
│   │   ├── esm/                  # ESM family models
│   │   ├── tranception/          # Tranception model
│   │   ├── eve/                  # EVE model
│   │   └── ...                   # Other models
│   ├── evaluation/               # Evaluation scripts
│   ├── data/                     # Data loaders and processors
│   └── utils/                    # Utility functions
├── scripts/                      # Ready-to-use scripts
│   ├── scoring_DMS_zero_shot/   # DMS scoring scripts
│   ├── scoring_clinical/         # Clinical variant scoring
│   └── performance/              # Performance evaluation
├── config/                       # Configuration files
├── tests/                        # Unit tests
├── examples/                     # Example notebooks
└── README.md                     # This file
```

## Available Models

### Sequence-Based Models

| Model | Type | Reference |
|-------|------|-----------|
| ESM-1b | Transformer | [Rives et al., 2021](https://www.pnas.org/doi/10.1073/pnas.2016239118) |
| ESM-1v | Transformer | [Meier et al., 2021](https://proceedings.neurips.cc/paper/2021/hash/f51338d736f95dd42427296047067694-Abstract.html) |
| ESM-2 | Transformer | [Lin et al., 2023](https://www.science.org/doi/10.1126/science.ade2574) |
| ESM-3 | Multimodal | [Hayes et al., 2025](https://www.science.org/doi/10.1126/science.ads0018) |
| Tranception | Autoregressive | [Notin et al., 2022](https://proceedings.mlr.press/v162/notin22a.html) |
| ProtGPT2 | GPT-based | [Ferruz et al., 2022](https://www.nature.com/articles/s41467-022-32007-7) |
| ProGen2 | Causal LM | [Nijkamp et al., 2022](https://arxiv.org/abs/2206.13517) |
| RITA | Transformer | [Hesslow et al., 2022](https://arxiv.org/abs/2205.05789) |

### MSA-Based Models

| Model | Type | Reference |
|-------|------|-----------|
| EVE | VAE | [Frazer et al., 2021](https://www.nature.com/articles/s41586-021-04043-8) |
| MSA Transformer | Transformer | [Rao et al., 2021](http://proceedings.mlr.press/v139/rao21a.html) |
| EVmutation | Statistical | [Hopf et al., 2017](https://www.nature.com/articles/nbt.3769) |
| GEMME | Epistatic | [Laine et al., 2019](https://pubmed.ncbi.nlm.nih.gov/31406981/) |
| PoET | Sequence-of-sequences | [Truong & Bepler, 2023](https://papers.nips.cc/paper_files/paper/2023/hash/f4366126eba252699b280e8f93c0ab2f-Abstract-Conference.html) |

### Structure-Based Models

| Model | Type | Reference |
|-------|------|-----------|
| ESM-IF1 | Inverse folding | [Hsu et al., 2022](https://www.biorxiv.org/content/10.1101/2022.04.10.487779v2) |
| ProteinMPNN | Inverse folding | [Dauparas et al., 2022](https://www.science.org/doi/10.1126/science.add2187) |
| MIF | Masked inverse folding | [Yang et al., 2022](https://doi.org/10.1101/2022.05.25.493516) |

### Multimodal Models

| Model | Type | Reference |
|-------|------|-----------|
| SaProt | Structure-aware | [Su et al., 2024](https://www.biorxiv.org/content/10.1101/2023.10.01.560349v5) |
| ProtSSN | Sequence + Structure | [Tan et al., 2023](https://elifesciences.org/articles/98033) |
| ProSST | Quantized structure | [Li et al., 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/3ed57b293db0aab7cc30c44f45262348-Abstract-Conference.html) |
| MULAN | Multimodal | [Frolova et al., 2024](https://www.biorxiv.org/content/10.1101/2024.05.30.596565v1) |

See [full model list](docs/models.md) for all available baselines.

## Benchmarking Workflow

### 1. Download Data

```bash
# Download DMS benchmark data
python scripts/download_data.py \
    --benchmark substitution \
    --output_dir data/
```

### 2. Run Model

```bash
# Score all variants with your model
python scripts/score_benchmark.py \
    --model esm1v \
    --benchmark_dir data/ \
    --output_dir scores/
```

### 3. Evaluate Performance

```bash
# Compute performance metrics
python scripts/evaluate_performance.py \
    --scores_dir scores/ \
    --benchmark substitution \
    --output metrics.csv
```

### 4. Submit to Leaderboard

```bash
# Validate and submit results
python scripts/submit_to_leaderboard.py \
    --model_name "MyModel" \
    --scores_dir scores/ \
    --contact your.email@example.com
```

## Adding a New Model

### Step 1: Implement Scoring Function

Create a new file `proteingym_benchmark/baselines/mymodel/compute_fitness.py`:

```python
from proteingym_benchmark.baselines.base import BaseScorer

class MyModelScorer(BaseScorer):
    def __init__(self, model_path, **kwargs):
        super().__init__(**kwargs)
        self.model = self.load_model(model_path)
    
    def score_variant(self, sequence, mutation):
        """Score a single variant"""
        return self.model.predict(sequence, mutation)
    
    def score_batch(self, sequences, mutations):
        """Score a batch of variants"""
        return [self.score_variant(s, m) 
                for s, m in zip(sequences, mutations)]
```

### Step 2: Create Scoring Script

Create `scripts/scoring_DMS_zero_shot/scoring_MyModel.sh`:

```bash
#!/bin/bash

python proteingym_benchmark/baselines/mymodel/compute_fitness.py \
    --model_path /path/to/model \
    --DMS_data_folder $DMS_DATA \
    --output_folder $OUTPUT_DIR \
    --batch_size 32
```

### Step 3: Submit Pull Request

See [CONTRIBUTING.md](CONTRIBUTING.md) for submission guidelines.

## Performance Metrics

### Ranking Metrics
- **Spearman's ρ**: Rank correlation between predictions and experimental scores
- **NDCG**: Normalized discounted cumulative gain
- **Top-k Recall**: Fraction of top-k variants correctly identified

### Correlation Metrics
- **Pearson's r**: Linear correlation
- **Kendall's τ**: Ordinal association

### Classification Metrics
- **AUC-ROC**: Area under receiver operating characteristic curve
- **AUC-PR**: Area under precision-recall curve
- **MCC**: Matthews correlation coefficient

## Configuration

Model and benchmark configurations are managed through YAML files:

```yaml
# config/models/mymodel.yaml
model:
  name: "MyModel"
  type: "sequence"
  checkpoint: "path/to/checkpoint"
  
scoring:
  batch_size: 32
  device: "cuda"
  
evaluation:
  benchmarks: ["substitution", "indel"]
  metrics: ["spearman", "ndcg"]
```

## Documentation

- [Installation Guide](docs/installation.md)
- [Model Documentation](docs/models.md)
- [Benchmarking Guide](docs/benchmarking.md)
- [API Reference](docs/api_reference.md)
- [Contributing Guide](CONTRIBUTING.md)
- [FAQ](docs/faq.md)

## Testing

```bash
# Run all tests
pytest

# Test specific model
pytest tests/test_baselines/test_esm.py

# Test with coverage
pytest --cov=proteingym_benchmark
```

## Contributing

We welcome new model implementations and improvements! See [CONTRIBUTING.md](CONTRIBUTING.md) for:

- Model submission requirements
- Code standards
- Testing requirements
- Documentation guidelines

### Requirements for New Models

1. **Open Source**: Model must be publicly available
2. **Complete Coverage**: Must score all variants in benchmark
3. **Reproducible**: Clear instructions for reproducing scores
4. **Documented**: API documentation and usage examples

## Citation

If you use ProteinGym-benchmark in your research, please cite:

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

## Related Projects

- **[OATML-Markslab/ProteinGym](https://github.com/OATML-Markslab/ProteinGym)**: Main benchmark repository
- **[ProteinGym-base](https://github.com/ProteinGym/ProteinGym-base)**: Core utilities and infrastructure
- **[ProteinGym Organization](https://github.com/ProteinGym)**: All ProteinGym projects

## Acknowledgments

We thank all model developers who have contributed baselines to ProteinGym, and the experimental teams who generated the DMS data underlying these benchmarks. Special thanks to the community for their continuous feedback and contributions.

## Contact

- **Issues**: [GitHub Issues](https://github.com/ProteinGym/ProteinGym-benchmark/issues)
- **Website**: [proteingym.org](https://www.proteingym.org/)
- **Main Repository**: [OATML-Markslab/ProteinGym](https://github.com/OATML-Markslab/ProteinGym)

## Support

For questions about:
- **Usage**: See [FAQ](docs/faq.md) or open an issue
- **New models**: See [CONTRIBUTING.md](CONTRIBUTING.md)
- **Data access**: Visit [proteingym.org](https://www.proteingym.org/)
- **Performance metrics**: See [documentation](docs/metrics.md)

---

*Part of the ProteinGym ecosystem for protein fitness prediction and design.*
