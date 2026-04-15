# Temporal Graph Analytics for Sensitivity Analysis

This repository contains the final report and companion notebooks for a project on temporal graph learning and benchmark interpretability. The project studies why temporal link prediction performance varies so strongly across datasets, and whether measurable temporal graph properties can help explain those differences.

Rather than treating benchmark results as isolated leaderboard numbers, the project takes a sensitivity-analysis perspective. It asks how dataset properties such as recurrence, novelty, edge repetition, activity, degree volatility, and node lifetime relate to downstream model behavior.

## Project summary

The study focuses on single-relational temporal link prediction in the Temporal Graph Benchmark (TGB). The retained comparison is intentionally narrow and computationally feasible. It centers on two training-free heuristic baselines, EdgeBank and BASE3, and one retained learned model, GraphMixer. Limited TGN and DyGFormer runs are kept only as auxiliary reference evidence where available.

The central goal is not to declare a universally best temporal graph model, but to understand when simple memorization-based heuristics are already sufficient and when a learned model provides a meaningful advantage.

## Main question

How do temporal graph properties shape the relative performance of history-based heuristics versus learned temporal graph models across benchmark datasets?

## Retained datasets

The main predictive study is built around the following TGB datasets:

- `tgbl-wiki`
- `tgbl-review`
- `tgbl-enron`
- `tgbl-uci`
- `tgbl-lastfm`

In addition, `tgbl-coin` is included as a feasibility-focused case to document scale-related computational limitations rather than as part of the main predictive comparison.

## Models

The main retained comparison uses:

- **EdgeBank**, a pure history-based heuristic baseline
- **BASE3**, a stronger training-free heuristic combining recurrence, popularity, and temporal co-occurrence
- **GraphMixer**, the retained learned model and principal neural contrast

Auxiliary runs with **TGN** and **DyGFormer** are discussed in the report where available, but they are not treated as part of the main uniform comparison across all datasets.

## What the project finds

A main takeaway of the project is that benchmark outcomes become more interpretable when model performance is analyzed together with explicit temporal graph characterization.

At a high level, the results suggest that:

- datasets with stronger historical repetition tend to favor memorization-based heuristics
- highly novel or structurally unstable datasets create more room for a learned model to help
- GraphMixer does not dominate uniformly, but follows a different operating profile from the heuristics
- computational feasibility and scalability should be treated as part of model suitability, not as a separate implementation detail
