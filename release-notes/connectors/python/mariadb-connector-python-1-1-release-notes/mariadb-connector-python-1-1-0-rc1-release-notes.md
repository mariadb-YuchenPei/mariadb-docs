# Connector/Python 1.1.0 RC1 Release Notes

{% include "../../../.gitbook/includes/latest-python.md" %}

<a href="https://mariadb.com/downloads/connectors/connectors-data-access/python-connector/" class="button primary">Download</a> <a href="mariadb-connector-python-1-1-0-rc1-release-notes.md" class="button secondary">Release Notes</a> <a href="../changelogs/mariadb-connector-python-11-changelogs/mariadb-connector-python-110-rc1-changelog.md" class="button secondary">Changelog</a> <a href="https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/connectors-quickstart-guides/connector-python-guide" class="button secondary">Connector/Python Overview</a>

**Release date:** 7 Apr 2022

This is a [_**Release Candidate (RC)**_](../../../community-server/about/release-criteria.md) release of MariaDB Connector/Python.

{% hint style="danger" %}
**Do not use non-stable (non-GA) releases in production!**
{% endhint %}

**For a description of this library see the** [**MariaDB Connector/Python documentation**](https://mariadb-corporation.github.io/mariadb-connector-python/index.html) **.**

MariaDB Connector/Python enables python programs to access MariaDB and MySQL databases, using an API which is compliant with the Python DB API 2.0 (PEP-249). It is written in C and uses MariaDB Connector/C client library for client server communication.

## Notable changes

* [CONPY-44](https://jira.mariadb.org/browse/CONPY-44): Added support for simple failover (Requires MariaDB Connector/C 3.3)
* [CONPY-184](https://jira.mariadb.org/browse/CONPY-184): Display status of objects in string representation (cursor, connection, pool)

## Bug fixes

* [CONPY-88](https://jira.mariadb.org/browse/CONPY-88): Get additional information in fieldinfo: cursor->description() now contains 3 additional elements: table\_name, orginal column name and original table name
* [CONPY-187](https://jira.mariadb.org/browse/CONPY-187): Fixed wrong detection of bulk capabilities
* [CONPY-188](https://jira.mariadb.org/browse/CONPY-188): If a connection or cursor is closed, an exception is returned whether a method or property of a closed object is called
* [CONPY-189](https://jira.mariadb.org/browse/CONPY-189): Fixed build with Visual Studio 2022
* [CONPY-178](https://jira.mariadb.org/browse/CONPY-178): If a cursor was not properly cleared (all results weren't fetched) the clear\_result routine has to free result sets only if field\_count > 0
* [CONPY-175](https://jira.mariadb.org/browse/CONPY-175): Allocate heap memory for string escaping

## Installation

MariaDB Connector/Python 1.1.0-rc1 can be obtained from central python repository:

```bash
pip3 install --pre mariadb
```

## Changelog

For a list of changes made in this release, with links to detailed information\
on each push, see the [changelog](../changelogs/mariadb-connector-python-11-changelogs/mariadb-connector-python-110-rc1-changelog.md).

## Links:

* [Documentation](https://mariadb-corporation.github.io/mariadb-connector-python/index.htmli)
* [Bug tracker](https://jira.mariadb.org)
* Sources are hosted on [Github](https://github.com/mariadb-corporation/mariadb-connector-python)

**Do not use non-stable (non-GA) releases in production!**

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
