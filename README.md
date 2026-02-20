# S1PR4-DeNovo-Design
Fragment-based de novo drug design workflow for S1PR4 receptor using RDKit and ChEMBL data.

📖 Overview
This repository contains a computational workflow for fragment-based de novo drug design targeting the Sphingosine 1-phosphate receptor 4 (S1PR4). Unlike stochastic reinforcement learning methods, this approach leverages known bioactivity data and structural constraints to generate novel, drug-like candidates with higher scientific grounding.
The workflow automates the process from data retrieval to candidate ranking, utilizing RDKit for cheminformatics and ChEMBL for bioactivity data.

🎯 Scientific Background
Target: Sphingosine 1-phosphate receptor 4 (S1PR4)
ChEMBL ID: CHEMBL3230
Therapeutic Area: Immune cell trafficking, Cancer, Autoimmune diseases
Receptor Type: G Protein-Coupled Receptor (GPCR)
S1PR4 is a promising target for modulating immune responses. Known ligands typically share specific pharmacophoric features:
Hydrophobic Tail: Long alkyl chains or aryl rings.
Polar Head Group: Phosphate mimics (e.g., carboxylic acid, sulfonamide).
Central Linker: Heterocycles (e.g., furan, oxadiazole, phenyl).

🚀 Features
Automated Data Curation: Retrieves IC50 bioactivity data directly from ChEMBL.
Pharmacophore Analysis: Visualizes top potent ligands to identify structural trends.
Fragment Decomposition: Uses RECAP (Retrosynthetic Combinatorial Analysis Procedure) to break actives into synthetically accessible fragments.
Combinatorial Generation: Reconstructs novel molecules by linking fragments.
Multi-Objective Scoring: Ranks candidates based on:
Physicochemical properties (MW, LogP, TPSA).
Lipinski's Rule of Five compliance.
Toxicity filtering (Brenk structural alerts).
Visualization: Generates grid images of top-ranked candidates.

📋 Requirements
Python: 3.8 or higher
RAM: Minimum 8GB recommended (16GB preferred for larger fragment libraries)

Dependencies
Install the required Python packages:
pip install rdkit chembl_webresource_client pandas matplotlib tqdm ipython
Or using conda:
conda create -n s1pr4_design python=3.9
conda activate s1pr4_design
conda install -c conda-forge rdkit pandas matplotlib tqdm
pip install chembl_webresource_client

🛠️ Usage
Clone the repository:
git clone https://github.com/yourusername/S1PR4-DeNovo-Design.git
cd S1PR4-DeNovo-Design

Open the Notebook:
Launch Jupyter Notebook or Jupyter Lab:

jupyter notebook S1PR4_De_Novo_Design.ipynb

Execute Cells:
Run the cells sequentially from top to bottom. The notebook will:
Connect to ChEMBL APIs.
Generate fragments.
Create new molecules.
Output a ranked table of candidates.

🧬 Workflow Methodology
1. Data Curation
Retrieves compounds associated with CHEMBL3230 filtering for IC50 values. Removes duplicates and standardizes units.
2. Pharmacophore Definition
Analyzes the top 5 most potent ligands to define the essential structural requirements for binding.
3. Fragment Generation
Applies RDKit's RecapDecompose to ligands with IC50 < 1μM to extract high-quality fragments.
4. Combinatorial Reconstruction
Randomly pairs fragments and joins them. Invalid chemical structures are discarded automatically.
5. Multi-Objective Scoring
Each generated molecule is scored based on:
MW: 300–500 Da
LogP: 2–5 (Lipophilicity suitable for GPCR binding)
TPSA: 40–100 Å²
Toxicity: Passes Brenk filters (no reactive alerts)
6. Ranking
Molecules are sorted by a composite desirability score. The top 5 are visualized for review.

📊 Expected Output
Dataframe: A pandas DataFrame containing SMILES, properties, toxicity alerts, and scores.
Images: Grid images of initial ligands and top-ranked de novo candidates.
Logs: Console output indicating the number of fragments generated and molecules processed.

⚠️ Disclaimer
This project is for educational and research purposes only. The generated molecules are computational predictions and have not been experimentally validated. They should not be used for clinical purposes without extensive further testing, including:
Molecular Dynamics Simulations
Docking Studies
ADMET Profiling
In Vitro / In Vivo Assays

📄 License
This project is licensed under the MIT License - see the LICENSE file for details.

🤝 Contributing
Contributions are welcome! Please feel free to submit a Pull Request if you improve the scoring function, add new filters, or optimize the fragment generation logic.

📧 Contact
For questions or collaborations, please open an issue in the repository or contact the maintainer.

