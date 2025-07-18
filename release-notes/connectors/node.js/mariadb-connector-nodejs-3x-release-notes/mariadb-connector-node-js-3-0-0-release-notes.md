# Connector/Node.js 3.0.0 GA Release Notes

{% include "../../../.gitbook/includes/latest-nodejs.md" %}

**Release date:** 1 Mar 2022

MariaDB Connector/Node.js 3.0.0 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release.

{% hint style="success" %}
**For an overview of MariaDB Connector/Node.js see the** [**About MariaDB Connector/Node.js**](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-nodejs/mariadb-connector-node-js-guide) **page**
{% endhint %}

see [3.0.0-rc](mariadb-connector-node-js-3-0-0-rc-release-notes.md) for 3.0.0 content from previous version.

## Notable Changes

* merged correction from 2.5.6
* \[[CONJS-185](https://jira.mariadb.org/browse/CONJS-185)] considering BIT(1) as boolean (option bitOneIsBoolean permit to disable that behavior for compatibility)
* pool ensuring multi-request process order
* set parser function once per result-set for better performance

## Changelog

For a complete list of changes made in this release, with links to detailed information\
on each push, see the [changelog](../changelogs/mariadb-connector-nodejs-3x-changelogs/mariadb-connector-nodejs-300-ga-changelog.md).

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
