=====================================================
Tahoe-LAFS Weekly News, issue number 69, June 23 2016
=====================================================

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
.. _look: https://tahoe-lafs.org/~marlowe/TWN69.html


Nuts and Bolts
==============

Tuesday 06/21/16
----------------

Attendees: warner, dawuud, meejah, liz, cypher, daira, zooko

`Decentralized Web Summit`_ was a blast, Tahoe lightning talk was well-received,
many stickers were handed out. There were several related projects on display,
and we can probably adopt ideas and code from them (web-based frontends,
NAT-punching techniques, UI patterns).

We talked about immutable file encodings that would give us shorter filecaps:
Daira's old RainHill / ElkPoint designs, warner and zooko's discussions from
last week.

* warner is envious of the short filecaps provided by several projects we saw at
  the Decentralized Web Summit the other week. OTOH almost none of them were
  trying to provide confidentiality, which has a major impact on the design
  space.

* The bits in a filecap provide various properties: Confidentiality,
  Integrity/Identification, Location. Also "committment" (to a single plaintext,
  equivalent to protection against hash collisions), protection against
  server-side "roadblock" attacks (enabling server-side verification), enabling
  repair.

* Sometimes a single bit can do double-duty (Confidentiality *and* Integrity),
  but at the cost of other properties.

* "committment" is the most expensive, since the birthday bound requires
  2*k*ln2(numfiles) bits to achieve a security parameter of "k", whereas most of
  the other properties only require 1*k.

meejah says the magic-folder branch is ready to land. warner will start testing
it locally today. daira wants to rebase the cloud-backend branch and land it
first, *then* re-rebase magic-folders. Either one landing would be justification
for making a new Tahoe release. We might delay the release by a week to get both
in, but if they're likely to take more time than that, we'd make two separate
releases.

zooko reminded us that `#1382`_ (servers of happiness) is really important, and
should really go into the next release. The next step is for warner to learn the
algorithm and re-implement it, as a way for him to be comfortable with the
changes. Fortunately the specification is very detailed and really only admits
one possible approach.

dawuud reminded us that we need to make progress on `Tor`_ integration, warner
will re-read the tickets and try to remember what the next step should be.

We're dropping down to one meeting per week for a while (just Tuesdays now, not
Tuesday and Friday). We had audio problems with 6/7 people on `appear.in`_
today, so we'll try Google Hangouts next week.

.. _`Decentralized Web Summit`: http://www.decentralizedweb.net/
.. _`#1382`: https://tahoe-lafs.org/trac/tahoe-lafs/ticket/1382
.. _`Tor`: https://torproject.org
.. _`appear.in`: https://appear.in

The Tahoe-LAFS Weekly News is published once a week by The Tahoe-LAFS Software
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

