# Connector/C 1.0.0 Changelog

The most recent [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release of MariaDB Connector/C is:[**MariaDB Connector/C 3.4.5**](../mariadb-connector-c-3-4-release-notes/mariadb-connector-c-3-4-5-release-notes.md)

[Download](https://downloads.mariadb.org/connector-c/1.0.0)[Release Notes](../mariadb-client-library-for-c-100-release-notes.md)[Changelog](mariadb-client-library-for-c-100-changelog.md)[About MariaDB Connector/C](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-c/README.md)

**Release date:** 29 Nov 2012

For the highlights of this release, see the [release notes](../mariadb-client-library-for-c-100-release-notes.md).

The revision number links will take you to the revision's page on Launchpad. On\
Launchpad you can view more details of the revision and view diffs of the code\
modified in that revision.

* [Revision #77](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/77)\
  Sat 2013-08-03 18:39:05 +0200
  * Fix for [CONC-42](https://jira.mariadb.org/browse/CONC-42): More informative errormessages for handshake errors
* [Revision #76](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/76)\
  Fri 2013-08-02 17:58:57 +0200
  * Fix for [CONC-41](https://jira.mariadb.org/browse/CONC-41): Connect errormessage doesn't return socket error
* [Revision #75](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/75)\
  Thu 2013-08-01 15:23:48 +0200
  * Fixed LOAD DATA LOCAL INFILE crash when specifying a file which doesn't exist Fixed error message for non existing file (was errno=0)
* [Revision #74](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/74)\
  Thu 2013-08-01 09:56:36 +0200
  * Fixed crash/undefined behaviour when running large amount of threads: replaced select() with poll() Added conneciton timeout support for windows platforms
* [Revision #73](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/73)\
  Wed 2013-07-24 07:01:48 +0200
  * Several test fixes
* [Revision #72](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/72)\
  Mon 2013-07-22 07:22:04 +0200
  * Fixes for Solaris build (Bugs [CONC-36](https://jira.mariadb.org/browse/CONC-36),[CONC-37](https://jira.mariadb.org/browse/CONC-37) and [CONC-38](https://jira.mariadb.org/browse/CONC-38))
* [Revision #71](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/71)\
  Mon 2013-07-15 10:47:05 +0200
  * DBUG update and fixes Fixed net\_read crash in debug version
* [Revision #70](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/70)\
  Wed 2013-07-03 07:37:10 +0200\
  \*
  * More OS/X fixes - Fixed wrong error message in mysql\_real\_connect
* [Revision #69](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/69)\
  Mon 2013-07-01 05:27:17 +0200
  * Fixed compiler warnings
* [Revision #68](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/68)\
  Mon 2013-07-01 05:00:34 +0200
  * Reworked compressed and protocol implementation, including fixes for [CONC-31](https://jira.mariadb.org/browse/CONC-31) and [CONC-34](https://jira.mariadb.org/browse/CONC-34) - Added win64 fixes in protocol (changed ulong to size\_t)
* [Revision #67](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/67)\
  Mon 2013-06-17 06:58:20 +0200
  * Fix for [CONC-27](https://jira.mariadb.org/browse/CONC-27): Prevent crash if mysql\_thread\_end was called without prior initialization via mysql\_thread\_init
* [Revision #66](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/66)\
  Thu 2013-06-13 11:38:37 +0200
  * Fix for OSX build: rename sigset to my\_sigset
* [Revision #65](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/65)\
  Wed 2013-06-12 15:58:37 +0200
  * Fix for [CONC-30](https://jira.mariadb.org/browse/CONC-30): Compilation issue on CentOS 3.9
* [Revision #64](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/64)\
  Mon 2013-06-03 08:27:12 +0200
  * Fixed reconnect problem Added workaround for [MDEV-4604](https://jira.mariadb.org/browse/MDEV-4604) in mysql\_stmt\_store\_result
* [Revision #63](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/63)\
  Sat 2013-06-01 13:50:35 +0200
  * Added workaround for [MDEV-6304](https://jira.mariadb.org/browse/MDEV-6304): In mysql\_stmt\_more\_results we check for both SERVER\_MORE\_RESULTS\_EXIST and for SERVER\_PS\_OUT\_PARAMS
* [Revision #62](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/62)\
  Wed 2013-05-29 11:59:01 +0200
  * Fixed crash when calling mysql\_close\_options twice (pointer weren't adjusted to NULL) Fixed wrong behaviour when using stored procedures inside prepared statements Fixed identiation in my\_stmt.h
* [Revision #61](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/61)\
  Mon 2013-05-20 18:00:08 +0200\
  \*
  * Fixed memory overrun in mysql\_stmt\_execute due to wrong length calculation. - Fixed bug in mysql\_stmt\_next\_result - Fixed mysql\_stmt\_reset: multi result sets weren't flushed properly - Fixed several test cases
* [Revision #60](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/60)\
  Mon 2013-05-20 10:50:58 +0200
  * Fix for prepared statment multi results: Reallocate buffers (fields and binds) for new resultsets
* [Revision #59](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/59)\
  Fri 2013-05-10 10:27:42 +0200
  * [CONC-26](https://jira.mariadb.org/browse/CONC-26): CLIENT\_REMEMBER\_OPTIONS is not supported
* [Revision #58](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/58)\
  Thu 2013-05-09 14:11:33 +0200
  * Fixed [CONC-9](https://jira.mariadb.org/browse/CONC-9): removed winsock2 from mysql.h Fixed [CONC-24](https://jira.mariadb.org/browse/CONC-24): reconnect failed mysql\_reconnect didn't set reconnect flag for new connection
* [Revision #57](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/57)\
  Thu 2013-05-09 12:05:38 +0200
  * Fixed bug in mysql\_stmt\_data\_seek: Reset the status of stmt to user fetching, otherwise stmt\_data\_seek will not work after fetch returned MYSQL\_NO\_DATA. Removed examples from build. This directory should be moved into doc tree
* [Revision #56](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/56)\
  Tue 2013-04-30 18:02:53 +0200
  * Added microseconds support for prepared statements: datetime, timestamp and time to string conversion now returns microsenconds
* [Revision #55](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/55)\
  Thu 2013-04-25 18:24:21 +0200
  * Fix for [CONC-21](https://jira.mariadb.org/browse/CONC-21): Ignore the 5.5.5- prefix for MariaDB 10 and report correct version numbers
* [Revision #54](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/54)\
  Thu 2013-04-25 08:14:23 +0200
  * Fix for [CONC-14](https://jira.mariadb.org/browse/CONC-14): Monitor the socket status in net\_clear: In case of a disconnection send\_query will try to reconnect
* [Revision #53](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/53)\
  Wed 2013-04-24 17:02:03 +0200
  * Fix for unbuffered stmt fetch: increase number of rows Added Test for [CONC-24](https://jira.mariadb.org/browse/CONC-24)
* [Revision #52](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/52)\
  Fri 2013-04-12 11:24:42 +0200
  * Fixed memory overrun (wrong length calculation in mysql\_stmt\_generate\_request) Fuxed crash with mysql\_send\_long\_data
* [Revision #51](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/51)\
  Fri 2013-03-29 18:29:35 +0100
  * Added missing -lm for mariadb\_config
* [Revision #50](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/50)\
  Tue 2013-03-26 11:31:54 +0100
  * Fixed crash when running out of memory in mysql\_stmt\_init.
* [Revision #49](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/49)\
  Sun 2013-03-24 18:04:45 +0100
  * Changed default built options
* [Revision #48](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/48)\
  Sun 2013-03-24 15:14:06 +0100
  * Fix for bug [CONC-16](https://jira.mariadb.org/browse/CONC-16): ource tarball without version info in filename
* [Revision #47](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/47)\
  Sun 2013-03-24 14:29:24 +0100
  * Test case fixes
* [Revision #46](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/46)\
  Wed 2013-03-20 11:00:46 +0100
  * Added MSI Installer for Windows
* [Revision #45](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/45)\
  Tue 2013-03-19 14:53:56 +0100
  * Disable DBUG for Release builds
* [Revision #44](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/44)\
  Tue 2013-03-19 13:31:29 +0100
  * Fixed build (CMAKE\_BINARY\_DIR for symbolic links)
* [Revision #43](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/43)\
  Tue 2013-03-19 13:24:39 +0100
  * Fixed wrong symlink (Thanks to Axel Schwenke)
* [Revision #42](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/42)\
  Sun 2013-03-17 12:32:08 +0100
  * Fix for [CONC-15](https://jira.mariadb.org/browse/CONC-15) Removed redundant prototypes Fixed several prototypes with void parameters
* [Revision #41](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/41)\
  Sun 2013-03-17 11:46:50 +0100
  * Fix for CONNC-18 declare local\_thr\_alaram as static
* [Revision #40](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/40)\
  Wed 2013-03-13 21:43:39 +0100
  * more test fixes
* [Revision #39](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/39)\
  Wed 2013-03-13 11:00:56 +0100
  * Fixed bug in character set autodetection Fixed compiler warnings in test suite Skipped change\_users tests: They don't work anymore (mysql\_change\_user) security fix Applied patch from John Schember
* [Revision #38](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/38)\
  Sat 2013-03-09 09:49:04 +0100
  * Replaced byte declarations (now unsigned char) Added initial support for character set autodetection
* [Revision #37](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/37)\
  Thu 2013-03-07 13:56:14 +0100
  * Fix dbug crash in mysql\_server\_end
* [Revision #36](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/36)\
  Tue 2013-02-26 11:52:22 +0100
  * Export of mysql\_ps\_fetch\_functions: This will allow clients to convert values after fetch (e.g. SQLGetData)
* [Revision #35](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/35)\
  Wed 2013-02-13 18:35:25 +0100
  * Prevent freeing of options if connect failed.
* [Revision #34](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/34)\
  Wed 2013-01-30 17:44:35 +0100
  * Updated documentation
* [Revision #33](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/33)\
  Wed 2013-01-30 08:42:05 +0100
  * Added missing test for embedded
* [Revision #32](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/32)\
  Wed 2013-01-30 08:37:24 +0100
  * Added support for embedded (sqlite)
* [Revision #31](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/31)\
  Wed 2013-01-23 07:25:26 +0100
  * Added support for options in options->extension
* [Revision #30](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/30)\
  Mon 2013-01-21 13:52:53 +0100
  * Fix for [CONC-7](https://jira.mariadb.org/browse/CONC-7): - added missing server error codes for MariaDB and MySQL Server - added symbolic links for projects which don't support mariadb\_config
* [Revision #29](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/29)\
  Sun 2013-01-20 14:08:36 +0100
  * Fix for connc-6: added missing functions - mysql\_library\_init,end as an alias for mysql\_server\_init/end - mysql\_get\_server and mariadb\_connection to determine type of server (mysql or mariadb)
* [Revision #28](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/28)\
  Thu 2012-12-27 12:02:09 +0100
  * Fixed license headers which didn't mention PHP code
* [Revision #27](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/27)\
  Wed 2012-12-26 23:14:09 +0100
  * Don't max out on windows warning settings, it is not practical - there are thousands of insignificant warnings
* [Revision #26](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/26)\
  Wed 2012-12-26 22:20:50 +0100
  * [CONC-4](https://jira.mariadb.org/browse/CONC-4) : link with static C runtime when using MSVC
* [Revision #25](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/25)\
  Wed 2012-12-26 20:57:26 +0100
  * Fix for bug [CONC-5](https://jira.mariadb.org/browse/CONC-5): field->catalog is undefined if result set was obtained from mysql\_stmt\_result\_metadata()
* [Revision #24](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/24)\
  Mon 2012-12-17 19:05:09 +0100
  * Fix for [CONC-3](https://jira.mariadb.org/browse/CONC-3): In older CMake versions FindOpenSSL.cmake doesn't work as expected, (OPENSSL\_LIBRARIES doesn't contain crypto library), so we set the required cmake version number to 2.8.0 and above
* [Revision #23](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/23)\
  Sun 2012-12-16 12:05:40 +0100
  * some clean up
* [Revision #22](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/22)\
  Sat 2012-12-15 13:49:47 +0100
  * Added IPV6 support
* [Revision #21](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/21)\
  Sat 2012-12-15 08:23:43 +0100
  * Fix for [CONC-1](https://jira.mariadb.org/browse/CONC-1) (Inverted error messages no 2058,2059) Added support for old password authentication: - Fixed scramble\_323: use exact length of message (SCRAMBLE\_LENGTH\_323 instead of strlen(message)) - Added old\_password\_authentication plugin into list of builtin plugins
* [Revision #20](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/20)\
  Tue 2012-12-11 20:29:50 +0100
  * removed mysql\_io.c (php streams), which is no longer used
* [Revision #19](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/19)\
  Sat 2012-12-01 14:02:34 +0100
  * Fixes for SSL - fix for php bug 51647 - added cert store - added certificates for testing
* [Revision #18](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/18)\
  Fri 2012-11-30 13:47:24 +0100
  * Fix for mariadb\_config: lib output was not correct cleanup fixed ps\_test (warning\_count differs on MariaDB servers)
* [Revision #17](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/17)\
  Thu 2012-11-29 17:27:56 +0100\
  \*
  * Fix for mysql\_stmt\_next\_result: obtain number of fields from mysql structure added test case (ps\_new.c) - Added additional parameter cipher for mysql\_ssl\_set - some cosmetics for test cases
* [Revision #16](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/16) \[merge]\
  Thu 2012-11-29 11:25:44 +0100
  * merge georg's fixes
  * [Revision #12.2.1](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/12.2.1) \[merge]\
    Thu 2012-11-29 11:02:40 +0100
    * merge
    * [Revision #12.1.1](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/12.1.1)\
      Thu 2012-11-29 09:06:15 +0100
      * implementation for mysql\_stmt\_next\_result fixed size of MYSQL: removed unused NET->cmd\_buffer\_length minor cosmetic fixes
* [Revision #15](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/15)\
  Thu 2012-11-29 01:58:44 +0100
  * fix typo in shared library versioning
* [Revision #14](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/14)\
  Wed 2012-11-28 22:44:42 +0100
  * set include directory correctly
* [Revision #13](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/13)\
  Wed 2012-11-28 23:13:00 +0100
  * re-branding
* [Revision #12](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/12)\
  Wed 2012-11-28 14:09:17 +0100
  * fix typo
* [Revision #11](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/11)\
  Wed 2012-11-28 12:30:33 +0100
  * more fixes, do not compile zlib library if system one is not found. Instead, add zlib source files to the libmysql\_sources
* [Revision #10](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/10)\
  Wed 2012-11-28 03:00:18 +0100
  * More CMake fixes, use system zlib when possible
* [Revision #9](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/9)\
  Wed 2012-11-28 02:43:39 +0100
  * as-needed is not recognized on mint
* [Revision #8](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/8)\
  Wed 2012-11-28 03:29:05 +0100
  * Further CMake fixes ensure no unresolved symbols in shared library
* [Revision #7](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/7)\
  Wed 2012-11-28 01:04:21 +0100
  * Fix export symbols from shared library on Windows, again
* [Revision #6](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/6)\
  Wed 2012-11-28 00:53:08 +0100
  * Fix build if openssl is not found various cosmetic bugs in cmake
* [Revision #5](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/5)\
  Tue 2012-11-27 09:57:10 +0100
  * Fixed crash when trying to call mysql\_close twice Fixed mysql\_config Header changes
* [Revision #4](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/4)\
  Mon 2012-11-26 11:23:56 +0100\
  \*
  * Added documentation (docbook based) - To build the documentation use cmake . -DBUILD\_DOCS=yes - minor fixes in tests
* [Revision #3](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/3)\
  Mon 2012-11-26 08:32:41 +0100
  * Added openssl layer support Imported libmysql unittests Added simple ssl tests minor cleanup
* [Revision #2](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/2)\
  Wed 2012-11-14 18:43:45 +0100
  * First implementation based on libmysql 3.23.58 and php's mysqlnd extension
* [Revision #1](https://bazaar.launchpad.net/~maria-captains/mariadb-native-client/trunk/revision/1)\
  Mon 2011-10-10 14:01:17 +0300
  * Initial import

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
