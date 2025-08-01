# Connector/ODBC 3.2.1 Changelog

The most recent [_**Stable**_](../../../../community-server/about/release-criteria.md) _**(GA)**_ release of MariaDB Connector/ODBC is:[**MariaDB Connector/ODBC 3.2.5**](../../mariadb-connector-odbc-3-2-release-notes/mariadb-connector-odbc-3-2-5-release-notes.md)

[Download](https://mariadb.com/downloads/connectors/connectors-data-access/odbc-connector/)[Release Notes](../../mariadb-connector-odbc-3-2-release-notes/mariadb-connector-odbc-3-2-1-release-notes.md)[Changelog](mariadb-connector-odbc-3-2-1-changelog.md)[About MariaDB Connector/ODBC](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-odbc/README.md)

**Release date:** 1 Dec 2023

For the highlights of this release, see the[release notes](../../mariadb-connector-odbc-3-2-release-notes/mariadb-connector-odbc-3-2-1-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On[GitHub](https://github.com/MariaDB/mariadb-connector-odbc) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #cea6787](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/cea6787)\
  2023-11-29 13:05:29 +0100
  * Somehow lost reset execution on SQL\_ATTR\_RESET\_CONNECTION
* [Revision #1746c05](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/1746c05)\
  2023-11-27 22:14:22 +0100
  * Fixes for MacOS/iOdbc
* [Revision #3e4d81e](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/3e4d81e)\
  2023-11-26 01:08:26 +0100
  * Fix of memory leak introduced earlier
* [Revision #ea408ce](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/ea408ce)\
  2023-11-18 00:42:55 +0100
  * Fix of warnings in 32b build(windows)
* [Revision #4573dac](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/4573dac)\
  2023-11-19 19:09:58 +0100
  * [ODBC-401](https://jira.mariadb.org/browse/ODBC-401) SQLCancel fix
* [Revision #dfbeccd](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/dfbeccd)\
  2023-11-15 18:53:11 +0100
  * Linux build fixes
* [Revision #3578ed0](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/3578ed0)\
  2023-11-15 15:59:01 +0100
  * Merge branch 'master'(3.1) into develop(3.2)
* [Revision #41b9d83](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/41b9d83)\
  2023-10-30 12:35:35 +0100
  * Small improvement in the connection process
* [Revision #349fe3b](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/349fe3b)\
  2023-09-22 00:23:38 +0200
  * Changes in tests for xpand
* [Revision #790b58b](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/790b58b)\
  2023-08-07 11:11:03 +0530
  * Fix Travis build for s390x
* [Revision #1598057](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/1598057)\
  2023-09-20 15:12:36 +0200
  * Removing dependency on pkg-config from binary rpm
* [Revision #77102f7](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/77102f7)\
  2023-09-18 12:36:56 +0200
  * C/C submodule has been updated to v3.3.7 release tag
* [Revision #0be3743](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/0be3743)\
  2023-09-05 22:23:38 +0200
  * Added dependencies to source rpm
* [Revision #86ad76e](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/86ad76e)\
  2023-08-30 16:00:21 +0200
  * Added 23.08 to travis matrix
* [Revision #c78d08f](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/c78d08f)\
  2023-08-23 13:49:39 +0200
  * Adding dirver UnixODBC template ini file to installation(RPM/DEB/TGZ)
* [Revision #9209023](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/9209023)\
  2023-08-13 23:10:32 +0200
  * Fix of travis script
* [Revision #918bf56](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/918bf56)\
  2023-11-15 15:05:38 +0100
  * Results is not shared ptr, and activeStreamingResult is not weak\_ptr now
* [Revision #8e43fb6](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/8e43fb6)\
  2023-11-14 13:01:21 +0100
  * Changes in "artificial" resultset realisation
* [Revision #a0ab285](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/a0ab285)\
  2023-11-06 23:43:01 +0100
  * [ODBC-66](https://jira.mariadb.org/browse/ODBC-66) Complience with ODBC 3.8 standard
* [Revision #2e065d7](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/2e065d7)\
  2023-10-31 10:18:04 +0100
  * Integration of yet one more class from minimal c/c++ infrastructure
* [Revision #d5a4759](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/d5a4759)\
  2023-10-11 17:44:57 +0200
  * [ODBC-397](https://jira.mariadb.org/browse/ODBC-397) Introducing LRU srver side prepared statement cache
* [Revision #2d2a979](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/2d2a979)\
  2023-08-13 18:56:37 +0200
  * Added fallback to CS prepare if native error is 1295(not preparable on
* [Revision #3418dbd](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/3418dbd)\
  2023-08-08 18:52:30 +0200
  * Merge branch 'master'(3.1) into develop(3.2)
* [Revision #bbe48ab](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/bbe48ab)\
  2023-07-21 00:24:43 +0200
  * Fix of couple of tests for the case of resultset streaming
* [Revision #abb23df](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/abb23df)\
  2023-07-20 17:18:43 +0200
  * [ODBC-395](https://jira.mariadb.org/browse/ODBC-395) The fix and the testcase
* [Revision #a7ba72d](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/a7ba72d)\
  2023-07-20 15:24:12 +0200
  * [ODBC-394](https://jira.mariadb.org/browse/ODBC-394) Changed use of tx\_isolation to transaction\_isolation
* [Revision #97b6d5e](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/97b6d5e)\
  2023-07-07 14:35:59 -0400
  * bump the VERSION
* [Revision #08da03f](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/08da03f)\
  2023-06-10 21:58:33 +0200
  * Overriding the problem with c/c requires C99 with older GCC
* [Revision #fc52d66](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/fc52d66)\
  2023-06-10 12:42:29 +0200
  * [ODBC-392](https://jira.mariadb.org/browse/ODBC-392) The fix and the testcase
* [Revision #a210bfa](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/a210bfa)\
  2023-06-05 12:44:14 +0200
  * [ODBC-391](https://jira.mariadb.org/browse/ODBC-391) Only the fix as lower\_case\_table\_names can't be changed for session. i.e. the test has been added, but to server has to be in lower\_case\_table\_names=2 mode to test the fix, otherwise it ensures that the fix doesn't break catalog functions against server in "normaler" mode. The fix adds reading of the lower\_case\_table\_names, and if it's 2, then it compares table name case insensitively where case sensitive comparison would be used otherwise. The problem actually affects not ony SQLStatistics, but almost all catalog functions, that take catalog and/or table parameter as ordinary argument.
* [Revision #60a5bd6](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/60a5bd6)\
  2023-06-02 14:03:09 +0200
  * [ODBC-350](https://jira.mariadb.org/browse/ODBC-350) The fix and the testcase
* [Revision #58426b1](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/58426b1)\
  2023-05-17 10:36:08 +0200
  * Merge branch 'master'(3.0) into develop(3.1)
* [Revision #9b96270](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/9b96270)\
  2023-05-17 10:28:42 +0200
  * Fix of potential issue found with ASAN
* [Revision #d809d2b](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/d809d2b)\
  2023-05-16 22:27:33 +0200
  * Merge branch 'master'(3.0) into develop(3.1)
* [Revision #2eb9877](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/2eb9877)\
  2023-05-15 10:16:55 +0200
  * Added WITH\_ASAN, WITH\_UBSAN and WITH\_MSAN cmake option to enable
* [Revision #0fe450b](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/0fe450b)\
  2023-04-28 16:57:03 +0200
  * Merge branch 'master'(3.1) into develop(3.2)
* [Revision #c0d989b](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/c0d989b)\
  2023-04-28 12:34:59 +0200
  * [ODBC-390](https://jira.mariadb.org/browse/ODBC-390) Using SQL\_ATTR\_QUERY\_TIMEOUT leaks memory
* [Revision #313102f](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/313102f)\
  2023-04-13 13:47:37 -0400
  * bump the VERSION
* [Revision #2459006](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/2459006)\
  2023-03-31 16:59:09 +0200
  * Fix of the testxase for iOdbc
* [Revision #373ade1](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/373ade1)\
  2023-03-21 15:00:16 +0100
  * [ODBC-313](https://jira.mariadb.org/browse/ODBC-313) The testcase for the fix, that has been already committed
* [Revision #889c56e](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/889c56e)\
  2023-04-28 13:49:37 +0200
  * [ODBC-389](https://jira.mariadb.org/browse/ODBC-389) alloc-dealloc mismatch
* [Revision #7a50276](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/7a50276)\
  2023-04-28 12:16:35 +0200
  * Added ':' as key-value separator for client attributes
* [Revision #836aef5](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/836aef5)\
  2023-04-21 14:58:16 -0400
  * bump the VERSION

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
