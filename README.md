
# Sudden Vector Projection (SVP) Model

A computational tool for predicting mode specificity and product energy disposal in chemical reactions based on the Sudden Vector Projection model developed by Prof. Bin Jiang and Prof. Hua Guo.

## Overview
The SVP model predicts reaction outcomes by analyzing projections of normal mode vectors onto the reaction coordinate at the transition state. It extends Polanyi's Rules to polyatomic reactions and has been successfully applied to:
- Gas-phase reactions
- Gas-surface reactions
- Systems with incomplete vibrational energy redistribution

## Key Features
- Calculates Sudden Vector Projections (SVPs) from ab-initio frequency calculations
- Supports multiple quantum chemistry packages:
  - Gaussian09/16
  - Molpro
  - VASP (gas-surface reactions)
  - Polyrate (with PES)
- Provides insights into mode-specific reactivity
- Applicable to transition-state controlled reactions

## Installation
1. Download from **Prof. Hua Guo's website** http://www.unm.edu/~hguo/Research.html
2. Extract package
3. Compile with Intel compiler:
   ```bash
   source intel_env.sh  # Activate Intel compiler environment
   make
   ```

## Usage Examples
Three sample cases are included:
1. **F+H₂O** (Polyrate/PES)
2. **H+CHD₃** (Molpro)
3. **H₂+Cu(111)** (VASP)

### Critical Preparation Step
⚠️ **IMPORTANT**: When calculating frequencies for reactants/products using ANY software (Polyrate/Gaussian/Molpro/VASP):
1. Combine both reactants (or products) into a single molecular system
2. Separate them by sufficient distance (>10 Å recommended) to avoid possible molecular interactions
3. Perform frequency calculation on this combined system
4. One SVP calculation used for one reaction path

### General Workflow
```bash
# For all cases
./svp.x < input.txt > output.out
```

### Case 1: Polyrate/PES
1. Prepare reactant/product geometries in Polyrate
2. Place `xxx.fu6` files in working directory
3. Run SVP calculation:
   ```bash
   cp svp.x F+H2O/
   cd F+H2O
   ./svp.x < fh2oinput-reactant.txt.txt > reactant.out
   ```

### Case 2: Gaussian/Molpro/VASP
1. Calculate frequencies for:
   - Reactant complex (separated reactants)
   - Transition state
   - Product complex (separated products)
2. Prepare input files following examples
3. Execute calculation as above

## Input Preparation
Key parameters in `input.txt`:
- Geometry specifications
- Frequency calculation outputs
- Reaction coordinate definition

## Important Notes
⚠️ **Limitations**
- Only valid for transition-state controlled reactions
- Separate SVP calculations for reactants and products
- Requires basic understanding of mode-specific chemistry

## Citation
If using this software, please cite:
```bibtex
@article{guo2014sudden,
  title={The sudden vector projection model for reactivity: Mode specificity and bond selectivity made simple},
  author={Guo, Hua and Jiang, Bin},
  journal={Accounts of Chemical Research},
  volume={47},
  number={12},
  pages={3679--3685},
  year={2014},
  publisher={ACS Publications}
}
@article{jiang2013control,
  title={Control of mode/bond selectivity and product energy disposal by the transition state: X+ H2O (X= H, F, O (3P), and Cl) reactions},
  author={Jiang, Bin and Guo, Hua},
  journal={Journal of the American Chemical Society},
  volume={135},
  number={40},
  pages={15251--15256},
  year={2013},
  publisher={ACS Publications}
}
@article{jiang2013relative,
  title={Relative efficacy of vibrational vs. translational excitation in promoting atom-diatom reactivity: Rigorous examination of Polanyi's rules and proposition of sudden vector projection (SVP) model},
  author={Jiang, Bin and Guo, Hua},
  journal={The Journal of Chemical Physics},
  volume={138},
  number={23},
  year={2013},
  publisher={AIP Publishing}
}
```

## References
1. Jiang & Guo, J. Chem. Phys. 2013 ([10.1063/1.4811103](https://doi.org/10.1063/1.4811103))
2. Jiang & Guo, J. Am. Chem. Soc. 2013 ([10.1021/ja408119k](https://doi.org/10.1021/ja408119k))
3. Li & Guo, J. Phys. Chem. A 2014 ([10.1021/jp5004764](https://doi.org/10.1021/jp5004764))

## Disclaimer
This code is provided "as-is" without warranty. Users are responsible for:
- Validating results
- Understanding model limitations
- Proper input preparation

## Contact
Prof. Hua Guo  
University of New Mexico  
Email: hguo@unm.edu  

Original developer:  
Prof. Bin Jiang (bjiang@unm.edu)
```
