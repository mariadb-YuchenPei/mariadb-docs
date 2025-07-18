# Connector/C 3.2.6 Release Notes

[Download](https://mariadb.com/downloads/connectors)[Release Notes](mariadb-connector-c-326-release-notes.md)[Changelog](../changelogs/mariadb-connector-c-32-changelogs/mariadb-connector-c-326-changelog.md)[About MariaDB Connector/C](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-c/README.md)

**Release date:** 15 Feb 2022

This is a [_**Stable (GA)**_](../../../community-server/about/release-criteria.md) release of MariaDB\
Connector/C, formerly known as MariaDB Client Library for C.

**For a description of this library see the**[**MariaDB Connector/C**](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-c) **page.**

## Notable changes

* [MDEV-27304](https://jira.mariadb.org/browse/MDEV-27304): FIx detection of MariaDB Server: If the server was startet with --version option, it might not contain the 5.5.5 prefix
* [MDEV-16383](https://jira.mariadb.org/browse/MDEV-16383): Add mariadb\_config --libmysqld-libs option. If server package was built with embedded server and MariaDB Connector/C was built as subproject in server package mariadb\_config will display link option for embedded server
* [MDEV-27109](https://jira.mariadb.org/browse/MDEV-27109): create libmariadb.a as symlink to libmariadbclient.a
* Fixed length calculation of MYSQL\_TIME values in binary protocol
* Added support for ROWS\_EVENT\_V2 (binlog api). Special Thanls to Sutou Kouhei for his contribution

## Changelog

For a list of changes made in this release, with links to detailed information\
on each push, see the [changelog](../changelogs/mariadb-connector-c-32-changelogs/mariadb-connector-c-326-changelog.md).

{% include "../../../.gitbook/includes/announce.md" %}

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
