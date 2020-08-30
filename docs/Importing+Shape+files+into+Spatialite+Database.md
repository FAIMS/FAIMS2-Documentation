Importing Shape files into Spatialite Database
==============================================

### Preface

If the shape files were produced by exporting a module\'s data via the
server, if may not be necessary to import them into a database. The
exporter produces its shape file output using a module\'s spatialite
database as input. In that case, following these steps would merely put
them back into spatialite format. Nonetheless, converting from a
module\'s spatialite database, to shape files, then back again can be
useful if you want each archent to have its own table.

### Requirements

You must have either Ubuntu (recommended) or Windows installed on your
computer to follow this article. The requirements for each are as
follows:

[Ubuntu:]

-   [Installing Spatialite on
    Ubuntu](https://faimsproject.atlassian.net../FAIMS/Installing+Spatialite+4+on+Ubuntu.html)
-   [Installing Spatialite Tools on
    Ubuntu](https://faimsproject.atlassian.net../FAIMS/Install+Spatialite+Tools+on+Ubuntu.html)
-   [Installing GDAL
    Tools](https://faimsproject.atlassian.net../FAIMS/Install+GDAL+Tools.html)

[Windows:]

-   [Installing Spatialite on
    Windows](https://faimsproject.atlassian.net../FAIMS/Installing+Spatialite+on+Windows.html)
-   [Installing Spatialite Tool on
    Windows](https://faimsproject.atlassian.net../FAIMS/Installing+Spatialite+Tool+on+Windows.html)
-   [Installing GDAL Tools on
    Windows](https://faimsproject.atlassian.net../FAIMS/Installing+GDAL+Tools+on+Windows.html)

### 1. Change shape file projection

1.  Change projection of shape file using the following command:


    ```
    $ ogr2ogr -s_srs EPSG:<Shape file projection> -t_srs EPSG:3857 <Output.shp> <Input.shp>
    ```


-   Shape file projection = projection of shape file
-   Input.shp = input shape file
-   Output.shp = output shape file

### 2. Import shape file into spatialite database

1.  Import shape file into spatialite database using the following
    command:


    ```
    $ spatialite_tool -i -shp <Input> -d <SpatialiteDB.sqlite> -t <Table name> -g Geometry -c utf-8 -s 3857
    ```


-   Input.shp = input shape file
-   SpatialiteDB.sqlite = output spatialite database
-   Table name = table to import shape file into


    *Note: You can import multiple shape files into the same spatialite
    database.*


### 3. Adding spatial indexes

1.  Open database file


    ```
    $ sqlite3 <SpatialiteDB.sqlite>
    ```

    Note that to successfully run the above command, sqlite3 must have
    the spatialite extension loaded. If you do not have the spatialite
    extension loaded (e.g. if you installed spatialite following the
    instructions in [Installing Spatialite on
    Windows](https://faimsproject.atlassian.net../FAIMS/Installing+Spatialite+and+Spatialite+Tools+on+Windows.html)),
    you may use the spatialite executable instead. To do so, run the
    above command by replacing `sqlite3` with `spatialite`.\
    \

2.  Create index for each table added


    ```
    > SELECT CreateSpatialIndex('<table>', 'Geometry');
    ```

-   SpatialiteDB.sqlite = spatialite database
-   Table = table name added

</div>
