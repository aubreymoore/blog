<!--
.. title: Setting Up web2py2 on DreamHost
.. slug: setting-up-web2py2-on-dreamhost
.. date: 2017-10-14 19:24:38 UTC+10:00
.. tags:
.. category:
.. link:
.. description:
.. type: text
-->

Reference:
http://www.bikmort.com/dokuwiki/web2py_on_dreamhost
by Tim Korb. Accessed 2017-10-14.

Tim's directions worked very well for me with minor tweaks.

* Create a fully-hosted domain at http://panel.dreamhost.com. I used web2py.guaminsects.net.

* Site configuration options include:
    * Remove WWW from beginning of name
    * use PHP 7.0 FastCGI (default)
    * use HTTPS
    * use Passenger (Click OK on dialog about /public)

* Use a shell account to open a terminal window on your DreamHost server.

        ssh <user>@web2py.guaminsects.net

* Create a virtual python environment in ~/python (could go elsewhere, but remember the path):

        cd ~
        virtualenv python

* Clone sources from the Web2Py github site into a top level directory called web2py:

        git clone --recursive https://github.com/web2py/web2py.git
        cp -a web2py/. web2py.guaminsects.net/

* Copy handlers/wsgihandler.py to passenger_wsgi.py:

        cd web2py.guaminsects.net
        cp handlers/wsgihandler.py passenger_wsgi.py

* Edit passenger_wsgi.py. Insert these two lines at immediately before the line "if not os.path.isdir('applications'):". Note that the INTERP path points to the virtualenv created earlier:

        INTERP = os.path.join(os.environ['HOME'], 'python', 'bin', 'python')
        if sys.executable != INTERP: os.execl(INTERP, INTERP, *sys.argv)

* Create tmp/restart.txt. Touch this file to force relaunch of Web2Py via Passenger:

        mkdir tmp
        touch tmp/restart.txt

* Set an admin password.  This command will give errors (for among other reasons, a user process cannot listen on port 443), but it will have generated the necessary parameters_443.py file.

        python web2py.py -p 443 -a "secret-secure-password"

* The Web2Py environment should now be operational. Visit https://web2py.guaminsects.net to see it.

* Clean up. Delete the top level directory where the web2py git repository was downloaded:

        cd ~
        rm -rf web2py


