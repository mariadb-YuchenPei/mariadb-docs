# MariaDB 10.4.26 Release Notes

The most recent release of [MariaDB 10.4](what-is-mariadb-104.md) is:[**MariaDB 10.4.34**](mariadb-10-4-34-release-notes.md) Stable (GA) [Download Now](https://downloads.mariadb.org/mariadb/10.4.34/)

[Download 10.4.26](https://downloads.mariadb.org/mariadb/10.4.26/)[Release Notes](mariadb-10426-release-notes.md)[Changelog](../../changelogs/changelogs-mariadb-10-4-series/mariadb-10426-changelog.md)[Overview of 10.4](what-is-mariadb-104.md)

**Release date:** 15 Aug 2022

[MariaDB 10.4](what-is-mariadb-104.md) is a previous _stable_ series of MariaDB. It is an evolution\
of [MariaDB 10.3](../release-notes-mariadb-10-3-series/what-is-mariadb-103.md) with several entirely new features not found anywhere else\
and with backported and reimplemented features from MySQL.

[MariaDB 10.4.26](mariadb-10426-release-notes.md) is a [_**Stable (GA)**_](../../about/release-criteria.md) release.

**For an overview of** [**MariaDB 10.4**](what-is-mariadb-104.md) **see the**[**What is MariaDB 10.4?**](what-is-mariadb-104.md) **page.**

Thanks, and enjoy MariaDB!

## Notable Items

### InnoDB

* InnoDB corruption due to lack of file locking ([MDEV-28495](https://jira.mariadb.org/browse/MDEV-28495))
* FULLTEXT search with apostrophe, and mandatory words ([MDEV-20797](https://jira.mariadb.org/browse/MDEV-20797))
* ALTER TABLE IMPORT TABLESPACE corrupts an encrypted table ([MDEV-28779](https://jira.mariadb.org/browse/MDEV-28779))
* ALTER TABLE wrong-result fix ([MDEV-26294](https://jira.mariadb.org/browse/MDEV-26294))

### Replication

* ER\_SLAVE\_INCIDENT error is specified now on slave to be seen with SHOW-SLAVE-STATUS ([MDEV-21087](https://jira.mariadb.org/browse/MDEV-21087))
* INCIDENT\_EVENT is no longer binlogged when a being logged transaction can be safely rolledback ([MDEV-21443](https://jira.mariadb.org/browse/MDEV-21443))
* sequences related row-format events are made to correspond to binlog\_row\_image ([MDEV-28487](https://jira.mariadb.org/browse/MDEV-28487))

### Galera

* [Galera](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/galera-cluster/README.md) updated to 26.4.12
* Possible to write/update with read\_only=ON and not a SUPER privilege ([MDEV-28546](https://jira.mariadb.org/browse/MDEV-28546))
* Node crashes with Transport endpoint is not connected mysqld got signal 6 ([MDEV-25068](https://jira.mariadb.org/browse/MDEV-25068))
* Galera4 not able to report proper wsrep\_incoming\_addresses ([MDEV-20627](https://jira.mariadb.org/browse/MDEV-20627))

### Optimizer

* Server crash in JOIN\_CACHE::free or in copy\_fields ([MDEV-23809](https://jira.mariadb.org/browse/MDEV-23809))
  * Queries that use DISTINCT and an always-constant function like COLLATION(aggegate\_func(...)) could cause a server crash. Note that COLLATION() is a special function - its value is constant even if its argument is not costant.
* Crash when using ANY predicand with redundant subquery in GROUP BY clause ([MDEV-29139](https://jira.mariadb.org/browse/MDEV-29139))
  * A query with a subuquery in this form could cause a crash:

```sql
... ANY (SELECT ... GROUP BY (SELECT redundant_subselect_here)) ...
```

* MariaDB Server SEGV on INSERT .. SELECT ([MDEV-26427](https://jira.mariadb.org/browse/MDEV-26427))
  * Certain queries in form "INSERT ... SELECT with\_aggregate\_or\_window\_func" could cause a crash.
* restore\_prev\_nj\_state() doesn't update cur\_sj\_inner\_tables correctly ([MDEV-28749](https://jira.mariadb.org/browse/MDEV-28749))
  * Subquery semi-join optimization could miss LooseScan or FirstMatch strategies for certain queries.
* Optimizer uses all partitions after upgrade to 10.3 ([MDEV-28246](https://jira.mariadb.org/browse/MDEV-28246))
  * For multi-table UPDATE or DELETE queries, the optimizer failed to apply Partition Pruning optimization for the table that is updated or deleted from.

### CONNECT

* [CONNECT Engine](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/connect) now supports [INSERT IGNORE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/inserting-loading-data/insert-ignore) with [Mysql Table type](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/connect/connect-table-types/connect-mysql-table-type-accessing-mysqlmariadb-tables) ([MDEV-27766](https://jira.mariadb.org/browse/MDEV-27766))

### mysql Client

* New [mysql client](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/clients-and-utilities/mariadb-client/mysql-command-line-client) option, `-enable-cleartext-plugin`. Option does not do anything, and is for MySQL-compatibility purposes only.

### General

* Crash in [JSON\_EXTRACT](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/special-functions/json-functions/json_extract) ([MDEV-29188](https://jira.mariadb.org/browse/MDEV-29188))
* ALTER TABLE ALGORITHM=NOCOPY does not work after upgrade ([MDEV-28727](https://jira.mariadb.org/browse/MDEV-28727))
* Server crash upon CREATE VIEW with unknown column in ON condition ([MDEV-29088](https://jira.mariadb.org/browse/MDEV-29088))
* As per the [MariaDB Deprecation Policy](../../about/platform-deprecation-policy.md), this will be the last release of [MariaDB 10.4](what-is-mariadb-104.md) for Debian 10 "Buster" for ppc64el

### Security

* Fixes for the following [security vulnerabilities](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/security/securing-mariadb/security):
  * [CVE-2023-5157](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-5157)
  * [CVE-2022-32089](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-32089)
  * [CVE-2022-32081](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-32081)
  * [CVE-2018-25032](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-25032)
  * [CVE-2022-32091](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-32091)
  * [CVE-2022-32084](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-32084)
  * [CVE-2022-38791](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-38791)

## Changelog

For a complete list of changes made in [MariaDB 10.4.26](mariadb-10426-release-notes.md), with links to detailed\
information on each push, see the [changelog](../../changelogs/changelogs-mariadb-10-4-series/mariadb-10426-changelog.md).

## Contributors

For a full list of contributors to [MariaDB 10.4.26](mariadb-10426-release-notes.md), see the [MariaDB Foundation release announcement](https://mariadb.org/mariadb-10-8-4-10-7-5-10-6-9-10-5-17-10-4-26-and-10-3-36-now-available/).

{% include "../../../.gitbook/includes/announce.md" %}

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
