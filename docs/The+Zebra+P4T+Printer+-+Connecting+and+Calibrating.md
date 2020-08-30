The Zebra P4T Printer - Connecting and Calibrating
===============================================================================================


Created: Christian Nassif-Haynes (Unlicensed) (christian\@fedarch.org) -
2017-09-19T09:17:24.186Z

Last Updated: Christian Nassif-Haynes (Unlicensed)
(christian\@fedarch.org) - 2017-09-19T13:31:09.368Z




Connecting
========================================

1.  Use `hcitool scan` to find the MAC address of the
    printer.
2.  Create a file at /etc/bluetooth/rfcomm.conf which contains the
    following contents:

        rfcomm0

    Make sure to replace \"00:07:80:44:4F:37\" with the MAC address of
    the printer.

3.  Run `sudo rfcomm connect rfcomm0 00:07:80:44:4F:37`. Make sure to
    replace \"00:07:80:44:4F:37\" with the MAC address of the
    printer.
4.  Use [this](http://sourceforge.net/p/pyserial/code/HEAD/tree/trunk/pyserial/serial/tools/miniterm.py)
    Python script to connect to the printer like
    so:

        sudo ./miniterm.py /dev/rfcomm0

    Ensure that the baud rate of the shell matches the baud rate of the
    printer.

5.  [Run the following command by pasting it into the terminal and
    pressing the return key:

        ! 0 200 200 210 1
        TEXT 4 0 200 40 Hello World
        FORM
        PRINT

    The printer should print a label containing the text \'Hello
    World\'.

Calibrating
=========================================

The printer can be calibrated for use with the installed media by
following [these instructions](https://km.zebra.com/kb/index?page=content&id=SO7452).
Note that although the instructions mention a CONFIG.SYS file, simply
running the following command was enough to calibrate our device for use
with gap media:

    ! U1 setvar "media.sense_mode" "gap"
    ! U1 setvar "device.languages" "zpl"
    ~jc^xa^jus^xz

We tested this command using 75.0mm x 25.0mm (w x h) thermal transfer
paper with a 19 mm core and no
perforations.

If this command ran successfully, the printer should feed the labels
through in regular intervals so that the label\'s gap is lined up with
the printer\'s cutter. In other words, pressing the feed button should
feed exactly one label.



</div>
