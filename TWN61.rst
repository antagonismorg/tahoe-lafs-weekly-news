======================================================
Tahoe-LAFS Weekly News, issue number 61, March 29 2016
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
.. _look: https://tahoe-lafs.org/~marlowe/TWN61.html


Announcements and News
======================

Foolscap 0.11 Released
----------------------

Brian `released Foolscap 0.11`_. Foolscap is a secure RPC protocol for
Twisted+Python, which Tahoe-LAFS uses for its connections to the storage
servers.

.. _`released Foolscap 0.11`:
  https://tahoe-lafs.org/pipermail/tahoe-dev/2016-March/009699.html

Test Grid Tests 1.11.0
----------------------

Paul Rabahy announced the `test grid will help test 1.11.0`_. The test grid will
track the alpha and beta releases. Please be advised this may cause some down
time.

.. _`test grid will help test 1.11.0`:
  https://tahoe-lafs.org/pipermail/tahoe-dev/2016-March/009701.html

PyPI "distribution name" changed, 1.11.0a2 tagged
-------------------------------------------------

Brian `released 1.11.0a2`_. This closes `#2011`_ which changes the PyPI
distribution name from "allmydata-tahoe" to "tahoe-lafs".

.. _`released 1.11.0a2`:
  https://tahoe-lafs.org/pipermail/tahoe-dev/2016-March/009703.html
.. _`#2011`:
  https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2011

1.11.0b1 tagged
---------------

Brian `released 1.11.0b1`_. Brian is aiming to make the final release on
Thursday, March 31. So, please test this out: see if the instructions in
the README (and the new INSTALL.rst) are surprising, or wrong. Look for
broken links, wiki pages that don't point to useful things, problems on
platforms we aren't able to test on. I'm especially looking for
independent confirmation of the OS-X and windows install docs.

.. _`released 1.11.0b1`:
  https://tahoe-lafs.org/pipermail/tahoe-dev/2016-March/009705.html

zfec trac is back
-----------------

Brian `fixed the zfec trac instance`_ and pointed it to vu3rdd's github repo.

.. _`fixed the zfec trac instance`:
  https://tahoe-lafs.org/pipermail/tahoe-dev/2016-March/009706.html

Rightscon
---------

Patrick will be at `Rightscon`_ next week. Please drop him a line and say hi.
He would love to hear what you like about TWN, what new things you would like
to see added, and how you are using Tahoe-LAFS.

.. _`Rightscon`: https://rightscon.org

Nuts and Bolts
==============

Nuts and Bolts is held regularly at 1700Z on Tuesdays and Fridays. Check in IRC
for the URI of the meeting. 

Tuesday, 03/29
--------------

Attendees: Brian Warner, David Stainton, Leif Ryge, Patrick R McDonald

We tested the 1.11.0b1 release. Things look good. We attached multiple servers,
including an experimental one over `Tor`_.

.. _`Tor`: https://torproject.org

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

