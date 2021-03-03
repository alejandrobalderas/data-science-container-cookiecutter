# Cookiecutter Data Science

_A logical, reasonably standardized, but flexible project structure for doing and sharing data science work._ 

### Requirements to use the cookiecutter template:
-----------
 - Python 3.5+
 - [Cookiecutter Python package](http://cookiecutter.readthedocs.org/en/latest/installation.html) >= 1.4.0: This can be installed with pip by or conda depending on how you manage your Python packages:
 - [Pipenv](https://pypi.org/project/pipenv/)

``` bash
pip3 install cookiecutter

# In a debian based system
sudo apt install pipenv

# Or following the official recommendations you can use the alternative command
# pipx install pipenv
```


### To start a new project, run:
------------

``` bash
cookiecutter https://github.com/alejandrobalderas/data-science-template
```

### Usage

Once the structure is in place you can run the following command in your terminal to start a new python virtual environment with pipenv
``` bash
pipenv install
```
This will install all packages inside of the Pipfile which by default include the following:
- pandas
- numpy
- scikit-learn
- scipy
- jupyterlab
- seaborn
- matplotlib
- statsmodels
- python-dotenv

If you want to install aditional packages you can run 
``` bash
pipenv install [name of your package]
```
or alternatively edit the Pipfile and just `pipenv install`.

The virtualenv will also install the src directory as a python package. You can import it from every file in your project without needing to worry about the path. 

#### Running the application
If you are using this repo to build an application use main.py as your main entry point. You can then use the Dockerfile to build an image to run the application inside a container.

You can use jupyter lab as a development environment from within the container by running 
``` bash
docker-compose up jupyter
```
This will build the app image and then run jupyter lab exposing port 8080. 

    
#### Difference to original Repo
This Repo was forked from [here](http://drivendata.github.io/cookiecutter-data-science/) and adapted by deleting some of the overhead of the original project.

This template will not try to build packages that you can then push into pip. The tox functionality was striped out. There is no binding to AWS and for the time being no Licence options.

This repo was expanded to add Docker functionality making data science projects even more portable. It uses pipenv to manage package dependencies as it has been proven better for reproducibility than just a requirements.txt


### The resulting directory structure
------------

The directory structure of your new project looks like this: 

```

    ├── Makefile           <- Makefile with commands like `make data` or `make train`
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `AB-01-initial-data-exploration`.
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── Pipfile            <- Using pipfile to manage package inside the project
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

```
