# Modified Sudoku Solver

This project implements a Sudoku solver that combines **human-style logical strategies** with **recursive backtracking using MRV (Minimum Remaining Values)**. The solver is designed to be **modular, effective, and general**, capable of solving any valid 9×9 Sudoku puzzle.

---

## Workflow & Phases

The solver is divided into **two main phases**:

### Phase 1: Human Strategies

Applies logical strategies that humans commonly use to solve Sudoku.  

**These strategies include:**

- **Naked Singles:** Fill cells that have only one candidate.
- **Hidden Singles:** Fill a number that appears in only one cell within a unit (row, column, or box).
- **Naked N-tuples (pairs, triples, quads):** If N cells in a unit share exactly N candidates, these candidates can be removed from other cells in the unit.

**Iteration:** Phase 1 is applied repeatedly until no more progress can be made.

**Purpose:** Solve as much of the board as possible deterministically without guessing.

---

### Phase 2: MRV Backtracking

Used when Phase 1 cannot completely solve the board.

**MRV (Minimum Remaining Values):**

- Select the empty cell with the fewest candidates to minimize branching.

**Recursive backtracking:**

1. Assign a candidate to the selected cell.
2. Propagate Phase 1 on the new board (solve any deterministic opportunities created by this guess).
3. If a contradiction occurs (cell with no candidates), backtrack and try the next candidate.

**Purpose:** Guarantee solution for any valid Sudoku puzzle using a combination of guessing and logic propagation.

---

## Why Propagate Phase 1 After Each Guess

When we assign a value in Phase 2, new opportunities may appear for deterministic strategies.  

- Propagating Phase 1 after each guess allows us to fill more cells without extra recursion, **reducing overall time complexity**.
- Ensures Phase 2 (backtracking) only explores truly ambiguous cells.

---

## Differences Between Phase 1 & Phase 2

| Aspect                 | Phase 1 (Human Strategies)       | Phase 2 (MRV Backtracking)       |
|------------------------|---------------------------------|---------------------------------|
| Approach               | Deterministic (logic-based)     | Recursive & guessing            |
| Guarantees             | May not solve all puzzles       | Guaranteed to solve valid puzzles |
| Time Complexity        | Fast (O(1) per strategy per cell)| Exponential in worst-case O(9^n) |
| Candidate Assignment   | Only when logical certainty exists | Assigns possible candidates to explore solutions |
| Priority               | Always applied first            | Only applied if Phase 1 can’t finish |

---

## Features

- **Modular:** Phase 1 and Phase 2 functions can be used independently or together.
- **Effective:** Solves easy and medium puzzles quickly using human strategies.
- **Guaranteed:** Can solve any valid puzzle using MRV backtracking.
- **Optimized:** Propagates Phase 1 after every guess to reduce recursion and unnecessary branching.
- **Extensible:** Naked N-tuples can be easily extended to higher N if desired.

---

## Conclusion

- Human strategies alone **cannot guarantee a solution** for all Sudoku boards, especially very hard puzzles.
- MRV backtracking ensures **complete solution coverage**.
- Propagating Phase 1 after each guess **maximizes logical deductions** and reduces the search space for backtracking.
- This hybrid approach combines human-style intuition with algorithmic power, making the solver both **fast and reliable**.
