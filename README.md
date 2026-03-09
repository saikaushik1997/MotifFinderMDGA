# MotifFinderMDGA

A DNA motif discovery tool using a **Genetic Algorithm (GA)** to identify recurring sequence patterns across a set of DNA strings. Implemented in Python as a Jupyter Notebook.

---

## What is Motif Finding?

A **motif** is a short, recurring pattern in DNA sequences that often has biological significance (e.g. transcription factor binding sites). Given a set of DNA sequences where each sequence is known to contain a hidden motif at some position, the goal is to recover the motif and the exact position (start index) where it appears in each sequence.

This is a classic bioinformatics search problem — the search space grows exponentially with sequence length and count, making exhaustive approaches infeasible. Genetic algorithms offer an effective heuristic for navigating this space.

---

## Approach

The motif finder uses a **Genetic Algorithm** with the following pipeline:

1. **Population Initialization** — randomly generate a population of candidate solutions, where each solution is a set of start positions (one per sequence)
2. **Fitness Evaluation** — score each candidate using a fitness function based on the consensus quality of the motifs at the predicted positions
3. **Selection** — select high-fitness candidates to reproduce
4. **Crossover** — combine pairs of candidates to produce offspring
5. **Mutation** — randomly perturb positions to maintain diversity and avoid local optima
6. **Termination** — iterate until convergence or a maximum generation count is reached

---

## Input

- **Artificially generated DNA sequences** (`ArtificialDNAs.ipynb`) — synthetic sequences with a known planted motif at known positions, used for controlled evaluation
- **Real biological sequences** — actual DNA datasets used to test generalizability beyond synthetic data

---

## Output

- **Predicted start positions** — the algorithm's best guess for where the motif begins in each sequence
- **Fitness score** — a quantitative measure of how well the predicted positions agree on a consensus motif; higher fitness indicates stronger motif signal
- **Performance evaluation** — predicted start positions are compared against the ground truth positions (available for synthetic data) to measure accuracy

---

## Repo Structure

```
MotifFinderMDGA/
├── MDGA.ipynb              # Main GA implementation and experiments
├── MDGA-Copy1.ipynb        # Experimental variant / parameter tuning
├── ArtificialDNAs.ipynb    # Synthetic DNA sequence generation and testing
└── README.md
```

---

## Setup

```bash
git clone https://github.com/saikaushik1997/MotifFinderMDGA.git
cd MotifFinderMDGA
pip install numpy jupyter
jupyter notebook
```

Open `MDGA.ipynb` to run the main motif discovery pipeline.

---

## Background

Developed as a course assignment exploring the application of evolutionary computation to bioinformatics search problems. The genetic algorithm approach is compared against the brute-force baseline to demonstrate the practical necessity of heuristic search at scale.

---

## Key Concepts

| Term | Description |
|------|-------------|
| Motif | A short recurring pattern planted in each DNA sequence |
| Start position | Index in a sequence where the motif begins |
| Fitness score | Consensus-based quality measure of a candidate solution |
| Generation | One iteration of selection → crossover → mutation |
| Planted motif problem | Benchmark formulation where ground truth positions are known |
