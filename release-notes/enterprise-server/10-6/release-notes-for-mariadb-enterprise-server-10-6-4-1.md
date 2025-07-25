# Release Notes for MariaDB Enterprise Server 10.6.4-1

MariaDB Enterprise Server 10.6.4-1 is the first General Availability (GA) release of [MariaDB Enterprise Server](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/mariadb-enterprise-server/README.md) 10.6. This release contains a variety of new features.

MariaDB Enterprise Server 10.6.4-1 was released on 2021-08-26.

## Fixed Security Vulnerabilities

| CVE (with [cve.org](https://github.com/mariadb-corporation/docs-release-notes/blob/test/mariadb-enterprise-server-release-notes/mariadb-enterprise-server-10-6/cve.org) link) | CVSS base score |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- |
| [CVE-2021-46658](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-46658)                                                                                               | 5.5             |

## Notable Changes

* Extensive internal optimizations, including a refactoring of [InnoDB storage engine](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb) code.
* Atomic DDL
  * DDL (Data Definition Language) statements are now atomic operations. If the DDL statement is not fully successful, the operation will be rolled back. When the server crashes or is killed in the middle of a DDL statement, the operation is rolled back during crash recovery when the server is restarted. ([MDEV-17567](https://jira.mariadb.org/browse/MDEV-17567))
  * During crash recovery, the server uses the DDL log to determine if an operation needs to be rolled back. When the [binary log](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/server-monitoring-logs/binary-log) is enabled, the crash recovery process ensures that the successful operations are written to the binary log and that the unsuccessful operations are not.
  * By default, the DDL log is at `ddl-recovery.log` in the [datadir](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#datadir). When DDL statements are being executed, the DDL log is synchronized to disk very frequently. If you want to configure a custom path for the DDL log, the [log-ddl-recovery](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-troubleshooting/innodb-recovery-modes) option can be used.
  * As of this release, the following storage engines fully support atomic DDL:
    * [Aria](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/aria)
    * [InnoDB](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb)
    * [MyISAM](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/myisam-storage-engine)
    * [MyRocks](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/myrocks)
* Default InnoDB flush method
  * The default [innodb\_flush\_method](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_flush_method) is now `O_DIRECT` ([MDEV-24854](https://jira.mariadb.org/browse/MDEV-24854))
  * Prior to this release, the default [innodb\_flush\_method](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_flush_method) was `fsync`
* UTF-8 (utf8) character set alias
  * The [utf8](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/data-types/string-data-types/character-sets) character set has been renamed to [utf8mb3](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/data-types/string-data-types/character-sets), which used to be an alias for the `utf8` character set
  * The character set `utf8` is now an alias that defaults to `utf8mb3` but can be turned into an alias for [utf8mb4](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/data-types/string-data-types/character-sets) with a config change
  * The new default of [old\_mode=UTF8\_IS\_UTF8MB3](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#old_mode) is what makes `utf8mb3` default to `utf8`, and anything that removes this new value from old\_mode changes `utf8` to mean `utf8mb4` ([MDEV-8334](https://jira.mariadb.org/browse/MDEV-8334))
  * In a future release series (after 10.6) the default value of `old_mode` will drop this new value, making `utf8` default to `utf8mb4`
* IPv6 by Default ([MDEV-6536](https://jira.mariadb.org/browse/MDEV-6536))
  * When [--bind-address=HOSTNAME](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#bind_address) is configured, MariaDB Enterprise Server now listens on both IPv6 and IPv4 addresses.

## Changes in Storage Engines

### ColumnStore

* This release incorporates [MariaDB Enterprise ColumnStore version 6.1.1](../../columnstore/mariadb-columnstore-6-release-notes/mariadb-columnstore-6-1-1-release-notes.md). Benefits include:
  * Disk-based aggregation allows larger aggregated result sets than can fit in memory
  * Increased DECIMAL precision
  * Transactional tables can be updated with data from ColumnStore tables
  * LZ4 compression

### InnoDB

* Default InnoDB flush method
  * (This item is also mentioned above in [Notable Changes](https://app.gitbook.com/s/rfK8h3eGTK4lYdomGpGT/readme/mariadb-connectors/mariadb-connector-c++/release-notes-and-changelogs/mariadb-connector-c++-1.1/mariadb-connector-c++-1.1.3#notable-changes) .)
  * The default [innodb\_flush\_method](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_flush_method) is now `O_DIRECT` ([MDEV-24854](https://jira.mariadb.org/browse/MDEV-24854))
  * Prior to this release, the default [innodb\_flush\_method](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_flush_method) was `fsync`
* SELECT .. SKIP LOCKED
  * [SELECT \[ FOR UPDATE | LOCK IN SHARED MODE \] .. SKIP LOCKED](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/selecting-data/select) ignores already-locked rows. ([MDEV-13115](https://jira.mariadb.org/browse/MDEV-13115))
  * One use case for this feature is within applications that sell a limited resource, such as ticketing, rentals, or seat-based sales. In these applications, you need a way to display only the available inventory. This can be accomplished by querying available inventory and skipping locked rows.

```sql
SELECT *
FROM ticketing
WHERE claimed = 0 AND section = 'B'
ORDER BY row DESC
LIMIT 10
FOR UPDATE SKIP LOCKED;
```

* Compressed rows read-only by default
  * [COMPRESSED](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-row-formats/innodb-compressed-row-format) row format is read-only by default. ([MDEV-23497](https://jira.mariadb.org/browse/MDEV-23497))
  * System variable [innodb\_read\_only\_compressed=ON](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_read_only) by default.
  * System variable `innodb_read_only_compressed=OFF` enables write support.
  * This is a preparatory change. Additional change will occur in a future release series (after 10.6), when `COMPRESSED` row format will no longer accept writes. It is recommended to alter tables using the `COMPRESSED` row format to use the [DYNAMIC](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-row-formats/innodb-dynamic-row-format) row format with InnoDB page compression:

```sql
ALTER TABLE tab
 ROW_FORMAT=DYNAMIC
 PAGE_COMPRESSED=1;
```

* For additional information, see "[Convert InnoDB Tables to the Dynamic Row Format](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/information-schema/information-schema-tables/information-schema-innodb-tables)" and "[Configure InnoDB Page Compression](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-page-compression)".
* Information Schema changes for InnoDB
  * Information Schema [INNODB\_SYS\_TABLESPACES](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/information-schema/information-schema-tables/information-schema-innodb-tables/information-schema-innodb_sys_tablespaces-table) directly reflects the filesystem. ([MDEV-22343](https://jira.mariadb.org/browse/MDEV-22343))
  * `INNODB_SYS_TABLESPACES.PAGE_SIZE` contains the physical page size of a page.
  * `INNODB_SYS_TABLESPACES.FILENAME` added as a replacement for [SYS\_DATAFILES.PATH](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/information-schema/information-schema-tables/information-schema-innodb-tables/information-schema-innodb_sys_datafiles-table)
  * Information Schema `INNODB_SYS_DATAFILES` removed. ([MDEV-22343](https://jira.mariadb.org/browse/MDEV-22343))
* Reduced global lock duration in InnoDB transaction deadlock checks ([MDEV-24738](https://jira.mariadb.org/browse/MDEV-24738))
* InnoDB no longer acquires advisory file locks by default ([MDEV-24393](https://jira.mariadb.org/browse/MDEV-24393))
* When using data-at-rest encryption with the [file\_key\_management](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/security/securing-mariadb/securing-mariadb-encryption/encryption-data-at-rest-encryption/key-management-and-encryption-plugins/file-key-management-encryption-plugin) encryption plugin, InnoDB will automatically disable key rotation checks. ([MDEV-14180](https://jira.mariadb.org/browse/MDEV-14180))\*
  * The [file\_key\_management](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/security/securing-mariadb/securing-mariadb-encryption/encryption-data-at-rest-encryption/key-management-and-encryption-plugins/file-key-management-encryption-plugin) encryption plugin does not support key rotation, so key rotation checks are not required.\*
  * In previous releases, unnecessary key rotation checks with the [file\_key\_management](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/security/securing-mariadb/securing-mariadb-encryption/encryption-data-at-rest-encryption/key-management-and-encryption-plugins/file-key-management-encryption-plugin) encryption plugin could reduce performance, unless they were explicitly disabled by setting [innodb\_encryption\_rotate\_key\_age=0](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_encryption_rotate_key_age).
*
  * Optimization added to speed up inserts into an empty InnoDB table. ([MDEV-515](https://jira.mariadb.org/browse/MDEV-515))
* Maximum value of the [innodb\_lock\_wait\_timeout](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_lock_wait_timeout) system variable is now 100000000, which means infinite timeout.
* Change in checksum algorithm options
  * [innodb\_checksum\_algorithm](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_checksum_algorithm) options have changed: ([MDEV-25105](https://jira.mariadb.org/browse/MDEV-25105))
    * Supported: `crc32, strict_crc32, full_crc32, strict_full_crc32`
    * Eliminated: `none, strict_none, innodb, strict_innodb`
  * When InnoDB reads a page using an eliminated checksum algorithm after performing a physical upgrade, InnoDB will continue to accept the checksum.
  * When a query changes a page using an eliminated checksum algorithm, InnoDB will automatically switch to a supported checksum algorithm when InnoDB writes the changed page to disk.

## Compatibility Enhancements

* Expanded compatibility with Oracle through new functions:
  * Added function [ADD\_MONTHS()](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/date-time-functions/add_months) ([MDEV-20025](https://jira.mariadb.org/browse/MDEV-20025))
  * Added function [ROWNUM()](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/secondary-functions/information-functions/rownum) ([MDEV-24285](https://jira.mariadb.org/browse/MDEV-24285))
  * Added function [SYS\_GUID()](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/secondary-functions/miscellaneous-functions/sys_guid) ([MDEV-24285](https://jira.mariadb.org/browse/MDEV-24285))
  * Added function [TO\_CHAR()](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/string-functions/to_char) ([MDEV-20017](https://jira.mariadb.org/browse/MDEV-20017))
* Expanded compatibility with Oracle through [sql\_mode=ORACLE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/variables-and-modes/sql-mode) enhancements:
  * With `sql_mode=ORACLE` added `MINUS` as an alias to `EXCEPT` ([MDEV-20021](https://jira.mariadb.org/browse/MDEV-20021))
  * With `sql_mode=ORACLE` improved `SYSDATE`to allow use without parenthesis. ([MDEV-19682](https://jira.mariadb.org/browse/MDEV-19682))
  * With `sql_mode=ORACLE` supports a [rownum](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/secondary-functions/information-functions/rownum) pseudo-column name as an alias for the [ROWNUM()](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/secondary-functions/information-functions/rownum) function ([MDEV-24089](https://jira.mariadb.org/browse/MDEV-24089))
  * With `sql_mode=ORACLE` subqueries in a FROM clause do not require the AS clause.
* Enhanced compatibility with Sybase SQL Anywhere through [sql\_mode=EXTENDED\_ALIASES](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/variables-and-modes/sql-mode): (MENT-1062)
  * With `sql_mode=EXTENDED_ALIASES`, alias resolution and use of column aliases in the SQL [SELECT](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/selecting-data/select) list and WHERE clause.
  * With `sql_mode=EXTENDED_ALIASES`, support use of an alias in the [SELECT](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/selecting-data/select) list before the alias is defined.
  * With `sql_mode=EXTENDED_ALIASES`, if the same label is used for an alias and a column, the alias is used.

## Operational Enhancements

* sys Schema
  * sys schema provides a set of views, functions, and stored procedures to aid DBA analysis of the [Performance Schema](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/performance-schema). ([MDEV-9077](https://jira.mariadb.org/browse/MDEV-9077))
* Increase in host name length
  * Host names in [CREATE USER](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/account-management-sql-statements/create-user), [GRANT](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/account-management-sql-statements/grant) and replication [CHANGE MASTER](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/administrative-sql-statements/replication-statements/change-master-to) can be up to 255 bytes long. ([MDEV-24312](https://jira.mariadb.org/browse/MDEV-24312))
* UTF8
* (This item is also mentioned above in Notable Changes .)
* The [utf8](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/variables-and-modes/old-mode#utf8_is_utf8mb3) character set has been renamed to [utf8mb3](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/variables-and-modes/old-mode#utf8_is_utf8mb3), which was formerly an alias for the `utf8` character set
* The character set `utf8` is now an alias that defaults to `utf8mb3` but can be turned into an alias for [utf8mb4](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/data-types/string-data-types/character-sets/supported-character-sets-and-collations#character-sets) with a config change
* The new default of [old\_mode=UTF8\_IS\_UTF8MB3](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#old_mode) is what makes `utf8mb3` default to `utf8`, and anything that removes this new value from `old_mode` changes `utf8` to mean `utf8mb4` ([MDEV-8334](https://jira.mariadb.org/browse/MDEV-8334))
* In a future release series (after 10.6) the default value of `old_mode` will drop this new value, making utf8 default to `utf8mb4`
* Ignored indexes
  * An index can be marked with the `IGNORED` option, which forbids the optimizer from using the index in queries. The `IGNORED` option can be used to evaluate whether an index is actually helpful for performance without dropping the index. ([MDEV-7317](https://jira.mariadb.org/browse/MDEV-7317))
  * Example syntax for `CREATE TABLE`:

```sql
CREATE TABLE table_name (
 id INT PRIMARY KEY,
 col_name INT,
 INDEX key_name (col_name) IGNORED
);
```

* Example syntax for CREATE INDEX:

```sql
CREATE INDEX key_name
 ON table_name
 (col_name) IGNORED;
```

* Example syntax for ALTER TABLE:

```sql
ALTER TABLE table_name
 ALTER INDEX key_name IGNORED;
```

* An ignored index cannot be referenced in index hints, such as `FORCE INDEX, IGNORE INDEX, or USE INDEX`. When you try to reference an ignored index in an index hint, the server raises an error with the [ER\_KEY\_DOES\_NOT\_EXISTS](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes) error code:

```sql
SELECT *
FROM table_name
 FORCE INDEX (key_name)
WHERE col_name > 1;
```

```
ERROR 1176 (42000): Key 'key_name' doesn't exist in table 'table_name'
```

* Thread Pool enhancements
  * The thread pool can be configured to reshuffle connections into random thread groups periodically, which can help prevent many connections from becoming concentrated in just a few thread groups. (MENT-622)
  * The thread\_pool\_reshuffle\_group\_period system variable defines how frequently the connections are reshuffled. By default, the value is 0 which means that connections are not reshuffled.
  * The THREAD\_POOL\_CONNECTIONS information schema table can be used to view which connections are assigned to each thread group.
* Systemd
  * Systemd socket activation is now supported. ([MDEV-5536](https://jira.mariadb.org/browse/MDEV-5536))

## SQL Level Enhancements

* JSON\_TABLE()
  * [JSON\_TABLE()](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/special-functions/json-functions/json_table) returns a table from JSON data. ([MDEV-17399](https://jira.mariadb.org/browse/MDEV-17399))
  * Queryable rows and columns are produced based on the JSON input, but are not stored in a table on disk. Column mappings are defined in a JSON path expression.
  * Prior to this release, the [JSON\_VALUE()](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/special-functions/json-functions/json_value) and [JSON\_QUERY()](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/special-functions/json-functions/json_query) functions could be used to retrieve values from JSON data on a per-column basis.
  * With `JSON_TABLE()`:
    * JSON data can JOIN with existing tables.\`\`
    * A table can be created from JSON data using [CREATE TABLE .. AS SELECT](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-definition/create/create-table) against a `JSON_TABLE()`.
    * [NESTED PATH](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/special-functions/json-functions/json_table) enables extraction of nested data from JSON arrays and objects.
* OFFSET syntax
  * Additional syntax is supported for [SELECT .. OFFSET](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/selecting-data/select) ([MDEV-23908](https://jira.mariadb.org/browse/MDEV-23908))
  * `OFFSET start { ROW | ROWS } FETCH { FIRST | NEXT } [ count ] { ROW | ROWS } { ONLY | WITH TIES }` is an alternative to `LIMIT .. OFFSET`
  * The `WITH TIES` option requires the use of `ORDER BY` and allows the number of rows to exceed the `FETCH` count to ensure that the final row in the chunk includes any additional rows that have the same values in the `ORDER BY` fields (eliminating the need to fetch the next chunk to check for spill-over).
    * For example, the following query can return more than 10 rows if there are more `username` rows that match the `username` in the 10th row (the order of the purchase values within the complete set of each `username`'s records is non-deterministic):

```sql
SELECT username, purchase
FROM user_purchases
ORDER BY username
OFFSET 305 ROWS
FETCH NEXT 10 ROWS WITH TIES;
```

* For example, the following query specifies `ONLY` instead of `WITH TIES`, so the query can't return more than 10 rows:

```sql
SELECT username, purchase
FROM user_purchases
ORDER BY username, purchase
OFFSET 0 ROWS
FETCH NEXT 10 ROWS ONLY;
```

* Views supported with [FLUSH TABLES tbl\_name \[, tbl\_name\] .. WITH READ LOCK](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/administrative-sql-statements/flush-commands/flush) ([MDEV-15888](https://jira.mariadb.org/browse/MDEV-15888))
* All SQL statements can be prepared except [PREPARE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/prepared-statements), [EXECUTE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/prepared-statements/execute-statement), \[DEALLOCATE / DROP [PREPARE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/prepared-statements)([MDEV-16708](https://jira.mariadb.org/browse/MDEV-16708))

## Security Features

* [MariaDB Enterprise Audit](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/plugins/mariadb-audit-plugin) allows database-specific and table-specific filters. (MENT-65)\
  For example:

```
{
 "connect_event" : "ALL",
 "table_event" : ["READ","WRITE",{"ignore_tables" : "mysql.*"}],
 "query_event" : ["DDL",{"tables" : "test.t2"}]
}
```

* The [gssapi](broken-reference/) authentication plugin can now authenticate a user account by checking if the user belongs to an Active Directory group. ([MDEV-23959](https://jira.mariadb.org/browse/MDEV-23959))
  * The group is specified in the authentication string using the [CREATE USER](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/account-management-sql-statements/create-user) statement. The group can be specified using the group name or the SID.
  * Example syntax using a group name without specifying the domain:

```sql
CREATE USER root
 IDENTIFIED VIA gssapi AS 'GROUP:Administrators';
```

* Example syntax using a group name that specifies the domain:

```sql
CREATE USER root
 IDENTIFIED VIA gssapi AS 'GROUP:Administrators';
```

* Example syntax using a SID in the usual format:

```sql
CREATE USER root
 IDENTIFIED VIA gssapi AS 'SID:S-1-5-32-544';
```

* Example syntax using a well-known SID:

```sql
CREATE USER everyone
 IDENTIFIED VIA gssapi AS 'SID:WD';
```

* When using data-at-rest encryption with the [file\_key\_management](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/security/securing-mariadb/securing-mariadb-encryption/encryption-data-at-rest-encryption/key-management-and-encryption-plugins/file-key-management-encryption-plugin) encryption plugin, InnoDB will automatically disable key rotation checks. ([MDEV-14180](https://jira.mariadb.org/browse/MDEV-14180))\*
  * The [file\_key\_management](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/security/securing-mariadb/securing-mariadb-encryption/encryption-data-at-rest-encryption/key-management-and-encryption-plugins/file-key-management-encryption-plugin) encryption plugin does not support key rotation, so key rotation checks are not required.\*
  * In previous releases, unnecessary key rotation checks with the [file\_key\_management](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/security/securing-mariadb/securing-mariadb-encryption/encryption-data-at-rest-encryption/key-management-and-encryption-plugins/file-key-management-encryption-plugin) encryption plugin could hurt performance, unless they were explicitly disabled by setting [innodb\_encryption\_rotate\_key\_age=0](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_encryption_rotate_key_age).
* With [MariaDB Enterprise Cluster](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/galera-cluster/README.md), TLS is required for MariaDB Enterprise Cluster by default. (MENT-1192)
  * Since TLS is required for Enterprise Cluster by default, database administrators should create TLS certificates for each node during the deployment process.
  * Database administrators can revert Enterprise Cluster to the mode used in previous releases by setting the wsrep\_ssl\_mode system variable to `PROVIDER`.
  * For additional information, see "WSREP TLS Modes".
* TLS functionality for State Snapshot Transfers (SSTs) is enhanced when MariaDB Enterprise Backup or Rsync is the SST method. ([MDEV-25359](https://jira.mariadb.org/browse/MDEV-25359))
  * For additional information, see "[SST TLS Modes](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/galera/README.md)".
* Cluster name verification is performed for Joiner nodes prior to State Snapshot Transfers (SSTs) and Incremental State Transfers (ISTs). ([MDEV-25359](https://jira.mariadb.org/browse/MDEV-25359))\
  For additional information, see "[Cluster Name Verification](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/galera/README.md)".
* With MariaDB Enterprise Cluster, system variable [wsrep\_certificate\_expiration\_hours\_warning](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/galera-cluster-system-variables) enables logging of a warning prior to expiration of the TLS certificate used for wsrep (Enterprise Cluster) communications. (MENT-1090)
  * For additional information, see ["Certificate Expiration Warnings"](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/galera/README.md).
*
  * With MariaDB Enterprise Cluster, communication between nodes can be changed from unencrypted to TLS without cluster downtime. ([MDEV-22131](https://jira.mariadb.org/browse/MDEV-22131))
  * Enabling TLS without downtime relies on two new options implemented for the [wsrep\_provider\_options](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/galera-cluster-system-variables#wsrep_provider_options) system variable: `socket.dynamic` and `socket.ssl_reload`.
  * For additional information, see "[Enable TLS without Downtime](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/galera-cluster-system-variables#wsrep_provider_options)".

## MariaDB Replication

* Performance Schema [replication\_applier\_status\_by\_worker](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/performance-schema/performance-schema-tables/performance-schema-replication_applier_status_by_worker-table) table provides information on replica worker threads. ([MDEV-20220](https://jira.mariadb.org/browse/MDEV-20220))
* Fine-grained binlog expiration
  * [binlog\_expire\_logs\_seconds](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/standard-replication/replication-and-binary-log-system-variables) system variable defines the frequency in seconds of automated removal of binary logs. ([MDEV-19371](https://jira.mariadb.org/browse/MDEV-19371))
  * Prior to this release, expiration time was defined in days using binlog\_expire\_logs\_days.
* Enhanced consistency for Semi-Sync Replication
  * When [rpl\_semi\_sync\_slave\_enabled=ON](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/standard-replication/semisynchronous-replication#rpl_semi_sync_slave_enabled), consistency is guaranteed for a Primary server in an HA (Primary/Replica) topology when using semi-synchronous replication. ([MDEV-21117](https://jira.mariadb.org/browse/MDEV-21117))
  * rior to this release, when using semi-synchronous replication, if a Primary crashed before sending a transaction to the Replica, on restart the Primary could recover incomplete InnoDB transactions when rejoining as a Replica.
  * With this release, when using semi-synchronous replication and with `rpl_semi_sync_slave_enabled=ON`, incomplete transactions will be rolled-back on the Replica, ensuring the new Primary (former Replica) and new Replica (former Primary) remain in sync.

## MariaDB Enterprise Cluster

MariaDB Enterprise Cluster is powered by Galera. New in this release:

* XA Transactions are supported (MENT-690)
* With [MariaDB Enterprise Cluster](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/galera-cluster/README.md), TLS is required for MariaDB Enterprise Cluster by default. (MENT-1192)
  * Since TLS is required for Enterprise Cluster by default, database administrators should create TLS certificates for each node during the deployment process.
  * Database administrators can revert Enterprise Cluster to the mode used in previous releases by setting the [wsrep\_ssl\_mode](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/galera-cluster-system-variables) system variable to `PROVIDER`.
  * For additional information, see "[WSREP TLS Modes](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/galera-security/securing-communications-in-galera-cluster)".
* TLS functionality for State Snapshot Transfers (SSTs) is enhanced when MariaDB Enterprise Backup or Rsync is the SST method. ([MDEV-25359](https://jira.mariadb.org/browse/MDEV-25359))
  * For additional information, see "[SST TLS Modes](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/galera-security/securing-communications-in-galera-cluster)".
* Cluster name verification is performed for Joiner nodes prior to State Snapshot Transfers (SSTs) and Incremental State Transfers (ISTs). ([MDEV-25359](https://jira.mariadb.org/browse/MDEV-25359))
  * For additional information, see "[Cluster Name Verification](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/galera/README.md)".
* [wsrep\_certificate\_expiration\_hours\_warning](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/galera-cluster-status-variables) system variable enables logging of a warning prior to expiration of the TLS certificate used for wsrep (Enterprise Cluster) communications. (MENT-1090)
  * For additional information, see "Certificate Expiration Warnings".
*
  * Communication between nodes can be changed from unencrypted to TLS without cluster downtime. ([MDEV-22131](https://jira.mariadb.org/browse/MDEV-22131))
  * Enabling TLS without downtime relies on two new options implemented for the [wsrep\_provider\_options](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/wsrep-variable-details/wsrep_provider_options) system variable: `socket.dynamic` and `socket.ssl_reload`.
  * For additional information, see "[Enable TLS without Downtime](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/galera/README.md)".
* Galera Cluster nodes can be configured to refuse statements that would generate local GTIDs. ([MDEV-20715](https://jira.mariadb.org/browse/MDEV-20715))
  * When Galera Cluster is used with MariaDB Replication, local GTIDs can cause replication errors when the primary or replica has to failover to a different cluster node. By configuring Galera Cluster nodes to refuse statements that would generate local GTIDs, replication is more likely to succeed against any available cluster node.
  * To configure a node to refuse statements that would generate local GTIDs, set [wsrep\_mode=DISALLOW\_LOCAL\_GTID](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/galera-cluster-system-variables#wsrep_mode).
* [wsrep\_mode=STRICT\_REPLICATION](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/galera-cluster-system-variables#wsrep_mode) replaces deprecated system variable [wsrep\_strict\_ddl](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/galera-cluster-system-variables#wsrep_strict_ddl) ([MDEV-20008](https://jira.mariadb.org/browse/MDEV-20008))
* [wsrep\_mode=REPLICATE\_MYISAM](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/galera-cluster-system-variables#wsrep_mode) replaces deprecated system variable [wsrep\_replicate\_myisam](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/galera-cluster-system-variables#wsrep_replicate_myisam) ([MDEV-24946](https://jira.mariadb.org/browse/MDEV-24946))
* When [wsrep\_debug=SERVER](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/galera-cluster-system-variables#wsrep_debug) and `wsrep_OSU_method=TOI`, information about DDL queries from remote hosts is logged in the local error log, not just locally-initiated DDL queries. ([MDEV-9609](https://jira.mariadb.org/browse/MDEV-9609))
  * The default of [wsrep\_debug=NONE](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/galera-cluster-system-variables#wsrep_debug) disables debug logging.
* The script `wsrep_sst_mariadb-backup` checks all server-related configuration groups when processing a configuration file. ([MDEV-25669](https://jira.mariadb.org/browse/MDEV-25669))
  * Prior to this release, only the \[`mysqld`] configuration group was checked when processing a configuration file.
* Performance Schema for Enterprise Cluster
  * Performance Schema table [galera\_group\_members](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/performance-schema/performance-schema-tables) logs information about the configuration of the cluster. ([MDEV-286](https://jira.mariadb.org/browse/MDEV-286))
  * Performance Schema table [galera\_group\_member\_stats](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/performance-schema/performance-schema-tables) logs information about the performance characteristics of nodes in the cluster. ([MDEV-286](https://jira.mariadb.org/browse/MDEV-286))

## Interface Changes

The following changes are as compared to MariaDB Enterprise Server 10.5.10-7, the latest GA release on the prior release series.

* For clients such as `mariadb` (`mysql`), the connection property specified via the command-line (such as `--port=3306`) will force the connection type (such as TCP/IP). ([MDEV-14974](https://jira.mariadb.org/browse/MDEV-14974))
* Unchanged metadata is not sent in the result set for prepared statements. ([MDEV-19237](https://jira.mariadb.org/browse/MDEV-19237))
* [ADD\_MONTHS()](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/date-time-functions/add_months) function added
* [binlog\_expire\_logs\_seconds](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/standard-replication/replication-and-binary-log-system-variables) system variable added
* columnstore\_cache\_use\_import system variable added
* columnstore\_decimal\_overflow\_check system variable added
* [Com\_multi](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-status-variables#com_multi) status variable removed
* [ER\_BINLOG\_UNSAFE\_SKIP\_LOCKED](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes/mariadb-error-codes-4100-to-4199/e4175) error code added
* [ER\_BLACKBOX\_ERROR](broken-reference) error code error number changed from 4174 to 6000
* [ER\_JSON\_TABLE\_ALIAS\_REQUIRED](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes/mariadb-error-codes-4100-to-4199/e4177) error code added
* [ER\_JSON\_TABLE\_ERROR\_ON\_FIELD](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes/mariadb-error-codes-4100-to-4199/e4176) error code added
* [ER\_JSON\_TABLE\_MULTIPLE\_MATCHES](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes/mariadb-error-codes-4100-to-4199/e4179) error code added
* [ER\_JSON\_TABLE\_SCALAR\_EXPECTED](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes/mariadb-error-codes-4100-to-4199/e4178) error code added
* [ER\_PK\_INDEX\_CANT\_BE\_IGNORED](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes/mariadb-error-codes-4100-to-4199/e4174) error code added
* [ER\_REMOVED\_ORPHAN\_TRIGGER](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes/mariadb-error-codes-4100-to-4199/e4181) error code added
* [ER\_STORAGE\_ENGINE\_DISABLED](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes/mariadb-error-codes-4100-to-4199/e4182) error code added
* [ER\_UNSUPPORTED\_COMPRESSED\_TABLE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes/mariadb-error-codes-4100-to-4199/e4179) error code replaces [ER\_UNSUPPORT\_COMPRESSED\_TEMPORARY\_TABLE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes/mariadb-error-codes-4000-to-4099/e4047)
* [ER\_UNUSED\_26](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes) error code replaces [ER\_COMMULTI\_BADCONTEXT](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes/mariadb-error-codes-4000-to-4099/e4000)
* [ER\_UNUSED\_27](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes) error code replaces [ER\_BAD\_COMMAND\_IN\_MULTI](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes/mariadb-error-codes-4000-to-4099/e4001)
* [ER\_UNUSED\_28](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes) error code replaces [ER\_TABLE\_IN\_FK\_CHECK](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes/mariadb-error-codes-1700-to-1799/e1725)
* [ER\_WITH\_TIES\_NEEDS\_ORDER](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/mariadb-internals/using-mariadb-with-your-programs-api/error-codes/mariadb-error-codes-4100-to-4199/e4180) error code added
* [expire\_logs\_days](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/standard-replication/replication-and-binary-log-system-variables#expire_logs_days) system variable default value changed from 0 to 0.000000
* [galera\_group\_member\_stats](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/performance-schema/performance-schema-tables) performance schema table added
* [galera\_group\_members](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/performance-schema/performance-schema-tables) performance schema table added
* [host\_summary](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/host_summary-and-xhost_summary-sys-schema-views) sys table added
* [host\_summary\_by\_file\_io](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/host_summary_by_file_io-and-xhost_summary_by_file_io-sys-schema-views) sys table added
* [host\_summary\_by\_file\_io\_type](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/host_summary_by_file_io_type-and-xhost_summary_by_file_io_type-sys-schema-v) sys table added
* [host\_summary\_by\_stages](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/host_summary_by_stages-and-xhost_summary_by_stages-sys-schema-views) sys table added
* [host\_summary\_by\_statement\_latency](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/sys-schema-views-host_summary_by_statement_latency-and-xhost_summary_by_sta) sys table added
* [host\_summary\_by\_statement\_type](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/host_summary_by_statement_type-and-xhost_summary_by_statement_type-sys-sche) sys table added
* `innochecksum` --strict-check (-C) command-line option removed
* `innochecksum` --write (-w) command-line option removed
* [innodb\_adaptive\_max\_sleep\_delay](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_adaptive_max_sleep_delay) system variable removed
* [innodb\_background\_scrub\_data\_check\_interval](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_background_scrub_data_check_interval) system variable removed
* [innodb\_background\_scrub\_data\_compressed](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_background_scrub_data_compressed) system variable removed
* [innodb\_background\_scrub\_data\_interval](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_background_scrub_data_interval) system variable removed
* [innodb\_background\_scrub\_data\_uncompressed](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_background_scrub_data_uncompressed) system variable removed
* [innodb\_buffer\_pool\_instances](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_buffer_pool_instances) system variable removed
* [Innodb\_buffer\_pool\_pages\_lru\_freed](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#Innodb_buffer_pool_pages_lru_freed) status variable added
* [innodb\_buffer\_stats\_by\_schema](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_buffer_stats_by_schema) sys table added
* [innodb\_buffer\_stats\_by\_table](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_buffer_stats_by_table) sys table added
* [innodb\_commit\_concurrency](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_commit_concurrency) system variable removed
* [innodb\_concurrency\_tickets](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_concurrency_tickets) system variable removed
* [innodb\_deadlock\_report](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_deadlock_report) system variable added
* [innodb\_file\_format](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_file_format) system variable removed
* [innodb\_flush\_method](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_flush_method) system variable default value changed from fsync to O\_DIRECT
* [innodb\_large\_prefix](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_large_prefix) system variable removed
* [innodb\_lock\_schedule\_algorithm](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_lock_schedule_algorithm) system variable removed
* [innodb\_lock\_wait\_timeout](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_lock_wait_timeout) system variable maximum value changed from 1073741824 to 100000000
* [innodb\_lock\_waits](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_lock_waits) sys table added
* [innodb\_log\_checksums](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_log_checksums) system variable removed
* [innodb\_log\_compressed\_pages](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_log_compressed_pages) system variable removed
* [innodb\_log\_files\_in\_group](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_log_files_in_group) system variable removed
* [innodb\_log\_optimize\_ddl](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_log_optimize_ddl) system variable removed
* INNODB\_MUTEXES information schema table removed
* INNODB\_MUTEXES plugin removed
* [innodb\_page\_cleaners](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_page_cleaners) system variable removed
* [innodb\_read\_only\_compressed](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_read_only_compressed) system variable added
* [innodb\_replication\_delay](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_replication_delay) system variable removed
* [innodb\_scrub\_log](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_scrub_log) System Variable system variable removed
* [innodb\_scrub\_log\_speed](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_scrub_log_speed) system variable removed
* [innodb\_sync\_array\_size](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_sync_array_size) system variable removed
* INNODB\_SYS\_DATAFILES information schema table removed
* `INNODB_SYS_DATAFILES` plugin removed
* INNODB\_SYS\_SEMAPHORE\_WAITS information schema table removed
* `INNODB_SYS_SEMAPHORE_WAITS` plugin removed
* [innodb\_thread\_concurrency](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_thread_concurrency) system variable removed
* [innodb\_thread\_sleep\_delay](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_thread_sleep_delay) system variable removed
* [innodb\_undo\_logs](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_undo_logs) system variable removed
* [io\_by\_thread\_by\_latency](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/io_by_thread_by_latency-and-xio_by_thread_by_latency-sys-schema-views) sys table added
* [io\_global\_by\_file\_by\_bytes](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/io_global_by_file_by_bytes-and-xio_global_by_file_by_bytes-sys-schema-views) sys table added
* [io\_global\_by\_file\_by\_latency](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/io_global_by_file_by_bytes-and-xio_global_by_file_by_bytes-sys-schema-views) sys table added
* [io\_global\_by\_wait\_by\_bytes](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/io_global_by_wait_by_bytes-and-xio_global_by_wait_by_bytes-sys-schema-views) sys table added
* [io\_global\_by\_wait\_by\_latency](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/io_global_by_wait_by_bytes-and-xio_global_by_wait_by_bytes-sys-schema-views) sys table added
* [JSON\_TABLE()](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/special-functions/json-functions/json_table) function added
* [KEYWORDS](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/information-schema/information-schema-tables/information-schema-keywords-table) information schema table added
* [latest\_file\_io](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/latest_file_io-and-xlatest_file_io-sys-schema-views) sys table added
* `mariadb-backup` [--debug-sleep-before-unlock](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/backing-up-and-restoring-databases/mariadb-backup/mariadb-backup-options#-debug-sleep-before-unlock) command-line option removed
* `mariadb-backup` [--debug-sync](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/backing-up-and-restoring-databases/mariadb-backup/mariadb-backup-options#-debug-sync) command-line option removed
* `mariadb-backup` [--innodb-log-files-in-group](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/backing-up-and-restoring-databases/mariadb-backup/mariadb-backup-options#-innodb-log-files-in-group) command-line option removed
* `mariadbd` [--binlog-expire-logs-seconds](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/standard-replication/replication-and-binary-log-system-variables) command-line option added
* `mariadbd` --columnstore-cache-use-import command-line option added
* `mariadbd` --columnstore-decimal-overflow-check command-line option added
* `mariadbd` [--innodb-adaptive-max-sleep-delay](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_adaptive_max_sleep_delay) command-line option removed
* `mariadbd` [--innodb-background-scrub-data-check-interval](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_background_scrub_data_check_interval) command-line option removed
* `mariadbd` [--innodb-background-scrub-data-compressed](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_background_scrub_data_compressed) command-line option removed
* `mariadbd` [--innodb-background-scrub-data-interval](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_background_scrub_data_interval) command-line option removed
* `mariadbd` [--innodb-background-scrub-data-uncompressed](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_background_scrub_data_uncompressed) command-line option removed
* `mariadbd` [--innodb-buffer-pool-instances](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_buffer_pool_instances) command-line option removed
* `mariadbd` [--innodb-commit-concurrency](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_commit_concurrency) command-line option removed
* `mariadbd` [--innodb-concurrency-tickets](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_concurrency_tickets) command-line option removed
* `mariadbd` [--innodb-deadlock-report](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/storage-engines/innodb/innodb-system-variables#innodb_deadlock_report) command-line option added
* `mariadbd` [--innodb-file-format](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-file-format) command-line option removed
* `mariadbd` [--innodb-large-prefix](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_large_prefix) command-line option removed
* `mariadbd` [--innodb-lock-schedule-algorithm](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_lock_schedule_algorithm) command-line option removed
* `mariadbd` [--innodb-log-checksums](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_log_checksums) command-line option removed
* `mariadbd` [--innodb-log-compressed-pages](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_log_compressed_pages) command-line option removed
* `mariadbd` [--innodb-log-files-in-group](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_log_files_in_group) command-line option removed
* `mariadbd` [--innodb-log-optimize-ddl](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_log_optimize_ddl) command-line option removed
* `mariadbd` [--innodb-mutexes](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/information-schema/information-schema-tables/information-schema-innodb-tables/information-schema-innodb_mutexes-table) command-line option removed
* `mariadbd` [--innodb-page-cleaners](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_page_cleaners) command-line option removed
* `mariadbd` [--innodb-read-only-compressed](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_read_only_compressed) command-line option added
* `mariadbd` [--innodb-replication-delay](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_replication_delay) command-line option removed
* `mariadbd` [--innodb-scrub-log](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_scrub_log) command-line option removed
* `mariadbd` [--innodb-scrub-log-speed](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_scrub_log_speed) command-line option removed
* `mariadbd` [--innodb-sync-array-size](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_sync_array_size) command-line option removed
* `mariadbd` [--innodb-sys-datafiles](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/information-schema/information-schema-tables/information-schema-innodb-tables/information-schema-innodb_sys_datafiles-table) command-line option removed
* `mariadbd` [--innodb-sys-semaphore-waits](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/information-schema/information-schema-tables/information-schema-innodb-tables/information-schema-innodb_sys_semaphore_waits-table) command-line option removed
* `mariadbd` [--innodb-thread-concurrency](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_thread_concurrency) command-line option removed
* `mariadbd` [--innodb-thread-sleep-delay](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_thread_sleep_delay) command-line option removed
* `mariadbd` [--innodb-undo-logs](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-undo-log) command-line option removed
* `mariadbd` [--log-ddl-recovery](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/starting-and-stopping-mariadb/mariadbd-options#log-ddl-recovery) command-line option added
* `mariadbd` [--server-audit-load-on-error](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables) command-line option added
* `mariadbd` [--thread-pool-connections](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/buffers-caches-and-threads/thread-pool) command-line option added
* `mariadbd` [--thread-pool-reshuffle-group-period](https://app.gitbook.com/s/kuTXWg0NDbRx6XUeYpGD/mariadb-enterprise-operator/metrics#mariadb-metrics) command-line option added
* `mariadbd` [--wsrep-certificate-expiration-hours-warning](https://app.gitbook.com/s/kuTXWg0NDbRx6XUeYpGD/mariadb-enterprise-operator/metrics#mariadb-metrics) command-line option added
* `mariadbd` [--wsrep-mode command-line](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/galera-cluster-system-variables#wsrep_mode) option added
* `mariadbd` wsrep-ssl-mode command-line option added
* [max\_recursive\_iterations](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#max_recursive_iterations) system variable default value changed from 4294967295 to 1000 ([MDEV-17239](https://jira.mariadb.org/browse/MDEV-17239))
* [memory\_by\_host\_by\_current\_bytes](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/memory_by_host_by_current_bytes-and-xmemory_by_host_by_current_bytes-views) sys table added
* [memory\_by\_thread\_by\_current\_bytes](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/memory_by_host_by_current_bytes-and-xmemory_by_host_by_current_bytes-views) sys table added
* [memory\_by\_user\_by\_current\_bytes](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/memory_by_host_by_current_bytes-and-xmemory_by_host_by_current_bytes-views) sys table added
* [memory\_global\_by\_current\_bytes](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/memory_by_host_by_current_bytes-and-xmemory_by_host_by_current_bytes-views) sys table added
* [memory\_global\_total](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/performance-schema/performance-schema-tables/performance-schema-memory_summary_global_by_event_name-table) sys table added
* [metrics](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/metrics-sys-schema-view) sys table added
* `MINUS` reserved word added
* `OFFSET` reserved word added
* [old\_mode](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#old_mode) system variable default value changed from "" (empty) to UTF8\_IS\_`UTF8MB3`
* processlist sys table added
* ps\_check\_lost\_instrumentation sys table added
* Resultset\_metadata\_skipped status variable added
* [ROWNUM()](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/secondary-functions/information-functions/rownum) function added
* `ROWNUM` reserved word added
* [schema\_auto\_increment\_columns](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/schema_auto_increment_columns-sys-schema-view) sys table added
* schema\_index\_statistics sys table added
* [schema\_object\_overview](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/schema_object_overview-sys-schema-view) sys table added
* schema\_redundant\_indexes-sys-schema-view sys table added
* [schema\_table\_lock\_waits](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/performance-schema/performance-schema-tables/performance-schema-table_lock_waits_summary_by_table-table) sys table added
* schema\_table\_statistics-sys-schema-view sys table added
* schema\_table\_statistics\_with\_buffer-sys-schema-viewsys table added
* schema\_schema\_tables\_with\_full\_table\_scansobject\_overview-sys-schema-view sys table added
* schema\_unused\_indexes-sys-schema-view sys table added
* server\_audit\_load\_on\_error system variable added
* session sys table added
* session\_ssl\_status sys table added
* [SQL\_FUNCTIONS](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/information-schema/information-schema-tables/information-schema-sql_functions-table) information schema table added
* `sql_mode` value EXTENDED\_ALIASES added
* statement\_analysis sys table added
* statements\_with\_errors\_or\_warnings sys table added
* statements\_with\_full\_table\_scans sys table added
* statements\_with\_runtimes\_in\_95th\_percentile sys table added
* statements\_with\_sorting sys table added
* statements\_with\_temp\_tables sys table added
* \[SYS\_GUID|\[SYS\_GUID()]] function added
* `SYSDATE` reserved word added
* system\_versioning\_asof system variable default value changed from DEFAULT to "" (empty)
* THREAD\_POOL\_CONNECTIONS information schema table added
* `THREAD_POOL_CONNECTIONS` plugin added
* thread\_pool\_reshuffle\_group\_period system variable added
* [TO\_CHAR()](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/string-functions/to_char) function added
* user\_summary sys table added
* user\_summary\_by\_file\_io sys table added
* user\_summary\_by\_file\_io\_type sys table added
* user\_summary\_by\_stages sys table added
* user\_summary\_by\_statement\_latency sys table added
* user\_summary\_by\_statement\_type sys table added
* version sys table added
* wait\_classes\_global\_by\_avg\_latency sys table added
* wait\_classes\_global\_by\_latency sys table added
* waits\_by\_host\_by\_latency sys table added
* waits\_by\_user\_by\_latency sys table added
* waits\_global\_by\_latency sys table added
* wsrep\_certificate\_expiration\_hours\_warning system variable added
* [wsrep\_mode system](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/galera-cluster-system-variables#wsrep_mode) variable added
* wsrep\_ssl\_mode system variable added
* [x$host\_summary](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/host_summary-and-xhost_summary-sys-schema-views) sys table added
* [x$host\_summary\_by\_file\_io](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/host_summary_by_file_io-and-xhost_summary_by_file_io-sys-schema-views) sys table added
* [x$host\_summary\_by\_file\_io\_type](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/host_summary_by_file_io_type-and-xhost_summary_by_file_io_type-sys-schema-v) sys table added
* [x$host\_summary\_by\_stages](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/host_summary_by_stages-and-xhost_summary_by_stages-sys-schema-views) sys table added
* [x$host\_summary\_by\_statement\_latency](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/sys-schema-views-host_summary_by_statement_latency-and-xhost_summary_by_sta) sys table added
* [x$host\_summary\_by\_statement\_type](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/sys-schema-views-host_summary_by_statement_latency-and-xhost_summary_by_sta) sys table added
* hinnodb\_buffer\_stats\_by\_schema-and-xinnodb\_buffer\_stats\_by\_schema-sys-schema-views sys table added
* [x$innodb\_buffer\_stats\_by\_table](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/innodb_buffer_stats_by_table-and-xinnodb_buffer_stats_by_table-sys-schema-v) sys table added
* [x$innodb\_lock\_waits](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/innodb_lock_waits-and-xinnodb_lock_waits-sys-schema-views) sys table added
* [x$io\_by\_thread\_by\_latency](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/io_by_thread_by_latency-and-xio_by_thread_by_latency-sys-schema-views) sys table added
* [x$io\_global\_by\_file\_by\_bytes](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/io_global_by_file_by_bytes-and-xio_global_by_file_by_bytes-sys-schema-views) sys table added
* io\_global\_by\_file\_by\_latency-and-xio\_global\_by\_file\_by\_latency-sys-schema-views sys table added
* [x$io\_global\_by\_wait\_by\_bytes](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/io_global_by_wait_by_bytes-and-xio_global_by_wait_by_bytes-sys-schema-views) sys table added
* io\_global\_by\_wait\_by\_latency-and-xio\_global\_by\_wait\_by\_latency-sys-schema-views sys table added
* [x$latest\_file\_io](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/sys-schema/sys-schema-views/latest_file_io-and-xlatest_file_io-sys-schema-views) sys table added
* memory\_by\_host\_by\_current\_bytes-and-xmemory\_by\_host\_by\_current\_bytes-sys-schema-views sys table added
* memory\_by\_thread\_by\_current\_bytes-and-xmemory\_by\_thread\_by\_current\_bytes-sys-schema-views sys table added
* memory\_by\_user\_by\_current\_bytes-and-xmemory\_by\_user\_by\_current\_bytes-sys-schema-views sys table added
* memory\_global\_by\_current\_bytes-and-xmemory\_global\_by\_current\_bytes-sys-schema-views sys table added
* memory\_global\_total-and-xmemory\_global\_total-sys-schema-views sys table added
* processlist-and-xprocesslist-sys-schema-views sys table added
* ps\_digest\_95th\_percentile\_by\_avg\_usy-and-xps\_digest\_95th\_percentile\_by\_avg\_us-sys-schema-views sys table added
* hps\_digest\_avg\_latency\_distribution-and-xps\_digest\_avg\_latency\_distribution-sys-schema-views sys table added
* ps\_schema\_table\_statistics\_io-and-xps\_schema\_table\_statistics\_io-sys-schema-views sys table added
* schema\_flattened\_keys-and-xschema\_flattened\_keys-sys-schema-views sys table added
* schema\_index\_statistics-and-xschema\_index\_statistics-sys-schema-views sys table added
* schema\_table\_lock\_waits-and-xschema\_table\_lock\_waits-sys-schema-views sys table added
* schema\_table\_statistics-and-xschema\_table\_statistics-sys-schema-views sys table added
* schema\_table\_statistics\_with\_buffer-and-xschema\_table\_statistics\_with\_buffer-sys-schema-views sys table added
* schema\_tables\_with\_full\_table\_scans-and-xschema\_tables\_with\_full\_table\_scans-sys-schema-views sys table added
* session-and-xsession-sys-schema-views sys table added
* statement\_analysis-and-xstatement\_analysis-sys-schema-views sys table added
* statements\_with\_errors\_or\_warnings-and-xstatements\_with\_errors\_or\_warnings-sys-schema-views sys table added
* statements\_with\_full\_table\_scans-and-xstatements\_with\_full\_table\_scans-sys-schema-views sys table added
* statements\_with\_runtimes\_in\_95th\_percentile-and-xstatements\_with\_runtimes\_in\_95th\_percentile-sys-schema-view sys table added
* statements\_with\_sorting-and-xstatements\_with\_sorting-sys-schema-views sys table added
* statements\_with\_temp\_tables-and-xstatements\_with\_temp\_tables-sys-schema-views sys table added
* user\_summary-and-xuser\_summary-sys-schema-views sys table added
* user\_summary\_by\_file\_io-and-xuser\_summary\_by\_file\_io-sys-schema-views sys table added
* user\_summary\_by\_file\_io\_type-and-xuser\_summary\_by\_file\_io\_type-sys-schema-views sys table added
* user\_summary\_by\_stages-and-xuser\_summary\_by\_stages-sys-schema-views sys table added
* user\_summary\_by\_statement\_latency-and-xuser\_summary\_by\_statement\_latency-sys-schema-views sys table added
* user\_summary\_by\_statement\_type-and-xuser\_summary\_by\_statement\_type-sys-schema-views sys table added
* wait\_classes\_global\_by\_avg\_latency-and-xwait\_classes\_global\_by\_avg\_latency-sys-schema-views) sys table added
* wait\_classes\_global\_by\_latency-and-xwait\_classes\_global\_by\_latency-sys-schema-views sys table added
* waits\_by\_host\_by\_latency-and-xwaits\_by\_host\_by\_latency-sys-schema-views sys table added
* waits\_by\_user\_by\_latency-and-xwaits\_by\_user\_by\_latency-sys-schema-views sys table added
* waits\_global\_by\_latency-and-xwaits\_global\_by\_latency-sys-schema-views sys table added

## Platforms

In alignment to the [enterprise lifecycle](../enterprise-server-lifecycle.md), MariaDB Enterprise Server 10.6.4-1 is provided for:

* CentOS 7
* Debian 9
* Debian 10
* Microsoft Windows
* Red Hat Enterprise Linux 7
* Red Hat Enterprise Linux 8
* SUSE Linux Enterprise Server 12
* SUSE Linux Enterprise Server 15
* Ubuntu 18.04
* Ubuntu 20.04

Some components of MariaDB Enterprise Server might not support all platforms. For additional information, see "[MariaDB Corporation Engineering Policies](https://mariadb.com/engineering-policies)".

## Installation Instructions

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
