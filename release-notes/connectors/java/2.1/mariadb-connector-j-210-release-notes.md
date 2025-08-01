# Connector/J 2.1.0 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/2.1.0/)[Release Notes](mariadb-connector-j-210-release-notes.md)[Changelog](../changelogs/2.1/mariadb-connector-j-210-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 31 July 2017

MariaDB Connector/J 2.1.0 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_\
release.

**For an overview of MariaDB Connector/J see the**[**About MariaDB Connector/J**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md) **page**

## Notable Changes

This version is a general availability (GA) release.\
(2.x version need java 8+)

## Notable changes and additions

### [CONJ-422](https://jira.mariadb.org/browse/CONJ-422) : verification of SSL Certificate Name Mismatch

When using ssl, driver check hostname against the server's identity as presented in the server's Certificate (checking alternative names or certificate CN) to prevent man-in-the-middle attack.\
Verification is disabled when the option "trustServerCertificate" is set.

A new option "disableSslHostnameVerification" permit to deactivate this validation.

### [CONJ-400](https://jira.mariadb.org/browse/CONJ-400) - Galera validation

When configuration with multi-master, Connection.isValid() will not only validate connection, but host state (@@wsrep\_cluster\_status).\
A connection to a node that is not in primary mode will return false (meaning that in pool, connection will be discarded)

### [CONJ-322](https://jira.mariadb.org/browse/CONJ-322) - ResultSet.update\* methods implementation

ResultSet.update\* methods aren't implemented\
statement using ResultSet.CONCUR\_UPDATABLE are now able to update record.\
example:

```java
Statement stmt = con.createStatement(
                                  ResultSet.TYPE_SCROLL_INSENSITIVE,
                                  ResultSet.CONCUR_UPDATABLE);
    ResultSet rs = stmt.executeQuery("SELECT age FROM TABLE2");
    // rs will be scrollable, will not show changes made by others,
    // and will be updatable
    while(rs.next()){
        //Retrieve by column name
        int newAge = rs.getInt(1) + 5;
        rs.updateDouble( 1 , newAge );
        rs.updateRow();
    }
```

### [CONJ-389](https://jira.mariadb.org/browse/CONJ-389) - faster batch insert

Use dedicated [COM\_STMT\_BULK\_EXECUTE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/clientserver-protocol/3-binary-protocol-prepared-statements/com_stmt_bulk_execute) protocol for batch insert when possible.\
(batch without Statement.RETURN\_GENERATED\_KEYS and streams) to have faster batch (significant only if server >= [MariaDB 10.2.7](../../../community-server/old-releases/release-notes-mariadb-10-2-series/mariadb-1027-release-notes.md)).

A new option "useBulkStmts" permit to deactivate this functionality.

### other evolution

* \[[CONJ-508](https://jira.mariadb.org/browse/CONJ-508)] Connection.getCatalog() optimisation for 10.2+ server using new session\_track\_schema capabilities
* \[[CONJ-492](https://jira.mariadb.org/browse/CONJ-492)] Failover handle automatic reconnection on KILL command

### Bug

* \[[CONJ-502](https://jira.mariadb.org/browse/CONJ-502)] isolation leak when using multiple pools on same VM on failover
* \[[CONJ-503](https://jira.mariadb.org/browse/CONJ-503)] regression on aurora Connection Connection.isReadOnly()
* \[[CONJ-505](https://jira.mariadb.org/browse/CONJ-505)] correcting issue that ended throwing "Unknown prepared statement handler given to mysqld\_stmt\_execute"
* \[[CONJ-496](https://jira.mariadb.org/browse/CONJ-496)] return rounded numeric when querying on a decimal field in place of throwing an exception for compatibility

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
