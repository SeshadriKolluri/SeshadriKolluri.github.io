---
layout: post
title:  "Traveling Salesman Problem - Understanding Through Visualization"
date:   2020-01-31
categories: rnotes
tags: notes
---

Background
----------

A Kaggle competition from 2018

**Goal:** To figure out a travel path for Santa Claus to cover about
200,000 cities, while minimizing the total travel distance

Traveling Salesman Problem: NP-Hard, and exact solution intractable for
more than \~ 30 cities

Can we gain a better understanding through visualization ?

<img src="./TSP_banner.png" style="width:100.0%" />

<table class="table table-striped" style="font-size: 8px; width: auto !important; margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:left;">
CityId
</th>
<th style="text-align:left;">
X
</th>
<th style="text-align:left;">
Y
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
0
</td>
<td style="text-align:left;">
317
</td>
<td style="text-align:left;">
2202
</td>
</tr>
<tr>
<td style="text-align:left;">
1
</td>
<td style="text-align:left;">
4377
</td>
<td style="text-align:left;">
337
</td>
</tr>
<tr>
<td style="text-align:left;">
2
</td>
<td style="text-align:left;">
3454
</td>
<td style="text-align:left;">
2820
</td>
</tr>
<tr>
<td style="text-align:left;">
3
</td>
<td style="text-align:left;">
4688
</td>
<td style="text-align:left;">
2936
</td>
</tr>
<tr>
<td style="text-align:left;">
4
</td>
<td style="text-align:left;">
1011
</td>
<td style="text-align:left;">
3237
</td>
</tr>
<tr>
<td style="text-align:left;">
:
</td>
<td style="text-align:left;">
:
</td>
<td style="text-align:left;">
:
</td>
</tr>
<tr>
<td style="text-align:left;">
:
</td>
<td style="text-align:left;">
:
</td>
<td style="text-align:left;">
:
</td>
</tr>
<tr>
<td style="text-align:left;">
197764
</td>
<td style="text-align:left;">
150
</td>
<td style="text-align:left;">
3135
</td>
</tr>
<tr>
<td style="text-align:left;">
197765
</td>
<td style="text-align:left;">
2615
</td>
<td style="text-align:left;">
2268
</td>
</tr>
<tr>
<td style="text-align:left;">
197766
</td>
<td style="text-align:left;">
4776
</td>
<td style="text-align:left;">
3104
</td>
</tr>
<tr>
<td style="text-align:left;">
197767
</td>
<td style="text-align:left;">
2994
</td>
<td style="text-align:left;">
1932
</td>
</tr>
<tr>
<td style="text-align:left;">
197768
</td>
<td style="text-align:left;">
1355
</td>
<td style="text-align:left;">
3218
</td>
</tr>
</tbody>
</table>
Overview of all the points
--------------------------

<img src="point_plot.png" width="60%" style="display: block; margin: auto;" />

In this problem, all the cities nicely form a reindeer pattern !

Simplest Path: Following the Cities in Order
--------------------------------------------

![](TravelingSalesman_github_files/figure-markdown_github/df_dumbest_path-1.png)

Following cities in the order of CityId is very inefficient ⇒ Let’s sort
them by X and Y.

Better Path: Sorting the Cities by X and Y
------------------------------------------

![](TravelingSalesman_github_files/figure-markdown_github/df_sorted_path-1.png)

Moving orderly from left to right. Still there are many unnecessary
up-down trips.

Sorting the Cities into a Grid
------------------------------

![](TravelingSalesman_github_files/figure-markdown_github/df_grid_path2-1.png)

A grid restricts the path to cover all X-values in a cell, before moving
to next Y-cell.

Sorting the Cities into a Grid
------------------------------

![](TravelingSalesman_github_files/figure-markdown_github/df_grid_path-1.png)

Next opportunity is to cut out long transitions between neighboring
vertical slices.

Sorting the Cities into an Alternating/Zig-Zag Grid
---------------------------------------------------

![](TravelingSalesman_github_files/figure-markdown_github/df_zigzag-1.png)

Going up one Y-slice and coming down the next Y-slice yields a 30%
improvement.

Alternating/Zig-Zag Grid (Full Path)
------------------------------------

![](TravelingSalesman_github_files/figure-markdown_github/df_zigzag_2-1.png)

Strategy so far has been to replace longer trips with shorter trips to
nearby cities.

Further improvement: Nearest Neighbor Path
------------------------------------------

![](TravelingSalesman_github_files/figure-markdown_github/df_nearest-1.png)

Advanced heuristic solvers / local optimization can improve the score
further…

Conclusion
----------

<img src="kaggle_nb_banner.png" width="50%" style="display: block; margin: auto;" />

Explored solutions for the Traveling Salesman Problem through
visualization.

This was the most popular notebook (by vote count) during that Kaggle
competition.

The competition was won by two professors working on TSP for decades,
with a 17% shorter path.
