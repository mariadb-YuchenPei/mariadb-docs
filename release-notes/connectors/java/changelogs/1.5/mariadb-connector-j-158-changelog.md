# Connector/J 1.5.8 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/1.5.8/)[Release Notes](../../1.5/mariadb-connector-j-158-release-notes.md)[Changelog](mariadb-connector-j-158-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 15 Feb 2017

For the highlights of this release, see the[release notes](../../1.5/mariadb-connector-j-158-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On[GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #a8dac31](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a8dac31) - \[misc] bump 1.5.8 version
* [Revision #b54793c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b54793c) - \[[CONJ-420](https://jira.mariadb.org/browse/CONJ-420)] high CPU usage against Aurora after 2 hours of inactivity
* [Revision #3a20910](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3a20910) - \[misc] checkstyle correction
* [Revision #2aa57ba](https://github.com/mariadb-corporation/mariadb-connector-j/commit/2aa57ba) - \[[CONJ-419](https://jira.mariadb.org/browse/CONJ-419)] failover execution when master is demote without restart
* [Revision #7e4650d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/7e4650d) - \[[CONJ-419](https://jira.mariadb.org/browse/CONJ-419)] checking if master connection is still in write mode when having exception with 1290 error code (ER\_OPTION\_PREVENTS\_STATEMENT)
* [Revision #31a264d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/31a264d) - \[misc] improve reading additional capabilities for [MariaDB 10.2](../../../../community-server/old-releases/release-notes-mariadb-10-2-series/what-is-mariadb-102.md)
* [Revision #ad5ce72](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ad5ce72) - \[misc] travis cache maven + update changelog
* [Revision #04c7877](https://github.com/mariadb-corporation/mariadb-connector-j/commit/04c7877) - Merge remote-tracking branch 'origin/hotfix/FIX1.5.8' into hotfix/FIX1.5.8
* [Revision #45361fd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/45361fd) - \[[CONJ-426](https://jira.mariadb.org/browse/CONJ-426)] Allow executeBatch to be interrupted
* [Revision #daf7c38](https://github.com/mariadb-corporation/mariadb-connector-j/commit/daf7c38) - \[[CONJ-425](https://jira.mariadb.org/browse/CONJ-425)] CallableStatement getObject class according to java.sql.Types value
* [Revision #ee0ee67](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ee0ee67) - Merge remote-tracking branch 'origin/pr/99' into hotfix/FIX1.5.8
* [Revision #722f717](https://github.com/mariadb-corporation/mariadb-connector-j/commit/722f717) - [CONJ-426](https://jira.mariadb.org/browse/CONJ-426) Allow executeBatch to be interrupted. Modify CmdInformationMultiple data structures for concurrent access
* [Revision #a95e3ba](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a95e3ba) - \[misc] bump 1.5.8-SNAPSHOT version
* [Revision #21ce6cb](https://github.com/mariadb-corporation/mariadb-connector-j/commit/21ce6cb) - \[[CONJ-424](https://jira.mariadb.org/browse/CONJ-424)] checkstyle correction
* [Revision #d228844](https://github.com/mariadb-corporation/mariadb-connector-j/commit/d228844) - \[[CONJ-424](https://jira.mariadb.org/browse/CONJ-424)] Empty getGeneratedKeys() reusability error
* [Revision #ee27135](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ee27135) - \[[CONJ-392](https://jira.mariadb.org/browse/CONJ-392)] Aurora cluster endpoint detection fails when time\_zone doesn't match system\_time\_zone
* [Revision #fde834c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fde834c) - \[misc] checkstyle improvement
* [Revision #c772b18](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c772b18) - \[[CONJ-412](https://jira.mariadb.org/browse/CONJ-412)] changing test to use year(4) to test MySQL compatibility
* [Revision #eaea777](https://github.com/mariadb-corporation/mariadb-connector-j/commit/eaea777) - \[[CONJ-412](https://jira.mariadb.org/browse/CONJ-412)] database DECIMAL\_DIGITS must have int datatype part 2
* [Revision #585adeb](https://github.com/mariadb-corporation/mariadb-connector-j/commit/585adeb) - \[[CONJ-412](https://jira.mariadb.org/browse/CONJ-412)] database DECIMAL\_DIGITS must have int datatype
* [Revision #cb7b705](https://github.com/mariadb-corporation/mariadb-connector-j/commit/cb7b705) - \[CONJ 412] tinyInt1isBit and yearIsDateType is not applied in method columnTypeClause
* [Revision #5c502c2](https://github.com/mariadb-corporation/mariadb-connector-j/commit/5c502c2) - Merge remote-tracking branch 'origin/pr/95' into hotfix/FIX1.5.8
* [Revision #40f2ccf](https://github.com/mariadb-corporation/mariadb-connector-j/commit/40f2ccf) - \[CONJ 415] ResultSet.absolute() should not always return true
* [Revision #2f99de9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/2f99de9) - \[CONJ 418] ResultSet.last() isLast() afterLast() and isAfterLast() correction when streaming
* [Revision #ec3f9a0](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ec3f9a0) - Merge branch 'pr/95'
* [Revision #1fde8e9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1fde8e9) - \[[CONJ-412](https://jira.mariadb.org/browse/CONJ-412)] tinyInt1isBit and yearIsDateType is not applied in method columnTypeClause
* [Revision #fb659d4](https://github.com/mariadb-corporation/mariadb-connector-j/commit/fb659d4) - Merge remote-tracking branch 'origin/master'
* [Revision #237d393](https://github.com/mariadb-corporation/mariadb-connector-j/commit/237d393) - \[[CONJ-415](https://jira.mariadb.org/browse/CONJ-415)] ResultSet.absolute should not always return true
* [Revision #dbc35a7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/dbc35a7) - \[[CONJ-418](https://jira.mariadb.org/browse/CONJ-418)] ResultSet.isLast() correction when streaming result
* [Revision #a470185](https://github.com/mariadb-corporation/mariadb-connector-j/commit/a470185) - \[[CONJ-418](https://jira.mariadb.org/browse/CONJ-418)] ResultSet.isAfterLast() correction when streaming result
* [Revision #17f7875](https://github.com/mariadb-corporation/mariadb-connector-j/commit/17f7875) - [CONJ-412](https://jira.mariadb.org/browse/CONJ-412) changes for review
* [Revision #757eb2d](https://github.com/mariadb-corporation/mariadb-connector-j/commit/757eb2d) - [CONJ-412](https://jira.mariadb.org/browse/CONJ-412): tinyInt1isBit is not applied in method columnTypeClause

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
