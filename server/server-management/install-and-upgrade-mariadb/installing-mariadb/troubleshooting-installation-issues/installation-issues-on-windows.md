# Installation issues on Windows

## [MariaDB 10.4.13](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/community-server/old-releases/release-notes-mariadb-10-4-series/mariadb-10413-release-notes)

[MariaDB 10.4.13](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/community-server/old-releases/release-notes-mariadb-10-4-series/mariadb-10413-release-notes) may not start on Windows. See [MDEV-22555](https://jira.mariadb.org/browse/MDEV-22555).

To resolve this, download, click and install [vc\_redist.x64.exe](https://aka.ms/vs/16/release/vc_redist.x64.exe) and then install 10.4.13.

## Unsupported Versions of Windows

Recent versions of MariaDB may not install on unsupported Windows versions. See [Deprecated Package Platforms](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/community-server/about/platform-deprecation-policy) to find the final supported versions.

## [MariaDB 5.2.5](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/community-server/old-releases/release-notes-mariadb-5-2-series/mariadb-525-release-notes) and earlier

### On Windows Vista/7 , changes to database or my.ini are not persistent, when mysqld.exe is run from the command line.

The reason for this behavior is Vista/Win7 file system redirection. Writes to\
protected locations (in this case a subdirectory of Program Files) are\
redirected to the user's so-called "Virtual Store".

Workarounds:

* Run mysqld.exe as service. See answer [here](https://stackoverflow.com/questions/4962342/mariadb-on-windows-what-is-this-error-when-trying-to-start-the-database-engine) on how to create a MariaDB service.
* Run mysqld.exe from the [elevated command prompt](https://www.winhelponline.com/articles/158/1/How-to-open-an-elevated-Command-Prompt-in-Windows-Vista.html).
* [Change the ACL](https://technet.microsoft.com/en-us/library/bb727008.aspx) of the data directory and add full control for the current\
  user.

The Windows installer for [MariaDB 5.2.6](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/community-server/old-releases/release-notes-mariadb-5-2-series/mariadb-526-release-notes) and higher will set the data directory\
ACL to include full access rights for the user who runs the setup to prevent\
this issue from happening.

## Systems with User Account Control

Running `mysql_install_db.exe` from a standard command prompt might cause the error:

```
FATAL ERROR: OpenSCManager failed
```

To get rid of it, use the elevated command prompt, for example on Windows 7 start it via 'Run as administrator' option.

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
