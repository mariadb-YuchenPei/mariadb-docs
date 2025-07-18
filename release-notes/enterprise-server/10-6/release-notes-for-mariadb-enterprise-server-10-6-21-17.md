# Release Notes for MariaDB Enterprise Server 10.6.21-17

MariaDB Enterprise Server 10.6.21-17 is a maintenance release of [MariaDB Enterprise Server](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/mariadb-enterprise-server/README.md) 10.4. This release includes a variety of fixes.

MariaDB Enterprise Server 10.6.21-17 was released on 19 Mar 2025.

## Fixed Security Vulnerabilities

| CVE (with [cve.org](https://github.com/mariadb-corporation/docs-release-notes/blob/test/mariadb-enterprise-server-release-notes/mariadb-enterprise-server-10-6/cve.org) link) | CVSS base score |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- |
| [CVE-2025-21490](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-21490)                                                                                               | 4.9             |

## Changes in Storage Engines

* This release incorporates MariaDB ColumnStore engine version 23.10.3.

## Notable changes

* Starting with this release we generate a Software Bill of Materials (SBOM) JSON file provided in the downloads archive, which can be reached from the "All Files" link on the MariaDB Enterprise Server downloads page (MENT-2200)
* New parameter `--skip-freed-pages` for `Innochecksum`. Use this parameter to not get freed undo logs reported as existing undo log pages. ([MDEV-35394](https://jira.mariadb.org/browse/MDEV-35394))
* Galera protocol versions are now shown by show status - change available with installation of galera library 26.4.21+ ([MDEV-35505](https://jira.mariadb.org/browse/MDEV-35505))
* MariaDB now supports MySQL 8.0 binlog events, including `PARTIAL_UPDATE_ROWS_EVENT`, `TRANSACTION_PAYLOAD_EVENT`, and `HEARTBEAT_LOG_EVENT_V2`. ([MDEV-35643](https://jira.mariadb.org/browse/MDEV-35643))
* InnoDB deadlock output query length increased to improve visibility of deadlocked statements. ([MDEV-32576](https://jira.mariadb.org/browse/MDEV-32576))
* [Galera](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/galera-cluster/README.md) updated to 26.4.21
  * NOTE: Includes increasing the GCS protocol version, which prevents downgrades of individual nodes in the cluster as soon as all nodes have been updated

## Issues Fixed

### Can result in data loss

* Fix incorrect writing of timestamp into binary log, causing discrepancy upon binlog replaying ([MDEV-31761](https://jira.mariadb.org/browse/MDEV-31761))
* Fix trigger created with "`CREATE TRIGGER` table1\_after\_insert `AFTER INSERT`" which is adding rows to another table using "`FOR EACH ROW insert into table2(`id`,` name`) values (NEW.`id`, NEW.`name`);`" that did not work correctly when if bulk inserts are used by the application. Only the first row of the bulk insert would be added to the table ([MDEV-34958](https://jira.mariadb.org/browse/MDEV-34958))
* History is now stored on the same partitions on different Galera nodes when system versioning is enabled ([MDEV-35096](https://jira.mariadb.org/browse/MDEV-35096))
* Fix assertion falilure and possible index corruption with unique key and nopad collation without `DESC` or `HASH` keys ([MDEV-30111](https://jira.mariadb.org/browse/MDEV-30111))

### Can result in hang or crash

* Fix client crash the command after client sets character set to `utf32` ([MDEV-34090](https://jira.mariadb.org/browse/MDEV-34090))
* Fix possible crash where server could not construct a geomery object from the input ([MDEV-33987](https://jira.mariadb.org/browse/MDEV-33987))
* Fix possible InnoDB hang while running out of buffer pool ([MDEV-35409](https://jira.mariadb.org/browse/MDEV-35409))
* Fix possible Spider thread hang in 'Update' state on 2nd `INSERT` ([MDEV-35064](https://jira.mariadb.org/browse/MDEV-35064))
* After changing the table definition for the system table '`mysql.servers`', a following execution of `CREATE SERVER` would previously lead to a server crash. ([MDEV-33783](https://jira.mariadb.org/browse/MDEV-33783))
  * NOTE: System tables should never be modified by a user anyhow
* FIx streaming replication transaction crash with `innodb_snapshot_isolation` ([MDEV-35281](https://jira.mariadb.org/browse/MDEV-35281))
* Fix sporadic failure of async replication on Galera async replica nodes with parallel replication enabled ([MDEV-35465](https://jira.mariadb.org/browse/MDEV-35465))
* Fix failing assertion causing disruption and replication failure ([MDEV-24035](https://jira.mariadb.org/browse/MDEV-24035))
* Fix possible failure of `wsrep_sst_rsync` SST script if user specified `aria_log_dir_path` different from default data directory ([MDEV-35387](https://jira.mariadb.org/browse/MDEV-35387))
* Fix connection hang after query on a partitioned table with `UNION` and `LIMIT ROWS EXAMINED` ([MDEV-35571](https://jira.mariadb.org/browse/MDEV-35571))
* Fix server crash in `get_sort_by_table`/`make_join_statistics` after `INSERT` into a view with `ORDER BY` ([MDEV-29935](https://jira.mariadb.org/browse/MDEV-29935))
* Fix possible hang during `CREATE TABLE...SELECT` error handling, especially with `innodb_snapshot_isolation` enabled ([MDEV-35647](https://jira.mariadb.org/browse/MDEV-35647))
* Fix incorrect locking order of `LOCK_log`/`LOCK_commit_ordered`, and `LOCK_global_system_variables` ([MDEV-29744](https://jira.mariadb.org/browse/MDEV-29744))
* Fix possible memory leak on `SHUTDOWN` ([MDEV-35326](https://jira.mariadb.org/browse/MDEV-35326))
* Fix possible memory leak while shutting down server after installing the `auth_gssapi` plugin ([MDEV-35575](https://jira.mariadb.org/browse/MDEV-35575))
* Fix possible crash on `DELETE` from a `HEAP` table ([MDEV-22695](https://jira.mariadb.org/browse/MDEV-22695))
* Fix possible server crash when using `INSERT DELAYED` on tables with virtual columns. ([MDEV-26891](https://jira.mariadb.org/browse/MDEV-26891))
* Fix possible crash during index traversal using `tree_search_next`. ([MDEV-28130](https://jira.mariadb.org/browse/MDEV-28130))
* Fix possible hang or crash during InnoDB purge with `HASH` indexes during `ALTER TABLE` ([MDEV-25654](https://jira.mariadb.org/browse/MDEV-25654))
* Fix possible hang or crash where zero offset applied to null pointer ([MDEV-35864](https://jira.mariadb.org/browse/MDEV-35864))
* Fix possible crash on bootup in `spider_sys_open_table` «ext-issue»«[MDEV-32822](https://jira.mariadb.org/browse/MDEV-32822)», «ext-issue»«[MDEV-34302](https://jira.mariadb.org/browse/MDEV-34302)» ([MDEV-34925](https://jira.mariadb.org/browse/MDEV-34925))
* Fix possible Spider crash or hang when the first byte of a connection key is changed ([MDEV-34849](https://jira.mariadb.org/browse/MDEV-34849))
* Fix possible runtime error caused by `XA RECOVER` applying a zero offset to a null pointer ([MDEV-35549](https://jira.mariadb.org/browse/MDEV-35549))
* Fix assertion failure on cascading foreign key update of table with vcol index in parent ([MDEV-29182](https://jira.mariadb.org/browse/MDEV-29182))
* Fix assertion failure where `CURRENT_USER` was not correctly copied during condition pushdown ([MDEV-35090](https://jira.mariadb.org/browse/MDEV-35090))
* Fix cluster node hang during shutdown if threadpool is used ([MDEV-35710](https://jira.mariadb.org/browse/MDEV-35710))
* Calling a stored routine that executes a join on three or more tables and referencing not-existent column name in the `USING` clause could previously result in a crash on its second invocation. ([MDEV-24935](https://jira.mariadb.org/browse/MDEV-24935))
* Fix possible assertion failure when Galera cluster is in '`split-brain`' state due to loss of communication between nodes (fix requires Galera library 26.4.21+) (MENT-2175)
* Fix assertion failure when executing `XA PREPARE` (and possibly other `XA` statements) on Galera cluster nodes (MENT-2212)
* Fix assertion failure when executing `XA` statements on Galera cluster nodes (MENT-2214)
* In rare cases, an `ALTER TABLE` or other operation could previously hang when using `NBO` mode on a cluster with very low network latencies (for example, when both nodes are running on the same physical machine) (MENT-2215)
* MariaDB Cluster and `ALTER INPLACE` running in Total Order Isolation (`wsrep_OSU_method=TOI`) now correctly abort a `DML INSERT` operation in InnoDB ([MDEV-33064](https://jira.mariadb.org/browse/MDEV-33064))
* Fix possible crash in `wsrep_check_sequence` ([MDEV-33245](https://jira.mariadb.org/browse/MDEV-33245))

### Can result in unexpected behaviour

* Fix sporadic reporting of success when a deadlock error occurs under `--ps-protocol BF` aborted transaction ([MDEV-35446](https://jira.mariadb.org/browse/MDEV-35446))
* Fix rare cases where binlog entries could receive incorrect timestamps on secondary nodes of a Galera cluster, potentially impacting replication accuracy ([MDEV-35157](https://jira.mariadb.org/browse/MDEV-35157))
* For an authentication with the ed25519 authentication plugin the password of the `CREATE USER` statement is now masked in the audit log ([MDEV-35507](https://jira.mariadb.org/browse/MDEV-35507))
* MariaDB Audit now detects all DCLs forms for masking a password ([MDEV-35522](https://jira.mariadb.org/browse/MDEV-35522))
* Fix potential issue in secondary Index with `ROW_FORMAT=COMPRESSED` and Change buffering enabled ([MDEV-35679](https://jira.mariadb.org/browse/MDEV-35679))
* `sql_mode='NO_UNSIGNED_SUBTRACTION'` now works for multiple unsigned integers ([MDEV-35651](https://jira.mariadb.org/browse/MDEV-35651))
* Fix doublewrite recovery of `innodb_checksum_algorithm=full_crc32` encrypted pages ([MDEV-34898](https://jira.mariadb.org/browse/MDEV-34898))
* `START TRANSACTION`, when triggering an implicit commit as a `COMMIT` or `ROLLBACK` has not been executed before, now resets optional characteristics added to the last `START TRANSACTION` command ([MDEV-35335](https://jira.mariadb.org/browse/MDEV-35335))
* `mariadb-binlog` can now correctly process more than one logfile when `--stop-datetime` is specified ([MDEV-35528](https://jira.mariadb.org/browse/MDEV-35528))
* Rows in table `mysql.gtid_slave_pos` are now correctly deleted on Galera nodes when `wsrep_gtid_mode = 1` is used, which previously lead to wrong information about replica delays ([MDEV-34924](https://jira.mariadb.org/browse/MDEV-34924))
* `EXCHANGE PARTITION` now works for tables with unique blobs ([MDEV-35612](https://jira.mariadb.org/browse/MDEV-35612))
* Fix issue where functions in default values in tables with certain character sets could break `SHOW CREATE` and `mariadb-dump` ([MDEV-29968](https://jira.mariadb.org/browse/MDEV-29968))
* Setting `pseudo_thread_id` to a value exceeding 4 bytes previously resulted in truncation when written to the binary log ([MDEV-35646](https://jira.mariadb.org/browse/MDEV-35646))
* A `BEFORE INSERT` Trigger previously returned with error "`Field 'xxx' doesn't have a default value`", if a `NULL` value was added for a column defined `NOT NULL` without explicit value and no `DEFAULT` specified ([MDEV-19761](https://jira.mariadb.org/browse/MDEV-19761))
* Undefined behavior could occur when attempting to perform `INSERT DELAYED` on a Galera cluster node. ([MDEV-35852](https://jira.mariadb.org/browse/MDEV-35852))
* Fix issue where `ON UPDATE SET NULL` could not be specified on a `NOT NULL` column ([MDEV-35445](https://jira.mariadb.org/browse/MDEV-35445))
* `algorithm = instant` can now correctly be used if a table has partitions and one tries to change a column with an index which is not the partitions key. This previously gave error "`ERROR 1846 (0A000): ALGORITHM=INSTANT is not supported. Reason: ADD INDEX. Try ALGORITHM=NOCOPY`" ([MDEV-34813](https://jira.mariadb.org/browse/MDEV-34813))
* Fix issue where `DROP TABLE` on child and `UPDATE` of parent table can cause a metadata lock `BF-BF` conflict when applied concurrently. ([MDEV-35018](https://jira.mariadb.org/browse/MDEV-35018))
* Can now correctly add a foreign key on a table with a long `UNIQUE` multi-column index that contains a foreign key as a prefix ([MDEV-33658](https://jira.mariadb.org/browse/MDEV-33658))
* Fix possibly wrong result using a degenerated subquery `(SELECT <expr>)` with window function ([MDEV-35869](https://jira.mariadb.org/browse/MDEV-35869))
* The "`Failed to write to mysql.slow_log`" error no longer shown without a detailed reason for the error ([MDEV-20281](https://jira.mariadb.org/browse/MDEV-20281))
* Fix `debian-start` script failure when using non-standard socket path ([MDEV-35907](https://jira.mariadb.org/browse/MDEV-35907))
* `wsrep_sst_mariadb-backup.sh` no longer uses `--use-memory default (100MB)` resulting in prepare stage which could take hours ([MDEV-35749](https://jira.mariadb.org/browse/MDEV-35749))
* `Replicate_*` fields in `Show-Slave-Status` may be truncated, impacting replication monitoring. (MENT-2238)

### Related to performance

* Conditions with `SP` local variables are now pushed into derived table. Previous behaviour caused slow performance and table scans instead of using the pushed down condition ([MDEV-35910](https://jira.mariadb.org/browse/MDEV-35910))
* `NULL`-aware materialization with IN predicate and single column no longer skips building sorted Ordered\_key structures ([MDEV-34665](https://jira.mariadb.org/browse/MDEV-34665))
* Cloning of table statistics while saving the InnoDB table stats is now avoided ([MDEV-35363](https://jira.mariadb.org/browse/MDEV-35363))

## Changelog

For the complete list of changes in this release, see the [changelog](changelog-for-mariadb-enterprise-server-10-6-21-17.md).

## Platforms

In alignment to the [enterprise lifecycle](../enterprise-server-lifecycle.md), MariaDB Enterprise Server 10.6.21-17 is provided for:

* AlmaLinux 8 (x86\_64, ARM64)
* AlmaLinux 9 (x86\_64, ARM64)
* Debian 11 (x86\_64, ARM64)
* Debian 12 (x86\_64, ARM64)
* Microsoft Windows (x86\_64) (MariaDB Enterprise Cluster excluded)
* Red Hat Enterprise Linux 8 (x86\_64, ARM64)
* Red Hat Enterprise Linux 9 (x86\_64, ARM64, PPC64LE)
* Rocky Linux 8 (x86\_64, ARM64)
* Rocky Linux 9 (x86\_64, ARM64)
* SUSE Linux Enterprise Server 12 (x86\_64)
* SUSE Linux Enterprise Server 15 (x86\_64, ARM64)
* Ubuntu 20.04 (x86\_64, ARM64)
* Ubuntu 22.04 (x86\_64, ARM64)
* Ubuntu 24.04 (x86\_64, ARM64)
* Red Hat UBI 8 (x86\_64, ARM64)
  * Red Hat UBI 8 is part of the Enterprise Server Docker Image. It does not support MariaDB Enterprise Cluster (Galera) or MariaDB ColumnStore.

Some components of MariaDB Enterprise Server are supported on a subset of platforms. See [MariaDB Engineering Policies](https://mariadb.com/engineering-policies) for details.

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
