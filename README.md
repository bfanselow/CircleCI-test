# CircleCI test

## A Continous-Integration demonstration using CircleCI

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
We instruct CircleCI on how to run your build using a YAML config file inside a **.circleci** dir in your repo base.  CircleCI expects this file to be called **config.yml.**
