# Release Notes for MariaDB Enterprise Server 10.6.12-8

MariaDB Enterprise Server 10.6.12-8 is a maintenance release of [MariaDB Enterprise Server](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/mariadb-enterprise-server/README.md) 10.6. This release includes a variety of fixes. Users of MariaDB Enterprise Server 10.6.12-7 are encouraged to upgrade. [Additional steps](release-notes-for-mariadb-enterprise-server-10-6-12-8.md#upgrade-procedure) are required if upgrading from Enterprise Server 10.6.12-7 to 10.6.12-8.

The next [scheduled maintenance release](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/faq/mariadb-software-questions/what-is-mariadbs-release-policy-and-schedule) for MariaDB Enterprise Server is 2023-06-12.

MariaDB Enterprise Server 10.6.12-8 was released on 2023-05-24.

## Fixed Security Vulnerabilities

| CVE (with [cve.org](https://github.com/mariadb-corporation/docs-release-notes/blob/test/mariadb-enterprise-server-release-notes/mariadb-enterprise-server-10-6/cve.org) link) | CVSS base score                                                              |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| [CVE-2022-47015](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-47015)                                                                                               | N/A (Medium)[#1](release-notes-for-mariadb-enterprise-server-10-6-12-8.md#1) |

`#1`:\
MariaDB CVEs are assigned a word rating instead of a CVSS base score. See the [MariaDB Engineering Policy](https://mariadb.com/engineering-policies) for details.

## Upgrade Procedure

**MariaDB Enterprise Server 10.6.12-8 has a special upgrade procedure that only applies to users who previously deployed MariaDB Enterprise Server 10.6.12-7.**

The following procedure is required to truncate the undo log tablespaces:

1. Upgrade from ES 10.6.12-7 to 10.6.12-8 using the normal upgrade procedure.
2. After the server has been started with ES 10.6.12-8, set `innodb_fast_shutdown=0:`

```sql
SET GLOBAL innodb_fast_shutdown=0;
```

1. Shutdown the server:

```bash
$ sudo systemctl stop mariadb
```

1. Change innodb\_undo\_tablespaces to a different value than its current value:

```
[mariadb]
innodb_undo_tablespaces=4
```

1. Start the server:

```bash
$ sudo systemctl start mariadb
```

## Notable Changes

* The optimizer can now use column histogram data when estimating output cardinality of hashed (BNL-H) joins. ([MDEV-30812](https://jira.mariadb.org/browse/MDEV-30812))
  * Starting with this release, the [optimizer\_switch system variable](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#optimizer_switch) has a new flag called hash\_join\_cardinality that can enable the feature.
  * When enabled, the optimizer uses a formula that provides conservative estimates.
  * To enable this functionality in a given session, set the flag using the [SET statement](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/administrative-sql-statements/set-commands/set):

```sql
SET optimizer_switch='hash_join_cardinality=on';
```

## Issues Fixed

### Can result in a hang or crash

* When a prepared statement is used to query a view that contains a `UNION`, the server can crash. ([MDEV-31102](https://jira.mariadb.org/browse/MDEV-31102))
* When [binlog\_row\_image=FULL](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/standard-replication/replication-and-binary-log-system-variables) is set and [slave\_parallel\_threads](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/standard-replication/replication-and-binary-log-system-variables) is greater than `0`, replica servers can hang if data is inserted into tables with a sequence. ([MDEV-29621](https://jira.mariadb.org/browse/MDEV-29621))
  * In previous releases, the replica server would treat full inserts into the sequence as DDL statements, which would cause it to acquire an exclusive lock on the sequence table. If another parallel replication thread is waiting on the lock at the same time, the two threads can deadlock.
  * Starting with this release, replica servers manage their locks better to avoid deadlocks in this scenario.
* When InnoDB splits or merges a B-tree page, the server can hang due to a race condition. ([MDEV-29835](https://jira.mariadb.org/browse/MDEV-29835))
* When InnoDB undo log truncation is enabled by setting [innodb\_undo\_log\_truncate=ON](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_undo_log_truncate), if some undo log tablespace exceeds [innodb\_max\_undo\_log\_size](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_max_undo_log_size), the server can hang. ([MDEV-30863](https://jira.mariadb.org/browse/MDEV-30863))
  * In previous releases, InnoDB chooses an undo log tablespace for truncation and marks all the related rollback segments with the state "truncation in progress". When the truncation is completed, InnoDB fails to re-enable the rollback segments. Consequently, if there are further write transactions before the server is shut down, the transactions must wait for usable rollback segments in a busy-loop. Since InnoDB does not re-enable the rollback segments, the transactions wait indefinitely.
  * Starting with this release, InnoDB properly manages the state of rollback segments when InnoDB undo log truncation is enabled.

### Can result in unexpected behavior

* For certain data distributions, the optimizer histogram code can produce wrong selectivity, which can lead to performance degradation. ([MDEV-31067](https://jira.mariadb.org/browse/MDEV-31067))
* The optimizer does not take into account the selectivity of the equality conditions for Block Nested Hash (BNL-H) joins.
  * In previous releases, this issue can cause mis-estimates and bad query plans when running with [join\_cache\_level](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#join_cache_level) set to 3 or higher (the default is 2).
* When the lateral derived optimization is used to execute a query, the derived table is re-filled on every incoming row combination, even if the parameter values have not changed. ([MDEV-26301](https://jira.mariadb.org/browse/MDEV-26301))
* When [slave\_parallel\_mode](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/standard-replication/replication-and-binary-log-system-variables) is `optimistic` and [slave\_parallel\_threads](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/standard-replication/replication-and-binary-log-system-variables) is greater than `0`, [ALTER SEQUENCE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-structure/sequences/alter-sequence) can fail with an out-of-order binlog error if the sequence uses InnoDB. ([MDEV-31077](https://jira.mariadb.org/browse/MDEV-31077))
  * In previous releases, the following error can be raised:

```
Last_Error: Error 'An attempt was made to binlog GTID 0-1-100 which would create an out-of-order sequence number with existing GTID 0-1-100 and gtid stric mode is enabled' on query. Default database: 'test'. Query: 'alter sequence s1 restart with 1' will be shown.
```

* InnoDB does not free undo logs when they are no longer needed. ([MDEV-31234](https://jira.mariadb.org/browse/MDEV-31234))
  * In the previous release, when [innodb\_undo\_tablespaces](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_undo_tablespaces) is set to 0, the undo logs would be stored in the InnoDB system tablespace (`ibdata1` by default), so this issue could cause the InnoDB system tablespace to grow indefinitely.
  * Starting with this release, InnoDB frees undo logs when they are no longer needed.
  * For servers that previously ran ES 10.6.12-7, a [special procedure](release-notes-for-mariadb-enterprise-server-10-6-12-8.md#upgrade-procedure) is required to truncate the undo log tablespaces after the upgrade is complete.
* InnoDB history list length increases faster in MariaDB Enterprise Server 10.6 compared to MariaDB Enterprise Server 10.5 for the same load. ([MDEV-29401](https://jira.mariadb.org/browse/MDEV-29401))

## Changes in Storage Engines

* This release incorporates MariaDB ColumnStore engine version 23.02.3.

## Interface Changes

* `hash_join_cardinality=off` has been incrementally added to the default value of the [optimizer\_switch](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#optimizer_switch) system variable.

## Platforms

In alignment to the [enterprise lifecycle](https://app.gitbook.com/o/diTpXxF5WsbHqTReoBsS/s/aEnK0ZXmUbJzqQrTjFyb/~/changes/32/mariadb-enterprise-server-release-notes/enterprise-server-lifecycle), MariaDB Enterprise Server 10.6.12-8 is provided for:

* CentOS 7 (x86\_64)
* Debian 10 (x86\_64, ARM64)
* Debian 11 (x86\_64, ARM64)
* Red Hat Enterprise Linux 7 (x86\_64)
* Red Hat Enterprise Linux 8 (x86\_64, ARM64)
* Red Hat Enterprise Linux 9 (x86\_64, ARM64)
* Rocky Linux 8 (x86\_64, ARM64)
* Rocky Linux 9 (x86\_64, ARM64)
* SUSE Linux Enterprise Server 12 (x86\_64)
* SUSE Linux Enterprise Server 15 (x86\_64, ARM64)
* Ubuntu 18.04 (x86\_64, ARM64)
* Ubuntu 20.04 (x86\_64, ARM64)
* Ubuntu 22.04 (x86\_64, ARM64)

Windows packages are not currently available for this release.

Some components of MariaDB Enterprise Server might not support all platforms. For additional information, see [MariaDB Corporation Engineering Policies".](https://mariadb.com/engineering-policies)

### Installation Instructions

* [MariaDB Enterprise Server ](../11-4/whats-new-in-mariadb-enterprise-server-11-4.md)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.6](../11-4/whats-new-in-mariadb-enterprise-server-11-4.md)
* [Enterprise Cluster Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)
* [Primary/Replica Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/primary-replica)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/primary-replica)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)
* [ColumnStore Object Storage Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-object-storage)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-object-storage)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[ and MariaDB Enterprise ColumnStore 23.02](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-object-storage)
* [ColumnStore Shared Local Storage Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-shared-local-storage)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-shared-local-storage)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[ and MariaDB Enterprise ColumnStore 23.02](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-shared-local-storage)
* [HTAP Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/htap)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/htap)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[ and MariaDB Enterprise ColumnStore 23.02](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/htap)
* [Single-Node Enterprise ColumnStore 23.02 with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies/enterprise-server-with-columnstore-object-storage)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies/enterprise-server-with-columnstore-object-storage)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[ and Object Storage](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies/enterprise-server-with-columnstore-object-storage)
* [Single-Node Enterprise ColumnStore 23.02 with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)
* [Enterprise Spider Sharded Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/sharded-mariadb-enterprise-spider-topology)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/sharded-mariadb-enterprise-spider-topology)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)
* [Enterprise Spider Federated Topology with MariaDB Enterprise Server 10.](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)

## Upgrade Instructions

* [Upgrade to MariaDB Enterprise Server 10.6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/install-and-upgrade-mariadb/upgrading/upgrading-from-to-specific-versions/upgrading-from-mariadb-10-5-to-mariadb-10-6)
* [Upgrade from MariaDB Community Server to MariaDB Enterprise Server 10.6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/install-and-upgrade-mariadb/upgrading/upgrading-between-major-mariadb-versions)

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
