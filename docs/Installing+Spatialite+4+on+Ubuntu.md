Installing Spatialite 4 on Ubuntu
==============================================================================





### Installing Spatialite on Ubuntu 

Follow these instructions to install Spatialite  on Ubuntu.

::: 
[ ]

::: 
*Note: This was tested on Ubuntu 12.04.1 LTS.*
:::
:::

##### Requirements 

-   install packages build-essential, g++

::: 
::: 
``` 
sudo apt-get install build-essential g++ libc6-dev zlib1g-dev
```
:::
:::

-   Download and install sqlite
    ([3071700](http://www.sqlite.org/2013/sqlite-autoconf-3071700.tar.gz))

::: 
[ ]

::: 
Note: it is likely going to conflict with sqlite on your system. If you
find a conflict please do before doing ldconfig:

::: 
::: 
``` 
sudo rm /usr/lib/i386-linux-gnu/*sqlite*
```
:::
:::
:::
:::

::: 
::: 
``` 
sudo apt-get remove sqlite3 libsqlite3-dev libsqlite3
wget http://www.sqlite.org/2013/sqlite-autoconf-3071700.tar.gz
tar -xzf sqlite-autoconf-3071700.tar.gz 
cd sqlite-autoconf-3071700
./configure
make
sudo make install
sudo ldconfig
cd ..
```
:::
:::

##### Instructions: 

-   download and compile [proj4
    (4.8.0)](https://trac.osgeo.org/proj/)

::: 
::: 
``` 
wget http://download.osgeo.org/proj/proj-4.8.0.tar.gz
tar -xzf proj-4.8.0.tar.gz
cd proj-4.8.0
./configure
make
sudo make install
```
:::
:::

-   download and compile [geos
    (3.3.8)](https://trac.osgeo.org/geos/)

::: 
::: 
``` 
wget http://download.osgeo.org/geos/geos-3.3.8.tar.bz2
tar -xjf geos-3.3.8.tar.bz2
cd geos-3.3.8
./configure
make
sudo make install
sudo ldconfig
cd ..
```
:::
:::

-   download and compile [freexl
    (1.0.0e)](https://www.gaia-gis.it/fossil/freexl/index)

::: 
::: 
``` 
wget http://www.gaia-gis.it/gaia-sins/freexl-sources/freexl-1.0.0e.tar.gz
tar -xzf freexl-1.0.0e.tar.gz
cd freexl-1.0.0e
./configure
make
sudo make install
sudo ldconfig
cd ..
```
:::
:::

-   download and compile [libspatialite
    (4.1.1)](http://www.gaia-gis.it/gaia-sins/libspatialite-sources/libspatialite-4.1.1.tar.gz)

::: 
::: 
``` 
wget http://www.gaia-gis.it/gaia-sins/libspatialite-sources/libspatialite-4.1.1.tar.gz
tar -xzf libspatialite-4.1.1.tar.gz
cd libspatialite-4.1.1
./configure --enable-geocallbacks
make
sudo make install
sudo ldconfig
cd ..
```
:::
:::

::: 
[ ]

::: 
You probably also want to use ldconfig to make sure /usr/local/lib is
included when Ubuntu looks for shared libraries.
:::
:::

##### Testing: 

::: 
::: 
``` 
$ sudo apt-get install rlwrap
$ rlwrap sqlite3
sqlite> select load_extension('libspatialite.so');
sqlite> select sqlite_version(), spatialite_version(), proj4_version(), geos_version()
sqlite_version()  spatialite_version()  proj4_version()           geos_version()  
----------------  --------------------  ------------------------  ----------------
3.7.17            4.1.1                 Rel. 4.8.0, 6 March 2012  3.3.8-CAPI-1.7.8 

sqlite> select InitSpatialMetaData();
sqlite> select distance(makepoint(151.23346, -33.91674, 4326), makepoint(151.20435, -33.86712, 4326));
distance(makepoint(151.23346, -33.91674, 4326), makepoint(151.20435, -33.86712, 4326))
\---------------------------------------------------------------------------------------------;
0.0575285711625093
sqlite> select hasGeoCallBacks();
hasGeoCallBacks()
\--------------------;
1
```
:::
:::

</div>