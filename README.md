# MLSec_Bello_S
Project for the "Machine Learning Security" course.

## Index
<!-- TOC -->
* [Project](#project)
* [Experimental setup](#experimental-setup)
  * [Models](#models)
  * [Parameters](#parameters)
  * [Technical specifications](#technical-specifications)
* [Repository structure](#repository-structure)
* [Code](#code)
<!-- TOC -->

## Project
_Select five CIFAR-10 (ℓ∞) models from RobustBench and re-evaluate them using AutoAttack under different values of the radius epsilon (e.g., from 1/255 to 16/255, regularly spaced interval including the baseline 8/255), using a subset of 100-200 samples. Compare the resulting robust accuracies and model rankings across these settings. Evaluate the stability of model rankings across different epsilon values. Identify cases where these changes lead to significant rank shifts and discuss what this reveals about the reliability of RobustBench leaderboards._

## Experimental setup
### Models
- `Carmon2019Unlabeled`
- `Sehwag2021Proxy_R18`
- `Rebuffi2021Fixing_R18_ddpm`
- `Wang2023Better_WRN-28-10`
- `Cui2023Decoupled_WRN-28-10`

[Compromise between lightness and architectural diversity].

### Parameters
- **Test subset size**: 200
- **Epsilon values**: 1/255, 4/255, 8/255, 12/255, 16/255
- **Batch size**: 16

### Technical specifications
- **CPU**: 13th Gen Intel i9-13900HX
- **GPU**: NVIDIA GeForce RTX 4070 Laptop GPU
- **Python** 3.12.12
- **PyTorch 2.5.1** + **PyTorch CUDA**
- **Anaconda** for virtual environment + **Jupyter Notebook**

## Repository structure
- Source files (folder `./src`):
  - `AutoAttack.ipynb`: code where AutoAttack was executed;
  - `analysis.ipynb`: code where plots and tables were created.
- Results data (folder `./json`):
  - `clean_ranking.json`: JSON file with clean accuracies;
  - `results_checkpoint.json`: JSON file containing the results of the experiment, for each pair "epsilon-model". It was deemed necessary to not lose previous computation results, as AutoAttack takes some time and it had to be run in separate sessions.
- Environment files (folder `./env_files`):
  - `environment.yaml`: YAML file of Anaconda virtual environment;
  - `requirements.txt`: TXT file containing dependencies (it might be incomplete, though, as Anaconda doesn't natively support dependecies file like PIP).
- Documentation:
  - `MLSec_Bello_S_Project.pptx`: PowerPoint presentation with results and considerations;
  - `README.md`: this Markdown file.

## Code
The code is commented. Anyway, the AutoAttack is performed within a custom class:

```
auto_attack = EvaluateOnAutoAttack(
    models_names=MODELS,             # List of 5 RobustBench models to evaluate
    epsilons=EPSILONS,               # List of 5 epsilon values to test
    dataset="cifar10",               # CIFAR-10 dataset (32x32 RGB images, 10 classes)
    threat_model="Linf",             # L-infinity norm (max pixel change bounded by epsilon)
    device=DEVICE,                   # GPU or CPU
    checkpoint_path=CHECKPOINT_PATH, # File to save/resume results
    batch_size=BATCH_SIZE            # Batch size for forward passes
)

auto_attack.attackModel()
```

