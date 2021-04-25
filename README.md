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
- [Conda](https://docs.conda.io/projects/conda/en/latest/index.html): If you are an engineer, or a scientist or use Numpy/Scipy package in windows environment, you have probably experienced the frustration of having to do a lot of work to install numpy/scipy packages. Anaconda is a distribution of python that makes it super simple to install those packages. Anaconda also has their own virtual environment system called conda. Make sure to have Anaconda installed.- 
- [PipEnv](https://pipenv.pypa.io/en/latest/): Pipenv was created due to many shortcomings of virtualenv and is my preferred method


### PipEnv

My personal preference is **PipEnv**, a tool that aims to bring the best of all packaging worlds (bundler, composer, npm, cargo, yarn, etc.) to the Python world. Windows is a first-class citizen, in our world.

To install pipenv, you need to install pip first. Then do

```
pip install pipenv
```

### PipEnv handson with a project

Let's create a simple proyect in python with just `main.py` under a virtual environment with pipenv


```
➜  ~ > mkdir myproject
➜  ~ > cd myproject
➜  myproject > pipenv install requests
Creating a virtualenv for this project...
Pipfile: /Users/luis/myproject/Pipfile
:
Pipfile.lock not found, creating...
Updated Pipfile.lock (fe5a22)!
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.

➜  myproject > cat Pipfile
[[source]]
url = "https://pypi.org/simple"
verify_ssl = true
name = "pypi"

[packages]
requests = "*"

[dev-packages]

[requires]
python_version = "3.9"

➜  myproject > pipenv lock
➜  myproject > pipenv lock -r
➜  myproject > pipenv shell
Launching subshell in virtual environment...
 . /Users/luis/.local/share/virtualenvs/myproject-8mgVbunj/bin/activate
➜  myproject >  . /Users/luis/.local/share/virtualenvs/myproject-8mgVbunj/bin/activate
(myproject) ➜  myproject > pip freeze
certifi==2020.12.5
chardet==4.0.0
idna==2.10
requests==2.25.1
urllib3==1.26.4
(myproject) ➜  myproject > cat > main.py
import requests
response = requests.get('https://httpbin.org/ip')
print('Your IP is {0}'.format(response.json()['origin']))

(myproject) ➜  myproject > python main.py
Your IP is 83.34.4.11
(myproject) ➜  myproject > exit

➜  myproject > pipenv run python main.py
Your IP is 83.34.4.11

```

### Prepare Jupyter lab environment

In this example I'm going to create a Jupyter Lab environment. First of all create the project (in the example python-regex`), then cd into it, install jupyterlab and run the lab. From your browser you can play in your new jupyterlab environment.

```
~ > mkdir python-regex
➜  ~ > cd python-regex
➜  python-regex >
➜  python-regex > pipenv install jupyterlab
➜  python-regex > pipenv run jupyter lab
```

Connect to my localhost at [http://localhost:8888/lab](http://localhost:8888/lab)
Create a new notebook

You can work from the browser or even from Visual Studio Code. 


### Other examples (Pandas environment)

For example, to create a Pandas environment run:

```
pipenv install pandas tabulate openpyxl lxml html5lib beautifulsoup4 sqlalchemy feather-format matplotlib xlrd scipy ipykernel jupyterlab pexpect ipython-sql Faker
```

### Remove PipEnv Enrironment

```
pipenv --rm
```

## Updates and Upgrades

Periodically run updates/upgrades of your installation: 

```
➜  ~ > pip install --upgrade pip
```

To update all installed packages with PIP there isn't a built-in flag yet, but you can use

```
➜  ~ > pip list --outdated --format=freeze | grep -v '^\-e' | cut -d = -f 1  | xargs -n1 pip install -U
```
