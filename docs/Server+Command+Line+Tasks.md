Server Command Line Tasks
======================================================================



Server Command Line Tasks
=========================

Use this guide to run common server tasks with the following commands.
They must be run from inside the faims-web project directory (default:
`/var/www/faims`) and require bundle exec to run (eg:
`bundle exec rake about`).


**Commands highlighted red are dangerous and could result in data loss
or client problems**

**Commands highlighted yellow stop services that faims needs to
function.**

Rake
----

List all rake commands
**rake -T**

List versions of all Rails frameworks and the environment
**rake about**

### Admin

Enter new admin password**
rake admin:password**

### App


Generating new secret
**rake app:generate_secret**


### Assets


Remove compiled assets
**rake assets:clean**

Compile all the assets named in config.assets.precompile
**rake assets:precompile**

### Cucumber

Alias for cucumber:ok
**rake cucumber**

Run all features
**rake cucumber:all**

Run features that should pass
**rake cucumber:ok**

Record failing features and run only them if any exist
**rake cucumber:rerun**

Run features that are being worked on
**rake cucumber:wip**

### Database

Backup the database
**rake db:backup**

show pending migrations
**rake db:cat_pending_migrations**

Create the database from DATABASE_URL or config/database.yml for the
current Rails.env (use db:create:all to create all dbs...
**rake db:create**


Drops the database using DATABASE_URL or the current Rails.env (use
db:drop:all to drop all databases)
**rake db:drop**


Load fixtures into the current environment's database
**rake db:fixtures:load**

Migrate the database (options: VERSION=x, VERBOSE=false)
**rake db:migrate**

Display status of migrations
**rake db:migrate:status**

Populate the database with some sample data for testing
**rake db:populate**

Rolls the schema back to the previous version (specify steps w/ STEP=n)
**rake db:rollback**


Create a db/schema.rb file that can be portably used against any DB
supported by AR
**rake db:schema:dump**


Load a schema.rb file into the database
**rake db:schema:load**

Load the seed data from db/seeds.rb
**rake db:seed**

Create the database, load the schema, and initialize with the seed data
(use db:reset to also drop the db first)
**rake db:setup**


Dump the database structure to db/structure.sql
**rake db:structure:dump**

Backup the database
**rake db:trim_backups**

Retrieves the current schema version number
**rake db:version**

### Discovery

Start discovery server
**rake discovery:start[background]**
**[background]** is a optional parameter


Get status of discovery server
**rake discovery:status**


Stop discover server
**rake discovery:stop**

### Doc

Generate docs for the app -- also available doc:rails, doc:guides,
doc:plugins (options: TEMPLATE=/rdoc-template.rb, TITLE=...
**rake doc:app**

### Exporters


Clear all exporters
**rake exporters:clear**


Install an exporter from a give tarball
**rake exporters:install exporter=</path/to/exporter/tarball>**


Uninstall an exporter with the given key
**rake exporters:uninstall key=<key of exporter>**


### Jobs

Exit with error status if any jobs older than max_age seconds haven't
been attempted yet
**rake jobs:check [max_age]**

Clear the delayed_job queue
**rake jobs:clear**

Start a delayed_job worker
**rake jobs:work**


Start a delayed_job worker and exit when all available jobs are
complete
**rake jobs:workoff**

### Log

Truncates all *.log files in log/ to zero bytes
**rake log:clear**

### Merge daemon

Start daemon to merge project module databases
**rake merge_daemon:start[background]**
***[background]** is a optional parameter*

Get status of daemon
**rake merge_daemon:status**

Stop daemon
**rake merge_daemon:stop**

### Middleware

Prints out your Rack middleware stack
**rake middleware**

### Modules

Archive all modules**
rake modules:archive**

Archive a specific module**
rake modules:archive key=<key of module>**

Clear all modules**
rake modules:clear**
*Note: these cannot be restored at a later time*

Create a module from a given tarball
**rake modules:create module=</path/to/module/tarball>**

Delete a module with the given key. This module can be restored later if
needed
**rake modules:delete key=<key of module>**

Restore module from archive
**rake modules:restore file=<path to file tarball>**


All module:settings have 2 modes, read and set, depending if the
**value=** optional parameter is given. If it is excluded the value will
be read from the current state, if it is given the new value will be
set.

Change module client sponsor
**rake modules:settings:client_sponsor key=<key of module>
value=<new value>**

Change module contact address
**rake modules:settings:contact_address key=<key of module>
value=<new value>**

Change module copyright holder
**rake modules:settings:copyright_holder key=<key of module>
value=<new value>**

Change module description
**rake modules:settings:description key=<key of module> value=<new
value>**

Change module has sensitive data
**rake modules:settings:has_sensitive_data key=<key of module>
value=<new value>**

Change module land owner
**rake modules:settings:land_owner key=<key of module> value=<new
value>**

Change module name or retrieve module name/keys
**rake modules:settings:name key=<key of module> value=<new value>**

Change module participant
**rake modules:settings:participant key=<key of module> value=<new
value>**

Change module permit holder
**rake modules:settings:permit_holder key=<key of module> value=<new
value>**

Change module permit issued by
**rake modules:settings:permit_issued_by key=<key of module>
value=<new value>**

Change module permit no
**rake modules:settings:permit_no key=<key of module> value=<new
value>**

Change module permit type
**rake modules:settings:permit_type key=<key of module> value=<new
value>**

Change module season
**rake modules:settings:season key=<key of module> value=<new
value>**

Change module SRID
**rake modules:settings:srid key=<key of module> value=<new value>**

Change module version
**rake modules:settings:version key=<key of module> value=<new
value>**

Setup project module assets
**rake modules:setup**

Generate test project modules
**rake modules:test:create[size]**

Undelete module
**rake modules:undelete**

Upload module files
**rake modules:upload**

Wipe a specific module including its files and database relationships
**rake modules:wipe**

### Notes

Enumerate all annotations (use notes:optimize, :fixme, :todo for focus)
**rake notes**

Enumerate a custom annotation, specify with ANNOTATION=CUSTOM
**rake notes:custom**

### Rails

Applies the template
**rake rails:template LOCATION=</path/to/template> or <URL>**

Update configs and some other initially generated files (or use just
update:configs, update:scripts, or update:application
**rake rails:update**

### Routes

Print out all defined routes in match order, with names
**rake routes**

### Secret

Generate a cryptographically secure secret key (this is typically used
to generate a secret for cookie sessions)
**rake secret**

### Server

Check for server updates. This will check if there are updates available
from by examining the latest source code.
**rake server:check_for_updates**

Initialise server with a uuid
**rake server:setup**

Update server. This will update the server to the latest version.
**rake server:update**

### Spec

Run all specs in spec directory (excluding plugin specs)
**rake spec**

Run the code examples in spec/controllers
**rake spec:controllers**

Run the code examples in spec/models
**rake spec:models**

Run the code examples in spec/queries
**rake spec:queries**

Run the code examples in spec/tools
**rake spec:tools**

### Stats

Report code statistics (KLOCs, etc) from the application
**rake stats**

### Test

Runs test:units, test:functionals, test:integration together (also
available: test:benchmark, test:profile, test:plugins)
**rake test**

Run tests for  / Test recent changes
**rake test:recent**

Run tests for
**rake test:single**

Run tests for  / Test changes since
last checkin (only Subversion and Git)
**rake test:uncommitted**

### Time

Displays all time zones, also available: time:zones:us, time:zones:local
-- filter with OFFSET parameter, e.g., OFFSET=-6
**rake time:zones:all**

### Tmp

Clear session, cache, and socket files from tmp/ (narrow w/
tmp:sessions:clear, tmp:cache:clear, tmp:sockets:clear)
**rake tmp:clear**

Creates tmp directories for sessions, cache, sockets, and pids
**rake tmp:create**

### Users

Create a user. This will then prompt you for a first name, last name,
email and password. Note: The password must be 6-20 characters and
contain at least one uppercase letter, one lowercase letter, one digit
and one symbol
**rake users:create**

Delete a user with the given email
**rake users:delete email=<user email>**

</div>
