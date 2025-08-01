# Connector/C++ 1.1.5 Release Notes

The most recent [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release of MariaDB Connector/C++ is:[**MariaDB Connector/C++ 1.1.6**](mariadb-connector-cpp-1-1-6-release-notes.md)

[Download Now](https://mariadb.com/downloads/connectors/connectors-data-access/cpp-connector)

**Release date:** 2024-08-27

This is a [_**Stable (GA)**_](../../../community-server/about/release-criteria.md) release of MariaDB Connector/C++.

This is a GA release of the [MariaDB Connector/C++ 1.1](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-cpp/README.md) series, the interface between C++ applications, and MariaDB Server. MariaDB Connector/C++ enables development of C++ applications using a JDBC-based API, which is also used by MariaDB Connector/JDBC.

MariaDB Connector/C++ in its current implementation uses the MariaDB protocol via the MariaDB Connector/C API. Connector/C 3.3.11 is used in this release.

## Bugs Fixed

* `getMoreResults()` could pick other statement's result ([CONCPP-132](https://jira.mariadb.org/browse/CONCPP-132))
* Driver failed to cache multiple results, i.e., if application executed a query while other query hadn't iterated thru all its results, the connection would get out of sync ([CONCPP-133](https://jira.mariadb.org/browse/CONCPP-133))

## Installation

* [Install MariaDB Connector/C++](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-cpp/install-mariadb-connector-cpp)

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
