mcctl
=====

mcctl is a bash script that greatly simplifies administering a minecraft server. It's like apachectl except for minecraft. 

Licensed under the GPL2.

dependencies
------------

* bash 4.0+
* gnu screen
* sudo (if you want to start/stop/restart the server as a different user)

installation
------------

Installation is pretty straightforward:

    $ git clone git://github.com/UncleNinja/mcctl.git mcctl
    $ cd mcctl
    # install -Dm 755 mcctl /usr/bin/mcctl
    # install -Dm 755 mcctl.conf /etc/mcctl/mcctl.conf

If you're an Arch user, download the [PKGBUILD](https://raw.github.com/UncleNinja/mcctl/master/PKGBUILD) and run `makepkg`.

usage
-----

* Get the server console: `mcctl console`
* Start the server: `mcctl start`
* Save and stop the server: `mcctl stop`
* Just stop the server: `mcctl rawstop`
* Restart the server: `mcctl restart`
* Restart the server without saving the level: `mcctl rawrestart`
* Save the server: `mcctl save`
* Force the server to stop (sigint/sigkill): `mcctl forcestop`
* Run a command on the server: `mcctl cmd say bacon`
* Get the process id of the server (no output if not running): `mcctl pid`
* Allow the users from `$allowusers` and `$allowgroup` to access the console's screen session: `mcctl flushusers`
