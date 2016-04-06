=====================================================
Tahoe-LAFS Weekly News, issue number 62, April 5 2016
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
.. _look: https://tahoe-lafs.org/~marlowe/TWN62.html


Announcements and News
======================

ANN: Tahoe-LAFS 1.11.0 released
-------------------------------

Brian `released Tahoe-LAFS 1.11.0`_. Please download and install or upgrade and
provde us feedback. We would love to hear your thoughts.

.. _`released Tahoe-LAFS 1.11.0`:
  https://tahoe-lafs.org/pipermail/tahoe-dev/2016-March/009712.html

Tahoe-LAFS on readthedocs.org
-----------------------------

`readthedocs`_ now hosts Tahoe-LAFS documentation.

"http://tahoe-lafs.readthedocs.org/ now contains a shiny new copy of the
Tahoe-LAFS documentation. I updated all the cross-references and fixed a lot of
formatting. This is now the preferred place to see rendered .rst documentation
(it gets updated on every commit). Github still renders the files, but it
doesn't get the links right, and it lacks the table-of-contents that ReadTheDocs
offers."

.. _`readthedocs`:
  https://tahoe-lafs.org/pipermail/tahoe-dev/2016-March/009708.html

zfec in Tahoe-LAFS github.org
-----------------------------

"vu3rdd has moved the "zfec" repository underneath the Tahoe-LAFS Github
organization, so the canonical URL is now:

   https://github.com/tahoe-lafs/zfec

He's working on a new release." [`0`_]

.. _`0`:
  https://tahoe-lafs.org/pipermail/tahoe-dev/2016-March/009708.html

The Github "attic" Repo
-----------------------

Brian created the `attic repo`_. All the old branches under the Tahoe-LAFS repo
now reside in the attic. Brian also provided some recommendations on using git
to hack on Tahoe-LAFS.

.. _`attic repo`:
  https://tahoe-lafs.org/pipermail/tahoe-dev/2016-April/009716.html

Test Grid Downtime
------------------

Paul Rabahy announced the `test grid will down`_ for about a week.

.. _`test grid will down`:
  https://tahoe-lafs.org/pipermail/tahoe-dev/2016-April/009718.html

No Nuts and Bolts This Week
---------------------------

As noted here, https://twitter.com/tahoelafs/status/716354143972012032, there
are no Nuts and Bolts this week. The devs are taking some well deserved R&R this
week after the 1.11.0 release. The meetings will resume next week.

Rightscon
---------

Patrick had a fantastic time at `Rightscon`_ and highly recommends you attend it
next year if at all possible. During the "hallway con" portion, he had a
fascinating discussion with Gus Andrews of `SimplySecure`_. Gus previously
provided terrific insights into the `UX of Tahoe-LAFS`_ and `Gridsync`_. Gus
will be attending a future Nuts and Bolts to help share further insights.

.. _`Rightscon`: https://rightscon.org
.. _`SimplySecure`: http://simplysecure.org
.. _`UX of Tahoe-LAFS`:
  http://gandre.ws/blog/blog/2015/04/07/why-the-command-line-is-not-usable/
.. _`Gridsync`:
  https://medium.com/@gusandrews/expert-review-gridsync-a-secure-cloud-app-built-on-tahoe-lafs-c290252b15bb

Nuts and Bolts
==============

Nuts and Bolts is held regularly at 1700Z on Tuesdays and Fridays. Check in IRC
for the URI of the meeting. 

Friday, 04/01
-------------

Note: Notes provided by Brian Warner and posted in full `here`_.

Attendees: Brian Warner, meejah

"On the devchat this morning, meejah and I talked about the status of the
"magic folders" project, specifically trying to work out how we could
start landing some of it, to reduce the increasing workload of
maintaining a long-running branch (while trunk has moved out from under
it).

I'd like to hear from Daira and Zooko (and everyone else involved), but
it sounds like the magic-folders branch might be 1: sufficiently
isolated, and 2: sufficiently functional, that we could land it now and
just mark it as "Experimental" without causing anything to explode. If
so, that'd be great, as then the folks hacking on it could do their
continued work on a much shorter branch that should be a lot easier to
maintain (and merge from trunk, or rebase, or however they choose to
manage it).

I've taken the liberty of rebasing the most recent branch that meejah
and I could find, "2438.magic-folder-stable.13", and rebasing it up to
current master. I fixed the merge conflicts along the way (mostly in the
docs, where I'd changed the format of inter-document links, and the 2438
branch had added some text around those links).

I pushed my work to github.com/warner/2438-13-rebased .

The branch is 224 patches long, which is a lot, but I'm willing to land
it (as a merge commit) as-is, if:

* the magic-folder folks say that it makes sense to do so
* it doesn't break anything outside of magic-folders

It looks like the branch removes the "drop-upload" feature (I imagine
magic folders is meant to replace drop-upload). If magic-folders remains
experimental for a while (in particular, if we make the next release
before it's ready), is it going to be a problem to have removed
drop-upload? I want trunk to remain releaseable, and if the current
magic-folder code is not a suitable replacement, then we need to change
this branch to retain drop-upload and provide both features in parallel
for a while.

Looking at the diff (git diff master..warner/2438-13-rebased --stat), I
see the new files, and the expected smaller changes to wires things in
(client.py, interfaces.py, web/root.py, etc). And then I see a bunch of
small changes that don't feel related, like immutable/upload.py . I'm
guessing these are cleanups or refactorings that were done along the
way. It'd be great if we could land these first, so the main "add magic
folders" merge patch only touches the things that are really related to
magic folders.

The way I usually do this (on my own work) is to squash down my feature
branch into a single/few commits, then split them back out into commits
that do cleanups followed by commits that add the feature. For example,
I'll check out the parent commit, perform my cleanup changes, commit,
then overwrite all files with the feature+cleanup versions, then commit
again. Then we can land the first commit on trunk now, and keep working
on the feature branch. This way, the branch gets smaller and smaller
over time until the only thing left on it is the feature itself.

I can try to do this work for the 2438 branch, if you want. If the
cleanup patches are relatively isolated, I can rearrange the branch to
put them near the front. But with such a long branch, that might not be
possible, so we may just have to review those cleanups along with
everything else, and land the whole thing at once.

Anyways, I'm concerned about the maintenance overhead of having those
long-lived large-feature branches hanging around outside the main tree
for a long time, and I'd like to start bringing them in. Let me know
what I can do to help."

.. _`here`:
  https://tahoe-lafs.org/pipermail/tahoe-dev/2016-April/009717.html

Tuesday, 04/05
--------------

No meeting due to R&R for 1.11.0 release

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

