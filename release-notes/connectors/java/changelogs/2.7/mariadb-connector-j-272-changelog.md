# Connector/J 2.7.2 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://mariadb.com/downloads/#connectors)[Release Notes](../../2.7/mariadb-connector-j-272-release-notes.md)[Changelog](mariadb-connector-j-272-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 29 Jan. 2021

For the highlights of this release, see the[release notes](../../2.7/mariadb-connector-j-272-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On[GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #83f50ab1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/83f50ab1) - Bump 2.7.2 version
* [Revision #8cc16d4c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8cc16d4c) - \[[CONJ-850](https://jira.mariadb.org/browse/CONJ-850)] MariaDbResultSetMetaData#getPrecision(int) returns wrong length for character data
* [Revision #a4f85ce2](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a4f85ce2) - Added support for Aurora cluster custom endpoints
* [Revision #323b82b5](https://github.com/mariadb-corporation/mariadb-connector-j/commit/323b82b5) - user must exist and 5.6 does not support the syntax if exists
* [Revision #61c21056](https://github.com/mariadb-corporation/mariadb-connector-j/commit/61c21056) - \[misc] MySQL 8 test correction
* [Revision #ee71dd44](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ee71dd44) - mysql 8.0 still does not have IS\_GENERATED column. tested version: 8.0.15
* [Revision #7644aaf5](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7644aaf5) - \[misc] benchmark update
* [Revision #6d68f763](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6d68f763) - \[misc] indentation correction
* [Revision #f1225752](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f1225752) - \[[CONJ-849](https://jira.mariadb.org/browse/CONJ-849)] in case of an object parameter with unknown type and not serializable driver now throw a SerialException, not an SQLNonTransientConnectionException that result in closing the connection.
* [Revision #1033ac60](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1033ac60) - \[misc] correcting initial SQL script for MySQL 8 compatibility.
* [Revision #fa7e4c44](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fa7e4c44) - \[misc] SkySQL test stability improvement
* [Revision #2d79c65d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/2d79c65d) - \[misc] replacing new Character() with Character.valueOf() method
* [Revision #722556c3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/722556c3) - \[[CONJ-852](https://jira.mariadb.org/browse/CONJ-852)] CmdInformationSingle.isDuplicateKeyUpdate() fails to detect ON DUPLICATE KEY clause if there are newlines in query. Solved by enabling DOTALL mode in regexp.
* [Revision #9eec426c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9eec426c) - \[misc] ensure MAXSCALE test reliability
* [Revision #01eae69e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/01eae69e) - \[misc] removing pgp retry
* [Revision #4e7d6c4f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4e7d6c4f) - \[misc] test [MariaDB 10.6](../../../../community-server/mariadb-10-6-series/what-is-mariadb-106.md) build version
* [Revision #d9d3a85a](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d9d3a85a) - \[misc] correct test when using maxscale with replication topology
* [Revision #186675d9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/186675d9) - \[misc] correct test since server message change
* [Revision #1687916e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1687916e) - \[[CONJ-847](https://jira.mariadb.org/browse/CONJ-847)] NPE at UpdatableResultSet#close
* [Revision #3bfa4ec5](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3bfa4ec5) - \[misc] codespell correction
* [Revision #bb1f2d10](https://github.com/mariadb-corporation/mariadb-connector-j/commit/bb1f2d10) - Merge branch 'fix/#166' into develop
* [Revision #07dd125f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/07dd125f) - Merge branch 'fix/#165' into develop
* [Revision #7bbd7404](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7bbd7404) - \[misc] MySQL 8 test correction
* [Revision #e2c46b23](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e2c46b23) - Merge branch 'fix/[CONJ-851](https://jira.mariadb.org/browse/CONJ-851)' into develop
* [Revision #abc533bf](https://github.com/mariadb-corporation/mariadb-connector-j/commit/abc533bf) - \[misc] benchmark update
* [Revision #86cceb76](https://github.com/mariadb-corporation/mariadb-connector-j/commit/86cceb76) - \[misc] indentation correction
* [Revision #78b8ef94](https://github.com/mariadb-corporation/mariadb-connector-j/commit/78b8ef94) - \[[CONJ-849](https://jira.mariadb.org/browse/CONJ-849)] in case of an object parameter with unknown type and not serializable driver now throw a SerialException, not an SQLNonTransientConnectionException that result in closing the connection.
* [Revision #1565981e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1565981e) - \[misc] correcting initial SQL script for MySQL 8 compatibility.
* [Revision #b35361d9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b35361d9) - \[misc] SkySQL test stability improvement
* [Revision #bfb426eb](https://github.com/mariadb-corporation/mariadb-connector-j/commit/bfb426eb) - \[misc] replacing new Character() with Character.valueOf() method
* [Revision #a4f14a67](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a4f14a67) - Merge branch 'fix/167' into develop
* [Revision #3350386d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3350386d) - \[misc] ensure MAXSCALE test reliability
* [Revision #bd8f85e5](https://github.com/mariadb-corporation/mariadb-connector-j/commit/bd8f85e5) - \[misc] removing pgp retry
* [Revision #c5887304](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c5887304) - \[misc] test [MariaDB 10.6](../../../../community-server/mariadb-10-6-series/what-is-mariadb-106.md) build version
* [Revision #5ef23935](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5ef23935) - \[misc] correct test when using maxscale with replication topology
* [Revision #1d820aa8](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1d820aa8) - \[misc] correct test since server message change
* [Revision #9edc3b88](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9edc3b88) - \[[CONJ-847](https://jira.mariadb.org/browse/CONJ-847)] NPE at UpdatableResultSet#close
* [Revision #b5fa2b12](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b5fa2b12) - CmdInformationSingle.isDuplicateKeyUpdate() fails to detect ON DUPLICATE KEY clause if there are newlines in query. Solved by enabling DOTALL mode in regexp.

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
