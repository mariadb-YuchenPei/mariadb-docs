# MariaDB Galera Cluster 10.0.35 Release Notes

The most recent [MariaDB Galera Cluster 10.0](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/galera/README.md) release is:[**MariaDB Galera Cluster 10.0.38**](mariadb-galera-cluster-10038-release-notes.md) [Download Now](https://downloads.mariadb.org/mariadb-galera/10.0.38)

[Download](https://downloads.mariadb.org/mariadb-galera/10.0.35)[Release Notes](mariadb-galera-cluster-10035-release-notes.md)[Changelog](../mariadb-galera-100-changelogs/mariadb-galera-cluster-10035-changelog.md)[Overview of MariaDB Galera Cluster](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/what-is-mariadb-galera-cluster/README.md)

**Release date:** 9 May 2018

MariaDB Galera Cluster 10.0.35 is a [_**Stable**_](../../../about/release-criteria.md) (GA)\
release. It is a merge of [MariaDB 10.0.35](../../release-notes-mariadb-10-0-series/mariadb-10035-release-notes.md) and[Galera Cluster](https://codership.com/content/using-galera-cluster) with\
additional bug fixes.

Various articles about MariaDB Galera Cluster, including[known limitations](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/galera-management/mariadb-galera-cluster-known-limitations) and[how to get started](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/galera-management/getting-started-with-mariadb-galera-cluster) are\
available in the [**Galera**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/galera/README.md) section of the documentation.

For a list of changes made in MariaDB Galera Cluster 10.0.35, with links to\
detailed information on each push, see the[MariaDB Galera Cluster 10.0.35 Changelog](../mariadb-galera-100-changelogs/mariadb-galera-cluster-10035-changelog.md).\
For changes made in [MariaDB 10.0.35](../../release-notes-mariadb-10-0-series/mariadb-10035-release-notes.md), see the[MariaDB 10.0.35 Changelog](../../../changelogs/changelogs-mariadb-100-series/mariadb-10035-changelog.md)

## Updates and fixes in this version

* This release is mainly a bug-fix release.
* Codership changes: [github.com/codership/mysql-wsrep/tree/5.6](https://github.com/codership/mysql-wsrep/tree/5.6)
* The [Galera library](https://codership.com/content/using-galera-cluster) used\
  by MariaDB Galera Cluster and included in the MariaDB repositories is\
  currently at version 25.3.23.
* Fixes for the following [security vulnerabilities](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/security/securing-mariadb/security):
  * [CVE-2018-2755](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-2755)
  * [CVE-2018-2761](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-2761)
  * [CVE-2018-2766](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-2766)
  * [CVE-2018-2767](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-2767)
  * [CVE-2018-2771](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-2771)
  * [CVE-2018-2781](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-2781)
  * [CVE-2018-2782](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-2782)
  * [CVE-2018-2784](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-2784)
  * [CVE-2018-2787](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-2787)
  * [CVE-2018-2813](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-2813)
  * [CVE-2018-2817](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-2817)
  * [CVE-2018-2819](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-2819)
  * [CVE-2018-3081](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-3081)
  * [CVE-2019-2455](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-2455)
* See the [MariaDB 10.0.35 Release Notes](../../release-notes-mariadb-10-0-series/mariadb-10035-release-notes.md) and[Changelog](../../../changelogs/changelogs-mariadb-100-series/mariadb-10035-changelog.md) for more information on the changes in\
  MariaDB.

## Notes

* Running MariaDB Galera Cluster 5.5 and 10.0 nodes in a cluster is not\
  supported ([MDEV-6257](https://jira.mariadb.org/browse/MDEV-6257))
* This version of MariaDB Galera Cluster supports `wsrep` API v25 which means\
  MariaDB Galera Cluster can be used with either a 25.2.x or 25.3.x\
  Galera `wsrep` provider. A 25.3.x `wsrep` provider is included in the\
  MariaDB repositories and is also available from the[downloads](https://downloads.mariadb.org/mariadb-galera/10.0) page.
* On Ubuntu and Debian, the Galera Arbitrator daemon (garbd) and the galera\
  library are in two separate packages. The packages are named galera-3\
  and galera-arbitrator-3. When installing MariaDB Galera Cluster on Ubuntu and\
  Debian (the mariadb-galera-server package), the galera-3 package will be\
  automatically installed. You can then install the arbitrator package on a\
  separate node (recommended) or on one of the nodes running\
  mariadb-galera-server (not recommended).

Note: If Galera 25.2.x and 25.3.x are both being used in the cluster, MariaDB\
with Galera 25.3.x must be started with[wsrep\_provider\_options='socket.checksum=1'](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/wsrep-variable-details/wsrep_provider_options#socketchecksum) in order to make it backward\
compatible with Galera v2. Galera wsrep providers other than 25.3.x or 25.2.x\
are not supported.

## Contributors

For a full list of contributors to MariaDB Galera Cluster 10.0.35, see the [MariaDB Foundation release announcement](https://mariadb.org/mariadb-10-1-33-and-mariadb-galera-cluster-10-0-35-now-available/).

Thank you for using MariaDB Galera Cluster!

{% include "../../../../.gitbook/includes/announce.md" %}

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
