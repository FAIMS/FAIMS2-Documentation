---
title: Known Issues and Limitations
---


This page was requested by Brian to detail known limitations of the
hardware and software associated with FAIMS. (This includes all known
bugs within the FAIMS system as of 29/10/2013)

### Tablet Software:

-   Android 4.0.3 on the Samsung 10"  does not work (supported Android
    versions are only those from 4.4.X upwards)
-   Android 4.1.2 Crashes due to insufficient ram allocations (even if
    the device "has" enough ram)
-   Samsung note 10.1 - the native video recorder does not record any
    video when using the default application, requiring the user to
    download an external video recording application
-   Depending on tablet, file selection for attachment may be restricted
    to the files contained on the SD card only

### Web App:

-   If all entities/relationships are deleted, there is no option to
    view deleted entities
-   Syncing devices while the server is locked (ie. when archiving a
    project, creating a project etc.) will sometimes slow the server
    down till it no longer loads anything. Server needs to be locked for
    a long period of time for it to be a problem


### Using web app on a tablet browser:

-   Don't. 
-   Attaching files to records may fail.
-   Certain versions of the Chrome browser will not download files from
    the web app correctly from an Android device (download unsuccessful
    error). Use the Firefox browser to download files
    instead

### Data schema:

-   Two attributes with the same name are treated as the same therefore
    only the first attribute defined will be used

### Map UI/performance:

-   Large map file sizes/large numbers of geometry etc. causes
    significant performance issues depending on the speed of the tablet.
    This can often make the map UI slow and inconsistent for practical
    use. This is worst when highlighting and/or labels are displayed
-   Selection of Experimental Fast Raster Loading in the layer config
    menu of raster layers may result in non-rendering of raster edges
-   Rotating the screen orientation while using the Nexus 4 will
    sometimes cause the phone to crash. Use only in locked screen mode
-   Wrong projection for the area will not allow user to save the
    created geometry on that area
-   Layer manager visual bug: activating re-order in layer manager,
    dragging the top layer to the middle position and then toggling any
    other layer's visibility will cause the layer highlighted to remain
    visible as a 'sticky' overlay on all screens
-   Tracklog features are always select-able (point select and polygon
    select tools) even if no tracklog layer exists on the map
-   Tracklog features load into Entity layers, resulting in
    double-plotting if Tracklog layer is also added to map
-   Hidden layers will always be selected if they match the criteria
    despite not being visible
