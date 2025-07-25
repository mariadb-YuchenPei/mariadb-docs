# Connector/ODBC 3.1.14 Changelog

The most recent [_**Stable**_](../../../../community-server/about/release-criteria.md) _**(GA)**_ release of MariaDB Connector/ODBC is:[**MariaDB Connector/ODBC 3.2.5**](../../mariadb-connector-odbc-3-2-release-notes/mariadb-connector-odbc-3-2-5-release-notes.md)

[Download](https://mariadb.com/downloads/#connectors)[Release Notes](../../mariadb-connector-odbc-3-1-release-notes/mariadb-connector-odbc-3-1-14-release-notes.md)[Changelog](mariadb-connector-odbc-3114-changelog.md)[About MariaDB Connector/ODBC](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-odbc/README.md)

**Release date:** 29 Oct 2021

For the highlights of this release, see the[release notes](../../mariadb-connector-odbc-3-1-release-notes/mariadb-connector-odbc-3-1-14-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On[GitHub](https://github.com/MariaDB/mariadb-connector-odbc) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #9a91685](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/9a91685)\
  2021-10-24 22:14:07 +0200
  * [ODBC-331](https://jira.mariadb.org/browse/ODBC-331) Actually moving libmariadb to 3.2.4
* [Revision #28aeddc](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/28aeddc)\
  2021-10-24 14:13:38 +0200
  * Changed default for WITH\_MSI to ON
* [Revision #0bb3767](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/0bb3767)\
  2021-10-22 19:00:50 +0200
  * [ODBC-341](https://jira.mariadb.org/browse/ODBC-341) Dialog fields for new READ\_TIMEOUT and WRITE\_TIMEOUT options
* [Revision #8f87425](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/8f87425)\
  2021-10-21 23:13:40 +0200
  * [ODBC-340](https://jira.mariadb.org/browse/ODBC-340) cmake could lose openssl libs in the list of dependencies
* [Revision #53c5ce0](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/53c5ce0)\
  2021-10-19 09:52:33 +0200
  * add testcase for read/write timeout; it's an adaptation of a unittest found inside libmariadb
* [Revision #ae1a6a1](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/ae1a6a1)\
  2021-10-13 15:41:26 +0200
  * allows to set read/write timeout via DSN parameters READ\_TIMEOUT and WRITE\_TIMEOUT
* [Revision #1bef182](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/1bef182)\
  2021-10-18 00:41:44 +0200
  * Added xcode properties required for notarization to C/C plugins
* [Revision #f4a891d](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/f4a891d)\
  2021-08-12 10:28:48 +0000
  * Adding few fixes to the s390x Travis job
* [Revision #1fa6712](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/1fa6712)\
  2021-10-10 11:24:16 +0200
  * Added libmaodbc.pc
* [Revision #28cec7e](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/28cec7e)\
  2021-09-20 12:36:23 +0200
  * [ODBC-320](https://jira.mariadb.org/browse/ODBC-320) (possibly not all) Changes required for successful notarization
* [Revision #5133f68](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/5133f68)\
  2021-09-09 15:06:57 +0200
  * [ODBC-331](https://jira.mariadb.org/browse/ODBC-331) Moved C/C to 3.2 branch
* [Revision #ff3031c](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/ff3031c)\
  2021-08-12 23:19:25 +0200
  * [ODBC-299](https://jira.mariadb.org/browse/ODBC-299) Fix of build on MacOS Big Sur
* [Revision #6761b5d](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/6761b5d)\
  2021-08-11 10:12:59 +0200
  * Moved s390 tot allow\_failures on travis, as it's not supported yet
* [Revision #8a60619](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/8a60619)\
  2021-06-18 15:31:40 +0530
  * Update .travis.yml
* [Revision #bd1bc38](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/bd1bc38)\
  2021-06-18 15:29:12 +0530
  * Update s390x.sh
* [Revision #6f0c52b](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/6f0c52b)\
  2021-06-18 13:45:10 +0530
  * Update s390x.sh
* [Revision #ab1bde4](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/ab1bde4)\
  2021-06-18 13:29:40 +0530
  * Update s390x.sh
* [Revision #4d3dd13](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/4d3dd13)\
  2021-06-18 13:26:41 +0530
  * Update .travis.yml
* [Revision #3f04587](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/3f04587)\
  2021-06-09 11:08:54 +0530
  * Create s390x.sh
* [Revision #d60ebaf](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/d60ebaf)\
  2021-06-09 11:07:49 +0530
  * Update .travis.yml
* [Revision #237887b](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/237887b)\
  2021-06-09 11:06:57 +0530
  * Update .travis.yml
* [Revision #2708333](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/2708333)\
  2021-07-28 19:23:27 +0530
  * Update ma\_statement.c
* [Revision #6e3ea47](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/6e3ea47)\
  2021-07-28 18:41:53 +0530
  * Update ma\_statement.c
* [Revision #35f2e36](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/35f2e36)\
  2021-06-18 10:51:57 +0100
  * Use '''' instead of ''' for increased robustnesss
* [Revision #50f2aec](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/50f2aec)\
  2021-08-09 15:15:10 +0200
  * Fix of the testcase in catalog2, that failed with 10.2 server
* [Revision #18f9675](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/18f9675)\
  2021-08-09 13:33:07 +0200
  * [ODBC-321](https://jira.mariadb.org/browse/ODBC-321) The fix and the testcase
* [Revision #61a7763](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/61a7763)\
  2021-08-09 00:19:54 +0200
  * [ODBC-334](https://jira.mariadb.org/browse/ODBC-334) If TcpIp is selected, and port is 0, default port will be used
* [Revision #0c7ff3a](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/0c7ff3a)\
  2021-08-02 14:16:51 +0200
  * [ODBC-330](https://jira.mariadb.org/browse/ODBC-330) Added WiX as prerequisite in BUILD.md and check of WiX binaries
* [Revision #5914ebf](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/5914ebf)\
  2021-08-02 09:32:36 +0200
  * [ODBC-326](https://jira.mariadb.org/browse/ODBC-326) Error while connecting Excel via Microsoft Query
* [Revision #6fcd1b9](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/6fcd1b9)\
  2021-07-30 22:50:56 +0200
  * [ODBC-324](https://jira.mariadb.org/browse/ODBC-324) SQLTables would not show versioned tables
* [Revision #8ce387a](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/8ce387a)\
  2021-05-13 14:35:31 +0700
  * [ODBC-311](https://jira.mariadb.org/browse/ODBC-311) Connector/ODBC libraries go to the wrong directories and it breaks packaging
* [Revision #3c0611e](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/3c0611e)\
  2021-06-08 01:19:56 -0400
  * bump the VERSION

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
