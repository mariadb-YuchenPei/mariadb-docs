# RESIGNAL

## Syntax

```
RESIGNAL [error_condition]
    [SET error_property
    [, error_property] ...]

error_condition:
    SQLSTATE [VALUE] 'sqlstate_value'
  | condition_name

error_property:
    error_property_name = <error_property_value>

error_property_name:
    CLASS_ORIGIN
  | SUBCLASS_ORIGIN
  | MESSAGE_TEXT
  | MYSQL_ERRNO
  | CONSTRAINT_CATALOG
  | CONSTRAINT_SCHEMA
  | CONSTRAINT_NAME
  | CATALOG_NAME
  | SCHEMA_NAME
  | TABLE_NAME
  | COLUMN_NAME
  | CURSOR_NAME
```

## Description

The syntax of `RESIGNAL` and its semantics are very similar to [SIGNAL](signal.md). This statement can only be used within an error [HANDLER](declare-handler.md). It produces an error, like [SIGNAL](signal.md). `RESIGNAL` clauses are the same as SIGNAL, except that they all are optional, even [SQLSTATE](programmatic-compound-statements-diagnostics/sqlstate.md). All the properties which are not specified in `RESIGNAL`, are identical to the properties of the error that was received by the error [HANDLER](../../reference/sql-structure/nosql/handler/). For a description of the clauses, see [diagnostics area](programmatic-compound-statements-diagnostics/diagnostics-area.md).

Note that `RESIGNAL` does not empty the diagnostics area: it just appends another error condition.

`RESIGNAL`, without any clauses, produces an error which is identical to the error that was received by [HANDLER](../../reference/sql-structure/nosql/handler/).

If used out of a [HANDLER](../../reference/sql-structure/nosql/handler/) construct, RESIGNAL produces the following error:

```
ERROR 1645 (0K000): RESIGNAL when handler not active
```

In [MariaDB 5.5](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/mariadb-community-server-release-notes/old-releases/release-notes-mariadb-5-5-series/changes-improvements-in-mariadb-5-5), if a [HANDLER](../../reference/sql-structure/nosql/handler/) contained a [CALL](../../reference/sql-statements/stored-routine-statements/call.md) to another procedure, that procedure could use `RESIGNAL`. Since [MariaDB 10.0](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/mariadb-community-server-release-notes/old-releases/release-notes-mariadb-10-0-series/changes-improvements-in-mariadb-10-0), trying to do this raises the above error.

For a list of `SQLSTATE` values and MariaDB error codes, see [MariaDB Error Codes](broken-reference).

The following procedure tries to query two tables which don't exist, producing a 1146 error in both cases. Those errors will trigger the [HANDLER](../../reference/sql-structure/nosql/handler/). The first time the error are ignored and the client will not receive it, but the second time, the error is re-signaled, so the client will receive it.

```
CREATE PROCEDURE test_error( )
BEGIN
   DECLARE CONTINUE HANDLER
      FOR 1146
   BEGIN
   IF @hide_errors IS FALSE THEN
      RESIGNAL;
   END IF;
   END;
   SET @hide_errors = TRUE;
   SELECT 'Next error are ignored' AS msg;
   SELECT `c` FROM `temptab_one`;
   SELECT 'Next error won''t be ignored' AS msg;
   SET @hide_errors = FALSE;
   SELECT `c` FROM `temptab_two`;
END;

CALL test_error( );

+----------------------------+
| msg                        |
+----------------------------+
| Next error are ignored |
+----------------------------+

+-----------------------------+
| msg                         |
+-----------------------------+
| Next error won't be ignored |
+-----------------------------+

ERROR 1146 (42S02): Table 'test.temptab_two' doesn't exist
```

The following procedure re-signals an error, modifying only the error message to clarify the cause of the problem.

```
CREATE PROCEDURE test_error()
BEGIN
   DECLARE CONTINUE HANDLER
   FOR 1146
   BEGIN
      RESIGNAL SET
      MESSAGE_TEXT = '`temptab` does not exist';
   END;
   SELECT `c` FROM `temptab`;
END;

CALL test_error( );
ERROR 1146 (42S02): `temptab` does not exist
```

As explained above, this works on [MariaDB 5.5](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/mariadb-community-server-release-notes/old-releases/release-notes-mariadb-5-5-series/changes-improvements-in-mariadb-5-5), but produces a 1645 error since 10.0.

```
CREATE PROCEDURE handle_error()
BEGIN
  RESIGNAL;
END;
CREATE PROCEDURE p()
BEGIN
  DECLARE EXIT HANDLER FOR SQLEXCEPTION CALL p();
  SIGNAL SQLSTATE '45000';
END;
```

## See Also

* [Diagnostics Area](programmatic-compound-statements-diagnostics/diagnostics-area.md)
* [SIGNAL](signal.md)
* [HANDLER](../../reference/sql-structure/nosql/handler/)
* [Stored Routines](../stored-routines/)
* [MariaDB Error Codes](broken-reference)

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
