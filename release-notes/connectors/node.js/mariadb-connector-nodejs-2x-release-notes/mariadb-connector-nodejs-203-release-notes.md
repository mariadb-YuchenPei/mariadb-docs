# Connector/Node.js 2.0.3 Release Notes

{% include "../../../.gitbook/includes/latest-nodejs.md" %}

[Download](https://mariadb.com/downloads/#connectors) | [Release Notes](mariadb-connector-nodejs-203-release-notes.md) | [Changelog](../changelogs/mariadb-connector-nodejs-2x-changelogs/mariadb-connector-nodejs-203-changelog.md) | [Connector/Node.js Overview](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-nodejs/mariadb-connector-node-js-guide.md)

**Release date:** 31 Jan 2019

MariaDB Connector/Node.js 2.0.3 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release.

{% hint style="success" %}
**For an overview of MariaDB Connector/Node.js see the** [**About MariaDB Connector/Node.js**](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-nodejs/mariadb-connector-node-js-guide) **page**
{% endhint %}

## Notable Changes

* \[[CONJS-56](https://jira.mariadb.org/browse/CONJS-56)] TypeError: Cannot read property 'totalConnections' of undefined
* \[[CONJS-59](https://jira.mariadb.org/browse/CONJS-59)] pool now throw `ER_ACCESS_DENIED_ERROR` in place of a basic timeout error
* \[[CONJS-60](https://jira.mariadb.org/browse/CONJS-60)] handling pipe error when streaming, avoiding hang in case of pipe error.
* \[[CONJS-55](https://jira.mariadb.org/browse/CONJS-55)] Connector throw an error when using incompatible options

## Changelog

For a complete list of changes made in this release, with links to detailed information\
on each push, see the [changelog](../changelogs/mariadb-connector-nodejs-2x-changelogs/mariadb-connector-nodejs-203-changelog.md).

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
