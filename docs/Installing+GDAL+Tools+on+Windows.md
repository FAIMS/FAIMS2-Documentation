FAIMS Mobile Platform Documentation (FAIMS): Installing GDAL Tools on Windows
=============================================================================

::: {style="font-size:70%; color:#444; font-style: italic"}
Created: Christian Nassif-Haynes (Unlicensed) (christian\@fedarch.org) -
2018-06-12T07:45:11.515Z

Last Updated: Christian Nassif-Haynes (Unlicensed)
(christian\@fedarch.org) - 2018-06-12T09:01:51.576Z
:::

<div>

\

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="74a92c17-7ec8-465f-93c0-cedc6440230f"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
*Note: This was tested on Windows 10.*
:::
:::

1.  Download the
    the [G](https://www.gaia-gis.it/spatialite-2.3.1/spatialite-tools-win-x86-2.3.1.zip){.external-link}[DAL
    Tools
    Installer](http://download.gisinternals.com/sdk/downloads/release-1911-gdal-2-3-0-mapserver-7-0-7/gdal-203-1911-ecw-33.msi){.external-link}.
2.  Follow the prompts. Select \'Typical\' when asked to choose the
    setup type which best suits your needs:\
    [![](attachments/299597846_thumbnails_3.PNG){.confluence-embedded-image
    width="495" height="387"
    srcset="https://faimsproject.atlassian.net/wiki/download/thumbnails/299597846/3.PNG?version=1&modificationDate=1528789785523&cacheVersion=1&api=v2&width=495&height=387 2x, https://faimsproject.atlassian.net/wiki/download/thumbnails/299597846/3.PNG?version=1&modificationDate=1528789785523&cacheVersion=1&api=v2&width=495&height=387 1x"}]{.confluence-embedded-file-wrapper
    .confluence-embedded-manual-size}
3.  Once the installer is finished, do the following:

    1.  Add the directory `C:\Program Files (x86)\GDAL` to your system
        path. A tutorial for adding directories to your system path can
        be found
        [here](https://www.howtogeek.com/118594/how-to-edit-your-system-path-for-easy-command-line-access/){.external-link}.

    2.  Add an environment variable named `GDAL_DATA` and set it to the
        directory `C:\Program Files (x86)\GDAL\gdal-data`. A tutorial
        for adding environment variables can be found
        [here](https://www.howtogeek.com/51807/how-to-create-and-use-global-system-environment-variables/){.external-link}.

4.  Test your installation by doing the following:

    1.  Open a new Command Prompt window, type `ogr2ogr --version` and
        press enter. If you see something like the following,
        installation of ogr2ogr was successful:

        ::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="35c2e994-890f-47dd-9310-47ba8130f054"}
        ::: {.codeContent .panelContent .pdl}
        ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
        C:\Users\mq20151400>ogr2ogr --version
        GDAL 2.3.0, released 2018/05/04
        ```
        :::
        :::

    2.  In a Command Prompt window, type `echo %GDAL_DATA%`. If you see
        something like the following, you correctly set the `GDAL_DATA`
        environment variable:

        ::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="ce59f07c-177d-45aa-9bee-38616b65062f"}
        ::: {.codeContent .panelContent .pdl}
        ``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
        C:\Users\mq20151400>echo %GDAL_DATA%
        C:\Program Files (x86)\GDAL\gdal-data
        ```
        :::
        :::

</div>

Attachments
-----------

-   [299597846\_attachments\_3.PNG](attachments/299597846_attachments_3.PNG)
