# us-congress-members-trading-analysis

## Naming Conventions for Jupyter Notebooks

`0.01-pjb-data-source-1.ipynb`

- 0.01 - Helps keep work in chronological order. The structure is PHASE.NOTEBOOK. NOTEBOOK is just the Nth notebook in that phase to be created.
  - 0 - Data exploration
  - 1 - Data cleaning and feature creation
  - 2 - Visualizations
  - 3 - Modeling - training machine learning models
  - 4 - Publication - Notebooks that get turned directly into reports
- pjb - Authors initials; this is helpful for knowing who created the notebook and prevents collisions from people working in the same notebook.
- data-source-1 - A description of what the notebook covers

## Project Organization

```
├── LICENSE            <- Open-source license if one is chosen
├── Makefile           <- Makefile with convenience commands like `make data` or `make train`
├── README.md          <- The top-level README for developers using this project.
├── data
│   ├── external       <- Data from third party sources.
│   ├── interim        <- Intermediate data that has been transformed.
│   ├── processed      <- The final, canonical data sets for modeling.
│   └── raw            <- The original, immutable data dump.
│
├── docs               <- A default mkdocs project; see www.mkdocs.org for details
│
├── models             <- Trained and serialized models, model predictions, or model summaries
│
├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
│                         the creator's initials, and a short `-` delimited description, e.g.
│                         `1.0-jqp-initial-data-exploration`.
│
├── pyproject.toml     <- Project configuration file with package metadata for 
│                         us_congress_members_trading_analysis and configuration for tools like black
│
├── references         <- Data dictionaries, manuals, and all other explanatory materials.
│
├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
│   └── figures        <- Generated graphics and figures to be used in reporting
│
├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
│                         generated with `pip freeze > requirements.txt`
│
├── setup.cfg          <- Configuration file for flake8
│
└── us_congress_members_trading_analysis   <- Source code for use in this project.
    │
    ├── __init__.py             <- Makes us_congress_members_trading_analysis a Python module
    │
    ├── config.py               <- Store useful variables and configuration
    │
    ├── dataset.py              <- Scripts to download or generate data
    │
    ├── features.py             <- Code to create features for modeling
    │
    ├── modeling                
    │   ├── __init__.py 
    │   ├── predict.py          <- Code to run model inference with trained models          
    │   └── train.py            <- Code to train models
    │
    └── plots.py                <- Code to create visualizations
```

--------

##  Setting up Development Environment using Docker to reproduce our findings

1. Clone the repository

```bash
git clone https://github.com/liamti5/US-Congress-Members-Trading-Analysis-UZH.git
```

2. Build the docker image using the provided dockerfile (you need to have [Docker](https://www.docker.com/products/docker-desktop/) installed):
```bash
docker build -t us-congress-trading .
```

3. Then, once the image is built, run the docker container 
   1. if you want to keep changes that you make in the container, you can mount your project directory to the container using a volume by running
    ```bash
   docker run -it --rm -p 8888:8888 -v "$(pwd):/app" us-congress-trading
   ```
   
   2. if you **don't** want to keep the changes you make in the container, run 
   ```bash
   docker run -it -p 8888:8888 --rm us-congress-trading
   ```

4. You should see an interactive bash session (in your commandline). You can look around the project, run `make` commands etc.

6. If you want to launch a jupyter server (necessary if you want to actually run the jupyter notebooks), run the following command:
```bash
jupyter notebook --ip=0.0.0.0 --port=8888 --no-browser --allow-root
```

