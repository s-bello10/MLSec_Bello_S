# MLSec_Bello_S
Project for the "Machine Learning Security" course.

## Index
<!-- TOC -->
* [Project](#project)
* [Technical specifications](#technical-specifications)
* [Repository structure](#repository-structure)
<!-- TOC -->

## Project
_Select five CIFAR-10 (ℓ∞) models from RobustBench and re-evaluate them using AutoAttack under different values of the radius epsilon (e.g., from 1/255 to 16/255, regularly spaced interval including the baseline 8/255), using a subset of 100-200 samples. Compare the resulting robust accuracies and model rankings across these settings. Evaluate the stability of model rankings across different epsilon values. Identify cases where these changes lead to significant rank shifts and discuss what this reveals about the reliability of RobustBench leaderboards._

## Technical specifications
- **CPU**: 13th Gen Intel i9-13900HX
- **GPU**: NVIDIA GeForce RTX 4070 Laptop GPU
- **Python** 3.12.12
- **PyTorch 2.5.1** + **PyTorch CUDA**
- **Anaconda** for virtual environment + **Jupyter Notebook**


## Repository structure
- Experiment files:
  - `AutoAttack.ipynb`: code where AutoAttack was executed;
  - `analysis.ipynb`: code where plots and tables were created;
  - `clean_ranking.json`: JSON file with clean accuracies;
  - `results_checkpoint.json`: JSON file containing the results of the experiment, for each pair "epsilon-model".
- Environment files:
  - `environment.yaml`: YAML file of Anaconda virtual environment;
  - `requirements.txt`: TXT file containing dependencies (it might be incomplete, though, as Anaconda doesn't natively support dependecies file like PIP).
- Documentation:
  - `MLSec_Bello_S_Project.pptx`: PowerPoint presentation with results and considerations;
  - `README.md`: this Markdown file.