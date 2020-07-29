FAIMS Mobile Platform Documentation (FAIMS): Importing Shape files into Spatialite Database
===========================================================================================

::: {style="font-size:70%; color:#444; font-style: italic"}
Created: Former user (Deleted) () - 2013-08-19T17:52:11.966Z

Last Updated: Petra Janouchova (Unlicensed) (petra\@fedarch.org) -
2018-06-14T00:35:25.389Z
:::

<div>

Importing Shape files into Spatialite Database {#ImportingShapefilesintoSpatialiteDatabase-ImportingShapefilesintoSpatialiteDatabase}
==============================================

### Preface {#ImportingShapefilesintoSpatialiteDatabase-Preface}

If the shape files were produced by exporting a module\'s data via the
server, if may not be necessary to import them into a database. The
exporter produces its shape file output using a module\'s spatialite
database as input. In that case, following these steps would merely put
them back into spatialite format. Nonetheless, converting from a
module\'s spatialite database, to shape files, then back again can be
useful if you want each archent to have its own table.

### Requirements {#ImportingShapefilesintoSpatialiteDatabase-Requirements}

You must have either Ubuntu (recommended) or Windows installed on your
computer to follow this article. The requirements for each are as
follows:

[Ubuntu:]{.underline}

-   [Installing Spatialite on
    Ubuntu](https://faimsproject.atlassian.net../FAIMS/Installing+Spatialite+4+on+Ubuntu.html)
-   [Installing Spatialite Tools on
    Ubuntu](https://faimsproject.atlassian.net../FAIMS/Install+Spatialite+Tools+on+Ubuntu.html)
-   [Installing GDAL
    Tools](https://faimsproject.atlassian.net../FAIMS/Install+GDAL+Tools.html)

[Windows:]{.underline}

-   [Installing Spatialite on
    Windows](https://faimsproject.atlassian.net../FAIMS/Installing+Spatialite+on+Windows.html)
-   [Installing Spatialite Tool on
    Windows](https://faimsproject.atlassian.net../FAIMS/Installing+Spatialite+Tool+on+Windows.html)
-   [Installing GDAL Tools on
    Windows](https://faimsproject.atlassian.net../FAIMS/Installing+GDAL+Tools+on+Windows.html)

### 1. Change shape file projection {#ImportingShapefilesintoSpatialiteDatabase-1.Changeshapefileprojection}

1.  Change projection of shape file using the following command:

    ::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="258e8f61-c8ac-4cd2-8ff1-619a79dc1c31"}
    ::: {.codeContent .panelContent .pdl}
    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    $ ogr2ogr -s_srs EPSG:<Shape file projection> -t_srs EPSG:3857 <Output.shp> <Input.shp>
    ```
    :::
    :::

-   Shape file projection = projection of shape file
-   Input.shp = input shape file
-   Output.shp = output shape file

### 2. Import shape file into spatialite database {#ImportingShapefilesintoSpatialiteDatabase-2.Importshapefileintospatialitedatabase}

1.  Import shape file into spatialite database using the following
    command:

    ::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="e0c19f72-b74d-4fd0-948b-394ff3572fb4"}
    ::: {.codeContent .panelContent .pdl}
    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    $ spatialite_tool -i -shp <Input> -d <SpatialiteDB.sqlite> -t <Table name> -g Geometry -c utf-8 -s 3857
    ```
    :::
    :::

-   Input.shp = input shape file
-   SpatialiteDB.sqlite = output spatialite database
-   Table name = table to import shape file into

    ::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="3d6d5a47-1d60-43c3-9e40-44872c34c728"}
    [ ]{.aui-icon .aui-icon-small .aui-iconfont-info
    .confluence-information-macro-icon}
    ::: {.confluence-information-macro-body}
    *Note: You can import multiple shape files into the same spatialite
    database.*
    :::
    :::

### 3. Adding spatial indexes {#ImportingShapefilesintoSpatialiteDatabase-3.Addingspatialindexes}

1.  Open database file

    ::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="7613bba2-f938-46dc-9c9b-035650e3b464"}
    ::: {.codeContent .panelContent .pdl}
    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    $ sqlite3 <SpatialiteDB.sqlite> 
    ```
    :::
    :::

    Note that to successfully run the above command, sqlite3 must have
    the spatialite extension loaded. If you do not have the spatialite
    extension loaded (e.g. if you installed spatialite following the
    instructions in [Installing Spatialite on
    Windows](https://faimsproject.atlassian.net../FAIMS/Installing+Spatialite+and+Spatialite+Tools+on+Windows.html)),
    you may use the spatialite executable instead. To do so, run the
    above command by replacing `sqlite3` with `spatialite`.\
    \

2.  Create index for each table added

    ::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="9645744e-39ec-465b-b649-75a295ea9c82"}
    ::: {.codeContent .panelContent .pdl}
    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    > SELECT CreateSpatialIndex('<table>', 'Geometry');
    ```
    :::
    :::

-   SpatialiteDB.sqlite = spatialite database
-   Table = table name added

</div>

Attachments
-----------
