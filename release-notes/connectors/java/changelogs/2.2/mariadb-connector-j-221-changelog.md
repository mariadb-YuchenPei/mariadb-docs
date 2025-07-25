# MariaDB Connector/J 2.2.1 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/2.2.1/)[Release Notes](../../2.2/mariadb-connector-j-221-release-notes.md)[Changelog](mariadb-connector-j-221-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 22 Dec 2017

For the highlights of this release, see the[release notes](../../2.2/mariadb-connector-j-221-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On[GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #c38d910e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c38d910e) - bump 2.2.1 version
* [Revision #a7bbd776](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a7bbd776) - \[misc] remove debug log from travis logs
* [Revision #a94ed403](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a94ed403) - \[travis] test with profileSql correction
* [Revision #926ed32f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/926ed32f) - \[travis] travis galera test use only one galera node to avoid memory issues when 3 galera node on travis VM
* [Revision #ab932c22](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ab932c22) - \[travis] ensure having no test false-positive result using PROFILE configuration
* [Revision #4093cbed](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4093cbed) - \[travis] galera docker configuration correction
* [Revision #b8386dd1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b8386dd1) - \[travis] galera test correction
* [Revision #e7bf0416](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e7bf0416) - \[[CONJ-558](https://jira.mariadb.org/browse/CONJ-558)] testing difference correction in getString() for float data
* [Revision #0eeeb778](https://github.com/mariadb-corporation/mariadb-connector-j/commit/0eeeb778) - \[[CONJ-558](https://jira.mariadb.org/browse/CONJ-558)] correct leading zero test when using binary protocol
* [Revision #d74681fa](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d74681fa) - \[misc] galera complete test integration - 4th part
* [Revision #6856112c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6856112c) - \[misc] ensure checkstyle compliance
* [Revision #f0b621f1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f0b621f1) - \[[CONJ-558](https://jira.mariadb.org/browse/CONJ-558)] ResultSet.getString() values on double/float values doesn't finish by '.0' for integer numbers
* [Revision #95c0ac96](https://github.com/mariadb-corporation/mariadb-connector-j/commit/95c0ac96) - \[misc] galera complete test integration - third part
* [Revision #e1d6c569](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e1d6c569) - \[misc] galera complete test integration - second part
* [Revision #4eebe7d7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4eebe7d7) - \[misc] galera complete test integration
* [Revision #c13206a2](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c13206a2) - \[misc] pool implementation correction when connection validation fail. Connection was still counted in available connection counter
* [Revision #69ae8619](https://github.com/mariadb-corporation/mariadb-connector-j/commit/69ae8619) - \[misc] galera validation correction
* [Revision #f8d119ad](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f8d119ad) - \[[CONJ-553](https://jira.mariadb.org/browse/CONJ-553)] cancel one travis test for aurora since cannot change max\_connection just for testing
* [Revision #f5d227dd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f5d227dd) - \[[CONJ-553](https://jira.mariadb.org/browse/CONJ-553)] travis test configuration modification to handle more than 150 connections
* [Revision #69c124c2](https://github.com/mariadb-corporation/mariadb-connector-j/commit/69c124c2) - \[[CONJ-553](https://jira.mariadb.org/browse/CONJ-553)] correction to handle large amount of concurrent batches, causing RejectedExecutionException error
* [Revision #78069a83](https://github.com/mariadb-corporation/mariadb-connector-j/commit/78069a83) - \[[CONJ-552](https://jira.mariadb.org/browse/CONJ-552)] correct anonymous user existance testing
* [Revision #80233671](https://github.com/mariadb-corporation/mariadb-connector-j/commit/80233671) - \[misc] correction to use 'show status like 'wsrep\_cluster\_status' in place of COM\_PING for galera connection validation
* [Revision #06acd268](https://github.com/mariadb-corporation/mariadb-connector-j/commit/06acd268) - \[[CONJ-552](https://jira.mariadb.org/browse/CONJ-552)] correct test if anonymous user exists
* [Revision #918fed76](https://github.com/mariadb-corporation/mariadb-connector-j/commit/918fed76) - \[[CONJ-555](https://jira.mariadb.org/browse/CONJ-555)] failover implementation correction when issue is due to timeout client side.
* [Revision #6b2a9751](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6b2a9751) - \[[CONJ-552](https://jira.mariadb.org/browse/CONJ-552)] password encoding test correction
* [Revision #c275fa1d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c275fa1d) - Revert "\[[CONJ-555](https://jira.mariadb.org/browse/CONJ-555)] failover implementation correction when issue is due to timeout client side."
* [Revision #e29fa943](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e29fa943) - \[[CONJ-555](https://jira.mariadb.org/browse/CONJ-555)] failover implementation correction when issue is due to timeout client side.
* [Revision #be7de9aa](https://github.com/mariadb-corporation/mariadb-connector-j/commit/be7de9aa) - \[[CONJ-552](https://jira.mariadb.org/browse/CONJ-552)] improve test, ensuring FLUSH PRIVILEGES
* [Revision #a07bbe90](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a07bbe90) - \[[CONJ-529](https://jira.mariadb.org/browse/CONJ-529)] checkstyle correction
* [Revision #d41ab06f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d41ab06f) - \[[CONJ-529](https://jira.mariadb.org/browse/CONJ-529)] test simplification
* [Revision #db44e590](https://github.com/mariadb-corporation/mariadb-connector-j/commit/db44e590) - \[[CONJ-529](https://jira.mariadb.org/browse/CONJ-529)] retriesAllDown sleep loop correction
* [Revision #32a29a71](https://github.com/mariadb-corporation/mariadb-connector-j/commit/32a29a71) - \[[CONJ-501](https://jira.mariadb.org/browse/CONJ-501)] javadoc correction of ed25519 implementation
* [Revision #08de1b84](https://github.com/mariadb-corporation/mariadb-connector-j/commit/08de1b84) - \[[CONJ-501](https://jira.mariadb.org/browse/CONJ-501)] simplify implementation and remove useless ed25519 classes
* [Revision #c6d8adda](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c6d8adda) - \[[CONJ-556](https://jira.mariadb.org/browse/CONJ-556)] correcting metadata case-insensitive test-case
* [Revision #74ce757d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/74ce757d) - \[misc] improve test stability
* [Revision #1af08de3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1af08de3) - \[[CONJ-501](https://jira.mariadb.org/browse/CONJ-501)] ed25519 authentication plugin test depending on plugin availability
* [Revision #6c51297c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6c51297c) - \[[CONJ-501](https://jira.mariadb.org/browse/CONJ-501)] support for ed25519 authentication plugin : remove optional dependency
* [Revision #d9a0cc94](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d9a0cc94) - \[[CONJ-501](https://jira.mariadb.org/browse/CONJ-501)] support for ed25519 authentication plugin
* [Revision #dbd67a4e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/dbd67a4e) - 404 on click on link
* [Revision #687c5532](https://github.com/mariadb-corporation/mariadb-connector-j/commit/687c5532) - \[misc] tag 2.2.1-SNAPSHOT
* [Revision #d2fcff8c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d2fcff8c) - Fix enabling logging in an OSGi environment
* [Revision #4e92b877](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4e92b877) - \[[CONJ-365](https://jira.mariadb.org/browse/CONJ-365)] add javadoc
* [Revision #e0a5cab7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e0a5cab7) - \[[CONJ-365](https://jira.mariadb.org/browse/CONJ-365)] non JDBC method to access server returned affected rows when using option rewriteBatchedStatements
* [Revision #3aaed2fb](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3aaed2fb) - \[[CONJ-413](https://jira.mariadb.org/browse/CONJ-413)] metadata according yearIsDateType : add test case
* [Revision #21cddd55](https://github.com/mariadb-corporation/mariadb-connector-j/commit/21cddd55) - \[[CONJ-550](https://jira.mariadb.org/browse/CONJ-550)] correcting lost statement streaming ability when reusing statement and last stream wasn't fully read : correction when using BULK
* [Revision #09654e9f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/09654e9f) - \[[CONJ-548](https://jira.mariadb.org/browse/CONJ-548)] don't use COM\_STMT\_BULK\_EXECUTE for INSERT ... SELECT statements
* [Revision #f80dba59](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f80dba59) - \[[CONJ-550](https://jira.mariadb.org/browse/CONJ-550)] correcting lost statement streaming ability when reusing statement and last stream wasn't fully read
* [Revision #26918b7d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/26918b7d) - \[misc] appveyor now using maven 3.5.2
* [Revision #fd0ac76e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fd0ac76e) - \[[CONJ-549](https://jira.mariadb.org/browse/CONJ-549)] using internal pool and useResetConnection, disable server prepare statement cache
* [Revision #bf85b18c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/bf85b18c) - bump 2.2.1-SNAPSHOT version
* [Revision #0d2d89d9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/0d2d89d9) - \[[CONJ-549](https://jira.mariadb.org/browse/CONJ-549)] using internal pool and useResetConnection, disable server prepare statement
* [Revision #49d08f82](https://github.com/mariadb-corporation/mariadb-connector-j/commit/49d08f82) - \[misc] checkstyle correction

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
