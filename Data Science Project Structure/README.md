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

- [PEP257](https://peps.python.org/pep-0257/) for docstring conventions
	- [Example Numpy Style Python Docstring](https://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_numpy.html)
	- [Example Google Style Python Docstrings](https://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_google.html)
- [PEP484](https://peps.python.org/pep-0484/) for type hints
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
	- [toptal/gitignore](https://github.com/toptal/gitignore) - The largest collection of useful `.gitignore` templates

## 🔗 Reference to articles to read

- [`.gitignore`](https://www.atlassian.com/git/tutorials/saving-changes/gitignore#global-git-ignore-rules)
	- [.gitignore](https://www.atlassian.com/ru/git/tutorials/saving-changes/gitignore) Russian
- [Git - `.gitignore` Documentation](https://git-scm.com/docs/gitignore)

## Useful tools and articles

- :octocat: [A collection of `.gitignore` templates](https://github.com/github/gitignore)
	- [Some common `.gitignore` configurations](https://gist.github.com/octocat/9257657)
	- [Python `.gitignore`](https://github.com/github/gitignore/blob/main/Python.gitignore)
- :octocat:[data-science-template/.gitignore](https://github.com/equinor/data-science-template/blob/master/.gitignore)

---

# 🪐 Jupiter Notebook Best Practices

## Autopep8

Autopep8 helps to reformat/prettify the contents of code cells with just a click. If you are tired of hitting the spacebar again and again to format the code, autopep8 is your savior.

## Magic Commands

There are two kinds of magic commands:

- line magic commands (start with `%`)
- cell magic commands (start with `%%`)

For a line magic command, inputs are provided following the command in the same line. 

For a cell magic command, contents in the entire cell become its inputs.

### `%load`

We can load code from an external source into a cell in Jupyter Notebook using this magic command.

Imagine that we are working in `magic_commands.ipynb` that is located in project1 folder and `setup.py` contained the following setup script:

``` python
# Contents in setup.py
# Data manipulation
import numpy as np
import pandas as pd

pd.options.display.max_columns=None
pd.options.display.float_format='{:.2f}'.format


# Visualisation
import matplotlib.pyplot as plt
import seaborn as sns

sns.set(style='whitegrid', context='talk', palette='rainbow')
```

We could import the contents in `setup.py` with the following one liner without leaving the notebook:

``` python
%load setup.py
```

It inserts the code from `setup.py` and comments itself.

If we wanted to load `setup.py` from the parent folder in the same notebook, we can update the file path to reflect the change:

``` python
%load ..\setup.py
```

Although this example case may seem trivial, it is a small change you could start practicing and it will hopefully inspire other applications.

Before we move on to the next command, it’s worth mentioning that while importing code from `.py` file is common, you can also import content from other files such as `.txt` and `.md`. In addition, you can also import code from URL like this:

``` python
%load https://gist.githubusercontent.com/zluvsand/74a6d88e401c4e3f76c2ae783a18689b/raw/5c9fd80a7bed839ba555bf4636e47572bd5c7e6d/pickle.py
```

### Save code with `%%writefile`

This command lets us do the opposite of the previous command. We can save code to an external source from a cell in Jupyter Notebook using this magic command. If we imagine ourselves still being inside magic_commands.ipynb, this is how we would create setup.py to Desktop without leaving the notebook:

``` python
%%writefile ..\setup.py

# Data manipulation
import numpy as np
import pandas as pd

pd.options.display.max_columns=None
pd.options.display.float_format='{:.2f}'.format


# Visualisation
import matplotlib.pyplot as plt
import seaborn as sns

sns.set(style='whitegrid', context='talk', palette='rainbow')
```

This will create a `setup.py` file if doesn’t exist. Otherwise, it will overwrite the contents in the existing file.

### Time code with `%timeit` or `%%timeit`

There are often multiple ways to accomplish the same task. One important consideration when choosing between the options is speed. Or sometimes you just want to time your code to understand its performance. Whatever your use case might be, it’s useful to know how to time your code. Fortunately, timing code is easy with `%[%]timeit`.

Firstly, we will prepare some dummy data:

``` python
import numpy as np

np.random.seed(seed=123)
numbers = np.random.randint(100, size=1000000)
```

Let’s imagine we wanted to time this code: `mean = np.mean(numbers)`. We can do so with the following one liner:

``` python
%timeit mean = np.mean(numbers)
```

Output shows mean and standard deviation of the speed across multiple runs & loops. This is more rigorous way to time your code compared to timing based on a single run.

Now let’s understand the difference between `%timeit` and `%%timeit `(the following guideline is true for most line and cell magic commands):

- To use %timeit, a line magic command, the code you want to time should consist of a single line and be written in the same line following the magic command. Although this is a good general rule, multiple lines is possible with tweaks according to the documentation (see documentation for details). 
- To use %%timeit, a cell magic command, the code you want to time can consist of any number of lines and written in the next line(s) following the magic command.

Here’s the equivalent of the previous code using `%%timeit`:

``` python
%%timeit
mean = np.mean(numbers)
```

### Check session history with `%history`, `%notebook`, `%recall`

These sets of commands are very useful if you experimented with a bunch of things and it’s already starting to get messy so it’s hard to remember exactly what you did. We can check the history of commands we ran in the current session with `%history`. Of note, `%hist` can be used instead of `%history`.
Let’s imagine we started a new session in section 3. We can see session history with:

``` python
%history
```

This is great but a little hard to see where one command ends and the other starts. Here’s how to check the history with each command numbered:

``` python
%history -n
```

This is easier to work with. Now, let’s learn how to export the history. If we want to write the history to a file named history.py in the same directory as the notebook, then we could use:

``` python
%history -f history.py
```

If we want to write the history to a Jupyter Notebook called `history.ipynb` in the same directory as the current notebook, then we use `%notebook`:

``` python
%notebook history.ipynb
```

This will insert each command into a separate cell. 

Sometimes, we may want to recall a section of commands from the history to tweak it or rerun it. In this case, we can use `%recall`. When using `%recall`, we need to pass the corresponding numbers for the section of commands from history like this example:

``` python
%recall 1-2
```

The code above inserts first two commands from history into the next cell.

### Other magic commands

- To see all available magic commands, run `%lsmagic`. 
- To access documentation for all commands, either check the documentation page or run `%magic`. 
- To access documentation of a magic command, you can run the magic command followed by `?`. For example: `%load?`.


## Embedded documentation

One of the very simple but effective features of Jupyter Notebook is its simple **documentation pop-up**. Once you have a function and open the parenthesis, hitting `Shift + Tab` simply opens a popup that displays the documentation of the function.

## Extensions

Notebook extensions let you move beyond the general vanilla way of using the Jupyter Notebooks. Notebook extensions (or `nbextensions`) are JavaScript modules that you can load on most of the views in your Notebook’s frontend. These extensions modify the user experience and interface.

### Installation

Installation with conda:

``` python
conda install -c conda-forge jupyter_nbextensions_configurator
```

Or with pip:

``` python
pip install jupyter_contrib_nbextensions && jupyter contrib nbextension install

#incase you get permission errors on MacOS

pip install jupyter_contrib_nbextensions && jupyter contrib nbextension install --user
```

Start a Jupyter notebook now, and you should be able to see an NBextensions Tab with a lot of options. Click the ones you want and see the magic happen.

### Table of Contents

The (Table of Contents)[https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/toc2/README.html] enables the collection of all running headers and displays them in a floating window, as a sidebar or with a navigation menu. The extension is also draggable, resizable, collapsable, dockable and features automatic numeration with unique links ids, and an optional toc cell. Sections of currently selected/edited or running cells are highlighted in the toc. Some minor display tweaks are also available (moving header tile/menus, widening cells). Finally, the toc can be preserved when exporting to HTML. The highlighting indicates your current position in the document — this will help you keep oriented in long notebooks.

### Hinterland

Hinterland enables code autocompletion menu for every keypress in a code cell, instead of only calling it with the tab. This makes Jupyter notebook’s autocompletion behave like other popular IDEs such as PyCharm.

### Collapsible Headings

The [Collapsible Headings](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/collapsible_headings/readme.html) extension allows you to hide entire sections of code, thereby letting you focus on your current workflow stage.

### Default Template Extension

This [default template](https://github.com/WillKoehrsen/Data-Analysis/tree/master/setup) extension causes notebooks to not be created empty, but with a default structure and common imports. Also, it will repeatedly ask you to change the name from `Untitled.ipynb` to something meaningful.

- [Set Your Jupyter Notebook up Right with this Extension](https://towardsdatascience.com/set-your-jupyter-notebook-up-right-with-this-extension-24921838a332)
- :octocat: [Data-Analysis](https://github.com/WillKoehrsen/Data-Analysis/tree/master/setup)

### Snippets

The Jupyter [snippets](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/snippets/README.html) extension allows you to conveniently insert often needed code blocks, e.g. your typical import statements.

- [Snippets](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/snippets/README.html)

## Productivity Hacks

- Learn the [Jupyter Keyboard Shortcuts](https://www.cheatography.com/weidadeyue/cheat-sheets/jupyter-notebook). Print the list and hang it on the wall next to your screen.
- Get to know Jupyter extensions: [Codefolding](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/codefolding/readme.html), [Hide input all](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/hide_input_all/readme.html), [Variable Inspector](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/varInspector/README.html), [Split Cells Notebook](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/splitcell/readme.html) and [many more](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions.html).
- [Jupyter Widgets](https://ipywidgets.readthedocs.io/en/stable/examples/Widget%20Basics.html) (sliders, buttons, dropdown-menus, …) allow you to build interactive GUIs.
- The :octocat: [tqdm](https://github.com/tqdm/tqdm#ipython-jupyter-integration) library provides a convenient progress bar.

## Widgets

> Make notebooks interactive

[Widgets](https://ipywidgets.readthedocs.io/en/stable/examples/Widget%20Basics.html#What-are-widgets?) are eventful python objects that have a representation in the browser, often as a control like a slider, textbox, etc. Widgets can be used to build interactive GUIs for the notebooks.

### Installation

``` python
# pip
pip install ipywidgets
jupyter nbextension enable --py widgetsnbextension

# Conda
conda install -c conda-forge ipywidgets

#Installing ipywidgets with conda automatically enables the extension
```

Let us have a look at some of the widgets. For complete details, you can visit their :octocat: [Github repository](https://github.com/jupyter-widgets/ipywidgets/blob/1223d4128aebe6c8831a034a73d1546a91f5138a/docs/source/examples/Using%20Interact.ipynb).

## Qgrid

> Make Data frames intuitive

Qgrid is also a Jupyter notebook widget but mainly focussed at dataframes. It uses :octocat:[SlickGrid](https://github.com/mleibman/SlickGrid) to render pandas DataFrames within a Jupyter notebook. This allows you to explore your DataFrames with intuitive scrolling, sorting and filtering controls, as well as edit your DataFrames by double-clicking cells. The :octocat:[Github Repository](https://github.com/quantopian/qgrid) contains more details and examples.

### Installation

- Installing with pip:

``` python
pip install qgrid
jupyter nbextension enable --py --sys-prefix qgrid
# only required if you have not enabled the ipywidgets nbextension yet
jupyter nbextension enable --py --sys-prefix widgetsnbextension
```

- Installing with conda:

``` python
# only required if you have not added conda-forge to your channels yet
conda config --add channels conda-forge
conda install qgrid
```


## 🧰 Tools

- [awswrangler](https://aws-data-wrangler.readthedocs.io/en/stable/)
- [Watermark](https://github.com/rasbt/watermark)
	- > An IPython magic extension for printing date and time stamps, version numbers, and hardware information
- 

### Extentios for Jupiter Notebook

- The [jupyter_contrib_nbextensions](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/index.html) package contains a collection of community-contributed unofficial extensions that add functionality to the Jupyter notebook. These extensions are mostly written in Javascript and will be loaded locally in your browser.
	- :octocat: [Jupyter Nbextensions Configurator](https://github.com/Jupyter-contrib/jupyter_nbextensions_configurator) 
- [Table of Contents](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/toc2/README.html)

### Formatting Jupiter Notebook

- [CSS: color property](https://www.techonthenet.com/css/properties/color.php)
- [Coolors](https://coolors.co)
- [Bootstrap Alerts](https://www.w3schools.com/bootstrap/bootstrap_alerts.asp)
- [Online Unicode Text Editor and Converter](https://texteditor.com/characters/arrows/)
- [emoji-cheat-sheet](https://github.com/ikatyang/emoji-cheat-sheet/blob/master/README.md)
- **Widgets:**
	-  

## Articles

- [Enrich your Jupyter Notebook with these tips](https://towardsdatascience.com/enrich-your-jupyter-notebook-with-these-tips-55c8ead25255)
- [Jupyter Notebook Best Practices](https://towardsdatascience.com/jupyter-notebook-best-practices-f430a6ba8c69)
- [Jupyter Notebook Extensions](https://towardsdatascience.com/jupyter-notebook-extensions-517fa69d2231)
- [Working efficiently with JupyterLab Notebooks](https://florianwilhelm.info/2018/11/working_efficiently_with_jupyter_lab/)
- [Bringing the best out of Jupyter Notebooks for Data Science](https://towardsdatascience.com/bringing-the-best-out-of-jupyter-notebooks-for-data-science-f0871519ca29)
