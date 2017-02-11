<!-- 
.. title: Failed Attempt to Run wep2py on Dreamhost
.. slug: failed-attempt-to-run-wep2py-on-dreamhost
.. date: 2017-02-11 09:28:41 UTC+10:00
.. tags: web2py,DreamHost,PythonAnywhere
.. category: 
.. link: 
.. description: 
.. type: text
-->

# Failed Attempt to Run wep2py on Dreamhost
Saturday, 11. February 2017 06:37AM 

* SSH to DreamHost shared hosting.
* Run python. Version is 2.7.3
* virtualenv is available

## Create virtualenv
* Reference http://docs.python-guide.org/en/latest/dev/virtualenvs/
~~~python
mkdir my_project_folder
cd my_project_folder
virtualenv venv
source venv/bin/activate
pip install requests
deactivate
~~~

## Download web2py
~~~python
wget https://mdipierro.pythonanywhere.com/examples/static/web2py_src.zip
unzip web2py_src.zip
rm web2py_src.zip
~~~

## First Attempt
~~~python
(venv)aubreymoore@cactus:~/my_project_folder $ cd web2py
(venv)aubreymoore@cactus:~/my_project_folder/web2py $ ls
CHANGELOG  LICENSE  MANIFEST.in  NEWINSTALL  README.markdown  VERSION  anyserver.py  applications  examples  extras  gluon  handlers  scripts  site-packages  web2py.py
(venv)aubreymoore@cactus:~/my_project_folder/web2py $ python web2py.py
web2py Web Framework
Created by Massimo Di Pierro, Copyright 2007-2017
Version 2.14.6-stable+timestamp.2016.05.10.00.21.47
Database drivers available: sqlite3, imaplib, pyodbc, pymysql, pg8000
WARNING:web2py:GUI not available because Tk library is not installed
choose a password:

please visit:
	http://127.0.0.1:8000/
use "kill -SIGTERM 28797" to shutdown the web2py server
~~~
* wep2py seems to run properly, but the local server it sets up is inaccessable

## Helpful Sites
* https://groups.google.com/forum/#!topic/web2py/nixNhDrxHtQ

## Seems Overly Complicated - Give Up and Deploy to pythonanywhere

* to clean up, we simply delete my_project_folder
~~~python
cd ~
rm -rf my_project_folder
~~~





	
	
