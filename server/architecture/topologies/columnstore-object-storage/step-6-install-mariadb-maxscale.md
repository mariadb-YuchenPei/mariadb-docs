# Step 6: Install MariaDB MaxScale

## Overview

This page details step 6 of the 9-step procedure "[Deploy ColumnStore Object Storage Topology](./)".

This step installs MariaDB MaxScale 22.08.

ColumnStore Object Storage requires 1 or more MaxScale nodes.

Interactive commands are detailed. Alternatively, the described operations can be performed using automation.

## Retrieve Customer Download Token

MariaDB Corporation provides package repositories for `CentOS / RHEL (YUM) and Debian / Ubuntu (APT)`. A download token is required to access the MariaDB Enterprise Repository.

Customer Download Tokens are customer-specific and are available through the MariaDB Customer Portal.

To retrieve the token for your account:

1. Navigate to [https://customers.mariadb.com/downloads/token/](https://customers.mariadb.com/downloads/token/)
2. Log in.
3. Copy the Customer Download Token.

Substitute your token for `CUSTOMER_DOWNLOAD_TOKEN` when configuring the package repositories.

## Set Up Repository

1. On the MaxScale node, install the prerequisites for downloading the software from the Web.\
   Install on CentOS / RHEL (YUM):

```bash
$ sudo yum install curl
```

Install on Debian / Ubuntu (APT):

```bash
$ sudo apt install curl apt-transport-https
```

2. On the MaxScale node, configure package repositories and specify MariaDB MaxScale 22.08:

```bash
$ curl -LsSO https://dlm.mariadb.com/enterprise-release-helpers/mariadb_es_repo_setup

$ echo "4d483b4df193831a0101d3dfa7fb3e17411dda7fc06c31be4f9e089c325403c0  mariadb_es_repo_setup" \
       | sha256sum -c -

$ chmod +x mariadb_es_repo_setup

$ sudo ./mariadb_es_repo_setup --token="CUSTOMER_DOWNLOAD_TOKEN" --apply \
      --skip-server \
      --skip-tools \
      --mariadb-maxscale-version="22.08"
```

## Install MaxScale

**On the MaxScale node**, install MariaDB MaxScale.

Install on CentOS / RHEL (YUM):

```bash
$ sudo yum install maxscale
```

Install on Debian / Ubuntu (APT):

```bash
$ sudo apt install maxscale
```

## Next Step

Navigation in the procedure "Deploy ColumnStore Object Storage Topology":

This page was **step 6 of 9**.

Next: Step 7: Start and Configure MariaDB MaxScale.

<sub>_This page is: Copyright © 2025 MariaDB. All rights reserved._</sub>

{% @marketo/form formId="4316" %}
