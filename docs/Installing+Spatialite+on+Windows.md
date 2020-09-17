Installing Spatialite on Windows
=============================================================================


Created: Christian Nassif-Haynes (Unlicensed) (christian@fedarch.org) -
2018-06-12T07:04:27.561Z

Last Updated: Christian Nassif-Haynes (Unlicensed)
(christian@fedarch.org) - 2018-06-13T11:12:19.756Z
 

*Note: This was tested on Windows 10.*


1.  Download the zip file which contains the [spatialite     binaries](http://www.gaia-gis.it/gaia-sins/windows-bin-x86/spatialite-4.3.0a-win-x86.7z).
2.  Extract the contents of the downloaded zip file to a directory
    called **`C:\Program Files (x86)\Spatialite`**. (You will probably
    have to make this directory.) After completing this step, there
    should be a file at
    **`C:\Program Files (x86)\Spatialite\spatialite.exe`**.
3.  Once the installer is finished, add the directory
    **`C:\Program Files (x86)\Spatialite`** to your system path. A
    tutorial for adding directories to your system path can be found
    [here](https://www.howtogeek.com/118594/how-to-edit-your-system-path-for-easy-command-line-access/).
4.  Test your installation by opening a new Command Prompt window,
    typing `spatialite -version` and pressing enter. If you see
    something like the following, installation was successful:


    ```
    C:\Users\mq20151400>spatialite -version
    3.8.11.1 2015-07-29 20:00:57 cf538e2783e468bbc25e7cb2a9ee64d3e0e80b2f
    ```


</div>
