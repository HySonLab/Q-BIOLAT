# Latent QUBO Protein Design — Extended Prototype

This package is a research-oriented prototype for latent-space optimization with:

- QUBO surrogate model (linear + pairwise binary interactions)
- Simulated annealing
- Greedy hill climbing
- Random search
- Genetic algorithm
- Lightweight latent Bayesian-style search
- NumPy MLP surrogate baseline

## Project structure

```text
latent_qubo_protein_design_extended/
├── src/
│   ├── models/
│   │   ├── qubo_model.py
│   │   └── mlp_surrogate.py
│   ├── optimization/
│   │   ├── simulated_annealing.py
│   │   ├── greedy_hill_climb.py
│   │   ├── random_search.py
│   │   ├── genetic_algorithm.py
│   │   └── latent_bo.py
│   ├── data/
│   │   ├── dataset.py
│   │   └── synthetic.py
│   └── utils/
│       ├── metrics.py
│       └── retrieval.py
├── examples/
│   ├── make_synthetic_dataset.py
│   └── test_read_dataset.py
├── experiments/
│   ├── train_surrogate.py
│   ├── optimize_latent.py
│   └── run_full_benchmark.py
├── configs/
│   └── default_synthetic.json
└── README.md
```

## Quick start

### 1. Generate a synthetic dataset

```bash
PYTHONPATH=. python examples/make_synthetic_dataset.py
```

Optional sparse-interaction version:

```bash
PYTHONPATH=. python examples/make_synthetic_dataset.py --sparse-interactions --interaction-keep-prob 0.15
```

### 2. Check the dataset

```bash
PYTHONPATH=. python examples/test_read_dataset.py
```

### 3. Train the QUBO surrogate

```bash
PYTHONPATH=. python experiments/train_surrogate.py --model qubo
```

### 4. Train the MLP baseline

```bash
PYTHONPATH=. python experiments/train_surrogate.py --model mlp
```

### 5. Run latent optimization baselines

```bash
PYTHONPATH=. python experiments/optimize_latent.py
```

### 6. Run the full benchmark

```bash
PYTHONPATH=. python experiments/run_full_benchmark.py
```

Outputs are written to `artifacts/`.

