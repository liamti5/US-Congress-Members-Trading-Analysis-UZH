# us-congress-members-trading-analysis
> [!NOTE]  
> This repository was created as a final project for the Network Science course at the University of Zurich.

This repository investigates trading patterns of US Congress members using network science techniques. By constructing and analyzing networks based on historical trade data, the project aims to uncover patterns and communities that may indicate suspicious trading behaviors.


## **Project Overview**
The project focuses on the following aspects:
- **Data Collection**: Trading data was sourced from the [QuiverQuant API](https://www.quiverquant.com/) and the [Congress Trades Dashboard](https://github.com/adrianmross/congress_trades_dashboard).
- **Graph Creation**: Networks were built with nodes representing Congress members and edges connecting members with similar trading activities.
- **Graph Analysis**: Statistical properties, community detection, and centrality measures were explored.
- **Graph Machine Learning**: Predictive analysis was conducted to identify anomalous trading returns.


## **Key Findings**
The main findings and insights are summarized in the `reports/report.ipynb` notebook. These include:
- Statistical properties of the networks.
- Community structures and their implications.
- Centrality metrics and key influencers within the network.
- Predictive modeling results for identifying anomalous returns.
For in-depth exploration, refer to the notebooks in the `notebooks` folder.


## **Data Sources**
- [QuiverQuant API](https://www.quiverquant.com/)
- [Congress Trades Dashboard](https://github.com/adrianmross/congress_trades_dashboard)

---

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
---

## Naming Conventions for Jupyter Notebooks (based on [Cookiecutter Data Science](https://drivendata.github.io/cookiecutter-data-science/))

`0.01-pjb-data-source-1.ipynb`

- 0.01 - Helps keep work in chronological order. The structure is PHASE.NOTEBOOK. NOTEBOOK is just the Nth notebook in that phase to be created.
  - 0 - Data exploration
  - 1 - Data cleaning and feature creation
  - 2 - Visualizations
  - 3 - Modeling - training machine learning models
  - 4 - Publication - Notebooks that get turned directly into reports
- pjb - Authors initials; this is helpful for knowing who created the notebook and prevents collisions from people working in the same notebook.
- data-source-1 - A description of what the notebook covers

---

## Project Organization

```
├── Makefile           <- Makefile with convenience commands like `make data` or `make train`
├── README.md          <- The top-level README for developers using this project.
├── data
│   ├── external       <- Data from third party sources.
│   └── internal       <- Internal data that has been transformed.
│
├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
│                         the creator's initials, and a short `-` delimited description, e.g.
│                         `1.0-jqp-initial-data-exploration`.
│
├── reports            <- Contains the main jupyter notebook report.
│
├── pyproject.toml     <- Project configuration file with package metadata for 
│                         us_congress_members_trading_analysis and configuration for tools like black
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
    └── config.py               <- Store useful variables and configuration
```



