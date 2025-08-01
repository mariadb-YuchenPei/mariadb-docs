# ALTER PROCEDURE

## Syntax

```sql
ALTER PROCEDURE proc_name [characteristic ...]

characteristic:
    { CONTAINS SQL | NO SQL | READS SQL DATA | MODIFIES SQL DATA }
  | SQL SECURITY { DEFINER | INVOKER }
  | COMMENT 'string'
```

## Description

This statement can be used to change the characteristics of a [stored\
procedure](./). More than one change may be specified in an `ALTER PROCEDURE`\
statement. However, you cannot change the parameters or body of a\
stored procedure using this statement. To make such changes, you must\
drop and re-create the procedure using either [CREATE OR REPLACE PROCEDURE](create-procedure.md) (since [MariaDB 10.1.3](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/community-server/old-releases/release-notes-mariadb-10-1-series/mariadb-10-1-3-release-notes)) or [DROP PROCEDURE](drop-procedure.md) and [CREATE PROCEDURE](create-procedure.md) ([MariaDB 10.1.2](../../../server-management/install-and-upgrade-mariadb/installing-mariadb/binary-packages/rpm/mariadb-installation-version-10121-via-rpms-on-centos-7.md) and before).

You must have the `ALTER ROUTINE` privilege for the procedure. By default, that privilege is granted automatically to the procedure creator. See [Stored Routine Privileges](../stored-functions/stored-routine-privileges.md).

## Example

```sql
ALTER PROCEDURE simpleproc SQL SECURITY INVOKER;
```

## See Also

* [Stored Procedure Overview](stored-procedure-overview.md)
* [CREATE PROCEDURE](create-procedure.md)
* [SHOW CREATE PROCEDURE](../../../reference/sql-statements/administrative-sql-statements/show/show-create-procedure.md)
* [DROP PROCEDURE](drop-procedure.md)
* [SHOW CREATE PROCEDURE](../../../reference/sql-statements/administrative-sql-statements/show/show-create-procedure.md)
* [SHOW PROCEDURE STATUS](../../../reference/sql-statements/administrative-sql-statements/show/show-procedure-status.md)
* [Stored Routine Privileges](../stored-functions/stored-routine-privileges.md)
* [Information Schema ROUTINES Table](../../../reference/system-tables/information-schema/information-schema-tables/information-schema-routines-table.md)

<sub>_This page is licensed: GPLv2, originally from_</sub> [<sub>_fill\_help\_tables.sql_</sub>](https://github.com/MariaDB/server/blob/main/scripts/fill_help_tables.sql)

{% @marketo/form formId="4316" %}
