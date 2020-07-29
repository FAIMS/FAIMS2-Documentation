FAIMS Mobile Platform Documentation (FAIMS): Importing GeoTiffs into FAIMS Android App
======================================================================================

::: {style="font-size:70%; color:#444; font-style: italic"}
Created: Former user (Deleted) () - 2013-08-19T17:51:23.901Z

Last Updated: Shawn Ross (shawn\@faims.edu.au) -
2018-04-23T00:38:39.133Z
:::

<div>

Importing GeoTiffs into FAIMS Android App {#ImportingGeoTiffsintoFAIMSAndroidApp-ImportingGeoTiffsintoFAIMSAndroidApp}
=========================================

### Requirements {#ImportingGeoTiffsintoFAIMSAndroidApp-Requirements}

-   [Installing Spatialite on
    Ubuntu](https://wiki.intersect.org.au/display/FAIMS/Installing+Spatialite+on+Ubuntu){.external-link}
-   [Installing Spatialite Tools on
    Ubuntu](https://wiki.intersect.org.au/display/FAIMS/Installing+Spatialite+Tools+on+Ubuntu){.external-link}
-   [Installing GDAL
    Tools](https://wiki.intersect.org.au/display/FAIMS/Installing+GDAL+Tools){.external-link}
-   [Install GRASS GIS](http://grass.osgeo.org/){.external-link}

### Change GeoTiff projection {#ImportingGeoTiffsintoFAIMSAndroidApp-ChangeGeoTiffprojection}

1.  Change the original GeoTiff projection to 3857 for proper rendering
    in FAIMS v2.5 using the following command in your Unix shell ( in
    Windows, use Bash shell, not windows command line). Copy the code
    below (skip the \$ symbol) and paste into your prompt:

    ::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="cafb1eb7-b587-4f03-86af-8a1dd09bf86e"}
    ::: {.codeContent .panelContent .pdl}
    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    $ gdalwarp -s_srs EPSG:<GeoTiff Projection> -t_srs EPSG:3857 <Input.tif> <Output.tif>
    ```
    :::
    :::

-   -s\_srs = refers to source projection
-   -t\_srs = refers to target projection
-   \<\>  = items in brackets need to be replaced with values, remove
    the brackets when replacing.
-   \<GeoTiff Projection\> = refers to the datum and projection of the
    source GeoTiff, communicated as a single EPSG number (go to
    www.spatialreference.org if you need to find the right code for your
    datum and projection )
-   \<Input.tif\> = refers to the input GeoTiff filename including the
    extension. Replace the entire string, e.g. KatoombaTopo.tif without
    brackets around it. 
-   \<Output.tif\> = refers to the output GeoTiff filename including the
    extension

-   a full example is: gdalwarp -s\_srs EPSG:28356 -t\_srs EPSG:3857
    JamisonTopo.tif Jam3857.tif 

    ::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="d5edf196-b363-46cc-865a-22dfdd940119"}
    [ ]{.aui-icon .aui-icon-small .aui-iconfont-info
    .confluence-information-macro-icon}
    ::: {.confluence-information-macro-body}
    *Note: This can sometimes fail due to versions of libraries
    installed. If the resulting GeoTiff is not properly reprojected then
    install gdal-bin package from ubuntu software center and retry.*
    :::
    :::

### Importing GeoTiffs into GRASS {#ImportingGeoTiffsintoFAIMSAndroidApp-ImportingGeoTiffsintoGRASS}

1.  Run grass from command line.
2.  Create location in same projection as GeoTiff.
3.  Use default mapset and create your own mapset.
4.  Start grass session.
5.  Import GeoTiff into grass using File \> Import raster Data \> Common
    import formats.
6.  Choose GeoTiff to import and click Import button.

    ::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="400ac2c7-d3f7-4ffb-8575-4452c8069c6d"}
    [ ]{.aui-icon .aui-icon-small .aui-iconfont-info
    .confluence-information-macro-icon}
    ::: {.confluence-information-macro-body}
    *Note: if import GeoTiff fails then the most likely reason is
    because its not in the same projection as the grass location
    specified in step 2. If this is the case then create a new location
    in the same projection as the GeoTiff.*
    :::
    :::

### Exporting GeoTiffs from GRASS {#ImportingGeoTiffsintoFAIMSAndroidApp-ExportingGeoTiffsfromGRASS}

1.  If maps aren\'t loaded then goto File \> Workspace \> Load map
    layers and load the geotiffs
2.  In map layers window select geotiff to export and right click
    geotiff and select Set computational region from selected maps(s).

    ::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="c242312e-17ef-446e-9228-bc4b36b8b571"}
    [ ]{.aui-icon .aui-icon-small .aui-iconfont-info
    .confluence-information-macro-icon}
    ::: {.confluence-information-macro-body}
    *Note: This tells GRASS the region you want to export.*
    :::
    :::

3.  Now export the GeoTiff using File \> Export raster map \> Common
    export formats.
4.  Select the raster you want to export and give an output filename and
    click the run button.

### Adding Tiling to GeoTiff {#ImportingGeoTiffsintoFAIMSAndroidApp-AddingTilingtoGeoTiff}

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="1b002580-eb13-4f13-8b70-e455de9b2ea8"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Note: the FAIMS android app currently does not tile rasters, so if tiles
are needed for rendering large files, they need to be added outside the
app using the following line of code.
:::
:::

1.  Add tiling to the GeoTiff by copying the code after the \$ and
    pasting into your shell. Edit the items in brackets:

    ::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c584206d-6704-4037-b4f1-bbc8a08eca26"}
    ::: {.codeContent .panelContent .pdl}
    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    $ gdalwarp -co TILED=YES <Input.tif> <Output.tif>
    ```
    :::
    :::

-   \<\>  = items in brackets need to be replaced with values
-   Input.tif = refers to the input GeoTiff filename (including the
    extension)
-   Output.tif = refers to the output GeoTiff filename (including the
    extension)

### Adding Pyramids to GeoTiff {#ImportingGeoTiffsintoFAIMSAndroidApp-AddingPyramidstoGeoTiff}

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="baf6b8e7-e33f-40fd-a33b-0bf7177189cb"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
Note: the FAIMS android app currently does not support pyramids, so if
pyramids are needed for rendering large files, they need to be added
outside the app using the following line of codes.
:::
:::

1.  Add Pyramids to the GeoTiff by copying the code after the \$ and
    pasting into your shell. Edit the items in brackets:

    ::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="15861bc8-0f13-47ae-ad2b-e2f5b766da55"}
    ::: {.codeContent .panelContent .pdl}
    ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
    $ gdaladdo -r nearest <Input.tif> 2 4 8 16 32 64 128 256 512 1024 2048 4096 8192
    ```
    :::
    :::

-   Input.tif = refers to the input GeoTiff filename (including the
    extension)

</div>

Attachments
-----------
