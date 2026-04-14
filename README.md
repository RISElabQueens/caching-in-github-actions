# Replication Package for  
# *How Developers Adopt, Use, and Evolve CI/CD Caching: An Empirical Study on GitHub Actions*


This repository contains the replication package for our paper, *How Developers Adopt, Use, and Evolve CI/CD Caching: An Empirical Study on GitHub Actions*, submitted in *Empirical Software Engineering Journal(EMSE)*.

**Authors:** Kazi Amit Hasan, Yuan Tian, Safwat Hassan, and Steven H. H. Ding


## Package Structure

```text
for_submission/
├── data/
│   ├── cache_adopted_repos.csv
│   ├── non_cache_adopted_repos.csv
│   └── changes.csv
├── mining/
│   ├── metadata_mining.ipynb
│   ├── workflow_mining.ipynb
│   └── extract_changes.ipynb
├── rq1/
│   └── rq1.ipynb
├── rq2/
│   └── rq2.ipynb
├── rq3/
│   ├── rq3.ipynb
│   ├── freq_rq3.ipynb
│   ├── sample_28_adding_parameter.csv
│   ├── sample_32_removing_parameter.csv
│   ├── sample_77_adding_cache.csv
│   ├── sample_79_removing_cache.csv
│   ├── sample_86_cache_ver_update.csv
│   └── sample_87_updating_parameter.csv
└── README.md
```



## Overview

This package contain datasets used in our study and the notebooks needed to reproduce the analyses reported in the paper. The package is organized into three main parts:

- data/ contains the processed datasets used by the analysis notebooks.
- mining/ contains notebooks for rebuilding the dataset from scratch.
- rq1/, rq2/, and rq3/ contain the notebooks for reproducing the analyses associated with each research question.

### Mining notebooks

- `mining/metadata_mining.ipynb`: mines repository metadata such as language, stars, forks, contributors, commits, pull requests, and issues. This notebook uses the GitHub API and requires a `GITHUB_TOKEN`.
- `mining/workflow_mining.ipynb`: downloads GitHub Actions workflow histories for the target repositories using `gigawork`.
- `mining/extract_changes.ipynb`: compares workflow versions and extracts workflow-level and step-level changes. This is the notebook that produces the workflow-change dataset.

If you would like to rebuild the dataset from scratch rather than use the archived CSV files included in this package (recommended), run the notebooks in mining/ in the following order: 


1. `metadata_mining.ipynb`
2. `workflow_mining.ipynb`
3. `extract_changes.ipynb`

### Analysis notebooks

- `rq1/rq1.ipynb`: analyzes repository characteristics and cache prevalence using the packaged metadata and workflow-change data.
- `rq2/rq2.ipynb`: analyzes cache-related change patterns and transitions across workflow evolution.
- `rq3/rq3.ipynb`: analyzes state transitions and temporal relationships among cache-related change types.
- `rq3/freq_rq3.ipynb`: summarizes the manually labeled RQ3 sample files in `rq3/`.

## Requirements


- Python 3.10 or newer,
- Jupyter Notebook or JupyterLab,
- `pandas`,
- `numpy`,
- `matplotlib`,
- `seaborn`,
- `scipy`,
- `PyYAML`,
- `tqdm`,
- `PyGithub`,
- `GitPython`,
- `transitions`,
- Graphviz support for notebooks that render state diagrams,
- `gigawork` for workflow mining.



### Run the notebooks

Open the notebooks from the repository root:

```bash
jupyter notebook
```

To reproduce the main analysis results, we recommend running the notebooks in the following order:


1. `rq1/rq1.ipynb`
2. `rq2/rq2.ipynb`
3. `rq3/rq3.ipynb`
4. `rq3/freq_rq3.ipynb`




##### Notes:

- Reproducing the mining pipeline requires a GitHub personal access token.
- The mining notebooks may take substantial time depending on API limits, repository size, and workflow history size.


