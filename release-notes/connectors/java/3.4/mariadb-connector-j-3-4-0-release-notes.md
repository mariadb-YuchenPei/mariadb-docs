# Connector/J 3.4.0 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://mariadb.com/downloads/connectors/connectors-data-access/java8-connector)[Release Notes](mariadb-connector-j-3-4-0-release-notes.md)[Changelog](../changelogs/3.4/mariadb-connector-j-3-4-0-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md)

**Release date:** 17 May 2024

MariaDB Connector/J 3.4.0 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release, and replaces 3.3 as the maintenance releases.

**For an overview of MariaDB Connector/J see the**[**About MariaDB Connector/J**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md) **page**

## Notable Changes

### [CONJ-1105](https://jira.mariadb.org/browse/CONJ-1105) ZERO-CONFIGURATION SSL ENCRYPTION

Using SSL (a more correct term would be TLS, but in reality SSL is more commonly used) has been simplified with [MariaDB Server 11.4](https://mariadb.com/resources/blog/announcing-mariadb-community-server-11-3-ga-and-11-4-rc/). Before version 11.4, proper SSL configuration required multiple manual steps for the server and all the clients connecting to it.

For MariaDB Connector/J before 3.4 to establish an SSL encrypted connection, or a MariaDB Server release series previous to 11.4, three options can be used:

* Have server certificates generated with trusted Certificate Authorities (CA), using a configuration like: `sslMode=verify-full`
* Configure the connector using a server certificate, like: `sslMode=verify-full&serverSslCert=file:///server-cert.pem`
* Disable the verification of the SSL certificate, which is insecure and not recommended, using a configuration like: `sslMode=trust`

For MariaDB Connector/J 3.4 to establish an SSL encrypted connection to MariaDB Server 11.4, enabling SSL does not require any special configuration apart from using sslMode=verify-full. The connector doesn't need to know the server certificate anymore, as long as the password is not empty.

### [CONJ-1171](https://jira.mariadb.org/browse/CONJ-1171) Changes to Timezone Configuration Options for TIMESTAMPS

The MariaDB Connector/J versions before 3.4 provide a single "timezone" option for working with different time zones for clients and servers. While this functionality remains compatible, it's now separated into two distinct settings:

* connectionTimeZone
* forceConnectionTimeZoneToSession

There are now 3 options that control timestamps behavior in the java connector:

* connectionTimeZone: (LOCAL | SERVER | ) This option defines the connection's time zone. LOCAL retrieves the JVM's default time zone, SERVER fetches the server's global time zone upon connection creation, and allows specifying a server time zone without requesting it during connection establishment.
* forceConnectionTimeZoneToSession: (true | false) This setting dictates whether the connector enforces the connection time zone for the session.
* preserveInstants: (true | false) This option controls whether the connector converts Timestamp values to the connection's time zone.

While remaining compatible with previous versions, this permits more flexibility when handling timezone difference scenarios. See [timezone documentation](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-j/about-mariadb-connector-j#timezone-consideration) for detailed information.

### [CONJ-981](https://jira.mariadb.org/browse/CONJ-981) Add support for connection redirection

Since [MariaDB 10.3.1](../../../community-server/old-releases/release-notes-mariadb-10-3-series/mariadb-1031-release-notes.md), the server has a new system variable redirect\_url to provide a connection string using the forma `mariadb/mysql://[<user>[:<password>]@]<host>[:<port>]/[<db>[?<opt1>=<value1>[&<opt2>=<value2>]]]`.

When set, all existing connections will be redirected to the designated URL values when appropriate. A connection will only be redirected when no transaction is active.

Example for enabling the redirection:`set @@global.redirect_url="mariadb://somehost:3306/"`

The redirection feature is enabled by default. It can be disabled by setting the new option permitRedirect to FALSE, which will result in ignoring the redirection URL.

### [CONJ-1154](https://jira.mariadb.org/browse/CONJ-1154) Reduced overhead for issuing queries for retrieving and setting isolation level metadata

When session tracking is supported by the MariaDB Server release series, Connection.getTransactionIsolation() won’t query the server as the current state is already known from the session tracking information. Connection.setTransactionIsolation will skip the query to set the transaction isolation level if the server is already using the requested transaction isolation level.

## Bugs Fixed

* [CONJ-1103](https://jira.mariadb.org/browse/CONJ-1103) Connector/J Version 3 Does Not Respect "nullCatalogMeansCurrent" Property
* [CONJ-1161](https://jira.mariadb.org/browse/CONJ-1161) Database connection failing on android
* [CONJ-1107](https://jira.mariadb.org/browse/CONJ-1107) MariaDB Connector 3 no longer supports query timeout with MySQL
* [CONJ-1125](https://jira.mariadb.org/browse/CONJ-1125) Inconsistency in Handling PreparedStatement.executeQuery() between MariaDB and MySQL Connectors
* [CONJ-1156](https://jira.mariadb.org/browse/CONJ-1156) getTables should be ordered as expected
* [CONJ-1163](https://jira.mariadb.org/browse/CONJ-1163) jdbcCompliantTruncation Does Not Appear To Be Working
* [CONJ-1164](https://jira.mariadb.org/browse/CONJ-1164) Variable initialization ahead of LOAD DATA INFILE not possible by validateLocalFileName pattern
* [CONJ-1168](https://jira.mariadb.org/browse/CONJ-1168) useBulkStmts compatibility value with pre 3.2 version
* [CONJ-1169](https://jira.mariadb.org/browse/CONJ-1169) improve Client prepared statement setMaxRows implementation
* [CONJ-1170](https://jira.mariadb.org/browse/CONJ-1170) OFFSET missing from getSQLKeywords
* [CONJ-1158](https://jira.mariadb.org/browse/CONJ-1158) DatabaseMetaData#getFunctions's result not property ordered
* [CONJ-1159](https://jira.mariadb.org/browse/CONJ-1159) DatabaseMetaData#getClientInfoProperties not ordered correctly
* [CONJ-1166](https://jira.mariadb.org/browse/CONJ-1166) Implement connection properties fallbackToSystemKeyStore and fallbackToSystemTrustStore
* [CONJ-1173](https://jira.mariadb.org/browse/CONJ-1173) Bulk implementation returning individual results
* [CONJ-1174](https://jira.mariadb.org/browse/CONJ-1174) ConnectorJ gives precision of 20 for signed bigint
* [CONJ-1100](https://jira.mariadb.org/browse/CONJ-1100) Be able to filter system tables and views

## Changelog

For a complete list of changes made in MariaDB Connector/J 3.4.0, with links to detailed\
information on each push, see the [changelog](../changelogs/3.4/mariadb-connector-j-3-4-0-changelog.md).

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
