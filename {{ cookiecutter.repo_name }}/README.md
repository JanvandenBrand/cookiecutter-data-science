{{cookiecutter.project_name}}
==============================

{{cookiecutter.description}}

# Instructions
The $ sign indicated operation from the terminal as a non-root user.

## Software requirements
1. Lunix style terminal, either Linux native OS, Git bash, or [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install)
2. Python >= 3.8

## Installation
1. Clone the repo:  
> $ git clone _your-repo_

2. Set-up a virtual environment to isolate the project:
> $ python3 -m venv ~/._path-to-your-repo_
> $ source ~/._path-to-your-repo_/bin/activate

3. install requirements
> $ make requirements

**NOTE:** If new packages are added during development, add them with a pinned version to _requirements.in_.  
For example:  
> numpy==1.22.2

4. Lint you code to adhere to style guides.
> make lint

5. Clean formatting
> make format

## Security checks, unit tests and license checks during development
### Security checks
To perform a static security lint step run in the terminal:
> $ bandit -r src tests -n 3 --severity-level high --confidence-level medium

To perform a dynamic scan of the package container, first install [trivy v0.28.0](https://aquasecurity.github.io/trivy/v0.28.0/) from a bash terminal:  
> $ sudo apt install -y rpm  
> $ wget https://github.com/aquasecurity/trivy/releases/download/v0.28.0/trivy_0.28.0_Linux-64bit.deb  
> $ sudo dpkg -i trivy_0.28.0_Linux-64bit.deb  
> $ trivy -v  

Next run a scan of an image from a repository, for example:
> $ trivy image _path-to-your-image_

### Unit Tests
To run pytest from the project root, run in the terminal:
> $ pytest tests -v

To run a specific test:
> $ pytest tests/test.py::*test_name* -v

To run a set of tests identified by a marker:
> $ pytest tests/test.py -m -v marker 

### Software license check
> $ pip-licenses --format=markdown --with-urls  --output-file=./licenses.md


# Project Organization
------------

    ├── LICENSE
    ├── Makefile           <- Makefile with commands like `make data` or `make train`
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── docs               <- A default Sphinx project; see sphinx-doc.org for details
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `1.0-jqp-initial-data-exploration`.
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
    │                         generated with `pip freeze > requirements.txt`
    │
    ├── setup.py           <- makes project pip installable (pip install -e .) so src can be imported
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   └── make_dataset.py
    │   │
    │   ├── features       <- Scripts to turn raw data into features for modeling
    │   │   └── build_features.py
    │   │
    │   ├── models         <- Scripts to train models and then use trained models to make
    │   │   │                 predictions
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │
    │   └── visualization  <- Scripts to create exploratory and results oriented visualizations
    │       └── visualize.py
    │
    └── tox.ini            <- tox file with settings for running tox; see tox.readthedocs.io


--------

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>
