# Connector/C 2.2.3 Release notes

The most recent [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release of MariaDB Connector/C is:[**MariaDB Connector/C 3.4.5**](../mariadb-connector-c-3-4-release-notes/mariadb-connector-c-3-4-5-release-notes.md)

[Download](https://downloads.mariadb.org/connector-c/2.2.3)[Release Notes](mariadb-connector-c-223-release-notes.md)[Changelog](../changelogs/mariadb-connector-c-22-changelogs/mariadb-connector-c-223-changelog.md)[About MariaDB Connector/C](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-c/README.md)

**Release date:** 26 Apr 2016

This is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release of the MariaDB\
Connector/C, formerly known as MariaDB Client Library for C.

**For a description of this library see the**[**MariaDB Connector/C**](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-c) **page.**

## Notable Bug fixes

* [CONC-167](https://jira.mariadb.org/browse/CONC-167): fix crash when fetching MYSQL\_TYPE\_BIT data. MYSQL\_TYPE\_BIT has no fixed packlength, so net\_field\_length should be checked instead.
* [CONC-169](https://jira.mariadb.org/browse/CONC-169): Memory corruption in mariadb\_dyncol\_unpack
* [CONC-168](https://jira.mariadb.org/browse/CONC-168): String conversion of timestamps is broken: When converting datetime value with microseconds to string (binary protocol) number of decimal places was ignored. Thanks to Patrick Huesmann for providing a fix.
* OpenSSL: remove warnings when using OPENSSL\_NO\_DEPRECATED versions
* [CONC-163](https://jira.mariadb.org/browse/CONC-163): mysql->info returns garbage if no row was updated.
* [CONC-161](https://jira.mariadb.org/browse/CONC-161): Increase user name length to 128
* [CONC-160](https://jira.mariadb.org/browse/CONC-160): field metadata doesn't show NUM\_FLAG for NEWDECIMAL columns
* [CONC-156](https://jira.mariadb.org/browse/CONC-156): Connector/C build fails on FreeBSD due to not including necessary header. Thanks to Andie H. Hwang for providing this patch!
* [CONC-155](https://jira.mariadb.org/browse/CONC-155): return trailing zero when fetching from binary columns into string
* [CONC-154](https://jira.mariadb.org/browse/CONC-154): set stmt->state to MYSQL\_STMT\_FETCH\_DONE if result set is empty (nothing to fetch) or madb\_stmt\_reset was called

## Changelog

For a list of changes made in this release, with links to detailed\
information on each push, see the[changelog](../changelogs/mariadb-connector-c-22-changelogs/mariadb-connector-c-223-changelog.md).

{% include "../../../.gitbook/includes/announce.md" %}

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
