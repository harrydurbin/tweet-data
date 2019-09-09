<h2>Data analysis for one million geo-tagged spatial points</h2>
<ul>
<li>Cluster with Minibatch Kmeans</li>
<li>Sub-cluster with DBSCAN</li>
<li>Write data to PSQL/PostGIS database</li>
<li>Import county shapefile and census population data</li>
<li>Querytweets per capita for each county</li>
</ul>
</br>
![alttag](https://github.com/harrydurbin/tweet-data/blob/master/img/points.png)
<br>
caption: geo-tagged tweets in bay area (color per cluster)
<br></br>
![alttag](https://github.com/harrydurbin/tweet-data/blob/master/img/kmeans.png)
caption: initial cluster boundaries after running k-means
<br></br>
![alttag](https://github.com/harrydurbin/tweet-data/blob/master/img/dbscan.png)
caption: final cluster boundaries after running dbscan
<br></br>
![alttag](https://github.com/harrydurbin/tweet-data/blob/master/img/chloropleth.png)
caption: chloropleth indicating tweets per capita for each county
<br></br>
For clustering, a hierarchical approach was used as a work around to memory limitations. One million samples would be too much for DBSCAN to run so points were first clusters broadly using MiniBatch Kmeans to quickly breakdown data into a minimum amount of cluster groups. The MiniBatch Kmeans method works by setting an initial cluster value and iteratively setting a centroid until it converges sufficiently. A limitation for Minibatch Kmeans, is that the number of clusters are arbitrarily picked. Alternatively, the DBSCAN cluster algorithm determines the number of clusters based on a stipulated distance (epsilon). After the initial breakdown of clusters established by Kmeans, DBSCAN was run on each Kmeans cluster to determine a final set of clusters. Clusters containing less than 1,000 tweets were considered insignificant and eliminated.

