FAIMS Mobile Platform Documentation (FAIMS): Copy of Harvard Excavation 2017 Regression Test - AW
=================================================================================================

::: {style="font-size:70%; color:#444; font-style: italic"}
Created: Brian Ballsun-Stanton (brian\@faims.edu.au) -
2019-09-04T01:43:05.409Z

Last Updated: Brian Ballsun-Stanton (brian\@faims.edu.au) -
2019-09-04T01:43:54.945Z
:::

<div>

(Based on MEMSAP Excavation 2016 Regression Test, author PJ, report any
issued to petra\@fedarch.org; the module lives on faims2.fedarch.org as
Tao River Module Beta - 22 April)

**Device:** Shield tablet (software version 5.1)

**Android version:** Android 7.0

**FAIMS version:** 2.5

[Action Bar]{.underline} {#CopyofHarvardExcavation2017RegressionTest-AW-ActionBar}
========================

-   Clicking **Clean Synced Files** allows the deleting of files that
    have already been synced to the server in order to clean up space on
    the device. [Cleaning synced files with/without thumbnails causes
    the icons in the top bar (sync, bluetooth, gps, etc) to glitch out
    (issue easily fixed by changing tabs). However, when attempting to
    clean synced files with GPS activated, icons glitch out and can only
    be fixed by reloading the module (occasionally causes the app to
    crash)]{style="color: rgb(255,0,0);"}\
    [\
    After waiting for \~30s, the glitch appeared to resolve itself, but
    files had not been deleted (still appear in search menu)\
    ]{style="color: rgb(255,0,0);"}
    -   Clicking **Clean Synced Files** opens an additional window with
        three options to select from: a) **Delete all synced files which
        have thumbnails**, b) **Delete all synced files**, or c)
        **Cancel**
    -   Clicking **Delete all synced files which have thumbnails**
        deletes all synced files, but leaves only thumbnails to display
        in the device (*Note: this can only be tested after few records
        have been created with pictures and synced with the server*)
    -   Clicking **Delete all synced files** deletes all synced files
        from the device
    -   Verify on the server that all synced and deleted files are
        stored on the server. [Not tested as I have no access to the
        server]{style="color: rgb(255,0,0);"}
-   Clicking **Disable (Enable) Sync** toggles synchronisation between
    activated and deactivated

    -   **Sync** is turned off by default,.

    -   If the **Sync** is disabled, the [the fifth icon in the Action
        bar has light grey colour. ]{style="color: rgb(0,0,0);"}
    -   [If the Sync is enabled, device is connected to the server and
        unsynced records exist on the device, the fifth icon in the
        Action bar will turn blue while
        syncing. ]{style="color: rgb(0,0,0);"}

        -   [Once the syncing has finished, the icon will again turn
            dark grey, which means all records have been synced with the
            server.]{style="color: rgb(0,0,0);"}

-   Clicking **Internal GPS** toggles the internal GPS on and off
    -   Internal GPS is turned off by
        default.[ ]{style="color: rgb(0,0,255);"}
-   Clicking **Enable External GPS** toggles the external GPS on and off
    -   With Bluetooth disabled, it correctly displays an error
    -   External GPS is turned off by default.
-   [Once the **Internal or External GPS** is turned on the GPS
    Diagnostics in the **Control Tabgroup** will signal whether the
    Internal and External GPS is on or off.]{style="color: rgb(0,0,0);"}
-   [Once the **Internal or External GPS** is turned on the third icon
    (dot-like icon) from the left [in the Action
    bar ]{style="color: rgb(0,0,0);"}will turn
    blue.]{style="color: rgb(0,0,0);"}
-   [Once [the **Internal or External GPS** is turned on, the device\'s
    time will be checked against the GPS system time and if they vary,
    warning message will advise changing the device\'s time to the GPS
    system
    time.]{style="color: rgb(0,0,0);"}]{style="color: rgb(0,0,0);"}
    -   *Note: The device\'s internal time can be change in the
        device\'s settings. It is necessary the device\'s internal time
        matches the GPS system time to ensure the consistency of
        recorded data.*
    -   If the warning message hasn\'t showed up, either the GPS is not
        enabled or the device\'s time matches the GPS system time.
-   The current record has to be saved if the first icon from the left
    [in the Action bar ]{style="color: rgb(0,0,0);"}(database-icon with
    three compartments) is blue. *Note: before navigation out of the
    current record wait for the autosaving to occur to make sure your
    records are all saved, eg. when the icon turns grey, to prevent any
    data loss. It can take few seconds.*

