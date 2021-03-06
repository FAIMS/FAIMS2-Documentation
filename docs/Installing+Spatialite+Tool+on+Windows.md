---
title: Installing Spatialite Tool on Windows
---


*Note: This was tested on Windows 10.*


1.  Download the zip file which contains the [spatialite tool binaries](http://www.gaia-gis.it/gaia-sins/windows-bin-x86/).
2.  Extract the contents of the downloaded zip file to a directory
    called **`C:\Program Files (x86)\Spatialite Tool`**. (You will
    probably have to make this directory.) After completing this step,
    there should be a file at
    **`C:\Program Files (x86)\Spatialite Tool\spatialite_tool.exe`**.
3.  Once the installer is finished, add the directory
    **`C:\Program Files (x86)\Spatialite Tool`** to your system path. A
    tutorial for adding directories to your system path can be found
    [here](https://www.howtogeek.com/118594/how-to-edit-your-system-path-for-easy-command-line-access/).
4.  Test your installation by opening a new Command Prompt window,
    typing `spatialite_tool --help` and pressing enter. If you see
    something like the following, installation was successful:


```
    C:\Users\mq20151400>spatialite_tool --help


    usage: spatitalite_tool CMD ARGLIST
    ==============================================================
    CMD has to be one of the followings:
    ------------------------------------
    -h or --help                      print this help message
    -i or --import                    import [CSV/TXT, DBF or SHP]
    -e or --export-shp                exporting some shapefile

    supported ARGs are:
    -------------------
    -dbf or --dbf-path pathname       the full DBF path
    -shp or --shapefile pathname      the shapefile path [NO SUFFIX]
    -d or --db-path pathname          the SpatiaLite db path
    -t or --table table_name          the db geotable
    -g or --geometry-column col_name  the Geometry column
    -c or --charset charset_name      a charset name
    -s or --srid SRID                 the SRID
    --type         [POINT | LINESTRING | POLYGON | MULTIPOINT]

    optional ARGs for SHP import are:
    ---------------------------------
    -2 or --coerce-2d                  coerce to 2D geoms [x,y]
    -k or --compressed                 apply geometry compression

    examples:
    ---------
    spatialite_tool -i -dbf abc.dbf -d db.sqlite -t tbl -c CP1252
    spatialite_tool -i -shp abc -d db.sqlite -t tbl -c CP1252 [-s 4326] [-g geom]
    spatialite_tool -i -shp abc -d db.sqlite -t tbl -c CP1252 [-s 4326] [-2] [-k]
    spatialite_tool -e -shp abc -d db.sqlite -t tbl -g geom -c CP1252 [--type POINT]

```
