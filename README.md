
[![ci](https://github.com/VOLTTRON/volttron-sql-historian/workflows/ci/badge.svg)](https://github.com/eclipse-volttron/volttron-lib-sql-historian/actions?query=workflow%3Aci)
[![pypi version](https://img.shields.io/pypi/v/volttron-sql-historian.svg)](https://pypi.org/project/volttron-lib-sql-historian/)


Generic SQL Historian library that can be used to implement a historian agent with a relational database backend. 
This library cannot be installed as a VOLTTRON agent as is. Only a concrete database implementation package such as 
[sqlite-historian](https://github.com/eclipse-volttron/volttron-sqlitehistorian) that depends on this library can be 
installed as a VOLTTRON agent.


## Requirements

 - Python >= 3.8

## Installation

This library can be installed using ```pip install volttron-lib-sql-historian```. However this is not necessary. Any 
historian agent that uses this library will automatically install it as part of its installation. For example, 
installing [SQLiteHistorian](https://github.com/eclipse-volttron/volttron-sqlitehistorian) will automatically install 
volttron-lib-sql-historian

## Development

Development requires poetry 1.2.2 or greater be used.  
One can install it from https://python-poetry.org/docs/#installation.  The VOLTTRON team prefers to have the python 
environments created within the project directory.  Execute this command to make that behavior the default.

```shell
poetry config virtualenvs.in-project true
```

Clone the repository.

```shell
git clone https://github.com/eclipse-volttron/volttron-lib-sql-historian
```

Change to the repository directory and use poetry install to setup the environment.

```shell
cd volttron-lib-sql-historian
poetry install
```
To create a new relational database based historian by extending this library, subclass 
[DBDriver](https://github.com/eclipse-volttron/volttron-lib-sql-historian/blob/develop/src/historian/sql/basedb.py#L79).
The subclass should be in a module historian.<database_type>.<database_type>functs.py for it to be dynamically loaded 
by the base DBDriver. Please refer to [SQLiteHistorian](https://github.com/eclipse-volttron/volttron-sqlitehistorian) as 
an example

### Building Wheel

To build a wheel from this project execute the following:

```shell
poetry build
```

The wheel and source distribution will be located in the ```./dist/``` directory.

### Bumping version number of project

To bump the version number of the project execute one of the following.

```shell
# patch, minor, major, prepatch, preminor, premajor, prerelease

# use patch
user@path$ poetry patch

# output
Bumping version from 0.2.0-alpha.0 to 0.2.0

# use prepatch
user@path$ poetry version prepatch

# output
Bumping version from 0.2.0 to 0.2.1-alpha.0
```

# Disclaimer Notice

This material was prepared as an account of work sponsored by an agency of the
United States Government.  Neither the United States Government nor the United
States Department of Energy, nor Battelle, nor any of their employees, nor any
jurisdiction or organization that has cooperated in the development of these
materials, makes any warranty, express or implied, or assumes any legal
liability or responsibility for the accuracy, completeness, or usefulness or any
information, apparatus, product, software, or process disclosed, or represents
that its use would not infringe privately owned rights.

Reference herein to any specific commercial product, process, or service by
trade name, trademark, manufacturer, or otherwise does not necessarily
constitute or imply its endorsement, recommendation, or favoring by the United
States Government or any agency thereof, or Battelle Memorial Institute. The
views and opinions of authors expressed herein do not necessarily state or
reflect those of the United States Government or any agency thereof.
