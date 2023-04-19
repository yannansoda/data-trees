---
{"topic":"TechHack","dg-publish":true,"permalink":"/Notes/Conda virtual environment/","dgPassFrontmatter":true,"noteIcon":""}
---

# Create a conda virtual environment

### Step 1: install conda

First, make sure conda is installed on your computer. For instance, conda installation on MacOS can be found [here](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html).

By default, a conda base environment is activated every time you open a new terminal. You can turn off this auto-activation:

```bash
conda config --set auto_activate_base false
```

### Step 2: create an enviroment

Let's create a conda virual environment called `myenv`. You can also assign which python version would be used in `myenv`:

```bash
åconda create --name myenv
conda create --name myenv python=python3.7
```

More advanced is installing packages like `scipy` and `seaborn` along with creating the environment:

```bash
conda create --name myenv scipy seaborn
```

Now `myenv` should be shown when you list all conda environments:

```bash
conda info --envs
```

### Step 3: always activate the enviroment

You should activate the environment everytime when you are about to use it:

```bash
conda activate myenv
```

# Install or remove packages in a conda environment

After activating `myenv`, you might also want to check what packages you have installed in it:

```bash
conda list
```

You can simply install or uninstall a package like `scipy` (which is available via conda install) or `beautifulsoup4` (which is not available via conda install but can be obtained from [Anaconda.org](http://anaconda.org/)) in `myenv`:

```bash
conda install scipy
conda install -c anaconda beautifulsoup4
```

Non-conda packages, for instance, `lmfit`, can be installed via conda-forge:

```bash
conda install -c conda-forge lmfit
```

Removing a package is easy:

```bash
conda remove scipy
```

# Use a conda environment in a Jupyter notebook

To use a conda environment in Jupyter notebook, never forget activating this environment before you are installing anything or running any notebook. A new line should always start with the environment name in your terminal, like this...

```bash
(myenv)foo@foo:   # type your command here...
```

At the first-time use, you need to install ipython **specifically** in this environment `myenv` via two commands:

```bash
conda install -c anaconda ipykernel
python -m ipykernel install --user --name=myenv
```

Now you are ready to go! Launch the Jupyter notebook, and you should already find `myenv` listed in the `kernel` option!

### Bonus

If you are also a fan of Jupyter notebook diverse extensions supporting table of contents, spell check, etc., you can install [notebook extensions](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/index.html) **in this environment**:

```bash
conda install -c conda-forge jupyter_contrib_nbextensions
```

For example, activate a function `toc2` which help automatically generating a table of contents:

```bash
jupyter nbextension enable toc2/main
```

# Use a created conda environment in Pycharm

In biref, you can use an existing environment via Pycharm settings:

1.  Click Settings/Preferences and choose Project Python Interpreter.
2.  Add a project interpreter and select Conda Environment.
3.  Choose Existing environment and specify a path to the Conda executable in your file system, for example, \Users\foo\anaconda3\python.exe

More detailed steps can be found in Pycharm [documentation](https://www.jetbrains.com/help/pycharm/conda-support-creating-conda-virtual-environment.html).