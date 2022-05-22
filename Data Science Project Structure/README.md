# Data Science Project Structure

## :octocat: Why use a specific project structure in Git?

### Take care of teammates

A well-defined, standard project structure means that a newcomer can begin to understand an analysis without digging into extensive documentation. It also means that they don't necessarily have to read 100% of the code before knowing where to look for very specific things.

Well organized code tends to be self-documenting in that the organization itself provides context for your code without much overhead. Other teammates will thank you for this because they can:

- Collaborate more easily with you on this analysis
- Learn from your analysis about the process and the domain
- Feel confident in the conclusions at which the analysis arrives

### Don't forget about yourself

Ever tried to reproduce an analysis that you did a few months ago or even a few years ago? You may have written the code, but it's now impossible to decipher whether you should use `make_figures.py.old`, `make_figures_working.py` or `new_make_figures01.py` to get things done. Here are some questions we've learned to ask with a sense of existential dread:

- Are we supposed to go in and join column X to the data before we get started or did that come from one of the notebooks?
- Come to think of it, which notebook do we have to run first before running the plotting code: was it "process data" or "clean data"?
- Where did the shapefiles get downloaded for the geographic plots?
- Et cetera…

## Creating a good project structure

### Automating project template creation with [Cookiecutter Data Science](https://github.com/drivendata/cookiecutter-data-science)

