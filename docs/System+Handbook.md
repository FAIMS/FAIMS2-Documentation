System Handbook
============================================================



Overview 
--------

[The FAIMS Mobile Platform is an Android application and Ruby server
built by intersect for the Federated Archaeological Information
Management Systems (FAIMS) Project, funded by the National eResearch
Collaboration Tools and Resources (NeCTAR) program. FAIMS is used by
Archaeologists to collect Survey and GIS data in the
field.]

Components 
----------

See <https://github.com/IntersectAustralia/faims-web/wiki/Product-Overview>

Source Code Repositories 
------------------------

::: 
+-----------------------------------+-----------------------------------+
| Component                         | Location                          |
+===================================+===================================+
| Ruby on Rails application         | <https://github.com/IntersectAust |
|                                   | ralia/faims-web>                  |
+-----------------------------------+-----------------------------------+
| Android application               | <https://github.com/IntersectAust |
|                                   | ralia/faims-android>              |
+-----------------------------------+-----------------------------------+
:::

Dependencies & Hardware 
-----------------------

::: 
+-----------------------+-----------------------+-----------------------+
| Component             | Dependencies          | Minimum Hardware      |
+=======================+=======================+=======================+
| Web app               | -   OS: Linux;        | CPU: Dual Core 64     |
|                       |     Ubuntu*12.04.1    | bit                   |
|                       |     LTS*              |                       |
|                       | -   Ruby: 1.9.3-p286  | RAM: 4GB+             |
|                       |     (or greater)      |                       |
|                       | -   GIS packages      | Hard Disk: 1TB        |
+-----------------------+-----------------------+-----------------------+
| Android app           | -   OS: Android 4.4   | Android device with   |
|                       |     (or greater)      | WIFI                  |
|                       |                       |                       |
|                       |                       | RAM: 2GB+             |
|                       |                       |                       |
|                       |                       | SDCard: ?             |
+-----------------------+-----------------------+-----------------------+
:::

Deployment 
----------

#### Deployment Procedures 

See [System Handbook](../FAIMS/System+Handbook.html)

#### Post Release Verification 

See [System Handbook](../FAIMS/System+Handbook.html)

#### Monitoring and Maintenance 

[*What monitoring and maintenance are in place or need to be regularly
performed. Who does it?*]

Support 
-------

See [System Handbook](../FAIMS/System+Handbook.html)

Production Environment(s) 
-------------------------

::: 
+-----------+-----------+-----------+-----------+-----------+-----------+
| Component | Location  | Owner     | Who at    | Version   | Notes     |
|           |           |           | Intersect | deployed  |           |
|           |           |           | has       |           |           |
|           |           |           | access?   |           |           |
+===========+===========+===========+===========+===========+===========+
| Web app   | This is   | N/A       | N/A       | 20130813\ | The web   |
|           | installed |           |           | _BETA\_1  | app is    |
|           | by users  |           |           |           | installed |
|           | on their  |           |           |           | via a     |
|           | own       |           |           |           | bash      |
|           | server.   |           |           |           | script    |
|           |           |           |           |           | which     |
|           |           |           |           |           | downloads |
|           |           |           |           |           | the [faim |
|           |           |           |           |           | s-web](ht |
|           |           |           |           |           | tps://git |
|           |           |           |           |           | hub.com/I |
|           |           |           |           |           | ntersectA |
|           |           |           |           |           | ustralia/ |
|           |           |           |           |           | faims-web |
|           |           |           |           |           | )  |
|           |           |           |           |           | repositor |
|           |           |           |           |           | y         |
|           |           |           |           |           | tag as a  |
|           |           |           |           |           | zip       |
|           |           |           |           |           | file.     |
+-----------+-----------+-----------+-----------+-----------+-----------+
| Android   | Play      | Intersect | ?         | 20130813\ | The       |
| app       | Store     |           |           | _BETA\_1  | android   |
|           |           |           |           |           | app is    |
|           |           |           |           |           | installed |
|           |           |           |           |           | via the   |
|           |           |           |           |           | play      |
|           |           |           |           |           | store.    |
+-----------+-----------+-----------+-----------+-----------+-----------+
:::

Release Notes 
-------------

See [Release Notes](../FAIMS/Release+Notes.html)

[Test/Demo Environments]

~~See QA Handbook~~

[Developer Setup]

See [Developer Setup](../FAIMS/Developer+Setup.html)

</div>