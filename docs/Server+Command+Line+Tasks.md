FAIMS Mobile Platform Documentation (FAIMS): Server Command Line Tasks
======================================================================

::: {style="font-size:70%; color:#444; font-style: italic"}
Created: Brian Ballsun-Stanton (brian\@faims.edu.au) -
2016-06-09T02:59:29.999Z

Last Updated: Matthew Smith () - 2016-09-06T03:00:47.922Z
:::

<div>

Server Command Line Tasks {#ServerCommandLineTasks-ServerCommandLineTasks}
=========================

Use this guide to run common server tasks with the following commands.
They must be run from inside the faims-web project directory (default:
`/var/www/faims`) and require bundle exec to run (eg:
`bundle exec rake about`).

\

::: {.confluence-information-macro .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="7108c0cd-f8fa-42b1-97f7-f0286295bdda"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-error
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
**Commands highlighted red are dangerous and could result in data loss
or client problems.\
**
:::
:::

::: {.confluence-information-macro .confluence-information-macro-note .conf-macro .output-block data-hasbody="true" data-macro-name="note" data-macro-id="49a3ccf2-f12b-4281-966a-21a691c47c96"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-warning
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
**Commands highlighted yellow stop services that faims needs to
function.**
:::
:::

**\
**

Rake {#ServerCommandLineTasks-Rake}
----

List all rake commands\
**rake -T**

List versions of all Rails frameworks and the environment\
**rake about**

### Admin {#ServerCommandLineTasks-Admin}

Enter new admin password**\
rake admin:password**

### App** ** {#ServerCommandLineTasks-App}

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="95f7c056-4820-42ba-946f-ef0243fe9730"}
::: {.confluence-information-macro-body}
Generating new secret**\
rake app:generate\_secret\
**
:::
:::

### Assets {#ServerCommandLineTasks-Assets}

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="062b7d6b-1e53-4e1d-95bc-05abb80ca62e"}
::: {.confluence-information-macro-body}
Remove compiled assets**\
rake assets:clean**
:::
:::

Compile all the assets named in config.assets.precompile\
**rake assets:precompile**

### Cucumber {#ServerCommandLineTasks-Cucumber}

Alias for cucumber:ok\
**rake cucumber**

Run all features\
**rake cucumber:all**

Run features that should pass\
**rake cucumber:ok**

Record failing features and run only them if any exist\
**rake cucumber:rerun**

Run features that are being worked on\
**rake cucumber:wip**

### Database {#ServerCommandLineTasks-Database}

Backup the database\
**rake db:backup**

show pending migrations\
**rake db:cat\_pending\_migrations**

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="42237bff-878a-42b0-9bff-02269fe2657e"}
::: {.confluence-information-macro-body}
Create the database from DATABASE\_URL or config/database.yml for the
current Rails.env (use db:create:all to create all dbs\...\
**rake db:create**
:::
:::

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="799d609b-7f2a-4021-81b5-858d82239eb0"}
::: {.confluence-information-macro-body}
Drops the database using DATABASE\_URL or the current Rails.env (use
db:drop:all to drop all databases)\
**rake db:drop**
:::
:::

Load fixtures into the current environment\'s database\
**rake db:fixtures:load**

Migrate the database (options: VERSION=x, VERBOSE=false)\
**rake db:migrate**

Display status of migrations\
**rake db:migrate:status**

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="c9dae957-ef00-4aa8-8644-e0cba03f6a8c"}
::: {.confluence-information-macro-body}
Populate the database with some sample data for testing\
**rake db:populate**
:::
:::

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="6d93c4f0-e9b9-49c5-a016-48a029684bf0"}
::: {.confluence-information-macro-body}
Rolls the schema back to the previous version (specify steps w/ STEP=n)\
**rake db:rollback**
:::
:::

Create a db/schema.rb file that can be portably used against any DB
supported by AR\
**rake db:schema:dump**

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="2dabb4c8-c48e-4230-a71b-f660c1c06aba"}
::: {.confluence-information-macro-body}
Load a schema.rb file into the database\
**rake db:schema:load**
:::
:::

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="b26dac37-51f6-476d-a578-76e7bc780424"}
::: {.confluence-information-macro-body}
Load the seed data from db/seeds.rb\
**rake db:seed**
:::
:::

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="112b6886-da46-4f49-818b-1b1d5390fcc1"}
::: {.confluence-information-macro-body}
Create the database, load the schema, and initialize with the seed data
(use db:reset to also drop the db first)\
**rake db:setup**
:::
:::

Dump the database structure to db/structure.sql\
**rake db:structure:dump**

Backup the database\
**rake db:trim\_backups**

Retrieves the current schema version number\
**rake db:version**

### Discovery {#ServerCommandLineTasks-Discovery}

