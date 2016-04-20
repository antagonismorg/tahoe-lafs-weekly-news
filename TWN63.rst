======================================================
Tahoe-LAFS Weekly News, issue number 63, April 19 2016
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
.. _look: https://tahoe-lafs.org/~marlowe/TWN63.html


Announcements and News
======================

Nuts and Bolts Moves to a New Time
----------------------------------

"Hey everybody.. we're moving the twice-weekly developer videochats up by
an hour, to make life easier for folks in europe. (the google calendar
entry that zooko managed was tied to UTC, and the transition to daylight
savings time pushed it an hour later for everybody).

We do these Tuesdays and Fridays (mornings in the US, evenings in
Europe).

The new time is:

* 0900 (9am) San Francisco (PDT)
* 1600 UTC
* 1700 (5pm) London (BST)
* 1800 (6pm) Berlin (CEST)
* 2130 (930pm) Mumbai (IST)
* 0400 (4am) Auckland (NZST) (sorry)

In the (northern-hemisphere) "winter", we'll move it forward to 1700 UTC
to keep local times the same. To honor the arbitraryness of time zones,
we'll make the transition on a randomly-selected date using a weighted
average of the local DST rules of the participants. For a long-term fix,
please see https://tahoe-lafs.org/trac/tahoe-lafs/ticket/1934 .

We're using talky.io for the hangouts these days (instead of google)..
seems to work pretty well. The URL is:

* https://talky.io/tahoe-lafs" [`0`_]

.. _`0`: https://tahoe-lafs.org/pipermail/tahoe-dev/2016-April/009732.html

Gmail Classifying TWN as Spam
-----------------------------

It turns out Gmail is classifying some TWN emails as spam. Patrick created 
`#2772`_ to deal with this issue. If your Gmail account classifies TWN as spam,
please provide the why is this spam reasoning to the ticket. Thank you to our
users who already provided this information. We hope to have this resolved soon.

.. _`#2772`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/2772

Nuts and Bolts
==============

Tuesday, 04/19
--------------

Attendees: Brian Warner, Daira Hopwood, meejah, Patrick R McDonald,
Leif Ryge, David Stainton

Patrick broached the idea of reproducible builds. As a first step, Brian
suggests we use requirements.txt and hashes

Daira added a "python -m allmydata.scripts.runner" -style mode and  also changed
tests that use subprocess(bin/tahoe) to use subprocess(sys.executable, -m,
allmydata.scripts.runner). The next step is to remove 'setup.py make_executable'
and remove bin/tahoe

David brought up the excellent point that we could use a packager for BSD
systems.

In regards to magic-folder, meejah will rebase for landing next week (some
pieces were landed on master, and no longer need to be in the branch).

Below is the `Tor`_/multiintroducer plan.

    * land 2491-sync next week
    * then land the Tor foolscap client connection handler plugin
      somewhere: either in Tahoe itself, or a 3rd package (but not in foolscap)
    * multi-introducer / introducerless / tor-client branch may be ready
      to land next week too, will enable client-side

    * Tor server-side:
        * meejah will work on a txtorcon function that: starts Tor with
          --no-network, creates ephemeral HS, retrieves private key and onion
          address, shuts down Tor
        * tahoe create-server will use that function to compute the
          tub.location, store private key into NODEDIR/private/ somewhere
        * tahoe start will (synchronously) call Tub.setLocation(),
          (synchronously) use txtorcon to create endpoint, pass endpoint to
          Tub.listenOn()
        * still need to decide about CLI arguments. "tahoe create-server
          --tor"? --listen-tor?
        * foolscap needs a test to see if startTLS works over unix-domain sockets
        * ideally SOCKs, Tor-oubound, and Tor-HS-inbound should all use
          unix-domain sockets locally, rather than TCP/localhost

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

