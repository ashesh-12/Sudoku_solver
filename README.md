# 🧠 Sudoku Solver in Python

This project is a **Sudoku Solver** built using Python. It began with a simple recursive backtracking approach and evolved into a sophisticated system that incorporates both **human-like solving strategies** and **heuristic optimizations (MRV)** for enhanced efficiency.

---

## 🗂️ Project Structure

The project progressed in multiple stages:

### 1. ✅ Backtracking + Recursion (Baseline)
- **Approach**: Implemented a classical backtracking algorithm with a recursive structure.
- **Functions**:
  - `find_empty()` to locate the next empty cell.
  - `is_valid()` to check if a number can be placed at a given position.
  - `solver()` to recursively try placing numbers.
- **Outcome**: Successfully solved all valid Sudoku puzzles but could be inefficient for harder boards due to exhaustive search.

---

### 2. 🧩 Human-Solving Strategies
As someone who enjoys solving Sudoku manually, I brought in real-life strategies that players use:

- **Naked Singles** – Place a number if it's the only possible candidate for a cell.
- **Hidden Singles** – Place a number if it's the only position for that candidate in a unit.
- **Naked Pairs** – Eliminate candidates when two cells share the same pair.

#### 📊 Result:
- These strategies were implemented separately and together (`human_strategies()`).
- **Easy boards**: Solved completely using these rules.
- **Medium boards**: Solved partially.
- **Hard boards**: Not enough alone – required guessing/backtracking.

---

### 3. 🧠 MRV (Minimum Remaining Values) Heuristic – Optimized Backtracking
I transitioned into AI-inspired **heuristic optimization** from the **Constraint Satisfaction Problem (CSP)** domain.

- **select_mrv_cell()**: Selects the empty cell with the fewest possible candidates.
- **mrv_solver()**: Performs backtracking guided by MRV for faster convergence.
  
#### Outcomes:
- Drastically improves performance on harder boards.
- Reduces the number of unnecessary recursive calls.
- Solves even the hardest 17-clue puzzles in milliseconds.

---

## 🔀 Current Thoughts & Hybrid Direction
After implementing both **human strategies** and **MRV-based backtracking**, I believe the optimal approach is a **hybrid model**:
> Use human strategies to reduce the board as much as possible, then apply MRV-based backtracking to finish the puzzle efficiently.

This combination mirrors how experienced human players tackle puzzles and complements it with AI-level speed and accuracy.

---

## 📌 Example Boards
- Easy, Medium, Hard boards tested
- Known 17-clue Sudoku minimal puzzle solved

---

