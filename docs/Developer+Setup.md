---
title: Developer Setup
---


Android App Development
=======================

### Requirements

-   Android Studio
-   Oracle Java JDK 1.7
-   Git

### Instructions

1.  Install JDK
2.  Install Git
3.  Checkout [faims-android repo](https://github.com/FAIMS/faims-android)  
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
    checkbox])*
8.  Create project from existing faims-android repo
9.  Configure `keystore.properties` for apk signing
10. Run a gradle sync *(Tools \> Android \> Sync project with gradle
    files)*
11. Run a Clean *(Build \> Clean Project)*
12. Run a Build *(Build \> Rebuild Project Project)*

### Build App

1.  Connect android device via USB
2.  Make sure android device has USB Debugging enabled
3.  Right-Click faims-android-app and select Run

### Run Tests

1.  Right-Click the test module in
    *./faimsandroidapp/src/androidTest/java/au/org/intersect/faims/android/test*
    you which to use and select Run

### Build a community apk

1.  Setup a faims server with your community module
2.  Run *packageModule.rb* with options for your community module and
    server
3.  Run a gradle sync *(Tools \> Android \> Sync project with gradle
    files)*
4.  Run a Clean *(Build \> Clean Project)*
5.  Run a Build *(Build \> Rebuild Project Project)*
6.  Run Build APK or Generate Signed APK (*Build \> Build APK or
    Generate Signed APK*)

Web App Development
===================

### Requirements

-   [Installing Spatialite on
    Ubuntu](https://wiki.intersect.org.au/display/FAIMS/Installing+Spatialite+on+Ubuntu)
-   [Installing Spatialite Tools on
    Ubuntu](https://wiki.intersect.org.au/display/FAIMS/Installing+Spatialite+Tools+on+Ubuntu)
-   [Installing GDAL
    Tools](https://wiki.intersect.org.au/display/FAIMS/Installing+GDAL+Tools)
-   You will need to have RVM installed on your system.



```
\curl -L https://get.rvm.io | bash -s stable --ruby
```


You should check for rvm requirements and install them!


### Install Server

-   Install Server



```
rvm install ruby-1.9.3-p286
rvm use 1.9.3-p286@faims --create
gem install bundler
git clone git@github.com:IntersectAustralia/faims-web.git
cd faims-web
bundle install
```



-   Setup and Start Server



```
cd faims-web
rake db:drop db:create db:migrate db:seed projects:setup projects:clean db:test:prepare
foreman start
```



-   For more server usage commands follow the [Developer
    Setup](../FAIMS/Developer+Setup.html) guide

### Troubleshooting



This is no longer relevant as Unicorn is used as the dev and production
server.

-   If webrick seems to be taking way to long to serve documents try
    editing its config (and if you use rvm that will be somewhere that
    looks like
    \~/.rvm/rubies/ruby-1.9.3-p286/lib/ruby/1.9.1/webrick/config.rb) and
    change the DoNotReverseLookup value from nil to true.

</div>
