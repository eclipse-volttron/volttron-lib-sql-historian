[![Eclipse VOLTTRON™](https://img.shields.io/badge/Eclips%20VOLTTRON--red.svg)](https://volttron.readthedocs.io/en/latest/)
![Python 3.10](https://img.shields.io/badge/python-3.10-blue.svg)
![Python 3.11](https://img.shields.io/badge/python-3.11-blue.svg)
[![pypi version](https://img.shields.io/pypi/v/volttron-lib-sql-historian.svg)](https://pypi.org/project/volttron-lib-sql-historian/)
![Passing?](https://github.com/VOLTTRON/volttron-lib-sql-historian/actions/workflows/run-tests.yml/badge.svg)

Generic SQL Historian library that can be used to implement a historian agent with a relational database backend.
This library cannot be installed as a VOLTTRON agent as is. Only a concrete database implementation package such as
[sqlite-historian](https://github.com/eclipse-volttron/volttron-sqlitehistorian) that depends on this library can be
installed as a VOLTTRON agent.

## Requirements

 - Python >= 3.10

## Installation

This library can be installed into a running VOLTTRON instance using 

```bash
vctl install-lib volttron-lib-sql-historian
```

To remove it later, use 

```bash
vctl remove-lib volttron-lib-sql-historian
```
However, this is not usually necessary. Any
historian agent that uses this library will automatically install it as part of its installation. For example,
installing [SQLiteHistorian](https://github.com/eclipse-volttron/volttron-sqlite-historian) will automatically install
volttron-lib-sql-historian into the same VOLTTRON environment.

## Development

Please see the following for contributing guidelines [contributing](https://github.com/eclipse-volttron/volttron-core/blob/develop/CONTRIBUTING.md).

Please see the following helpful guide about [developing modular VOLTTRON agents](https://github.com/eclipse-volttron/volttron-core/blob/develop/DEVELOPING_ON_MODULAR.md)

To create a new relational database based historian by extending this library, subclass
[DBDriver](https://github.com/eclipse-volttron/volttron-lib-sql-historian/blob/develop/src/historian/sql/basedb.py#L79).
The subclass should be in a module historian.<database_type>.<database_type>functs.py for it to be dynamically loaded
by the base DBDriver. Please refer to [SQLiteHistorian](https://github.com/eclipse-volttron/volttron-sqlitehistorian) as
an example

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
