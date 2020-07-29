FAIMS Mobile Platform Documentation (FAIMS): Import GeoTiffs into FAIMS App via ArcGIS
======================================================================================

::: {style="font-size:70%; color:#444; font-style: italic"}
Created: Adela Sobotkova (adela\@faims.edu.au) -
2014-02-27T14:15:08.801Z

Last Updated: Penny Crook (penny\@faims.edu.au) -
2014-04-22T00:36:50.322Z
:::

<div>

*For ArcGIS 10.1 users, here are the instructions on how to prepare
GeoTiffs for use in the FAIMS app using the ArcGIS tools.*

Step-by-step guide {#ImportGeoTiffsintoFAIMSAppviaArcGIS-Step-by-stepguide}
------------------

The preparation of rasters in ArcGIS for FAIMS deployment comprises
three basic steps: reprojection, tiling, transfer. The second is
optional, depending on your raster size. This procedure has been tested
in ArcGIS 10.1 SP1, and we welcome any feedback on other versions of the
software.

1.  Make sure your file is a GeoTiff format

2.  Reproject the file to EPSG 3857

3.  Tile the image. This step is optional and applies especially to
    large files (100Mb and higher), or if for some reason your raster is
    not displaying fast enough on your device (low power processor).

4.  Upload the tile(s) (GeoTiffs) onto the FAIMS Server using this
    route:

    1.  Open the web browser with your FAIMS server and login

    2.  Navigate to your \"Module Actions\" \> click \"Upload Files\"\
        [![](attachments/3014710_thumbnails_UploadFilesArrow.png){.confluence-embedded-image
        width="500"
        srcset="https://faimsproject.atlassian.net/wiki/download/thumbnails/3014710/UploadFilesArrow.png?version=1&modificationDate=1393511529100&cacheVersion=1&api=v2&width=992&height=528 2x, https://faimsproject.atlassian.net/wiki/download/thumbnails/3014710/UploadFilesArrow.png?version=1&modificationDate=1393511529100&cacheVersion=1&api=v2&width=500&height=266 1x"}]{.confluence-embedded-file-wrapper
        .confluence-embedded-manual-size}

    3.  Use the existing \"Data\" directory or create additional
        sub-directories using the \"create directory\"  button\
        [![](attachments/3014710_thumbnails_FilesArrow.png){.confluence-embedded-image
        width="500"
        srcset="https://faimsproject.atlassian.net/wiki/download/thumbnails/3014710/FilesArrow.png?version=1&modificationDate=1393511544280&cacheVersion=1&api=v2&width=1000&height=474 2x, https://faimsproject.atlassian.net/wiki/download/thumbnails/3014710/FilesArrow.png?version=1&modificationDate=1393511544280&cacheVersion=1&api=v2&width=500&height=237 1x"}]{.confluence-embedded-file-wrapper
        .confluence-embedded-manual-size}
    4.  Upload individual files using the \"upload file\" button next to
        \"create directory\".
    5.  If you have multiple files, you can use the black  \"Upload\"
        button after you zip **all** your files up using 7zip. The
        zipped files needs to have a .tar.gz extension for the batch
        upload to work.

5.  Propagate the newly added files to all your devices by connecting
    your devices to the Server, clicking on the Module and selecting
    \"Download\" 

6.  There is a substitute way of uploading rasters onto the device via
    USB cable from your desktop, without putting them up on Server
    first. This route is explained in the note below. It is
    **disrecommended** for multiple reasons and may cause problems with
    your raster rendering, please use it as the last resort.\
    \
    \

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id=""}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
*Note that you can also transfer the ArcGIS raster files from your
desktop onto the USB-connected device *via a File Explorer. You need to*
navigate to the appropriate FAIMS Module folder on your Device (Internal
memory \> Emulated \> 0 \> FAIMS \> Modules \> Module UUID; UUIDs can be
tricky to identify with a particular module if you have multiple modules
loaded, as it is not a human-readable name!). Inside the module folder
you navigate to Files\>Data folder. You can create Maps folder inside or
simply deposit the rasters in the Data folder. Make sure all have
transferred. Back on the device, open the module, navigate to Map
screen, click on Layers \> Add Raster file \> navigate to the folder
where you deposited the files \> click one of the files and watch it
render. Again, this is a **disrecommended** option. Use it as the last
resort, if you use one and only one device in the field, or if your
network connection fails fatally.*
:::
:::

Related articles {#ImportGeoTiffsintoFAIMSAppviaArcGIS-Relatedarticles}
----------------

-   <div>

    [Page:]{.icon .aui-icon .aui-icon-small .aui-iconfont-page-default
    title="Page"}

    </div>

    ::: {.details}
    [Install and Run the FAIMS
    Server](../FAIMS/Install+and+Run+the+FAIMS+Server.html)
    :::

-   <div>

    [Page:]{.icon .aui-icon .aui-icon-small .aui-iconfont-page-default
    title="Page"}

    </div>

    ::: {.details}
    [Create a Module on the
    Server](../FAIMS/Create+a+Module+on+the+Server.html)
    :::

-   <div>

    [Page:]{.icon .aui-icon .aui-icon-small .aui-iconfont-page-default
    title="Page"}

    </div>

    ::: {.details}
    [Import GeoTiffs into FAIMS App via
    ArcGIS](../FAIMS/Import+GeoTiffs+into+FAIMS+App+via+ArcGIS.html)
    :::

-   <div>

    [Page:]{.icon .aui-icon .aui-icon-small .aui-iconfont-page-default
    title="Page"}

    </div>

    ::: {.details}
    [Testing Methodology](../FAIMS/Testing+Methodology.html)
    :::

</div>

Attachments
-----------

-   [3014710\_attachments\_FilesArrow.png](attachments/3014710_attachments_FilesArrow.png)
-   [3014710\_attachments\_UploadFilesArrow.png](attachments/3014710_attachments_UploadFilesArrow.png)
-   [3014710\_attachments\_Files.png](attachments/3014710_attachments_Files.png)
-   [3014710\_attachments\_UploadFiles.png](attachments/3014710_attachments_UploadFiles.png)
