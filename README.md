# CircleCI test

## A Continous-Integration demonstration using CircleCI to execute Flake8 and pytest 

## Resource:
  * CircleCI: https://circleci.com/   
  * Follows tutorial from https://realpython.com/python-continuous-integration/

## Goals:
  * Learn how to integrate GitHub project with CircleCI
  * Learn how to use **flake8** linter and **pytest-cov** for testing code "coverage". 

## Requires (pip install):
 * flake8 
 * pytest 
 * pytest-cov

### Flake8
Make sure to exclude **venv**, else flake8 will dump a bunch of warnings from the venv files.
```
 flake8 --statistics --exclude=venv
```

### pytest

**Basic testing**  
```
 python -m pytest -v
```
Notice we run pytest with instead of *python -m pytest [...]* instead of just *pytest*  This yields nearly equivalent behaviour but will add the current directory to sys.path, which is helpfull.   This allows us to simply write **import calculator** in the *tests/test_calculator* and pytest will successfully execute.

**Check coverage**
```
 python -m pytest tests -v --cov
```
We must create a **.coveragerc** file so that the coverage testsing omits the **venv** dir
```
$ cat .coveragerc
[run]
omit = venv/*
```

## CircleCI
 1) Create a **.circleci** dir in your repo base, and a YAML config file (**config.yml**) under this new dir. This instructs CircleCI on how to run your build (CircleCI expects this file to be called **config.yml.**)
 2) Add the build instructions in **config.yml** to include the **flake8** and **pytest** operations above.
 3) Now (git) add, commit and push changes (i.e. the **.circleci** directory). 
 4) Login to *circleci.com* (using GitHub) credentials. Find this project and select **"Set Up Project"** and follow instructions.
 5) All subsequent *push* requests for this project will automatically include the CI build steps. 
  

