# Stage 1: Data preparation

## Steps and important commands

### Get dataset from the [dataset repository](https://github.com/iNeuron-Pvt-Ltd/wafer-dataset) or- 
[Download Dataset](https://github.com/iNeuron-Pvt-Ltd/wafer-dataset/archive/main.zip){ .md-button } 

## Create a default structure -
Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a> cookiecutterdatascience

---

### Project Organization
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

---

```bash
git init
```

```bash
dvc init
```

```bash
git add . && git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/<USERNAME>/<REPONAME>.git
git push -u origin main
```

```bash 
git checkout -b dev
```

One line readme update and push command to dev branch-
```bash
git add README.md && git commit -m "update readme" && git push origin dev
```

add data 

```bash
dvc add Training_Batch_Files/*.csv Prediction_Batch_files/*.csv
```
```bash
git add data/data.xml.dvc data/.gitignore && git commit -m "Add raw data"
```

install dvc for gdrive

```bash
pip install dvc[gdrive]
```

add remote storage

```bash
dvc remote add -d storage gdrive://<DRIVE ID>

git add .dvc/config && git commit -m "Configure remote storage"
```

add gdrive credential secrets in github repo secrets. this credentials can be found in 
`.dvc >> temp >> gdrive-user-credentials.json`

push the data to remote -

```bash
dvc push
```

to retrived data
```bash
dvc pull
```

refer [dvc-data-versioning](https://dvc.org/doc/start/data-versioning) to know more

