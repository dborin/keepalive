keepalive
=========

This is a Mac OS X VPN tool.

####keepalive

As the name implies, it will keep a VPN session alive by sending pings and a cURL request every two minutes.

Since I developed this while working at LivingSocial, my default URI is:

`code.livingsocial.net`

and the default maximum length it will run (in seconds):

`259200`

That's three days for those not wanting to do math

    Usage: keepalive [-ut]

      OPTIONS:
        -u <URI>  specify URI (FQDN) to cURL and ping.  URI only (no http://) [OPTIONAL]
                  DEFAULT: code.livingsocial.net

        -t <TIME> Maximum runtime in seconds [OPTIONAL]
                  DEFAULT: 259200 == 3 days
                  
####keepalive_screen

This is the screen application.  You can either start a detached screen session that runs the keepalive script, or shut down all screen sessions label 'keepalive'

    Usage: keepalive_screen.sh [-ksutq]

      OPTIONS:
        -k        Kill all screen sessions with label 'keepalive'

        -s        Start a screen session labeled 'keepalive' and run the keepalive script

        -u <URI>  specify URI (FQDN) to cURL and ping.  URI only (no http://) [OPTIONAL]
                  DEFAULT: code.livingsocial.net

        -t <TIME> Maximum runtime in seconds [OPTIONAL]
                  DEFAULT: 259200 == 3 days

        -q        Quiet -- do not return screen status after startup or kill

####keepalive.app

This is the AppleScript that will automagically detect your existing VPN connections, pop-up with a selector (it will remember your selection the next time), and then automagically start the VPN client with your selected VPN.

You'll still need any authentication mechanism (i.e. RSA token), but once you've authenticated, the `keepalive` script will run and in theory, you should have an open VPN connection for 3 days.

If you run the app again, it will kill your VPN session AND the `keepalive` session.

I use [Quicksilver](http://qsapp.com/) and I've configured a keyboard trigger (shortcut) so I can start and stop all of this with a handy key combination.

####keepalive_install

Pretty self explanatory.  Run it and it will copy the two shell scripts to `/usr/local/bin/`.  This is of course assuming that you're using the standard Mac OS X $PATH value.  If not, you'll need to add `/usr/local/bin/` to your path.  `keepalive.app` gets copied to /Applications

<hr>
Please let me know if something is very wrong and I'll try my best to fix it.