---
title: FAIMS User Handouts
---

You can download these instructions from the [handout](../handout.pdf) in case you need them on the go.

[TOC]


# FAIMS101: Getting Started

* [FAIMS101 - Getting Started - with pictures](../getting-started)

This guide shows you how to install the FAIMS app and try our sample recording modules.

## What you need:

-  An Android 6+ device
-  Access to fast internet via wifi
-  5 minutes



## Step by Step



-  Go to the Play Store; download and install the FAIMS app onto your device.
-  Open the app, click 'Connect to Demo server' on the bottom left.
-  You should now see a scrolling list of the available 'modules'. modules are FAIMS digital recording forms that can be tailored to specific projects and unique research workflows.
-  Click on any module and download it to your device (may take minutes).
-  Press 'Load the module' and explore the module!
-  After module download, switch off the radios, as the app works offline.







##  Tips and Tricks

### Module download


-  If you touch your device’s screen while a module is downloading, the process will stop and you have to start over.
-  Downloading modules with maps can take several minutes (e.g. CSIRO module)
-  If you are asked 'Do you want to download or update the module?', then the module is already on your device.

### Where does the module live on your device?


-  The module sits in a folder with a long hexadecimal identifier in 'FAIMS' > 'modules'.
-  Deleting the module folder deletes the module off your device.
-  *Deleting the folder deletes all unsynced data.*


### Helpful notes

-  In a module, note the bar at the top of the screen indicating GPS and syncing status.
-  Each module has a side bar (swipe right from the left edge of the screen); it orients you within the module and contains action buttons like 'New' or'Delete record'.



# FAIMS102: Coolest Features

Raise your data collection to a new level!

## Annotations:

Digital 'scribbling on the margin' lets you collect additional info about your observations. Use it to enrich your data, or to collect metadata.

## Certainty sliders:

Let you set the confidence with which you made your observation. Use when you are not 100\% sure about the value of a given attribute.

## Info Buttons:

Provide additional information about attributes, as specified by the user during design to help in the field.

## Picture Galleries:

Let you pick a value using pictures, each of which represents controlled vocab term.

## Hierarchical Dropdowns:

Allow you to progress through a series of embedded dropdown lists until you reach the desired term. Hierarchical dropdowns can use picture galleries!


## Instantaneous Translation:

Modules can be deployed in multiple languages. On the 'Load Module' screen, available translations appear in a dropdown. Each user can choose a preferred language.

## Attach Photos to Records (\& vice versa):

'Take a Picture' button connects you to the device's camera to snap a as many shots as you like. Pictures are attached to your record and inherit its data upon export. To delete an attached picture, press it and hold, go to 'Picture management' and 'Delete'

## Add Drawings to Records:

An 'Attach a File' button lets you attach one or more existing files to a record. See our 'Attach a Sketch' workflow #106 to produce digital sketches and tie them to records.

## Duplicate a Record:

Use this button in the sidebar to make a duplicate record with automatically assigned new ID number. Pictures and attachments are usually not replicated. Save your effort when recording similar objects or situations!

*For more, server-based features, see Guide#200.*

# FAIMS103: Deploy a Module

Deploy an existing module to all your devices.

## What you need:


-  Module definition packet (see other side)
-  Android 7+ devices with the FAIMS app
-  Admin access to a FAIMS server
-  A local or internet connection to that server
-  10 minutes


## How to Instantiate a Module on the Server:


-  Login into your FAIMS server with your username. The defaults are:
	-  Username: `faimsadmin@intersect.org.au`
	-  Password: `Pass.123`
-  Click the 'Create Module' button on top left
-  On the left side in the 'Static data' section, enter module name and metadata about your project.
-  On the right side, upload the definition documents in their respective slots:


-  Data Definition Schema (data_schema.xml)
-  User Interface Schema (ui_schema.xml)
-  User Interface Logic (ui_logic.bsh)
-  Translation file (faims.0.properties)
-  Validation file and CSS files (optional)


