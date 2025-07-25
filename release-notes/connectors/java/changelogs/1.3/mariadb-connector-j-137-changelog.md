# MariaDB Connector/J 1.3.7 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/1.3.7/)[Release Notes](../../1.3/mariadb-connector-j-137-release-notes.md)[Changelog](mariadb-connector-j-137-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md)

**Release date:** 23 Mar 2016

For the highlights of this release, see the[release notes](../../1.3/mariadb-connector-j-137-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On[GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more details of the revision and view diffs of the code modified in that revision.

### Major

* [CONJ-259](https://jira.mariadb.org/browse/CONJ-259) : Server prepare statement failover use the associated connection [Revision #dfe8a7d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/dfe8a7d)
* Performance improvement : using directly the query.getByte("UTF-8") array to\
  avoid recreating a new array, rewriteStatement improvement (parsing query to\
  verify that the query can be rewritten + performance) [CONJ-262](https://jira.mariadb.org/browse/CONJ-262), Local file upload\
  correction when using useCompression option.
  * [Revision #048b927](https://github.com/mariadb-corporation/mariadb-connector-j/commit/048b927)
  * [Revision #db08fc1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/db08fc1)
  * [Revision #dfe8a7d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/dfe8a7d)
  * [Revision #5ac170f](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5ac170f)
  * [Revision #e115014](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e115014)
  * [Revision #1cd83a3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1cd83a3)
  * [Revision #48d6ebd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/48d6ebd)
  * [Revision #3b7cfb9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3b7cfb9)
  * [Revision #be23cbd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/be23cbd)
  * [Revision #b5cc750](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b5cc750)
  * [Revision #6fcfdaf](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6fcfdaf)

### Minor

* [CONJ-264](https://jira.mariadb.org/browse/CONJ-264) : SQLException when calling PreparedStatement.executeBatch() without calling addBatch(). [Revision #6634fa5](https://github.com/mariadb-corporation/mariadb-connector-j/commit/6634fa5)
* [CONJ-263](https://jira.mariadb.org/browse/CONJ-263) : Error in stored procedure or SQL statement with allowMultiQueries does not raise Exception when there is a result returned prior to erroneous statement.[Revision #c02b379](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c02b379)
* [CONJ-267](https://jira.mariadb.org/browse/CONJ-267) : getString on '0000-00-00' date was returning npe. [Revision #d384a62](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d384a62)
* PrepareStatement [setObject(int parameterIndex, Object x, int targetSqlType, int scaleOrLength)](https://docs.oracle.com/javase/7/docs/api/java/sql/PreparedStatement.html#setObject\(int,%20java.lang.Object,%20int,%20int\)) now doesn't lose decimal when using Float or Double object, [Revision #d5a4ecd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d5a4ecd), [Revision #a3c030d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a3c030d)

**Misc**

* ServerPrepareStatement avoid the fallback to Client PrepareStatement when there is a socket exception. [Revision #f2a4571](https://github.com/mariadb-corporation/mariadb-connector-j/commit/f2a4571)

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
