# Connector/J 3.3.0 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://mariadb.com/downloads/connectors/connectors-data-access/java8-connector)[Release Notes](../../3.3/mariadb-connector-j-3-3-0-release-notes.md)[Changelog](mariadb-connector-j-3-3-0-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 08 Nov 2023

For the highlights of this release, see the[release notes](../../3.3/mariadb-connector-j-3-3-0-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On[GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #d9b36887](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d9b36887) - Merge branch 'release/3.3.0'
* [Revision #7ef158f9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7ef158f9) - bump 3.3.0
* [Revision #5ff1421b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5ff1421b) - \[[CONJ-1108](https://jira.mariadb.org/browse/CONJ-1108)] Database metadata listing TEMPORARY tables/sequences - ensure null handling
* [Revision #52ab8d38](https://github.com/mariadb-corporation/mariadb-connector-j/commit/52ab8d38) - \[[CONJ-1108](https://jira.mariadb.org/browse/CONJ-1108)] Database metadata listing TEMPORARY tables/sequences
* [Revision #057b2e9d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/057b2e9d) - \[misc] default compiler version correction
* [Revision #86903861](https://github.com/mariadb-corporation/mariadb-connector-j/commit/86903861) - \[[CONJ-1102](https://jira.mariadb.org/browse/CONJ-1102)] BatchUpdateException.getUpdateCounts() wrong results
* [Revision #69735a54](https://github.com/mariadb-corporation/mariadb-connector-j/commit/69735a54) - \[misc] TemporalField use code simplification
* [Revision #c46c6bc0](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c46c6bc0) - \[misc] remove skysql testing
* [Revision #be3eb29f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/be3eb29f) - bump jmh version
* [Revision #f5a33b6d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f5a33b6d) - \[[CONJ-1115](https://jira.mariadb.org/browse/CONJ-1115)] Make connector become virtual-thread friendly - part 2
* [Revision #db657101](https://github.com/mariadb-corporation/mariadb-connector-j/commit/db657101) - \[misc] update mysql connector in benchmark to recent version (8.1.0)
* [Revision #a1772853](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a1772853) - \[[CONJ-1115](https://jira.mariadb.org/browse/CONJ-1115)] Make connector become virtual-thread friendly
* [Revision #10a11071](https://github.com/mariadb-corporation/mariadb-connector-j/commit/10a11071) - \[[CONJ-1116](https://jira.mariadb.org/browse/CONJ-1116)] Avoid unnecessary synchronization on calendar when no calendar parameter
* [Revision #02921369](https://github.com/mariadb-corporation/mariadb-connector-j/commit/02921369) - \[misc] correct UnixDomainSocket not used sun\_family variable, but mandatory for JNI
* [Revision #f2c90f9b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f2c90f9b) - \[misc] test suite using openjdk17 by default
* [Revision #7b197fe6](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7b197fe6) - \[misc] pattern matching in instanceof correction for java 8 support
* [Revision #04f99d50](https://github.com/mariadb-corporation/mariadb-connector-j/commit/04f99d50) - \[misc] spotless addition to ensure code style compatible with java 21
* [Revision #c50b6fa0](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c50b6fa0) - \[misc] correct missing export
* [Revision #6a77c87a](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6a77c87a) - \[misc] ed25519 update to 0.3.0
* [Revision #875d9f06](https://github.com/mariadb-corporation/mariadb-connector-j/commit/875d9f06) - \[[CONJ-1112](https://jira.mariadb.org/browse/CONJ-1112)] java 19 deprecated methods pre-removal
* [Revision #2acd4376](https://github.com/mariadb-corporation/mariadb-connector-j/commit/2acd4376) - \[[CONJ-1112](https://jira.mariadb.org/browse/CONJ-1112)] style correction after google style update
* [Revision #141ed872](https://github.com/mariadb-corporation/mariadb-connector-j/commit/141ed872) - \[[CONJ-1112](https://jira.mariadb.org/browse/CONJ-1112)] license header uniformization
* [Revision #23d6e414](https://github.com/mariadb-corporation/mariadb-connector-j/commit/23d6e414) - \[[CONJ-1112](https://jira.mariadb.org/browse/CONJ-1112)] code style validation change
* [Revision #65c2f1e8](https://github.com/mariadb-corporation/mariadb-connector-j/commit/65c2f1e8) - \[[CONJ-1111](https://jira.mariadb.org/browse/CONJ-1111)] ensure using same ip in place of DNS when creating a connection to kill running query
* [Revision #e41f0243](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e41f0243) - \[misc] correct windows named pipe testing for mysql 8.0.14+
* [Revision #3710eb02](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3710eb02) - \[misc] update formatting plugin to com.spotify.fmt/fmt-maven-plugin
* [Revision #e24a6318](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e24a6318) - \[misc] use [mariadb 11.1](../../../../community-server/old-releases/release-notes-mariadb-11-1-series/what-is-mariadb-111.md) in test suite
* [Revision #706016b7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/706016b7) - \[misc] ensure multi host connection close call when not succeeded
* [Revision #4434a290](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4434a290) - \[misc] code style correction
* [Revision #31b36c12](https://github.com/mariadb-corporation/mariadb-connector-j/commit/31b36c12) - \[misc] update ES test from 23.07 to 23.08
* [Revision #3f197b98](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3f197b98) - \[misc] update ES test from 23.06 to 23.07
* [Revision #888e22f7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/888e22f7) - \[misc] test correction
* [Revision #18fe4035](https://github.com/mariadb-corporation/mariadb-connector-j/commit/18fe4035) - Merge branch 'master' into develop
* [Revision #7ddcd9ee](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7ddcd9ee) - \[misc] correct batch for mysql server
* [Revision #e05fc3dd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e05fc3dd) - \[misc] update README versions
* [Revision #c234b046](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c234b046) - Merge tag '3.2.0' into develop

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
