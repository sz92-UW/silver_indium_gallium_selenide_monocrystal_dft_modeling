# Ab Initio Engineering of Chalcopyrite Alloys: $AgGa_{1-x}In_xSe_2$

This repository contains the computational framework, input decks, and structural data for evaluating the electronic and structural trends of the chalcopyrite alloy system $AgGa_{1-x}In_xSe_2$ ($x = 0, 0.25, 0.50, 1.00$). Calculations were performed using Density Functional Theory (DFT) as implemented in the **Quantum ESPRESSO** suite, leveraged on the University of Washington's **Hyak (Klone)** supercomputer cluster.

---

## Project Overview

Chalcopyrite semiconductors ($I-III-VI_2$) are highly regarded for optoelectronic and photovoltaic applications. This project systematically investigates how the chemical substitution of the Group III cation (replacing smaller $\text{Ga}$ with larger $\text{In}$) alters the underlying crystal lattice and electronic landscapes.

A $1 \times 1 \times 2$ tetragonal supercell configuration containing 16 atoms was engineered to cleanly simulate intermediate doping fractions ($x = 0.25$ and $x = 0.50$).

---

## Computational Methodology

* **Codebase:** Quantum ESPRESSO (`pw.x`)
* **Functional:** Generalized Gradient Approximation (GGA-PBE) with Ultra-Soft Pseudopotentials (USPP)
* **Kinetic Energy Cutoff:** `ecutwfc = 80.0 Ry`
* **K-Point Grid:** $4 \times 4 \times 4$ Monkhosrt-Pack automatic grid for Self-Consistent Field (SCF) ground-state convergence.
* **Electronic Smearing:** Gaussian smearing (`degauss = 0.02 Ry`) to handle convergence behaviors across varied alloy configurations.

### Simulation Pipeline
1. **Variable-Cell Relaxation (`vc-relax`):** Full optimization of internal atomic coordinates and lattice parameters ($a, c$) until total residual forces dropped below the $1.0 \times 10^{-4} \text{ Ry/Bohr}$ threshold.
2. **Self-Consistent Field Calculation (`scf`):** Fixed-geometry execution evaluating high-precision electronic charge densities (`conv_thr = 1.0d-9`).
3. **Electronic Properties:** Non-Self-Consistent Field (`nscf`) densified grids ($8 \times 8 \times 8$) and high-symmetry point path executions (`bands`) mapping out the Density of States (DOS) and Band Structures.

---

## Key Findings

### 1. Lattice Expansion Metrics
As Indium composition ($x$) scales to 100%, an anisotropic lattice expansion is observed due to the larger ionic radius of $\text{In}^{3+}$ relative to $\text{Ga}^{3+}$.

| Concentration ($x$) | Cation Configuration | $a$ (Å) | $c$ (Å) | Fermi_energy_eV |
| :--- | :--- | :--- | :--- | :--- |
| 0.00 ($AgGaSe_2$) | Pure End-member | 5.837 | 11.013 |   9.1756 |
| 0.25 | Symmetric Sub. | 5.873 | 11.187 |   9.0312 |
| 0.50 | Symmetric (50s) | 5.918 | 11.325 |   8.8922 |
| 1.00 ($AgInSe_2$) | Pure End-member | 5.983 | 11.766 |   8.5626 |

### 2. Local Anion Displacement
Internal geometry relaxations capture the physical displacement of the Selenium ($\text{Se}$) anions. Because $\text{In-Se}$ bonds are inherently longer than $\text{Ga-Se}$ bonds, internal localized strains break the perfect tetrahedral symmetry, directly dictating the non-linear electronic band gap bowing across the mixing sweep.

---

## How to Reproduce

To run these input decks on a Slurm-managed cluster environment like Hyak:

```bash

# Example: Running the 25% substitution ground state SCF
sbatch scripts/run_25_scf.sh
---

## 3. Creating the Repo via Command Line

Once you have your files ready on Hyak or your local machine, run these standard terminal commands to initialize and push your repository to GitHub:

```bash
# Initialize the local repository folder
git init

# Add all files to the tracking staging environment
git add .

# Commit with a clean description message
git commit -m "Initial commit: Add input templates, lattice data, and project documentation"

# Link to your personal remote GitHub repository
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/AgGaInSe2-DFT.git

# Push your code online
git push -u origin main
