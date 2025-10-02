# Quantum Annealing for the Knapsack Problem

This repository contains a **Jupyter Notebook implementation** of the **Knapsack Problem** using **D-Wave’s quantum annealing framework**.  
It demonstrates how to formulate the problem as a **Binary Quadratic Model (BQM)**, embed it onto D-Wave’s hardware topology (via **MinorMiner**), and solve it using D-Wave’s **simulated annealing sampler**. The same code can be run on the **real D-Wave quantum annealer** with minimal changes.

---

## Repository Contents

- **`D_Wave_BQM_Knapsack_and_Embedding.ipynb`**  
  The main notebook containing:
  - Construction of the knapsack problem as a BQM.
  - Embedding onto D-Wave’s Chimera/Pegasus topology using **MinorMiner**.
  - Solving the problem via **D-Wave’s simulated annealing sampler**.  
    (Easily switchable to a real D-Wave solver.)

- **Knapsack instances (`.kp` format)**  
  Two example problem instances:
  - The first line: number of items.  
  - The second line: knapsack capacity.  
  - Following lines: two columns for each item’s **value** and **weight**.  

  Example (`example.kp`):
  ```
  5
  11
  8 4
  10 5
  15 8
  4 3
  5 2
  ```
  Here:
  - 5 items  
  - Capacity = 11  
  - Items: (value=8, weight=4), (value=10, weight=5), ...

---

## How It Works

1. **Problem Formulation**  
   - The knapsack problem is expressed as a **Binary Quadratic Model (BQM)**.  
   - Decision variables are binary: 1 = include item, 0 = exclude item.  
   - The objective maximizes total item value while enforcing the capacity constraint.

2. **Embedding**  
   - The BQM is mapped to D-Wave’s hardware graph using **MinorMiner**, which finds an efficient minor embedding.

3. **Solving**  
   - The embedded problem is solved using **D-Wave’s simulated annealer**.  
   - The notebook can be easily adapted to run on an actual **D-Wave quantum sampler** by swapping the solver backend.

---

## Requirements

- Python 3.x  
- [D-Wave Ocean SDK](https://docs.ocean.dwavesys.com/)  
  - `dimod`  
  - `minorminer`  
  - `dwave-system`  
- Jupyter Notebook

Install dependencies with:
```bash
pip install dwave-ocean-sdk
```

---

## Usage

1. Open the notebook:
   ```bash
   jupyter notebook D_Wave_BQM_Knapsack_and_Embedding.ipynb
   ```
2. Run through the cells to:
   - Load a knapsack instance (`.kp`).  
   - Build the corresponding BQM.  
   - Find an embedding.  
   - Solve via simulated annealing (or real quantum annealer).  

---

## Notes

- The provided `.kp` instances are small and intended for demonstration.  
- The notebook code is general enough to handle other `.kp` instances.  
- Switching to the real quantum annealer requires a valid **D-Wave Leap account** and API token.

---

## License

This project is released under the MIT License.
