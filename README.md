MemoServ Integration Script adds basic MemoServ functionality to KVIrc (access to commands and getting emailed when memo(s) are available) for networks supporting the 'ms' shortcut (scripted for Rizon, please tell me when other servers also work). Since I don't have much use for memos (but absolutely wanted to know if someone was trying to communicate with me), this script is very simple, and can do with feature requests if there is demand.

To see if this script will work for you on your network of interest, try the following in the server's console window:

    /ms list

If the server responds with 'Unknown command' then this will not work. Please create a feature request (see later) on the issue tracker if you want your network supported (I'm hoping this will be simple enough to do).

Last updated on 4.11.14 for v1.3.


Installation
============

v1.3+ requires KVIrc 4.3.1 r6393 or higher due to a KVIrc Script change - for all I know I'm the only user of this script, if you have an earlier version of KVIrc and want to use this script, please open an issue on Github (see 'Bugs And Feature Requests' later) and I will try to work something out.

To load the script into KVIrc (which then persists until you uninstall) and run its startup alias, first disable 'User friendly command-line mode' (it prevents the parse command from working):

In a KVIrc console window, look at the bottom right - on the far right of the text entry widget, you'll see an arrow button. Press to expand, then press the 3rd button from the left - normal KVS command mode is now active, and the parse command below works:

    /parse <path to script file, speechmark-delimited if the path contains spaces>
    /MemoServIntegrationScript::Startup

Once the script is installed, MemoServIntegrationScript::Startup is automatically called when KVIrc is started.

You can turn back on 'User friendly command-line mode' if you want, its a per-window setting.


Dependencies
============

Optionally a mail command of your choice - I use [sendemail](http://caspian.dotconf.net/menu/Software/SendEmail/), a perl script currently packaged in Debian. This script must be told how to invoke it (see later) - if you don't configure a command, the script will complain when it detects memos.


Uninstallation
==============

In a KVIrc console window:

    /MemoServIntegrationScript::uninstall::uninstall


General Use And Configuration
=============================

The 'Scripts' menu is created on the main KVIrc menubar, which then hosts the MemoServ Integration Script menu. This gives you access to the MemoServ commands:

![Script menu](https://f92fac806bf10a96c0b8-8a0a46e5f1a5cc9854958bc3503f0f88.ssl.cf1.rackcdn.com/media_entries/7436/script-menu.png)

'Send memo to registered user on <network\>' pops up the following dialog:

![Send memo to registered user dialog](https://f92fac806bf10a96c0b8-8a0a46e5f1a5cc9854958bc3503f0f88.ssl.cf1.rackcdn.com/media_entries/7438/send-memo-to-registered-user-dialog.png)

The 'Check Nick' button allows you to quickly run an 'ns info' command to ensure the recipient is a registered nick - see the server's console window for results. This won't work on networks that don't support the 'ns' shortcut - do such networks exist that support ms but not ns?

At the bottom of this list is the 'Configure email command...' option:

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

OmegaPhil@startmail.com
