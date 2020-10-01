---
title: Install GDAL Tools
---

Install GDAL Tools
===============================================================





### Installing GDAL Tools

Follow these instructions to install GDAL Tools on Ubuntu.


*Note: This was tested on Ubuntu 12.04.1 LTS.*

##### Requirements:

-   This assumes you have installed [Spatialite](../Install+GDAL+Tools)

##### Instructions:

-   Download and compile [gdal (1.10.0)](http://download.osgeo.org/gdal/1.10.0/gdal-1.10.0.tar.gz)


```
wget http://download.osgeo.org/gdal/1.10.0/gdal-1.10.0.tar.gz
tar zxf gdal-1.10.0.tar.gz
cd gdal-1.10.0
./configure
make
sudo make install
cd ..
```

You probably also want to use ldconfig to make sure /usr/local/lib is
included when Ubuntu looks for shared libraries.


</div>