-  Push the 'Submit' button.
-  Connect your devices to the server; download your module (see Guide#101)





## What is a 'definition packet'?

FAIMS modules are compiled from a set of 'definition files' uploaded to the server.

The definition packet can have from four to seven files:


-  Data Definition Schema
-  User Interface Schema
-  User Interface Logic
-  Translation('Arch16n') file(s)
-  Validation file (optional)
-  User Stylesheet (optional)
-  Any static images (in a tarball, optional)




## How do I get a module's definition packet?



-  Download it from our github repository as a zip file (https://github.com/FAIMS).
-  Download it from a FAIMS server, by pressing 'Download Module' while logged in. (You also get your data this way!)
-  Generate one using Heurist, a web app (account needed; see Guide #301)
-  Commission one or more custom modules for your project from FAIMS!




# FAIMS104: Switching Servers



As our demo server comes with no guarantees or privacy, you'll want to switch to a private online or local server for actual fieldwork.

## What you need:


-  An Android 7+ device with the FAIMS app
-  A local or online FAIMS server
-  Hostname for your server (e.g. )
-  A local or internet connection to that server


## New FAIMS Users:

Follow these steps if you have just downloaded or reinstalled the FAIMS app.

-  Open the FAIMS app.
-  Press 'Enter Server Details'. If the button is missing, turn this page.
-  On the 'Select Server' screen, use the dropdown to switch to a new server (or auto-discover the server if it is local)
-  Type the new server hostname into the 'Server Host' field.
-  Press 'Test Connection'. If you see 'Connection test succeeded', you have established a connection.
-  Press 'Connect' to connect to the new server and bring up a list of modules.
-  You have successfully connected to a different server!



## Existing Users of FAIMS:


-  Open the FAIMS app.
-  Press 'Show Modules'. If the button is missing, turn this page.
-  Above the 'List of modules', you can see you are still connected to your original server. To change that, press the 'Settings' button (three dots or a hardware button whose exact position varies with every device).
-  On the 'Select server' screen, select 'New Server' from the dropdown.
-  Type the new server hostname in the 'Server Host' field.
-  Press 'Test Connection'. If you get 'Connection test succeeded', you have established a connection.
-  Press 'Connect' to connect to the new server and bring up the list of modules.


## Tips & Tricks
If you want to refresh the list of modules (e.g. because someone has uploaded a new one), drag the module list downwards.


# FAIMS105: Update a Module


If anyone makes changes (structural or administrative) to your module on a server, you need to connect your device to the server and refresh your module.
## What you need:


-  An Android 7+ device with the FAIMS app
-  Access to your server via local network or internet


## Step by Step


-  Open the FAIMS app and press 'Show Modules'.
-  Check that you are connected to your server.
-  Tap on your module and hold for two seconds.
-  An 'Update or Restore module' screen pops up. Three options appear:
-  'Update' updates the structure of the module (users, vocabularies) and does not effect recorded data.
-  'Restore' re-downloads the entire module, updating the structure and files (e.g. maps) in the process. It deletes all records that have not been synced with the server. Beware, you can lose unsynced data!
-  'Cancel' returns you to module without any changes.



# FAIMS106: Attach a Sketch


Use FAIMS to attach sketches, drawings, and plans to your records!  

## What you need:

-  An Android 7+ device
-  'Attach a Sketch/File' and 'View attached files' buttons in your module
-  File manager app
-  Sketching app, e.g. Autodesk Sketchbook, or Samsung S Memo
-  Picture viewing app, e.g. Fast Image Viewer


## Step by Step

-  Use the sketching app to make a sketch.
-  Save it in known location or 'Export' into your module folder on the device (see Guide#101 for guidance)
-  In your module, press the 'Attach a sketch' button.
-  In the 'Choose files' dialogue navigate to your saved sketch. Tapping the filename will attach it to the record.
-  Synchronise to upload the sketch to the server.




## Viewing the Attached Sketch

-  Install an image viewing app that supports the file type(s) you want to view (e.g. TIFF)
-  In the module, press the 'View attachment' button
-  If you have attached more than one file, tap the filename you wish to view
-  Select your new viewing app to open the file (check 'Set as default' or 'Always' if desired)


## Tips and Tricks:

-  There are many good sketching apps on PlayStore
-  Sketching apps let you snap a picture, draw on it, and save the composite
-  You can annotate your Sketch in the module by clicking on the Pencil icon next to the attached Sketch name
-  If you attach .tiff or .ai format files, you need to install appropriate viewing app. JPEGs will display in Gallery.-  If your image viewing app does not appear on the list of options when you attempt to open the file, you may need to try a different viewing app



# FAIMS107: External GPS

Improve the quality of your spatial data by connecting to an External Bluetooth GPS!

## What you need:

-  An Android 7+ device with Bluetooth
-  FAIMS module with External GPS switch
-  External Bluetooth GPS (NMEA 0183 protocol)



## Step by Step

-  Exit all apps and switch off internal GPS on your device
-  Start your external Bluetooth GPS
-  Activate Bluetooth on your device
-  Pair device with the GPS (this sometimes requires a pairing code; Trimble uses 0183)
-  Once the device and GPS are successfully paired, start the FAIMS app
-  In your module, find the GPS controls in your module and enable external GPS
-  Once the GPS obtains a fix you can start collecting spatial data




## Tips and Tricks:

-  Start Bluetooth and pair your GPS before you start the FAIMS app
-  Do not switch between different external GPSs.
-  If you are having trouble, restart all devices and start over.
-  Keep the GPS close so you don’t lose the bluetooth connection.
-  If not sure about pairing code, check with your GPS provider.
-  If GPS loses signal, you will see 'toasts' (pop-up warnings) like 'no valid signal', 'no bluetooth', etc.
-  This workflow may work with all Bluetooth devices
-  Using an external GPS extends the tablet’s battery life, improves performance when the sky is partly blocked, and speeds up position fixes






# FAIMS200: Server Work


The FAIMS server is an essential component of the FAIMS Mobile Platform. It allows authorised users to customise and deploy field recording modules, synchronize multiple devices in the field, manage module users, resolve conflicts, merge duplicates, view and revert record history and export your data in a structured format.

## What you need:

-  A local or online server
-  Access to your server via local network or internet
-  Server hostname and login
-  Computer with a modern browser, like Chrome.


## Working on the Server

-  On your computer, connect to the faims in a box local network or to the internet.
-  Open the browser and go to the server. Log in to the server. Make sure to use your own login if you have one.

  Defaults:

-   Username: `faimsadmin@intersect.org.au`
-   Password: `Pass.123`

-  Click on your module. Module page offers you the following functionality:
	-  Under Module Actions you can manage your module and your module's users.
	-  Under Module Details, you can control your data, its history and structure.





## Tips and Tricks

-  You can order a preconfigured local server - FAIMS in the box - from the FAIMS team.
-  FAIMS offers a virtual private server for rent, if you want to sync to a secure and private instance of FAIMS online.
-  You can setup your own FAIMS server if you have adequate IT skills.
-  All FAIMS software code is open source and freely available on GitHub.
-  Any modern web browser will work, including Chrome on your tablet.
-  The FAIMS Mobile Platform provides record uniqueness by time and username. Make sure to never share a login to the server or a module at the same time.




# FAIMS201: Work with Data

On the server, you can search, view, compare, edit, and delete your records. You can resolve conflicting records and merge duplicates.

## What you need:

-  Familiarity with Guide#200.


## Editing your Data on the Server

-  On the server, click on your module. On the module page select the 'Search Entity Records' button under module details.
-  In the 'Search Entity' screen you can see a list of all synced entities, author, creation date, and modification date.
-  To view and edit the record, click on it in the list. Scroll to the bottom of page for pictures and files.
-  To batch delete records, return to entity list, check multiple records and push 'Delete' button at the bottom of the page.
-  If you want to compare or merge records, check two desired records, and click the 'compare' button.
-  To see the complete history of edits in a single record, press the 'View History' button on top of a record's individual page. You may now revert any deletion or change.




## Tips & Tricks

-  Without a server you can only edit and delete records one by one in your app interface.
-  Without a server you cannot resolve conflicts, merge duplicates or view record history.
-  When looking for a particular record, search for it by entering a string in the search box.
-  Use a filtering dropdown to filter records by entity type or user or literal search string.



# FAIMS202: Edit the Module

Use the server to edit your module's metadata and update its UI or Logic.

## What you need:

-  New metadata or definition files.
-  Familiarity with Guide#200.



## Edit module Metadata and Structure


-  On the server, navigate to your module.
-  Select 'Edit Module' button under module actions.
-  On the 'Edit Module' page you can modify module metadata, including updating your spatial reference (SRID) in the 'Static Data' section.
-  On the 'Edit Module' page you can alter the module ui, logic, translation files, validation, or styling by uploading new definition files. To do so, upload new file in its slot and press 'Update'.
-  Make sure to update the module on your device to implement the changes (for details see reverse).




## Update your Module:
If anyone commits changes to your module on a server, you need to connect your device to the server and refresh your module.

## What you need:

-  An Android 7+ device with the FAIMS app
-  Access to your server via local network or internet


## Step by Step


-  Open the FAIMS app
-  Press 'Show Modules'.
-  Check that you are connected to your server.
-  Tap on your module's name and hold for two seconds.
-  An 'Update or Restore module' screen pops up. Three options appear:
-  'Update' updates the module's structure (ui, logic, static pictures, vocabularies, or maps) and does not effect recorded data.
-  'Restore' re-downloads the entire module, updating the structure and files (e.g. maps) in the process. It deletes all records that have not been synced with the server. Beware, you *will* lose unsynced data!
-  'Cancel' returns you to module without any changes.





# FAIMS203: User Admin

Use the server to add and administer your module users. You need 'superuser' status to do so.

## What you need:

-  'Superuser' status on your server.
-  Familiarity with Guide#200.


## Step by Step

-  On the 'Module Actions' screen, select the 'Edit Users' button. If you cannot see the 'Add Users' field you do not have superuser privileges. Check with project admin staff.
-  Go to the User Management section on the top black ribbon. You need to first create new users on your server and assign them user roles.
-  When finished, navigate back to 'Module Actions' in a given module and select 'Edit Users'. Add users to your module via the dropdown.
-  Make sure to create user accounts before fieldwork. They cannot be created on a device.
-  To delete users, use the same screen as when adding. After you 'update module settings' the deleted users will no longer appear as users in your module.



## Update your Module:

If anyone commits changes to your module on a server, you need to connect your device to the server and refresh your module to implement them.
## What you need:


-  An Android 7+ device with the FAIMS app
-  Access to your server via local network or internet


## Step by Step


-  Open the FAIMS app
-  Press 'Show Modules'.
-  Check that you are connected to your server.
-  Tap on your module's name and hold for two seconds.
-  An 'Update or Restore module' screen pops up. Three options appear:
-  'Update' updates the module's structure (ui, logic, static pictures, vocabularies, or maps) and does not effect recorded data.
-  'Restore' re-downloads the entire module, updating the structure and files (e.g. maps) in the process. It deletes all records that have not been synced with the server. Beware, you *will* lose unsynced data!
-  'Cancel' returns you to module without any changes.




# FAIMS204: Edit Vocabularies

Use the server to edit your module's controlled vocabularies!

## What you need:

-  Familiarity with Guide#200.


## Step by Step

-  Start from the Module page and select 'Edit Vocabulary' under Module Actions.
-  If you 'Select Attribute' you want to change, you can then edit existing or add more items to controlled vocabularies.
-  You can update labels, and/or descriptions which will appear as Info/Help text next to the attribute in the app.
-  You can affect the vocabulary ordering as it appears in the app, edit hierarchies, or urls of picture galleries.
-  You need to 'update settings' on all devices with this module to deploy the changes.


Note that changing vocabulary presentation (between checkbox, radio-button, dropdown, picture gallery, or hierarchical versions) requires changes to the module logic.

## Update your Module:

If anyone commits changes to your module on a server, you need to connect your device to the server and refresh your module.
## What you need:


-  An Android 7+ device with the FAIMS app.
-  Access to your server via local network or internet.


## Step by Step


-  Open the FAIMS app.
-  Press 'Show Modules'.
-  Check that you are connected to your server.
-  Tap on your module's name and hold for two seconds.
-  An 'Update or Restore module' screen pops up. Three options appear:
-  'Update' updates the module's structure (ui, logic, static pictures, vocabularies, or maps) and does not effect recorded data.
-  'Restore' re-downloads the entire module, updating the structure and files (e.g. maps) in the process. It deletes all records that have not been synced with the server. Beware, you *will* lose unsynced data!
-  'Cancel' returns you to module without any changes.




# FAIMS205: Pushing Files

Use the server to promulgate new maps, images and files to all devices!

## What you need:

-  New maps or other files.
-  Familiarity with Guide#200.


## Step by Step

-  Start from the module page and select the button 'Upload Files' under module actions.
-  Select 'Batch Upload' if you have all data collated in one .tar.gz format. Use 7zip (or other open source tool) to compress. Be careful of extra non-desired files on a Mac. This is a useful way of uploading large picture galleries without uploading them one at a time.
-  Select 'Create Directory' and 'Upload File' to create folders and upload files one by one.
-  Update your module settings! (see reverse).



## Update your Module:
If anyone commits changes to your module on a server, you need to connect your device to the server and refresh your module.
## What you need:


-  An Android 7+ device with the FAIMS app.
-  Access to your server via local network or internet.


## Step by Step



-  Open the FAIMS app.
-  Press 'Show Modules'.
-  Check that you are connected to your server.
-  Tap on your module's name and hold for two seconds.
-  An 'Update or Restore module' screen pops up. Three options appear:
-  'Update' updates the module's structure (ui, logic, static pictures, vocabularies, or maps) and does not effect recorded data.
-  'Restore' re-downloads the entire module, updating the structure and files (e.g. maps) in the process. It deletes all records that have not been synced with the server. Beware, you *will* lose unsynced data!
-  'Cancel' returns you to module without any changes.




# FAIMS206: Module Backup


Use the server to safely backup your team's work! This procedure will download the module structure (definition files) and all synced data to your computer.

## What you need:

-  Familiarity with Guide#200.


## Step by Step

-  Login to the server and choose your module.
-  Select the button 'Download Module'.
-  The module and data will download as one 'tarball'. The tarball will contain:

-  Data Definition files.
-  All data entered into the module.
-  All Pictures, Maps etc. within the sqlite database and associated folders.




This tarball may be used to instantiate *the exact same module* onto another server. Be careful not to sync with multiple servers.



# FAIMS207: Emergency Backup
In case of emergency, you can manually backup your individual device onto an SD card or USB drive while in the field. These actions can risk permanent data loss, and should seldom be normally undertaken. Recovery should only be attempted by the FAIMS team.

## What you need:

-  Device with a module.
-  SD card or USB & host cable (OTG).
-  File Manager (we recommend ES File Explorer) on device.
-  Ability to copy files on device.
-  An urgent and critical need to back up your data without recourse to the server.


## Step by Step

-  Go into settings and make sure to stop the FAIMS app.
-  Insert SD card or connect USB stick to device via host cable.
-  On the device, use File Manager to navigate to your FAIMS module folder
-  Copy the entire folder
-  Using File Manager navigate to your SD card or USB stick
-  Paste your module folder here and change its label to include current date.
-  Keep SD card or USB stick safe!


(Note: Contact FAIMS to attempt to synchronise your data. This may be quite expensive.)

# FAIMS208: Export Data


Use the server to export your data in a default or custom-made well-structured format!

## What you need:

-  Module with data on a server.
-  Familiarity with Guide#200.


## Step by Step

-  On the nodule page click 'Export Module'.
-  On 'Export Module', choose an available exporter from the dropdown.
-  For the generalised exporter, we include csvs, shapefiles (if geometries exist), and a sqlite database by default. Tick the checkbox if you want to download images as well and press 'Export'.
-  Press 'Download' button to download the archive with structured data.
-  Unzip your archive and start your analysis!



## Tips and Tricks

-  The 'Export' button exports only the data, not the data definition files.
-  The default exporter makes shapefiles (.shp) out of your spatial data, puts all records in .csv by Entity, and renames all your Photos by your identifier. Data gets written into the shapefile attributes as well as exif data in your Photos.
-  The archive also contains a sqlite database which houses all your raw data.
-  Contact FAIMS if you need to export your data in different format than .shp or .csv
