---
layout: post
title: 'Refactoring SMTP Diagnostics...The Story Continues'
categories:
  - blogger

---

My small refactoring effort on SMTP Diagnostics turned into a much bigger effort but the end result is a much better code base.  The exercise led to re-architecting most of the application.  The GUI remains untouched but everything else behind the scenes has changed.  After an 11 hour marathon session, I finally got a clean compile.  I still need to re-wire parts of the GUI to the new object model before I can begin testing.  But I did write unit tests (using <a href="http://dunit.sourceforge.net/">DUnit</a>) for all of the non-GUI code as part of the refactoring exercise.  All of this re-work is definitely going to make it easier to add new features in the future.<br /><br /><b>Incorporating another New Feature</b><br /><br />Speaking of new features, a fellow developer recommended I incorporate <a href="http://www.xml.com/pub/a/2002/12/18/dive-into-xml.html">RSS</a> feeds as a way to inform users of new releases within the program.  I instantly fell in love with this idea mainly because it allows me to share more information with customer beyond just "a new release is available".  By using an RSS feed, I will be able to let users know about new releases, show the list of enhancements and bug fixes, send out tips, and possibly a newsletter some day.<br /><br />Of course the user will have the option to turn off the feed feature, or to display the feed on demand.  But I think this is a great use for RSS that I plan to incorporate in all of our products going forward.