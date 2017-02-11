<!-- 
.. title: Publish Nikola Site on GitHub
.. slug: publish-nikola-site-on-github
.. date: 2017-02-11 10:09:34 UTC+10:00
.. tags: Nikola, github pages
.. category: 
.. link: 
.. description: 
.. type: text
-->

## Publish Nikola Site on GitHub

Publishing my Nikola site on **github pages** was remarkably easy.

* Instructions are found in the Nikola Handbook here: https://getnikola.com/handbook.html#deploying-to-github

* Created a new repo on github called **aubreymoore/blog**
	* IMPORTANT: Go to the settings page for the new repo and enable github pages. The root URL for these pages will be at https://aubreymoore.github.io/blog/

* Created a git repo on my local machine:
~~~python
git init .
git remote add origin git@github.com:aubreymoore/blog.git
~~~

* Pushed my site to github from the command line:
~~~python
nikola github_deploy
~~~
