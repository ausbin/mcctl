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

    $ git clone git://github.com/ausbin/mcctl.git mcctl
    $ cd mcctl
    # install -Dm 755 mcctl /usr/bin/mcctl
    # install -Dm 755 mcctl.conf /etc/mcctl/mcctl.conf

If you're an Arch user, download the [PKGBUILD](https://raw.github.com/ausbin/mcctl/master/PKGBUILD) and run `makepkg`.

config
------

The configuration file (`/etc/mcctl/mcctl.conf`) is heavily commented and full of examples, but there are still a few things worth noting:

1. **If you're using craftbukkit**, set `$niceprompt` to 1. Craftbukkit has a nice readline-style prompt that, among other features, allows the prompt to be cleared before commands are sent.
2. Keep in mind that if you modify `$mcuser` or `$mcsession` while the server is running, screen may be unable to find the session.
3. Similarly, changing `$invocation` while the server is running will result in mcctl being unable to find the server process.

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
