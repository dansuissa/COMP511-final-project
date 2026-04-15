# Temporal Graph Analytics for Sensitivity Analysis

This repository contains the final report for a project on temporal graph learning and benchmark interpretability. The project studies why temporal link prediction performance varies so much across datasets, and whether measurable temporal graph properties can help explain those differences.

The analysis focuses on single-relational temporal link prediction in the Temporal Graph Benchmark (TGB). Rather than running a broad model leaderboard, the project uses a smaller and more computationally feasible comparison between two training-free heuristic baselines, EdgeBank and BASE3, and one retained learned model, GraphMixer. The goal is to understand when simple memorization-based methods are sufficient and when a learned temporal model is more useful.

## Project overview

Temporal graph models often behave very differently from one benchmark to another. A model that performs well on one dataset can perform much worse on another, even when the task looks similar. This project approaches that problem from a sensitivity-analysis perspective: instead of asking only which model wins, it asks which temporal graph characteristics are associated with that outcome.

To do this, the project characterizes each dataset using descriptive temporal graph metrics and relates them to downstream predictive performance measured by test Mean Reciprocal Rank (MRR).

## Main question

How do temporal graph properties shape the relative performance of history-based heuristics versus learned temporal graph models across benchmark datasets?

## Datasets

The main predictive study is built on a selected subset of TGB temporal link prediction datasets:

- `tgbl-wiki`
- `tgbl-review`
- `tgbl-enron`
- `tgbl-uci`
- `tgbl-lastfm`

The dataset `tgbl-coin` is included mainly as a feasibility case to document large-scale computational limitations rather than as a full member of the main predictive comparison.

## Models

The retained comparison focuses on three main methods:

- **EdgeBank**: a simple history-based baseline that predicts future links from previously observed edges
- **BASE3**: a stronger training-free heuristic that combines recurrence, popularity, and temporal co-occurrence
- **GraphMixer**: the retained learned model, used as a tractable neural contrast to memorization-based methods

Limited runs with **TGN** and **DyGFormer** are also kept in the report as auxiliary reference evidence where available.

## Dataset characterization

Each dataset is described using temporal graph statistics designed to capture different structural and temporal regimes, including:

- surprise
- recurrence
- novelty
- edge repeat rate
- mean active node ratio
- mean active edge density
- degree volatility
- node lifetime statistics

These metrics are then compared with model performance using exploratory correlation analysis.

## Main findings

The main result of the project is that benchmark outcomes become much easier to interpret when model performance is studied together with explicit temporal graph structure.

At a high level, the report finds that:

- datasets with stronger historical repetition tend to favor memorization-based heuristics
- highly novel or structurally unstable datasets create more room for a learned model to help
- GraphMixer does not dominate uniformly, but shows a different operating profile from the heuristics
- computational feasibility matters as much as raw predictive accuracy, especially on large temporal graphs

A central takeaway is that model choice in temporal graph learning should depend not only on leaderboard results, but also on the temporal regime of the target dataset.
