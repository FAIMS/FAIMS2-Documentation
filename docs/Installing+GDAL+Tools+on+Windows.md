---
title: Installing GDAL Tools on Windows
---



Installing GDAL Tools on Windows
=============================================================================


Created: Christian Nassif-Haynes (Unlicensed) (christian@fedarch.org) -
2018-06-12T07:45:11.515Z

Last Updated: Christian Nassif-Haynes (Unlicensed)
(christian@fedarch.org) - 2018-06-12T09:01:51.576Z


*Note: This was tested on Windows 10.*

1.  Download the [G](https://www.gaia-gis.it/spatialite-2.3.1/spatialite-tools-win-x86-2.3.1.zip)[DAL Tools Installer](http://download.gisinternals.com/sdk/downloads/release-1911-gdal-2-3-0-mapserver-7-0-7/gdal-203-1911-ecw-33.msi).
2.  Follow the prompts. Select 'Typical' when asked to choose the
    setup type which best suits your needs:
    ![](attachments/299597846_thumbnails_3.PNG)    
3.  Once the installer is finished, do the following:

    1.  Add the directory `C:\Program Files (x86)\GDAL` to your system
        path. A tutorial for adding directories to your system path can
        be found
        [here](https://www.howtogeek.com/118594/how-to-edit-your-system-path-for-easy-command-line-access/).

    2.  Add an environment variable named `GDAL_DATA` and set it to the
        directory `C:\Program Files (x86)\GDAL\gdal-data`. A tutorial
        for adding environment variables can be found
        [here](https://www.howtogeek.com/51807/how-to-create-and-use-global-system-environment-variables/).

4.  Test your installation by doing the following:

    1.  Open a new Command Prompt window, type `ogr2ogr --version` and
        press enter. If you see something like the following,
        installation of ogr2ogr was successful:

        ```
        C:\Users\mq20151400>ogr2ogr --version
        GDAL 2.3.0, released 2018/05/04
        ```


    2.  In a Command Prompt window, type `echo %GDAL_DATA%`. If you see
        something like the following, you correctly set the `GDAL_DATA`
        environment variable:


        ```
        C:\Users\mq20151400>echo %GDAL_DATA%
        C:\Program Files (x86)\GDAL\gdal-data
        ```



-   [299597846_attachments_3.PNG](attachments/299597846_attachments_3.PNG)
