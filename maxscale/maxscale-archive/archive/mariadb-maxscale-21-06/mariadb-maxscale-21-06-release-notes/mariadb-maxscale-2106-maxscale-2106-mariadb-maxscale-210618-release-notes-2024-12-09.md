# MariaDB MaxScale 21.06.18 Release Notes -- 2024-12-09

Release 21.06.18 is a GA release.

This document describes the changes in release 21.06.18, when compared to the\
previous release in the same series.

If you are upgrading from an older major version of MaxScale, please read the[upgrading document](https://mariadb.com/kb/Upgrading/Upgrading-To-MaxScale-21) for\
this MaxScale version.

For any problems you encounter, please consider submitting a bug\
report on [our Jira](https://jira.mariadb.org/projects/MXS).

### External CVEs resolved.

* [CVE-2023-0437](https://www.cve.org/CVERecord?id=CVE-2023-0437) Fixed by [MXS-5400](https://jira.mariadb.org/browse/MXS-5400) Upgrade MongoC library to 1.27.5
* [CVE-2024-7553](https://www.cve.org/CVERecord?id=CVE-2024-7553) Fixed by [MXS-5400](https://jira.mariadb.org/browse/MXS-5400) Upgrade MongoC library to 1.27.5

### Bug fixes

* [MXS-5394](https://jira.mariadb.org/browse/MXS-5394) Empty passwords are shown as non-empty if password encryption is enabled
* [MXS-5387](https://jira.mariadb.org/browse/MXS-5387) Crash in MariaDBParser::Helper::get\_query\_info()
* [MXS-5378](https://jira.mariadb.org/browse/MXS-5378) Nested listener parameters depend on protocol being defined
* [MXS-5377](https://jira.mariadb.org/browse/MXS-5377) Debug assert if backend fails during multi-packet query
* [MXS-5374](https://jira.mariadb.org/browse/MXS-5374) Kafkaimporter doesn't work with MariaDB 11
* [MXS-5372](https://jira.mariadb.org/browse/MXS-5372) timeout in kafkacdc is not a duration type
* [MXS-5363](https://jira.mariadb.org/browse/MXS-5363) GDB stacktraces may hang
* [MXS-5357](https://jira.mariadb.org/browse/MXS-5357) Improve MariaDB Monitor documentation on auto\_failover and auto\_rejoin
* [MXS-5344](https://jira.mariadb.org/browse/MXS-5344) Kafkaimporter constraint makes it difficult to use with kafkacdc
* [MXS-5343](https://jira.mariadb.org/browse/MXS-5343) Kafkacdc does not mention row-based replication as a requirement
* [MXS-5341](https://jira.mariadb.org/browse/MXS-5341) User account manager hangs on shutdown
* [MXS-5339](https://jira.mariadb.org/browse/MXS-5339) Slow servers may cause OOM situations if prepared statements are used
* [MXS-5302](https://jira.mariadb.org/browse/MXS-5302) Prepared statements should never be removed from session command history
* [MXS-5298](https://jira.mariadb.org/browse/MXS-5298) Kafkacdc always reads last GTID from Kafka on startup
* [MXS-5295](https://jira.mariadb.org/browse/MXS-5295) SET NAMES UTF8MB4,autocommit=0 is not detected correctly
* [MXS-5273](https://jira.mariadb.org/browse/MXS-5273) The --config-check fails if /var/cache/maxscale cannot be read
* [MXS-5268](https://jira.mariadb.org/browse/MXS-5268) Read-only error during read-write transaction should trigger transaction replay
* [MXS-5264](https://jira.mariadb.org/browse/MXS-5264) MaxScale installs scripts with non-standard file permissions
* [MXS-5263](https://jira.mariadb.org/browse/MXS-5263) Valgrind reports read from uninitialized GWBUF for ccrfilter
* [MXS-5259](https://jira.mariadb.org/browse/MXS-5259) Retrying of reads on the current primary unnecessarily requires delayed\_retry
* [MXS-5258](https://jira.mariadb.org/browse/MXS-5258) delayed\_retry should not retry interrupted writes
* [MXS-5256](https://jira.mariadb.org/browse/MXS-5256) SET statements multiple values are not parsed correctly
* [MXS-5255](https://jira.mariadb.org/browse/MXS-5255) test\_mxb\_string sometimes times out on aarch64
* [MXS-5248](https://jira.mariadb.org/browse/MXS-5248) Debug assertion due to non-existent dcall ID
* [MXS-5247](https://jira.mariadb.org/browse/MXS-5247) Remove obsolete prelink script
* [MXS-5245](https://jira.mariadb.org/browse/MXS-5245) MaxCtrl does not accept dot notation for nested parameters
* [MXS-5239](https://jira.mariadb.org/browse/MXS-5239) Listener with ssl=false allows user accounts created with REQUIRE SSL to log in
* [MXS-5236](https://jira.mariadb.org/browse/MXS-5236) wsrep\_desync behavior is undocumented
* [MXS-5234](https://jira.mariadb.org/browse/MXS-5234) webpack warns about yargs
* [MXS-5229](https://jira.mariadb.org/browse/MXS-5229) Master Stickiness status not displayed correctly with use\_priority
* [MXS-5178](https://jira.mariadb.org/browse/MXS-5178) Replicas after maxscale binlog don't get updates

### Known Issues and Limitations

In the previous version of MaxScale, maxctrl was implemented as a JavaScript\
script that was run using the node interpreter on the platform. That introduced\
a dependency on node that earlier was not present. In this version of MaxScale,\
maxctrl is again a native executable without that dependency.

There are some limitations and known issues within this version of MaxScale.\
For more information, please refer to the [Limitations](../mariadb-maxscale-21-06-about/mariadb-maxscale-2106-maxscale-2106-limitations-and-known-issues-within-mariadb-maxscale.md) document.

### Packaging

RPM and Debian packages are provided for the supported Linux distributions.

Packages can be downloaded [here](https://mariadb.com/downloads/#mariadb_platform-mariadb_maxscale).

### Source Code

The source code of MaxScale is tagged at GitHub with a tag, which is identical\
with the version of MaxScale. For instance, the tag of version X.Y.Z of MaxScale\
is `maxscale-X.Y.Z`. Further, the default branch is always the latest GA version\
of MaxScale.

The source code is available [here](https://github.com/mariadb-corporation/MaxScale).

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
