Translate Toolkit
-----------------

.. image:: https://travis-ci.org/translate/translate.png
    :alt: Build Status
    :target: https://travis-ci.org/translate/translate

The Translate Toolkit is a set of software and documentation designed to help
make the lives of localizers both more productive and less frustrating.
The Toolkit is part of the translate.sourceforge.net project,
hosted at <http://translate.sourceforge.net/>.

The software includes programs to covert localization formats to the common
PO, and emerging XLIFF format.  There are also programs to check and manage PO
and XLIFF files.  Online documentation includes guides on using the tools,
running a localization project and how to localize various projects from
OpenOffice.org to Mozilla.

At its core the software contains a set of classes for handling various
localization storage formats: DTD, properties, OpenOffice.org GSI/SDF,
CSV, MO, Qt .ts, TMX, TBX, WordFast txt, Gettext .mo, Windows RC, and
of course PO and XLIFF.  It also provides scripts to convert between
these formats.

Also part of the Toolkit are Python programs to create word counts, merge
translations and perform various checks on translation files.


Download
--------
The latest version of the Translate Toolkit can be downloaded from:
<http://sourceforge.net/projects/translate/files/Translate%20Toolkit/>.

The latest documentation is always available at
http://docs.translatehouse.org/projects/translate-toolkit/en/latest/
(Documentation is also included in the doc directory).


Copying
-------
The Translate Toolkit is developed and Copyright::

	Zuza Software Foundation (Translate.org.za), and
	St James Software

and is released under the GPL license.

The Translate Toolkit Documentation is Copyright::

	Dwayne Bailey
	Javier SOLA
	David Fraser
	Friedel Wolff
	and others

and is released under the GPL.

Where useful emails have been quoted we have attempted to preserve the authors
name and assume that their work may be republished.

Joining the Translate Project
-----------------------------
If you would like to join the translate project mailing list then visit:
<http://lists.sourceforge.net/lists/listinfo/translate-devel>.

The vision of the Translate Project is to be a meta project for localizers
built on the premise that your language deserves to be a project on its own
right not a poor cousin of the main project.

Most projects are inattentive to the needs and difficulties experienced by
localizers. To that end the aim is to work towards creating tools and
documentation that allows localizers to focus on what they do best: translating
software.

Requirements
------------

