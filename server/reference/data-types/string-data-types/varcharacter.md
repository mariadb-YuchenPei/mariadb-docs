# VARCHARACTER

## Overview

See [VARCHAR](varchar.md).

## EXAMPLES

```sql
CREATE TABLE varcharacter_example (
  example VARCHARACTER(32)
);
```

```sql
SHOW CREATE TABLE varcharacter_example\G

*************************** 1. row ***************************
       Table: varcharacter_example
Create Table: CREATE TABLE `varcharacter_example` (
  `example` varchar(32) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1
```

<sub>_This page is: Copyright © 2025 MariaDB. All rights reserved._</sub>

{% @marketo/form formId="4316" %}
