FAIMS Mobile Platform Documentation (FAIMS): Developer Usage
============================================================

::: {style="font-size:70%; color:#444; font-style: italic"}
Created: Former user (Deleted) () - 2013-08-25T18:34:49.664Z

Last Updated: Brian Ballsun-Stanton (brian\@faims.edu.au) -
2016-09-23T07:09:48.934Z
:::

<div>

Developer Usage {#DeveloperUsage-DeveloperUsage}
===============

This page describes how to use the server and android app.

### Recreating the server database {#DeveloperUsage-Recreatingtheserverdatabase}

-   Open a terminal and navigate to the root folder of the rails app

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="33b42598-7e0e-450a-8fcf-55c4c94fcef4"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
rake app:generate_secret db:drop db:create db:migrate db:seed modules:setup modules:clean db:test:prepare # the last option is for running tests
```
:::
:::

### Dev Server Startup {#DeveloperUsage-DevServerStartup}

-   To run the server and setup the background processes use the
    following command

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="c394fc8d-47cc-4bb7-af90-5ecf696fa30a"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
foreman start
```
:::
:::

### Production Server Startup {#DeveloperUsage-ProductionServerStartup}

-   To run the server in production use the following

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="67ef524a-5f17-4446-9354-35bda7d0bec9"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
rake assets:precompile
foreman start -f Procfile.production
```
:::
:::

### Change Admin Password {#DeveloperUsage-ChangeAdminPassword}

-   To change the admin password use the following command

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="5557c400-1614-4c72-8c16-c3e6fecc307f"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
$ rake admin:password
```
:::
:::

### Server Update {#DeveloperUsage-ServerUpdate}

-   Open a terminal and navigate to the root folder of the rails app

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="5bf80a8d-eeb9-498b-928a-1917108b6433"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
git pull
rake db:migrate db:test:prepare
```
:::
:::

### Cleaning up projects {#DeveloperUsage-Cleaningupprojects}

-   Open a terminal and navigate to the root folder of the rails app

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="05d580a2-6c2d-40f9-afee-005b00b416d8"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
rake modules:clear
```
:::
:::

### Clearing locks in projects {#DeveloperUsage-Clearinglocksinprojects}

-   Open a terminal and navigate to the root folder of the rails app

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="fbc3c4e9-6f61-449a-8f79-1cd816ff6e78"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
rake modules:clear_lock
```
:::
:::

### Archiving projects {#DeveloperUsage-Archivingprojects}

-   To archive projects for download by the app use the following

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="69e19793-7c87-43d4-9eb6-4348b181f9c2"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
rake modules:archive
```
:::
:::

or to archive a single project use the following

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="85f41a88-c3ca-4298-9eb7-6cea2d286214"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
rake modules:archive[key] # key is the uuid of the project
```
:::
:::

### Validate schemas {#DeveloperUsage-Validateschemas}

-   Open terminal and navigate to the faims-web folder

::: {.code .panel .pdl .conf-macro .output-block style="border-width: 1px;" data-hasbody="true" data-macro-name="code" data-macro-id="29ccd6b2-32d8-4816-b380-d09d05bbf1c2"}
::: {.codeContent .panelContent .pdl}
``` {.syntaxhighlighter-pre data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence"}
rails c
irb(main):001:0> XSDValidator.validate_ui_schema('${absolute_path_to_ui_schema_xml}')
irb(main):002:0> XSDValidator.validate_data_schema('${absolute_path_to_data_schema_xml}')
```
:::
:::

\

</div>

Attachments
-----------