There is not a clear consensus in the data science community on best practices for organizing machine learning projects, but there is a tool called Cookiecutter Data Science which is a [standardized but flexible project structure for doing and sharing data science work. A few lines of code set up a whole series of subdirectories and make it easier to start, structure, and share analysis](https://github.com/drivendata/cookiecutter-data-science).

### The modified Cookiecutter Data Science

> Cookiecutter Data Science is a great template for data science projects out there, but it lacks some good practices such as testing, configuring, or formatting your code. That’s why we combine and supplement the standard template with a modified version of it by [khuyentran1401](https://github.com/khuyentran1401).

``` Shell
cookiecutter https://github.com/khuyentran1401/data-science-template
```

🧰 **The tools used in this template are:**

- [Poetry](https://python-poetry.org): Dependency management - 📃 [article](https://towardsdatascience.com/how-to-effortlessly-publish-your-python-package-to-pypi-using-poetry-44b305362f9f)
- [hydra](https://hydra.cc/): Manage configuration files - 📃 [article](https://towardsdatascience.com/introduction-to-hydra-cc-a-powerful-framework-to-configure-your-data-science-projects-ed65713a53c6)
- [pre-commit plugins](https://pre-commit.com/): Automate code reviewing formatting - 📃 [article](https://towardsdatascience.com/4-pre-commit-plugins-to-automate-code-reviewing-and-formatting-in-python-c80c6d2e9f5?sk=2388804fb174d667ee5b680be22b8b1f)
- [DVC](https://dvc.org/): Data version control - 📃 [article](https://towardsdatascience.com/introduction-to-dvc-data-version-control-tool-for-machine-learning-projects-7cb49c229fe0)
- [pdoc](https://github.com/pdoc3/pdoc): Automatically create an API documentation for your project

## Data is immutable, add `.gitignore` file

Don't ever edit your raw data, especially not manually, and especially not in Excel. Don't overwrite your raw data. Don't save multiple versions of the raw data. Treat the data (and its format) as immutable. The code you write should move the raw data through a pipeline to your final analysis. You shouldn't have to run all of the steps every time you want to make a new figure, but anyone should be able to reproduce the final products with only the code in src and the data.

Also, if data is immutable, it doesn't need source control in the same way that code does. Therefore, **by default, the data folder is included in the `.gitignore` file**. If you have a small amount of data that rarely changes, you may want to include the data in the repository.  Some other options for storing/syncing large data include  AWS S3 with a syncing tool (e.g., s3cmd), Git Large File Storage, Git Annex, and dat.

## Data Analysis

Often in an analysis you have long-running steps that preprocess data or train models. If these steps have been run already (and you have stored the output somewhere like the data/interim directory), you don't want to wait to rerun them every time. We prefer make for managing steps that depend on each other, especially the long-running ones. Make is a common tool on Unix-based platforms (and is available for Windows). Following the [make documentation](https://www.gnu.org/software/make/), [Makefile conventions](https://www.gnu.org/prep/standards/html_node/Makefile-Conventions.html#Makefile-Conventions), and [portability guide](http://www.gnu.org/savannah-checkouts/gnu/autoconf/manual/autoconf-2.69/html_node/Portable-Make.html#Portable-Make) will help ensure your Makefiles work effectively across systems. Here are [some](http://zmjones.com/make/) [examples](http://blog.kaggle.com/2012/10/15/make-for-data-scientists/) to [get started](https://web.archive.org/web/20150206054212/http://www.bioinformaticszen.com/post/decomplected-workflows-makefiles/).

Makefile allows you to create short and readable commands for a series of tasks. You can use Makefile to automate tasks such as setting up the environment:

``` python
install: 
	@echo "Installing..."
	poetry install
	poetry run pre-commit install

activate:
	@echo "Activating virtual environment"
	poetry shell

initialize_git:
  @echo "Initialize git"
	git init 

setup: initialize_git install
```

Now whenever others want to set up the environment for your projects, they just need to run:

``` Shell
make activate
make setup
```

There are other tools for managing DAGs that are written in Python instead of a DSL (e.g., [Paver](http://paver.github.io/paver/#), [Luigi](http://luigi.readthedocs.org/en/stable/index.html), [Airflow](https://airflow.apache.org/index.html), [Snakemake](https://snakemake.readthedocs.io/en/stable/), [Ruffus](http://www.ruffus.org.uk/), or [Joblib](https://pythonhosted.org/joblib/memory.html)). Feel free to use these if they are more appropriate for your analysis.

## Manage Data and Models with DVC

All data is stored under the subdirectories under `data`. Each subdirectory stores data from different stages.

All models are stored under the directory `model`.

Since Git is not ideal for version binary files, we use [DVC — Data Version Control](https://dvc.org) to version our data and models.

We specify DVC stages in the `dvc.yaml` file. Each stage represents individual data processes, including their inputs (`deps`) and resulting output (`outs`).

``` python
stages:
  process_data:
    cmd: python src/process.py
    deps:
    - config/main.yaml
    - config/process
    - data/raw
    - src/process.py
    outs:
    - data/processed:
        persist: true
  train_model:
    cmd: python src/train_model.py
    deps:
    - config/main.yaml
    - config/model
    - data/processed
    - src/train_model.py
    outs:
    - data/final:
        persist: true
    - models:
        persist: true
```

All directories and files under `outs` will be automatically tracked by DVC.

If you want to execute commands defined in their stages, run `dvc repro`. DVC will skip the stages that didn’t change.

### Store Your Data Remotely

The main benefit of using DVC is that it allows you to upload data tracked by DVC to remote storage. You can store your data on [DagsHub](https://towardsdatascience.com/dagshub-a-github-supplement-for-data-scientists-and-ml-engineers-9ecaf49cc505), Google Drive, Amazon S3, Azure Blob Storage, Google Cloud Storage, Aliyun OSS, SSH, HDFS, and HTTP.

``` Shell
dvc remote add -d remote <REMOTE-URL>
```

After adding data to your local project, you can push the data to remote storage:

``` Shell
dvc push
```

Add and push all changes to :octocat: Git:

``` Shell
git add .
git commit -m 'commit-message'
git push origin <branch>
```

## 🏗️ Build from the environment up

The first step in reproducing an analysis is always reproducing the computational environment it was run in. You need the same tools, the same libraries, and the same versions to make everything play nicely together.

One effective approach to this is to use [virtualenv](https://virtualenv.pypa.io/en/latest/) (we recommend [virtualenvwrapper](https://virtualenvwrapper.readthedocs.org/en/latest/) for managing virtualenvs). By listing all of your requirements in the repository (we include a `requirements.txt` file) you can easily track the packages needed to recreate the analysis. Here is a good workflow:

1. Run `mkvirtualenv` when creating a new project
2. `pip install` the packages that your analysis needs
3. Run `pip freeze > requirements.txt` to pin the exact package versions used to recreate the analysis
4. If you find you need to install another package, run `pip freeze > requirements.txt` again and commit the changes to version control.

If you have more complex requirements for recreating your environment, consider a virtual machine-based approach such as [Docker](https://www.docker.com/) or [Vagrant](https://www.vagrantup.com/). Both of these tools use text-based formats (Dockerfile and Vagrantfile respectively) you can easily add to source control to describe how to create a virtual machine with the requirements you need.

### Install Dependencies

This project uses  https://python-poetry.org  instead of pip to manage dependencies since Poetry allows you to:

- Separate the main dependencies and the sub-dependencies into two separate files (instead of storing all dependencies in `requirements.txt`)
- Create readable dependencies files
- Remove all unused sub-dependencies when removing a library
- Avoid installing new packages that are conflict with the existing packages
- Package your project in several lines of code

Find the instruction on how to install Poetry [here](https://python-poetry.org/docs/#installation). All main dependencies for this project are specified in `pyproject.toml` . 

- To install all dependencies, run:

``` Shell
poetry install
```

- To add a new PyPI library, run:

``` Shell
poetry add <library-name>
```

- To remove a library, run:

``` Shell
poetry remove <library-name>
```

## 🔐 Store your secrets and config variables in a special file

A configuration file stores all of the values in one place, which helps to separate the values from the code and avoid hard coding. In this template, all configuration files are stored under the directory `config`.

You really don't want to leak your AWS secret key or Postgres username and password on  Git. Enough said — see the [Twelve Factor App](http://12factor.net/config) principles on this point. Here's one way to do this:

### 🔑 Store your secrets and config variables in a special file

Create a `.env` file in the project root folder. Thanks to the `.gitignore`, this file should never get committed into the version control repository. Here's an example:

``` python
# example .env file
DATABASE_URL=postgres://username:password@localhost:5432/dbname
AWS_ACCESS_KEY=myaccesskey
AWS_SECRET_ACCESS_KEY=mysecretkey
OTHER_VARIABLE=something
```

### 📄 Use a package to load these variables automatically

If you look at the stub script in `src/data/make_dataset.py` from the project template created by Cookiecutter Data Science, it uses a package called [python-dotenv](https://github.com/theskumar/python-dotenv) to load up all the entries in this file as environment variables so they are accessible with os.environ.get. Here's an example snippet adapted from the python-dotenv documentation:

``` python
# src/data/dotenv_example.py
import os
from dotenv import load_dotenv, find_dotenv

# find .env automagically by walking up directories until it's found
dotenv_path = find_dotenv()

# load up the entries as environment variables
load_dotenv(dotenv_path)

database_url = os.environ.get("DATABASE_URL")
other_variable = os.environ.get("OTHER_VARIABLE")
```

### AWS CLI configuration

When using Amazon S3 to store data, a simple method of managing AWS access is to set your access keys to environment variables. However, managing mutiple sets of keys on a single machine (e.g. when working on multiple projects) it is best to use a [credentials file](https://docs.aws.amazon.com/cli/latest/userguide/cli-config-files.html), typically located in `~/.aws/credentials`. A typical file might look like:

``` python
[default]
aws_access_key_id=myaccesskey
aws_secret_access_key=mysecretkey

[another_project]
aws_access_key_id=myprojectaccesskey
aws_secret_access_key=myprojectsecretkey
```

### Manage Configuration Files with Hydra

[Hydra](https://hydra.cc/) is a Python library that allows you to access parameters from a configuration file inside a Python script.

**_For example,_** if our main.yaml file looks like below:
``` python
raw: 
  path: data/raw/sample.csv

processed:
  path: data/processed/processed.csv

final:
  path: data/final/final.csv
```

…, then we can access the value inside the configuration file by adding the decorator `@hydra.main` on a specific function. Inside this function, we can access the value under `processed` and `path` by using a dot notation: `config.processed.path`.

``` python
"""
This is the demo code that uses hydra to access the parameters in under the directory config.
Author: Khuyen Tran
"""

import hydra
from omegaconf import DictConfig
from hydra.utils import to_absolute_path as abspath

@hydra.main(config_path="../config", config_name='main')
def process_data(config: DictConfig):
    """Function to process the data"""

    raw_path = abspath(config.raw.path)
    print(f"Process data using {raw_path}")
    print(f"Columns used: {config.process.use_columns}")

if __name__ == '__main__':
    process_data()
```

## Check Issues in Your Code Before Committing

When committing your Python code to  Git, you need to make sure your code:
- looks nice
- is organized
- ‼️ conforms to the [PEP 8 – Style Guide for Python Code](https://peps.python.org/pep-0008/)
- ‼️ includes Docstrings

However, it can be overwhelming to check all of these criteria before committing your code. Pre-commit is a framework that allows you to identify simple issues in your code before committing it.

> [4 pre-commit Plugins to Automate Code Reviewing and Formatting in Python](https://towardsdatascience.com/4-pre-commit-plugins-to-automate-code-reviewing-and-formatting-in-python-c80c6d2e9f5)

We use 5 different plugins that are specified in `.pre-commit-config.yaml`. They are:

- [black](https://black.readthedocs.io/en/stable/) -  formats Python code
- [flake8](https://flake8.pycqa.org/en/latest/) — checks the style and quality of your Python code
- [isort](https://github.com/PyCQA/isort) - automatically sorts imported libraries alphabetically and separates them into sections and types.
- [mypy](https://github.com/python/mypy) — checks static type
- [nbstripout](https://github.com/kynan/nbstripout) — strips output from Jupyter notebooks

To add pre-commit to git hooks, type:

``` Shell
pre-commit install
```

Now, whenever you run `git commit`, your code will be automatically checked and reformatted before being committed.

### Plugins  

You can add different plugins to your pre-commit pipeline. Once your files are committed, they will be checked by these plugins. Unless all checks are passed, no code will be committed.

## 🔩 Tools

- **Cookiecutter Data Science:**
  - [Cookiecutter](https://github.com/cookiecutter/cookiecutter)
  - [Cookiecutter Data Science](http://drivendata.github.io/cookiecutter-data-science/)
  - :octocat:[cookiecutter-data-science](https://github.com/drivendata/cookiecutter-data-science)
- [readme.so](https://readme.so/)
- [Poetry](https://python-poetry.org): Dependency management - 📃 [article](https://towardsdatascience.com/how-to-effortlessly-publish-your-python-package-to-pypi-using-poetry-44b305362f9f)
- [hydra](https://hydra.cc/): Manage configuration files - 📃 [article](https://towardsdatascience.com/introduction-to-hydra-cc-a-powerful-framework-to-configure-your-data-science-projects-ed65713a53c6)
- [pre-commit plugins](https://pre-commit.com/): Automate code reviewing formatting - 📃 [article](https://towardsdatascience.com/4-pre-commit-plugins-to-automate-code-reviewing-and-formatting-in-python-c80c6d2e9f5?sk=2388804fb174d667ee5b680be22b8b1f)
- [DVC](https://dvc.org/): Data version control - 📃 [article](https://towardsdatascience.com/introduction-to-dvc-data-version-control-tool-for-machine-learning-projects-7cb49c229fe0)
- [pdoc](https://github.com/pdoc3/pdoc): Automatically create an API documentation for your project

### Other tools

- [Filesystem Hierarchy Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) for Unix-like systems
- [Git Large File Storage](https://git-lfs.github.com)
- [Git Annex](https://git-annex.branchable.com/)
- [make documentation](https://www.gnu.org/software/make/)
- [Makefile conventions](https://www.gnu.org/prep/standards/html_node/Makefile-Conventions.html#Makefile-Conventions)
- [portability guide](http://www.gnu.org/savannah-checkouts/gnu/autoconf/manual/autoconf-2.69/html_node/Portable-Make.html#Portable-Make)
- [GNU Make for Reproducible Data Analysis](http://zmjones.com/make/)
- []()

## 🔗 Reference to articles to read

- [Automate your data science project structure in three easy steps](https://towardsdatascience.com/automate-your-data-science-project-structure-in-three-easy-steps-277c92328d24)
- [How to Structure a Data Science Project for Readability and Transparency](https://towardsdatascience.com/how-to-structure-a-data-science-project-for-readability-and-transparency-360c6716800)
  - [Data Science Cookie Cutter](https://github.com/khuyentran1401/data-science-template)
- [How to Create a Professional Github Data Science Repository](https://towardsdatascience.com/how-to-create-a-professional-github-data-science-repository-84e9607644a2)


--- 

# `.gitignore`

## 🧰 Tools

- [gitignore.io](https://www.gitignore.io/)

## 🔗 Reference to articles to read

- [`.gitignore`](https://www.atlassian.com/git/tutorials/saving-changes/gitignore#global-git-ignore-rules)
	- [.gitignore](https://www.atlassian.com/ru/git/tutorials/saving-changes/gitignore) Russian
- [Git - `.gitignore` Documentation](https://git-scm.com/docs/gitignore)
- 

## Useful tools and articles

- :octocat: [A collection of `.gitignore` templates](https://github.com/github/gitignore)
	- [Some common `.gitignore` configurations](https://gist.github.com/octocat/9257657)
	- [Python `.gitignore`](https://github.com/github/gitignore/blob/main/Python.gitignore)
- 
