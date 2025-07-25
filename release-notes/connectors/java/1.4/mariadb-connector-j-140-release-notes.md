# Connector/J 1.4.0 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/1.4.0/)[Release Notes](mariadb-connector-j-140-release-notes.md)[Changelog](../changelogs/1.4/mariadb-connector-j-140-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md)

**Release date:** 1 Apr 2016

**An issue was reported as a "Blocker" in this version. Please use the corrected version 1.4.3.**\
Issue resolution in MariaDB is visible through the corresponding ticket in MariaDB’s tracking system (JIRA): [CONJ-284](https://jira.mariadb.org/browse/CONJ-284)

**For a description of MariaDB Connector/J see the**[**About MariaDB Connector/J**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md) **page**

For a list of all changes made in this release, with links to detailed\
information on each push, see the[changelog](../changelogs/1.4/mariadb-connector-j-140-changelog.md).

This version is a bugfix / performance improvement release.

## Notable changes and additions

### Complete implementation of fetch size

[CONJ-26](https://jira.mariadb.org/browse/CONJ-26)\
JDBC allows specifying the number of rows fetched for a query, and this number is referred to as the fetch size.\
Before version 1.4.0, queries were loading all results or row by row using `Statement.setFetchSize(Integer.MIN_VALUE)`.\
Now it's possible to set the fetch size according to your needs.\
Loading all results for large result sets uses a lot of memory. This functionality permits saving memory without a performance decrease.

### Memory footprint improvement

[CONJ-125](https://jira.mariadb.org/browse/CONJ-125) - Buffers have been optimized to reduced memory footprint

### CallableStatement performance improvement

[CONJ-209](https://jira.mariadb.org/browse/CONJ-209) - Calling function / procedure performance is now optimized according to the query. Depending on the queries, the difference can be up to 300%.

### Authentication evolution

[CONJ-251](https://jira.mariadb.org/browse/CONJ-251) Permit new authentication possibilities : [PAM authentication](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/plugins/authentication-plugins/authentication-with-pluggable-authentication-modules-pam/authentication-plugin-pam), and GSSAPI/SSPI authentication.

The GSSAPI/SSPI authentication plugin for MariaDB permits passwordless login.

On Unix systems, GSSAPI is usually synonymous with Kerberos authentication. Windows has a slightly different but very similar API called SSPI that, along with Kerberos, also supports NTLM authentication.

See more details at: [GSSAPI/SSPI configuration](https://github.com/MariaDB/mariadb-connector-j/blob/master/documentation/plugin/GSSAPI.creole)

### Connection attributes

[CONJ-217](https://jira.mariadb.org/browse/CONJ-217) - Driver information is now sent to [connection attributes tables](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/system-tables/performance-schema/performance-schema-tables/performance-schema-session_connect_attrs-table) (performance\_schema must be activated).\
A new option "connectionAttributes" permits adding client-specific data.

For example when connecting with the following connection string `"jdbc:mysql://localhost:3306/testj?user=root&connectionAttributes=myOption:1,mySecondOption:'jj'"`,\
if performance\_schema is activated, information about this connection will be available during the time this connection is active :

```sql
SELECT * FROM performance_schema.session_connect_attrs WHERE processList_id = 5
```

```
+----------------+-----------------+---------------------+------------------+
| PROCESSLIST_ID | ATTR_NAME       | ATTR_VALUE          | ORDINAL_POSITION |
+----------------+-----------------+---------------------+------------------+
|5               |_client_name     |MariaDB connector/J  |0                 |
|5               |_client_version  |1.4.0-SNAPSHOT       |1                 |
|5               |_os              |Windows 8.1          |2                 | 
|5               |_pid             |14124@portable-diego |3                 |
|5               |_thread          |5                    |4                 |
|5               |_java_vendor     |Oracle Corporation   |5                 |
|5               |_java_version    |1.7.0_79             |6                 |
|5               |myOption         |1                    |7                 |
|5               |mySecondOption   |'jj'                 |8                 |
+----------------+-----------------+---------------------+------------------+
```

### Minor evolution

* [CONJ-210](https://jira.mariadb.org/browse/CONJ-210) : adding a "jdbcCompliantTruncation" option to force truncation warning as an SQLException.
* [CONJ-211](https://jira.mariadb.org/browse/CONJ-211) : when in master/slave configuration, option "assureReadOnly" will ensure that slaves are in read-only mode ( forcing transaction by a query "SET SESSION TRANSACTION READ ONLY").
* [CONJ-213](https://jira.mariadb.org/browse/CONJ-213) : new option "continueBatchOnError". Permit to continue batch when an exception occur : When executing a batch and an error occur, must the batch stop immediatly (default) or finish remaining batch before throwing exception.

### Bugfix

* [CONJ-236](https://jira.mariadb.org/browse/CONJ-236) : Using a parametrized query with a smallint -1 does return the unsigned value
* [CONJ-250](https://jira.mariadb.org/browse/CONJ-250) : Tomcat doesn't stop when using Aurora failover configuration
* [CONJ-269](https://jira.mariadb.org/browse/CONJ-269) : handle server configuration autocommit=0
* [CONJ-271](https://jira.mariadb.org/browse/CONJ-271) : ResultSet.first() may throw SQLDataException: Current position is before the first row

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
