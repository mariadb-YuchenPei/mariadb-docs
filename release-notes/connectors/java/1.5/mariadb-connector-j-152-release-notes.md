# Connector/J 1.5.2 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/1.5.2/)[Release Notes](mariadb-connector-j-152-release-notes.md)[Changelog](../changelogs/1.5/mariadb-connector-j-152-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md)

**Release date:** 1 Sep 2016

MariaDB Connector/J 1.5.2 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_\
release.

**For a description of MariaDB Connector/J see the**[**About MariaDB Connector/J**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md) **page**

## Notable Changes

This version is a feature release.

### Use native SSPI windows implementation

[CONJ-295](https://jira.mariadb.org/browse/CONJ-295).

kerberos implementation on windows has java limitations. Main limitations are :

* need a windows registry entry (HKEY\_LOCAL\_MACHINE\System\CurrentControlSet\Control\Lsa\Kerberos\Parameters\AllowTGTSessionKey) so windows shared current ticket to java.
* java kinit must be executed to create a Ticket.
* restriction when client with local admin rights

See [see openJDK issue](https://bugs.openjdk.java.net/browse/JDK-6722928) for more informations

Kerberos GSSAPI implementation on windows in now based on [Waffle](https://github.com/dblock/waffle) that support windows SSPI based on [JNA](https://github.com/java-native-access/jna).\
If waffle-jna (and dependencies) is on classpath, native implementation will automatically be used.

This removes all those limitations.

### Support for TLSv1.1 and TLSv1.2

[CONJ-249](https://jira.mariadb.org/browse/CONJ-249)/[CONJ-301](https://jira.mariadb.org/browse/CONJ-301)

Driver before version 1.5 support only TLSv1.\
Default supported protocol are now TLSv1 and TLSv1.1, other protocols can be activated by options.

MariaDB and MySQL community server permit TLSv1 and TLSv1.1.\
MariaDB server from version 10.0.15 is using the openSSL library permitting TLSv1.2 (>= 5.5.41 for the 5.5 branch)._YaSSL doesn't support TLSv1.2, so if MariaDB server is build from sources with YaSSL, only TLSv1 and TLSv1.1 will be available, even for versions > 10.0.15_

TLSv1.2 can be enabled by setting option `enabledSslProtocolSuites` to values `"TLSv1, TLSv1.1, TLSv1.2"`.

A new option `enabledSslCipherSuites` permits setting a specific cipher.

New Options :

| enabledSslProtocolSuites | enabledSslCipherSuites                                                                                                                                                                |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| enabledSslProtocolSuites | Force TLS/SSL protocol to a specific set of TLS versions (comma separated list). Example : "TLSv1, TLSv1.1, TLSv1.2" Default: TLSv1, TLSv1.1. Since 1.5.0                             |
| enabledSslCipherSuites   | Force TLS/SSL cipher (comma separated list). Example : "TLS\_DHE\_RSA\_WITH\_AES\_256\_GCM\_SHA384, TLS\_DHE\_DSS\_WITH\_AES\_256\_GCM\_SHA384" Default: use JRE ciphers. Since 1.5.0 |

### Performance improvements

[CONJ-291](https://jira.mariadb.org/browse/CONJ-291)

Different performance improvements have been implemented :

* Using PreparedStatement on client side uses a simple query parser to identify query parameters. This parsing was taking up to 7% of query time, reduced to 3%.
* Better UTF-8 decoding avoiding memory consumption and gaining 1-2% query time for big String.
* client parsing optimization : rewriteBatchedStatements (`insert into ab (i) values (1)` and `insert into ab (i) values (2)` rewritten as `insert into ab (i) values (1), (2)`)\
  is now 19% faster (Depending on queries 40-50% of CPU time was spent testing that the buffer size was big enough to contain the query)
* there was some memory wastage when a query returned a big resultset (> 10kb), slowing the query
* and many more

[CONJ-320](https://jira.mariadb.org/browse/CONJ-320)\
Batch improvement :\
Send X command without reading results, and read those X results asynchronously.\
Basically that permits avoiding a lot of 'ping-pong' between driver and server.

New Options :

| useBatchMultiSend       | useBatchMultiSendNumber                                                                                        |
| ----------------------- | -------------------------------------------------------------------------------------------------------------- |
| useBatchMultiSend       | PreparedStatement.executeBatch() will send many QUERY before reading result packets.Default: true. Since 1.5.0 |
| useBatchMultiSendNumber | When using useBatchMultiSend, indicate maximum query that can be send at a time.Default: 100. Since 1.5.0      |

### Prepare + execute in one call

[CONJ-296](https://jira.mariadb.org/browse/CONJ-296)

When using MySQL/MariaDB prepared statements, there are 3 exchanges with server :

* PREPARE - Prepares statement for execution.
* EXECUTE - Executes a prepared statement preparing by a PREPARE statement.
* DEALLOCATE PREPARE - Releases a prepared statement.

See [Server prepare documentation](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/prepared-statements/prepare-statement) for more information.

Since [MariaDB 10.2.2](../../../community-server/old-releases/release-notes-mariadb-10-2-series/mariadb-1022-release-notes.md), the last PREPARE statement id can be identified with value "-1".\
The driver uses this functionality to PREPARE and EXECUTE in one client-server round-trip.

### Client logging

Client logging can be enabled, permitting logging of query information, execution time and different failover information.\
This implementation needs the standard SLF4J dependency.

New Options :

| log                     | maxQuerySizeToLog                                                                                                                                                                                                | slowQueryThresholdNanos | profileSql |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------- | ---------- |
| log                     | Enable log information. require Slf4j version > 1.4 dependency.Default: false. Since 1.5.0                                                                                                                       |                         |            |
| maxQuerySizeToLog       | Only the first characters corresponding to this options size will be displayed in logsDefault: 1024. Since 1.5.0                                                                                                 |                         |            |
| slowQueryThresholdNanos | Will log query with execution time superior to this value (if defined )Default: 1024. Since 1.5.0                                                                                                                |                         |            |
| profileSql              | log connection id, query and execution time.log example : 2016-07-29 23:28:50 \[main] INFO org.mariadb.jdbc.MariaDbStatement - Query - conn:10295 - 0,309 ms - "select \* from TABLE"Default: false. Since 1.5.0 |                         |            |

### Aurora host auto-discovery

([CONJ-325](https://jira.mariadb.org/browse/CONJ-325))

Aurora now auto discovers nodes from the cluster endpoint.

**Aurora endpoints**

Every aurora instance has a specific endpoint, i.e. a URL that identifies the\
host. These endpoints look like `xxx.yyy.zzz.rds.amazonaws.com`.

There is another endpoint named "cluster endpoint" (format`xxx.cluster-yyy.zzz.rds.amazonaws.com`) which is assigned to the current\
master instance and will change when a new master is promoted.

In previous versions, cluster endpoint use was discouraged, since, when a\
failover occurs, this cluster endpoint can point for a limited time to a host\
that is no longer the current master. The old recommendation was to list all\
specific end-points, like:

```java
jdbc:mysql:aurora://a.yyy.zzz.rds.amazonaws.com.com,b.yyy.zzz.rds.amazonaws.com.com/db
```

This kind of URL string will still work, but now the recommended URL string only has to use the cluster endpoint:

```java
jdbc:mysql:aurora://xxx.cluster-yyy.zzz.rds.amazonaws.com/db
```

The driver will automatically discover master and slaves of this cluster from\
the current cluster endpoint during connection time. This permits adding new\
replicas to the cluster instance that will be discovered without changing the\
driver configuration.

This discovery appends at connection time, so if you are using a pool\
framework, check if this framework has a property that controls the maximum\
lifetime of a connection in the pool, and set a value to avoid infinite\
lifetime. When this lifetime is reached, the pool will discarded for the\
current connection, and will create a new one (if needed). New connections will\
use the new replicas.

(If connections are never discarded, new replicas will begin to be used only\
when a failover occurs.)

### "LOAD DATA INFILE" Interceptors

[CONJ-305](https://jira.mariadb.org/browse/CONJ-305)\
LOAD DATA INFILE The fastest way to load most data is using the query [LOAD DATA INFILE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/inserting-loading-data/load-data-into-tables-or-index/load-data-infile).\
The problem is using "LOAD DATA LOCAL INFILE" (ie : loading a file from client), may be a security problem :

* A "man in the middle" proxy server can change the actual file asked from server so client will send a Local file to this proxy.
* If someone has can execute a query from the client, he can have access to any file on client (according to the rights of the user running the client process).

See the [load-data-infile documentation](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/inserting-loading-data/load-data-into-tables-or-index/load-data-infile) for more information.

Interceptors can now filter the LOAD DATA LOCAL INFILE query's file location to validate the path and file name.\
Those interceptors:

* Must implement interface `org.mariadb.jdbc.LocalInfileInterceptor`.
* Use [ServiceLoader](https://docs.oracle.com/javase/7/docs/api/java/util/ServiceLoader.html) implementation, so interceptors classes must be listed in file META-INF/services/org.mariadb.jdbc.LocalInfileInterceptor.

Example:

```java
package org.project;
public class LocalInfileInterceptorImpl implements LocalInfileInterceptor {
    @Override
    public boolean validate(String fileName) {
        File file = new File(fileName);
        String absolutePath = file.getAbsolutePath();
        String filePath = absolutePath.substring(0,absolutePath.lastIndexOf(File.separator));
        return filePath.equals("/var/tmp/exchanges");
    }
}
```

file META-INF/services/org.mariadb.jdbc.LocalInfileInterceptor must exist with content `org.project.LocalInfileInterceptorImpl`.

You can get rid of defining the META-INF/services file using the [google auto-service](https://github.com/google/auto/tree/master/service) framework, which allows using the annotation `@AutoService(LocalInfileInterceptor.class)` that will register the implementation as a service automatically.

Using the previous example:

```java
@AutoService(LocalInfileInterceptor.class)
public class LocalInfileInterceptorImpl implements LocalInfileInterceptor {
    @Override
    public boolean validate(String fileName) {
        File file = new File(fileName);
        String absolutePath = file.getAbsolutePath();
        String filePath = absolutePath.substring(0,absolutePath.lastIndexOf(File.separator));
        return filePath.equals("/var/tmp/exchanges");
    }
}
```

### Minor evolution

* [CONJ-260](https://jira.mariadb.org/browse/CONJ-260) : Add jdbc nString, nCharacterStream, nClob implementation

### Bugfixes

* [CONJ-316](https://jira.mariadb.org/browse/CONJ-316) : Wrong Exception thrown for ScrollType TYPE\_SCROLL\_INSENSITIVE
* [CONJ-298](https://jira.mariadb.org/browse/CONJ-298) : Error on Callable function exception when no parameter and space before parenthesis
* [CONJ-314](https://jira.mariadb.org/browse/CONJ-314) : Permit using Call with Statement / Prepare Statement
* [CONJ-329](https://jira.mariadb.org/browse/CONJ-329) and [CONJ-330](https://jira.mariadb.org/browse/CONJ-330) : rewriteBatchedStatements execute single query exceptions correction.
* [CONJ-331](https://jira.mariadb.org/browse/CONJ-331) : clearWarnings() now throw exception on closed connection
* [CONJ-299](https://jira.mariadb.org/browse/CONJ-299) : PreparedStatement.setObject(Type.BIT, "1") registered as true.
* [CONJ-293](https://jira.mariadb.org/browse/CONJ-293) : permit named pipe connection without host
* [CONJ-333](https://jira.mariadb.org/browse/CONJ-333) : ResultSet.getString() of PreparedStatement return NULL When TIME column value=00:00:00

RC corrections

* [CONJ-335](https://jira.mariadb.org/browse/CONJ-335) : Pool connection may fail to connect with good user
* [CONJ-332](https://jira.mariadb.org/browse/CONJ-332) : option enabledSslCipherSuites rely on java supportedCipherSuites (replacing enabledCipherSuites)
* UTF-8 conversion correction (last character was not well encode if high surrogate)

## Changelogs

For a list of all changes made in this release, with links to detailed\
information on each push, see the Connector/J 1.5.x changelogs:

* [MariaDB Connector/J 1.5.0 Changelog](../changelogs/1.5/mariadb-connector-j-150-changelog.md)
* [MariaDB Connectot/J 1.5.1 Changelog](../changelogs/1.5/mariadb-connector-j-151-changelog.md)
* [MariaDB Connectot/J 1.5.2 Changelog](../changelogs/1.5/mariadb-connector-j-152-changelog.md)

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
