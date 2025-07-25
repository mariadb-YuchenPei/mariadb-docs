# Connector/ODBC 3.0.8 Changelog

The most recent [_**Stable**_](../../../../community-server/about/release-criteria.md) _**(GA)**_ release of MariaDB Connector/ODBC is:[**MariaDB Connector/ODBC 3.2.5**](../../mariadb-connector-odbc-3-2-release-notes/mariadb-connector-odbc-3-2-5-release-notes.md)

[Download](https://downloads.mariadb.org/connector-odbc/3.0.8/)[Release Notes](../../mariadb-connector-odbc-30-release-notes/mariadb-connector-odbc-308-release-notes.md)[Changelog](mariadb-connector-odbc-308-changelog.md)[About MariaDB Connector/ODBC](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-odbc/README.md)

**Release date:** 4 Jan 2019

For the highlights of this release, see the[release notes](../../mariadb-connector-odbc-30-release-notes/mariadb-connector-odbc-308-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On[GitHub](https://github.com/MariaDB/mariadb-connector-odbc) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #7b463c1](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/7b463c1)\
  2018-12-20 16:42:02 -0700
  * [ODBC-207](https://jira.mariadb.org/browse/ODBC-207) Fix multi-statement param realloc.\
    Example use case:\
    Prepare the following SQL statement:\
    "INSERT INTO tbl (a,b) VALUES (?,?); SELECT 1 FROM tbl WHERE c = ?"\
    First execution of prepared statement will work, second execution will segfault or cause memory corruption.
* [Revision #99a8ac0](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/99a8ac0)\
  2019-01-03 19:15:48 +0100
  * Merge branch 'master' into [ODBC-3](https://jira.mariadb.org/browse/ODBC-3).0
* [Revision #5d5ec8e](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/5d5ec8e)\
  2018-10-17 12:39:33 +0100
  * Add SQL\_OUTER\_JOINS support to SQLGetInfo\
    This is an older attribute that is largely superseded by\
    the newer SQL\_OJ\_CAPABILITIES attribute but some software\
    checks it first and only uses SQL\_OJ\_CAPABILITIES to get\
    more details if SQL\_OUTER\_JOINS says they are supported.
* [Revision #5916978](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/5916978)\
  2019-01-02 13:31:26 +0100
  * Updating libmariadb to the 3.0.8 release tag
* [Revision #cb5b7ce](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/cb5b7ce)\
  2018-12-10 18:16:41 +0100
  * [ODBC-205](https://jira.mariadb.org/browse/ODBC-205) The patch moves string to date/time types conversion from C/C on C/ODBC\
    side to better meet ODBC requirements.
* [Revision #20e0a50](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/20e0a50)\
  2018-12-02 22:31:37 +0100
  * [ODBC-203](https://jira.mariadb.org/browse/ODBC-203) The fix and the testcase.\
    The problem occurred only with data fetched as SQL\_C\_WCHAR. That\
    happened because for statement handles after 1st one, there wasn't STMT\_ATTR\_UPDATE\_MAX\_LENGTH attribute set, and getting data as a widestring depends on max\_length.
* [Revision #f1e0cd2](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/f1e0cd2)\
  2018-11-30 01:16:37 +0100
  * [ODBC-204](https://jira.mariadb.org/browse/ODBC-204) SQLGetData did not return empty wide string
* [Revision #92699ab](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/92699ab)\
  2018-11-28 01:33:13 +0100
  * odbc\*.ini files were generated in CMAKE\_SOURCE\_DIR, instead of CMAKE\_BINARY\_DIR. That probably is not right, and they have to be along with tests binaries
* [Revision #07381cc](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/07381cc)\
  2018-11-16 12:06:49 +0100
  * Version bump -> 3.0.8 + new logo in README.md

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
