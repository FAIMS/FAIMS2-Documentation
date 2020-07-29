FAIMS Mobile Platform Documentation (FAIMS): Install GDAL Tools
===============================================================

::: {style="font-size:70%; color:#444; font-style: italic"}
Created: Former user (Deleted) () - 2013-08-19T18:11:46.536Z

Last Updated: Former user (Deleted) () - 2013-08-19T18:11:47.536Z
:::

<div>

### Installing GDAL Tools {#InstallGDALTools-InstallingGDALTools}

Follow these instructions to install GDAL Tools on Ubuntu.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id=""}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
*Note: This was tested on Ubuntu 12.04.1 LTS.*
:::
:::

##### Requirements: {#InstallGDALTools-Requirements:}

-   This assumes you have
    installed [Spatialite](../FAIMS/Install+GDAL+Tools.html)

##### Instructions: {#InstallGDALTools-Instructions:}

-   download and compile [gdal
    (1.10.0)](http://download.osgeo.org/gdal/1.10.0/gdal-1.10.0.tar.gz){.external-link}

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id=""}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
wget http://download.osgeo.org/gdal/1.10.0/gdal-1.10.0.tar.gz
tar zxf gdal-1.10.0.tar.gz
cd gdal-1.10.0
./configure
make
sudo make install
cd ..
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id=""}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
You probably also want to use ldconfig to make sure /usr/local/lib is
included when Ubuntu looks for shared libraries.
:::
:::

</div>

Attachments
-----------
