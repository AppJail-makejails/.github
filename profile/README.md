# AppJail Makejails

Welcome to the centralized repository, here you can find some useful Makejails to deploy cool projects.

github.com/DtxdF/AppJail

<img src="https://avatars.githubusercontent.com/u/124508626?s=200&v=4" width="30%" height="auto">

## Status

Every 21 days all AppJail images will be created thanks to the great CI/CD framework, [BuildBot](https://buildbot.net/). In addition, for each commit in repositories that use AppJail images, the image will be recreated and uploaded again. There are only two exceptions:

1. The image is not created if the change contains the `.ajspec` file.
2. The image is not created if the commit message contains the `[SKIP-BUILD]` keyword.

### Building your own images

If for some reason, for example, you see the above problems I have described because the status page is `updating` or you prefer to build your own images for security reasons, you can, and it is easier with [appjail-reproduce](https://github.com/DtxdF/reproduce), just follow the steps below.

```sh
appjail makejail \
    -j hello \
    -f gh+AppJail-makejails/hello \
    -o virtualnet=":<random> default" \
    -o nat -- \
        --hello_ajspec reproduce+hello
```

**Note#1**: The same principle applies to other images, but you must read the README of the project you want to deploy.

**Note#2**: The above steps assume that you have already followed the instructions in the [appjail-reproduce](https://github.com/DtxdF/reproduce) repository.

## Images

All images were built using [AppJail Reproduce](https://github.com/DtxdF/reproduce).

## Deploy

You can deploy a stack of applications using [AppJail Director](https://github.com/DtxdF/director).

## AppJail vs. AppJail (devel)

All these Makejails were created using [sysutils/appjail-devel](https://www.freshports.org/sysutils/appjail-devel) (or the latest version installed using [git(1)](https://man.freebsd.org/cgi/man.cgi?query=git)) to take advantage of the latest features.

## Nodes

New nodes are welcome to provide redundancy. Anything that supports [fetch(1)](https://man.freebsd.org/cgi/man.cgi?query=fetch) is acceptable, such as FTP or HTTP, but the latter is preferable. SFTP is preferred for file management, but anything else you can provide is acceptable. If you are interested, please contact me or join the Telegram group.

**Current Nodes**:

* [HPC.at](http://appjail.hpc.at/)
* [K&T Host](https://images.all101bsd.download/)

**mirror.sh**:

`cd(1)` to your web directory and run the following script. It will recursively download each directory with its files, including the `index.html` file, resulting in an exact copy of the mirror you selected.

```sh
#!/bin/sh

USER_AGENT="Mozilla/5.0 (Windows NT 10.0; rv:124.0) Gecko/20100101 Firefox/124.0"

MIRROR="$1"

if [ -z "${MIRROR}" ]; then
    echo "usage: mirror.sh <HPC|KNT>"
    exit 1
fi

case "$1" in
    HPC) MIRROR_URL="http://appjail.hpc.at" ;;
    KNT) MIRROR_URL="https://images.all101bsd.download" ;;
    *) "$0"; exit 1 ;;
esac

wget --user-agent="${USER_AGENT}" --no-host-directories -N -c -r "${MIRROR_URL}"
```

## How to contribute a new Makejail

New Makejails are welcome. Send Makejail or provide a project that you think can be automated in a useful way in the following means:

* Open a new issue in [AppJail](https://github.com/DtxdF/AppJail/issues/new).
* Telegram Group.
* E-mail.

**Note**: I am very busy, so email is less preferable than other means.

You can create your own repository on your hosting or personal git profile if you prefer, I simply clone and upload it to the Centralized Repository.

### Assumptions

#### Almost all of these Makejails cannot be combined in a single jail

This is because it is preferable to separate the jails by function, this means that if you need, for example, a web server with PHP and DBMS support, you need to create two or three: Apache (with PHP module) and MariaDB or NGINX, PHP-FPM and MariaDB. It is not just a matter of philosophy, technically it is not possible since the `FROM` instruction cannot be used twice and some Makejails are intended to write to a single directory which must not be sharable.

#### Makejails should automate what the project does, not limit to just install it

Think about using a Makejail that just installs the application, like WordPress and doesn't configure it, what's the gain? I know for some projects they are really hard to automate, but with effort I think it is possible. *Wasting hours automating a project to use it in minutes is better than wasting hours installing and configuring it each time*.

#### Be respectful of user preferences unless there is a need not to

This is not to stick to only one network feature that AppJail supports in order to use a project. If a user prefers to use DHCP instead of Virtual Networks, that is the user's problem.

## To bump

Some Makejails require changing the source project version to the new version, so it is necessary to keep track of them.

* [Alpine Linux](https://github.com/AppJail-makejails/alpine-linux/blob/main/update/update.conf)
* [Burp Suite](https://github.com/AppJail-makejails/burpsuite/blob/main/update/update.conf)
* [InvenTree](https://github.com/AppJail-makejails/inventree/blob/main/update/update.conf)
* [AdminerEvo](https://github.com/AppJail-makejails/inventree/blob/main/update/update.conf)
* [MariaDB](https://github.com/AppJail-makejails/mariadb/blob/main/update/update.conf)
* [WordPress](https://github.com/AppJail-makejails/wordpress/blob/main/update/update.conf)
* [PHP](https://github.com/AppJail-makejails/php/blob/main/update/update.conf)
* [File Browser](https://github.com/AppJail-makejails/filebrowser/blob/main/update/update.conf)
* [GO](https://github.com/AppJail-makejails/go/blob/main/update/update.conf)
* [Python](https://github.com/AppJail-makejails/python/blob/main/update/update.conf)
* [Homepage](https://github.com/AppJail-makejails/homepage/blob/main/update/update.conf)
* [Calibre Web](https://github.com/AppJail-makejails/homepage/blob/main/update/update.conf)
* [Lychee](https://github.com/AppJail-makejails/lychee/blob/main/update/update.conf)
