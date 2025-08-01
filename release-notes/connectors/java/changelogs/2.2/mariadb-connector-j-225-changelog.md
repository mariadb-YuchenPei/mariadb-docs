# MariaDB Connector/J 2.2.5 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/2.2.5/)[Release Notes](../../2.2/mariadb-connector-j-225-release-notes.md)[Changelog](mariadb-connector-j-225-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md)

**Release date:** 30 May 2018

For the highlights of this release, see the[release notes](../../2.2/mariadb-connector-j-225-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On[GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #bb4a0d97](https://github.com/mariadb-corporation/mariadb-connector-j/commit/bb4a0d97) - bump 2.2.5 version
* [Revision #5dd325e6](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5dd325e6) - \[test] removing plugins from server test build
* [Revision #07fbe296](https://github.com/mariadb-corporation/mariadb-connector-j/commit/07fbe296) - \[[CONJ-614](https://jira.mariadb.org/browse/CONJ-614)] disabling test for aurora since aurora proxy has new issue
* [Revision #880c9c58](https://github.com/mariadb-corporation/mariadb-connector-j/commit/880c9c58) - \[[CONJ-604](https://jira.mariadb.org/browse/CONJ-604)] handling tx\_isolation deprecation for mysql 5.7.20+
* [Revision #723f06a3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/723f06a3) - \[[CONJ-595](https://jira.mariadb.org/browse/CONJ-595)] Correct galera server validation state on Connection.isValid()
* [Revision #6f33872a](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6f33872a) - \[[CONJ-605](https://jira.mariadb.org/browse/CONJ-605)] activate ignored test
* [Revision #8fc2cf6f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8fc2cf6f) - \[[CONJ-613](https://jira.mariadb.org/browse/CONJ-613)] ensuring that connection using "replication" Parameters doesn't fail when no slave is available
* [Revision #9ef71785](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9ef71785) - \[misc] avoiding escaping sql String for callable statement unnecessary
* [Revision #ab06aaed](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ab06aaed) - \[misc] adding test for replication connection when slave is down
* [Revision #655b1c37](https://github.com/mariadb-corporation/mariadb-connector-j/commit/655b1c37) - \[misc] column information parsing performance improvement
* [Revision #14a22bf6](https://github.com/mariadb-corporation/mariadb-connector-j/commit/14a22bf6) - \[[CONJ-610](https://jira.mariadb.org/browse/CONJ-610)] correction if reaching max\_allowed\_packet
* [Revision #45c8ed0b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/45c8ed0b) - \[[CONJ-610](https://jira.mariadb.org/browse/CONJ-610)] Option "allowMasterDownConnection" improvement on connection validation and Exceptions on master down
* [Revision #dfe6d097](https://github.com/mariadb-corporation/mariadb-connector-j/commit/dfe6d097) - \[[CONJ-604](https://jira.mariadb.org/browse/CONJ-604)] handle support for mysql 8.0 tx\_isolation replacement by transaction\_isolation
* [Revision #ba2d0053](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ba2d0053) - \[[CONJ-609](https://jira.mariadb.org/browse/CONJ-609)] Using getDate with some function result can return wrong result using binary protocol - correction
* [Revision #01170ca6](https://github.com/mariadb-corporation/mariadb-connector-j/commit/01170ca6) - \[misc] better exceptions error : - when PIPE connection failed - when wrong packet order in result-set test small improvement
* [Revision #b0bd3431](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b0bd3431) - \[[CONJ-609](https://jira.mariadb.org/browse/CONJ-609)] Using getDate with some function result can return wrong result using binary protocol
* [Revision #904b3e64](https://github.com/mariadb-corporation/mariadb-connector-j/commit/904b3e64) - More lenient syntax validation for calling stored procedures
* [Revision #a8ad6852](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a8ad6852) - \[misc] travis fix certificate request error on OpenSSL 1.1.0h
* [Revision #33430958](https://github.com/mariadb-corporation/mariadb-connector-j/commit/33430958) - \[misc] appveyor upgrade to maven 3.5.3
* [Revision #fa602797](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fa602797) - \[misc] appveyor upgrade to maven 3.5.3
* [Revision #c45a1e48](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c45a1e48) - bump 2.2.5-SNAPSHOT version
* [Revision #de8883b0](https://github.com/mariadb-corporation/mariadb-connector-j/commit/de8883b0) - \[[CONJ-602](https://jira.mariadb.org/browse/CONJ-602)] add server hostname to connection packet for proxy
* [Revision #3234fa1e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3234fa1e) - \[misc] appveyor download server file timeout correction
* [Revision #2a5d9ddf](https://github.com/mariadb-corporation/mariadb-connector-j/commit/2a5d9ddf) - \[misc] appveyor server version change + 2 tests with timeout disabled due to appveyor very
* [Revision #89d3499b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/89d3499b) - \[misc] appveyor server version change + 2 tests with timeout disabled due to appveyor very slow VM that interfere
* [Revision #c596cd13](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c596cd13) - \[misc] checkstyle javadoc correction

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
