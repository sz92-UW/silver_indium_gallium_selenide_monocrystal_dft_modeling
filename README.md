# First-Principles DFT Modeling of AgGa1-xInxSe2 Chalcopyrite Semiconductors

## Overview
This project uses first-principles density functional theory calculations to study AgGa1-xInxSe2 chalcopyrite semiconductors with different indium substitution concentrations. The workflow includes supercell model construction, vc-relax calculations, SCF calculations, and Fermi energy trend analysis.

## Motivation
AgGa1-xInxSe2 chalcopyrite semiconductors are relevant to optoelectronic and photovoltaic materials. Substituting In for Ga can tune the electronic behavior of the material, making DFT useful for understanding composition-property relationships.

## Methods
- Quantum ESPRESSO
- Density functional theory
- PBE-GGA exchange-correlation functional
- PAW pseudopotentials
- 16-atom supercell models
- vc-relax and SCF calculations
- UW Hyak high-performance computing
- Python-based data analysis and plotting

## Results
DFT calculations were performed for AgGa1-xInxSe2 compositions with different In concentrations. The calculated Fermi energy decreased systematically as In content increased, from 9.1756 eV for AgGaSe2 to 8.5626 eV for AgInSe2.

## Skills Demonstrated
- First-principles DFT modeling
- Quantum ESPRESSO input preparation
- HPC calculation workflow
- Crystal structure relaxation
- SCF electronic-structure calculation
- Materials data analysis
- Scientific plotting and technical reporting

## Repository Structure
- `inputs/`: selected Quantum ESPRESSO input files
- `results/`: cleaned result tables, including Fermi energy summary
- `figures/`: plots generated from calculation results
- `report/`: project summary report

## Notes
This repository is a cleaned academic project summary. Large raw output folders, temporary calculation files, and unnecessary HPC scratch files are not included.