Start discovery server\
**rake discovery:start\[background\]**\
***\[background\]** is a optional parameter\
*

Get status of discovery server\
**rake discovery:status**

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-note .conf-macro .output-block data-hasbody="true" data-macro-name="note" data-macro-id="8c5aa29d-ba6c-4f54-a13b-4e8059ecdf22"}
::: {.confluence-information-macro-body}
Stop discover server\
**rake discovery:stop**
:::
:::

### Doc {#ServerCommandLineTasks-Doc}

Generate docs for the app \-- also available doc:rails, doc:guides,
doc:plugins (options: TEMPLATE=/rdoc-template.rb, TITLE=\...\
**rake doc:app**

### Exporters {#ServerCommandLineTasks-Exporters}

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="3ceb3929-e34d-4f28-96f0-5415ce021d26"}
::: {.confluence-information-macro-body}
Clear all exporters**\
rake exporters:clear**
:::
:::

Install an exporter from a give tarball**\
rake exporters:install exporter=\</path/to/exporter/tarball\>**

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="4a649b86-feec-44f2-ab92-2bf73dda096d"}
::: {.confluence-information-macro-body}
Uninstall an exporter with the given key**\
rake exporters:uninstall key=\<key of exporter\>**
:::
:::

### Jobs {#ServerCommandLineTasks-Jobs}

Exit with error status if any jobs older than max\_age seconds haven\'t
been attempted yet\
**rake jobs:check\[max\_age\]**

Clear the delayed\_job queue\
**rake jobs:clear**

Start a delayed\_job worker\
**rake jobs:work**

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-note .conf-macro .output-block data-hasbody="true" data-macro-name="note" data-macro-id="27261165-2fd8-44ea-b157-0a2a00703806"}
::: {.confluence-information-macro-body}
Start a delayed\_job worker and exit when all available jobs are
complete\
**rake jobs:workoff**
:::
:::

### Log {#ServerCommandLineTasks-Log}

Truncates all \*.log files in log/ to zero bytes\
**rake log:clear**

### Merge daemon {#ServerCommandLineTasks-Mergedaemon}

Start daemon to merge project module databases\
**rake merge\_daemon:start\[background\]**\
***\[background\]** is a optional parameter*

Get status of daemon\
**rake merge\_daemon:status**

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-note .conf-macro .output-block data-hasbody="true" data-macro-name="note" data-macro-id="6f3d1b1f-4345-4d1d-83c2-0963e9c7fbb2"}
::: {.confluence-information-macro-body}
Stop daemon\
**rake merge\_daemon:stop**
:::
:::

### Middleware {#ServerCommandLineTasks-Middleware}

Prints out your Rack middleware stack\
**rake middleware**

### Modules {#ServerCommandLineTasks-Modules}

Archive all modules**\
rake modules:archive**

Archive a specific module**\
rake modules:archive key=\<key of module\>**

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="2d29bfdf-72a2-49f4-8489-5f2a7364553c"}
::: {.confluence-information-macro-body}
Clear all modules**\
rake modules:clear**\
*Note: these cannot be restored at a later time*
:::
:::

Create a module from a given tarball\
**rake modules:create module=\</path/to/module/tarball\>**

Delete a module with the given key. This module can be restored later if
needed\
**rake modules:delete key=\<key of module\>**

Restore module from archive\
**rake modules:restore file=\<path to file tarball\>**

::: {.confluence-information-macro .confluence-information-macro-information .conf-macro .output-block data-hasbody="true" data-macro-name="info" data-macro-id="46065fb0-4251-43b7-81bc-11bd97c0ea1b"}
[ ]{.aui-icon .aui-icon-small .aui-iconfont-info
.confluence-information-macro-icon}

::: {.confluence-information-macro-body}
All module:settings have 2 modes, read and set, depending if the
**value=** optional parameter is given. If it is excluded the value will
be read from the current state, if it is given the new value will be
set.
:::
:::

Change module client sponsor\
**rake modules:settings:client\_sponsor key=\<key of module\>
value=\<new value\>**

Change module contact address\
**rake modules:settings:contact\_address key=\<key of module\>
value=\<new value\>**

Change module copyright holder\
**rake modules:settings:copyright\_holder key=\<key of module\>
value=\<new value\>**

Change module description\
**rake modules:settings:description key=\<key of module\> value=\<new
value\>**

Change module has sensitive data\
**rake modules:settings:has\_sensitive\_data key=\<key of module\>
value=\<new value\>**

Change module land owner\
**rake modules:settings:land\_owner key=\<key of module\> value=\<new
value\>**

Change module name or retrieve module name/keys\
**rake modules:settings:name key=\<key of module\> value=\<new value\>**

Change module participant\
**rake modules:settings:participant key=\<key of module\> value=\<new
value\>**

