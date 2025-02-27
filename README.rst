.. image:: http://www.blinkstick.com/images/logos/blinkstick-python.png
   :alt: BlinkStick Python

BlinkStick Python interface to control devices connected to the
computer.

Modified by RetroRodent to include convenient features and fixes left languishing on the seemingly abandoned official repo.

===========
Fixes included:
===========

-  pull_35 delmic: Update .get_string() call to follow latest pyusb convension
-  pull_45 jmtd: Add trailing newline to udev rule
-  pull_50 dakotacody: Added function to return a random hex
-  pull_56 dpiche174: Fix misplaced closing parenthesis
-  pull_58 jiceher: Fix issue #57 : check for device while get serial
-  pull_72 StefanUlbrich: Fix error in adding udev rule
-  pull_75 chaddcw: fix intensity scaling in blink, pulse, and morph
-  pull_80 PureTryOut: Changed dependency on pyusb to accept anything higher than 1.0.0
-  pull_81 PureTryOut: Make sure to use python3


What is BlinkStick? It's a smart USB LED pixel. More info about it here:

http://www.blinkstick.com

===========
 Resources
===========

- `Code repository on GitHub <https://github.com/arvydas/blinkstick-python>`_
- `API reference documentation <https://arvydas.github.io/blinkstick-python>`_
- `Code Examples <https://github.com/arvydas/blinkstick-python/wiki>`_

==============
 Requirements
==============

-  Python
-  BlinkStick pip module
-  Libusb for Mac OSX

===========================
 Requirements Installation
===========================

Linux
=====

Install pip (Python package management software):

::

    sudo apt-get install python-pip

Mac OS X
========

Install libusb with `homebrew <http://mxcl.github.io/homebrew/>`_:

::

    brew install libusb

Install pip

::

    sudo easy_install pip

Known Errors
------------

::

    ValueError: No backend available

This means that the Python usb module cannot find your installation of libusb.
It seems to be an issue when you have ``homebrew`` installed somewhere that is
not expected.

It can be mitigated with

::

    sudo ln -s `brew --prefix`/lib/libusb-* /usr/local/lib/

Microsoft Windows
=================

* Download and install `Python <https://www.python.org/downloads/>`_ 2.7.9 or any later version
* During the installation, make sure you select "Add python.exe to Path" to install on local hard drive

Python 2.7.9 and later already comes with pip making it very easy to install BlinkStick Python package on Windows. 

=================================
 BlinkStick package Installation
=================================

Linux and Mac OS X
==================

Install blinkstick Python package with pip:

::

    sudo pip install blinkstick


Microsoft Windows
=================

Open commandline environment by using Win+R keyboard shortcut and typing in:

::

    cmd

Assuming that Python was installed into C:\\Python27 folder, type in the 
following into the command window:

::

    C:\Python27\Scripts\pip.exe install blinkstick

===================
 Command line tool
===================

Together with the Python module an additional command line tool is
installed to control BlinkSticks. 

::

    blinkstick --pulse red


You can find more details about command line tool options and usage 
examples in the `wiki <https://github.com/arvydas/blinkstick-python/wiki>`_.

===========================================
 Permission problems in Linux and Mac OS X
===========================================

If the script returns with an error

::

    Access denied (insufficient permissions)

You can either run the script with sudo, for example:

::

    sudo blinkstick --set-color random 

Or you can add a udev rule to allow any user to access the device
without root permissions with this single command.

::

    sudo blinkstick --add-udev-rule

There is also another equivalent command that does exactly the same thing:

::

    echo "SUBSYSTEM==\"usb\", ATTR{idVendor}==\"20a0\", ATTR{idProduct}==\"41e5\", MODE:=\"0666\"" | sudo tee /etc/udev/rules.d/85-blinkstick.rules

Reboot computer after you have added the command and all users will have
permissions to access the device without the need of root permissions.

=============
 Maintainers
=============

-  Arvydas Juskevicius - http://twitter.com/arvydev
-  Rob Berwick - http://twitter.com/robberwick

