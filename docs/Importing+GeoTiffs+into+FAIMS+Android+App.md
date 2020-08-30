Importing GeoTiffs into FAIMS Android App
======================================================================================



Importing GeoTiffs into FAIMS Android App
=========================================

### Requirements

-   [Installing Spatialite on
    Ubuntu](https://wiki.intersect.org.au/display/FAIMS/Installing+Spatialite+on+Ubuntu)
-   [Installing Spatialite Tools on
    Ubuntu](https://wiki.intersect.org.au/display/FAIMS/Installing+Spatialite+Tools+on+Ubuntu)
-   [Installing GDAL
    Tools](https://wiki.intersect.org.au/display/FAIMS/Installing+GDAL+Tools)
-   [Install GRASS GIS](http://grass.osgeo.org/)

### Change GeoTiff projection

1.  Change the original GeoTiff projection to 3857 for proper rendering
    in FAIMS v2.5 using the following command in your Unix shell ( in
    Windows, use Bash shell, not windows command line). Copy the code
    below (skip the \$ symbol) and paste into your prompt:


    ```
    $ gdalwarp -s_srs EPSG:<GeoTiff Projection> -t_srs EPSG:3857 <Input.tif> <Output.tif>
    ```


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


    *Note: This can sometimes fail due to versions of libraries
    installed. If the resulting GeoTiff is not properly reprojected then
    install gdal-bin package from ubuntu software center and retry.*


### Importing GeoTiffs into GRASS

1.  Run grass from command line.
2.  Create location in same projection as GeoTiff.
3.  Use default mapset and create your own mapset.
4.  Start grass session.
5.  Import GeoTiff into grass using File \> Import raster Data \> Common
    import formats.
6.  Choose GeoTiff to import and click Import button.


    *Note: if import GeoTiff fails then the most likely reason is
    because its not in the same projection as the grass location
    specified in step 2. If this is the case then create a new location
    in the same projection as the GeoTiff.*


### Exporting GeoTiffs from GRASS

1.  If maps aren\'t loaded then goto File \> Workspace \> Load map
    layers and load the geotiffs
2.  In map layers window select geotiff to export and right click
    geotiff and select Set computational region from selected maps(s).


    *Note: This tells GRASS the region you want to export.*

3.  Now export the GeoTiff using File \> Export raster map \> Common
    export formats.
4.  Select the raster you want to export and give an output filename and
    click the run button.

### Adding Tiling to GeoTiff


Note: the FAIMS android app currently does not tile rasters, so if tiles
are needed for rendering large files, they need to be added outside the
app using the following line of code.


1.  Add tiling to the GeoTiff by copying the code after the \$ and
    pasting into your shell. Edit the items in brackets:


    ```
    $ gdalwarp -co TILED=YES <Input.tif> <Output.tif>
    ```



-   \<\>  = items in brackets need to be replaced with values
-   Input.tif = refers to the input GeoTiff filename (including the
    extension)
-   Output.tif = refers to the output GeoTiff filename (including the
    extension)

### Adding Pyramids to GeoTiff

Note: the FAIMS android app currently does not support pyramids, so if
pyramids are needed for rendering large files, they need to be added
outside the app using the following line of codes.



1.  Add Pyramids to the GeoTiff by copying the code after the \$ and
    pasting into your shell. Edit the items in brackets:


    ```
    $ gdaladdo -r nearest <Input.tif> 2 4 8 16 32 64 128 256 512 1024 2048 4096 8192
    ```

-   Input.tif = refers to the input GeoTiff filename (including the
    extension)

</div>
