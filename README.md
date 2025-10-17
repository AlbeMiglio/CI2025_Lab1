# CI2025_lab1: Local Search Solvers for the Knapsack Problem

This project provides a Python framework for solving the **Multiple Multidimensional Knapsack Problem (MMKP)** using various local search metaheuristics. It is designed to be a clean, modular, and extensible implementation for comparing different optimization strategies like Hill Climbing and Simulated Annealing.

## 1. The Problem: MMKP

This solver is built to tackle the **Multiple Multidimensional Knapsack Problem (MMKP)**.

* `N` **items**, each with a `value`.
* `K` **knapsacks** (containers).
* `D` **dimensions** (e.g., `weight` and `volume`).

**Goal:** Assign each item to *at most one* knapsack to **maximize the total value** of all assigned items, without exceeding the capacity of any knapsack in *any* dimension.

## 2. Algorithms & Design

The framework is built using an object-oriented design that separates the problem logic from the search strategy.

* `BaseSolver`: An abstract class that defines the MMKP problem. It handles solution representation, constraint checking (`_is_feasible`), fitness calculation (`_fitness`), and neighbor generation (`_tweak`).
* `HillClimber(BaseSolver)`: Implements a Stochastic Hill Climber, which samples `k` neighbors at each step and moves to the best one if it offers an improvement or a sideways move.
* `SimulatedAnnealing(BaseSolver)`: Implements Simulated Annealing with a flexible, function-based temperature scheduling system.

## 3. How to Define Your Problem

Structure of problem configuration.

```python
import numpy as np

# --- 1. Define Problem Data ---
rng = np.random.default_rng(seed=42)
NUM_ITEMS = 50
NUM_KNAPSACKS = 5
NUM_DIMENSIONS = 2 # (e.g., weight, volume)

VALUES = rng.integers(10, 100, size=NUM_ITEMS)
WEIGHTS = rng.integers(5, 25, size=(NUM_ITEMS, NUM_DIMENSIONS))
CONSTRAINTS = rng.integers(
    150, 200, size=(NUM_KNAPSACKS, NUM_DIMENSIONS)
)
```
