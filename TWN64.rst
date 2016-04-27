======================================================
Tahoe-LAFS Weekly News, issue number 64, April 26 2016
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
.. _look: https://tahoe-lafs.org/~marlowe/TWN64.html


Nuts and Bolts
==============

Friday, 04/22
-------------

Attending: Zooko, Daira, Meejah, Brian, rkrishnan

* The new time (9am pacific) seems to work for everybody, but Zooko
  hadn't updated the calendar announcement that he maintains, so he and
  Daira hadn't heard about the new time.

* We landed a small patch from the magic-folders branch. Meejah
  continues to rearrange that branch, pulling out the pieces that are
  not specific to the magic-folders project, and submitting them as
  separate PRs (to land first). We're hoping to land the rest of the
  branch next week. One bug was filed (`#2780`_) to use the pre-existing
  OneShotObserverList device instead of passing a Deferred into a class
  constructor: that cleanup should be pretty quick, but needs to happen
  before the branch will land.

* Zooko expressed concern about Tahoe's current behavior when it hasn't
  finished connecting to all storage servers: until we land the "servers
  of happiness" branch, a node will cheerfully upload all shares to a
  single server, or to itself (if that node is both server and client),
  if no other servers are available. This can happen if the upload is
  started very soon after node startup (before it's finished connecting
  to servers), or when the host computer is not yet on a network (think
  of a laptop with wifi turned off). He proposed that we actively
  discourage folks from using Tahoe on anything but a
  one-client-one-server configuration. That obviously didn't feel great,
  so we agreed to double down on landing shares-of-happiness (`#1382`_).
  The branch itself is large and stale, and nobody really understands it
  anymore, so Zooko suggested the best approach might be to start by
  reading the docs, understanding the intent, then write a brand new
  branch (grabbing bits of code from the old one when possible), rather
  than trying to rebase/modify the existing branch.

* We closed several obsolete pull requests that had targetted
  intermediate branches, rather than master.

* Daira has rebased the cloud-backend branch to current master, and is
  working on making tests pass. She will submit a PR with the best
  branch to review, and we'll iterate on improving it (both to get the
  tests to pass, and to pull out any non-cloud-specific cleanups that
  can be landed first). My goal is to have a clear history for future
  readers: first turn the existing local-disk backend into a plugin,
  then second adding the cloud-backend provider plugins.

.. _`#2780`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2780
.. _`#1382`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/1382 

Tuesday, 04/26
--------------

Attendees: warner, meejah, dstainton

* reviewed, improved, and landed `PR #269`_, which adds a hook to stall
  drop-upload/magic-folder uploading until a sufficient quorum of
  storage servers are connected. Discussed how to do this without using
  the recently-deprecated rref.notifyOnDisconnect()

* added a dependency on "mock" when running the test suite

* improve the comments in the initial tahoe.cfg file to explain that the
  "encoding parameters" are only used for newly-uploaded files, so you
  can safely change them whenever you want, without affecting your
  ability to download old files

* switched to https://appear.in/tahoe-lafs , which appears to use less
  CPU (perhaps it turns off the video codec when facemuted?), and caused
  meejah to be less robot-voiced than `talky.io`_

.. _`PR #269`: https://github.com/tahoe-lafs/tahoe-lafs/pull/269
.. _`talky.io`: http://talky.io

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

