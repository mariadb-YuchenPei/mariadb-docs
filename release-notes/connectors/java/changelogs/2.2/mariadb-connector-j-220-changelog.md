# MariaDB Connector/J 2.2.0 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/2.2.0/)[Release Notes](../../2.2/mariadb-connector-j-220-release-notes.md)[Changelog](mariadb-connector-j-220-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md)

**Release date:** 9 Nov 2017

For the highlights of this release, see the[release notes](../../2.2/mariadb-connector-j-220-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On[GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #455bbfc4](https://github.com/mariadb-corporation/mariadb-connector-j/commit/455bbfc4) - bump 2.2.0 version
* [Revision #5a6cf5d1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5a6cf5d1) - \[misc] resultset findColumn null parameter
* [Revision #216e75f4](https://github.com/mariadb-corporation/mariadb-connector-j/commit/216e75f4) - \[misc] test : ensure reliable active connection result
* [Revision #fb75796a](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fb75796a) - \[misc] resultset findColumn alias use column name if alias not found
* [Revision #cc2cfbd4](https://github.com/mariadb-corporation/mariadb-connector-j/commit/cc2cfbd4) - \[[CONJ-510](https://jira.mariadb.org/browse/CONJ-510)] allow execution of read-only statements on slaves when master is down
* [Revision #83f8ec44](https://github.com/mariadb-corporation/mariadb-connector-j/commit/83f8ec44) - \[[CONJ-495](https://jira.mariadb.org/browse/CONJ-495)] Improve reading resultset data - BIT and BIGDECIMAL implementation correction
* [Revision #11e85d51](https://github.com/mariadb-corporation/mariadb-connector-j/commit/11e85d51) - \[[CONJ-495](https://jira.mariadb.org/browse/CONJ-495)] Improve reading resultset data
* [Revision #2eb02241](https://github.com/mariadb-corporation/mariadb-connector-j/commit/2eb02241) - \[misc] improve pool test stability
* [Revision #81a7e1e2](https://github.com/mariadb-corporation/mariadb-connector-j/commit/81a7e1e2) - \[[CONJ-469](https://jira.mariadb.org/browse/CONJ-469)] Improve Blob/Clob implementation (avoiding array copy from result-set row)
* [Revision #fe3a531f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fe3a531f) - \[misc] correct test when max\_allowed\_packet > 500m
* [Revision #f3c682cd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f3c682cd) - \[misc] SchedulerServiceProviderHolder test correction
* [Revision #98c99e94](https://github.com/mariadb-corporation/mariadb-connector-j/commit/98c99e94) - \[misc] checkstyle correction
* [Revision #36f5079c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/36f5079c) - \[misc] removing threadly test dependency
* [Revision #53b101d7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/53b101d7) - \[misc] correct test for java 9 that strangly permit having multiple value in HashSet
* [Revision #90907c58](https://github.com/mariadb-corporation/mariadb-connector-j/commit/90907c58) - \[misc] ensure that enablePacketDebug option works when timer tick is big
* [Revision #16ffb2e4](https://github.com/mariadb-corporation/mariadb-connector-j/commit/16ffb2e4) - \[misc] testing : permit running tests on server with docker
* [Revision #b53f8426](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b53f8426) - Check that getMoreResults returns false
* [Revision #1ac4f1bc](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1ac4f1bc) - \[[CONJ-541](https://jira.mariadb.org/browse/CONJ-541)] Fix behavior of ResultSet#relative when crossing result set boundaries
* [Revision #31593580](https://github.com/mariadb-corporation/mariadb-connector-j/commit/31593580) - \[[CONJ-541](https://jira.mariadb.org/browse/CONJ-541)] Test behavior of ResultSet#relative when going backward
* [Revision #7063f6f8](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7063f6f8) - \[[CONJ-541](https://jira.mariadb.org/browse/CONJ-541)] Test behavior of ResultSet#relative when going forward
* [Revision #22a429fa](https://github.com/mariadb-corporation/mariadb-connector-j/commit/22a429fa) - \[[CONJ-522](https://jira.mariadb.org/browse/CONJ-522)] pool closing : racing condition correction
* [Revision #a9623e82](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a9623e82) - Fix typo in "Connection is close(d)"'
* [Revision #db957e38](https://github.com/mariadb-corporation/mariadb-connector-j/commit/db957e38) - \[[CONJ-522](https://jira.mariadb.org/browse/CONJ-522)] pool implementation using one thread for connection creation
* [Revision #67b9dbb7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/67b9dbb7) - \[[CONJ-522](https://jira.mariadb.org/browse/CONJ-522)] ensuring pool closing does not leak connection
* [Revision #8c59138e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8c59138e) - \[[CONJ-539](https://jira.mariadb.org/browse/CONJ-539)] better message when server close connection
* [Revision #fde60c15](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fde60c15) - \[[CONJ-522](https://jira.mariadb.org/browse/CONJ-522)] Pool datasource implementation
* [Revision #a7be3637](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a7be3637) - \[misc] network timeout without keeping initial connection String parameter
* [Revision #4a37e2ed](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4a37e2ed) - \[misc] improve some test
* [Revision #8c96b62b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8c96b62b) - \[misc] correcting test if using ensure maxscale (using different XID if maxscale use the same connection)
* [Revision #6c38e17c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6c38e17c) - \[[CONJ-533](https://jira.mariadb.org/browse/CONJ-533)] add missing javadoc
* [Revision #603d4078](https://github.com/mariadb-corporation/mariadb-connector-j/commit/603d4078) - \[[CONJ-533](https://jira.mariadb.org/browse/CONJ-533)] PrepareStatement.setTime() may insert incorrect time according to current timezone, time and option "useLegacyDatetimeCode"
* [Revision #9dbf456b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9dbf456b) - \[misc] codacy improvement
* [Revision #28773e50](https://github.com/mariadb-corporation/mariadb-connector-j/commit/28773e50) - \[[CONJ-535](https://jira.mariadb.org/browse/CONJ-535)] resultset.getInt() throwing an error if BIT data type value is bigger than Integer.MAX\_VALUE
* [Revision #dac87b3c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/dac87b3c) - \[[CONJ-535](https://jira.mariadb.org/browse/CONJ-535)] correction on numerical getter for BIT data type fields
* [Revision #024e8b04](https://github.com/mariadb-corporation/mariadb-connector-j/commit/024e8b04) - \[misc] add "autocommit" option
* [Revision #c15e2380](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c15e2380) - \[misc] connect timeout test correction
* [Revision #c3098192](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c3098192) - \[misc] url parsing optimisation
* [Revision #6bc2632c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6bc2632c) - \[misc] default option "connectTimeout" value to 30 seconds (was 0 = no timeout)
* [Revision #e6009aa6](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e6009aa6) - \[misc] add java 9 testing to travis
* [Revision #19091f7c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/19091f7c) - \[[CONJ-532](https://jira.mariadb.org/browse/CONJ-532)] correction Statement.getMoreResults() for multi-queries
* [Revision #fc586c5e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fc586c5e) - \[misc] adding minimum maxscale version for testing statement.cancel()
* [Revision #81403bf9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/81403bf9) - \[misc] parsing MySQL server version that didn't have any additional comment
* [Revision #776446e4](https://github.com/mariadb-corporation/mariadb-connector-j/commit/776446e4) - \[misc] avoid race condition on Connection.abort() if the options "enablePacketDebug" and "log" are enable
* [Revision #7c533614](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7c533614) - \[misc] result-set Exception simplification
* [Revision #b82fa1ea](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b82fa1ea) - \[[CONJ-531](https://jira.mariadb.org/browse/CONJ-531)] permit cancelling streaming result-set using Statement.cancel. Deletion of the option "killFetchStmtOnClose" that was permitting to KILL QUERY on close to cancel streaming result-set
* [Revision #f9d20bfe](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f9d20bfe) - Update GSSAPI.creole
* [Revision #158b9a94](https://github.com/mariadb-corporation/mariadb-connector-j/commit/158b9a94) - \[misc] make checkstyle happy
* [Revision #fa9e9e5f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fa9e9e5f) - \[misc] connection performance improvement correction
* [Revision #9708fcdd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9708fcdd) - \[misc] update kerberos documentation
* [Revision #05b78b26](https://github.com/mariadb-corporation/mariadb-connector-j/commit/05b78b26) - \[misc] update documentation
* [Revision #0a2ba9a9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/0a2ba9a9) - \[misc] language correction
* [Revision #b7171cc9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b7171cc9) - \[misc] presentation correction
* [Revision #49a4ddf8](https://github.com/mariadb-corporation/mariadb-connector-j/commit/49a4ddf8) - \[misc] connection performance improvement
* [Revision #8ab419a3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8ab419a3) - \[[CONJ-530](https://jira.mariadb.org/browse/CONJ-530)] Permit Connection.abort() forcing killing the connection, even if connection is stuck in another thread
* [Revision #afd81468](https://github.com/mariadb-corporation/mariadb-connector-j/commit/afd81468) - \[misc] permit wrong failover format without 3rd colon for compatibility
* [Revision #03180d8c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/03180d8c) - \[misc] faster failover parsing in connection String
* [Revision #fd1dad0c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fd1dad0c) - Bump 2.2.0-SNAPSHOT version

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
