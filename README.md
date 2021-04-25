# Introduction

This repository documents how to create a development environment in my Mac OS with Python & JupyterLab. 

## Install Python 3 in Mac OS

You will need Python installed in your local machine, - Mac OS comes with old versions of Python `/usr/bin/python Python 2.7.16`and `/usr/bin/python3 Python 3.8.2`

1) [Download the latest version for Mac OS X](https://www.python.org/downloads/mac-osx/)
2) Run "Install Certificates.command" from /Applications/Python 3.9 (From FINDER)
3) Open a SHELL (Terminal.app or iTerm) and run: `/Applications/Python 3.9/Update/Shell Profile.command`
4) Modify your SHELL to anticipate the new PYTHON in $PATH: `export PATH=/usr/local/bin:/usr/local/sbin:$PATH`
5) TIP: To avoid running "python" with the old version, in your .zshrc: `alias python=/usr/local/bin/python3" >> ~/.zshrc`
6) Never delete the original Python that OSX comes with.
7) From now on use the following PATH for the new python: `/usr/local/bin/python3`

[Miniforge](https://github.com/conda-forge/miniforge)

## Install PIP

Open your terminal or iTerm2 and install pip with: 

```
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python3 get-pip.py
```

When I installed Pythong and Pip I had this versions:

```
➜  ~ > python --version
Python 3.9.2
➜  ~ > pip --version
pip 21.0.1 from /Library/Frameworks/Python.framework/Versions/3.9/lib/python3.9/site-packages/pip (python 3.9)
```


## Isolated Python Environments

Python has three popular ways of creating virtual environment at the moment

- [Virtualenv](https://virtualenv.pypa.io/en/latest/): Virtualenv was the default way of creating virtual environment for many years. It is still used by many although people are moving to improved pipenv or conda (explained below).
- [PipEnv](https://pipenv.pypa.io/en/latest/): Pipenv was created due to many shortcomings of virtualenv.
- [Conda](https://docs.conda.io/projects/conda/en/latest/index.html): If you are an engineer, or a scientist or use Numpy/Scipy package in windows environment, you have probably experienced the frustration of having to do a lot of work to install numpy/scipy packages. Anaconda is a distribution of python that makes it super simple to install those packages. Anaconda also has their own virtual environment system called conda. Make sure to have Anaconda installed.- 


### My recommendation: PipEnv

To install pipenv, you need to install pip first. Then do

```
pip install pipenv
```







```
pipenv install pandas tabulate openpyxl lxml html5lib beautifulsoup4 sqlalchemy feather-format matplotlib xlrd scipy ipykernel jupyterlab pexpect ipython-sql Faker
```

### Jupyter lab
```

pipenv run jupyter lab
```

### Remove PipEnv Enrironment

```
pipenv --rm
```

## Conda

```
conda create -n environment-pandas
conda activate environment-pandas

conda install pandas tabulate openpyxl lxml html5lib beautifulsoup4 sqlalchemy feather-format matplotlib xlrd scipy ipykernel jupyterlab pexpect Faker

pip install ipython-sql
```

### Jupyter Lab
```
conda activate environment-pandas
jupyter lab
```


### Remove Conda Environment

````
conda env remove -n environment-pandas
````
