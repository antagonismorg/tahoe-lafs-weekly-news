===================================================
Tahoe-LAFS Weekly News, issue number 65, May 3 2016
===================================================

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
.. _look: https://tahoe-lafs.org/~marlowe/TWN65.html


Nuts and Bolts
==============

Friday, 04/29
-------------

Notes were kindly provided by Brian Warner.

Attendees: meejah, warner, ramki (dropped out due to audio problems)

We still trying to find workable videochat. Used appear.in today, meejah got
connected alright but ramki couldn't get audio working in both directions at the
same time.

We talked about "tahoe create-server" arguments for setting hostname, Tor
options, etc (ticket `#2773`_). We settled on:

  * if you have a public IP address, run "tahoe create-server
    --hostname=HOST", and it will allocate a port for you
  * if you can configure a firewall port-forwarding, use
    "--location=tcp:EXTHOST:EXTPORT --port=tcp:INTPORT"
  * if you have neither, but do have Tor, and all your clients can use
    Tor, do "--listen-tor"

We talked about a "server setup wizard" mode, which would try multiple things
(ifconfig, UPnP), guide the user through port-forwarding settings, and could
confirm conntectivity by having a tahoe-lafs.org-hosted service attempt to
connect to the purported FURL. Then it starts the service and provide
instructions/automation to bring the server up automatically at next boot 
cron jobs, systemd scripts, OS-X LaunchAgent config, etc).

Brian showed off an event-timeline visualization tool I built for
`magic-wormhole`_, similar to Tahoe's "recent uploads and downloads"
download-timeline view. A zoomable timeline that shows where the command is
waiting for network, where it waits for user input, and can guide optimization
efforts.

Gus Andrews and Cypher will join us next tuesday to talk UX

.. _`#2773`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2773 
.. _`magic-wormhole`: https://github.com/warner/magic-wormhole

Tuesday, 05/03
--------------

Attendees: Brian Warner, cypher, David Stainton, Gus Andrews, meejah, Patrick
McDonald 

We discussed our answers to the `questions`_ Gus posed on the tahoe-dev mailing
list. Gus and cypher provided the `answers`_ to the questions they received at
`IFF`_. I found it very eye opening to see the differences between how I
envisioned our eyes and who those potential users were. A special thanks goes to
Gus and Cypher for sharing this. As a result of this work, cypher has a `list of
issues`_ for `Gridsync`_. In addition, cypher is applying for 12 months of
funding to improve Gridsync.

.. _`questions`: https://tahoe-lafs.org/pipermail/tahoe-dev/2016-May/009742.html
.. _`answers`:
  https://github.com/gridsync/gridsync/wiki/Report-from-Internet-Freedom-Fest-%282016%29
.. _`IFF`: https://internetfreedomfestival.org/
.. _`list of issues`:
  https://github.com/gridsync/gridsync/issues?q=is%3Aissue+is%3Aopen+label%3A%22Internet+Freedom+Festival+Design+Workshop%22
.. _`Gridsync`: https://github.com/gridsync/gridsync

From Mailing List
=================

removing the "key-generator" node
---------------------------------

Brian described the idea of `removing the "key-generator" node`_. `#2783`_
describes the issue in greater detail.

.. _`removing the "key-generator node`:
  https://tahoe-lafs.org/pipermail/tahoe-dev/2016-April/009737.html
.. _`#2783`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2783
 
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

