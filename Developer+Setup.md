FAIMS Mobile Platform Documentation (FAIMS): Developer Setup
============================================================

::: {style="font-size:70%; color:#444; font-style: italic"}
Created: Former user (Deleted) () - 2013-08-26T16:58:21.917Z

Last Updated: Matthew Smith () - 2016-09-06T04:53:19.587Z
:::

<div>

Android App Development {#DeveloperSetup-AndroidAppDevelopment}
=======================

### Requirements {#DeveloperSetup-Requirements}

-   Android Studio
-   Oracle Java JDK 1.7
-   Git

### Instructions {#DeveloperSetup-Instructions}

1.  Install JDK
2.  Install Git
3.  Checkout faims-android repo *(git clone
    <https://github.com/FAIMS/faims-android> ./faims-android)*\
    *Make sure you use the correct branch you are developing/testing
    for.*
4.  Install android studio
5.  Configure android studio to work with git *(File \> Settings.. \>
    Version Control \> Git \> Path to Git executable)*
6.  Configure the sdk manager *(Tools \> Android \> SDK Manager \>
    Launch Standalone SDK Manager).*\
    Install everything except the system images and preview sdk\'s
7.  Turn off instant run *(F[ile \> Settings \> Build, execution,
    deployment \> Instant run \> untick the top
    checkbox]{style="color: rgb(0,0,0);text-decoration: none;"})*
8.  Create project from existing faims-android repo
9.  Configure `keystore.properties` for apk signing
10. Run a gradle sync *(Tools \> Android \> Sync project with gradle
    files)*
11. Run a Clean *(Build \> Clean Project)*
12. Run a Build *(Build \> Rebuild Project Project)*

### Build App {#DeveloperSetup-BuildApp}

1.  Connect android device via USB
2.  Make sure android device has USB Debugging enabled
3.  Right-Click faims-android-app and select Run

### Run Tests {#DeveloperSetup-RunTests}

1.  Right-Click the test module in
    *./faimsandroidapp/src/androidTest/java/au/org/intersect/faims/android/test*
    you which to use and select Run

### Build a community apk {#DeveloperSetup-Buildacommunityapk}

1.  Setup a faims server with your community module
2.  Run *packageModule.rb* with options for your community module and
    server
3.  Run a gradle sync *(Tools \> Android \> Sync project with gradle
    files)*
4.  Run a Clean *(Build \> Clean Project)*
5.  Run a Build *(Build \> Rebuild Project Project)*
6.  Run Build APK or Generate Signed APK (*Build \> Build APK or
    Generate Signed APK*)

Web App Development {#DeveloperSetup-WebAppDevelopment}
===================

### Requirements {#DeveloperSetup-Requirements.1}

-   [Installing Spatialite on
    Ubuntu](https://wiki.intersect.org.au/display/FAIMS/Installing+Spatialite+on+Ubuntu){.external-link}
-   [Installing Spatialite Tools on
    Ubuntu](https://wiki.intersect.org.au/display/FAIMS/Installing+Spatialite+Tools+on+Ubuntu){.external-link}
-   [Installing GDAL
    Tools](https://wiki.intersect.org.au/display/FAIMS/Installing+GDAL+Tools){.external-link}
-   You will need to have RVM installed on your system.

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="80b541d5-e57a-433b-88c9-8cf428aed44d"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
\curl -L https://get.rvm.io | bash -s stable --ruby
```
:::
:::

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="f259d720-a726-45c4-a2a9-14a12dc1027a"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
You should check for rvm requirements and install them!
:::
:::

### Install Server {#DeveloperSetup-InstallServer}

-   Install Server

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="e9de1eb3-80f5-47b4-9b07-6d5bfbfcf3f7"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
rvm install ruby-1.9.3-p286
rvm use 1.9.3-p286@faims --create
gem install bundler
git clone git@github.com:IntersectAustralia/faims-web.git
cd faims-web
bundle install
```
:::
:::

-   Setup and Start Server

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="0a337c5d-3e51-46a4-9a5e-2e5832a5a584"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
cd faims-web
rake db:drop db:create db:migrate db:seed projects:setup projects:clean db:test:prepare
foreman start
```
:::
:::

-   For more server usage commands follow the [Developer
    Setup](../FAIMS/Developer+Setup.html) guide

### Troubleshooting {#DeveloperSetup-Troubleshooting}

::: {.confluence-information-macro .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="4ddc29f8-5ea1-410c-b7e5-60b7eb6ce680"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-error
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
This is no longer relevant as Unicorn is used as the dev and production
server.
:::
:::

-   If webrick seems to be taking way to long to serve documents try
    editing its config (and if you use rvm that will be somewhere that
    looks like
    \~/.rvm/rubies/ruby-1.9.3-p286/lib/ruby/1.9.1/webrick/config.rb) and
    change the DoNotReverseLookup value from nil to true.

</div>

Attachments
-----------
