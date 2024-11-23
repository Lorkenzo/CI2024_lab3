# COMPUTATIONAL INTELLIGENCE LAB3

## Layer Greedy Solver

The solution provided in [n-puzzle_layer](./n-puzzle_layer.ipynb) is based on a layer-based solver for the N-PUZZLE problem. This algorithm can find a non-optimal solution very quickly (in just a few seconds), even for puzzles with high dimensionality. Unlike the solution in [n-puzzle_A-star](./n-puzzle_A-star.ipynb), which uses an A-Star approach enhanced with ChatGPT-4, the greedy algorithm offers high scalability, solving puzzles with \( N = 50 \) in just 32 seconds. In contrast, the A-Star algorithm can solve puzzles optimally within a reasonable time frame only for dimensions of 3 or 4. For the given initialization, A-Star took negligible time for \( N = 3 \), but for \( N = 4 \), it required more than two hours. Moreover, for A-Star, the time to find a solution for \( N = 4 \) heavily depends on the initial configuration, ranging from a few minutes to several hours.

The layer solver operates in two main steps:  
1. **N-2 Layer Solver:** Solves one row at a time up to the \( N-2 \) layer.  
2. **Last-2 Layer Solver:** Solves the last two rows together, handling one column at a time until the final solution is reached.


The number of randomized steps increase linearly with the dimensionality in order to provide a good initial randomization

## Results

The following are the compared results for the two algorithms, for A-Star the evaluation stops at N = 4 for the reasons exlpaned before.

| Hyperparameters      |                | Number of steps |          |
| -------------------- | -------------- | --------------- | -------- |
| __Randomized Steps__ | __Puzzle Dim__ | _Layer Solver_  | _A-Star_ |
| 100_000              | 3              | 31              | 23       |
| 100_000              | 4              | 168             | 55       |
| 100_000              | 5              | 235             | -        |
| 200_000              | 7              | 947             | -        |
| 300_000              | 10             | 3_316           | -        |
| 500_000              | 15             | 10_503          | -        |
| 600_000              | 20             | 25_754          | -        |
| 1_600_000            | 50             | 225_838         | -        |