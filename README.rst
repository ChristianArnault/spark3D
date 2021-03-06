.. raw:: html

    <img src="https://github.com/JulienPeloton/spark3D/blob/master/pic/spark3d_logo.jpg" height="200px">


Why spark3D?
================

The volume of data recorded by current and
future High Energy Physics & Astrophysics experiments,
and the complexity of their data set require a broad panel of
knowledge in computer science, signal processing, statistics, and physics.
Exact analysis of those data sets produced is a serious computational challenge,
which cannot be done without the help of state-of-the-art tools.
This has to be matched by sophisticated and robust analysis performed on many
powerful machines, as we need to process or simulate several times data sets.

While a lot of efforts have been made to develop cluster computing systems for
processing large-scale spatial 2D data
(see e.g. `GeoSpark <http://geospark.datasyslab.org>`_),
there are very few frameworks to process and analyse 3D data sets
which were hitherto too costly to be processed efficiently.
With the recent development of fast and general engine such as
`Apache Spark <http://spark.apache.org>`_, taking advantage of
distributed systems, we enter in a new area of possibilities.

`spark3D <https://github.com/JulienPeloton/spark3D>`_ extends Apache Spark to
efficiently load, process, and analyze large-scale 3D spatial data sets across machines.

Contributors
================
* Julien Peloton (peloton at lal.in2p3.fr)
* Christian Arnault (arnault at lal.in2p3.fr)

Scenario for manipulating large astronomical data with Apache Spark
=============================================================
We have to distribute the computation for a very large amount of 2D or 3D data, eventually exceeding the memory available 
in our cluster (The Spark cluster).
In addition, the JVM does not allow to create collections beyond 2G elements (due to the fundamental JVM indexing properties based on 32 bits indexes).
Thus we have to construct a pipeline scenario exploiting the iterator mechanisms (both true for Scala and Apache Spark).
Several goals have to be undertaken in this project:

- construct a highly scalable architecture so as to accept very large dataset. (typically greater than what can be handled by practical memory sets) 
- datasets are sets of 3D data, ie. object data contining both 3D information plus additional physics related data.
- méchanisms should offer:
  + indexing mechanisms
  + ways to define a matric (ie. distance between objects) 
  + selection capability of objects or objects within a region
  
Data storage
============
Since the scientific domain considered here is mostly the Atrophysics domain, the natural storage or exchange file format is the FITS format. 
Therefore we consider as part of the problem, the possibility to allow FITS files to be directly injected into the HDFS infrastructure, so as to develop a Spark based applications.

The usual cfitsio software, as welle as the FITS i/o format is not adapted to a distributed file system as HDFS.

Therefore we'll have to develop low level Reader/Writer services, to support direct access to FITS data, without copy nor conversion needs.






