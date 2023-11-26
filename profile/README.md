# AppJail Makejails

Welcome to the centralized repository, here you can find some useful Makejails to deploy cool projects.

github.com/DtxdF/AppJail

<img src="https://avatars.githubusercontent.com/u/124508626?s=200&v=4" width="30%" height="auto">

## Status

**Current Status**: `updating`

Every week I update the images of all the projects to provide security updates or simply update dependencies. When doing these updates I try to automate everything, but in some other operations I have to update manually, namely when updating ajspec files. I am actively working to automate everything.

What the status means is the assumption that you should do.

* `safe`: I am not updating images, so everything should work correctly.
* `updating`: I am updating images, this means that when I upload files I overwrite the old files with the new ones, so the checksum may not match, the file cannot be found, etc. In many cases this is fixed very quickly.

## Images

All images were built using [AppJail Reproduce](https://github.com/DtxdF/reproduce).

## Deploy

You can deploy a stack of applications using [AppJail Director](https://github.com/DtxdF/director).

## Nodes

New nodes are welcome to provide redundancy. Anything that supports [fetch(1)](https://man.freebsd.org/cgi/man.cgi?query=fetch) is acceptable, such as FTP or HTTP, but the latter is preferable. SFTP is preferred for file management, but anything else you can provide is acceptable. If you are interested, please contact me or join the Telegram group.

**Current Nodes**:

* [HPC.at](http://appjail.hpc.at/)
* [K&T Host](https://images.all101bsd.download/)
* [Google Drive](https://drive.google.com/drive/folders/1GSU3EqDwPH1Q_08Xbcwc0c4b5XcJ7TJd)

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
