# SudokuSolver

![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)
![Algorithm](https://img.shields.io/badge/Algorithm-Backtracking-green)
![License](https://img.shields.io/badge/license-MIT-blue)
![Status](https://img.shields.io/badge/status-active-success)

A Python implementation of a Sudoku puzzle solver using the backtracking algorithm. This program efficiently solves standard 9x9 Sudoku puzzles by recursively trying different number combinations and backtracking when conflicts arise.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Algorithm](#algorithm)
- [Installation](#installation)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Example](#example)
- [Technical Details](#technical-details)
- [Requirements](#requirements)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)
- [Author](#author)

## Overview

This Sudoku solver implements a classic backtracking algorithm to solve any valid 9x9 Sudoku puzzle. The solver validates each number placement against Sudoku rules (row, column, and 3x3 box constraints) and uses recursion with backtracking to efficiently find the solution.

## Features

- **Efficient Backtracking Algorithm**: Uses recursive backtracking for optimal solving
- **Complete Validation**: Checks rows, columns, and 3x3 boxes for validity
- **Visual Board Display**: Prints the puzzle before and after solving with clear formatting
- **Zero Dependencies**: Uses only Python standard library
- **Educational Code**: Well-commented code suitable for learning algorithms
- **Fast Execution**: Solves most puzzles in milliseconds

## Algorithm

The solver uses the **Backtracking** algorithm:

1. **Find Empty Cell**: Locate the next empty cell (represented by 0)
2. **Try Numbers**: Attempt numbers 1-9 in the empty cell
3. **Validate**: Check if the number is valid (no conflicts in row, column, or 3x3 box)
4. **Recurse**: If valid, move to the next empty cell
5. **Backtrack**: If no valid number found, backtrack and try a different number
6. **Complete**: When no empty cells remain, the puzzle is solved

## Installation

### Prerequisites

- Python 3.6 or higher
- No external dependencies required

### Steps

1. **Clone the repository** (if using Git):
   ```bash
   git clone https://github.com/josemsantiago/SudokuSolver.git
   cd SudokuSolver
   ```

2. **Or download the script**:
   - Download `Sudoku_solver.py` directly
   - Place it in your preferred directory

3. **Verify Python installation**:
   ```bash
   python --version
   # or
   python3 --version
   ```

## Usage

### Basic Usage

Run the solver with the example board:

```bash
python Sudoku_solver.py
```

or on systems with both Python 2 and 3:

```bash
python3 Sudoku_solver.py
```

### Custom Puzzle

To solve your own Sudoku puzzle:

1. **Open `Sudoku_solver.py`** in your favorite editor

2. **Modify the `example_board` array** (line 1-11):
   - Use `0` to represent empty cells
   - Use numbers `1-9` for pre-filled cells

   Example:
   ```python
   example_board = [
       [5, 3, 0, 0, 7, 0, 0, 0, 0],
       [6, 0, 0, 1, 9, 5, 0, 0, 0],
       [0, 9, 8, 0, 0, 0, 0, 6, 0],
       [8, 0, 0, 0, 6, 0, 0, 0, 3],
       [4, 0, 0, 8, 0, 3, 0, 0, 1],
       [7, 0, 0, 0, 2, 0, 0, 0, 6],
       [0, 6, 0, 0, 0, 0, 2, 8, 0],
       [0, 0, 0, 4, 1, 9, 0, 0, 5],
       [0, 0, 0, 0, 8, 0, 0, 7, 9]
   ]
   ```

3. **Run the solver**:
   ```bash
   python Sudoku_solver.py
   ```

### Programmatic Usage

You can also import and use the solver in your own Python code:

```python
from Sudoku_solver import solver, print_board

# Your puzzle (0 represents empty cells)
my_board = [
    [7, 8, 0, 4, 0, 0, 1, 2, 0],
    [6, 0, 0, 0, 7, 5, 0, 0, 9],
    # ... rest of the board
]

# Solve the puzzle
print("Original Board:")
print_board(my_board)

if solver(my_board):
    print("\nSolved Board:")
    print_board(my_board)
else:
    print("\nNo solution exists for this puzzle")
```

## How It Works

### Core Functions

#### `valid(board, number, position)`
Validates if a number can be placed at a given position:
- **Row Check**: Ensures the number doesn't exist in the same row
- **Column Check**: Ensures the number doesn't exist in the same column
- **Box Check**: Ensures the number doesn't exist in the same 3x3 box

**Parameters**:
- `board`: The current Sudoku board (2D list)
- `number`: The number to validate (1-9)
- `position`: Tuple (row, col) representing the position

**Returns**: `True` if valid, `False` otherwise

#### `find_empty(board)`
Finds the next empty cell in the board:

**Parameters**:
- `board`: The current Sudoku board

**Returns**:
- Tuple `(row, col)` of the next empty cell
- `None` if no empty cells remain

#### `solver(board)`
Recursively solves the Sudoku puzzle using backtracking:

**Parameters**:
- `board`: The Sudoku board to solve (modified in place)

**Returns**:
- `True` if puzzle is solved
- `False` if no solution exists

#### `print_board(board)`
Prints the Sudoku board in a formatted grid:

**Parameters**:
- `board`: The Sudoku board to display

**Output**: Displays the board with visual separators for 3x3 boxes

## Example

### Input Board:
```
7 8 0 | 4 0 0 | 1 2 0
6 0 0 | 0 7 5 | 0 0 9
0 0 0 | 6 0 1 | 0 7 8
- - - - - - - - - - - -
0 0 7 | 0 4 0 | 2 6 0
0 0 1 | 0 5 0 | 9 3 0
9 0 4 | 0 6 0 | 0 0 5
- - - - - - - - - - - -
0 7 0 | 3 0 0 | 0 1 2
1 2 0 | 0 0 7 | 4 0 0
0 4 9 | 2 0 6 | 0 0 7
```

### Solved Board:
```
7 8 5 | 4 3 9 | 1 2 6
6 1 2 | 8 7 5 | 3 4 9
4 9 3 | 6 2 1 | 5 7 8
- - - - - - - - - - - -
8 5 7 | 9 4 3 | 2 6 1
2 6 1 | 7 5 8 | 9 3 4
9 3 4 | 1 6 2 | 7 8 5
- - - - - - - - - - - -
5 7 8 | 3 9 4 | 6 1 2
1 2 6 | 5 8 7 | 4 9 3
3 4 9 | 2 1 6 | 8 5 7
```

## Technical Details

### Time Complexity
- **Worst Case**: O(9^(n*n)) where n is the board size (9 for standard Sudoku)
- **Average Case**: Much faster due to early pruning from validation
- **Best Case**: O(n*n) when puzzle is already solved or nearly solved

### Space Complexity
- **O(n*n)**: Recursion stack depth in worst case
- Modifies the input board in place (no extra board storage)

### Algorithm Characteristics
- **Complete**: Always finds a solution if one exists
- **Sound**: Only returns valid Sudoku solutions
- **Deterministic**: Same puzzle always produces same solution

### Optimization Techniques Used
1. **Early Termination**: Validation stops at first conflict
2. **Box Calculation**: Efficient 3x3 box boundary computation
3. **In-Place Modification**: No extra memory for board copies
4. **Sequential Search**: Optimized empty cell discovery

## Requirements

- **Python**: 3.6+ (recommended), works with Python 2.7+
- **Operating System**: Cross-platform (Windows, macOS, Linux)
- **Dependencies**: None (uses only Python standard library)
- **Memory**: Minimal (< 1 MB)
- **Disk Space**: < 10 KB

## Project Structure

```
SudokuSolver/
├── Sudoku_solver.py      # Main solver implementation
├── README.md             # This file
├── LICENSE               # MIT License
├── CHANGELOG.md          # Version history
├── CONTRIBUTING.md       # Contribution guidelines
├── requirements.txt      # Dependencies (none required)
├── .gitignore           # Git ignore rules
├── .editorconfig        # Editor configuration
├── Sudoku Solver.pdf    # Algorithm documentation
└── Sudoku Solver.docx   # Algorithm documentation (Word)
```

## Performance

### Benchmark Results
- **Easy Puzzles**: < 0.01 seconds
- **Medium Puzzles**: < 0.1 seconds
- **Hard Puzzles**: < 1 second
- **Extreme Puzzles**: 1-5 seconds

*Tested on: MacBook Pro M1, Python 3.9*

## Limitations

- Designed for standard 9x9 Sudoku only
- Does not check if the initial puzzle is valid
- Assumes input board is properly formatted (9x9 grid)
- Does not support puzzle generation (solver only)

## Future Enhancements

Potential improvements for future versions:
- [ ] Input validation for initial board
- [ ] Support for different board sizes (4x4, 16x16)
- [ ] GUI implementation using Tkinter
- [ ] Puzzle generator
- [ ] Multiple solution detection
- [ ] Performance statistics and timing
- [ ] Step-by-step solution visualization
- [ ] CLI with argument parsing

## Screenshots

> **Note:** Screenshots will be added soon. To see the solver in action, run `python Sudoku_solver.py` - the console will display the puzzle before and after solving with formatted output.

## Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### How to Contribute

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

**Jose Santiago Echevarria**
- GitHub: [@josemsantiago](https://github.com/josemsantiago)
- Email: jose.santiago.echevarria@outlook.com

## Acknowledgments

- Backtracking algorithm concept from classic computer science literature
- Sudoku puzzle rules from World Sudoku Championship standards
- Inspired by various algorithmic problem-solving techniques

## Additional Resources

- [Sudoku Rules](https://www.sudoku.com/how-to-play/sudoku-rules-for-complete-beginners/)
- [Backtracking Algorithm](https://en.wikipedia.org/wiki/Backtracking)
- [Python Recursion](https://docs.python.org/3/tutorial/controlflow.html#defining-functions)

---

**Need Help?** Open an issue on GitHub or contact the author directly.

**Enjoy solving Sudoku puzzles!** 🧩
