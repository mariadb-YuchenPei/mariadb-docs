# MariaDB Connector/J 2.1.2 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/2.1.2/)[Release Notes](../../2.1/mariadb-connector-j-212-release-notes.md)[Changelog](mariadb-connector-j-212-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md)

**Release date:** 26 Sep 2017

For the highlights of this release, see the[release notes](../../2.1/mariadb-connector-j-212-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On[GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #afb7cbd9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/afb7cbd9) - bump 2.1.2 version
* [Revision #277ca8b1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/277ca8b1) - \[misc] travis test with maxscale now use 2.1.8 version
* [Revision #f285e8a6](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f285e8a6) - \[misc] improving tests
* [Revision #d0a5f48b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d0a5f48b) - \[[CONJ-528](https://jira.mariadb.org/browse/CONJ-528)] remove limitation max\_allowed\_packet size for LOAD DATA LOCAL INFILE command
* [Revision #ab8e666c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ab8e666c) - \[[CONJ-525](https://jira.mariadb.org/browse/CONJ-525)] merge PR to handle DELETE batching with bulk command
* [Revision #755d1627](https://github.com/mariadb-corporation/mariadb-connector-j/commit/755d1627) - [CONJ-525](https://jira.mariadb.org/browse/CONJ-525) Set exception has happened to false
* [Revision #9fb3fe35](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9fb3fe35) - \[misc] change appveyor to avoid oom during tests
* [Revision #528786bd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/528786bd) - \[misc] bump 2.1.2-SNAPSHOT version
* [Revision #5a6312e9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5a6312e9) - \[[CONJ-527](https://jira.mariadb.org/browse/CONJ-527)] resultset.last() return wrong value if resultset has only one result
* [Revision #f9494701](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f9494701) - \[misc] make the tests more robust, to avoid false positives
* [Revision #ef9680b6](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ef9680b6) - \[misc] executeLargeBatch() exception correction for rewritten option
* [Revision #7104e4aa](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7104e4aa) - \[misc] bump 2.2.0-SNAPSHOT version
* [Revision #2fe943c6](https://github.com/mariadb-corporation/mariadb-connector-j/commit/2fe943c6) - \[[CONJ-526](https://jira.mariadb.org/browse/CONJ-526)] better error message getting metadata information when SQL syntax is wrong
* [Revision #8d469322](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8d469322) - \[misc] improved test stability
* [Revision #c502c4a1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c502c4a1) - \[misc] aurora test correction
* [Revision #621c877f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/621c877f) - \[misc] aurora valid timeout correction
* [Revision #2e9a6fd2](https://github.com/mariadb-corporation/mariadb-connector-j/commit/2e9a6fd2) - \[misc] improving url parser performance
* [Revision #a34d1a6b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a34d1a6b) - \[misc] test correction to ensuring to reactivate proxy
* [Revision #338397bb](https://github.com/mariadb-corporation/mariadb-connector-j/commit/338397bb) - [CONJ-525](https://jira.mariadb.org/browse/CONJ-525) Fix for having extra update count during batch queries, with -3 which is unexpected by external consumers
* [Revision #1c195fc9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1c195fc9) - \[misc] thread name avoiding automatic addition of "MariaDb" prefix
* [Revision #e05821d9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e05821d9) - \[misc] ensuring Connection.isValid(timeout) always respect timeout value
* [Revision #4d3e53a1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4d3e53a1) - \[misc] code cleaning : small constructor simplification
* [Revision #8e084370](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8e084370) - \[misc] standardization of connection exceptions
* [Revision #3d721e25](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3d721e25) - \[misc] ensuring connection loop without failover options loop though all host if an initial query exception occur
* [Revision #1fbfd8a8](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1fbfd8a8) - \[misc] correction of an exception message
* [Revision #de745e40](https://github.com/mariadb-corporation/mariadb-connector-j/commit/de745e40) - \[misc] remove getPassword() from connection implementation

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
