# Hybrid Training of Neural Networks

**MSc AI & Adaptive Systems — University of Sussex, 2020**

> Using genetic algorithms to find optimal weight initialisation for feedforward neural networks, reducing the epochs needed for gradient descent to converge.

---

## Abstract

Standard gradient-descent algorithms like backpropagation suffer from a well-known problem: random weight initialisation can land the network in a poor region of the error landscape, leading to slow convergence or local minima traps.

This project explores a hybrid approach — using a **microbial genetic algorithm** to perform global search and identify a strong starting set of weights, then handing off to backpropagation for fine-tuning. The result is faster convergence and better robustness on tasks with complex error landscapes.

### Key findings

- The hybrid approach consistently reduced the number of epochs needed to learn all three benchmark tasks
- Benefits were most pronounced on the **two-spirals problem**, where the error landscape has many local minima — exactly where pure gradient descent struggles
- A simple microbial GA (population size 2, probabilistic crossover) was sufficient — no complex evolutionary machinery needed
- Prior work confirms hybrid GA+NN approaches outperform standard methods in fields including **finance and medical diagnosis** — domains where error landscape complexity is high and local minima are costly

---

## Benchmark tasks

| Task | Description | Why it's used |
|------|-------------|---------------|
| XOR | Classic non-linearly separable problem | Baseline — simple landscape |
| NMN encoder | N-to-M-to-N compression network | Mid-complexity, symmetric landscape |
| Two-spirals | Two interleaved spirals, binary classification | Hard — highly non-convex landscape |

---

## Approach

```
Population of weight vectors
        │
        ▼
Microbial Genetic Algorithm (global search)
  → select 2 individuals
  → crossover winner genes into loser
  → mutate loser
  → evaluate fitness (network error)
        │
        ▼
Best weight vector found
        │
        ▼
Backpropagation (local fine-tuning)
  → standard gradient descent from warm start
  → runs to convergence
        │
        ▼
Final trained network
```

---

## Repository contents

- `tasks/` — benchmark task implementations (XOR, NMN encoder, two-spirals)
- `research/` — reference material and papers used during the study
- `report/` — full written paper

---

## Why this project matters (beyond the grade)

This research sits at the intersection of **evolutionary computation and neural network optimisation** — a space that remains highly relevant in modern ML:

- The problem of weight initialisation is still actively studied (see: He initialisation, warm starting in transfer learning)
- Hybrid evolutionary-gradient approaches appear in hyperparameter search, neural architecture search (NAS), and reinforcement learning
- The core insight — *use global search to escape local minima, then use local search to converge fast* — maps directly to how modern AutoML systems work

---

## Context

This project was completed as part of the **MSc in AI and Adaptive Systems** at the University of Sussex (2020). It reflects a foundation in:

- Neural network theory and implementation
- Evolutionary / genetic algorithms
- Experimental design and empirical evaluation
- Scientific writing and literature review

---

*Marcello Chiesa — [LinkedIn](https://linkedin.com/in/marcellochies) · [GitHub](https://github.com/marci6)*
