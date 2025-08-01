# MariaDB 10.5.27 Release Notes

{% include "../../../.gitbook/includes/latest-10-5.md" %}

<a href="https://downloads.mariadb.org/mariadb/10.5.27/" class="button primary">Download</a> <a href="mariadb-10-5-27-release-notes.md" class="button secondary">Release Notes</a> <a href="../../changelogs/changelogs-mariadb-105-series/mariadb-10-5-27-changelog.md" class="button secondary">Changelog</a> <a href="what-is-mariadb-105.md" class="button secondary">Overview of 10.5</a>

**Release date:** 1 Nov 2024

[MariaDB 10.5](what-is-mariadb-105.md) is a previous _stable_ series of MariaDB, [maintained until](https://mariadb.org/about/#maintenance-policy) June 2025. It is an evolution of [MariaDB 10.4](../release-notes-mariadb-10-4-series/what-is-mariadb-104.md) with several entirely new features not found anywhere else and with backported and reimplemented features from MySQL.

[MariaDB 10.5.27](mariadb-10-5-27-release-notes.md) is a [_**Stable (GA)**_](../../about/release-criteria.md) release.

Thanks, and enjoy MariaDB!

## Notable Items

### Storage Engines

#### [InnoDB](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb)

* Fix MariaDB crash with SIGILL because the OS does not support AVX512 ([MDEV-34565](https://jira.mariadb.org/browse/MDEV-34565))
* Fix innodb.innodb-lock-inherit-read\_commited failure with timeout ([MDEV-33106](https://jira.mariadb.org/browse/MDEV-33106))

#### [Spider](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/spider)

* Fix server crash when calling [spider UDF](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/spider/spider-functions) after [aria\_encrypt\_tables](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/aria/aria-system-variables#aria_encrypt_tables) is enabled ([MDEV-34682](https://jira.mariadb.org/browse/MDEV-34682))
* SELECT MIN on Spider table no longer returns more rows than expected ([MDEV-26345](https://jira.mariadb.org/browse/MDEV-26345))
* Fix Spider group by handler wrong result on order by aggregate ([MDEV-29546](https://jira.mariadb.org/browse/MDEV-29546))

### Optimizer

* Fix crash caused by query containing constant having clause ([MDEV-23983](https://jira.mariadb.org/browse/MDEV-23983))

### Data Definition - Alter Table

* Fix InnoDB crash under Windows Subsystem for Linux on ALTER TABLE or OPTIMIZE TABLE ([MDEV-34938](https://jira.mariadb.org/browse/MDEV-34938))
* Modification of the column now correctly checks foreign key constraint ([MDEV-34392](https://jira.mariadb.org/browse/MDEV-34392))
* Fix incorrect NULL value handling for instantly dropped BLOB columns ([MDEV-35122](https://jira.mariadb.org/browse/MDEV-35122))

### Galera

* Galera updated to 26.4.20
* Fix server crash when setting wsrep\_cluster\_address after adding invalid value to wsrep\_allowlist table ([MDEV-31173](https://jira.mariadb.org/browse/MDEV-31173))
* Fix INSERT...SELECT' on MyISAM table suddenly replicated by alera ([MDEV-34647](https://jira.mariadb.org/browse/MDEV-34647))
* Fix galera\_ssl\_reload failure with warning message ([MDEV-32778](https://jira.mariadb.org/browse/MDEV-32778))
* When InnoDB gets an assertion failure, WSREP layer is now handled gracefully ([MDEV-32363](https://jira.mariadb.org/browse/MDEV-32363))

### Backup

* Recovery now correctly notes some log corruption ([MDEV-34802](https://jira.mariadb.org/browse/MDEV-34802))
* Can now selectively restore sequences using innodb tables from backup ([MDEV-32350](https://jira.mariadb.org/browse/MDEV-32350))

### General

* As per the [MariaDB Deprecation Policy](../../about/platform-deprecation-policy.md), this will be the last release of [MariaDB 10.5](what-is-mariadb-105.md) for SLES 12, and Windows 11 22H2
* [mariadbd](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/starting-and-stopping-mariadb/mariadbd) no longer hangs on startup when --init-file target does not exist ([MDEV-34814](https://jira.mariadb.org/browse/MDEV-34814))
* LOAD DATA INFILE with geometry data no longer fails ([MDEV-34883](https://jira.mariadb.org/browse/MDEV-34883))
* Fix heap-use-after-free in group\_concat with compressed or GIS columns ([MDEV-16699](https://jira.mariadb.org/browse/MDEV-16699))
* Trigger now works correctly with bulk update ([MDEV-34718](https://jira.mariadb.org/browse/MDEV-34718))
* Fix assertion failure in find\_producing\_item upon a query from a view ([MDEV-35276](https://jira.mariadb.org/browse/MDEV-35276))
* Add new setting, [--quick-max-column-width](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/clients-and-utilities/mariadb-client/mariadb-command-line-client#-quick-max-column-widthn) to the mariadb client for use in --quick mode ([MDEV-34704](https://jira.mariadb.org/browse/MDEV-34704))

### Security

* Fixes for the following [security vulnerabilities](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/security/securing-mariadb/security):
  * CVE-`-``#`

## Changelog

For a complete list of changes made in [MariaDB 10.5.27](mariadb-10-5-27-release-notes.md), with links to detailed\
information on each push, see the [changelog](../../changelogs/changelogs-mariadb-105-series/mariadb-10-5-27-changelog.md).

## Contributors

For a full list of contributors to [MariaDB 10.5.27](mariadb-10-5-27-release-notes.md), see the [MariaDB Foundation release announcement](https://mariadb.org/mariadb-11-4-4-11-2-6-10-11-10-10-6-20-and-10-5-27-now-available/).

{% include "../../../.gitbook/includes/announce.md" %}

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
