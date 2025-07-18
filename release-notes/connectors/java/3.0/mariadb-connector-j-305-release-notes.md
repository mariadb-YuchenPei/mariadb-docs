# Connector/J 3.0.5 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://mariadb.com/downloads/#connectors)[Release Notes](mariadb-connector-j-305-release-notes.md)[Changelog](../changelogs/3.0/mariadb-connector-j-305-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 25 May 2022

MariaDB Connector/J 3.0.5 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release.

**For an overview of MariaDB Connector/J see the**[**About MariaDB Connector/J**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md) **page**

### Notable Changes

* [CONJ-958](https://jira.mariadb.org/browse/CONJ-958) When multiple hosts are defined in the connection URL and no failover or load balancing mode is used, MariaDB Connector/J will try the hosts sequentially until a connection is successful.
* [CONJ-961](https://jira.mariadb.org/browse/CONJ-961) LOAD DATA LOCAL INFILE is now enabled by default on the client side, for compatibility with MariaDB Connector/J 2.7.
  * The connector validates that only the filename used in the original request will be provided, to prevent a man-in-the-middle change of the filename.
  * This might cause Batch performance regression. In case of non use of LOCAL DATA LOCAL INFILE, disable option `allowLocalInfile` explicitly can improve performance.

### Bugs Fixed

* [CONJ-956](https://jira.mariadb.org/browse/CONJ-956) ArrayIndexOutOfBoundsException when alias length > 250
* [CONJ-947](https://jira.mariadb.org/browse/CONJ-947) value after milliseconds precision lost when timestamp is encoded
* [CONJ-949](https://jira.mariadb.org/browse/CONJ-949) keep clientCertificateKeyStoreUrl and clientCertificateKeyStoreUrl aliases
* [CONJ-950](https://jira.mariadb.org/browse/CONJ-950) metadata TEXT/TINYTEXT/MEDIUMTEXT/LONGTEXT wrong column type and length
* [CONJ-954](https://jira.mariadb.org/browse/CONJ-954) java.time.OffsetDateTime not supported
* [CONJ-958](https://jira.mariadb.org/browse/CONJ-958) compatibility with 2.7: now loop through hosts when multiple host without failover mode
* [CONJ-959](https://jira.mariadb.org/browse/CONJ-959) java.time.Instant not supported
* [CONJ-962](https://jira.mariadb.org/browse/CONJ-962) resultset for negative TIME value return erronous LocalDateTime values
* [CONJ-965](https://jira.mariadb.org/browse/CONJ-965) better error message when not loading serverSslCert file
* [CONJ-967](https://jira.mariadb.org/browse/CONJ-967) clearParameters() breaks validity when using output parameters in stored procedures
* [CONJ-969](https://jira.mariadb.org/browse/CONJ-969) org.mariadb.jdbc.ClientPreparedStatement is missing a toString implementation, useful for logging

## Changelog

For a complete list of changes made in MariaDB Connector/J 3.0.5, with links to detailed\
information on each push, see the [changelog](../changelogs/3.0/mariadb-connector-j-305-changelog.md).

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
