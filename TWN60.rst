======================================================
Tahoe-LAFS Weekly News, issue number 60, March 22 2016
======================================================

Welcome to the Tahoe-LAFS Weekly News (TWN).  Tahoe-LAFS_ is a secure,
distributed storage system. `View TWN on the web`_ *or* `subscribe to
TWN`_.
If you would like to view the "new and improved" TWN, complete with pictures;
please take a `look`_.

.. _Tahoe-LAFS: https://tahoe-lafs.org
.. _View TWN on the web:
  https://tahoe-lafs.org/trac/tahoe-lafs/wiki/TahoeLAFSWeeklyNews
.. _subscribe to TWN:
  https://tahoe-lafs.org/cgi-bin/mailman/listinfo/tahoe-lafs-weekly-news
.. _look: https://tahoe-lafs.org/~marlowe/TWN60.html


Announcements and News
======================

First alpha tagged: 1.11.0a1
----------------------------

Brian Warner `announced`_ the first alpha release of 1.11.0. The main feature
of this release is the use of pip to install Tahoe. Please test early and often.

.. _`announced`:
 `https://tahoe-lafs.org/pipermail/tahoe-dev/2016-March/009697.html

State of donations, new bitcoin address
---------------------------------------

In a tale that must be read to be believed, Brian `described`_ the rather
harrowing tale of Tahoe-LAFS' bitcoins. Please see `here`_ if you would like to
donate to Tahoe-LAFS.

.. _`described`:
  https://tahoe-lafs.org/pipermail/tahoe-dev/2016-March/009695.html
.. _`here`:
  https://github.com/tahoe-lafs/tahoe-lafs/blob/master/docs/donations.rst

Packaging/release updates
-------------------------

The close of `#1582`_ marks the end of an era. The new `scheme`_ is just plain tox.
Everything installs with pip. Run it in a virtualenv. Brian detailed the
remaining issues with the build slaves. We wil need to resolve these issues
before the release.

.. _`#1582`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/1582
.. _`scheme`:
  https://tahoe-lafs.org/pipermail/tahoe-dev/2016-March/009687.html

Rightscon
---------

Patrick will be at `Rightscon`_ next week. Please drop him a line and say hi.
He would love to hear what you like about TWN, what new things you would like
to see added, and how you are using Tahoe-LAFS.

.. _`Rightscon`: https://rightscon.org

Nuts and Bolts
==============

Nuts and Bolts is held regularly at 1700Z on Tuesdays and Fridays. Check in IRC
for the URI of the meeting. A special thanks to Brian Warner for taking notes as
I was unavailable due to DST and Hangout issues.

Friday, 03/18
-------------

We raised the setuptools dependency from 0.6, because Daira had an old
environment with some ancient version (0.9.8), and something wanted a
less-ancient one (>=1.0), but somehow it failed to update properly. I raised it
to 20.3, since that's the latest version, but Daira pointed out that that might
make things difficult for packagers, especially Debian/Ubuntu releases that have
an older one. We don't actually need much out of setuptools for *running* Tahoe.
We settled on ">=11.3", since the "cryptography" package wants that too (so
there's no point in allowing anything older than that). Debian/jesse (via
backports), Debian/stretch, and Ubuntu/vivid all meet this. Ubuntu/trusty (aka
14.04 LTS, the most recent LTS until 16.06 ships next month) does not, so
backporting Tahoe to trusty may require a backport of setuptools too.

We're trying to build pre-compiled wheels for windows and OS-X, so folks on
these platforms don't need a compiler to install Tahoe. This is pretty easy for
OS-X, but we're trying trying to figure out how to get our Appveyor.com -based
CI system to expose the wheels it's already building.

The OpenBSD buildslave is currently failing, we think there might be an
incompatibility between the "cryptography" package and the flavor of OpenSSL 
that's available in OpenBSD-5.6 (in particular it appears to lack the ALPN
feature that "cryptography" wants to link against). We'd really like to resolve
this and not have a release that fails to build on OpenBSD.

We spent some time figuring out why Daira's buildslave is failing to build
anything at all. Appveyor is working, so we think windows is working overall,
but we'd really like to have her buildslave operational.

OS-X ".pkg" installers are now working again (they were broken for a while after
the pip switchover). They still only provide a CLI tool, not a double-clickable
setup application, but it's not a bad way to get tahoe and its dependencies
installed.

Windows installers are still a work-in-progress, so we don't build or upload
them.

I'm hoping to announce an alpha1 release later today, or tomorrow.

Tuesday, 03/22
--------------

We worked on `#2745`_, a Linux Mint build failure. We decided this will not be a
blocker.

.. _`#2745`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2745

*The Tahoe-LAFS Weekly News is published once a week by The Tahoe-LAFS*

The Tahoe-LAFS Weekly News is published once a week by The Tahoe-LAFS
Software
Foundation, President and Treasurer: Peter Secor |peter|. Scribes: Patrick
"marlowe" McDonald |marlowe|, Zooko Wilcox-O'Hearn , Editor Emeritus:
|zooko|.
Send your news stories to `marlowe@antagonism.org`_ - submission deadline:
Monday night.

.. _`marlowe@antagonism.org`: mailto:marlowe at antagonism.org
.. |peter| image:: psecor.jpg
   :height: 35
   :alt: peter
   :target: http://tahoe-lafs.org/trac/tahoe-lafs/wiki/AboutUs
.. |marlowe| image:: marlowe-x75-bw.jpg
   :height: 35
   :alt: marlowe
   :target: http://tahoe-lafs.org/trac/tahoe-lafs/wiki/AboutUs
.. |zooko| image:: zooko.png
   :height: 35
   :alt: zooko
   :target: http://tahoe-lafs.org/trac/tahoe-lafs/wiki/AboutUs

