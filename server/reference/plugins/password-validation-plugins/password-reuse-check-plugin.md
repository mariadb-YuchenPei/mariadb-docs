# Password Reuse Check Plugin

{% hint style="info" %}
`password_reuse_check` is available from [MariaDB 10.7.0](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/community-server/old-releases/release-notes-mariadb-10-7-series/mariadb-1070-release-notes).
{% endhint %}

## Description

The plugin is used to prevent a user from reusing a password, which can be a requirement in some security policies. The [password\_reuse\_check\_interval](password_reuse_check_interval.md) system variable determines the retention period, in days, for a password. By default this is zero, meaning unlimited retention. Old passwords are stored in the [mysql.password\_reuse\_check\_history table](../../system-tables/the-mysql-database-tables/mysqlpassword_reuse_check_history-table.md).

Note that passwords can be directly set as a hash, bypassing the password validation, if the [strict\_password\_validation](../../../ha-and-performance/optimization-and-tuning/system-variables/server-system-variables.md#strict_password_validation) variable is `OFF` (it is `ON` by default).

### Installing the Plugin

Although the plugin's shared library is distributed with MariaDB by default, the plugin is not actually installed by MariaDB by default.

You can install the plugin dynamically, without restarting the server, by executing [INSTALL SONAME](../../sql-statements/administrative-sql-statements/plugin-sql-statements/install-soname.md) or [INSTALL PLUGIN](../../sql-statements/administrative-sql-statements/plugin-sql-statements/install-plugin.md):

```sql
INSTALL SONAME 'password_reuse_check';
```

The second method can be used to tell the server to load the plugin when it starts up. The plugin can be installed this way by providing the [--plugin-load](../../../server-management/starting-and-stopping-mariadb/mariadbd-options.md) or the [--plugin-load-add](../../../server-management/starting-and-stopping-mariadb/mariadbd-options.md) options. This can be specified as a command-line argument to [mysqld](../../../server-management/starting-and-stopping-mariadb/mariadbd-options.md) or it can be specified in a relevant server [option group](../../../server-management/install-and-upgrade-mariadb/configuring-mariadb/configuring-mariadb-with-option-files.md#option-groups) in an [option file](../../../server-management/install-and-upgrade-mariadb/configuring-mariadb/configuring-mariadb-with-option-files.md):

```ini
[mariadb]
...
plugin_load_add = password_reuse_check
```

### Uninstalling the Plugin

You can uninstall the plugin dynamically by executing [UNINSTALL SONAME](../../sql-statements/administrative-sql-statements/plugin-sql-statements/uninstall-soname.md) or [UNINSTALL PLUGIN](../../sql-statements/administrative-sql-statements/plugin-sql-statements/uninstall-plugin.md):

```sql
UNINSTALL SONAME 'password_reuse_check';
```

If you installed the plugin by providing the [--plugin-load](../../../server-management/starting-and-stopping-mariadb/mariadbd-options.md) or the [--plugin-load-add](../../../server-management/starting-and-stopping-mariadb/mariadbd-options.md) options in a relevant server [option group](../../../server-management/install-and-upgrade-mariadb/configuring-mariadb/configuring-mariadb-with-option-files.md#option-groups) in an [option file](../../../server-management/install-and-upgrade-mariadb/configuring-mariadb/configuring-mariadb-with-option-files.md), then those options should be removed to prevent the plugin from being loaded the next time the server is restarted.

## Example

```sql
INSTALL SONAME 'password_reuse_check';

GRANT SELECT ON *.* TO user1@localhost identified by 'pwd1';
Query OK, 0 rows affected (0.038 sec)

GRANT SELECT ON *.* TO user1@localhost identified by 'pwd1';
ERROR 1819 (HY000): Your password does not satisfy the current policy requirements

GRANT SELECT ON *.* TO user1@localhost identified by 'pwd2';
Query OK, 0 rows affected (0.003 sec)

GRANT SELECT ON *.* TO user1@localhost identified by 'pwd1';
ERROR 1819 (HY000): Your password does not satisfy the current policy requirements
```

## Versions

| Version | Status | Introduced                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| ------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.0     | Alpha  | [MariaDB 10.7.0](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/community-server/old-releases/release-notes-mariadb-10-7-series/mariadb-1070-release-notes)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| 1.0     | Beta   | [MariaDB 10.7.2](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/community-server/old-releases/release-notes-mariadb-10-7-series/mariadb-1072-release-notes)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| 1.0     | Gamma  | [MariaDB 10.7.4](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/community-server/old-releases/release-notes-mariadb-10-7-series/mariadb-1074-release-notes)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| 2.0     | Stable | [MariaDB 10.7.7](https://github.com/mariadb-corporation/docs-server/blob/test/server/reference/plugins/password-validation-plugins/broken-reference/README.md), [MariaDB 10.8.7](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/community-server/old-releases/release-notes-mariadb-10-8-series/mariadb-10-8-7-release-notes), [MariaDB 10.9.5](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/community-server/old-releases/release-notes-mariadb-10-9-series/mariadb-10-9-5-release-notes), [MariaDB 10.10.2](https://github.com/mariadb-corporation/docs-server/blob/test/server/reference/plugins/password-validation-plugins/broken-reference/README.md) |

{% hint style="warning" %}
The bump to version 2.0 required the change of the stored format to mitigate an implementation weakness ([MDEV-28838](https://jira.mariadb.org/browse/MDEV-28838)) and as such the bump from 1.0 to 2.0 will invalidate previously saved password reuse protections.
{% endhint %}

## See Also

* [Password Validation](./)
* [10.7 preview feature: Password Reuse Check plugin](https://mariadb.org/10-7-preview-feature-password-reuse-check-plugin/) (MariaDB Foundation blog post)

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
