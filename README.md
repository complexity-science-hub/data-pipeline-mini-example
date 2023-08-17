# data pipeline mini example

Serves as an introductory example towards DBT.

It can be extended if needed with:

- more in-depth introduction of DBT (jinja, macros, plugins)
- using DBT with postgres
- examples on how to apply
    - auto formatting
    - linting
    - testing
    - style checks for SQL
- introduction to dagster with DBT
- introduction to a more complex project (the migration project)

## prerequisites

- a computer with internet access to install python packages
- an installed mamba forge https://github.com/conda-forge/miniforge#mambaforge for your operating system
    - ensure the `mamba`command is in your path and working correctly
- docker
- an installation of `make` command in your path
- git
- an SSH key readily set up to connect to github
- permissions to view this (https://github.com/complexity-science-hub/data-pipeline-mini-example) repository

## set up of dependencies

```bash
git clone git@github.com:complexity-science-hub/data-pipeline-mini-example.git
cd data-pipeline-mini-example

make create_environment
# this should work irrespective of OS
# in case you use a Mac with ARM (Apple Silicon) this works as well (for the mini tutorial)
# in case you add more python packages where some do not support ARM use the create_environment_osx to use the x64 Rosetta emulation mode
```

## tutorial

### T1: DBT mini example

I am assuming you have activated your conda environment using:

```bash
conda activate data-pipeline-mini-example
```

Then

```bash
cd dpme_dbt

dbt deps
# download DBT plugins (if you use any)

dbt debug --profiles-dir config
# check everything is set up correctly
# you should not see any error if everything works fine on your setup

dbt run --profiles-dir config
# run the SQL code

dbt test --profiles-dir config
# run data quality tests

dbt build --profiles-dir config
# combines run & test in a single command

dbt docs generate --profiles-dir config
# compute the documentation

dbt docs serve --profiles-dir config
# serve the documentation
```
Move to this URL in your browser and explore the documentation http://localhost:8080/#!/model/model.dpme.my_first_dbt_model

Now look at the code in the models directory.

It is all plain SQL - plus some enhancements

### T2: (to follow as needed upon request)

lets discuss about what is useful for you/this project

## content backup for future tutorials

```
# ensure that the .env file with some variables is present and interpreted by your system to be used as environment variables
# the recommendation is to use https://ohmyz.sh/ with the https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/dotenv plugin

make start
# to start a postgres database on your computer
```