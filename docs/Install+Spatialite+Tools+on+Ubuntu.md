FAIMS Mobile Platform Documentation (FAIMS): Install Spatialite Tools on Ubuntu
===============================================================================

::: {style="font-size:70%; color:#444; font-style: italic"}
Created: Former user (Deleted) () - 2013-08-19T17:46:13.392Z

Last Updated: Former user (Deleted) () - 2013-08-19T17:46:14.392Z
:::

<div>

### Installing Spatialite Tools on Ubuntu {#InstallSpatialiteToolsonUbuntu-InstallingSpatialiteToolsonUbuntu}

Follow these instructions to install Spatialite on Ubuntu.

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id=""}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
*Note: This was tested on Ubuntu 12.04.1 LTS.*
:::
:::

##### Requirements: {#InstallSpatialiteToolsonUbuntu-Requirements:}

-   install spatialite ([instructions can be found
    here](../FAIMS/Install+Spatialite+Tools+on+Ubuntu.html))
-   install packages expat libexpat1-dev zlib1g-dev

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id=""}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
sudo apt-get install expat libexpat1-dev zlib1g-dev
```
:::
:::

##### Instructions: {#InstallSpatialiteToolsonUbuntu-Instructions:}

-   download and compile [readosm
    (1.0.0b)](http://www.gaia-gis.it/gaia-sins/readosm-1.0.0b.tar.gz){.external-link}

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id=""}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
wget http://www.gaia-gis.it/gaia-sins/readosm-1.0.0b.tar.gz
tar zxf readosm-1.0.0b.tar.gz
cd readosm-1.0.0b
./configure
make
sudo make install
cd ..
```
:::
:::

-   download and compile [spatialite-tools
    (4.1.1)](http://www.gaia-gis.it/gaia-sins/spatialite-tools-4.1.1.tar.gz){.external-link}

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id=""}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
wget http://www.gaia-gis.it/gaia-sins/spatialite-tools-4.1.1.tar.gz
tar zxf spatialite-tools-4.1.1.tar.gz
cd spatialite-tools-4.1.1
./configure
make
sudo make install
cd ..
```
:::
:::

##### Usage: {#InstallSpatialiteToolsonUbuntu-Usage:}

Now you should have access to all the tools.

Some tools may raise errors due to missing file e.g. \... missing file
libspatialite.so.2. In such cases simply add the appropriate file to
library path.

e.g.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id=""}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
sudo ldconfig /usr/local/lib/libspaitalite.so.2
```
:::
:::

</div>

Attachments
-----------
