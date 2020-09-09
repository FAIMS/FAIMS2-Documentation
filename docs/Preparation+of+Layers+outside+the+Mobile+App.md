---
title: Preparation of Layers outside the Mobile App
---


### Raster

The safest format to use with the FAIMS app is a geotiff (georeferenced
image in an uncompressed .tiff format). All rasters need to be uploaded
on the device for them to display. Before uploading it on the device the
file needs to be optimized for display in the app. The optimization
includes (1) defining the file projection, (2) tiling the file, (3)
adding pyramids to the image. (2) and (3) ensure that the file display
is quick and smooth.

For the transformation you need a Linux computer with spatialite and
gdal tools. You need to run the following script in a command
line: [Importing Geotiffs](../Importing+GeoTiffs+into+FAIMS+Android+App)

### Vector

The application support the rendering of legacy vectors (kml,
shapefiles created outside of the application). The transformations
include  (1) defining the projection, (2) importing of the file into
Spatialite database, (3) indexing the database.

See: [Importing Legacy Vectors](../Importing+Shape+files+into+Spatialite+Database)

Once your layers are all prepared you can upload them onto the server
into a designated folder under the project you are working on. The files
will be automatically downloaded onto the mobile devices when you finish
project creation and download the recording module to a device.


</div>
