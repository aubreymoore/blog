<!--
.. title: Calculate geographical coordinates for equidistant points at vertices of a triangular grid
.. slug: calculate-geographical-coordinates-for-equidistant-points-at-vertices-of-a-triangular-grid
.. date: 2017-05-28 09:33:46 UTC+10:00
.. tags: GIS GPS KML
.. category:
.. link:
.. description:
.. type: text
-->

I needed to set up a grid of equally spaced insect pheromone traps. While it is
convenient to put traps at the vertices of a rectangular grid, this is not
optimal because nearest neighbors on the diagonals are further away than those
within rows or columns (If the spacing within rows and columns is X, then the
diagonal spacing is sqrt(0.75)*X).  For equidistant spacing, points are placed
at vertices of a grid made with equilateral triangles. This python script
returns such a grid of points and returns the data as a KML file containing
latitude/longitude coordinates in decimal degrees.

<script src="https://gist.github.com/aubreymoore/7f3688e88556e08a8069623ecf48b68f.js"></script>

The KML file may be displayed using Google Earth.

![example output](/images/points.jpg)