Change module permit holder\
**rake modules:settings:permit\_holder key=\<key of module\> value=\<new
value\>**

Change module permit issued by\
**rake modules:settings:permit\_issued\_by key=\<key of module\>
value=\<new value\>**

Change module permit no\
**rake modules:settings:permit\_no key=\<key of module\> value=\<new
value\>**

Change module permit type\
**rake modules:settings:permit\_type key=\<key of module\> value=\<new
value\>**

Change module season\
**rake modules:settings:season key=\<key of module\> value=\<new
value\>**

Change module SRID\
**rake modules:settings:srid key=\<key of module\> value=\<new value\>**

Change module version\
**rake modules:settings:version key=\<key of module\> value=\<new
value\>**

Setup project module assets\
**rake modules:setup**

Generate test project modules\
**rake modules:test:create\[size\]**

Undelete module\
**rake modules:undelete**

Upload module files\
**rake modules:upload**

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="b4cf2f4a-0c27-466a-8a59-b0759f31b32a"}
::: {.confluence-information-macro-body}
Wipe a specific module including its files and database relationships\
**rake modules:wipe**
:::
:::

### Notes {#ServerCommandLineTasks-Notes}

Enumerate all annotations (use notes:optimize, :fixme, :todo for focus)\
**rake notes**

Enumerate a custom annotation, specify with ANNOTATION=CUSTOM\
**rake notes:custom**

### Rails {#ServerCommandLineTasks-Rails}

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="857a779f-ef55-4894-8d5b-7e649334f001"}
::: {.confluence-information-macro-body}
Applies the template\
**rake rails:template LOCATION=\</path/to/template\> or \<URL\>**
:::
:::

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="25958db2-f746-4385-8ae9-4fd62b13876a"}
::: {.confluence-information-macro-body}
Update configs and some other initially generated files (or use just
update:configs, update:scripts, or update:application\
**rake rails:update**
:::
:::

### Routes {#ServerCommandLineTasks-Routes}

Print out all defined routes in match order, with names\
**rake routes**

### Secret {#ServerCommandLineTasks-Secret}

Generate a cryptographically secure secret key (this is typically used
to generate a secret for cookie sessions)\
**rake secret**

### Server {#ServerCommandLineTasks-Server}

Check for server updates. This will check if there are updates available
from by examining the latest source code.\
**rake server:check\_for\_updates**

Initialise server with a uuid\
**rake server:setup**

Update server. This will update the server to the latest version.\
**rake server:update**

### Spec {#ServerCommandLineTasks-Spec}

Run all specs in spec directory (excluding plugin specs)\
**rake spec**

Run the code examples in spec/controllers\
**rake spec:controllers**

Run the code examples in spec/models\
**rake spec:models**

Run the code examples in spec/queries\
**rake spec:queries**

Run the code examples in spec/tools\
**rake spec:tools**

### Stats {#ServerCommandLineTasks-Stats}

Report code statistics (KLOCs, etc) from the application\
**rake stats**

### Test {#ServerCommandLineTasks-Test}

Runs test:units, test:functionals, test:integration together (also
available: test:benchmark, test:profile, test:plugins)\
**rake test**

Run tests for {:recent=\>\"test:prepare\"} / Test recent changes\
**rake test:recent**

Run tests for {:single=\>\"test:prepare\"}\
**rake test:single**

Run tests for {:uncommitted=\>\"test:prepare\"} / Test changes since
last checkin (only Subversion and Git)\
**rake test:uncommitted**

### Time {#ServerCommandLineTasks-Time}

Displays all time zones, also available: time:zones:us, time:zones:local
\-- filter with OFFSET parameter, e.g., OFFSET=-6\
**rake time:zones:all**

### Tmp {#ServerCommandLineTasks-Tmp}

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="af17df6c-3fe7-44df-b9b1-c23200295b1a"}
::: {.confluence-information-macro-body}
Clear session, cache, and socket files from tmp/ (narrow w/
tmp:sessions:clear, tmp:cache:clear, tmp:sockets:clear)\
**rake tmp:clear**
:::
:::

Creates tmp directories for sessions, cache, sockets, and pids\
**rake tmp:create**

### Users {#ServerCommandLineTasks-Users}

Create a user. This will then prompt you for a first name, last name,
email and password. Note: The password must be 6-20 characters and
contain at least one uppercase letter, one lowercase letter, one digit
and one symbol\
**rake users:create**

::: {.confluence-information-macro .has-no-icon .confluence-information-macro-warning .conf-macro .output-block data-hasbody="true" data-macro-name="warning" data-macro-id="4a799f7e-d7f4-48f4-aac0-d9d6b43abe95"}
::: {.confluence-information-macro-body}
Delete a user with the given email\
**rake users:delete email=\<user email\>**
:::
:::

</div>

Attachments
-----------
