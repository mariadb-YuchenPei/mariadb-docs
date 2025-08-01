# MariaDB 10.2.30 Release Notes

The most recent release of [MariaDB 10.2](what-is-mariadb-102.md) is:[**MariaDB 10.2.44**](mariadb-10244-release-notes.md) Stable (GA) [Download Now](https://downloads.mariadb.org/mariadb/10.2.44/)

Note that this version contains an issue that disabled all events created by a server with a different server\_id. See [MDEV-21758](https://jira.mariadb.org/browse/MDEV-21758) for details.

[Download](https://downloads.mariadb.org/mariadb/10.2.30/)[Release Notes](mariadb-10230-release-notes.md)[Changelog](../../changelogs/changelogs-mariadb-102-series/mariadb-10230-changelog.md)[Overview of 10.2](what-is-mariadb-102.md)

**Release date:** 11 Dec 2019

[MariaDB 10.2](what-is-mariadb-102.md) is a previous stable series of MariaDB. It is an evolution\
of [MariaDB 10.1](../release-notes-mariadb-10-1-series/changes-improvements-in-mariadb-10-1.md) with several entirely new features not found anywhere else\
and with backported and reimplemented features from MySQL 5.6 and 5.7.

[MariaDB 10.2.30](mariadb-10230-release-notes.md) is a [_**Stable (GA)**_](../../about/release-criteria.md) release.

**For an overview of** [**MariaDB 10.2**](what-is-mariadb-102.md) **see the**[**What is MariaDB 10.2?**](what-is-mariadb-102.md) **page.**

Thanks, and enjoy MariaDB!

## Notable Changes

### General

* [MDEV-13492](https://jira.mariadb.org/browse/MDEV-13492): SEC\_E\_INVALID\_TOKEN when server sends large message during SSL handshake

### mariadb-backup

* [MDEV-18310](https://jira.mariadb.org/browse/MDEV-18310): Aria engine: Undo phase failed from incremental backup

### InnoDB

* [MDEV-20949](https://jira.mariadb.org/browse/MDEV-20949): Stop issuing '`row size`' error on DML
* [MDEV-20832](https://jira.mariadb.org/browse/MDEV-20832): Don't print "`row size too large`" warnings in error log if `innodb_strict_mode=OFF` and `log_warnings<=2`
* [MDEV-21024](https://jira.mariadb.org/browse/MDEV-21024): Remove redundant writes to the redo log
* [MDEV-21069](https://jira.mariadb.org/browse/MDEV-21069): Crash on `DROP TABLE` if the data file is corrupted
* some cleanup of AIO code, to better report errors

### Optimizer

* [MDEV-21044](https://jira.mariadb.org/browse/MDEV-21044): Wrong result when using a smaller size for sort buffer

### Replication

* [MDEV-19376](https://jira.mariadb.org/browse/MDEV-19376): `Repl_semi_sync_master::commit_trx` assertion failure
* Fixes for the following [security vulnerabilities](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/security/securing-mariadb/security):
  * CVE-\`-\`\`\`

Upgrading from 10.2 versions earlier than 10.2.17 is **highly recommended**\
for all [**Galera**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/galera/README.md) users due to bug [MDEV-12837](https://jira.mariadb.org/browse/MDEV-12837) which caused serious stability\
issues with earlier versions. See the bug issue page for more information.\
When upgrading from [MariaDB 10.2.16](mariadb-10216-release-notes.md) or earlier to [MariaDB 10.2.17](mariadb-10217-release-notes.md) or higher,\
running [mysql\_upgrade](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/clients-and-utilities/legacy-clients-and-utilities/mysql_upgrade) is **required** due to changes introduced in [MDEV-14637](https://jira.mariadb.org/browse/MDEV-14637).

## Changelog

For a complete list of changes made in [MariaDB 10.2.30](mariadb-10230-release-notes.md) with links to detailed\
information on each push, see the [changelog](../../changelogs/changelogs-mariadb-102-series/mariadb-10230-changelog.md).

## Contributors

For a full list of contributors to [MariaDB 10.2.30](mariadb-10230-release-notes.md), see the [MariaDB Foundation release announcement](https://mariadb.org/mariadb-10-4-11-10-3-21-and-10-2-30-now-available/).

{% include "../../../.gitbook/includes/announce.md" %}

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
