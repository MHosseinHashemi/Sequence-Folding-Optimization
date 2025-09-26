#### Bioinformatics Graduate Course Project:
# Optimizing Protein Sequence Folding in a 3D Lattice

---

### Objective
This project explores **protein sequence folding** using the **Hydrophobic–Polar (HP) model** on a **3D lattice structure**. The primary objective is to apply a **Genetic Algorithm (GA)** to optimize folding pathways and achieve minimal energy conformations.  

Protein folding is a fundamental challenge in **bioinformatics** and **computational biology**, where simplified models like HP help us understand how amino acid sequences determine 3D structures.  

This implementation includes:  
- Random sequence and population initialization.  
- Folding path generation in 2D and 3D lattices.  
- Fitness evaluation using the **Custodio energy function**.  
- Optimization via **Genetic Algorithm** operators (selection, crossover, mutation).  
- Visualizations of folding conformations and energy convergence. 

### A glimpse of HP model
The HP model reduces amino acids into two categories:  
- **H (Hydrophobic):** Non-polar residues that cluster away from solvent.  
- **P (Polar):** Polar residues that interact with solvent.  

The folding task is modeled on a **lattice**, where the sequence seeks a conformation that minimizes hydrophobic–polar energy.  

---

### Workflow  
1. **Population Initialization**  
   - Randomly generate sequences of `H` and `P`.  

2. **Path Representation**  
   - Encode folding moves as relative steps: `L` (left), `R` (right), `F` (forward).  

3. **Folding Simulation**  
   - Map paths onto **2D** or **3D lattices**.  

4. **Fitness Evaluation**  
   - Apply the **Custodio function**:  
     - Reward valid hydrophobic contacts.  
     - Penalize overlaps and invalid paths.  
     - Favor stable, low-energy structures.  

5. **Genetic Algorithm**  
   - **Selection:** Choose the fittest solutions (tournament selection).  
   - **Crossover:** Combine folding paths from two candidates.  
   - **Mutation:** Randomly alter moves to introduce variation.  
   - Iterate across generations to improve folding solutions.  

---

### Code Documentation  

#### 1. Population & Initialization  
- **`population_init(n)`** – Generate a random sequence of length `n` (composed of `H` and `P`).  
- **`population_init(pop_size, sample_len)`** – Create an initial population of `pop_size` sequences, each of length `sample_len`.  

#### 2. Path & Folding  
- **`relative_path(n)`** – Generate a random folding path (`L`, `R`, `F`).  
- **`two_D_fold(rel_path)`** – Map folding onto a 2D lattice.  (Initial Implementations, later moved to 3D)
- **`three_D_fold(rel_path)`** – Extend folding into 3D lattice space.  

#### 3. Evaluation & Fitness  
- **`contact_counter(seq, coords)`** – Count non-consecutive hydrophobic contacts.  
- **`custodio_energy_function(seq, coords, overlaps)`** – Compute folding energy with penalties for overlaps.  

#### 4. Genetic Algorithm  
- **`cross_over(seq_1, path_1, seq_2, path_2)`** – Combine folding paths from two parents.  
- **`mutation(path)`** – Randomly alter a folding path.  
- **`tournament_selection(population, paths, fitness_values, n)`** – Select `n` candidates via tournament selection.  
- **`GA(number_of_generations, pop_size, sample_len, mutation_rate)`** – Main GA loop for optimization.  

---

### Results
The GA successfully identified low-energy conformations for the insulin sequence. Visualizations of the optimized 3D lattice folding are available in the repository

#### Test Case: Homo Sapiens Insulin
<img width="1000" alt="Screenshot 2025-04-11 011518" src="https://github.com/user-attachments/assets/8890edaa-9a49-49dc-bcc3-57eb3a1a9ab5" />
<img width="1000" alt="Screenshot 2025-04-11 011518" src="https://github.com/user-attachments/assets/f8197b78-1ab5-4e7f-9113-5a76dbe883e2" />

---

**@Acknowledgement**

This readme while supervised by the repo owner, is written by GPT-5. Hence, if you wanted to integrate or use it, double check the source code.


