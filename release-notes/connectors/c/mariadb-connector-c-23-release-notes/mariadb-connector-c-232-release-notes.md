# Connector/C 2.3.2 Release notes

The most recent [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release of MariaDB Connector/C is:[**MariaDB Connector/C 3.4.5**](../mariadb-connector-c-3-4-release-notes/mariadb-connector-c-3-4-5-release-notes.md)

[Download](https://downloads.mariadb.org/connector-c/2.3.2)[Release Notes](mariadb-connector-c-232-release-notes.md)[Changelog](../changelogs/mariadb-connector-c-23-changelogs/mariadb-connector-c-232-changelog.md)[About MariaDB Connector/C](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-c/README.md)

**Release date:** 18 Jan 2017

This is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release of the MariaDB\
Connector/C, formerly known as MariaDB Client Library for C.

**For a description of this library see the**[**MariaDB Connector/C**](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-c) **page.**

## New features

Plugin API interface change: Changed the interface of authentication plugins, so plugins from C/C 3.0 (like GSSAPI/Kerberos plugin) can be used with Connector/C 2.3

## Notable Bug fixes

* [CONC-205](https://jira.mariadb.org/browse/CONC-205): Any field going after a TEXT field in the selecion list is fetched incorrectly (prepared statements)
* [CONC-198](https://jira.mariadb.org/browse/CONC-198): Can't use more than one statement per connection
* [CONC-223](https://jira.mariadb.org/browse/CONC-223): Add client support for missing collations
* [MDEV-10894](https://jira.mariadb.org/browse/MDEV-10894): big endian conversion
* fixed packet\_length in dialog plugin
* fixed include of my\_stmt.h
* fixed wrong behavior of read\_timeout
* fixed timeout for non-blocking operations
* fixed output for plugindir in mariadb\_config
* removed extra check for non binary result types in fetch\_bin (prepared statements)

For a list of changes made in this release, with links to detailed\
information on each push, see the[changelog](../changelogs/mariadb-connector-c-23-changelogs/mariadb-connector-c-232-changelog.md).

{% include "../../../.gitbook/includes/announce.md" %}

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
