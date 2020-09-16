Testing Methodology
================================================================





This guide specifies the method used for testing a completed module.

Step-by-step guide
------------------

1.  Begin by thoroughly cleaning up the code. Note that all unused code
    should be deleted/commented out, all utility functions should be
    moved the bottom and all code related to specific archents should be
    grouped together. Ensure your code is commented (at minimum
    describing each section).
2.  Next, we should begin exploratory testing of the UI. This will
    involve;
    1.  Creating a new module on the server (to ensure we are working on
        a clean database).
    2.  Ensuring we are testing on the debug version of the apk
        (otherwise there will not be any helpful messages in monitor).
    3.  Testing every field and every button on every page of the UI.
        Any bugs found here should be fixed.
3.  Finally, once you are certain the UI is behaving as expected, step
    line by line through the UI Logic, cross checking each line of code
    with each element on the Android device, and ensuring that the code
    instructs that element to behave as is expected.

-   

    Page:

    </div>

    [Testing Methodology](../Testing+Methodology)


</div>
