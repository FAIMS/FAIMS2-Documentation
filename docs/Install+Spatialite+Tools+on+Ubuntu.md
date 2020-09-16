Install Spatialite Tools on Ubuntu
===============================================================================





### Installing Spatialite Tools on Ubuntu

Follow these instructions to install Spatialite on Ubuntu.


*Note: This was tested on Ubuntu 12.04.1 LTS.*
=

##### Requirements:

-   install spatialite ([instructions can be found here](../Install+Spatialite+Tools+on+Ubuntu))
-   install packages expat libexpat1-dev zlib1g-dev


```
sudo apt-get install expat libexpat1-dev zlib1g-dev
```


##### Instructions:

-   download and compile [readosm    (1.0.0b)](http://www.gaia-gis.it/gaia-sins/readosm-1.0.0b.tar.gz)


```
wget http://www.gaia-gis.it/gaia-sins/readosm-1.0.0b.tar.gz
tar zxf readosm-1.0.0b.tar.gz
cd readosm-1.0.0b
./configure
make
sudo make install
cd ..
```


-   download and compile [spatialite-tools    (4.1.1)](http://www.gaia-gis.it/gaia-sins/spatialite-tools-4.1.1.tar.gz)


```
wget http://www.gaia-gis.it/gaia-sins/spatialite-tools-4.1.1.tar.gz
tar zxf spatialite-tools-4.1.1.tar.gz
cd spatialite-tools-4.1.1
./configure
make
sudo make install
cd ..
```


##### Usage:

Now you should have access to all the tools.

Some tools may raise errors due to missing file e.g. missing file
libspatialite.so.2. In such cases simply add the appropriate file to
library path.

e.g.


```
sudo ldconfig /usr/local/lib/libspaitalite.so.2
```

</div>
