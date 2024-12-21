# us-congress-members-trading-analysis

<a target="_blank" href="https://cookiecutter-data-science.drivendata.org/">
    <img src="https://img.shields.io/badge/CCDS-Project%20template-328F97?logo=cookiecutter" />
</a>

A short description of the project.

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

