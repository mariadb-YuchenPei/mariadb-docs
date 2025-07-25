# MariaDB MaxScale Plugin Development Guide

This document and the attached example code explain prospective plugin\
developers the MariaDB MaxScale plugin API and also present and explain some\
best practices and possible pitfalls in module development. We predict tha&#x74;_&#x66;ilters_ and _routers_ are the module types developers are most likely to work\
on, so the APIs of these two are discussed in detail.

* [MariaDB MaxScale plugin development guide](mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-plugin-development-guide.md#mariadb-maxscale-plugin-development-guide)
  * [Introduction](mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-plugin-development-guide.md#introduction)
  * [Module categories](mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-plugin-development-guide.md#module-categories)
  * [Common definitions and headers](mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-plugin-development-guide.md#common-definitions-and-headers)
    * [Module information container](mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-plugin-development-guide.md#module-information-container)
  * [Module API](mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-plugin-development-guide.md#module-api)
    * [Overview](mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-plugin-development-guide.md#overview)
    * [General module management](mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-plugin-development-guide.md#general-module-management)
    * [Protocol](mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-plugin-development-guide.md#protocol)
    * [Authenticator](mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-plugin-development-guide.md#authenticator)
    * [Filter and Router](mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-plugin-development-guide.md#filter-and-router)
    * [Monitor](mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-plugin-development-guide.md#monitor)
  * [Compiling, installing and running](mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-plugin-development-guide.md#compiling-installing-and-running)
    * [Hands-on example: RoundRobinRouter](mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-plugin-development-guide.md#hands-on-example-roundrobinrouter)
  * [Summary and conclusion](mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-plugin-development-guide.md#summary-and-conclusion)

### Introduction

MariaDB MaxScale is designed to be an extensible program. Much, if not most, of\
the actual processing is done by plugin modules. Plugins receive network data,\
process it and relay it to its destination. The MaxScale core loads plugins,\
manages client sessions and threads and, most importantly, offers a selection of\
functions for the plugins to call upon. This collection of functions is called\
the _MaxScale Public Interface_ or just **MPI** for short.

The plugin modules are shared libraries (.so-files) implementing a set of\
interface functions, the plugin API. Different plugin types have different APIs,\
although there are similarities. The MPI is a set of C and C++ header files,\
from which the module code includes the ones required. MariaDB MaxScale is\
written in C/C++ and the plugin API is in pure C. Although it is possible\
to write plugins in any language capable of exposing a C interface and\
dynamically binding to the core program, in this document we assume plugin\
modules are written in C++.

The _RoundRobinRouter_ is a practical example of a simple router plugin. The\
RoundRobinRouter is compiled, installed and ran in [section\
5.1](mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-plugin-development-guide.md#hands-on-example:-roundrobinrouter). The source for the router is located\
in the `examples`-folder.

### Module categories

This section lists all the module types and summarises their core tasks. The\
modules are listed in the order a client packet would typically travel through.\
For more information about a particular module type, see the corresponding\
folder in `MaxScale/Documentation/`, located in the main MariaDB MaxScale\
repository.

**Protocol** modules implement I/O between clients and MaxScale, and between\
MaxScale and backend servers. Protocol modules read and write to socket\
descriptors using raw I/O functions provided by the MPI, and implement\
protocol-specific I/O functions to be used through a common interface. The\
Protocol module API is defined in `protocol.h`. Currently, the only implemented\
database protocol is _MySQL_.

**Authenticator** modules retrieve user account information from the backend\
databases, store it and use it to authenticate connecting clients. MariaDB\
MaxScale includes authenticators for MySQL (normal and GSSApi). The\
authenticator API is defined in `authenticator.h`.

**Filter** modules process data from clients before routing. A data buffer may\
travel through multiple filters before arriving in a router. For a data buffer\
going from a backend to the client, the router receives it first and the\
filters receive it in reverse order. MaxScale includes a healthly selection of\
filters ranging from logging, overwriting query data and caching. The filter\
API is defined in `filter.h`.

**Router** modules route packets from the last filter in the filter chain to\
backends and reply data from backends to the last filter. The routing decisions\
may be based on a variety of conditions; typically packet contents and backend\
status are the most significant factors. Routers are often used for load\
balancing, dividing clients and even individual queries between backends.\
Routers use protocol functions to write to backends, making them somewhat\
protocol-agnostic. The router API is defined in `router.h`.

**Monitor** modules do not process data flowing through MariaDB MaxScale, but\
support the other modules in their operation by updating the status of the\
backend servers. Monitors are ran in their own threads to minimize\
interference to the worker threads. They periodically connect to all their\
assigned backends, query their status and write the results in global structs.\
The monitor API is defined in `monitor.h`.

### Common definitions and headers

Generally, most type definitions, macros and functions exposed by the MPI to be\
used by modules are prefixed with **MXS**. This should avoid name collisions\
in the case a module includes many symbols from the MPI.

Every compilation unit in a module should begin with `#define MXS_MODULE_NAME "<name>"`. This definition will be used by log macros for clarity, prepending`<name>` to every log message. Next, the module should`#include <maxscale/cppdefs.h>` (for C++) or `#include <maxscale/cdefs.h>` (for\
C). These headers contain compilation environment dependent definitions and\
global constants, and include some generally useful headers. Including one of\
them first in every source file enables later global redefinitions across all\
MaxScale modules. If your module is composed of multiple source files, the above\
should be placed to a common header file included in the beginning of the source\
files. The file with the module API definition should also include the header\
for the module type, e.g. `filter.h`.

Other common MPI header files required by most modules are listed in the table\
below.

| Header       | Contents                            |
| ------------ | ----------------------------------- |
| alloc.h      | Malloc, calloc etc. replacements    |
| buffer.h     | Packet buffer management            |
| config.h     | Configuration settings              |
| dcb.h        | I/O using descriptor control blocks |
| debug.h      | Debugging macros                    |
| modinfo.h    | Module information structure        |
| server.h     | Backend server information          |
| service.h    | Service definition                  |
| session.h    | Client session definition           |
| logmanager.h | Logging macros and functions        |

#### Module information container

A module must implement the `MXS_CREATE_MODULE()`-function, which returns a\
pointer to a `MXS_MODULE`-structure. This function is called by the module\
loader during program startup. `MXS_MODULE` (type defined in `modinfo.h`)\
contains function pointers to further module entrypoints, miscellaneous\
information about the module and the configuration parameters accepted by the\
module. This function must be exported without C++ name mangling, so in C++ code\
it should be defined `extern "C"`.

The information container describes the module in general and is constructed\
once during program excecution. A module may have multiple _instances_ with\
different values for configuration parameters. For example, a filter module can\
be used with two different configurations in different services (or even in the\
same service). In this case the loader uses the same module information\
container for both but creates two module instances.

The MariaDB MaxScale configuration file `maxscale.cnf` is parsed by the core.\
The core also checks that all the defined parameters are of the correct type for\
the module. For this, the `MXS_MODULE`-structure includes a list of parameters\
accepted by the module, defining parameter names, types and default values. In\
the actual module code, parameter values should be extracted using functions\
defined in `config.h`.

### Module API

#### Overview

This section explains some general concepts encountered when implementing a\
module API. For more detailed information, see the module specific subsection,\
header files or the doxygen documentation.

Modules with configuration data define an _INSTANCE_ object, which is created by\
the module code in a `createInstance`-function or equivalent. The instance\
creation function is called during MaxScale startup, usually when creating\
services. MaxScale core holds the module instance data in the`SERVICE`-structure (or other higher level construct) and gives it as a\
parameter when calling functions from the module in question. The instance\
structure should contain all non-client-specific information required by the\
functions of the module. The core does not know what the object contains (since\
it is defined by the module itself), nor will it modify the pointer or the\
referenced object in any way.

Modules dealing with client-specific data require a _SESSION_ object for every\
client. As with the instance data, the definition of the module session\
structure is up to the module writer and MaxScale treats it as an opaque type.\
Usually the session contains status indicators and any resources required by the\
client. MaxScale core has its own `MXS_SESSION` object, which tracks a variety\
of client related information. The `MXS_SESSION` is given as a parameter to\
module-specific session creation functions and is required for several typical\
operations such as connecting to backends.

Descriptor control blocks (`DCB`), are generalized I/O descriptor types. DCBs\
store the file descriptor, state, remote address, username, session, and other\
data. DCBs are created whenever a new socket is created. Typically this happens\
when a new client connects or MaxScale connects the client session to backend\
servers. The module writer should use DCB handling functions provided by the MPI\
to manage connections instead of calling general networking libraries. This\
ensures that I/O is handled asynchronously by epoll. In general, module code\
should avoid blocking I/O, _sleep_, _yield_ or other potentially costly\
operations, as the same thread is typically used for many client sessions.

Network data such as client queries and backend replies are held in a buffer\
container called `GWBUF`. Multiple GWBUFs can form a linked list with type\
information and properties in each GWBUF-node. Each node includes a pointer to a\
reference counted shared buffer (`SHARED_BUF`), which finally points to a slice\
of the actual data. In effect, multiple GWBUF-chains can share some data while\
keeping some parts private. This construction is meant to minimize the need for\
data copying and makes it easy to append more data to partially received data\
packets. Plugin writers should use the MPI to manipulate GWBUFs. For more\
information on the GWBUF, see [Filter and Router](mariadb-maxscale-2106-maxscale-2106-mariadb-maxscale-plugin-development-guide.md#filter-and-router).

#### General module management

```
int process_init()
void process_finish()
int thread_init()
void thread_finish()
```

These four functions are present in all `MXS_MODULE` structs and are not part of\
the API of any individual module type. `process_init` and `process_finish` are\
called by the module loader right after loading a module and just before\
MaxScale terminates, respectively. Usually, these can be set to null in`MXS_MODULE` unless the module needs some general initializations before\
creating any instances. `thread_init` and `thread_finish` are thread-specific\
equivalents.

```
void diagnostics(INSTANCE *instance, DCB *dcb)
```

A diagnostics printing routine is present in nearly all module types, although\
with varying signatures. This entrypoint should print various statistics and\
status information about the module instance `instance` in string form. The\
target of the printing is the given DCB, and printing should be implemented by\
calling `dcb_printf`.

#### Protocol

```
int32_t read(struct dcb *)
int32_t write(struct dcb *, GWBUF *)
int32_t write_ready(struct dcb *)
int32_t error(struct dcb *)
int32_t hangup(struct dcb *)
int32_t accept(struct dcb *)
int32_t connect(struct dcb*, struct server*, MXS_SESSION*)
int32_t close(struct dcb *)
int32_t listen(struct dcb *, char *)
int32_t auth(struct dcb*, struct server*, MXS_SESSION*, GWBUF*)
int32_t session(struct dcb *, void *)
char auth_default()
int32_t connlimit(struct dcb *, int limit)
```

Protocol modules are laborous to implement due to their low level nature. Each\
DCB maintains pointers to the correct protocol functions to be used with it,\
allowing the DCB to be used in a protocol-independent manner.

`read`, `write_ready`, `error` and `hangup` are _epoll_ handlers for their\
respective events. `write` implements writing and is usually called in a router\
module. `accept` is a listener socker handler. `connect` is used during session\
creation when connecting to backend servers. `listen` creates a listener socket.`close` closes a DCB created by `accept`, `connect` or `listen`.

In the ideal case modules other than the protocol modules themselves should not\
be protocol-specific. This is currently difficult to achieve, since many actions\
in the modules are dependent on protocol-speficic details. In the future,\
protocol modules may be expanded to implement a generic query parsing and\
information API, allowing filters and routers to be used with different SQL\
variants.

#### Authenticator

```
void* initialize(char **options)
void* create(void* instance)
int extract(struct dcb *, GWBUF *)
bool connectssl(struct dcb *)
int authenticate(struct dcb *)
void free(struct dcb *)
void destroy(void *)
int loadusers(struct servlistener *)
void diagnostic(struct dcb*, struct servlistener *)
int reauthenticate(struct dcb *, const char *user, uint8_t *token,
                   size_t token_len, uint8_t *scramble, size_t scramble_len,
                   uint8_t *output, size_t output_len);
```

Authenticators must communicate with the client or the backends and implement\
authentication. The authenticators can be divided to client and backend modules,\
although the two types are linked and must be used together. Authenticators are\
also dependent on the protocol modules.

#### Filter and Router

Filter and router APIs are nearly identical and are presented together. Since\
these are the modules most likely to be implemented by plugin developers, their\
APIs are discussed in more detail.

```
INSTANCE* createInstance(SERVICE* service, char** options)
void destroyInstance(INSTANCE* instance)
```

`createInstance` should read the `options` and initialize an instance object for\
use with `service`. Often, simply saving the configuration values to fields is\
enough. `destroyInstance` is called when the service using the module is\
deallocated. It should free any resources claimed by the instance. All sessions\
created by this instance should be closed before calling the destructor.

```
SESSION* newSession(INSTANCE* instance, MXS_SESSION* mxs_session, SERVICE* service)
void closeSession(INSTANCE* instance, SESSION* session)
void freeSession(INSTANCE* instance, SESSION* session)
```

These functions manage sessions. `newSession` should allocate a router or filter\
session attached to the client session represented by `mxs_session`. MaxScale\
will pass the returned pointer to all the API entrypoints that process user data\
for the particular client. `closeSession` should close connections the session\
has opened and release any resources specific to the served client. Th&#x65;_&#x53;ESSION_ structure allocated in `newSession` should not be deallocated by`closeSession` but in `freeSession`. These two are called in succession\
by the core.

```
int routeQuery(INSTANCE *instance, SESSION session, GWBUF* queue) void
clientReply(INSTANCE* instance, SESSION session, GWBUF* queue, const mxs::ReplyRoute& down, const mxs::Reply& reply)
uint64_t getCapabilities(INSTANCE* instance)
```

`routeQuery` is called for client requests which should be routed to backends,\
and `clientReply` for backend reply packets which should be routed to the\
client. For some modules, MaxScale itself is the backend. For filters, these can\
be NULL, in which case the filter will be skipped for that packet type.

`routeQuery` is often the most complicated function in a router, as it\
implements the routing logic. It typically considers the client request `queue`,\
the router settings in `instance` and the session state in `session` when making\
a routing decision. For filters aswell, `routeQuery` typically implements the\
main logic, although the routing target is constant. For router modules,`routeQuery` should send data forward with `dcb->func.write()`. Filters should\
directly call `routeQuery` for the next filter or router in the chain.

`clientReply` processes data flowing from backend back to client. For routers,\
this function is often much simpler than `routeQuery`, since there is only one\
client to route to. Depending on the router, some packets may not be routed to\
the client. For example, if a client query was routed to multiple backends,\
MaxScale will receive multiple replies while the client only expects one.\
Routers should pass the reply packet to the last filter in the chain (reversed\
order) using the function `mxs_route_reply`. Filters should call the`clientReply` of the previous filter in the chain. There is no need for filters\
to worry about being the first filter in the chain, as this is handled\
transparently by the session creation routine.

Application data is not always received in complete packets from the network\
stack. How partial packets are handled by the receiving protocol module depends\
on the attached filters and the router, communicated by their`getCapabilities`-functions. `getCapabilities` should return a bitfield\
resulting from ORring the individual capabilities. `routing.hh` lists the allowed\
capability flags.

If a router or filter sets no capabilities, `routeQuery` or `clientReply` may be\
called to route partial packets. If the routing logic does not require any\
information on the contents of the packets or even tracking the number of\
packets, this may be fine. For many cases though, receiving a data packet in a\
complete GWBUF chain or in one contiguos GWBUF is required. The former can be\
requested by `getCapabilities` returning _RCAP\_TYPE\_STMT_, the latter b&#x79;_&#x52;CAP\_TYPE\_CONTIGUOUS_. Separate settings exist for queries and replies. For\
replies, an additional value, _RCAP\_TYPE\_RESULTSET\_OUTPUT_ is defined. This\
requests the protocol module to gather partial results into one result set.\
Enforcing complete packets will delay processing, since the protocol module will\
have to wait for the entire data packet to arrive before sending it down the\
processing chain.

```
bool handleError(INSTANCE* instance, SESSION* session, GWBUF* errmsgbuf, mxs::Endpoint* problem, const mxs::Reply& reply);
```

This router-only entrypoint is called if a network error occurs in one of the\
backend server connections in use by the session. When the entrypoint is called,\
the router should try to continue the session if possible. If the session can\
continue operating normally, the function should return `true`. If the router\
cannot continue routing queries, for example due to a complete cluster outage,\
the function should return `false` which will cause the whole session to close.

#### Monitor

```
MONITOR* startMonitor(MXS_MONITOR *monitor, const MXS_CONFIG_PARAMETER *params)
void stopMonitor(MXS_MONITOR *monitor)
void diagnostics(DCB *, const MXS_MONITOR *)
```

Monitor modules typically run a repeated monitor routine with a used defined\
interval. The `MXS_MONITOR` is a standard monitor definition used for all\
monitors and contains a void pointer for storing module specific data.`startMonitor` should create a new thread for itself using functions in the MPI\
and have it regularly run a monitor loop. In the beginning of every monitor\
loop, the monitor should lock the `SERVER`-structures of its servers. This\
prevents any administrative action from interfering with the monitor during its\
pass.

### Compiling, installing and running

The requirements for compiling a module are:_The public headers (MPI)_ A compatible compiler, typically GCC

* Libraries required by the public headers

Some of the public header files themselves include headers from other libraries.\
These libraries need to be installed and it may be required to point out their\
location to gcc. Some of the more commonly required libraries are:

* _MySQL Connector-C_, used by the MySQL protocol module
* _pcre2 regular expressions_ (libpcre2-dev), used for example by the header`modutil.h`

After all dependencies are accounted for, the module should compile with a\
command similar to

```
gcc -I /usr/local/include/mariadb -shared -fPIC -g -o libmymodule.so mymodule.cpp
```

Large modules composed of several source files and using additional libraries\
may require a more complicated compilation scheme, but that is outside the scope\
of this document. The result of compiling a plugin should be a single shared\
library file.

The compiled .so-file needs to be copied to the MaxScale library folder, which\
is `/usr/local/lib/maxscale` by default. MaxScale expects the filename to be`lib<name>.so`, where `<name>` must match the module name given in the\
configuration file.

#### Hands-on example: RoundRobinRouter

In this example, the RoundRobinRouter is compiled, installed and tested. The\
software environment this section was written and tested is listed below. Any\
recent Linux setup should be applicaple.

* Linux Mint 18
* gcc 5.4.0, glibc 2.23
* MariaDB MaxScale 2.1.0 debug build (binaries in `usr/local/maxscale`, modules in`/usr/local/lib/maxscale`)
* MariaDB Connector-C 2.3.2 (installed to `/usr/local/lib/mariadb`, headers in`/usr/local/include/mariadb`)
* `roundrobinrouter.cpp` in the current directory
* MaxScale plugin development headers (in `usr/include/maxscale`)

**Step 1** Compile RoundRobinRouter with `$gcc -I /usr/local/include/mariadb -shared -fPIC -g -o libroundrobinrouter.so roundrobinrouter.cpp`.\
Assuming all headers were found, the shared library `libroundrobinrouter.so`\
is produced.

**Step 2** Copy the compiled module to the MaxScale module directory: `$sudo cp libroundrobinrouter.so /usr/local/lib/maxscale`.

**Step 3** Modify the MaxScale configuration file to use the RoundRobinRouter as\
a router. Example service and listener definitions are below. The _servers_\
and _write\_backend_-lines should be configured according to the actual backend\
configuration.

```
[RR-Service]
type=service
router=roundrobinrouter
servers=LocalMaster1,LocalSlave1,LocalSlave2
user=maxscale
password=maxscale
filters=MyLogFilter1
max_backends=10
write_backend=LocalMaster1
print_on_routing=true
dummy_setting=two

[RR-Listener]
type=listener
service=RR-Service
port=4009
```

**Step 4** Start MaxScale: `$ maxscale -d`. Output:

```
MariaDB Corporation MaxScale 2.1.0  Mon Feb 20 17:22:18 2017
------------------------------------------------------
Info : MaxScale will be run in the terminal process.
    See the log from the following log files :

Configuration file : /etc/maxscale.cnf
Log directory      : /var/log/maxscale
Data directory     : /var/lib/maxscale
Module directory   : /usr/local/lib/maxscale
Service cache      : /var/cache/maxscale
```

**Step 5** Test with a MySQL client. The RoundRobinRouter has been tested with both a command line and a GUI client. With `DEBUG_RRROUTER` defined and `print_on_routing` enabled, the `/var/log/maxscale/maxscale.log` file will report nearly every action taken by the router.

```
2017-02-21 10:37:23   notice : [RoundRobinRouter] Creating instance.
2017-02-21 10:37:23   notice : [RoundRobinRouter] Settings read:
2017-02-21 10:37:23   notice : [RoundRobinRouter] 'max_backends': 10
2017-02-21 10:37:23   notice : [RoundRobinRouter] 'write_backend': 0xf0ce70
2017-02-21 10:37:23   notice : [RoundRobinRouter] 'print_on_routing': 1
2017-02-21 10:37:23   notice : [RoundRobinRouter] 'dummy_setting': 2
.
.
.
2017-02-21 10:37:37   notice : [RoundRobinRouter] Session with 4 connections created.
2017-02-21 10:37:37   notice : [RoundRobinRouter] QUERY: SHOW VARIABLES WHERE Variable_name in ('max_allowed_packet', 'system_time_zone', 'time_zone', 'sql_mode')
2017-02-21 10:37:37   notice : [RoundRobinRouter] Routing statement of length 110u  to backend 'LocalMaster1'.
2017-02-21 10:37:37   notice : [RoundRobinRouter] Replied to client.
2017-02-21 10:37:37   notice : [RoundRobinRouter] QUERY: set session autocommit=1,sql_mode='NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES'
2017-02-21 10:37:37   notice : [RoundRobinRouter] Routing statement of length 103u to 4 backends.
2017-02-21 10:37:37   notice : [RoundRobinRouter] Replied to client.
2017-02-21 10:37:37   notice : [RoundRobinRouter] QUERY: SET @ApplicationName='DBeaver 3.8.5 - Main'
2017-02-21 10:37:37   notice : [RoundRobinRouter] Routing statement of length 48u to 4 backends.
2017-02-21 10:37:37   notice : [RoundRobinRouter] Replied to client.
2017-02-21 10:37:37   notice : [RoundRobinRouter] QUERY: select @@lower_case_table_names
2017-02-21 10:37:37   notice : [RoundRobinRouter] Routing statement of length 36u  to backend 'LocalSlave1'.
2017-02-21 10:37:37   notice : [RoundRobinRouter] Replied to client.
```

**Step 5** Connect with MaxCtrl, print diagnostics and call a custom command.

```
$ maxctrl
maxctrl show service RR-Service
┌─────────────────────┬────────────────────────────────────────────┐
│ Service             │ RR-Service                                 │
├─────────────────────┼────────────────────────────────────────────┤
│ Router              │ roundrobinrouter                           │
├─────────────────────┼────────────────────────────────────────────┤
│ State               │ Started                                    │
├─────────────────────┼────────────────────────────────────────────┤
│ Started At          │ Tue Apr 28 08:45:19 2020                   │
├─────────────────────┼────────────────────────────────────────────┤
│ Current Connections │ 0                                          │
├─────────────────────┼────────────────────────────────────────────┤
│ Total Connections   │ 0                                          │
├─────────────────────┼────────────────────────────────────────────┤
│ Max Connections     │ 0                                          │
├─────────────────────┼────────────────────────────────────────────┤
│ Cluster             │                                            │
├─────────────────────┼────────────────────────────────────────────┤
│ Servers             │ Server1                                    │
├─────────────────────┼────────────────────────────────────────────┤
│ Services            │                                            │
├─────────────────────┼────────────────────────────────────────────┤
│ Filters             │                                            │
├─────────────────────┼────────────────────────────────────────────┤
│ Parameters          │ {                                          │
│                     │     "router_options": null,                │
│                     │     "targets": null,                       │
│                     │     "user": "maxskysql",                   │
│                     │     "password": "*****",                   │
│                     │     "enable_root_user": false,             │
│                     │     "max_connections": 0,                  │
│                     │     "connection_timeout": 0,               │
│                     │     "net_write_timeout": 0,                │
│                     │     "auth_all_servers": false,             │
│                     │     "strip_db_esc": true,                  │
│                     │     "localhost_match_wildcard_host": true, │
│                     │     "version_string": null,                │
│                     │     "log_auth_warnings": true,             │
│                     │     "session_track_trx_state": false,      │
│                     │     "retain_last_statements": -1,          │
│                     │     "session_trace": false,                │
│                     │     "cluster": null,                       │
│                     │     "rank": "primary",                     │
│                     │     "connection_keepalive": 300,           │
│                     │     "connection_init_sql_file": null,      │
│                     │     "max_backends": 0,                     │
│                     │     "print_on_routing": false,             │
│                     │     "write_backend": null,                 │
│                     │     "dummy_setting": "the_answer"          │
│                     │ }                                          │
├─────────────────────┼────────────────────────────────────────────┤
│ Router Diagnostics  │ {                                          │
│                     │     "queries_ok": 0,                       │
│                     │     "queries_failed": 0,                   │
│                     │     "replies": 0                           │
│                     │ }                                          │
└─────────────────────┴────────────────────────────────────────────┘
maxctrl

MaxScale> call command roundrobinrouter test_command "one" 0
```

The result of the `test_command "one" 0` is printed to the terminal MaxScale is\
running in:

```
RoundRobinRouter wishes the Admin a good day.
The module got 2 arguments.
Argument 0: type 'string' value 'one'
Argument 1: type 'boolean' value 'false'
```

### Summary and conclusion

Plugins offer a way to extend MariaDB MaxScale whenever the standard modules are\
found insufficient. The plugins need only implement a set API, can be\
independently compiled and installation is simply a file copy with some\
configuration file modifications.

Out of the different plugin types, filters are the easiest to implement. They\
work independently and have few requirements. Protocol and authenticator modules\
require indepth knowledge of the database protocol they implement. Router module\
complexity depends on the routing logic requirements.

The provided RoundRobinRouter example code should serve as a valid starting\
point for both filters and routers. Studying the MaxScale Public Interface\
headers to get a general idea of what services the core provides for plugins,\
is also highly recommeded.

Lastly, MariaDB MaxScale is an open-source project, so code contributions can be\
accepted if they fulfill the[requirements](https://github.com/mariadb-corporation/MaxScale/wiki/Contributing).

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
