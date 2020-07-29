FAIMS Mobile Platform Documentation (FAIMS): Installing Spatialite 4 on Ubuntu
==============================================================================

::: {style="font-size:70%; color:#444; font-style: italic"}
Created: Former user (Deleted) () - 2013-08-19T17:45:24.848Z

Last Updated: Former user (Deleted) () - 2013-10-27T11:00:18.398Z
:::

<div>

### Installing Spatialite on Ubuntu {#InstallingSpatialite4onUbuntu-InstallingSpatialiteonUbuntu}

Follow these instructions to install Spatialite  on Ubuntu.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id=""}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
*Note: This was tested on Ubuntu 12.04.1 LTS.*
:::
:::

##### Requirements {#InstallingSpatialite4onUbuntu-Requirements}

-   install packages build-essential, g++

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id=""}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
sudo apt-get install build-essential g++ libc6-dev zlib1g-dev
```
:::
:::

-   Download and install sqlite
    ([3071700](http://www.sqlite.org/2013/sqlite-autoconf-3071700.tar.gz){.external-link})

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id=""}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Note: it is likely going to conflict with sqlite on your system. If you
find a conflict please do before doing ldconfig:

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id=""}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
sudo rm /usr/lib/i386-linux-gnu/*sqlite*
```
:::
:::
:::
:::

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id=""}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
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

##### Instructions: {#InstallingSpatialite4onUbuntu-Instructions:}

-   download and compile [proj4
    (4.8.0)](https://trac.osgeo.org/proj/){.external-link}

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id=""}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
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
    (3.3.8)](https://trac.osgeo.org/geos/){.external-link}

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id=""}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
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
    (1.0.0e)](https://www.gaia-gis.it/fossil/freexl/index){.external-link}

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id=""}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
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
    (4.1.1)](http://www.gaia-gis.it/gaia-sins/libspatialite-sources/libspatialite-4.1.1.tar.gz){.external-link}

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id=""}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
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

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id=""}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
You probably also want to use ldconfig to make sure /usr/local/lib is
included when Ubuntu looks for shared libraries.
:::
:::

##### Testing: {#InstallingSpatialite4onUbuntu-Testing:}

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id=""}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
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

Attachments
-----------
