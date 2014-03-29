MemoServ Integration Script adds basic MemoServ functionality to KVIrc (access to commands and getting emailed when memo(s) are available) for networks supporting the 'ms' shortcut (scripted for Rizon, please tell me when other servers also work). Since I don't have much use for memos (but absolutely wanted to know if someone was trying to communicate with me), this script is very simple, and can do with feature requests if there is demand.

To see if this script will work for you on your network of interest, try the following in the server's console window:

    /ms list

If the server responds with 'Unknown command' then this will not work. Please create a feature request (see later) on the issue tracker if you want your network supported (I'm hoping this will be simple enough to do).

Last updated on 29.03.14 for v1.2.


Installation
============

To load the script into KVIrc (which then persists until you uninstall) and run its startup alias, in a KVIrc console window:

    /parse <path to script file, speechmark-delimited if the path contains spaces>
    /MemoServIntegrationScript::Startup

Once the script is installed, MemoServIntegrationScript::Startup is automatically called when KVIrc is started.


Dependencies
============

Mail command of your choice - I use [sendemail](http://caspian.dotconf.net/menu/Software/SendEmail/), a perl script currently packaged in Debian. This script must be told how to invoke it (see later).


Uninstallation
==============

In a KVIrc console window:

    /MemoServIntegrationScript::uninstall::uninstall


General Configuration
=====================

The 'Scripts' menu is created on the main KVIrc menubar, which then hosts the MemoServ Integration Script menu. This gives you access to the MemoServ commands:

![Script menu](https://f92fac806bf10a96c0b8-8a0a46e5f1a5cc9854958bc3503f0f88.ssl.cf1.rackcdn.com/media_entries/7436/script-menu.png)

At the bottom of this list is the 'Configure email command...' option - The nick blacklisting dialog:

![Configure email command dialog](https://f92fac806bf10a96c0b8-8a0a46e5f1a5cc9854958bc3503f0f88.ssl.cf1.rackcdn.com/media_entries/7437/configure-email-command-dialog.png)

The bottom command should be selectable and copyable once [this feature request](https://svn.kvirc.de/kvirc/ticket/1468) has been merged into KVIrc. In the meantime, the command is:

    /usr/bin/sendemail -f "me@mymailhost.org" -t "to@destinationhost.org" -s "mymailserver.co.uk" -xu "SMTPAuthUsername" -xp "SMTPAuthPassword" -o tls=no -u "%s" -m "%m"

Obviously replace with what you want, and test it in a shell if things appear not to work (you can also see sendemail complain in '~/.xsession-errors' when this script tries to run a bad invocation).


Email Notification
==================

Along with access to commands, this script emails you (after you have configured the mail command) when you receive a memo, or when you log into an IRC server and have unread memos. Currently no attempt is made to fetch memo contents as it is simple for you to just read the memo(s) on the server - the script's main job is to make you aware they are there.


Development
===========

Try out my modification of the [geany](http://www.geany.org/) IDE, extending it to syntax highlight, parse KVIrc Script for aliases, events, variables, shortcut for loading scripts into KVIrc etc: [Github documentation](https://github.com/OmegaPhil/geany-kvircscript/wiki/README---KVIrc-Script-Integration).


Bugs And Feature Requests
=========================

Please create an issue on the [Github issue tracker](https://github.com/OmegaPhil/kvirc-memoserv-integration-script/issues).


Contact Details
===============

OmegaPhil+KVIrc.Script@gmail.com