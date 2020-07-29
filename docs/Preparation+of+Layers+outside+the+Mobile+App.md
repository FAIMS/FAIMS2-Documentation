FAIMS Mobile Platform Documentation (FAIMS): Preparation of Layers outside the Mobile App
=========================================================================================

::: {style="font-size:70%; color:#444; font-style: italic"}
Created: Former user (Deleted) () - 2013-08-19T21:47:11.534Z

Last Updated: Adela Sobotkova (adela\@faims.edu.au) -
2013-08-19T22:00:19.507Z
:::

<div>

### [Raster]{style="color: rgb(102,102,102);"} {#PreparationofLayersoutsidetheMobileApp-Raster}

[The safest format to use with the FAIMS app is a geotiff (georeferenced
image in an uncompressed .tiff format). All rasters need to be uploaded
on the device for them to display. Before uploading it on the device the
file needs to be optimized for display in the app. The optimization
includes (1) defining the file projection, (2) tiling the file, (3)
adding pyramids to the image. (2) and (3) ensure that the file display
is quick and smooth.]{style="color: rgb(0,0,0);"}

[For the transformation you need a Linux computer with spatialite and
gdal tools. You need to run the following script in a command
line]{style="color: rgb(0,0,0);"}:[ [Importing
]{style="line-height: 1.4285715;"}Geotiffs](../FAIMS/Importing+GeoTiffs+into+FAIMS+Android+App.html)

### [Vector]{style="color: rgb(102,102,102);"} {#PreparationofLayersoutsidetheMobileApp-Vector}

[The application support the rendering of legacy vectors (kml,
shapefiles created outside of teh application). The transformations
include  (1) defining the projection, (2) importing of the file into
Spatialite database, (3) indexing the
database]{style="color: rgb(0,0,0);"}

See: [Importing Legacy
Vectors](../FAIMS/Importing+Shape+files+into+Spatialite+Database.html)

[Once your layers are all prepared you can upload them onto the server
into a designated folder under the project you are working on. The files
will be automatically downloaded onto the mobile devices when you finish
project creation and download the recording module to a device.
]{style="color: rgb(0,0,0);"}

</div>

Attachments
-----------
