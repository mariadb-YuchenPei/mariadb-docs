# Connector/J 3.0.3 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://mariadb.com/downloads/#connectors)[Release Notes](../../3.0/mariadb-connector-j-303-release-notes.md)[Changelog](mariadb-connector-j-303-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md)

**Release date:** 25 Jan 2022

For the highlights of this release, see the[release notes](../../3.0/mariadb-connector-j-303-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On[GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #c8152e15](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c8152e15) misc - updated CHANGELOG
* [Revision #d754f799](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d754f799) misc - test correction for stability
* [Revision #b3808219](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b3808219) \[[CONJ-909](https://jira.mariadb.org/browse/CONJ-909)] adding createDatabaseIfNotExist option for 2.x compatibility
* [Revision #900725fc](https://github.com/mariadb-corporation/mariadb-connector-j/commit/900725fc) \[[CONJ-910](https://jira.mariadb.org/browse/CONJ-910)] permit jdbc:mysql scheme when connection string contains "permitMysqlScheme" for compatibility
* [Revision #9ab6f86b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9ab6f86b) \[misc] test correction for maxscale
* [Revision #99dea0e5](https://github.com/mariadb-corporation/mariadb-connector-j/commit/99dea0e5) \[misc] bulk command correction.
* [Revision #913f15d5](https://github.com/mariadb-corporation/mariadb-connector-j/commit/913f15d5) \[misc] test PAM with maxscale
* [Revision #320d699d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/320d699d) \[[CONJ-913](https://jira.mariadb.org/browse/CONJ-913)] Avoid executing additional command on connection
* [Revision #b295d6d5](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b295d6d5) \[[CONJ-912](https://jira.mariadb.org/browse/CONJ-912)] remove security manager code (JEP 411)
* [Revision #5b98d766](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5b98d766) \[test] correcting test for maxscale error [MXS-3929](https://jira.mariadb.org/browse/MXS-3929)
* [Revision #e06c31eb](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e06c31eb) \[[CONJ-911](https://jira.mariadb.org/browse/CONJ-911)] enable keep-alive by default
* [Revision #6f8f13b9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6f8f13b9) \[misc] pool connection correction
* [Revision #e57faf89](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e57faf89) Merge pull request #176
* [Revision #43b427a9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/43b427a9) Upgrading Logback 1.3.0-alpha11
* [Revision #357297f9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/357297f9) \[misc] correcting wrong mention of log4j by slf4J
* [Revision #486d9862](https://github.com/mariadb-corporation/mariadb-connector-j/commit/486d9862) \[misc] failover improvement. some specific commands not in transaction are considered to be replayed in case of failover, like PING, PREPARE, ROLLBACK, ...
* [Revision #8abced35](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8abced35) \[misc] small code improvement
* [Revision #6bcae387](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6bcae387) \[misc] add [MariaDB 10.7](../../../../community-server/old-releases/release-notes-mariadb-10-7-series/what-is-mariadb-107.md) testing
* [Revision #32a2c601](https://github.com/mariadb-corporation/mariadb-connector-j/commit/32a2c601) \[misc] update JMH version
* [Revision #075342ac](https://github.com/mariadb-corporation/mariadb-connector-j/commit/075342ac) \[misc] ensuring test reliability on Skysql HA
* [Revision #68178629](https://github.com/mariadb-corporation/mariadb-connector-j/commit/68178629) \[misc] ensuring test reliability on Skysql HA
* [Revision #6a943f77](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6a943f77) Merge tag '3.0.3' into develop
* [Revision #eb0d4114](https://github.com/mariadb-corporation/mariadb-connector-j/commit/eb0d4114) Merge branch 'release/3.0.3'
* [Revision #5489ff06](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5489ff06) bump 3.0.3 version
* [Revision #d5c219d0](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d5c219d0) \[misc] code style correction
* [Revision #5b165c74](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5b165c74) \[misc] remove benchmark option trackSessionState=TRUE now that [MDEV-26868](https://jira.mariadb.org/browse/MDEV-26868) is released
* [Revision #bb9b11ff](https://github.com/mariadb-corporation/mariadb-connector-j/commit/bb9b11ff) \[misc] test correction
* [Revision #69fd0e5e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/69fd0e5e) \[misc] connection parser avoiding REGEX
* [Revision #844df48d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/844df48d) \[misc] test stability correction
* [Revision #baae3db3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/baae3db3) \[misc] setting "transaction read only" only for replica
* [Revision #361cf716](https://github.com/mariadb-corporation/mariadb-connector-j/commit/361cf716) \[misc] keeping option interactiveClient for compatibility
* [Revision #2c39f465](https://github.com/mariadb-corporation/mariadb-connector-j/commit/2c39f465) \[misc] adding option `transactionReplaySize` to control redo cache size
* [Revision #5aae10e9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5aae10e9) \[misc] only set skip metadata connection flag when using binary protocol
* [Revision #520d1a2b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/520d1a2b) \[misc] correcting test suite for max\_allowed\_packet=16M
* [Revision #fd2f5c5d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fd2f5c5d) \[misc] adding INSERT micro-benchmark test
* [Revision #d1f85cae](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d1f85cae) \[[CONJ-705](https://jira.mariadb.org/browse/CONJ-705)] parameter metadata get parameter count even when query cannot be prepared
* [Revision #04f0062d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/04f0062d) \[misc] prepareStatement.addBatch must initialize with previous set
* [Revision #55365a0b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/55365a0b) \[misc] prepared statement parameter list wrong containsKey method
* [Revision #84f28a2f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/84f28a2f) \[misc] correct Connection.prepareStatement(String sql, int\[] columnIndexes/String\[] columnNames) to return generated keys
* [Revision #fba5ec32](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fba5ec32) \[misc] permit getString on a binary object
* [Revision #2f29c3a8](https://github.com/mariadb-corporation/mariadb-connector-j/commit/2f29c3a8) \[misc] using latest mysql version for benchmark (using option trackSessionState to avoid [MDEV-26868](https://jira.mariadb.org/browse/MDEV-26868) issue)
* [Revision #3fa61961](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3fa61961) \[misc] performance improvement for multi-rows result-set.
* [Revision #960c82d9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/960c82d9) \[misc] using mysql compatible version for benchmark until [MDEV-26868](https://jira.mariadb.org/browse/MDEV-26868) is corrected
* [Revision #862c08b5](https://github.com/mariadb-corporation/mariadb-connector-j/commit/862c08b5) \[misc] compression correction for multi-packet
* [Revision #0e8c7a06](https://github.com/mariadb-corporation/mariadb-connector-j/commit/0e8c7a06) \[misc] coverage addition + correcting development combination SKIP META with EOF
* [Revision #e3f03952](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e3f03952) \[misc] test coverage addition
* [Revision #ab728188](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ab728188) \[misc] correcting codecov coverage generation
* [Revision #d51c2e30](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d51c2e30) \[misc] adding test coverage
* [Revision #64241e4a](https://github.com/mariadb-corporation/mariadb-connector-j/commit/64241e4a) \[misc] ensuring pipelining packet sequence state
* [Revision #e464bac2](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e464bac2) \[misc] Configuration initialUrl/toString using simplified host notation when possible
* [Revision #6fd72070](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6fd72070) \[misc] Datasource permitting setting user/password for 2.x compatibility
* [Revision #f4538c57](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f4538c57) \[misc] benchmark description improvement
* [Revision #a2f25231](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a2f25231) \[misc] Batch result correction
* [Revision #fa7635eb](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fa7635eb) \[misc] COM\_RESET\_CONNECTION expect a response (ERR\_Packet or OK\_Packet)
* [Revision #6dc60037](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6dc60037) \[misc] ensure not throwing error when not having read all DatabaseMetadata resultset
* [Revision #1ea7c07a](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1ea7c07a) \[[CONJ-901](https://jira.mariadb.org/browse/CONJ-901)] ArrayIndexOutOfBoundsException on StandardReadableByteBuf.readByte error
* [Revision #54ac944a](https://github.com/mariadb-corporation/mariadb-connector-j/commit/54ac944a) \[misc] benchmark stable multi columns results
* [Revision #59ee0909](https://github.com/mariadb-corporation/mariadb-connector-j/commit/59ee0909) Merge branch 'master' into develop
* [Revision #c7500486](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c7500486) Merge tag '3.0.2' into develop

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
