# Connector/J 2.1.1 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/2.1.1/)[Release Notes](../../2.1/mariadb-connector-j-211-release-notes.md)[Changelog](mariadb-connector-j-211-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 6 Sep 2017

For the highlights of this release, see the[release notes](../../2.1/mariadb-connector-j-211-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On[GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #a2687da9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a2687da9) - \[misc] add developers information's since needed for sonatype
* [Revision #e01335be](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e01335be) - \[misc] update readme for version 2.1.1 release
* [Revision #933e022d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/933e022d) - bump 2.1.1 version
* [Revision #9cf39061](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9cf39061) - \[misc] remove unused access of @@sql\_mode during connection time
* [Revision #bc0eb9e3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/bc0eb9e3) - \[misc] avoid Unix domain socket multiple close
* [Revision #861657c2](https://github.com/mariadb-corporation/mariadb-connector-j/commit/861657c2) - \[misc] checkstyle correction
* [Revision #c108a054](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c108a054) - \[misc] improving option "enablePacketDebug"
* [Revision #6ccaef96](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6ccaef96) - \[misc] standardization of logger implementation using parameters
* [Revision #4619f99d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4619f99d) - \[misc] add testing with [MariaDB 10.3](../../../../community-server/old-releases/release-notes-mariadb-10-3-series/what-is-mariadb-103.md).x
* [Revision #159cc9bd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/159cc9bd) - \[misc] checkstyle correction
* [Revision #f0bd9337](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f0bd9337) - \[misc] correction of possible race condition when multi-threading on result-set with fetch size set
* [Revision #abd80af6](https://github.com/mariadb-corporation/mariadb-connector-j/commit/abd80af6) - \[[CONJ-519](https://jira.mariadb.org/browse/CONJ-519)] checkstyle correction
* [Revision #60cf61d0](https://github.com/mariadb-corporation/mariadb-connector-j/commit/60cf61d0) - \[[CONJ-519](https://jira.mariadb.org/browse/CONJ-519)] Updatable result-set possible NPE when same field is repeated.
* [Revision #4fbc42b6](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4fbc42b6) - \[[CONJ-514](https://jira.mariadb.org/browse/CONJ-514)] ResultSet method wasNull() always return true after a call on a "null-date" field binary protocol handling
* [Revision #0932c58e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/0932c58e) - \[[CONJ-514](https://jira.mariadb.org/browse/CONJ-514)] ResultSet method wasNull() always return true after a call on a "null-date" field ("0000-00-00 00:00:00" for timestamp, "0000-00-00" for date , ...)
* [Revision #6aa4782a](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6aa4782a) - \[misc] correcting debug output when having offset
* [Revision #83fdfc03](https://github.com/mariadb-corporation/mariadb-connector-j/commit/83fdfc03) - \[[CONJ-517](https://jira.mariadb.org/browse/CONJ-517)] report test for Result-set identification of OK\_Packet with 0xFE header when using option useCompression
* [Revision #d9fb5f07](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d9fb5f07) - \[misc] remove test that is effective 99% of the time (performance test) for better CI reliability
* [Revision #41a29d66](https://github.com/mariadb-corporation/mariadb-connector-j/commit/41a29d66) - \[misc] remove test that is effective 99% of the time (performance test) for better CI reliability
* [Revision #a19f9403](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a19f9403) - \[[CONJ-516](https://jira.mariadb.org/browse/CONJ-516)] Permit using updatable result-set when fetching
* [Revision #4e723df2](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4e723df2) - \[misc] add XA transaction test
* [Revision #c3ab5e50](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c3ab5e50) - \[misc] add pipeline reading threads only if needed
* [Revision #456e1cde](https://github.com/mariadb-corporation/mariadb-connector-j/commit/456e1cde) - \[misc] disable test with fractional time when using MySQL 5.5.x server
* [Revision #ff91ae0b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ff91ae0b) - \[misc] java code cleaning
* [Revision #fa18f052](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fa18f052) - Catch Throwable instead of Exception to cover cases like UnsatisfiedLinkError thrown from JNA
* [Revision #8fb92e3c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8fb92e3c) - \[[CONJ-511](https://jira.mariadb.org/browse/CONJ-511)] adding javadoc
* [Revision #cabb9174](https://github.com/mariadb-corporation/mariadb-connector-j/commit/cabb9174) - \[[CONJ-511](https://jira.mariadb.org/browse/CONJ-511)] Add trace logs on SSL hostname verification
* [Revision #d4ae2a24](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d4ae2a24) - \[[CONJ-511](https://jira.mariadb.org/browse/CONJ-511)] Add legacy SSL certificate Hostname verification with CN even when SAN are set Improve error message
* [Revision #533626df](https://github.com/mariadb-corporation/mariadb-connector-j/commit/533626df) - \[misc] correct network timeout
* [Revision #e8db130f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e8db130f) - \[misc] checkstyle correction
* [Revision #562aeb25](https://github.com/mariadb-corporation/mariadb-connector-j/commit/562aeb25) - \[misc] handling connection error when no database is provided
* [Revision #39885f4d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/39885f4d) - \[misc] set network socket timeout (SO\_TIMEOUT) on socket creation, so SSL exchanges use default timeout
* [Revision #d9c7bf94](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d9c7bf94) - \[misc] tag 2.1.1-SNAPSHOT internally
* [Revision #b9098c03](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b9098c03) - \[misc] tag 2.1.1-SNAPSHOT
* [Revision #ed95b47c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ed95b47c) - \[misc] add trace to HostnameVerifier implementation
* [Revision #9a68376c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9a68376c) - \[misc] improve error message on setting erroneous parameter
* [Revision #5607a8e4](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5607a8e4) - \[misc] delete inaccurate list of developers in pom
* [Revision #95a2c127](https://github.com/mariadb-corporation/mariadb-connector-j/commit/95a2c127) - \[misc] connection optimization (based on standard case)
* [Revision #007a55cd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/007a55cd) - \[misc] correct typo in error message when setting wrong parameter
* [Revision #501b9129](https://github.com/mariadb-corporation/mariadb-connector-j/commit/501b9129) - \[misc] checkstyle correction
* [Revision #45be8ac9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/45be8ac9) - \[misc] using dns mariadb.example.com for SSL tests for hostname verification
* [Revision #a3c6b446](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a3c6b446) - \[misc] travis hostname change for hostname verification

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
