<!-- 
.. title: Tweeking Nikola CSS to Improve Table Display
.. slug: tweeking-nikola-css-to-improve-table-display
.. date: 2017-02-20 19:28:56 UTC+10:00
.. tags: Nikola, css
.. category: 
.. link: 
.. description: 
.. type: text
-->

Crappy default styling of tables was fixed by adding this file:

**~nik/mysite/files/assets/css/custom.css** **
~~~css
/* Tweeks by Aubrey Moore */

td {
	padding: 15px;
}

th {
	text-align: center;
	padding: 15px;
}

tr:nth-child(even){background-color: #f2f2f2}
~~~



