# Connector/Python 1.1.13 Changelog

<a href="https://mariadb.com/downloads/connectors/connectors-data-access/python-connector/" class="button primary">Download</a>  <a href="../../mariadb-connector-python-1-1-release-notes/mariadb-connector-python-1-1-13-release-notes.md" class="button secondary">Release Notes</a>  <a href="connector-python-1.1.13-changelog.md" class="button secondary">Changelog</a>  <a href="https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/connectors-quickstart-guides/connector-python-guide" class="button secondary">Connector/Python Overview</a>

**Release date:** Jul 15 2025

For the highlights of this release, see the [release notes](../../mariadb-connector-python-1-1-release-notes/mariadb-connector-python-1-1-13-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On [GitHub](https://github.com/MariaDB/mariadb-connector-python/) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #7b015f2](https://github.com/mariadb-corporation/mariadb-connector-python/commit/7b015f2) <sub>_2025-06-22 07:39:00 +0200_</sub>
  * CONPY-313: Check float types "inf", "-inf" and "nan"
* [Revision #6831e07](https://github.com/mariadb-corporation/mariadb-connector-python/commit/6831e07) <sub>_2025-06-16 14:07:09 +0200_</sub>
  * Skip reconnect test for maxscale
* [Revision #8090efa](https://github.com/mariadb-corporation/mariadb-connector-python/commit/8090efa) <sub>_2025-06-16 12:44:14 +0200_</sub>
  * Fixed various memory leaks and address sanitizer related problems:
* [Revision #7b0fbd8](https://github.com/mariadb-corporation/mariadb-connector-python/commit/7b0fbd8) <sub>_2025-04-01 09:15:21 +0200_</sub>
  * Merge pull request #31 from mr-c/typo
* [Revision #b89c90a](https://github.com/mariadb-corporation/mariadb-connector-python/commit/b89c90a) <sub>_2024-11-25 13:02:05 +0100_</sub>
  * fix a typo
* [Revision #ee884c8](https://github.com/mariadb-corporation/mariadb-connector-python/commit/ee884c8) <sub>_2025-02-24 12:00:32 +0100_</sub>
  * For the moment we disable benchmarking on travis.
* [Revision #0723803](https://github.com/mariadb-corporation/mariadb-connector-python/commit/0723803) <sub>_2025-02-24 11:58:17 +0100_</sub>
  * CONPY-306: Fix crash when getting invalid unicode
* [Revision #63e10d0](https://github.com/mariadb-corporation/mariadb-connector-python/commit/63e10d0) <sub>_2025-02-22 11:04:02 +0100_</sub>
  * Improve cursor behavior on closed connections
* [Revision #5f227fc](https://github.com/mariadb-corporation/mariadb-connector-python/commit/5f227fc) <sub>_2025-02-21 08:31:57 +0100_</sub>
  * Run benchmarks with 3.12 instead of 3.13
* [Revision #0ebfcd5](https://github.com/mariadb-corporation/mariadb-connector-python/commit/0ebfcd5) <sub>_2025-02-21 08:22:12 +0100_</sub>
  * Added tp\_dealloc for cursor object
* [Revision #11a22ad](https://github.com/mariadb-corporation/mariadb-connector-python/commit/11a22ad) <sub>_2025-02-20 19:53:33 +0100_</sub>
  * CONPY-296: Include test suite in sdist
* [Revision #4d8dde1](https://github.com/mariadb-corporation/mariadb-connector-python/commit/4d8dde1) <sub>_2025-02-17 17:14:33 +0100_</sub>
  * Enable benchmark for 3.13
* [Revision #aac09d2](https://github.com/mariadb-corporation/mariadb-connector-python/commit/aac09d2) <sub>_2025-02-14 14:24:26 +0100_</sub>
  * Fix warnings in mariadb\_codecs.c
* [Revision #e73f280](https://github.com/mariadb-corporation/mariadb-connector-python/commit/e73f280) <sub>_2025-02-13 14:19:54 +0100_</sub>
  * bump version (to 1.1.13)