[[Navigation Drawer]{.underline}]{style="color: rgb(0,0,0);"} {#CopyofHarvardExcavation2017RegressionTest-AW-NavigationDrawer}
=============================================================

-   [Pressing the device\'s screen on the left edge if the screen and
    dragging to the right side will open a **navigation drawer**
    panel.]{style="color: rgb(0,0,0);"}
-   [User can navigate through different Tab Groups, such as the
    following: **Control, Site, Trench, Locus, Stratum/Feature, FCN,
    Relationship, Photograph Log, Diary, Legacy.**[ Only control, site,
    and trench available in the navigation drawer
    panel]{style="color: rgb(255,0,0);"}]{style="color: rgb(0,0,0);"}
-   [Clicking** **the **Module Home** button will open the **Login Tab**
    of the module.]{style="color: rgb(0,0,0);"}
-   [Clicking the **Exit Module** button will open a warning message.
    Clicking yes will result in exiting the
    module.]{style="color: rgb(0,0,0);"}
-   [Clicking the ]{style="color: rgb(0,0,0);"}**New**[ button will
    create a new record of the current type, eg. if you are currently in
    Locus, new Locus record will be
    created.]{style="color: rgb(0,0,0);"}[  Click on the \'new\' button
    while on the log-in page has the same effect as clicking the exit
    module button]{style="color: rgb(255,0,0);"}
-   [Clicking **Duplicate** button will duplicate a current record: all
    entered text fields, numeric fields, selected dropdown box values,
    radiobutton values, or picture galleries will be
    duplicated. ]{style="color: rgb(0,0,0);"}
    -   [Any attachments and GPS coordinates, Record Created by and
        Record Created at will not be
        duplicated. ]{style="color: rgb(0,0,0);"}
    -   [If the ID number is created by autonumbering from a number
        defined by the user for each device in **Control Tabgroup, Next
        IDs Tab**, the ID of the duplicated record will be the last used
        ID number of the duplicated record type +1, eg. if the last
        created Locus had ID number 55, the duplicated Locus will have
        ID 56, no matter if the record being duplicated had ID 55
        or 32.]{style="color: rgb(0,0,0);"}
-   Clicking the **Delete** button will delete the current record. Note:
    this cannot be undone if the device\'s has not been synchronized
    with the server prior deleting the record.
-   Clicking the **Validate** button will display list of all validated
    fields with blank values in the current record.\
    \

[Login Tabgroup]{.underline} {#CopyofHarvardExcavation2017RegressionTest-AW-LoginTabgroup}
============================

[User List Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-UserListTab style="margin-left: 30.0px;"}
-----------------------------------------------

-   -   A **User** can be selected from the drop down menus provided\
        -   Excluding **User**, the values of these views are saved to
            the local settings of the device upon logging
            in.***[ ]{style="color: rgb(255,0,0);"}***
        -   The value for **User** must be selected each time the tab is
            shown
    -   Clicking the **Log In** button logs in the selected user and
        shows the **Control **tab group
        -   A non-empty **User** must be selected before logging in,
            otherwise an appropriate warning is generated.
    -   Clicking the **Module Guide** button displays the **Help **tab
    -   The user drop down is updated whenever this tab is shown. To
        check this, the following tests are to be performed in sequence:
        (Note: make sure you are connected with your device to the same
        server where the module resides). [Unable to test, no access to
        server]{style="color: rgb(255,0,0);"}
        -   Add a new user on the server or ensure one already exists.
            (We refer to this user as *User A*.)
        -   Add a new user on the server. (*User B.)*
        -   Log in as *User A*.
        -   Activate syncing and wait for a sync to occur.
        -   Check that *User A* and *User B* can be seen upon re-loading
            the module.
        -   Delete *User B *from the server*.*
        -   Log in as *User A.*
        -   Ensure syncing is enabled and wait for a sync to occur.
        -   Go back to the **Login** tab and ensure *User B* is no
            longer present in the list.
        -   Add a new user on the server. (*User C*.)
        -   Ensure syncing is still enabled and log in as *User A*.
        -   Wait for a sync to occur.
        -   Go back to the **Login** tab and ensure *User C* is present
            in the list.
    -   Clicking the **Device Code** dropdown menu will select the
        Device Code.
    -   Clicking the **Login** button will open a **Control** Tabgroup.
        -   If **User** or **Device Code** haven\'t been selected and
            the **Login** button is clicked, a warning message will
            appear and the login process will abort.

[Help tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-Helptab style="margin-left: 30.0px;"}
------------------------------------------

-   -   A **Module Guide** is displayed which provides an overview of
        the features and navigation of the Module. (Note: no **Module
        Guide** has been provided here) 

[[Control Tabgroup]{.underline}]{style="color: rgb(0,0,0);"} {#CopyofHarvardExcavation2017RegressionTest-AW-ControlTabgroup}
============================================================

[Site Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-SiteTab style="margin-left: 30.0px;"}
------------------------------------------

-   -   **New Site Name** and **Year of Campaign** are styled in red.
    -   Clicking
        the [**[Create]{style="color: rgb(51,51,51);"} **]{style="color: rgb(0,0,255);"}N**ew
        Site **button** **creates a new Site for data entry
    -   When **New Site** is created the record name (identifier) is
        combination of \'**New Site Name**\' and \'**Year of
        Campaign**\'. [Although instructions state that \"Trench ID must
        be in the format T + number\", there is no warning/error message
        when using different format]{style="color: rgb(255,0,0);"}
        -   If the \'**New Site Name**\' and \'**Year of Campaign**\'
            are left empty and the **Create New Site** button is
            clicked, new **Site** with an empty identifier will be
            created.
        -   If the new **Site** with an empty identifier was created,
            you can always deleted by clicking the **Delete** button in
            the **navigation drawer**.
    -   Existing Sites are displayed under **Choose an Existing Site**
        list. 
    -   If a user attemps to create a site with already
        existing combination of \'**New Site Name**\' and \'**Year of
        Campaign**\' a warning message will show up.
        -   The warning message can be ignored, which will result in
            creating a duplicate **Site** record.
    -   Selecting a site record from **Choose an Existing Site** list
        will open the selected **Site** record.\
        \

-   [Next IDS Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-NextIDSTab}
    ----------------------------------------------

    -   A separate numerical Starting **ID** is displayed for each of
        the **Locus ID**, **Stratum/Feature ID**, and **Next FCN ID**
        entities.
        -   Each Starting ID is used to set the ID of a respective
            entity upon creation and is automatically incremented by 1
            each time it is used.
        -   Each Starting ID can be modified by the user at any time.
        -   The default setting of each starting ID is set as \'1\'.
        -   Each Starting ID is saved into local settings upon blur, and
            is automatically repopulated upon logging in.

[Search Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-SearchTab style="margin-left: 30.0px;"}
--------------------------------------------

[Deleting an entity from \'Existing sites\' does not appear to delete
entities created within it (e.g trenches). Despite deleting all existing
sites, trenches/loci/etc from the sites were still available in the
search menu. The same thing happened when deleting
trenches. ]{style="color: rgb(255,0,0);"}

[\
]{style="color: rgb(255,0,0);"}

[\
]{style="color: rgb(255,0,0);"}

-   -   Search results are automatically shown in the **Entity
        List** whenever this tab is shown
        -   These results are automatically refined by the
            selected ****Entity Type,**** and/or ****User,**** and/or
            ****Site****
        -   If **Entity Type** is selected, the **Entity list** shows
            only records of the selected **Entity Type**, eg. Locus or
            Photolog.
        -   If ****User**** is selected, the ****Entity list**** shows
            only records created by the selected **User,** eg. Faims
            Admin or All.
        -   If **Site** is selected, the
        -   **The Entity Type, User, and Site** filters can be combined,
            eg. user can look for a **Diary** from given **Site,** or by
            given **Author.**
    -   The default entity type selected is **All**, which represents
        any of the following entities: **Site, Trench, Trench Files,
        Locus, Stratum/Feature, Sediment/Aggregate, Photograph Log,
        Diary, FCN, Soil Munsel Color, Legacy**.
    -   The search results can be refined by\...
        -   \...some search term by entering free-text string into
            the **Search Term** view and clicking the **Search** button.
            -   The Search searches only from the beginning of the
                string and only complete match, e. g. when \"11\" is
                entered, only the records whose identifier starts with
                11 will be displayed. It can display records 11, 112,
                1105, 1100006 under the Entity List.
            -   The Search does not find any records when the free-text
                string comes from other part of the identifier, than
                from its beginning, e.g. the record identifier is \"New
                York\", text entered \"York\" then the Search will not
                display any records under the Entity List.[ Typing
                \"T3\" or \"testing\" into the search bar yields
                entities with names such as \"testing deletion
                2008-T3-L2\". However typing L2 does not yield the above
                result. ]{style="color: rgb(255,0,0);"}
        -   \...the type of entity record by selecting an option from
            the **Entity Types **drop down menu.
    -   Clicking on one of the listed search results in the **Entity
        List** loads the appropriate record.

[Site Tabgroup]{.underline} {#CopyofHarvardExcavation2017RegressionTest-AW-SiteTabgroup}
===========================

-   When the tab group is shown, the navigation drawer is updated with
    the **New/Duplicate/Delete/Validate** buttons for the Site. 
-   When the tab group is shown, the current changes to the tab group
    are kept and auto-saving is initiated.
-   **Site Name** and **Year of Campaign** are autopopulated from
    previous tabs and non-writable fields.
-   **Trench ID** is styled in red and is validated
    when [the **Validation** button is clicked in the **navigation
    drawer**]{style="color: rgb(0,0,0);"}[.]{style="color: rgb(0,0,0);"}\
    -   Clicking the **Trenches **button** **creates a new Trench for
        data entry
    -   Existing Trenches are displayed under **List of Existing
        Trenches** list. 
    -   If a user attemps to create a site with already existing
        \'**Trench ID**\' a warning message will show up.
        -   The warning message can be ignored, which will result in
            creating a duplicate **Trench** record.
    -   Selecting a site record from **List of Existing Trenches** list
        will open the selected **Trench** record.

[[Trench Tabbgroup]{.underline}]{style="color: rgb(0,0,0);"} {#CopyofHarvardExcavation2017RegressionTest-AW-TrenchTabbgroup}
============================================================

-   When the tab group is shown, the navigation drawer is updated with
    the **New/Duplicate/Delete/Validate** buttons for the Site. 
-   When the tab group is shown, the current changes to the tab group
    are kept and auto-saving is initiated.

[Trench Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-TrenchTab}
--------------------------------------------

-   **Site Name, Author,** **Trench ID,** and **Date Opened** are
    autopopulated from previous tabs and non-writable fields.
-   Clicking the **Take From GPS** button will autopopulate Latitude and
    Longitude, Northing and Easting, and Accuracy if the Internal or
    External GPS is enabled and connected.
-   Excavation method is styled in red and is validated
    when [the **Validation** button is clicked in the **navigation
    drawer**]{style="color: rgb(0,0,0);"}[.]{style="color: rgb(0,0,0);"}
-   [Clicking the **Set Date Closed\... **button will open a Date Picker
    Tab where a closing date can be selected.\
    ]{style="color: rgb(0,0,0);"}
    -   [Clicking on a selected date and clicking on the Set Date Closed
        button will return back to the Trench Tab Group and will set the
        **Date Closed**.]{style="color: rgb(0,0,0);"}
    -   [Once set, the **Date Closed** cannot be undone, it can only be
        modified to a different date.]{style="color: rgb(0,0,0);"}
-   [Clicking **Add Trench Files** button will open a **Trench File
    Tabgroup**.]{style="color: rgb(0,0,0);"}
-   [**Existing Trench Files** are displayed under **Attached Trench
    Files** dropdown menu.]{style="color: rgb(0,0,0);"}

[Loci Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-LociTab}
------------------------------------------

-   Clicking the **Create New Locus** button opens new Locus Tabgroup,
    Tab General Information. 
-   All existing Loci are displayed under** List** **of Existing Loci**
    list.
-   Only the existing Loci belonging to the current Trench are displayed
    under** List** **of Existing Loci** list.
-   Tapping on Locus record in the **List of Existing Loci** will open
    the Locus record.

[Strata/Features Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-Strata/FeaturesTab}
-----------------------------------------------------

-   Clicking the **Create New Stratum/Feature** button opens new
    Stratum/Feature Tabgroup. 
-   All existing Strata/Feature records are displayed
    under** List** **of Existing Strata/Features** list.
-   Only the existing Strata/Feature records belonging to the current
    Trench are displayed under** List** **of Existing
    Strata/Features** list.
-   Tapping on Locus record in the **List** **of Existing
    Strata/Features** will open the Stratum/Feature record.

[FCNs Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-FCNsTab}
------------------------------------------

-   Clicking the **Create New FCN** button opens new FCN Tabgroup. 
-   All existing FCNs belonging to the current Trench are displayed
    under** List** **of Existing FCNs** list.
-   Only the existing FCNs belonging to the current Trench are displayed
    under** List** **of Existing FCNs** list.
-   Tapping on Locus record in the **List** **of Existing FCNs** will
    open the FCN record.

[Diaries Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-DiariesTab}
---------------------------------------------

-   Clicking the **Create New Diary** button opens new Locus Tabgroup,
    Tab General Information. 
-   All existing Diaries are displayed under** List** **of
    Existing **Diaries**** list.
-   Only the existing Diaries belonging to the current Trench are
    displayed under** List** **of Existing **Diaries**** list.
-   Tapping on Locus record in the **List** **of Existing
    ****Diaries****** will open the Diary record.

[Legacies Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-LegaciesTab}
----------------------------------------------

-   Clicking the **Create New Legacy** button opens new Legacy
    Tabgroup. 
-   All existing Legacies are displayed under** Listof
    Existing **Legacies**** list.
-   Only the existing Legacies belonging to the current Site are
    displayed under** Listof Existing **Legacies**** list.
-   Tapping on Locus record in the **List of
    Existing ****Legacies****** will open the Legacy record.

[[Locus Tabgroup]{.underline}]{style="color: rgb(0,0,0);"} {#CopyofHarvardExcavation2017RegressionTest-AW-LocusTabgroup}
==========================================================

-   When the tab group is shown, the navigation drawer is updated with
    the **New/Duplicate/Delete/Validate** buttons for the Site. 
-   When the tab group is shown, the current changes to the tab group
    are kept and auto-saving is initiated.

[General Information Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-GeneralInformationTab}
---------------------------------------------------------

-   **Site Name, Locus ID, Excavation Method** are styled in red and
    validated when [the **Validation** button is clicked in
    the **navigation
    drawer**]{style="color: rgb(0,0,0);"}[.]{style="color: rgb(0,0,0);"}
-   [**Trench ID, Locus ID, Record Created By, Record Created Date** are
    autopopulated from previous tabs and non-writable fields.\
    ]{style="color: rgb(0,0,0);"}
-   [[**Site Name, Date Opened** are autopopulated from previous
    tabs and can be modified.]{style="color: rgb(0,0,0);"}\
    ]{style="color: rgb(0,0,0);"}
-   [[**Locus Type** can be selected by clicking on any image of the
    picture
    dictionary.]{style="color: rgb(0,0,0);"}]{style="color: rgb(0,0,0);"}
    -   [[If the **Locus Type** is selected, clicking on the **Fill in
        Locus Type Details** will open a new Tab with corresponding
        Locus Type
        information.]{style="color: rgb(0,0,0);"}]{style="color: rgb(0,0,0);"}
-   [[Clicking **Add Date Closed** button will add current timestamp to
    the Date Closed
    field.]{style="color: rgb(0,0,0);"}]{style="color: rgb(0,0,0);"}
    -   [Once created, the ]{style="color: rgb(0,0,0);"}**Date Closed**[
        can be changed manually or by clicking the Add Date Closed
        button. ]{style="color: rgb(0,0,0);"}

[Measure Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-MeasureTab}
---------------------------------------------

-    **Absolute Height Top (m), Absolute Height Bottom (m), Length (m),
    Width (m), Depth (m), Volume (l)** are styled in red and
    validated when [the **Validation** button is clicked in
    the **navigation
    drawer**]{style="color: rgb(0,0,0);"}[.]{style="color: rgb(0,0,0);"}

[Locus Type Information Tab (Cut, Deposit, Natural, Construction, Skeleton Tab)]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-LocusTypeInformationTab(Cut,Deposit,Natural,Construction,SkeletonTab)}
----------------------------------------------------------------------------------------------------------------

-   Based on the selected **Locus Type** in the General Tab, the current
    tab will be called one of the following: **Cut, Deposit, Natural,
    Construction, Skeleton Tab**.

### Cut Locus Type {#CopyofHarvardExcavation2017RegressionTest-AW-CutLocusType}

-   **Your Interpretation, Shape in Plan, Shape of Corners, Break of
    Slope-Top, Break of Slope-Base, Sides of Cut, Shape of Base,
    Orentation, Orentation Degree, Inclination of Axis** are styled in
    red and validated when [the **Validation** button is clicked in
    the **navigation
    drawer**]{style="color: rgb(0,0,0);"}[.]{style="color: rgb(0,0,0);"}

### Deposit Locus Type {#CopyofHarvardExcavation2017RegressionTest-AW-DepositLocusType}

-   **Your Interpretation, Texture, Material, Deposit Structure,
    Bedding, Deposit Influsions** are styled in red and
    validated when [the **Validation** button is clicked in
    the **navigation
    drawer**]{style="color: rgb(0,0,0);"}[.]{style="color: rgb(0,0,0);"}
-   [Clicking on the **Material Helper** opens new Tab Material
    Helper.]{style="color: rgb(0,0,0);"}
    -   [Clicking on the **Material Helper** dropdown menu navigates
        user through the process of defining the material. By clicking
        to the appropriate values user can establish the type of
        Material.]{style="color: rgb(0,0,0);"}
    -   [Once the type of Material is established, clicking on the
        Update Material button will return to the Deposit Locus Type Tab
        and the field **Material** will be updated to the selected type
        of Material.]{style="color: rgb(0,0,0);"}
-   [Clicking on the **Add Munsel Color** button opens a new Add Soil
    Munsel Color Tab where user can select the appropriate Munsel color
    from the dropdown.]{style="color: rgb(0,0,0);"}[\
    ]{style="color: rgb(0,0,0);"}
    -   [Clicking the device\'s Back button will return back to the
        Deposit Locus Type Tab.]{style="color: rgb(0,0,0);"}
    -   [The added Munsel Colors can be displayed under the **Munsel
        Colors** dropdown menu.]{style="color: rgb(0,0,0);"}
-   [[Clicking on the **Add New Sediment/Aggregate** button opens a new
    Sediment/Aggregate Tab where user can enter the data about new
    Sediment/Aggregate.\
    ]{style="color: rgb(0,0,0);"}]{style="color: rgb(0,0,0);"}
-   Clicking the device\'s Back button will return back to the Deposit
    Locus Type Tab.
-   The added Munsel Colors can be displayed under the **Associated
    Sediment/Aggregates** dropdown menu.

### Natural Locus Type {#CopyofHarvardExcavation2017RegressionTest-AW-NaturalLocusType}

-   The information recorded in the **Natural Locus Type** is identical
    with the Deposit Locus Type information.

### Construction Locus Type {#CopyofHarvardExcavation2017RegressionTest-AW-ConstructionLocusType}

-   None of the fields is styled in red nor validated.

### Skeleton Locus Type {#CopyofHarvardExcavation2017RegressionTest-AW-SkeletonLocusType}

-   **Head, Body, Left Arm and Hand Location, Right Arm and Hand
    Location, Left Leg and Foot Location, Right Leg and Foot Location,
    Condition, Target A:X, Target A:Y, Target A:Z** are styled in red
    and validated when [the **Validation** button is clicked in
    the **navigation
    drawer**]{style="color: rgb(0,0,0);"}[.]{style="color: rgb(0,0,0);"}

[Intepretation Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-IntepretationTab}
---------------------------------------------------

-   **Your Description, Your Discussion** are styled in red and
    validated when [the **Validation** button is clicked in
    the **navigation
    drawer**]{style="color: rgb(0,0,0);"}[.]{style="color: rgb(0,0,0);"}

[Relationships Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-RelationshipsTab}
---------------------------------------------------

-   When the tab is shown the **Existing Relationships to This
    Locus ** list is automatically updated with all other Loci related
    to the current one.
-   Clicking the **Create Relationships to This Locus** button opens a
    new tabgroup **Relationships**. makes a hierarchical relationship
    between the current Context and selected Context, using the selected
    type of relationship.
-   The **Existing Relationships to This Locus **list shows the existing
    relationships to this **Locus**.
-   The **Existing Relationships to This Locus **list shows only the
    existing relationships to this **Locus**.
-   If there are no existing relationships, the **Existing Relationships
    to This Locus List** is empty. 
-   Clicking the **Existing Relationships to This Locus **list shows the
    selected existing relationships to this context on the right side
    under the **Selected Relationship** label.
-   Clicking the **Load Related Locus** the user be taken to the context
    it refers to.
-   Clicking the **Delete Relationship **button will delete the
    relationship between the current context and the selected context
    from the **Existing Relationships to This Locus l**ist.

[FCNs Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-FCNsTab.1}
------------------------------------------

-   Clicking the **Add FCN** button opens new FCN Tabgroup. 
-   All existing FCNs belonging to the current Locus are displayed
    under** List of Related FCNs** list.
-   Only the existing **FCNs** belonging to the current **Locus** are
    displayed under** List of Related FCNs** list.
-   Tapping on Locus record in the **List of FCNs** will open the Legacy
    record.

[Add Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-AddTab}
-----------------------------------------

-   Clicking the **Photo** button will open device\'s camera and use
    will be able to take photo.

    -   A thumbnail of a taken photo will de displayed.
    -   Clicking on the pencil icon next to the name of the photo will
        open Annotation widon where an annotation to the current photo
        can be written.

-   Clicking the **Attach File** button will attach the selected file to
    the context.

-   Clicking the **Take Photograph **button will allow a photo to be
    taken using the device camera and will then attach the selected
    photo to the context.

-   Clicking the **View Attached Files** button will list all the files
    attached to the context.

    -   Pressing the item from the list of attached files will display
        the full file with its contents, e.g. picture if the attachment
        is a photograph or an image, textfile if the attached file is a
        textfile.

-   Clicking the **Add Photo Log **button will create a new Photolog.

-   Selecting the Photolog from the **Select a Photograph Log** will
    load the selected Photolog.

-   Only the existing **Photo Logs** belonging to the current Locus are
    displayed in the **Select a Photograph Log** dropdown menu. 

[[Photo Log Tabgroup]{.underline}]{style="color: rgb(0,0,0);"} {#CopyofHarvardExcavation2017RegressionTest-AW-PhotoLogTabgroup}
==============================================================

-   -   When the tab group is shown, the current changes to the tab
        group are kept and auto-saving is initiated.

    -   **Locus ID** or **Stratum/Feature ID** contains autopopulated
        from previous tabs and non-writable values.
    -   **Photograph Reference ID** contains manually entered
        autonumeric values.\
        \

[[Relationships Tabgroup]{.underline}]{style="color: rgb(0,0,0);"} {#CopyofHarvardExcavation2017RegressionTest-AW-RelationshipsTabgroup style="background-image: none;"}
==================================================================

[Relationship Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-RelationshipTab}
--------------------------------------------------

-   [**Parent Identifier** displays the identifier of the current
    Locus.]{style="color: rgb(0,0,0);"}
-   [**Loci** from the current **Site** can be searched by entering the
    Trench ID and/or the Locus ID, the list of **Unrelated Loci** will
    be updated.]{style="color: rgb(0,0,0);"}
-   [Only [**Loci** from the current **Site** can be searched by
    entering the Trench ID and/or the Locus ID, the list
    of ]{style="color: rgb(0,0,0);"}**Unrelated Loci**[ will be
    updated.]{style="color: rgb(0,0,0);"}\
    ]{style="color: rgb(0,0,0);"}
    -   [After a **Trench ID** has been entered, clicking
        the **Search** button displays the filtered unrelated Loci and
        Legacies under **Unrelated
        Loci** list.]{style="color: rgb(0,0,0);"}
    -   [After a **Locus ID** has been entered, clicking
        the **Search** button displays the filtered unrelated Loci and
        Legacies under **Unrelated
        Loci** list.]{style="color: rgb(0,0,0);"}
    -   After a **Trench ID **[has been selected, clicking
        the ]{style="color: rgb(0,0,0);"}**Search**[ button displays the
        filtered Loci and Legacies with existing realtionship
        under ]{style="color: rgb(0,0,0);"}**Existing
        Relationships**[ list.]{style="color: rgb(0,0,0);"}
    -   [After a **Locus ID** has been selected, clicking
        the **Search** button displays the filtered Loci and Legacies
        with existing realtionship under **Existing
        Relationships** list.]{style="color: rgb(0,0,0);"}

    <!-- -->

    -   [If the **Search** button has not been clicked, the list of
        **Unrelated Loci** is empty.]{style="color: rgb(0,0,0);"}
    -   [If the **Search** button has not been clicked, the list of
        **Existing Realtionships** is
        empty.]{style="color: rgb(0,0,0);"}[\
        ]{style="color: rgb(0,0,0);"}

-   [Selecting from the **Relationship Type** dropdown menu enables to
    set the list of Relationship Type.]{style="color: rgb(0,0,0);"}
    -   [The default value for the **Relationship Type** is the last
        used **Relationship Type.** If none has been used before, the
        default value is **Child of**.]{style="color: rgb(0,0,0);"}
-   [Selecting a context from **Unrelated Loci** list will display the
    full length of Proposed Realtionship above, together with the
    selected Relationship Type.]{style="color: rgb(0,0,0);"}
-   [**Relationship Type** contains the following values: **Child of,
    Parent of, Arbitrarily separated from, Bonded to, Broadly
    contemporary with, Butted by, Butts, Covered by, Covers, Cuts, Cut
    by, Immediately Earlier Than, Immediately Later Than, Fill of,
    Filled with, Precisely Contemporary
    with.**]{style="color: rgb(0,0,0);"}
-   Clicking the **Add Relationship** button will add the **Proposed
    Relationship** into the **Existing Relationship** list.
-   The** **new relationship will appear in the **Existing
    Relationship** list only after the **Proposed Relationship** has
    been defined in its fulle lenght (an **Unrelated Locus** has been
    selected and **Relationship Type** has been defined) and the **Add
    Relationship** button has been clicked.
-   [Clicking the **Delete Relationship** button will delete
    relationship displayed under the label **Selected
    Relationship**.]{style="color: rgb(0,0,0);"}
    -   [The deleted relationship will disappear from the **Existing
        Relationship** list.]{style="color: rgb(0,0,0);"}[\
        ]{style="color: rgb(0,0,0);"}

[Legacies Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-LegaciesTab.1}
----------------------------------------------

-   [Clicking on the **Create New Legacy** button will open the Legacy
    Tabgroup where new Legacy can be
    created.]{style="color: rgb(0,0,0);"}
-   [List of Existing Legacies shows existing
    legacies.]{style="color: rgb(0,0,0);"}

[Legacy Tabgroup]{.underline} {#CopyofHarvardExcavation2017RegressionTest-AW-LegacyTabgroup}
=============================

[Legacy Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-LegacyTab}
--------------------------------------------

-   [**Site Name** is autopopulated from previous tabs and
    non-writable.]{style="color: rgb(0,0,0);"}
-   [**Year of Campaign** is [autopopulated from previous tabs and
    writable.]{style="color: rgb(0,0,0);"}]{style="color: rgb(0,0,0);"}
-   [[**Year of Campaign, Trench ID** and **Locus ID** are styled in
    red and validated when [the **Validation** button is clicked in
    the **navigation
    drawer**]{style="color: rgb(0,0,0);"}[.]{style="color: rgb(0,0,0);"}]{style="color: rgb(0,0,0);"}]{style="color: rgb(0,0,0);"}

[[Stratum/Feature Tabgroup]{.underline}]{style="color: rgb(0,0,0);"} {#CopyofHarvardExcavation2017RegressionTest-AW-Stratum/FeatureTabgroup}
====================================================================

-   When the tab group is shown, the navigation drawer is updated with
    the **New/Duplicate/Delete/Validate** buttons for the Context Group.
-   When the tab group is shown, the current changes to the tab group
    are kept and auto-saving is initiated.                              
                                      

[Stratum/Feature General Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-Stratum/FeatureGeneralTab}
-------------------------------------------------------------

-   The radiobutton Record Type has the following options: **Stratum,
    Feature.**
-   If **Feature** is selected:
    -   **Record Type, Feature Prefix, Stratum/Feature ID, Description,
        Interpretation** are styled in red and
        validated when [the **Validation** button is clicked in
        the **navigation
        drawer**]{style="color: rgb(0,0,0);"}[.]{style="color: rgb(0,0,0);"}
    -   [If **Feature Type** is selected and **Feature Prefix** is
        filled in, the values remain the same, even when user switches
        the Record Type between Stratum and
        Feature.]{style="color: rgb(0,0,0);"}
-   [If **Stratum** is selected:]{style="color: rgb(0,0,0);"}
    -   **Record Type, Stratum/Feature ID, Description,
        Interpretation** are styled in red and
        validated when [the **Validation** button is clicked in
        the **navigation
        drawer**]{style="color: rgb(0,0,0);"}[.]{style="color: rgb(0,0,0);"}
-   The **Date recorded** view is automatically populated with the
    current date and is read-only.
-   The **Record Created By** view is automatically populated with the
    current user\'s username and is read-only.

[Stratum/Feature Relationships Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-Stratum/FeatureRelationshipsTab}
-------------------------------------------------------------------

-   -   When the tab is shown the **Existing Relationships to This
        Stratum/Feature **list is automatically updated with all other
        Loci related to the current one. 
    -   Clicking the **Create Relationships to This
        **Stratum/Feature ****button opens a new
        tabgroup **Relationships**. makes a hierarchical relationship
        between the current Context and selected Context, using the
        selected type of relationship.
    -   The **Existing Relationships to This
        **Stratum/Feature ** **list shows the existing relationships to
        this Stratum/Feature.
    -   The **Existing Relationships to
        This **Stratum/Feature ** **list shows only the existing
        relationships to this Stratum/Feature.
    -   If there are no existing relationships, the **Existing
        Relationships to This **Stratum/Feature** List** is empty. 
    -   Clicking the **Existing Relationships to This
        **Stratum/Feature ** **list shows the selected existing
        relationships to this context on the right side under
        the **Selected Relationship** label.
    -   Clicking the **Load Related Locus** the user be taken to the
        context it refers to.
    -   Clicking the **Delete Relationship **button will delete the
        relationship between the current context and the selected
        context from the **Existing Relationships to This
        **Stratum/Feature** l**ist.

[Stratum/Feature Attachments Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-Stratum/FeatureAttachmentsTab}
-----------------------------------------------------------------

-   -   Clicking the **Attach File** button will attach the selected
        file to the context.

    -   Clicking the **Take Photograph **button will allow a photo to be
        taken using the device camera and will then attach the selected
        photo to the context.

    -   Clicking the **View Attached Files** button will list all the
        files attached to the context.

        -   Pressing the item from the list of attached files will
            display the full file with its contents, e.g. picture if the
            attachment is a photograph or an image, textfile if the
            attached file is a textfile.

    -   Clicking the **New Photo Log **button will create a new
        Photolog.

    -   Selecting the Photolog from the **Select a Photo Log** will load
        the selected Photolog.

    -   Only the existing **Photo Logs** belonging to the current
        **Stratum/Feature** are displayed in the **Select a Photograph
        Log** dropdown menu. 

[[Photolog Tabgroup]{.underline}]{style="color: rgb(0,0,0);"} {#CopyofHarvardExcavation2017RegressionTest-AW-PhotologTabgroup}
=============================================================

-   -   When the tab group is shown, the current changes to the tab
        group are kept and auto-saving is initiated.

    -   **Locus ID** or **Stratum/Feature ID** contains autopopulated
        from previous tabs and non-writable values. [No locus
        ID]{style="color: rgb(255,0,0);"}
    -   **Photograph Reference ID** contains manually entered
        autonumeric values.

[[Stratum/Feature Relationships Tabgroup]{style="color: rgb(0,0,0);"}]{.underline} {#CopyofHarvardExcavation2017RegressionTest-AW-Stratum/FeatureRelationshipsTabgroup}
==================================================================================

[Relationships Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-RelationshipsTab.1}
---------------------------------------------------

-   [**Parent Identifier** displays the identifier of the current
    Locus.]{style="color: rgb(0,0,0);"}
-   [**Loci** from the current **Site** can be searched by entering the
    Trench ID and/or the Locus ID, the list of **Unrelated Loci** will
    be updated. ]{style="color: rgb(0,0,0);"}
-   [Only [**Loci** from the current **Site** can be searched by
    entering the Trench ID and/or the Locus ID, the list
    of ]{style="color: rgb(0,0,0);"}**Unrelated Loci**[ will be
    updated.]{style="color: rgb(0,0,0);"}\
    ]{style="color: rgb(0,0,0);"}
    -   [After a **Trench ID** has been entered, clicking
        the **Search** button displays the filtered unrelated Loci and
        Legacies under **Unrelated
        Loci** list.]{style="color: rgb(0,0,0);"}
    -   [After a **Locus ID** has been entered, clicking
        the **Search** button displays the filtered unrelated Loci and
        Legacies under **Unrelated
        Loci** list.]{style="color: rgb(0,0,0);"}
    -   After a **Trench ID **[has been selected, clicking
        the ]{style="color: rgb(0,0,0);"}**Search**[ button displays the
        filtered Loci and Legacies with existing realtionship
        under ]{style="color: rgb(0,0,0);"}**Existing
        Relationships**[ list.]{style="color: rgb(0,0,0);"}
    -   [After a **Locus ID**[ has been selected, clicking
        the ]{style="color: rgb(0,0,0);"}**Search**[ button displays the
        filtered Loci and Legacies with existing realtionship
        under ]{style="color: rgb(0,0,0);"}**Existing
        Relationships**[ list.]{style="color: rgb(0,0,0);"}\
        ]{style="color: rgb(0,0,0);"}
    -   [If the **Search** button has not been clicked, the list
        of **Unrelated Loci** is empty.]{style="color: rgb(0,0,0);"}
    -   [If the **Search** button has not been clicked, the list
        of **Existing Realtionships** is
        empty.]{style="color: rgb(0,0,0);"}[\
        ]{style="color: rgb(0,0,0);"}
-   [Selecting a context from **Unrelated Loci** list will display the
    full length of Proposed Realtionship above, together with the
    selected Relationship Type.]{style="color: rgb(0,0,0);"}
-   [**Relationship Type** is set as default to
    \'**includes\'.**]{style="color: rgb(0,0,0);"}
-   Clicking the **Add Relationship** button will add the **Proposed
    Relationship** into the **Existing Relationship** list.
-   The** **new relationship will appear in the** Existing
    Relationship** list only after the** Proposed Relationship** has
    been defined in its fulle lenght (an **Unrelated Locus** has been
    selected and **Relationship Type** has been defined) and the **Add
    Relationship** button has been clicked.
-   [Clicking the **Delete Relationship** button will delete
    relationship displayed under the label **Selected
    Relationship**.]{style="color: rgb(0,0,0);"}
    -   [The deleted relationship will disappear from the **Existing
        Relationship** list. [Only after pressing the search button a
        second
        time]{style="color: rgb(255,0,0);"}]{style="color: rgb(0,0,0);"}

[Legacies Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-LegaciesTab.2}
----------------------------------------------

-   [Clicking on the **Create New Legacy** button will open the **Legacy
    Tabgroup** where new Legacy can be
    created.]{style="color: rgb(0,0,0);"}
-   [List of Existing Legacies shows existing
    legacies.]{style="color: rgb(0,0,0);"}

[Legacy Tabgroup]{.underline} {#CopyofHarvardExcavation2017RegressionTest-AW-LegacyTabgroup.1}
=============================

[Legacy Tab]{style="color: rgb(51,51,153);"} {#CopyofHarvardExcavation2017RegressionTest-AW-LegacyTab.1}
--------------------------------------------

\

-   [**Site Name** is autopopulated from previous tabs and
    non-writable.]{style="color: rgb(0,0,0);"}
-   [**Year of Campaign** is autopopulated from previous tabs and
    writable.]{style="color: rgb(0,0,0);"}
-   [**Year of Campaign, Trench ID** and **Locus ID** are styled in
    red and validated when the **Validation** button is clicked in
    the **navigation drawer**.]{style="color: rgb(0,0,0);"}\
    \

</div>

Attachments
-----------
