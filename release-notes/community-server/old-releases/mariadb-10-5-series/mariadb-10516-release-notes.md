# MariaDB 10.5.16 Release Notes

{% include "../../../.gitbook/includes/latest-10-5.md" %}

<a href="https://downloads.mariadb.org/mariadb/10.5.16/" class="button primary">Download</a> <a href="mariadb-10516-release-notes.md" class="button secondary">Release Notes</a> <a href="../../changelogs/changelogs-mariadb-105-series/mariadb-10516-changelog.md" class="button secondary">Changelog</a> <a href="what-is-mariadb-105.md" class="button secondary">Overview of 10.5</a>

**Release date:** 20 May 2022

[MariaDB 10.5](what-is-mariadb-105.md) is a previous _stable_ series of MariaDB. It is an evolution\
of [MariaDB 10.4](../release-notes-mariadb-10-4-series/what-is-mariadb-104.md) with several entirely new features not found anywhere else\
and with backported and reimplemented features from MySQL.

[MariaDB 10.5.16](mariadb-10516-release-notes.md) is a [_**Stable (GA)**_](../../about/release-criteria.md) release.

Thanks, and enjoy MariaDB!

## Notable Items

### InnoDB

* [innodb\_disallow\_writes](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_disallow_writes) removed ([MDEV-25975](https://jira.mariadb.org/browse/MDEV-25975))
* InnoDB gap locking fixes ([MDEV-20605](https://jira.mariadb.org/browse/MDEV-20605), [MDEV-28422](https://jira.mariadb.org/browse/MDEV-28422))
* InnoDB performance improvements ([MDEV-27557](https://jira.mariadb.org/browse/MDEV-27557), [MDEV-28185](https://jira.mariadb.org/browse/MDEV-28185))

### Replication

* Server initialization time gtid\_slave\_pos purge related reason of crashing in binlog background thread is removed ([MDEV-26473](https://jira.mariadb.org/browse/MDEV-26473))
* Shutdown of the semisync master can't produce inconsistent state anymore ([MDEV-11853](https://jira.mariadb.org/browse/MDEV-11853))
* Binlogs disappear after rsync IST ([MDEV-28583](https://jira.mariadb.org/browse/MDEV-28583))
* master crash is eliminated in compressed semisync replication protocol with packet counting amendment ([MDEV-25580](https://jira.mariadb.org/browse/MDEV-25580))
* OPTIMIZE on a sequence does not cause counterfactual ER\_BINLOG\_UNSAFE\_STATEMENT anymore ([MDEV-24617](https://jira.mariadb.org/browse/MDEV-24617))
* Automatically generated Gtid\_log\_list\_event is made to recognize within replication event group as a formal member ([MDEV-28550](https://jira.mariadb.org/browse/MDEV-28550))
* [Replication unsafe](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/standard-replication/unsafe-statements-for-statement-based-replication) [INSERT .. ON DUPLICATE KEY UPDATE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/inserting-loading-data/insert-on-duplicate-key-update) using two or more unique key values at a time with [MIXED format binlogging](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/server-monitoring-logs/binary-log/binary-log-formats#mixed-logging) is corrected ([MDEV-28310](https://jira.mariadb.org/browse/MDEV-28310))
* [Replication unsafe](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/standard-replication/unsafe-statements-for-statement-based-replication) [INSERT .. ON DUPLICATE KEY UPDATE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/inserting-loading-data/insert-on-duplicate-key-update) stops issuing unnecessary "Unsafe statement" with [MIXED binlog format](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/server-monitoring-logs/binary-log/binary-log-formats#mixed-logging) ([MDEV-21810](https://jira.mariadb.org/browse/MDEV-21810))
* Incomplete replication event groups are detected to error out by the slave IO thread ([MDEV-27697](https://jira.mariadb.org/browse/MDEV-27697))
* [mysqlbinlog --stop-never --raw](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/clients-and-utilities/logging-tools/mariadb-binlog/mariadb-binlog-options) now flushes the result file to disk after each processed event so the file can be listed with the actual bytes ([MDEV-14608](https://jira.mariadb.org/browse/MDEV-14608))

### Backup

* Incorrect binlogs after Galera SST using rsync and [mariadb-backup](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/backup-and-restore/mariadb-backup) ([MDEV-27524](https://jira.mariadb.org/browse/MDEV-27524))
* [mariadb-backup](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/backup-and-restore/mariadb-backup) does not detect multi-source replication slave ([MDEV-21037](https://jira.mariadb.org/browse/MDEV-21037))
* Useless warning "InnoDB: Allocated tablespace ID for , old maximum was 0" during backup stage ([MDEV-27343](https://jira.mariadb.org/browse/MDEV-27343))
* [mariadb-backup](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/backup-and-restore/mariadb-backup) prepare fails for incrementals if a new schema is created after full backup is taken ([MDEV-28446](https://jira.mariadb.org/browse/MDEV-28446))

### Optimizer

* A SEGV in Item\_field::used\_tables/update\_depend\_map\_for\_order... ([MDEV-26402](https://jira.mariadb.org/browse/MDEV-26402))
* ANALYZE FORMAT=JSON fields are incorrect for UNION ALL queries ([MDEV-27699](https://jira.mariadb.org/browse/MDEV-27699))
* Subquery in an UPDATE query uses full scan instead of range ([MDEV-22377](https://jira.mariadb.org/browse/MDEV-22377))
* Assertion \`item1->type() == Item::FIELD\_ITEM ... ([MDEV-19398](https://jira.mariadb.org/browse/MDEV-19398))
* Server crashes in Expression\_cache\_tracker::fetch\_current\_stats ([MDEV-28268](https://jira.mariadb.org/browse/MDEV-28268))
* MariaDB server crash at Item\_subselect::init\_expr\_cache\_tracker ([MDEV-26164](https://jira.mariadb.org/browse/MDEV-26164), [MDEV-26047](https://jira.mariadb.org/browse/MDEV-26047))
* Crash with union of my\_decimal type in ORDER BY clause ([MDEV-25994](https://jira.mariadb.org/browse/MDEV-25994))
* SIGSEGV in st\_join\_table::cleanup ([MDEV-24560](https://jira.mariadb.org/browse/MDEV-24560))
* Assertion \`!eliminated' failed in Item\_subselect::exec ([MDEV-28437](https://jira.mariadb.org/browse/MDEV-28437))

### General

* Server [error messages](https://app.gitbook.com/s/WCInJQ9cmGjq1lsTG91E/development-articles/general-info/mariadb-fault-finding/mariadb-error-messages) are [now available in Chinese](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/data-types/string-data-types/character-sets/internationalization-and-localization/setting-the-language-for-error-messages) ([MDEV-28227](https://jira.mariadb.org/browse/MDEV-28227))
* For RHEL/CentOS 7, non x86\_64 architectures are no longer supported upstream and so our support will also be dropped with this release
* As per the [MariaDB Deprecation Policy](../../about/platform-deprecation-policy.md), this will be the last release of [MariaDB 10.5](what-is-mariadb-105.md) for Debian 9 "Stretch", Ubuntu 21.10 "Impish", and Fedora 34

### Security

* Fixes for the following [security vulnerabilities](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/security/securing-mariadb/security):
  * [CVE-2021-46669](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-46669)
  * [CVE-2022-27376](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27376)
  * [CVE-2022-27377](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27377)
  * [CVE-2022-27378](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27378)
  * [CVE-2022-27379](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27379)
  * [CVE-2022-27380](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27380)
  * [CVE-2022-27381](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27381)
  * [CVE-2022-27382](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27382)
  * [CVE-2022-27383](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27383)
  * [CVE-2022-27384](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27384)
  * [CVE-2022-27386](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27386)
  * [CVE-2022-27387](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27387)
  * [CVE-2022-27444](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27444)
  * [CVE-2022-27445](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27445)
  * [CVE-2022-27446](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27446)
  * [CVE-2022-27447](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27447)
  * [CVE-2022-27448](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27448)
  * [CVE-2022-27449](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27449)
  * [CVE-2022-27451](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27451)
  * [CVE-2022-27452](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27452)
  * [CVE-2022-27455](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27455)
  * [CVE-2022-27456](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27456)
  * [CVE-2022-27457](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27457)
  * [CVE-2022-27458](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-27458)
  * [CVE-2022-32087](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-32087)
  * [CVE-2022-32086](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-32086)
  * [CVE-2022-32085](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-32085)
  * [CVE-2022-32083](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-32083)
  * [CVE-2022-32088](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-32088)

## Changelog

For a complete list of changes made in [MariaDB 10.5.16](mariadb-10516-release-notes.md), with links to detailed\
information on each push, see the [changelog](../../changelogs/changelogs-mariadb-105-series/mariadb-10516-changelog.md).

## Contributors

For a full list of contributors to [MariaDB 10.5.16](mariadb-10516-release-notes.md), see the [MariaDB Foundation release announcement](https://mariadb.org/mariadb-10-9-1-10-8-3-10-7-4-10-6-8-10-5-16-10-4-25-10-3-35-and-10-2-44-now-available/).

{% include "../../../.gitbook/includes/announce.md" %}

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
