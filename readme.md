<h2>Data analysis for one million geo-tagged spatial points</h2>
<ul>
<li>Cluster with Minibatch Kmeans</li>
<li>Sub-cluster with DBSCAN</li>
<li>Write data to PSQL/PostGIS database</li>
<li>Import county shapefile and census population data</li>
<li>Query tweets per capita for each county</li>
</ul>
See iPython Notebooke code <a href="https://github.com/harrydurbin/tweet-data/blob/master/tweets.ipynb">here</a>.
<br><br>
Figure 1: Geo-tagged tweets in bay area (color per cluster)
<img src="../master/img/points.png?raw=true" width="100%"/>
<br>
Figure 2: Final cluster boundaries after running DBSCAN
<img src="../master/img/dbscan.png?raw=true" width="100%"/><br>
<br>
Figure 3: Chloropleth indicating tweets per capita for each county
<img src="../master/img/chloropleth.png?raw=true" width="100%"/><br>
<br>
For clustering, a hierarchical approach was used to overcome memory limitations. One million datapoints is too much for DBSCAN, so first minibatch Kmeans was used to quickly breakdown data into a minimal amount of cluster groups. The minibatch Kmeans cluster method uses a pre-determined number of clusters and iteratively sets a centroid until it converging into equal density clusters. Alternatively, the DBSCAN cluster method uses a stipulated distance (epsilon) to connect datapoints and establish clusters. Clusters containing less than 1,000 tweets were considered insignificant and eliminated.


