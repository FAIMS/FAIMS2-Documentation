FAIMS Mobile Platform Documentation (FAIMS): Unit Testing for Modules
=====================================================================

::: {style="font-size:70%; color:#444; font-style: italic"}
Created: Christian Nassif-Haynes (Unlicensed) (christian\@fedarch.org) -
2017-11-02T02:33:50.053Z

Last Updated: Christian Nassif-Haynes (Unlicensed)
(christian\@fedarch.org) - 2017-11-10T06:09:45.552Z
:::

<div>

Overview {#UnitTestingforModules-Overview}
========

This wiki article describes how to implement unit tests for modules
created using FAIMS-Tools.

FAIMS-Tools generates files for unit testing whenever a module is
compiled. These are placed in the `tests` directory, relative to your
`module.xml` file:

    $ tree /path/to/module
    /path/to/module
    ├── module
    │   ├── data_schema.xml
    │   ├── english.0.properties
    │   ├── ui_logic.bsh
    │   ├── ui_schema.xml
    │   ├── ui_styling.css
    │   └── validation.xml
    ├── module.xml
    └── tests
        ├── mock
        │   ├── mock.bsh
        │   └── ...
        ├── ModuleUtil.java
        ├── test.bsh
        └── test.sh

Of note are `mock.bsh` and `test.bsh`. (`ModuleUtil.java` is used for UI
testing, which is outside the scope of this wiki article.)

mock.bsh {#UnitTestingforModules-mock.bsh}
--------

`mock.bsh` contains function and class definitions. For modules that run
within the FAIMS APK, these functions would ordinarily be defined by
[ui\_commands.bsh](https://github.com/FAIMS/faims-android/blob/master/faimsandroidapp/src/main/assets/ui_commands.bsh){.external-link}.
However, instead of running in the FAIMS APK, unit tests run on the
desktop, directly from within the Beanshell interpreter.

The functions defined in `mock.bsh` are not very true-to-life; The
primary purpose of this file is to allow the module\'s `ui_logic.bsh`
file to run during a test without triggering exceptions due to undefined
functions.

test.bsh {#UnitTestingforModules-test.bsh}
--------

`test.bsh` executes the unit tests. (This involves running the scripts
`mock.bsh`, `ui_logic.bsh` and `test.bsh`, respectively.) The `test.bsh`
script itself should be invoked by running `test.sh` (which initialises
Java\'s `CLASSPATH` variable.)

Running a Trivial Test {#UnitTestingforModules-RunningaTrivialTest}
======================

Suppose that our module has the following directory structure:

    $ tree /path/to/module
    /path/to/module
    ├── module
    │   ├── data_schema.xml
    │   ├── english.0.properties
    │   ├── ui_logic.bsh
    │   ├── ui_schema.xml
    │   ├── ui_styling.css
    │   └── validation.xml
    ├── module.xml
    └── tests
        ├── mock
        │   ├── mock.bsh
        │   └── ...
        ├── ModuleUtil.java
        ├── test.bsh
        └── test.sh

Suppose also that our current working directory is `path/to/module`.
Now, we\'d like to run our unit tests, so we execute `tests/test.sh`
from the terminal. Assuming that our ui\_logic.bsh file can run without
exceptions, we will see something like the following:

    $ tests/test.sh
    === ALL VARIABLES STARTING WITH 'REF' CONTAIN VALID REFS ===

    === NO TESTS IMPLEMENTED. TESTS SHOULD BE PLACED IN `tests/tests.bsh`. ===

Clearly we need to write some tests. To do so, we create the file
`tests/tests.bsh` with the following contents:

    print("a");
    assert(true);
    print("b");
    assert(false);
    print("c");

In FAIMS unit tests, the `assert(boolean)` function is used to verify a
condition. If the condition evaluates to `false`, an exception is
thrown, an error message is printed, and execution of `tests/test.bsh`
stops. In fact, any uncaught exception causes `tests/test.bsh` to stop
and the tests to fail. Now, if we run `tests/test.sh` again, we get the
following output:

    === ALL VARIABLES STARTING WITH 'REF' CONTAIN VALID REFS ===

    a
    b
    Sourced file: /tmp/tmp/tests/tests.bsh : TargetError : at Line: 49 : in file: /tmp/tmp/module/ui_logic.bsh : throw new Exception ( msg ) ; 

    Called from method: assert : at Line: 4 : in file: /tmp/tmp/tests/tests.bsh : assert ( false ) 
    Target exception: java.lang.Exception: Test failed: Line: 4: assert ( false ) . CallStack:
        NameSpace: assert (bsh.NameSpace@24273305) (method) 
        NameSpace: global (bsh.NameSpace@5b1d2887)


    === ONE OR MORE TESTS FAILED ===

Notice that we only see the output from the print functions before
`print("c")`, an assertion failed before that print statement had a
chance to execute. If we replace `assert("false")` with
`assert("true")`, our unit tests all succeed:

    $ tests/test.sh
    === ALL VARIABLES STARTING WITH 'REF' CONTAIN VALID REFS ===

    a
    b
    c
    === ALL TESTS PASSED ===

Testing Code from ui\_logic.bsh {#UnitTestingforModules-TestingCodefromui_logic.bsh}
===============================

Because `test.bsh` runs the code from `ui_logic.bsh` before running
`tests.bsh`, we can call any of the functions defined in `ui_logic.bsh`
from within `tests.bsh`. For instance, if we wanted to test a function
defined in `ui_logic.bsh` called `banana(String)`, which should return
the `String` \"om nom\" if the input argument was the `String`
\"banana\", and \"ew\" otherwise, our `tests.bsh` might be the
following:

    assert("om nom".equals(banana("banana" )));
    assert("ew"    .equals(banana("spinach")));
    assert("ew"    .equals(banana("BANANA!")));

Mocking by Redefining Functions {#UnitTestingforModules-MockingbyRedefiningFunctions}
===============================

Functions in Beanshell can be redefined. This allows their functionality
to be mocked at test time. It is often useful to write something like
the following in unit tests:

    {
      boolean mockedFunction() {
        return true; // Let's see how returning TRUE affects dependent code
      }
      // Call functions which depend on mockedFunction
      // Assert stuff
    }

    {
      boolean mockedFunction() {
        return false; // Now let's see how returning FALSE affects dependent code
      }
      // Call functions which depend on mockedFunction again
      // Assert more stuff
    }

Useful Functions {#UnitTestingforModules-UsefulFunctions}
================

-   `assert(boolean)` -- Defined in `ui_logic.bsh`. Verifies that a
    condition is true.
-   `executeOnEvent(String, String)` -- Defined in `ui_logic.bsh`.
    Triggers functions that would ordinarily happen upon an event.
-   `getDisplayedTabGroup(String)` -- Defined in `ui_logic.bsh`.
    Sometimes calling `executeOnEvent` is meant to result in a change of
    tab groups. Depending on the way you\'ve written your module, using
    `getDisplayedTabGroup(String)` can help to verify that the tab group
    has changed.
-   `getFieldValue(String)` -- Defined in `mock.bsh`. Allows a mock
    field value to be set.
-   `getStdout(Callable)` -- Defined in `test.bsh`. Captures stdout
    during execution of the `Callable` argument and returns it as a
    string. This is useful for capturing the output of functions which
    would normally produce messages in logcat. A [Beanshell scripted
    object](http://www.beanshell.org/manual/objects.html){.external-link}
    can be used in place of a `Callable` as long as it defines a
    `void run()` method.
-   `setFieldValue(String, Object)` -- Defined in `mock.bsh`. Allows a
    mock field value to be set.
-   `showToast(String)` -- Defined in `mock.bsh`. The mocked version of
    this function directs its output to stdout.
-   `showWarning(String, String)` -- Defined in `mock.bsh`. The mocked
    version of this function directs its output to stdout.
-   `Fetch.useDatabase(String)` -- Defined in `Fetch.java`. Uses the
    database whose path is provided as the argument in order to execute
    `fetchAll` and `fetchOne` queries. If the empty string is given as
    the argument, or `useDatabase(String)` wasn\'t called, a transient
    in-memory database is used.
-   `Fetch.importFromDatabase(String)` -- Defined in `Fetch.java`.
    Imports data from the database whose path is provided as the
    argument. The imported data is added to the database given by
    `Fetch.useDatabase(String)`.

Many of the functions defined by the autogen under the \"DOCUMENT OBJECT
MODEL\" section of `ui_logic.bsh` are useful.

Advantages of This Unit Testing Methodology {#UnitTestingforModules-AdvantagesofThisUnitTestingMethodology}
===========================================

Testing as described herein confers all the usual befits of unit
testing.

Additionally, a key advantage of this testing methodology is that (with
some caveats) the `ui_logic.bsh` file is run on the development machine.
Not having to upload the logic to a server and download it to a device
allows for vastly hastened development, especially on large modules.

Limitations of This Unit Testing Methodology {#UnitTestingforModules-LimitationsofThisUnitTestingMethodology}
============================================

A major limitation of this testing approach is that records cannot be
saved on the development machine. In principle is it possible to
recreate the behaviour of `saveArchEnt` by using `fetchAll` or
`fetchOne`, however this is inconvenient in practice.

In general, most functions defined in `mock.bsh` do not behave exactly
as they would when the module runs in the FAIMS APK. It is incumbent
upon the developer to ensure that the mocked functions really do mock
the desired behaviour of the FAIMS APK.

</div>

Attachments
-----------
