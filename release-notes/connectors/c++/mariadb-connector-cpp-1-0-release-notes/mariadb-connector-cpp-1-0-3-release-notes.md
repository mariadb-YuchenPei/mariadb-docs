# Connector/C++ 1.0.3 Release Notes

The most recent [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release of MariaDB Connector/C++ is:[**MariaDB Connector/C++ 1.1.6**](../mariadb-connector-cpp-1-1-release-notes/mariadb-connector-cpp-1-1-6-release-notes.md)

[Download Now](https://mariadb.com/downloads/connectors/connectors-data-access/cpp-connector)

**Release date:** 2024-01-08

This is a [_**Stable (GA)**_](../../../community-server/about/release-criteria.md) release of MariaDB Connector/C++.

**For a description of this library see the**[**MariaDB Connector/C++**](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-cpp) **page.**

[MariaDB Connector/C++](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-cpp/README.md) is the interface between C++ applications and MariaDB Server. MariaDB Connector/C++ enables development of C++ applications using a JDBC-based API, which is also used by MariaDB Connector/J.

MariaDB Connector/C++ implements the MySQL protocol using the MariaDB Connector/C API. This release depends on MariaDB Connector/C 3.3.8.

## Notable Changes

* A new static Connector/C++ library mariadbcpp-static.(lib|a) is included in the release packages.
  * Symlink libmariadbcpp.a is created on platforms other than Windows
  * To link against the static library MARIADB\_STATIC\_LINK needs to be defined during compilation. ([CONCPP-117](https://jira.mariadb.org/browse/CONCPP-117))
* Added support of connection attributes ([CONCPP-112](https://jira.mariadb.org/browse/CONCPP-112))
  * Attributes can be defined in the URL or in properties under the name connectionAttributes in the format

```c
connectionAttributes=attr1:value1,attr2:value2
```

* New option WITH\_UNIT\_TESTS to allow building the connector with or without tests ([CONCPP-102](https://jira.mariadb.org/browse/CONCPP-102))
  * New option BUILD\_TESTS\_ONLY can be used to only generate test projects
* Packages for Red Hat (rpm) and Debian/Ubuntu (deb) added

## Issues Fixed

* Possible crash during execution when a parameter is set with setByte ([CONCPP-116](https://jira.mariadb.org/browse/CONCPP-116))
* Minor issues related to compilation of the connector, like errors/warnings when enabling more compiler warnings ([CONCPP-18](https://jira.mariadb.org/browse/CONCPP-18)) ([CONCPP-110](https://jira.mariadb.org/browse/CONCPP-110))

## Installation

[Install MariaDB Connector/C++](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-cpp/install-mariadb-connector-cpp)

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
