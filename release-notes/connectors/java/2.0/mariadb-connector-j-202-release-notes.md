# Connector/J 2.0.2 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/2.0.2/)[Release Notes](mariadb-connector-j-202-release-notes.md)[Changelog](../changelogs/2.0/mariadb-connector-j-202-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 7 Jun 2017

MariaDB Connector/J 2.0.2 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_\
release.

**For an overview of MariaDB Connector/J see the**[**About MariaDB Connector/J**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md) **page**

### Bug

* [CONJ-490](https://jira.mariadb.org/browse/CONJ-490) - DataSource connectTimeout is in second, but was set on socket timeout that is in milliseconds
* [CONJ-481](https://jira.mariadb.org/browse/CONJ-481) - option "useServerPrepStmts" : Possible Buffer overrun reading ResultSet
* [CONJ-470](https://jira.mariadb.org/browse/CONJ-470) - option "rewriteBatchedStatements" : Error when executing SQL contains "values" that aren't inserts
* [CONJ-477](https://jira.mariadb.org/browse/CONJ-477) - option "usePipelineAuth" : incompatibility with aurora. Now automatically disabled when aurora is detected
* [CONJ-479](https://jira.mariadb.org/browse/CONJ-479) - compatibility : ArrayIndexOutOfBoundsException on connect to MySQL 5.1.73
* [CONJ-480](https://jira.mariadb.org/browse/CONJ-480) - compatibility : Access denied error on connect to MySQL 5.1.73
* [CONJ-471](https://jira.mariadb.org/browse/CONJ-471) - metadata : DatabaseMetadata.getPrimaryKeys() return a null value for PK\_NAME, must always be 'PRIMARY'
* [CONJ-483](https://jira.mariadb.org/browse/CONJ-483) - metadata : Wrong content of DEFERRABILITY column in MariaDbDatabaseMetaData
* [CONJ-487](https://jira.mariadb.org/browse/CONJ-487) - No timeout exception on client PrepareStatement
* [CONJ-489](https://jira.mariadb.org/browse/CONJ-489) - log: javax.transaction.xa.XAException message error truncated ( near '0x )

### Task

* [CONJ-478](https://jira.mariadb.org/browse/CONJ-478) - Change CI tests to use maxscale 2.1 version
* [CONJ-482](https://jira.mariadb.org/browse/CONJ-482) - Connection.setNetworkTimeout don't throw exception if no executor
* [CONJ-488](https://jira.mariadb.org/browse/CONJ-488) - Use java.net.URL to read keyStore and trustStore again

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
