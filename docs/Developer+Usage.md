---
title: Developer Usage
---


This page describes how to use the server and android app.

### Recreating the server database

-   Open a terminal and navigate to the root folder of the rails app


```
rake app:generate_secret db:drop db:create db:migrate db:seed modules:setup modules:clean db:test:prepare # the last option is for running tests
```

### Dev Server Startup

-   To run the server and setup the background processes use the
    following command

```
foreman start
```


### Production Server Startup

-   To run the server in production use the following


```
rake assets:precompile
foreman start -f Procfile.production
```


### Change Admin Password

-   To change the admin password use the following command


```
$ rake admin:password
```


### Server Update

-   Open a terminal and navigate to the root folder of the rails app


```
git pull
rake db:migrate db:test:prepare
```



### Cleaning up projects

-   Open a terminal and navigate to the root folder of the rails app



```
rake modules:clear
```

### Clearing locks in projects

-   Open a terminal and navigate to the root folder of the rails app



```
rake modules:clear_lock
```



### Archiving projects

-   To archive projects for download by the app use the following



```
rake modules:archive
```



or to archive a single project use the following



```
rake modules:archive[key] # key is the uuid of the project
```


### Validate schemas

-   Open terminal and navigate to the faims-web folder


```
rails c
irb(main):001:0> XSDValidator.validate_ui_schema('$')
irb(main):002:0> XSDValidator.validate_data_schema('$')
```




</div>