.. note:: Please check ``requirements/*.txt``::

       pip install -r requirements/recommended.txt

   Will install all recommended requirements, while ``optional.txt`` will also
   install support for all other formats.

Python 2.4 or later is recommended.

The Toolkit should still work with Python 2.4 but is now most extensively
tested using Python 2.7.

The package lxml is needed for XML file processing. Version 1.3.4 and upwards
should work, but lxml 2.1.0 or later is strongly recommended. <http://lxml.de/>
Depending on your platform, the easiest way to install might be through your
system's package management. Alternatively you can try ::

    easy_install lxml

which should install the newest version from the web. See the easy_install
documentation for more details on how to force installation of a certain
version, or to specify upgrade options, etc.

For Mac OSX, the following pages might be of help:
<http://lxml.de/build.html#building-lxml-on-macos-x>
<http://lxml.de/installation.html#macos-x>

The package lxml has dependencies on libxml2 and libxslt. Please check the lxml
site for the recommended versions of these libraries if you need to install
them separately at all. Most packaged versions of lxml will already contain
these dependencies.

When the environment variable USECPO is set to 1, the toolkit will attempt to
use libgettextpo from the gettext-tools package (it might have a slightly
different name on your distribution). This can greatly speed up access to PO
files, but has not yet been tested as extensively. Feedback is most welcome.

The package iniparse is necessary for ini2po and po2ini.
http://code.google.com/p/iniparse/

The python-Levenshtein package will improve performance for fuzzy matching if
it is available. This can improve the performance of pot2po, for example.  It
is optional and no functionality is lost if it is not installed, only speed.
<http://sourceforge.net/projects/translate/files/python-Levenshtein/>

Functions in the lang.data module can supply functions to translate language
names using the iso-codes package. It can even translate names in the format
``Language (Country)``
such as
``English (South Africa)``
This is used by Pootle and Virtaal. If the package is not installed, the
language names will simply appear in English. It is therefore recommended you
install the iso-codes package for your distribution, but it is optional.
Alternatively, it is also available from
http://packages.debian.org/unstable/source/iso-codes

The package vobject is needed for ical2po and po2ical.  Versions from
0.6.0 have been tested, 0.6.5 is required to fix an issue related to
Lotus Notes calendars. <http://vobject.skyhouseconsulting.com/>

The aeidon package (or gaupol if aeidon is not available) is needed for sub2po
and po2sub. Some Unicode encoded files (including most files from
<http://dotsub.com/>) require version 0.14 or later.
<http://home.gna.org/gaupol/>
Gaupol might need the 'Universal Encoding Detector'
<http://pypi.python.org/pypi/chardet>

Trados TXT TM support requires the BeautifulSoup parser
<http://www.crummy.com/software/BeautifulSoup/>

The programs have been tested on Linux and Windows.


Installation
------------

To install the Translate Toolkit

*   Windows

    Double click on translate-toolkit-N.N-setup.exe (the larger download file).
    This installer contains all dependencies you will need, including Python. To
    use any of the command line tools, just type their name in a command window.
    For example::

        moz2po --version

    Alternatively you can install the smaller translate-toolkit-N.N.N.win32.exe
    This needs an existing Python installation, and assumes you will install all
    the dependencies yourself. You will probably need to edit your PATH
    environment variable to be able to use the tools in any command window.

*   Linux ::

        tar xzf translate-N.N.tar.gz
        cd translate-N.N
        su -c ./setup.py install

    If you get an error along the lines of ::

        Unable to open /usr/lib/python2.N/config/Makefile (no such file or directory)

    while running setup.py, you need to install python-dev or libpython2.N-devel
    package. Try to install python2.N-dev or libpython2.N-devel or something
    similar with your distribution's package manager.


Bugs
----
We think there might be some :)

Please send your bug reports to:
translate-devel at lists.sourceforge.net
or report them at our bugzilla server at
<http://bugs.locamotion.org/>

Some help in writing useful bug reports are mentioned here:
<http://translate.sourceforge.net/wiki/developers/reporting_bugs>

Documentation
-------------
Please read our documentation online at
http://docs.translatehouse.org/projects/translate-toolkit/en/latest/.
There they are constantly being updated. Please feel free to contribute new
sections and suggest corrections.

Most tools support the options ``--help`` and ``--manpage`` of which the output
is automatically generated. The output of ``--manpage`` produces output suitable
for formatting as a standard manpage. This can be viewed on UNIX platforms with
::

    nroff -Tutf8 -mandoc

With pot2po as example::

    pot2po --manpage | nroff -Tutf8 -mandoc | less

This is probably most useful for packagers to help them generate manual pages
for the packaged versions.

Program overview
----------------

Use ``--help`` to find the syntax and options for all programs.

* Converters::

        oo2po    - convert between OpenOffice.org GSI files and PO
        oo2xliff - convert between OpenOffice.org GSI files and XLIFF
        moz2po   - convert between Mozilla files and PO
        csv2po   - convert PO format to CSV for editing in a spreadsheet program
        php2po   - PHP localisable string arrays converter.
        ts2po    - convert Qt Linguist (.ts) files to PO
        txt2po   - convert simple text files to PO
        html2po  - convert HTML to PO (beta)
        xliff2po - XLIFF (XML Localisation Interchange File Format) converter
        prop2po  - convert Java .properties files to PO
        po2wordfast - Wordfast Translation Memory converter
        po2tmx   - TMX (Translation Memory Exchange) converter
        pot2po   - PO file initialiser
        csv2tbx  - Create TBX (TermBase eXchange) files from Comma Separated
                   Value (CSV) files
        ini2po   - convert .ini files to to PO
        ical2po  - Convert iCalendar files (*.ics) to PO
        sub2po   - Convert many subtitle files to PO

* Tools (Quality Assurance)::

        pofilter - run any of the 40+ checks on your PO files
        pomerge  - merge corrected translations from pofilter back into
                   your existing PO files.
        poconflicts - identify conflicting use of terms
        porestructure - restructures po files according to poconflict directives
        pogrep   - find words in PO files

* Tools (Other)::

        pocompile - create a Gettext MO files from PO or XLIFF files
        pocount   - count translatable file formats (PO, XLIFF)
        podebug   - Create comment in your PO files' msgstr which can
                    then be used to quickly track down mistranslations
                    as the comments appear in the application.
        posegment - Break a PO or XLIFF files into sentence segments,
                    useful for creating a segmented translation memory.
        poswap    - uses a translation of another language that you
                    would rather use than English as source language
        poterminology - analyse PO or POT files to build a list of
                        frequently occurring words and phrases
