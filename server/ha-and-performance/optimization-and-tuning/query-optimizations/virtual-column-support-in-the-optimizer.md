# Virtual Column Support in the Optimizer

**MariaDB starting with** [**11.8**](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/community-server/mariadb-11-8-series/what-is-mariadb-118)

Starting from [MariaDB 11.8](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/community-server/mariadb-11-8-series/what-is-mariadb-118), the optimizer can recognize use of indexed virtual column expressions in the WHERE clause and use them to construct range and ref(const) accesses.

## Motivating Example

Suppose one has a table with data in JSON:

```sql
CREATE TABLE t1 (json_data JSON);
INSERT INTO t1 VALUES('{"column1": 1234}'); 
INSERT INTO t1 ...
```

In order to do efficient queries over data in JSON, one can add a virtual column and an index on it:

```sql
ALTER TABLE t1
  ADD COLUMN vcol1 INT AS (cast(json_value(json_data, '$.column1') AS INTEGER)),
  ADD INDEX(vcol1);
```

Before [MariaDB 11.8](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/community-server/mariadb-11-8-series/what-is-mariadb-118), one had to use `vcol1` in the WHERE clause. Now, one can use the\
virtual column expression, too:

```sql
-- This will use the index before 11.8:
EXPLAIN SELECT * FROM t1 WHERE vcol1=100;
-- Starting from 11.8, this will use the index, too:
EXPLAIN SELECT * FROM t1 
WHERE cast(json_value(json_data, '$.column1') AS INTEGER)=100;
```

```
+------+-------------+-------+------+---------------+-------+---------+-------+------+-------+
| id   | select_type | table | type | possible_keys | key   | key_len | ref   | rows | Extra |
+------+-------------+-------+------+---------------+-------+---------+-------+------+-------+
|    1 | SIMPLE      | t1    | ref  | vcol1         | vcol1 | 5       | const | 1    |       |
+------+-------------+-------+------+---------------+-------+---------+-------+------+-------+
```

## General Considerations

* In MariaDB, one has to create a virtual column and then create an index over it. Other databases allow to create an index directly over expression: `create index on t1((col1+col2))`. This is not yet supported in MariaDB ([MDEV-35853](https://jira.mariadb.org/browse/MDEV-35853)).
* The `WHERE` clause must use the exact same expression as in the virtual column definition.
* The optimization is implemented in a similar way to MySQL: the optimizer finds potentially useful occurrences of `vcol_expr` in the WHERE clause and replaces them with `vcol_name`.
* In the optimizer trace, the rewrites are shown like so:

```json
"virtual_column_substitution": {
              "condition": "WHERE",
              "resulting_condition": "t1.vcol1 = 100"
            }
```

## Accessing JSON fields

### Cast the value to the desired type

SQL is strongly-typed language while JSON is weakly-typed. This means one must specify the desired datatype when accessing JSON data from SQL. In the above example, we declared `vcol1` as `INT` and then used `(CAST ... AS INTEGER)` (both in the ALTER TABLE and in the `WHERE` clause in SELECT query:):

```sql
ALTER TABLE t1
  ADD COLUMN vcol1 INT AS (CAST(json_value(json_data, '$.column1') AS INTEGER)) ...
```

```sql
SELECT ...  WHERE ... CAST(json_value(json_data, '$.column1') AS INTEGER) ...;
```

### Specify collation for strings

When extracting string values, `CAST` is not necessary, as `JSON_VALUE` returns strings.

However, one must take into account collations. If one declares the column as `JSON`:

```sql
CREATE TABLE t1 ( 
  json_data JSON 
  ...
```

the collation of `json_data` will be `utf8mb4_bin`. The collation of`JSON_VALUE(json_data, ...)` will also be `utf8mb4_bin`.

Most use cases require a more commonly-used collation. It is possible to achieve that using the `COLLATE` clause:

```sql
ALTER TABLE t1
  ADD col1 VARCHAR(100) COLLATE utf8mb4_uca1400_ai_ci AS
  (json_value(js1, '$.string_column') COLLATE utf8mb4_uca1400_ai_ci),
  ADD INDEX(col1);
...
SELECT  ... 
WHERE
  json_value(js1, '$.string_column') COLLATE utf8mb4_uca1400_ai_ci='string-value';
```

## References

* [MDEV-35616](https://jira.mariadb.org/browse/MDEV-35616): Add basic optimizer support for virtual columns

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
