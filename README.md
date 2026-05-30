# PR_SS26_N_QUEENS

Benchmark of four algorithms for the N-Queens problem: exhaustive DFS / backtracking, hill climbing with min-conflicts, simulated annealing, and a memetic genetic algorithm. Sweeps `N ∈ {10, 30, 50, 100, 200, 500}` and reports time, peak memory, and final conflict count.

## Getting the notebook

The notebook is committed as `nqueens_all_algorithms.ipynb.txt` (GitHub's notebook renderer was failing on the `.ipynb` version). Rename it back before opening:

```bash
mv nqueens_all_algorithms.ipynb.txt nqueens_all_algorithms.ipynb
```

Or on Windows (PowerShell):

```powershell
Rename-Item nqueens_all_algorithms.ipynb.txt nqueens_all_algorithms.ipynb
```

## Running

```bash
pip install jupyter matplotlib pandas
jupyter notebook nqueens_all_algorithms.ipynb
```

Then run all cells. Outputs written to the repo root:

- `results.csv` — per-(algorithm, N) wall time, peak memory, final conflicts
- `time_comparison.png`, `memory_comparison.png`, `conflicts_comparison.png`

## Algorithms

```text
1. DFS Backtracking      — exact; randomized restart with geometric backtrack budget
2. Hill Climbing         — min-conflicts move + random restarts on plateau
3. Simulated Annealing   — permutation rep; O(1) swap delta; warm-start at N ≥ 100
4. Genetic Algorithm     — memetic: tournament + OX + conflict-aware mutation + repair
```

All conflict calculations are O(N) via column and diagonal count arrays. Board representation: `board[row] = column`. Seed is fixed (`SEED = 42`) for reproducibility.
