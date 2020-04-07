# CircleCI test

A Continous-Integration demonstration using CircleCI:  https://circleci.com/   
Follows tutorial from https://realpython.com/python-continuous-integration/

## Goals:
  * Learn how to integrate GitHub project with CircleCI
  * Learn how to use **flake8** linter and **pytest-cov** for testing code "coverage". 

### Flake8
Make sure to exclude **venv**, else flake8 will dump a bunch of warnings from the venv files.
```
 flake8 --statistics --exclude=venv
```
