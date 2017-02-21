<!-- 
.. title: Install web2py in a Conda Virtual Environment
.. slug: play-pen
.. date: 2017-02-21 13:01:06 UTC+10:00
.. tags: web2py, virtualenv, python, Anaconda
.. category: 
.. link: 
.. description: 
.. type: text
-->

Here's how to get **web2py** installed in a virtual environment using **conda** instead of **virtualenv**.

Info on **conda environments** is available here: 
https://uoa-eresearch.github.io/eresearch-cookbook/recipe/2014/11/20/conda/

## Step 1. Create a directory for our web2py project.
~~~sh
cd Devel
mkdir playpen
cd playpen
~~~

## Step 2. Create a virtual environment and activate it.
Note that **web2py** runs under python 2, not python 3.
~~~sh
conda create -n playpen python=2.7
source activate playpen
~~~

## Step 3. Download and install web2py.
~~~sh
wget https://mdipierro.pythonanywhere.com/examples/static/web2py_src.zip
unzip web2py_src.zip
rm web2py_src.zip
~~~

## Step 3. Install pygraphwiz (used to visualize models).
~~~sh
pip install pygraphviz
~~~

## Step 4. At the end of a session, the virtual environment can be deactivated.
~~~sh
source deactivate playpen
~~~

## Step 5. To undo everything:
~~~sh
conda remove -n playpen --all
cd ..
rm -rf playpen
~~~



