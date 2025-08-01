# Authentication Plugin - ed25519

MySQL has used SHA-1 based authentication since version 4.1. The authentication plugin is called [mysql\_native\_password](authentication-plugin-mysql_native_password.md). Over the years as computers became faster, new attacks on SHA-1 were being developed. Nowadays SHA-1 is no longer considered as secure as it was in 2001. That's why the `ed25519` authentication plugin was created.

The `ed25519` authentication plugin uses [Elliptic Curve Digital Signature Algorithm (ECDSA)](https://en.wikipedia.org/wiki/Elliptic_Curve_Digital_Signature_Algorithm) to securely store users' passwords and to authenticate users. The [ed25519](https://en.wikipedia.org/wiki/EdDSA#Ed25519) algorithm is the same one that is [used by OpenSSH](https://www.openssh.com/txt/release-6.5). It is based on the elliptic curve and code created by [Daniel J. Bernstein](https://en.wikipedia.org/wiki/Daniel_J._Bernstein).

## Installing the Plugin

Although the plugin's shared library is distributed by default with MariaDB, with a file name of `auth_ed25519.so` (Unix) or `auth_ed25519.dll` (Windows), the plugin is not actually installed by MariaDB by default. There are two methods that can be used to install the plugin with MariaDB.

The first method can be used to install the plugin without restarting the server. You can install the plugin dynamically by executing [INSTALL SONAME](../../sql-statements/administrative-sql-statements/plugin-sql-statements/install-soname.md) or [INSTALL PLUGIN](../../sql-statements/administrative-sql-statements/plugin-sql-statements/install-plugin.md):

```sql
INSTALL SONAME 'auth_ed25519';
```

The second method can be used to tell the server to load the plugin when it starts up. The plugin can be installed this way by providing the [--plugin-load](../../../server-management/starting-and-stopping-mariadb/mariadbd-options.md#plugin-load) or the [--plugin-load-add](../../../server-management/starting-and-stopping-mariadb/mariadbd-options.md#plugin-load-add) options. This can be specified as a command-line argument to [mariadbd](../../../server-management/starting-and-stopping-mariadb/mariadbd-options.md) or it can be specified in a relevant server [option group](../../../server-management/install-and-upgrade-mariadb/configuring-mariadb/configuring-mariadb-with-option-files.md#option-groups) in an [option file](../../../server-management/install-and-upgrade-mariadb/configuring-mariadb/configuring-mariadb-with-option-files.md):

```ini
[mariadb]
...
plugin_load_add = auth_ed25519
```

## Uninstalling the Plugin

You can uninstall the plugin dynamically by executing [UNINSTALL SONAME](../../sql-statements/administrative-sql-statements/plugin-sql-statements/uninstall-soname.md) or [UNINSTALL PLUGIN](../../sql-statements/administrative-sql-statements/plugin-sql-statements/uninstall-plugin.md):

```sql
UNINSTALL SONAME 'auth_ed25519';
```

If you installed the plugin by providing the [--plugin-load](../../../server-management/starting-and-stopping-mariadb/mariadbd-options.md#-plugin-load) or the [--plugin-load-add](../../../server-management/starting-and-stopping-mariadb/mariadbd-options.md#-plugin-load-add) options in a relevant server [option group](../../../server-management/install-and-upgrade-mariadb/configuring-mariadb/configuring-mariadb-with-option-files.md#option-groups) in an [option file](../../../server-management/install-and-upgrade-mariadb/configuring-mariadb/configuring-mariadb-with-option-files.md), those options must be removed to prevent the plugin from being loaded the next time the server is restarted.

## Creating Users

You can create a user account by executing the [CREATE USER](../../sql-statements/account-management-sql-statements/create-user.md) statement and providing the [IDENTIFIED VIA](../../sql-statements/account-management-sql-statements/create-user.md#identified-viawith-authentication_plugin) clause followied by the name of the plugin, `ed25519`, and providing the `USING` clause followed by the [PASSWORD()](../../sql-functions/secondary-functions/encryption-hashing-and-compression-functions/password.md) function, with the plain-text password as an argument:

```sql
CREATE USER username@hostname IDENTIFIED VIA ed25519 USING PASSWORD('secret');
```

If [SQL\_MODE](../../../server-management/variables-and-modes/sql-mode.md) does not have `NO_AUTO_CREATE_USER` set, then you can also create the user account via [GRANT](../../sql-statements/account-management-sql-statements/grant.md):

```sql
GRANT SELECT ON db.* TO username@hostname IDENTIFIED VIA ed25519 USING PASSWORD('secret');
```

The [PASSWORD()](../../sql-functions/secondary-functions/encryption-hashing-and-compression-functions/password.md) function and [SET PASSWORD](../../sql-statements/account-management-sql-statements/set-password.md) statements don't work with the `ed25519` authentication plugin. Instead, you have to use the [UDF](../../../server-usage/user-defined-functions/) that comes with the authentication plugin to calculate the password hash:

```sql
CREATE FUNCTION ed25519_password RETURNS STRING SONAME "auth_ed25519.so";
```

Now you can calculate a password hash by executing this query:

```sql
SELECT ed25519_password("secret");
+---------------------------------------------+
| SELECT ed25519_password("secret");          |
+---------------------------------------------+
| ZIgUREUg5PVgQ6LskhXmO+eZLS0nC8be6HPjYWR4YJY |
+---------------------------------------------+
```

Now you can use it to create the user account using the new password hash. As with any password, you should always use a complex password that isn't easy to guess. If you don't, if anyone gets access to the stored passwords in the `mysql.user` table, they could use [rainbow tables](https://en.wikipedia.org/wiki/Rainbow_table) to figure out the original password.

To create a user account via [CREATE USER](../../sql-statements/account-management-sql-statements/create-user.md), specify the name of the plugin in the [IDENTIFIED VIA](../../sql-statements/account-management-sql-statements/create-user.md#identified-viawith-authentication_plugin) clause while providing the password hash as the `USING` clause:

```sql
CREATE USER username@hostname IDENTIFIED VIA ed25519 
  USING 'ZIgUREUg5PVgQ6LskhXmO+eZLS0nC8be6HPjYWR4YJY';
```

If [SQL\_MODE](../../../server-management/variables-and-modes/sql-mode.md) does not have `NO_AUTO_CREATE_USER` set, you can also create the user account via [GRANT](../../sql-statements/account-management-sql-statements/grant.md):

```sql
GRANT SELECT ON db.* TO username@hostname IDENTIFIED VIA ed25519 
  USING 'ZIgUREUg5PVgQ6LskhXmO+eZLS0nC8be6HPjYWR4YJY';
```

{% hint style="warning" %}
Note that users require a password in order to be able to connect. It is possible to create users without specifying a password, but they will be unable to connect.
{% endhint %}

## Changing User Passwords

You can change a user account's password by executing the [SET PASSWORD](../../sql-statements/account-management-sql-statements/set-password.md) statement followed by the [PASSWORD()](../../sql-functions/secondary-functions/encryption-hashing-and-compression-functions/password.md) function and providing the plain-text password as an argument:

```sql
SET PASSWORD =  PASSWORD('new_secret')
```

You can also change the user account's password with the [ALTER USER](../../sql-statements/account-management-sql-statements/alter-user.md) statement. You would have to specify the name of the plugin in the [IDENTIFIED VIA](../../sql-statements/account-management-sql-statements/alter-user.md#identified-viawith-authentication_plugin) clause while providing the plain-text password as an argument to the `PASSWORD()` function in the `USING` clause:

```sql
ALTER USER username@hostname IDENTIFIED VIA ed25519 USING PASSWORD('new_secret');
```

The `PASSWORD()` function and [SET PASSWORD](../../sql-statements/account-management-sql-statements/set-password.md) statement did not work with the `ed25519` authentication plugin. Instead, you would have to use the [UDF](../../../server-usage/user-defined-functions/) that comes with the authentication plugin to calculate the password hash:

```sql
CREATE FUNCTION ed25519_password RETURNS STRING SONAME "auth_ed25519.so";
```

Now you can calculate a password hash by executing this query:

```sql
SELECT ed25519_password("secret");
+---------------------------------------------+
| SELECT ed25519_password("secret");          |
+---------------------------------------------+
| ZIgUREUg5PVgQ6LskhXmO+eZLS0nC8be6HPjYWR4YJY |
+---------------------------------------------+
```

Now you can change the user account's password using the new password hash.

You can change the user account's password with the [ALTER USER](../../sql-statements/account-management-sql-statements/alter-user.md) statement. You have to specify the name of the plugin in the [IDENTIFIED VIA](../../sql-statements/account-management-sql-statements/alter-user.md#identified-viawith-authentication_plugin) clause, while providing the password hash as the `USING` clause:

```sql
ALTER USER username@hostname IDENTIFIED VIA ed25519 
  USING 'ZIgUREUg5PVgQ6LskhXmO+eZLS0nC8be6HPjYWR4YJY';
```

## Client Authentication Plugins

For clients that use the `libmysqlclient` or [MariaDB Connector/C](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-c) libraries, MariaDB provides one client authentication plugin that is compatible with the `ed25519` authentication plugin:

* `client_ed25519`

When connecting with a [client or utility](../../../clients-and-utilities/) to a server as a user account that authenticates with the `ed25519` authentication plugin, you may need to tell the client where to find the relevant client authentication plugin by specifying the `--plugin-dir` option:

```bash
mysql --plugin-dir=/usr/local/mysql/lib64/mysql/plugin --user=alice
```

### `client_ed25519`

The `client_ed25519` client authentication plugin hashes and signs the password using the [Elliptic Curve Digital Signature Algorithm (ECDSA)](https://en.wikipedia.org/wiki/Elliptic_Curve_Digital_Signature_Algorithm) before sending it to the server.

## Support in Client Libraries

### Using the Plugin with MariaDB Connector/C

[MariaDB Connector/C](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-c) supports `ed25519` authentication using the client authentication plugins mentioned in the previous section.

### Using the Plugin with MariaDB Connector/ODBC

[MariaDB Connector/ODBC](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-odbc) supports `ed25519` authentication using the client authentication plugins mentioned in the previous section.

### Using the Plugin with MariaDB Connector/J

[MariaDB Connector/J](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-j) supports `ed25519` authentication.

### Using the Plugin with MariaDB Connector/Node.js

[MariaDB Connector/Node.js](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-nodejs) supports `ed25519` authentication.

### Using the Plugin with MySqlConnector for .NET

[MySqlConnector for ADO.NET](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-net/mariadb-connector-net-guide) supports `ed25519` authentication.

The connector implemented support for this authentication plugin in a separate [NuGet](https://docs.microsoft.com/en-us/nuget/what-is-nuget) package called [MySqlConnector.Authentication.Ed25519](https://www.nuget.org/packages/MySqlConnector.Authentication.Ed25519/). After the package is installed, your application must call `Ed25519AuthenticationPlugin.Install` to enable it.

## Options

### `ed25519`

* Description: Controls how the server should treat the plugin when it starts up.
  * Valid values are:
    * `OFF` - Disables the plugin without removing it from the [mysql.plugins](../../system-tables/the-mysql-database-tables/mysql-plugin-table.md) table.
    * `ON` - Enables the plugin. If the plugin cannot be initialized, then the server will still continue starting up, but the plugin will be disabled.
    * `FORCE` - Enables the plugin. If the plugin cannot be initialized, then the server will fail to start with an error.
    * `FORCE_PLUS_PERMANENT` - Enables the plugin. If the plugin cannot be initialized, then the server will fail to start with an error. In addition, the plugin cannot be uninstalled with [UNINSTALL SONAME](../../sql-statements/administrative-sql-statements/plugin-sql-statements/uninstall-soname.md) or [UNINSTALL PLUGIN](../../sql-statements/administrative-sql-statements/plugin-sql-statements/uninstall-plugin.md) while the server is running.
  * See [Plugin Overview: Configuring Plugin Activation at Server Startup](../plugin-overview.md#configuring-plugin-activation-at-server-startup) for more information.
* Command line: `--ed25519=value`
* Data Type: `enumerated`
* Default Value: `ON`
* Valid Values: `OFF`, `ON`, `FORCE`, `FORCE_PLUS_PERMANENT`

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
