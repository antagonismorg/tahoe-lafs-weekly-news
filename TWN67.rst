====================================================
Tahoe-LAFS Weekly News, issue number 67, May 19 2016
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
.. _look: https://tahoe-lafs.org/~marlowe/TWN67.html


Nuts and Bolts
==============

Friday, 05/13
-------------

Attendees: warner, zooko, daira, meejah, marlowe

* Zooko, Brian, and possibly Patrick will be at the `Decentralizing the Web
  Summit`_. Please seek us out and share your thoughts on Tahoe-LAFS. We would
  love to hear from you and see you in person.

.. _`Decentralizing the Web Summit`: http://www.decentralizedweb.net/

Tuesday, 05/17
--------------
 
Attendees: warner, meejah, dawuud, daira

* Daira is still working on cloud-backend branch, trying to rebase to
  1.11.0, tests are currently failing in nondeterministic ways

* Meejah is still working on magic-folders branch, trying to resolve a
  windows-only test failure

* Most of the meeting was spent discussing the cluster of tickets that
  will enable `Tor`_, support multiple (or no) introducers, allow
  manually-specified storage servers, and allow configuration of
  connection policy on a per-server basis. `#2759`_ / `#2788`_ are
  related. We settled on a pleasant-looking schema for the
  "connections.yaml" file, but weren't quite sure what to name the
  file or whether to use YAML in the first place.

Brian and Meejah (at least) will be at `PyCon`_ in Portland at the end
of the month (Brian is presenting Magic-Wormhole,
https://github.com/warner/magic-wormhole/). Both will be around for a
few days of sprints, so other Tahoe hackers should find them and hack
together.

.. _`Tor`: https://torproject.org
.. _`PyCon`: https://us.pycon.org/2016/
.. _`#2759`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2759
.. _`#2788`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2788

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

