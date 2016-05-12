====================================================
Tahoe-LAFS Weekly News, issue number 66, May 11 2016
====================================================

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
.. _look: https://tahoe-lafs.org/~marlowe/TWN66.html


Nuts and Bolts
==============

Friday, 05/06
-------------

Attendees: Brian Warner, Daira Hopwood, meejah, Patrick R McDonald


Brian and Patrick worked through tickets owned by Patrick:

* `#2215`_
* `#2222`_
* `#1663`_
* `#1745`_
* `#1826`_
* `#1879`_
* `#1884`_
* `#1929`_
* `#2050`_
* `#2127`_
* `#2226`_
* `#2228`_
* `#2257`_
* `#2258`_
* `#1782`_
* `#2012`_

In addition, they created #2785 as another documentation ticket.

Brian Warner kindly provided the remaining notes.

Daira and Meejah showed up at 10am, just after you and I dropped off,
and we discussed:

* introducing a "tahoe configure-node" command, which would either edit
  tahoe.cfg, or use some new API calls to ask a running tahoe node to
  modify its own config. This could be interactive (either with a
  text/curses UI, or through a web page), and could walk you through
  questions like "do you want to run a server?", "what is your
  hostname?", etc.

* "tahoe create-server" could be a shortcut for "create-node +
  configure-node".

* "tahoe create-server --hostname=auto" could mean "use ifconfig to scan
  for IP addresses, ask tahoe-lafs.org to try to connect to them, if
  that works great, if not, explain about firewalls and port
  forwardings". That would make it easy to automatically set up a server
  if you're in the (small) class of users who have public IP addresses,
  and would provide a clear failure (and instructions about what to do
  next) if you aren't.

* Daira is working on rebasing the LAE "cloud-backend" branch to 1.11,
  after which we'll re-rebase it to current trunk and try to land it.
  This branch adds pluggable backend storage providers (like AWS/S3) and
  the "lease DB", both of which power LAE's "S4" service. It is a very
  large branch (150 commits), and has been diverging from trunk for
  years, so it is a pretty tricky merge. It includes a number of other
  fixes that we'd prefer to split out into separate patches (in
  particular it'd be nice to land leasedb first, then the additional
  backends), but it may be too involved to do that.

* Meejah is still working on fixing the magic-folders branch (`PR #275`_)
  so we can land it. It currently fails tests on windows, and has some
  minor debug messages that need to be turned off. I'm hoping we can
  land this next week.

* After Daira left, Meejah and Brian discussed approaches for
  integrating tahoe with other projects. In the long-run, should
  magic-folders be a feature of the main Tahoe daemon, or should it be a
  tahoe plugin, or should it be a standalone application that imports
  tahoe as a library? I'll write a longer email to tahoe-dev about this
  one.

.. _`#2215`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2215
.. _`#2222`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2222
.. _`#1663`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/1663
.. _`#1745`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/1745
.. _`#1826`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/1826
.. _`#1879`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/1879
.. _`#1884`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/1884
.. _`#1929`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/1929
.. _`#2050`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2050
.. _`#2127`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2127
.. _`#2226`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2226
.. _`#2228`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2228
.. _`#2257`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2257
.. _`#2258`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2258
.. _`#1782`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/1782
.. _`#2012`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2012

.. _`PR #275`: https://github.com/tahoe-lafs/tahoe-lafs/pull/275

Tuesday, 05/03
--------------
 
Attendees: daira, zooko, meejah, dawuud, cypher, warner

* more audio problems, warner and meejah couldn't hear each other, zooko
  was robot-voiced

* daira is working on rebasing the cloud-backend branch to 1.11.0, both
  to get LAE's S4 service working again, and to move it closer to
  landing. warner agreed to take it the rest of the way (rebasing from
  1.11.0 to current trunk, then landing it), although that probably
  won't happen until after PyCon (early June)

* meejah is getting close to getting a working magic-folder branch
  rebased onto current master. It currently fails tests on windows, and
  he's trying to pull windows-specific fixes from other branches to
  resolve the problem. Once tests are passing, we'll land it.

* We might be able to do a new release in late June, with one or both of
  these features in place.

* We discussed Tahoe-as-library for a little while. cypher's "grid-sync"
  program is happy using Tahoe-as-local-service. Afterwards, meejah and
  warner came up with "txlafs", a hypothetical library that does Tahoe
  uploads and downloads, but which does not include any frontends or
  server code or daemon-ish tendencies. Ticket `#2786`_ has details.

.. _`#2786`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2786

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

