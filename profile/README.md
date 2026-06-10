# AppJail Makejails

Welcome to the centralized repository, here you can find some useful Makejails to deploy cool projects.

github.com/DtxdF/AppJail

<img src="https://avatars.githubusercontent.com/u/124508626?s=200&v=4" width="30%" height="auto">

## Status

Every 21 days, all OCI images are updated via a GitHub workflow using [dbuild](https://freshports.org/sysutils/py-dbuild) and distributed through the GitHub registry.

We are currently migrating from AppJail images to OCI images. AppJail images can no longer be downloaded, as the mirror is no longer operational.

As an alternative, you can deploy OCI images from [daemonless.io](https://daemonless.io) using AppJail.

## Deploy

You can deploy a stack of applications using [AppJail Director](https://github.com/DtxdF/director).

## AppJail vs. AppJail (devel)

All these Makejails were created using [sysutils/appjail-devel](https://www.freshports.org/sysutils/appjail-devel) (or the latest version installed using [git(1)](https://man.freebsd.org/cgi/man.cgi?query=git)) to take advantage of the latest features.

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

Think about using a Makejail that just installs the application, like WordPress and doesn't configure it, what's the gain? I know for some projects that are really hard to automate, but with effort I think it is possible. *Wasting hours automating a project to use it in minutes is better than wasting hours installing and configuring it each time*.

#### Be respectful of user preferences unless there is a need not to

This is not to stick to only one network feature that AppJail supports in order to use a project. If a user prefers to use DHCP instead of Virtual Networks, that is the user's problem.
