# Connector/J 3.3.2 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://mariadb.com/downloads/connectors/connectors-data-access/java8-connector)[Release Notes](mariadb-connector-j-3-3-2-release-notes.md)[Changelog](../changelogs/3.3/mariadb-connector-j-3-3-2-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 19 Dec 2023

MariaDB Connector/J 3.3.2 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release, and will replace 3.2 as the maintenance releases.

**For an overview of MariaDB Connector/J see the**[**About MariaDB Connector/J**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md) **page**

## Bugs Fixed

* [CONJ-1117](https://jira.mariadb.org/browse/CONJ-1117) new option `returnMultiValuesGeneratedIds` for connector 2.x compatibility, so getGeneratedKeys() return all ids of multi-value inserts
* [CONJ-1140](https://jira.mariadb.org/browse/CONJ-1140) regression caussing ClassCastException on DatabaseMetaData when use with option defaultFetchSize set
* [CONJ-1129](https://jira.mariadb.org/browse/CONJ-1129) Metadata.getPrimaryKeys table comparison using like in place of strict equality
* [CONJ-1130](https://jira.mariadb.org/browse/CONJ-1130) ensuring batch parameter are cleared after SQL Failure
* [CONJ-1131](https://jira.mariadb.org/browse/CONJ-1131) NullPointerException when Calling getGeneratedKeys() after an SQL Failure
* [CONJ-1132](https://jira.mariadb.org/browse/CONJ-1132) Ensuring reseting result for getUpdateCount() after an SQL Failure
* [CONJ-1135](https://jira.mariadb.org/browse/CONJ-1135) ensuring BULK command not used when using INSERT ON DUPLICATE KEY UPDATE in order to always have unique affected rows by default
* [CONJ-1136](https://jira.mariadb.org/browse/CONJ-1136) wrong decoding for Resultset.getByte() results for binary varchar fields
* [CONJ-1137](https://jira.mariadb.org/browse/CONJ-1137) ensuring never having NPE in OkPacket when setting auto commit
* [CONJ-1138](https://jira.mariadb.org/browse/CONJ-1138) Inconsistency in Behavior of PreparedStatement After closeOnCompletion() Between MariaDB and MySQL\
  Connectors
* [CONJ-1049](https://jira.mariadb.org/browse/CONJ-1049) Metadata getTableTypes result was not ordered by TABLE\_TYPE

## Changelog

For a complete list of changes made in MariaDB Connector/J 3.3.2, with links to detailed\
information on each push, see the [changelog](../changelogs/3.3/mariadb-connector-j-3-3-2-changelog.md).

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
