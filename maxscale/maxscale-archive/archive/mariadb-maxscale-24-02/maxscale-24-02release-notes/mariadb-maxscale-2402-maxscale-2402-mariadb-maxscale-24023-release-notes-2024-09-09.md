# MariaDB MaxScale 24.02.3 Release Notes -- 2024-09-09

Release 24.02.3 is a GA release.

This document describes the changes in release 24.02.3, when compared to the\
previous release in the same series.

If you are upgrading from an older major version of MaxScale, please read the[upgrading document](https://mariadb.com/kb/Upgrading/Upgrading-To-MaxScale-24.02) for\
this MaxScale version.

For any problems you encounter, please consider submitting a bug\
report on [our Jira](https://jira.mariadb.org/projects/MXS).

### Bug fixes

* [MXS-5234](https://jira.mariadb.org/browse/MXS-5234) webpack warns about yargs
* [MXS-5232](https://jira.mariadb.org/browse/MXS-5232) Large batches of session commands may leave sessions alive for a long time
* [MXS-5231](https://jira.mariadb.org/browse/MXS-5231) Connections to servers in maintenance are sometimes not discarded
* [MXS-5227](https://jira.mariadb.org/browse/MXS-5227) MaxScale does not drop supplementary groups if --user is used
* [MXS-5226](https://jira.mariadb.org/browse/MXS-5226) LICENSE.TXT is a dangling symlink in RPMs
* [MXS-5213](https://jira.mariadb.org/browse/MXS-5213) Erroneous "Cluster gtid domain is unknown" error message during failover
* [MXS-5209](https://jira.mariadb.org/browse/MXS-5209) Reads with max\_slave\_connections=0 after a switchover do not discard stale connections
* [MXS-5206](https://jira.mariadb.org/browse/MXS-5206) Readwritesplit does not drop connections to severely lagging servers
* [MXS-5200](https://jira.mariadb.org/browse/MXS-5200) CMake 3.28.3 warnings
* [MXS-5198](https://jira.mariadb.org/browse/MXS-5198) Default logrotate config in .deb / docu missing params
* [MXS-5196](https://jira.mariadb.org/browse/MXS-5196) /maxscale/logs/data may return no data if maxlog=0 and syslog=1
* [MXS-5193](https://jira.mariadb.org/browse/MXS-5193) Multi-statement commands may end up being stored in the session command history
* [MXS-5191](https://jira.mariadb.org/browse/MXS-5191) Two cache filters in same service causes errors on session creation
* [MXS-5190](https://jira.mariadb.org/browse/MXS-5190) dotnet EntityFrameworkCore generates insert queries that are getting routed to all nodes as session write
* [MXS-5179](https://jira.mariadb.org/browse/MXS-5179) Active schema is not highlighted in the schema tree explorer
* [MXS-5171](https://jira.mariadb.org/browse/MXS-5171) MaxScale does not have time to open the file during rotation for a new binlog
* [MXS-5165](https://jira.mariadb.org/browse/MXS-5165) MariaDB Monitor rebuild server may try to chown "/var/lib/mysql/" instead of just "/var/lib/mysql"
* [MXS-5162](https://jira.mariadb.org/browse/MXS-5162) Post reboot binlog router entered stuck state
* [MXS-5160](https://jira.mariadb.org/browse/MXS-5160) postinst script prints output while installing
* [MXS-5159](https://jira.mariadb.org/browse/MXS-5159) MaxScale does not use remote address sent in proxy header from client for authenticating the client
* [MXS-5146](https://jira.mariadb.org/browse/MXS-5146) 23.08.6 build ppc64le fails
* [MXS-5135](https://jira.mariadb.org/browse/MXS-5135) The GUI should clear all http readonly cookies
* [MXS-5133](https://jira.mariadb.org/browse/MXS-5133) Memory leak in namedserverfilter
* [MXS-5132](https://jira.mariadb.org/browse/MXS-5132) Inbound proxy protocol does not generate the correct error if proxy\_protocol\_network is not defined
* [MXS-5131](https://jira.mariadb.org/browse/MXS-5131) comment filter uses the wrong module name
* [MXS-5129](https://jira.mariadb.org/browse/MXS-5129) Cache may delete values from LRU but not from storage
* [MXS-5128](https://jira.mariadb.org/browse/MXS-5128) Failed patching passive parameter value
* [MXS-5127](https://jira.mariadb.org/browse/MXS-5127) DEALLOCATE PREPARE is not routed to all nodes
* [MXS-5126](https://jira.mariadb.org/browse/MXS-5126) Segfault in cache filter with default configuration
* [MXS-5125](https://jira.mariadb.org/browse/MXS-5125) Executing identical prepared statements may lose one of them on reconnection
* [MXS-5121](https://jira.mariadb.org/browse/MXS-5121) MaxScale detects wrong server character set
* [MXS-5109](https://jira.mariadb.org/browse/MXS-5109) A logout endpoint for the GUI to clear all http readonly cookies
* [MXS-4605](https://jira.mariadb.org/browse/MXS-4605) Monitor should drop the connection when faced with an Access Denied error

### Known Issues and Limitations

There are some limitations and known issues within this version of MaxScale.\
For more information, please refer to the [Limitations](../maxscale-24-02about/mariadb-maxscale-2402-maxscale-2402-limitations-and-known-issues-within-mariadb-maxscale.md) document.

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
