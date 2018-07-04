Electrum-NMC - Lightweight Namecoin client
=====================================

::

  Licence: GNU GPLv3+ for Electrum-DOGE components; MIT Licence for all other components
  Author: The Namecoin developers; based on Electrum by Thomas Voegtlin and Electrum-DOGE by The Electrum-DOGE contributors
  Language: Python
  Homepage: https://www.namecoin.org/ ; original Electrum Homepage at https://electrum.org/


.. image:: https://travis-ci.org/namecoin/electrum-nmc.svg?branch=master
    :target: https://travis-ci.org/namecoin/electrum-nmc
    :alt: Build Status
.. image:: https://coveralls.io/repos/github/namecoin/electrum-nmc/badge.svg?branch=master
    :target: https://coveralls.io/github/namecoin/electrum-nmc?branch=master
    :alt: Test coverage statistics
.. image:: https://img.shields.io/badge/help-translating-blue.svg
    :target: https://crowdin.com/project/electrum
    :alt: Help translating Electrum online





Getting started
===============

Electrum-NMC is a pure python application. If you want to use the
Qt interface, install the Qt dependencies::

    sudo apt-get install python3-pyqt5

If you downloaded the official package (tar.gz), you can run
Electrum-NMC from its root directory, without installing it on your
system; all the python dependencies are included in the 'packages'
directory. To run Electrum-NMC from its root directory, just do::

    ./electrum-nmc

You can also install Electrum-NMC on your system, by running this command::

    sudo apt-get install python3-setuptools
    pip3 install .[fast]

This will download and install the Python dependencies used by
Electrum-NMC, instead of using the 'packages' directory.
The 'fast' extra contains some optional dependencies that we think
are often useful but they are not strictly needed.

If you cloned the git repository, you need to compile extra files
before you can run Electrum-NMC. Read the next section, "Development
Version".



Development version
===================

Check out the code from GitHub::

    git clone git://github.com/namecoin/electrum-nmc.git
    cd electrum-nmc

Run install (this should install dependencies)::

    pip3 install .[fast]

Render the SVG icons to PNGs (optional)::

    for i in lock unlock confirmed status_lagging status_disconnected status_connected_proxy status_connected status_waiting preferences; do convert -background none icons/$i.svg icons/$i.png; done

Compile the icons file for Qt::

    sudo apt-get install pyqt5-dev-tools
    pyrcc5 icons.qrc -o gui/qt/icons_rc.py

Compile the protobuf description file::

    sudo apt-get install protobuf-compiler
    protoc --proto_path=lib/ --python_out=lib/ lib/paymentrequest.proto

Create translations (optional)::

    sudo apt-get install python-requests gettext
    ./contrib/make_locale




Creating Binaries
=================


To create binaries, create the 'packages' directory::

    ./contrib/make_packages

This directory contains the python dependencies used by Electrum-NMC.

Mac OS X / macOS
--------

See `contrib/build-osx/`.

Windows
-------

See `contrib/build-wine/`.


Android
-------

See `gui/kivy/Readme.txt` file.
