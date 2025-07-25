# MaxScale 22.08 MariaDB Monitor

## MariaDB Monitor

## MariaDB Monitor

* [MariaDB Monitor](mariadb-maxscale-2208-mariadb-monitor.md#mariadb-monitor)
  * [Overview](mariadb-maxscale-2208-mariadb-monitor.md#overview)
  * [Required Grants](mariadb-maxscale-2208-mariadb-monitor.md#required-grants)
    * [Cluster Manipulation Grants](mariadb-maxscale-2208-mariadb-monitor.md#cluster-manipulation-grants)
  * [Master selection](mariadb-maxscale-2208-mariadb-monitor.md#master-selection)
  * [Configuration](mariadb-maxscale-2208-mariadb-monitor.md#configuration)
  * [Common Monitor Parameters](mariadb-maxscale-2208-mariadb-monitor.md#common-monitor-parameters)
  * [MariaDB Monitor optional parameters](mariadb-maxscale-2208-mariadb-monitor.md#mariadb-monitor-optional-parameters)
    * [assume\_unique\_hostnames](mariadb-maxscale-2208-mariadb-monitor.md#assume_unique_hostnames)
    * [master\_conditions](mariadb-maxscale-2208-mariadb-monitor.md#master_conditions)
    * [slave\_conditions](mariadb-maxscale-2208-mariadb-monitor.md#slave_conditions)
    * [failcount](mariadb-maxscale-2208-mariadb-monitor.md#failcount)
    * [enforce\_writable\_master](mariadb-maxscale-2208-mariadb-monitor.md#enforce_writable_master)
    * [enforce\_read\_only\_slaves](mariadb-maxscale-2208-mariadb-monitor.md#enforce_read_only_slaves)
    * [enforce\_read\_only\_servers](mariadb-maxscale-2208-mariadb-monitor.md#enforce_read_only_servers)
    * [maintenance\_on\_low\_disk\_space](mariadb-maxscale-2208-mariadb-monitor.md#maintenance_on_low_disk_space)
    * [cooperative\_monitoring\_locks](mariadb-maxscale-2208-mariadb-monitor.md#cooperative_monitoring_locks)
    * [script\_max\_replication\_lag](mariadb-maxscale-2208-mariadb-monitor.md#script_max_replication_lag)
  * [Cluster manipulation operations](mariadb-maxscale-2208-mariadb-monitor.md#cluster-manipulation-operations)
    * [Operation details](mariadb-maxscale-2208-mariadb-monitor.md#operation-details)
    * [Manual activation](mariadb-maxscale-2208-mariadb-monitor.md#manual-activation)
      * [Queued switchover](mariadb-maxscale-2208-mariadb-monitor.md#queued-switchover)
    * [Automatic activation](mariadb-maxscale-2208-mariadb-monitor.md#automatic-activation)
    * [Limitations and requirements](mariadb-maxscale-2208-mariadb-monitor.md#limitations-and-requirements)
    * [External master support](mariadb-maxscale-2208-mariadb-monitor.md#external-master-support)
    * [Configuration parameters](mariadb-maxscale-2208-mariadb-monitor.md#configuration-parameters)
      * [auto\_failover](mariadb-maxscale-2208-mariadb-monitor.md#auto_failover)
      * [auto\_rejoin](mariadb-maxscale-2208-mariadb-monitor.md#auto_rejoin)
      * [switchover\_on\_low\_disk\_space](mariadb-maxscale-2208-mariadb-monitor.md#switchover_on_low_disk_space)
      * [enforce\_simple\_topology](mariadb-maxscale-2208-mariadb-monitor.md#enforce_simple_topology)
      * [replication\_user and replication\_password](mariadb-maxscale-2208-mariadb-monitor.md#replication_user-and-replication_password)
      * [replication\_master\_ssl](mariadb-maxscale-2208-mariadb-monitor.md#replication_master_ssl)
      * [failover\_timeout and switchover\_timeout](mariadb-maxscale-2208-mariadb-monitor.md#failover_timeout-and-switchover_timeout)
      * [verify\_master\_failure](mariadb-maxscale-2208-mariadb-monitor.md#verify_master_failure)
      * [master\_failure\_timeout](mariadb-maxscale-2208-mariadb-monitor.md#master_failure_timeout)
      * [servers\_no\_promotion](mariadb-maxscale-2208-mariadb-monitor.md#servers_no_promotion)
      * [promotion\_sql\_file and demotion\_sql\_file](mariadb-maxscale-2208-mariadb-monitor.md#promotion_sql_file-and-demotion_sql_file)
      * [handle\_events](mariadb-maxscale-2208-mariadb-monitor.md#handle_events)
  * [Cooperative monitoring](mariadb-maxscale-2208-mariadb-monitor.md#cooperative-monitoring)
    * [Releasing locks](mariadb-maxscale-2208-mariadb-monitor.md#releasing-locks)
  * [Rebuild server](mariadb-maxscale-2208-mariadb-monitor.md#rebuild-server)
    * [Settings](mariadb-maxscale-2208-mariadb-monitor.md#settings)
      * [ssh\_user](mariadb-maxscale-2208-mariadb-monitor.md#ssh_user)
      * [ssh\_keyfile](mariadb-maxscale-2208-mariadb-monitor.md#ssh_keyfile)
      * [ssh\_check\_host\_key](mariadb-maxscale-2208-mariadb-monitor.md#ssh_check_host_key)
      * [ssh\_timeout](mariadb-maxscale-2208-mariadb-monitor.md#ssh_timeout)
      * [ssh\_port](mariadb-maxscale-2208-mariadb-monitor.md#ssh_port)
      * [rebuild\_port](mariadb-maxscale-2208-mariadb-monitor.md#rebuild_port)
    * [sudoers.d configuration](mariadb-maxscale-2208-mariadb-monitor.md#sudoersd-configuration)
  * [ColumnStore commands](mariadb-maxscale-2208-mariadb-monitor.md#columnstore-commands)
    * [Get status](mariadb-maxscale-2208-mariadb-monitor.md#get-status)
    * [Add or remove node](mariadb-maxscale-2208-mariadb-monitor.md#add-or-remove-node)
    * [Start and stop cluster](mariadb-maxscale-2208-mariadb-monitor.md#start-and-stop-cluster)
    * [Set read-only or readwrite](mariadb-maxscale-2208-mariadb-monitor.md#set-read-only-or-readwrite)
    * [Settings](mariadb-maxscale-2208-mariadb-monitor.md#settings_1)
      * [cs\_admin\_port](mariadb-maxscale-2208-mariadb-monitor.md#cs_admin_port)
      * [cs\_admin\_api\_key](mariadb-maxscale-2208-mariadb-monitor.md#cs_admin_api_key)
      * [cs\_admin\_base\_path](mariadb-maxscale-2208-mariadb-monitor.md#cs_admin_base_path)
  * [Other commands](mariadb-maxscale-2208-mariadb-monitor.md#other-commands)
    * [fetch-cmd-result](mariadb-maxscale-2208-mariadb-monitor.md#fetch-cmd-result)
    * [cancel-cmd](mariadb-maxscale-2208-mariadb-monitor.md#cancel-cmd)
  * [Troubleshooting](mariadb-maxscale-2208-mariadb-monitor.md#troubleshooting)
    * [Failover/switchover fails](mariadb-maxscale-2208-mariadb-monitor.md#failoverswitchover-fails)
    * [Slave detection shows external masters](mariadb-maxscale-2208-mariadb-monitor.md#slave-detection-shows-external-masters)
  * [Using the MariaDB Monitor With Binlogrouter](mariadb-maxscale-2208-mariadb-monitor.md#using-the-mariadb-monitor-with-binlogrouter)

### Overview

MariaDB Monitor monitors a Master-Slave replication cluster. It probes the\
state of the backends and assigns server roles such as master and slave, which\
are used by the routers when deciding where to route a query. It can also modify\
the replication cluster by performing failover, switchover and rejoin. Backend\
server versions older than MariaDB/MySQL 5.5 are not supported. Failover and\
other similar operations require MariaDB 10.0.2 or later.

Up until MariaDB MaxScale 2.2.0, this monitor was called _MySQL Monitor_.

### Required Grants

The monitor user requires the following grant:

```
CREATE USER 'maxscale'@'maxscalehost' IDENTIFIED BY 'maxscale-password';
GRANT REPLICATION CLIENT ON *.* TO 'maxscale'@'maxscalehost';
```

In MariaDB Server versions 10.5.0 to 10.5.8, the monitor user instead requires\
REPLICATION SLAVE ADMIN:

```
GRANT REPLICATION SLAVE ADMIN ON *.* TO 'maxscale'@'maxscalehost';
```

In MariaDB Server 10.5.9 and later, REPLICA MONITOR is required:

```
GRANT REPLICA MONITOR ON *.* TO 'maxscale'@'maxscalehost';
```

If the monitor needs to query server disk space (i.e. `disk_space_threshold` is\
set), then the FILE-grant is required with MariaDB Server versions 10.4.7,\
10.3.17, 10.2.26 and 10.1.41 and later.

```
GRANT FILE ON *.* TO 'maxscale'@'maxscalehost';
```

MariaDB Server 10.5.2 introduces CONNECTION ADMIN. This is recommended since it\
allows the monitor to log in even if server connection limit has been reached.

```
GRANT CONNECTION ADMIN ON *.* TO 'maxscale'@'maxscalehost';
```

#### Cluster Manipulation Grants

If [cluster manipulation operations](mariadb-maxscale-2208-mariadb-monitor.md#cluster-manipulation-operations) are used,\
the following additional grants are required:

```
GRANT SUPER, RELOAD, PROCESS, SHOW DATABASES, EVENT ON *.* TO 'maxscale'@'maxscalehost';
GRANT SELECT ON mysql.user TO 'maxscale'@'maxscalehost';
```

As of MariaDB Server 11.0.1, the SUPER-privilege no longer contains several of\
its former sub-privileges. These must be given separately.

```
GRANT RELOAD, PROCESS, SHOW DATABASES, EVENT, SET USER, READ_ONLY ADMIN ON *.* TO 'maxscale'@'maxscalehost';
GRANT REPLICATION SLAVE ADMIN, BINLOG ADMIN, CONNECTION ADMIN ON *.* TO 'maxscale'@'maxscalehost';
GRANT SELECT ON mysql.user TO 'maxscale'@'maxscalehost';
```

If a separate replication user is defined (with `replication_user` and`replication_password`), it requires the following grant:

```
CREATE USER 'replication'@'replicationhost' IDENTIFIED BY 'replication-password';
GRANT REPLICATION SLAVE ON *.* TO 'replication'@'replicationhost';
```

### Master selection

Only one backend can be master at any given time. A master must be running\
(successfully connected to by the monitor) and its _read\_only_-setting must be\
off. A master may not be replicating from another server in the monitored\
cluster unless the master is part of a multimaster group. Master selection\
prefers to select the server with the most slaves, possibly in multiple\
replication layers. Only slaves reachable by a chain of running relays or\
directly connected to the master count. When multiple servers are tied for\
master status, the server which appears earlier in the `servers`-setting of the\
monitor is selected.

Servers in a cyclical replication topology (multimaster group) are interpreted\
as having all the servers in the group as slaves. Even from a multimaster group\
only one server is selected as the overall master.

After a master has been selected, the monitor prefers to stick with the choice\
even if other potential masters with more slave servers are available. Only if\
the current master is clearly unsuitable does the monitor try to select another\
master. An existing master turns invalid if:

1. It is unwritable (read\_only is on).
2. It has been down for more than failcount monitor passes and has no running\
   slaves. Running slaves behind a downed relay count. A slave in this context is\
   any server with at least a partially running replication connection (either\
   io or sql thread is running). The slave servers must also be down for more than\
   failcount monitor passes to allow new master selection.
3. It did not previously replicate from another server in the cluster but it\
   is now replicating.
4. It was previously part of a multimaster group but is no longer, or the\
   multimaster group is replicating from a server not in the group.

Cases 1 and 2 cover the situations in which the DBA, an external script or even\
another MaxScale has modified the cluster such that the old master can no longer\
act as master. Cases 3 and 4 are less severe. In these cases the topology has\
changed significantly and the master should be re-selected, although the old\
master may still be the best choice.

The master change described above is different from failover and switchover\
described in section[Failover, switchover and auto-rejoin](mariadb-maxscale-2208-mariadb-monitor.md#failover,-switchover-and-auto-rejoin).\
A master change only modifies the server roles inside MaxScale but does not\
modify the cluster other than changing the targets of read and write queries.\
Failover and switchover perform a master change on their own.

As a general rule, it's best to avoid situations where the cluster has multiple\
standalone servers, separate master-slave pairs or separate multimaster groups.\
Due to master invalidation rule 2, a standalone master can easily lose the\
master status to another valid master if it goes down. The new master probably\
does not have the same data as the previous one. Non-standalone masters are less\
vulnerable, as a single running slave or multimaster group member will keep the\
master valid even when down.

### Configuration

A minimal configuration for a monitor requires a set of servers for monitoring\
and a username and a password to connect to these servers.

```
[MyMonitor]
type=monitor
module=mariadbmon
servers=server1,server2,server3
user=myuser
password=mypwd
```

From MaxScale 2.2.1 onwards, the module name is `mariadbmon` instead of`mysqlmon`. The old name can still be used.

The grants required by `user` depend on which monitor features are used. A full\
list of the grants can be found in the [Required Grants](mariadb-maxscale-2208-mariadb-monitor.md#required-grants)\
section.

### Common Monitor Parameters

For a list of optional parameters that all monitors support, read the[Monitor Common](mariadb-maxscale-2208-common-monitor-parameters.md) document.

### MariaDB Monitor optional parameters

These are optional parameters specific to the MariaDB Monitor. Failover,\
switchover and rejoin-specific parameters are listed in their own[section](mariadb-maxscale-2208-mariadb-monitor.md#cluster-manipulation-operations). Rebuild-related parameters are\
described in the [Rebuild server-section](mariadb-maxscale-2208-mariadb-monitor.md#rebuild-server). ColumnStore\
parameters are described in the [ColumnStore commands-section](mariadb-maxscale-2208-mariadb-monitor.md#settings).

#### `assume_unique_hostnames`

* Type: [boolean](https://mariadb.com/kb/en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#booleans)
* Mandatory: No
* Dynamic: Yes
* Default: `true`

When active, the monitor assumes that server hostnames and\
ports are consistent between the server definitions in the MaxScale\
configuration file and the "SHOW ALL SLAVES STATUS" outputs of the servers\
themselves. Specifically, the monitor assumes that if server A is replicating\
from server B, then A must have a slave connection with `Master_Host` and`Master_Port` equal to B's address and port in the configuration file. If this\
is not the case, e.g. an IP is used in the server while a hostname is given in\
the file, the monitor may misinterpret the topology. In MaxScale 2.4.1, the\
monitor attempts name resolution on the addresses if a simple string comparison\
does not find a match. Using exact matching addresses is, however, more\
reliable.

This setting must be ON to use any cluster operation features such as failover\
or switchover, because MaxScale uses the addresses and ports in the\
configuration file when issuing "CHANGE MASTER TO"-commands.

If the network configuration is such that the addresses MaxScale uses to connect\
to backends are different from the ones the servers use to connect to each\
other, `assume_unique_hostnames` should be set to OFF. In this mode, MaxScale\
uses server id:s it queries from the servers and the `Master_Server_Id` fields\
of the slave connections to deduce which server is replicating from which. This\
is not perfect though, since MaxScale doesn't know the id:s of servers it has\
never connected to (e.g. server has been down since MaxScale was started). Also,\
the `Master_Server_Id`-field may have an incorrect value if the slave connection\
has not been established. MaxScale will only trust the value if the monitor has\
seen the slave connection IO thread connected at least once. If this is not the\
case, the slave connection is ignored.

#### `master_conditions`

* Type: [enum\_mask](https://mariadb.com/kb/en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#enumerations)
* Mandatory: No
* Dynamic: Yes
* Values: `none`, `connecting_slave`, `connected_slave`, `running_slave`, `primary_monitor_master`
* Default: `primary_monitor_master`

Designate additional conditions fo&#x72;_&#x4D;aster_-status, i.e qualified for read and write queries.

Normally, if a suitable master candidate server is found as described in[Master selection](mariadb-maxscale-2208-mariadb-monitor.md#master-selection), MaxScale designates it _Master_._master\_conditions_ sets additional conditions for a master server. This\
setting is an enum\_mask, allowing multiple conditions to be set simultaneously.\
Conditions 2, 3 and 4 refer to slave servers. If combined, a single slave must\
fulfill all of the given conditions for the master to be viable.

If the master candidate fails _master\_conditions_ but fulfill&#x73;_&#x73;lave\_conditions_, it may be designated _Slave_ instead.

The available conditions are:

1. none : No additional conditions
2. connecting\_slave : At least one immediate slave (not behind relay) is\
   attempting to replicate or is replicating from the master (Slave\_IO\_Running is\
   'Yes' or 'Connecting', Slave\_SQL\_Running is 'Yes'). A slave with incorrect\
   replication credentials does not count. If the slave is currently down, results\
   from the last successful monitor tick are used.
3. connected\_slave : Same as above, with the difference that the replication\
   connection must be up (Slave\_IO\_Running is 'Yes'). If the slave is currently\
   down, results from the last successful monitor tick are used.
4. running\_slave : Same as connecting\_slave, with the addition that the\
   slave must also be Running.
5. primary\_monitor\_master : If this MaxScale is[cooperating](mariadb-maxscale-2208-mariadb-monitor.md#cooperative-monitoring) with another MaxScale and this is the\
   secondary MaxScale, require that the candidate master is selected also by the\
   primary MaxScale.

The default value of this setting is`master_requirements=primary_monitor_master` to ensure that both monitors use\
the same master server when cooperating.

For example, to require that the master must have a slave which is both\
connected and running, set

```
master_conditions=connected_slave,running_slave
```

#### `slave_conditions`

* Type: [enum\_mask](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#enumerations)
* Mandatory: No
* Dynamic: Yes
* Values: `none`, `linked_master`, `running_master`, `writable_master`, `primary_monitor_master`
* Default: `none`

Designate additional conditions for _Slave_-status,\
i.e qualified for read queries.

Normally, a server is _Slave_ if it is at least attempting to replicate from the\
master candidate or a relay (Slave\_IO\_Running is 'Yes' or 'Connecting',\
Slave\_SQL\_Running is 'Yes', valid replication credentials). The master candidate\
does not necessarily need to be writable, e.g. if it fails it&#x73;_&#x6D;aster\_conditions_. _slave\_conditions_ sets additional conditions for a slave\
server. This setting is an enum\_mask, allowing multiple conditions to be set\
simultaneously.

The available conditions are:

1. none : No additional conditions. This is the default value.
2. linked\_master : The slave must be connected to the master (Slave\_IO\_Running\
   and Slave\_SQL\_Running are 'Yes') and the master must be Running. The same\
   applies to any relays between the slave and the master.
3. running\_master : The master must be running. Relays may be down.
4. writable\_master : The master must be writable, i.e. labeled Master.
5. primary\_monitor\_master : If this MaxScale is[cooperating](mariadb-maxscale-2208-mariadb-monitor.md#cooperative-monitoring) with another MaxScale and this is the\
   secondary MaxScale, require that the candidate master is selected also by the\
   primary MaxScale.

For example, to require that the master server of the cluster must be running\
and writable for any servers to have _Slave_-status, set

```
slave_conditions=running_master,writable_master
```

#### `failcount`

* Type: number
* Mandatory: No
* Dynamic: Yes
* Default: `5`

Number of consecutive monitor passes a master server must be down before it is\
considered failed. If automatic failover is enabled (`auto_failover=true`), it\
may be performed at this time. A value of 0 or 1 enables immediate failover.

If automatic failover is not possible, the monitor will try to\
search for another server to fulfill the master role. See section[Master selection](mariadb-maxscale-2208-mariadb-monitor.md#master-selection)\
for more details. Changing the master may break replication as queries could be\
routed to a server without previous events. To prevent this, avoid having\
multiple valid master servers in the cluster.

The worst-case delay between the master failure and the start of the failover\
can be estimated by summing up the timeout values and `monitor_interval` and\
multiplying that by `failcount`:

```
(monitor_interval + backend_connect_timeout) * failcount
```

#### `enforce_writable_master`

* Type: [boolean](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#booleans)
* Mandatory: No
* Dynamic: Yes
* Default: `false`

If set to ON, the monitor attempts to\
disable the _read\_only_-flag on the master when seen. The flag is\
checked every monitor tick. The monitor user requires the SUPER-privilege for\
this feature to work.

Typically, the master server should never be in read-only-mode. Such a situation\
may arise due to misconfiguration or accident, or perhaps if MaxScale crashed\
during switchover.

When this feature is enabled, setting the master manually to _read\_only_ will no\
longer cause the monitor to search for another master. The master will instead\
for a moment lose its \[Master]-status (no writes), until the monitor again\
enables writes on the master. When starting from scratch, the monitor still\
prefers to select a writable server as master if possible.

#### `enforce_read_only_slaves`

* Type: [boolean](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#booleans)
* Mandatory: No
* Dynamic: Yes
* Default: `false`

If set to ON, the monitor attempts to\
enable the _read\_only_-flag on any writable slave server. The flag is checked\
every monitor tick. The monitor user requires the SUPER-privilege\
(or READ\_ONLY ADMIN) for this\
feature to work. While the _read\_only_-flag is ON, only users with the\
SUPER-privilege (or READ\_ONLY ADMIN) can write to the backend server. If\
temporary write access is required, this feature should be disabled before\
attempting to disable _read\_only_ manually. Otherwise, the monitor will quickly\
re-enable it.

_read\_only_ won't be enabled on the master server, even if it has\
lost \[Master]-status due to [master\_conditions](mariadb-maxscale-2208-mariadb-monitor.md#master_conditions) and is\
marked \[Slave].

#### `enforce_read_only_servers`

* Type: [boolean](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#booleans)
* Mandatory: No
* Dynamic: Yes
* Default: `false`

Works similar to[enforce\_read\_only\_slaves](mariadb-maxscale-2208-mariadb-monitor.md#enforce_read_only_slaves) except will se&#x74;_&#x72;ead\_only_ on any writable server that is not the primary and not in\
maintenance (a superset of the servers altered by _enforce\_read\_only\_slaves_).

The monitor user requires the SUPER-privilege\
(or READ\_ONLY ADMIN) for this feature to work. If the cluster has no valid\
primary or primary candidate, _read\_only_ is not set on any server as it is\
unclear which servers should be altered.

#### `maintenance_on_low_disk_space`

* Type: [boolean](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#booleans)
* Mandatory: No
* Dynamic: Yes
* Default: `true`

If a running server that is not the master\
or a relay master is out of disk space the server is set to maintenance mode.\
Such servers are not used for router sessions and are ignored when performing a\
failover or other cluster modification operation. See the general monitor\
parameters [disk\_space\_threshold](mariadb-maxscale-2208-common-monitor-parameters.md#disk_space_threshold) and[disk\_space\_check\_interval](mariadb-maxscale-2208-common-monitor-parameters.md#disk_space_check_interval)\
on how to enable disk space monitoring.

Once a server has been put to maintenance mode, the disk space situation\
of that server is no longer updated. The server will not be taken out of\
maintenance mode even if more disk space becomes available. The maintenance\
flag must be removed manually:

```
maxctrl clear server server2 Maint
```

#### `cooperative_monitoring_locks`

* Type: [enum](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#enumerations)
* Mandatory: No
* Dynamic: Yes
* Values: `none`, `majority_of_all`, `majority_of_running`
* Default: `none`

Using this setting is recommended when multiple MaxScales are monitoring the\
same backend cluster. When enabled, the monitor attempts to acquire exclusive\
locks on the backend servers. The monitor considers itself the primary monitor\
if it has a majority of locks. The majority can be either over all configured\
servers or just over running servers. See[Cooperative monitoring](mariadb-maxscale-2208-mariadb-monitor.md#cooperative-monitoring)\
for more details on how this feature works and which value to use.

Allowed values:

1. `none` Default value, no locking.
2. `majority_of_all` Primary monitor requires a majority of locks, even counting\
   servers which are \[Down].
3. `majority_of_running` Primary monitor requires a majority of locks over\
   \[Running] servers.

This setting is separate from the global MaxScale setting _passive_. I&#x66;_&#x70;assive_ is set to `true`, cluster operations are disabled even if monitor has\
acquired the locks. Generally, it's best not to mix cooperative monitoring wit&#x68;_&#x70;assive_. Either set `passive=false` or do not set it at all.

#### `script_max_replication_lag`

* Type: number
* Mandatory: No
* Dynamic: Yes
* Default: `-1`

Defines a replication lag limit in seconds for\
launching the monitor script configured in the _script_-parameter. If the\
replication lag of a server goes above this limit, the script is ran with the\
$EVENT-placeholder replaced by "rlag\_above". If the lag goes back below the\
limit, the script is ran again with replacement "rlag\_below".

Negative values disable this feature. For more information on monitor scripts,\
see [general monitor documentation](https://mariadb.com/kb/en/node:mariadb-maxscale-2208-common-monitor-parameters#script).

### Cluster manipulation operations

Starting with MaxScale 2.2.1, MariaDB Monitor supports replication cluster\
modification. The operations implemented are:

* _failover_, which replaces a failed master with a slave
* _switchover_, which swaps a running master with a slave
* _async-switchover_, which schedules a switchover and returns
* _rejoin_, which directs servers to replicate from the master
* _reset-replication_ (added in MaxScale 2.3.0), which deletes binary logs and\
  resets gtid:s

See [operation details](mariadb-maxscale-2208-mariadb-monitor.md#operation-details) for more information on the\
implementation of the commands.

The cluster operations require that the monitor user (`user`) has the following\
privileges:

* SUPER, to modify slave connections, set globals such as read\_only and kill\
  connections from other super-users
* REPLICATION CLIENT (REPLICATION SLAVE ADMIN in MariaDB Server 10.5), to list\
  slave connections
* RELOAD, to flush binary logs
* PROCESS, to check if the event\_scheduler process is running
* SHOW DATABASES and EVENT, to list and modify server events
* SELECT on mysql.user, to see which users have SUPER

A list of the grants can be found in the [Required Grants](mariadb-maxscale-2208-mariadb-monitor.md#required-grants)\
section.

The privilege system was changed in MariaDB Server 10.5. The effects of this on\
the MaxScale monitor user are minor, as the SUPER-privilege contains many of the\
required privileges and is still required to kill connections from other\
super-users.

In MariaDB Server 11.0.1 and later, SUPER no longer contains all the required\
grants. The monitor requires:

* READ\_ONLY ADMIN, to set read\_only
* REPLICA MONITOR and REPLICATION SLAVE ADMIN, to view and manage replication\
  connections
* RELOAD, to flush binary logs
* PROCESS, to check if the event\_scheduler process is running
* SHOW DATABASES, EVENT and SET USER, to list and modify server events
* BINLOG ADMIN, to delete binary logs (during reset-replication)
* CONNECTION ADMIN, to kill connections
* SELECT on mysql.user, to see which users have SUPER

In addition, the monitor needs to know which username and password a\
slave should use when starting replication. These are given in`replication_user` and `replication_password`.

The user can define files with SQL statements which are executed on any server\
being demoted or promoted by cluster manipulation commands. See the sections on`promotion_sql_file` and `demotion_sql_file` for more information.

The monitor can manipulate scheduled server events when promoting or demoting a\
server. See the section on `handle_events` for more information.

All cluster operations can be activated manually through MaxCtrl. See\
section [Manual activation](mariadb-maxscale-2208-mariadb-monitor.md#manual-activation) for more details.

See [Limitations and requirements](mariadb-maxscale-2208-mariadb-monitor.md#limitations-and-requirements) for\
information on possible issues with failover and switchover.

#### Operation details

**Failover** replaces a failed master with a running slave. It does the\
following:

1. Select the most up-to-date slave of the old master to be the new master. The\
   selection criteria is as follows in descending priority:
2. gtid\_IO\_pos (latest event in relay log)
3. gtid\_current\_pos (most processed events)
4. log\_slave\_updates is on
5. disk space is not low
6. If the new master has unprocessed relay log items, cancel and try again\
   later.
7. Prepare the new master:
8. Remove the slave connection the new master used to replicate from the\
   old master.
9. Disable the read\_only-flag.
10. Enable scheduled server events (if event handling is on). Only events\
    that were enabled on the old master are enabled.
11. Run the commands in `promotion_sql_file`.
12. Start replication from external master if one existed.
13. Redirect all other slaves to replicate from the new master:
14. STOP SLAVE
15. CHANGE MASTER TO
16. START SLAVE
17. Check that all slaves are replicating.

Failover is considered successful if steps 1 to 3 succeed, as the cluster then\
has at least a valid master server.

**Switchover** swaps a running master with a running slave. It does the\
following:

1. Prepare the old master for demotion:
2. Stop any external replication.
3. Kill connections from super-users since read\_only does not affect\
   them.
4. Enable the read\_only-flag to stop writes.
5. Disable scheduled server events (if event handling is on).
6. Run the commands in `demotion_sql_file`.
7. Flush the binary log (FLUSH LOGS) so that all events are on disk.
8. Wait for the new master to catch up with the old master.
9. Promote new master and redirect slaves as in failover steps 3 and 4. Also\
   redirect the demoted old master.
10. Check that all slaves are replicating.

Similar to failover, switchover is considered successful if the new master was\
successfully promoted.

**Rejoin** joins a standalone server to the cluster or redirects a slave\
replicating from a server other than the master. A standalone server is joined\
by:

1. Run the commands in `demotion_sql_file`.
2. Enable the read\_only-flag.
3. Disable scheduled server events (if event handling is on).
4. Start replication: CHANGE MASTER TO and START SLAVE.

A server which is replicating from the wrong master is redirected simply with\
STOP SLAVE, RESET SLAVE, CHANGE MASTER TO and START SLAVE commands.

**Reset-replication** (added in MaxScale 2.3.0) deletes binary logs and resets\
gtid:s. This destructive command is meant for situations where the gtid:s in the\
cluster are out of sync while the actual data is known to be in sync. The\
operation proceeds as follows:

1. Reset gtid:s and delete binary logs on all servers:
2. Stop (STOP SLAVE) and delete (RESET SLAVE ALL) all slave connections.
3. Enable the read\_only-flag.
4. Disable scheduled server events (if event handling is on).
5. Delete binary logs (RESET MASTER).
6. Set the sequence number of gtid\_slave\_pos to zero. This also affects\
   gtid\_current\_pos.
7. Prepare new master:
8. Disable the read\_only-flag.
9. Enable scheduled server events (if event handling is on). Events are\
   only enabled if the cluster had a master server when starting the\
   reset-replication operation. Only events that were enabled on the previous\
   master are enabled on the new.
10. Direct other servers to replicate from the new master as in the other\
    operations.

#### Manual activation

Cluster operations can be activated manually through the REST API or MaxCtrl.\
The commands are only performed when MaxScale is in active mode. The commands\
generally match their automatic versions. The exception is _rejoin_, in which\
the manual command allows rejoining even when the joining server has empty\
gtid:s. This rule allows the user to force a rejoin on a server without binary\
logs.

All commands require the monitor instance name as the first parameter. Failover\
selects the new master server automatically and does not require additional\
parameters. Rejoin requires the name of the joining server as second parameter.\
Replication reset accepts the name of the new master server as second parameter.\
If not given, the current master is selected.

Switchover takes one to three parameters. If only the monitor name is given,\
switchover will autoselect both the slave to promote and the current master as\
the server to be demoted. If two parameters are given, the second parameter is\
interpreted as the slave to promote. If three parameters are given, the third\
parameter is interpreted as the current master. The user-given current master is\
compared to the master server currently deduced by the monitor and if the two\
are unequal, an error is given.

Example commands are below:

```
call command mariadbmon failover MyMonitor
call command mariadbmon rejoin MyMonitor OldMasterServ
call command mariadbmon reset-replication MyMonitor
call command mariadbmon reset-replication MyMonitor NewMasterServ
call command mariadbmon switchover MyMonitor
call command mariadbmon switchover MyMonitor NewMasterServ
call command mariadbmon switchover MyMonitor NewMasterServ OldMasterServ
```

The commands follow the standard module command syntax. All require the monitor\
configuration name (MyMonitor) as the first parameter. For switchover, the\
last two parameters define the server to promote (NewMasterServ) and the server\
to demote (OldMasterServ). For rejoin, the server to join (OldMasterServ) is\
required. Replication reset requires the server to promote (NewMasterServ).

It is safe to perform manual operations even with automatic failover, switchover\
or rejoin enabled since automatic operations cannot happen simultaneously\
with manual ones.

When a cluster modification is initiated via the REST-API, the URL path is of the\
form:

```
/v1/maxscale/modules/mariadbmon/<operation>?<monitor-instance>&<server-param1>&<server-param2>
```

* `<operation>` is the name of the command: failover, switchover, rejoin\
  or reset-replication.
* `<monitor-instance>` is the monitor section name from the MaxScale\
  configuration file.
* `<server-param1>` and `<server-param2>` are server parameters as described\
  above for MaxCtrl. Only switchover accepts both, failover doesn't need any\
  and both rejoin and reset-replication accept one.

Given a MaxScale configuration file like

```
[Cluster1]
type=monitor
module=mariadbmon
servers=server1, server2, server3, server 4
...
```

with the assumption that `server2` is the current master, then the URL\
path for making `server4` the new master would be:

```
/v1/maxscale/modules/mariadbmon/switchover?Cluster1&server4&server2
```

Example REST-API paths for other commands are listed below.

```
/v1/maxscale/modules/mariadbmon/failover?Cluster1
/v1/maxscale/modules/mariadbmon/rejoin?Cluster1&server3
/v1/maxscale/modules/mariadbmon/reset-replication?Cluster1&server3
```

**Queued switchover**

Most cluster modification commands wait until the operation either succeeds or\
fails. _async-switchover_ is an exception, as it returns immediately. Otherwis&#x65;_&#x61;sync-switchover_ works identical to a normal _switchover_ command. Use the\
module command _fetch-cmd-result_ to view the result of the queued command._fetch-cmd-result_ returns the status or result of the latest manual command,\
whether queued or not.

```
maxctrl call command mariadbmon async-switchover Cluster1
OK
maxctrl call command mariadbmon fetch-cmd-result Cluster1
{
    "links": {
        "self": "http://localhost:8989/v1/maxscale/modules/mariadbmon/fetch-cmd-result"
    },
    "meta": "switchover completed successfully."
}
```

#### Automatic activation

Failover can activate automatically if `auto_failover` is on. The activation\
begins when the master has been down at least `failcount` monitor iterations.\
Before modifying the cluster, the monitor checks that all prerequisites for the\
failover are fulfilled. If the cluster does not seem ready, an error is printed\
and the cluster is rechecked during the next monitor iteration.

Switchover can also activate automatically with the`switchover_on_low_disk_space`-setting. The operation begins if the master\
server is low on disk space but otherwise the operating logic is quite similar\
to automatic failover.

Rejoin stands for starting replication on a standalone server or redirecting a\
slave replicating from the wrong master (any server that is not the cluster\
master). The rejoined servers are directed to replicate from the current cluster\
master server, forcing the replication topology to a 1-master-N-slaves\
configuration.

A server is categorized as standalone if the server has no slave connections,\
not even stopped ones. A server is replicating from the wrong master if the\
slave IO thread is connected but the master server id seen by the slave does not\
match the cluster master id. Alternatively, the IO thread may be stopped or\
connecting but the master server host or port information differs from the\
cluster master info. These criteria mean that a STOP SLAVE does not yet set a\
slave as standalone.

With `auto_rejoin` active, the monitor will try to rejoin any servers matching\
the above requirements. Rejoin does not obey `failcount` and will attempt to\
rejoin any valid servers immediately. When activating rejoin manually, the\
user-designated server must fulfill the same requirements.

#### Limitations and requirements

Switchover and failover are meant for simple topologies (one master and\
several slaves). Using these commands with complicated topologies\
(multiple masters, relays, circular replication) may give unpredictable results\
and should be tested before use on a production system.

The server cluster is assumed to be well-behaving with no significant\
replication lag (within `failover_timeout`/`switchover_timeout`) and all\
commands that modify the cluster (such as "STOP SLAVE", "CHANGE MASTER",\
"START SLAVE") complete in a few seconds (faster than `backend_read_timeout`\
and `backend_write_timeout`).

The backends must all use GTID-based replication, and the domain id should not\
change during a switchover or failover. Slave servers should not have extra\
local events so that GTIDs are compatible across the cluster.

Failover cannot be performed if MaxScale was started only after the master\
server went down. This is because MaxScale needs reliable information on the\
gtid domain of the cluster and the replication topology in general to properly\
select the new master. `enforce_simple_topology=1` relaxes this requirement.

Failover may lose events. If a master goes down before sending new events to at\
least one slave, those events are lost when a new master is chosen. If the old\
master comes back online, the other servers have likely moved on with a\
diverging history and the old master can no longer join the replication cluster.

To reduce the chance of losing data, use[semisynchronous replication](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/replication-cluster-multi-master/standard-replication/semisynchronous-replication).\
In semisynchronous mode, the master waits for a slave to receive an event before\
returning an acknowledgement to the client. This does not yet guarantee a clean\
failover. If the master fails after preparing a transaction but before receiving\
slave acknowledgement, it will still commit the prepared transaction as part of\
its crash recovery. If the slaves never saw this transaction, the\
old master has diverged from the cluster. See[Configuring the Master Wait Point](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/replication-cluster-multi-master/standard-replication/semisynchronous-replication)\
for more information. This situation is much less likely in MariaDB Server\
10.6.2 and later, as the improved crash recovery logic will delete such\
transactions.

Even a controlled shutdown of the master may lose events. The server does not by\
default wait for all data to be replicated to the slaves when shutting down and\
instead simply closes all connections. Before shutting down the master with the\
intention of having a slave promoted, run _switchover_ first to ensure that all\
data is replicated. For more information on server shutdown, see[Binary Log Dump Threads and the Shutdown Process](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/replication-cluster-multi-master/standard-replication/replication-threads).

Switchover requires that the cluster is "frozen" for the duration of the\
operation. This means that no data modifying statements such as INSERT or UPDATE\
are executed and the GTID position of the master server is stable. When\
switchover begins, the monitor sets the global _read\_only_ flag on the old\
master backend to stop any updates. _read\_only_ does not affect users with the\
SUPER-privilege so any such user can issue writes during a switchover. These\
writes have a high chance of breaking replication, because the write may not be\
replicated to all slaves before they switch to the new master. To prevent this,\
any users who commonly do updates should NOT have the SUPER-privilege. For even\
more security, the only SUPER-user session during a switchover should be the\
MaxScale monitor user. This also applies to users running scheduled server\
events. Although the monitor by default disables events on the master, an\
event may already be executing. If the event definer has SUPER-privilege, the\
event can write to the database even through _read\_only_.

When mixing rejoin with failover/switchover, the backends should hav&#x65;_&#x6C;og\_slave\_updates_ on. The rejoining server is likely lagging behind the rest\
of the cluster. If the current cluster master does not have binary logs from the\
moment the rejoining server lost connection, the rejoining server cannot\
continue replication. This is an issue if the master has changed and\
the new master does not have _log\_slave\_updates_ on.

If an automatic cluster operation such as auto-failover or auto-rejoin fails,\
all cluster modifying operations are disabled for `failcount` monitor iterations,\
after which the operation may be retried. Similar logic applies if the cluster is\
unsuitable for such operations, e.g. replication is not using GTID.

#### External master support

The monitor detects if a server in the cluster is replicating from an external\
master (a server that is not monitored by the monitor). If the replicating\
server is the cluster master server, then the cluster itself is considered to\
have an external master.

If a failover/switchover happens, the new master server is set to replicate from\
the cluster external master server. The username and password for the replication\
are defined in `replication_user` and `replication_password`. The address and\
port used are the ones shown by `SHOW ALL SLAVES STATUS` on the old cluster\
master server. In the case of switchover, the old master also stops replicating\
from the external server to preserve the topology.

After failover the new master is replicating from the external master. If the\
failed old master comes back online, it is also replicating from the external\
server. To normalize the situation, either have _auto\_rejoin_ on or manually\
execute a rejoin. This will redirect the old master to the current cluster\
master.

#### Configuration parameters

**`auto_failover`**

* Type: [boolean](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#booleans)
* Mandatory: No
* Dynamic: Yes
* Default: `false`

Enable automatic master failover. When automatic failover is enabled, MaxScale\
will elect a new master server for the cluster if the old master goes down. A\
server is assumed _Down_ if it cannot be connected to, even if this is caused by\
incorrect credentials. Failover triggers if the master stays down for[failcount](mariadb-maxscale-2208-mariadb-monitor.md#failcount) monitor intervals. Failover will not take place if\
MaxScale is set [passive](https://mariadb.com/kb/en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#passive).

As failover alters replication, it requires more privileges than normal\
monitoring. See [here](mariadb-maxscale-2208-mariadb-monitor.md#cluster-manipulation-grants) for a list of grants.

Failover is designed to be used with simple master-slave topologies. More\
complicated topologies, such as multilayered or circular replication, are not\
guaranteed to always work correctly. Test before using failover with such\
setups.

**`auto_rejoin`**

* Type: [boolean](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#booleans)
* Mandatory: No
* Dynamic: Yes
* Default: `false`

Enable automatic joining of servers to the cluster. When enabled, MaxScale will\
attempt to direct servers to replicate from the current cluster master if they\
are not currently doing so. Replication will be started on any standalone\
servers. Servers that are replicating from another server will be redirected.\
This effectively enforces a 1-master-N-slaves topology. The current master\
itself is not redirected, so it can continue to replicate from an external\
master. Rejoin is also not performed on any server that is replicating from\
multiple sources, as this indicates a complicated topology (this rule is\
overridden by [enforce\_simple\_topology](mariadb-maxscale-2208-mariadb-monitor.md#enforce_simple_topology)).

This feature is often paired with [auto\_failover](mariadb-maxscale-2208-mariadb-monitor.md#auto_failover) to redirect\
the former master when it comes back online. Sometimes this kind of rejoin will\
fail as the old master may have transactions that were never replicated to the\
current one. See [limitations](mariadb-maxscale-2208-mariadb-monitor.md#limitations-and-requirements) for more\
information.

As an example, consider the following series of events:

1. Slave A goes down
2. Master goes down and a failover is performed, promoting Slave B
3. Slave A comes back
4. Old master comes back

Slave A is still trying to replicate from the downed master, since it wasn't\
online during failover. If _auto\_rejoin_ is on, Slave A will quickly be\
redirected to Slave B, the current master. The old master will also rejoin the\
cluster if possible.

**`switchover_on_low_disk_space`**

* Type: [boolean](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#booleans)
* Mandatory: No
* Dynamic: Yes
* Default: `false`

If enabled, the monitor will attempt to\
switchover a master server low on disk space with a slave. The switch is only\
done if a slave without disk space issues is found. If`maintenance_on_low_disk_space` is also enabled, the old master (now a slave)\
will be put to maintenance during the next monitor iteration.

For this parameter to have any effect, `disk_space_threshold` must be specified\
for the [server](https://mariadb.com/kb/en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#disk_space_threshold)\
or the [monitor](mariadb-maxscale-2208-common-monitor-parameters.md#disk_space_threshold).\
Also, [disk\_space\_check\_interval](mariadb-maxscale-2208-common-monitor-parameters.md#disk_space_check_interval)\
must be defined for the monitor.

```
switchover_on_low_disk_space=true
```

**`enforce_simple_topology`**

* Type: [boolean](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#booleans)
* Mandatory: No
* Dynamic: Yes
* Default: `false`

This setting tells the monitor to assume that the servers should be arranged in a\
1-master-N-slaves topology and the monitor should try to keep it that way. If`enforce_simple_topology` is enabled, the settings `assume_unique_hostnames`,`auto_failover` and `auto_rejoin` are also activated regardless of their individual\
settings.

By default, mariadbmon will not rejoin servers with more than one replication\
stream configured into the cluster. Starting with MaxScale 6.2.0, when`enforce_simple_topology` is enabled, all servers will be rejoined into the\
cluster and any extra replication sources will be removed. This is done to make\
automated failover with multi-source external replication possible.

This setting also allows the monitor to perform a failover to a cluster where the master\
server has not been seen \[Running]. This is usually the case when the master goes down\
before MaxScale is started. When using this feature, the monitor will guess the GTID\
domain id of the master from the slaves. For reliable results, the GTID:s of the cluster\
should be simple.

```
enforce_simple_topology=true
```

**`replication_user` and `replication_password`**

* Type: string
* Mandatory: No
* Dynamic: Yes
* Default: None

The username and password of the replication user. These are given as the values\
for `MASTER_USER` and `MASTER_PASSWORD` whenever a `CHANGE MASTER TO` command is\
executed.

Both `replication_user` and `replication_password` parameters must be defined if\
a custom replication user is used. If neither of the parameters is defined, the`CHANGE MASTER TO`-command will use the monitor credentials for the replication\
user.

The credentials used for replication must have the `REPLICATION SLAVE`\
privilege.

`replication_password` uses the same encryption scheme as other password\
parameters. If password encryption is in use, `replication_password` must be\
encrypted with the same key to avoid erroneous decryption.

**`replication_master_ssl`**

* Type: [boolean](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#booleans)
* Mandatory: No
* Dynamic: Yes
* Default: `false`

If set to ON, any `CHANGE MASTER TO`-command generated will set `MASTER_SSL=1` to enable\
encryption for the replication stream. This setting should only be enabled if the backend\
servers are configured for ssl. This typically means setting _ssl\_ca_, _ssl\_cert_ an&#x64;_&#x73;sl\_key_ in the server configuration file. Additionally, credentials for the replication\
user should require an encrypted connection (`e.g. ALTER USER repl@'%' REQUIRE SSL;`).

If the setting is left OFF, `MASTER_SSL` is not set at all, which will preserve existing\
settings when redirecting a slave connection.

**`failover_timeout` and `switchover_timeout`**

* Type: [duration](https://mariadb.com/kb/en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#durations)
* Mandatory: No
* Dynamic: Yes
* Default: `90s`

Time limit for failover and switchover operations. The default\
values are 90 seconds for both. `switchover_timeout` is also used as the time\
limit for a rejoin operation. Rejoin should rarely time out, since it is a\
faster operation than switchover.

The timeouts are specified as documented[here](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#durations). If no explicit unit\
is provided, the value is interpreted as seconds in MaxScale 2.4. In subsequent\
versions a value without a unit may be rejected. Note that since the granularity\
of the timeouts is seconds, a timeout specified in milliseconds will be rejected,\
even if the duration is longer than a second.

If no successful failover/switchover takes place within the configured time\
period, a message is logged and automatic failover is disabled. This prevents\
further automatic modifications to the misbehaving cluster.

**`verify_master_failure`**

* Type: [boolean](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#booleans)
* Mandatory: No
* Dynamic: Yes
* Default: `true`

Enable additional master failure verification for automatic failover.`verify_master_failure` enables this feature and[master\_failure\_timeout](mariadb-maxscale-2208-mariadb-monitor.md#master_failure_timeout) defines the timeout.

Failure verification is performed by checking whether the slave servers are\
still connected to the master and receiving events. An event is either a change\
in the _Gtid\_IO\_Pos_-field of the `SHOW SLAVE STATUS` output or a heartbeat\
event. Effectively, if a slave has received an event within`master_failure_timeout` duration, the master is not considered down when\
deciding whether to failover, even if MaxScale cannot connect to the master.`master_failure_timeout` should be longer than the `Slave_heartbeat_period` of\
the slave connection to be effective.

If every slave loses its connection to the master (_Slave\_IO\_Running_ is not\
"Yes"), master failure is considered verified regardless of timeout. This allows\
faster failover when the master properly disconnects.

For automatic failover to activate, the `failcount` requirement must also be\
met.

**`master_failure_timeout`**

* Type: [duration](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#durations)
* Mandatory: No
* Dynamic: Yes
* Default: `10s`

The master failure timeout is specified as documented[here](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#durations). If no explicit unit\
is provided, the value is interpreted as seconds in MaxScale 2.4. In subsequent\
versions a value without a unit may be rejected. Note that since the granularity\
of the timeout is seconds, a timeout specified in milliseconds will be rejected,\
even if the duration is longer than a second.

**`servers_no_promotion`**

* Type: string
* Mandatory: No
* Dynamic: Yes
* Default: None

This is a comma-separated list of server names that will not be chosen for\
master promotion during a failover or autoselected for switchover. This does not\
affect switchover if the user selects the server to promote. Using this setting\
can disrupt new master selection for failover such that an non-optimal server is\
chosen. At worst, this will cause replication to break. Alternatively, failover\
may fail if all valid promotion candidates are in the exclusion list.

```
servers_no_promotion=backup_dc_server1,backup_dc_server2
```

**`promotion_sql_file` and `demotion_sql_file`**

* Type: string
* Mandatory: No
* Dynamic: Yes
* Default: None

These optional settings are paths to text files with SQL statements in them.\
During promotion or demotion, the contents are read line-by-line and executed on\
the backend. Use these settings to execute custom statements on the servers to\
complement the built-in operations.

Empty lines or lines starting with '#' are ignored. Any results returned by the\
statements are ignored. All statements must succeed for the failover, switchover\
or rejoin to continue. The monitor user may require additional privileges and\
grants for the custom commands to succeed.

When promoting a slave to master during switchover or failover, the`promotion_sql_file` is read and executed on the new master server after its\
read-only flag is disabled. The commands are ran _before_ starting replication\
from an external master if any.

`demotion_sql_file` is ran on an old master during demotion to slave, before the\
old master starts replicating from the new master. The file is also ran before\
rejoining a standalone server to the cluster, as the standalone server is\
typically a former master server. When redirecting a slave replicating from a\
wrong master, the sql-file is not executed.

Since the queries in the files are ran during operations which modify\
replication topology, care is required. If `promotion_sql_file` contains data\
modification (DML) queries, the new master server may not be able to\
successfully replicate from an external master. `demotion_sql_file` should never\
contain DML queries, as these may not replicate to the slave servers before\
slave threads are stopped, breaking replication.

```
promotion_sql_file=/home/root/scripts/promotion.sql
demotion_sql_file=/home/root/scripts/demotion.sql
```

**`handle_events`**

* Type: [boolean](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#booleans)
* Mandatory: No
* Dynamic: Yes
* Default: `true`

If enabled, the monitor continuously queries the\
servers for enabled scheduled events and uses this information when performing\
cluster operations, enabling and disabling events as appropriate.

When a server is being demoted, any events with "ENABLED" status are set to\
"SLAVESIDE\_DISABLED". When a server is being promoted to master, events that are either\
"SLAVESIDE\_DISABLED" or "DISABLED" are set to "ENABLED" if the same event was also enabled\
on the old master server last time it was successfully queried. Events are considered\
identical if they have the same schema and name. When a standalone server is rejoined to\
the cluster, its events are also disabled since it is now a slave.

The monitor does not check whether the same events were disabled and enabled during a\
switchover or failover/rejoin. All events that meet the criteria above are altered.

The monitor does not enable or disable the event scheduler itself. For the\
events to run on the new master server, the scheduler should be enabled by the\
admin. Enabling it in the server configuration file is recommended.

Events running at high frequency may cause replication to break in a failover\
scenario. If an old master which was failed over restarts, its event scheduler\
will be on if set in the server configuration file. Its events will also\
remember their "ENABLED"-status and run when scheduled. This may happen before\
the monitor rejoins the server and disables the events. This should only be an\
issue for events running more often than the monitor interval or events that run\
immediately after the server has restarted.

### Cooperative monitoring

As of MaxScale 2.5, MariaDB-Monitor supports cooperative monitoring. This means\
that multiple monitors (typically in different MaxScale instances) can monitor\
the same backend server cluster and only one will be the primary monitor. Only\
the primary monitor may perform _switchover_, _failover_ or _rejoin_ operations.\
The primary also decides which server is the master. Cooperative monitoring is\
enabled with the[cooperative\_monitoring\_locks](mariadb-maxscale-2208-mariadb-monitor.md#cooperative_monitoring_locks)-setting.\
Even with this setting, only one monitor per server per MaxScale is allowed.\
This limitation can be circumvented by defining multiple copies of a server in\
the configuration file.

Cooperative monitoring uses[server locks](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements-and-structure/sql-statements/built-in-functions/secondary-functions/miscellaneous-functions/get_lock)\
for coordinating between monitors. When cooperating, the monitor regularly\
checks the status of a lock named _maxscale\_mariadbmonitor_ on every server and\
acquires it if free. If the monitor acquires a majority of locks, it is the\
primary. If a monitor cannot claim majority locks, it is a secondary monitor.

The primary monitor of a cluster also acquires the loc&#x6B;_&#x6D;axscale\_mariadbmonitor\_master_ on the master server. Secondary monitors check\
which server this lock is taken on and only accept that server as the master.\
This arrangement is required so that multiple monitors can agree on which server\
is the master regardless of replication topology. If a secondary monitor does\
not see the master-lock taken, then it won't mark any server as \[Master],\
causing writes to fail.

The lock-setting defines how many locks are required for primary status. Setting`cooperative_monitoring_locks=majority_of_all` means that the primary monitor\
needs _n\_servers/2 + 1_ (rounded down) locks. For example, a cluster of three\
servers needs two locks for majority, a cluster of four needs three, and a\
cluster of five needs three.\
This scheme is resistant against split-brain situations in the sense\
that multiple monitors cannot be primary simultaneously. However, a split may\
cause both monitors to consider themselves secondary, in which case a master\
server won't be detected.

Even without a network split, `cooperative_monitoring_locks=majority_of_all`\
will lead to neither monitor claiming lock majority once too many servers go\
down. This scenario is depicted in the image below. Only two out of four servers\
are running when three are needed for majority. Although both MaxScales see both\
running servers, neither is certain they have majority and the cluster stays in\
read-only mode. If the primary server is down, no failover is performed either.

![](../../../../.gitbook/assets/mariadb-corporation/MaxScale/22.08.17/Documentation/Monitors/images/coop_lock_no_majority.png.png)

Setting `cooperative_monitoring_locks=majority_of_running` changes the wa&#x79;_&#x6E;\_servers_ is calculated. Instead of using the total number of servers, only\
servers currently \[Running] are considered. This scheme adapts to multiple\
servers going down, ensuring that claiming lock majority is always possible.\
However, it can lead to multiple monitors claiming primary status in a\
split-brain situation. As an example, consider a cluster with servers 1 to 4\
with MaxScales A and B, as in the image below. MaxScale A can connect to\
servers 1 and 2 (and claim their locks) but not to servers 3 and 4 due to\
a network split. MaxScale A thus assumes servers 3 and 4 are down. MaxScale B\
does the opposite, claiming servers 3 and 4 and assuming 1 and 2 are down.\
Both MaxScales claim two locks out of two available and assume that they have\
lock majority. Both MaxScales may then promote their own primaries and route\
writes to different servers.

![](../../../../.gitbook/assets/mariadb-corporation/MaxScale/22.08.17/Documentation/Monitors/images/coop_lock_split_brain.png.png)

The recommended strategy depends on which failure scenario is more likely and/or\
more destructive. If it's unlikely that multiple servers are ever down\
simultaneously, then _majority\_of\_all_ is likely the safer choice. On the other\
hand, if split-brain is unlikely but multiple servers may be down\
simultaneously, then _majority\_of\_running_ would keep the cluster operational.

To check if a monitor is primary, fetch monitor diagnostics with `maxctrl show monitors` or the REST API. The boolean field **primary** indicates whether the\
monitor has lock majority on the cluster. If cooperative monitoring is disabled,\
the field value is _null_. Lock information for individual servers is listed in\
the server-specific field **lock\_held**. Again, _null_ indicates that locks are\
not in use or the lock status is unknown.

If a MaxScale instance tries to acquire the locks but fails to get majority\
(perhaps another MaxScale was acquiring locks simultaneously) it will release\
any acquired locks and try again after a random number of monitor ticks. This\
prevents multiple MaxScales from fighting over the locks continuously as one\
MaxScale will eventually wait less time than the others. Conflict probability\
can be further decreased by configuring each monitor with a differen&#x74;_&#x6D;onitor\_interval_.

The flowchart below illustrates the lock handling logic.

![](../../../../.gitbook/assets/mariadb-corporation/MaxScale/22.08.17/Documentation/Monitors/images/coop_lock_flowchart.svg.svg)

#### Releasing locks

Monitor cooperation depends on the server locks. The locks are\
connection-specific. The owning connection can manually release a lock, allowing\
another connection to claim it. Also, if the owning connection closes, the\
MariaDB Server process releases the lock. How quickly a lost connection is\
detected affects how quickly the primary monitor status moves from one monitor\
and MaxScale to another.

If the primary MaxScale or its monitor is stopped normally, the monitor\
connections are properly closed, releasing the locks. This allows the secondary\
MaxScale to quickly claim the locks. However, if the primary simply vanishes\
(broken network), the connection may just look idle. In this case, the\
MariaDB Server may take a long time before it considers the monitor connection\
lost. This time ultimately depends on TCP keepalive settings on the machines\
running MariaDB Server.

On MariaDB Server 10.3.3 and later, the TCP keepalive settings can be configured\
for just the server process. See[Server System Variables](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/replication-cluster-multi-master/optimization-and-tuning/system-variables/server-system-variables#tcp_keepalive_interval)\
for information on settings _tcp\_keepalive\_interval_, _tcp\_keepalive\_probes_ an&#x64;_&#x74;cp\_keepalive\_time_. These settings can also be set on the operating system\
level, as described[here](https://www.tldp.org/HOWTO/TCP-Keepalive-HOWTO/usingkeepalive.html).

As of MaxScale 6.4.16, 22.08.13, 23.02.10, 23.08.6 and 24.02.2, configuring\
TCP keepalive is no longer necessary as monitor sets the session _wait\_timeout_\
variable when acquiring a lock. This causes the MariaDB Server to close the\
monitor connection if the connection appears idle for too long. The value o&#x66;_&#x77;ait\_timeout_ used depends on the monitor interval and connection timeout\
settings, and is logged at MaxScale startup.

A monitor can also be ordered to manually release its locks via the module\
command _release-locks_. This is useful for manually changing the primary\
monitor. After running the release-command, the monitor will not attempt to\
reacquire the locks for one minute, even if it wasn't the primary monitor to\
begin with. This command can cause the cluster to become temporarily unusable by\
MaxScale. Only use it when there is another monitor ready to claim the locks.

```
maxctrl call command mariadbmon release-locks MyMonitor1
```

### Rebuild server

The rebuild server-feature replaces the contents of a database server with the\
contents of another server. The source server is effectively cloned and all data\
on the target server is lost. This is useful when a slave server has diverged\
from the master server, or when adding a new server to the cluster. The\
MariaDB Server configuration files are not affected.

MariaDB-Monitor can perform this operation by running[mariadb-backup](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/backing-up-and-restoring-databases/mariadb-backup/) on both the source and\
target servers. To do this, MaxScale needs to have ssh-access on the machines.\
Also, the following tools need to be installed on the source and target\
machines:

1. mariadb-backup. Backups and restores MariaDB Server contents. Installed e.g.\
   with `yum install MariaDB-backup`.
2. pigz. Compresses and decompresses the backup stream. Installed e.g. with`yum install pigz`.
3. socat. Streams data from one machine to another. Is likely already\
   installed. If not, can be installed e.g. with `yum install socat`.

The _ssh\_user_ and _ssh\_keyfile_-settings define the SSH credentials MaxScale\
uses to access the servers. MaxScale must be able to run commands with _sudo_ on\
both the source and target servers. mariadb-backup, on the other hand, needs to\
authenticate to the MariaDB Server being copied from. For this, MaxScale uses\
the monitor user. The monitor user may thus require additional privileges. See[mariadb-backup documentation](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/backing-up-and-restoring-databases/mariadb-backup/mariadb-backup-overview#authentication-and-privileges)\
for more details.

When launched, the rebuild operation proceeds as below. If any step fails, the\
operation is stopped and the target server will be left in an unspecified state.

1. Log in to both servers with ssh and check that the tools listed above are\
   present (e.g. `mariadb-backup -v` should succeed).
2. Check that the port used for transferring the backup is free on the source\
   server. If not, kill the process holding it. This requires running lsof and\
   kill.
3. Test the connection by streaming a short message from the source host to the\
   target.
4. Launch mariadb-backup on the source machine, compress the stream and listen\
   for an incoming connection. This is performed with a command like`mariadb-backup --backup --safe-slave-backup --stream=xbstream | pigz -c | socat - TCP-LISTEN:<port>`.
5. Stop MariaDB-server on the target machine and delete all contents of the data\
   directory /var/lib/mysql.
6. On the target machine, connect to the source machine, read the backup stream,\
   decompress it and write to the data directory. This is performed with a command\
   like `socat -u TCP:<host>:<port> STDOUT | pigz -dc | mbstream -x`. This step can\
   take a long time if there is much data to transfer.
7. Check that the data directory is not empty.
8. Prepare the backup on the target server with a command like`mariadb-backup --use-memory=1G --prepare`. This step can also take some time if\
   the source server performed writes during data transfer.
9. On the target server, change ownership of datadir contents to the\
   mysql-user and start MariaDB-server.
10. Read gtid from the data directory. Have the target server start replicating\
    from the master.

The rebuild-operation is a monitor module command and is best launched with\
MaxCtrl. The command takes three arguments: the monitor name, target server name\
and source server name. The source server can be left out, in which case it is\
autoselected. When autoselecting, the monitor prefers to pick an up-to-date\
slave server. Due to the `--safe-slave-backup`-option, the slave will stop\
replicating until the backup data has been transferred.

```
maxctrl call command mariadbmon async-rebuild-server MariaDB-Monitor MyServer3 MyServer2
```

The operation does not launch if the target server is already replicating or if\
the source server is not a master or slave.

Steps 6 and 8 can take a long time depending on the size of the database and if\
writes are ongoing. During these steps, the monitor will continue monitoring the\
cluster normally. After each monitor tick the monitor checks if the\
rebuild-operation can proceed. No other monitor operations, either manual or\
automatic, can run until the rebuild completes.

#### Settings

**`ssh_user`**

* Type: string
* Mandatory: No
* Dynamic: Yes
* Default: None

Ssh username. Used when logging in to backend servers to run commands.

**`ssh_keyfile`**

* Type: path
* Mandatory: No
* Dynamic: Yes
* Default: None

Path to file with an ssh private key. Used when logging in to backend servers to\
run commands.

**`ssh_check_host_key`**

* Type: [boolean](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#booleans)
* Mandatory: No
* Dynamic: Yes
* Default: `true`

Boolean, default: true. When logging in to backends, require that the server is\
already listed in the known\_hosts-file of the user running MaxScale.

**`ssh_timeout`**

* Type: [duration](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/#durations)
* Mandatory: No
* Dynamic: Yes
* Default: `10s`

The rebuild operation consists of multiple ssh\
commands. Most of the commands are assumed to complete quickly. If these\
commands take more than _ssh\_timeout_ to complete, the operation fails. Adjust\
this setting if rebuild fails due to ssh commands timing out. This setting does\
not affect steps 5 and 6, as these are assumed to take significant time.

**`ssh_port`**

* Type: number
* Mandatory: No
* Dynamic: Yes
* Default: `22`

SSH port. Used for running remote commands on servers.

**`rebuild_port`**

* Type: number
* Mandatory: No
* Dynamic: Yes
* Default: `4444`

The port which the source server listens on for a\
connection. The port must not be blocked by a firewall or listened on by any\
other program. If another process is listening on the port when rebuild is\
starting, MaxScale will attempt to kill the process.

#### sudoers.d configuration

If giving MaxScale general sudo-access is out of the question, MaxScale must be\
allowed to run the specific commands required by the rebuild-operation. This can\
be achieved by creating a file with the commands in the`/etc/sudoers.d`-directory. In the example below, the user _johnny_ is given the\
power to run commands as root. The contents of the file may need to be tweaked\
due to changes in install locations.

```
johnny ALL= NOPASSWD: /bin/systemctl stop mariadb
johnny ALL= NOPASSWD: /bin/systemctl start mariadb
johnny ALL= NOPASSWD: /usr/sbin/lsof
johnny ALL= NOPASSWD: /bin/kill
johnny ALL= NOPASSWD: /usr/bin/mariadb-backup
johnny ALL= NOPASSWD: /bin/mbstream
johnny ALL= NOPASSWD: /bin/du
johnny ALL= NOPASSWD: /bin/rm -rf /var/lib/mysql/*
johnny ALL= NOPASSWD: /bin/chown -R mysql\:mysql /var/lib/mysql/*
johnny ALL= NOPASSWD: /bin/cat
```

### ColumnStore commands

Since MaxScale version 22.08, MariaDB Monitor can run ColumnStore administrative\
commands against a ColumnStore cluster. The commands interact with the\
ColumnStore REST-API present in recent ColumnStore versions and have been tested\
with MariaDB-Server 10.6 running the ColumnStore plugin version 6.2. None of the\
commands affect monitor configuration or replication topology. MariaDB Monitor\
simply relays the commands to the backend cluster.

MariaDB Monitor can fetch cluster status, add and remove nodes, start and stop\
the cluster, and set cluster read-only or readwrite. MaxScale only communicates\
with the first server in the `servers`-list.

Most of the commands are asynchronous, i.e. they do not wait for the operation\
to complete on the ColumnStore backend before returning to the command prompt.\
MariaDB Monitor itself, however, runs the command in the background and does not\
perform normal monitoring until the operation completes or fails. After an\
operation has started the user should use _fetch-cmd-result_ to check its\
status. The examples below show how to run the commands using MaxCtrl. If a\
command takes a timeout-parameter, the timeout can be given in seconds (s),\
minutes (m) or hours (h).

ColumnStore command settings are listed [here](mariadb-maxscale-2208-mariadb-monitor.md#settings). At least`cs_admin_api_key` must be set.

#### Get status

Fetch cluster status. Returns the result as is. Status fetching has an automatic\
timeout of ten seconds.

```
maxctrl call command mariadbmon cs-get-status <monitor-name>
maxctrl call command mariadbmon async-cs-get-status <monitor-name>
```

Examples:

```
maxctrl call command mariadbmon cs-get-status MyMonitor
{
    "mcs1": {
        "cluster_mode": "readwrite",
        "dbrm_mode": "master",
<snip>

maxctrl call command mariadbmon async-cs-get-status MyMonitor
OK
maxctrl call command mariadbmon fetch-cmd-result MyMonitor
{
    "mcs1": {
        "cluster_mode": "readwrite",
        "dbrm_mode": "master",
<snip>
```

#### Add or remove node

Add or remove a node to/from the ColumnStore cluster.

```
maxctrl call command mariadbmon async-cs-add-node <monitor-name> <node-host> <timeout>
maxctrl call command mariadbmon async-cs-remove-node <monitor-name> <node-host> <timeout>
```

`<node-host>` is the hostname or IP of the node being added or removed.

Examples:

```
maxctrl call command mariadbmon async-cs-add-node MyMonitor mcs3 1m
OK
maxctrl call command mariadbmon fetch-cmd-result MyMonitor
{
    "node_id": "mcs3",
    "timestamp": "2022-05-05 08:07:51.518268"
}
maxctrl call command mariadbmon async-cs-remove-node MyMonitor mcs3 1m
OK
maxctrl call command mariadbmon fetch-cmd-result MyMonitor
{
    "node_id": "mcs3",
    "timestamp": "2022-05-05 10:46:46.506947"
}
```

#### Start and stop cluster

```
maxctrl call command mariadbmon async-cs-start-cluster <monitor-name> <timeout>
maxctrl call command mariadbmon async-cs-stop-cluster <monitor-name> <timeout>
```

Examples:

```
maxctrl call command mariadbmon async-cs-start-cluster MyMonitor 1m
OK
maxctrl call command mariadbmon fetch-cmd-result MyMonitor
{
    "timestamp": "2022-05-05 09:41:57.140732"
}
maxctrl call command mariadbmon async-cs-stop-cluster MyMonitor 1m
OK
maxctrl call command mariadbmon fetch-cmd-result MyMonitor
{
    "mcs1": {
        "timestamp": "2022-05-05 09:45:33.779837"
    },
<snip>
```

#### Set read-only or readwrite

```
maxctrl call command mariadbmon async-cs-set-readonly <monitor-name> <timeout>
maxctrl call command mariadbmon async-cs-set-readwrite <monitor-name> <timeout>
```

Examples:

```
maxctrl call command mariadbmon async-cs-set-readonly MyMonitor 30s
OK
maxctrl call command mariadbmon fetch-cmd-result MyMonitor
{
    "cluster-mode": "readonly",
    "timestamp": "2022-05-05 09:49:18.365444"
}
maxctrl call command mariadbmon async-cs-set-readwrite MyMonitor 30s
OK
maxctrl call command mariadbmon fetch-cmd-result MyMonitor
{
    "cluster-mode": "readwrite",
    "timestamp": "2022-05-05 09:50:30.718972"
}
```

#### Settings

**`cs_admin_port`**

Numeric, default: 8640. The REST-API port on the ColumnStore nodes. All nodes\
are assumed to listen on the same port.

```
cs_admin_port=8641
```

**`cs_admin_api_key`**

String. The API-key MaxScale sends to the ColumnStore nodes when making a\
REST-API request. Should match the value configured on the ColumnStore nodes.

```
cs_admin_api_key=somekey123
```

**`cs_admin_base_path`**

String, default: _/cmapi/0.4.0_. Base path sent with the REST-API request.

### Other commands

#### `fetch-cmd-result`

Fetches the result of the last manual command. Requires monitor name as\
parameter. Most commands only return a generic success message or an error\
description. ColumnStore commands may return more data. Scheduling another\
command clears a stored result.

```
maxctrl call command mariadbmon fetch-cmd-result MariaDB-Monitor
"switchover completed successfully."
```

#### `cancel-cmd`

Cancels the latest operation, whether manual or automatic, if possible. Requires\
monitor name as parameter. A scheduled manual command is simply canceled\
before it can run. If a command is already running, it stops as soon as\
possible. The _cancel-cmd_ itself does not wait for a running operation to stop.\
Use _fetch-cmd-result_ or check the log to see if the operation has truly\
completed. Canceling is most useful for stopping a stalled rebuild operation.

```
maxctrl call command mariadbmon cancel-cmd MariaDB-Monitor
OK
```

### Troubleshooting

#### Failover/switchover fails

See the [Limitations and requirements-section](mariadb-maxscale-2208-mariadb-monitor.md#limitations_and_requirements).

Before performing failover or switchover, the monitor checks that\
prerequisites are fulfilled, printing any errors and warnings found. This should\
catch and explain most issues with failover or switchover not working.\
If the operations are attempted and still fail, then most likely one of\
the commands the monitor issued to a server failed or timed out. The log should\
explain which query failed.

A typical failure reason is that a command such as `STOP SLAVE` takes longer than the`backend_read_timeout` of the monitor, causing the connection to break. As of 2.3, the\
monitor will retry most such queries if the failure was caused by a timeout. The retrying\
continues until the total time for a failover or switchover has been spent. If the log\
shows warnings or errors about commands timing out, increasing the backend timeout\
settings of the monitor should help. Other settings to look at are `query_retries` and`query_retry_timeout`. These are general MaxScale settings described in the[Configuration guide](../../../../../en/maxscale-2208-getting-started-mariadb-maxscale-configuration-guide/). Setting`query_retries` to 2 is a reasonable first try.

If switchover causes the old master (now slave) to fail replication, then most\
likely a user or perhaps a scheduled event performed a write while monitor\
had set `read_only=1`. This is possible if the user performing the write has\
"SUPER" or "READ\_ONLY ADMIN" privileges. The switchover-operation tries to kick\
out SUPER-users but this is not certain to succeed. Remove these privileges\
from any users that regularly do writes to prevent them from interfering with\
switchover.

The server configuration files should have `log-slave-updates=1` to ensure that\
a newly promoted master has binary logs of previous events. This allows the new\
master to replicate past events to any lagging slaves.

To print out all queries sent to the servers, start MaxScale with`--debug=enable-statement-logging`. This setting prints all queries sent to the\
backends by monitors and authenticators. The printed queries may include\
usernames and passwords.

#### Slave detection shows external masters

If a slave is shown in _maxctrl_ as "Slave of External Server" instead of\
"Slave", the reason is likely that the "Master\_Host"-setting of the replication connection\
does not match the MaxScale server definition. As of 2.3.2, the MariaDB Monitor by default\
assumes that the slave connections (as shown by `SHOW ALL SLAVES STATUS`) use the exact\
same "Master\_Host" as used the MaxScale configuration file server definitions. This is\
controlled by the setting [assume\_unique\_hostnames](mariadb-maxscale-2208-mariadb-monitor.md#assume_unique_hostnames).

### Using the MariaDB Monitor With Binlogrouter

Since MaxScale 2.2 it's possible to detect a replication setup\
which includes Binlog Server: the required action is to add the\
binlog server to the list of servers only if _master\_id_ identity is set.

CC BY-SA / Gnu FDL
